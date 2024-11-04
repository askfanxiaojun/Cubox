OpenAI开发系列（十二）：Function calling功能的流程优化与多轮对话实现
=============================================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/645732735)算法小陈互联网行业 运维开发工程师

目录

收起

一、Function calling 流程优化思路

二、优化一：如何实现functions参数值的自动构建

三、优化二：如何实现中间过程messages的自动拼接

四、实践：开发一个专属对话小助理

五、总结

> **授权声明：**   
> 本文基于九天Hector的原创课程资料创作，已获得其正式授权。   
> 原课程出处：[九天Hector的B站主页](https://link.zhihu.com/?target=https%3A//space.bilibili.com/385842994)，感谢九天Hector为学习者带来的宝贵知识。   
> 请尊重原创，转载或引用时，请标明来源。

**全文共7000余字，预计阅读时间约25\~40分钟 \| 满满干货(附代码)，建议收藏！**

**本文目标：围绕Chat Completion模型的Function calling功能进行更高层次的函数封装，实现一个能够调用外部函数的多轮对话助理**
> 写在前面：本文内容的复现过程，如果有条件的，建议使用gpt 4接口，输出稳定，gpt3.5不太稳定，但运行几次也能得到标准结果。
>
> 如果存在Rate limit 报错，是OpenAI的速率限制，可以绑定信用卡后解除，以保证程序正常运行。
![](https://image.cubox.pro/cardImg/2023111018080856438/65795.jpg?imageMogr2/quality/90/ignore-error/1)

[代码下载地址 pan.baidu.com/s/1osyF6tgyEHRkaAW-44V6BA?pwd=0dz2](https://link.zhihu.com/?target=https%3A//pan.baidu.com/s/1osyF6tgyEHRkaAW-44V6BA%3Fpwd%3D0dz2)

**一、Function calling 流程优化思路**
-----------------------------

在[OpenAI开发系列（十一）：Function calling功能的实际应用流程与案例解析](https://zhuanlan.zhihu.com/p/645501247)这篇文章中详细解释了Function calling的用法，当大模型激活Function calling功能时，其完整的推理流程应该是这样的：
![](https://image.cubox.pro/cardImg/2023111018080862903/77170.jpg?imageMogr2/quality/90/ignore-error/1)

当大模型激活Function Calling功能时，其推理过程也会发生相应的改变，即：**根据大模型返回的函数和函数参数，在本地完成函数计算，然后再将计算过程和结果保存为message并追加到messages后面，并第二次调用Chat Completion模型分析函数的计算结果，并最终根据函数计算结果输出用户问题的答案。**

尽管这种方式是有效的，对于目前的Function Calling实现流程，尽管步骤明确，但涉及多个代码环节以完成一个完整流程。在需要高频使用此功能的应用场景中，这种复杂性会显著降低使用和开发效率。因此，对该流程的优化是一定要做的事。

**总的来说，可以想到的优化的方向有两个**：提升functions参数的编写效率和优化不断拼接messages的这个过程。

还是使用上篇文章我创建的函数内容来说明，我稍微做了一些修改，在函数命名上及其对应的JSON Schema描述上分别使用后缀*function和*describe来更好的区分，代码如下：

     # 1.定义功能函数
     def calculate_total_age_function(input_json):
         """
         从给定的JSON格式字符串（按'split'方向排列）中解析出DataFrame，计算所有人的年龄总和，并以JSON格式返回结果。
     ​
         参数:
         input_json (str): 包含个体数据的JSON格式字符串。
     ​
         返回:
         str: 所有人的年龄总和，以JSON格式返回。
         """
     ​
         # 将JSON字符串转换为DataFrame
         df = pd.read_json(input_json, orient='split')
     ​
         # 计算所有人的年龄总和
         total_age = df['Age'].sum()
     ​
         # 将结果转换为字符串形式，然后使用json.dumps()转换为JSON格式
         return json.dumps({"total_age": str(total_age)})
     ​
     # 2.将功能函数存储至外部函数仓库
     function_repository = {
                 "calculate_total_age_function": calculate_total_age_function,
             }
     ​
     ​
     # 3.构建功能函数的Json Schema描述
     calculate_total_age_describe = {"name": "calculate_total_age_function",
                           "description": "计算年龄总和的函数，从给定的JSON格式字符串（按'split'方向排列）中解析出DataFrame，计算所有人的年龄总和，并以JSON格式返回结果。",
                           "parameters": {"type": "object",
                                          "properties": {"input_json": {"type": "string",
                                                                  "description": "执行计算年龄总和的数据集"},
                                                        },
                                          "required": ["input_json"],
                                         },
                          }
     ​
     ​
     # 4. 添加到functions列表中，在对话过程中作为函数库传递给function参数
     functions = [calculate_total_age_describe]

如果真的理解了[OpenAI开发系列（十一）：Function calling功能的实际应用流程与案例解析](https://zhuanlan.zhihu.com/p/645501247)这篇文章的内容，上述代码应该很容易理解，此处就不重复说明了 。

上面这份代码虽然逻辑上没有什么问题，但其实存在两点问题：

1. **一个外部函数库`function_repository`必然是包含大量不同的功能函数，逐个手工编写其对应的JSON Schema会非常复杂。**
2. **与模型的交互过程中，关心的是最后的输出结果，所以向大模型提问时中间有几次调用模型的过程，体现出来没有任何意义。**

对于上述两点，我能想到的优化方式是：

1. **通过提示工程，让大模型根据传入的功能函数代码自动编写出其Json Schema描述，创建想用的functions参数**。
2. **以代码形式，将人工拼接的messages过程用函数做好封装，把中间过程作为一个黑箱子闭合起来**。

下面是我针对这两方面的优化过程。

**二、优化一：如何实现functions参数值的自动构建**
-------------------------------

* **Step 1：明确需求**

**在请求大模型完成特定需求前，首先要确认其是否具备相应能力**，这就像不可能指望一个小学生解决高考题一样。对于我的需求，我希望大模型能自动根据功能函数代码生成对应的JSON Schema描述。因此，首先我需要确认大模型是否理解什么是JSON Schema对象。

* **Step 2：确定大模型的知识储备**

     response = openai.ChatCompletion.create(
       model="gpt-3.5-turbo-16k-0613",
       messages=[
         {"role": "user", "content": "你知道Json Schema对象吗？如果知道的话，请详细的描述一下"}
       ]
     )

看下大模型的回复：

     response.choices[0].message['content']

![](https://image.cubox.pro/cardImg/2023111018080916540/54916.jpg?imageMogr2/quality/90/ignore-error/1)

可以明显看到，大模型对JSON Schema的结构的一些关键点还是非常清楚。

需要明确的是，生成JSON Schema对象描述主要依赖于两个关键因素：**函数的说明文档和其代码逻辑，包括输入参数和返回值**。虽然大模型在代码解析方面无疑是强大的，但生成准确的JSON Schema仍然受到函数文档清晰度和变量、返回值规范性的严格限制。

所以有理由相信：**只要详细的编写每个函数的函数说明，并且通过合理的提示让模型理解functions参数结构，同时借助模型本身对JSON Schema的理解，是能够让Chat Completions模型很好的解析功能函数并生成其标准的JSON Schema描述的。**这也是为什么我在上一篇文章中强调，编写功能函数时应遵循良好和规范的编程风格。

* **Step 3：提取功能函数的函数说明**

在Python中，可以通过一个内置的`inspect`模块来提取函数的文档字符串（docstring）。

     import inspect
     ​
     # 使用inspect模块提取文档字符串
     function_declaration = inspect.getdoc(calculate_total_age_function)

看下提取结果：
![](https://image.cubox.pro/cardImg/2023111018080928685/93109.jpg?imageMogr2/quality/90/ignore-error/1)

* **Step 4: 编写提示词，生成函数对应的JSON Schema描述**

根据功能函数的说明编写提示词，引导模型生成正确的JSON Schema描述，如下是我写的提示词：

     response = openai.ChatCompletion.create(
       model="gpt-3.5-turbo-16k-0613",
       messages=[
         {"role": "system", "content": "你是一位优秀的数据分析师，现在有一个函数的详细声明如下：%s" % function_declaration},
         {"role": "user", "content": "请根据这个函数声明，为我生成一个JSON Schema对象描述。这个描述应该清晰地标明函数的输入和输出规范。具体要求如下：\
                                     1. 在JSON Schema对象中，设置函数的参数类型为'object'.\
                                     2. 'properties'字段如果有参数，必须表示出字段的描述. \
                                     3. 从函数声明中解析出函数的描述，并在JSON Schema中以中文字符形式表示在'description'字段.\
                                     4. 识别函数声明中哪些参数是必需的，然后在JSON Schema的'required'字段中列出这些参数. \
                                     5. 输出的应仅为符合上述要求的JSON Schema对象内容,不需要任何上下文修饰语句. "}
       ]
     ) 

看下大模型的输出结果：
![](https://image.cubox.pro/cardImg/2023111018080970394/60316.jpg?imageMogr2/quality/90/ignore-error/1)

可以看出，大模型已经按照提示词的第5条要求仅输出了 JSON格式对象，可以通过json.loads方法将其转化为python对象，直观的看一下：

     json.loads(response.choices[0].message['content'])

看下结果：
![](https://image.cubox.pro/cardImg/2023111018080954399/54486.jpg?imageMogr2/quality/90/ignore-error/1)

通过对比手动编写的结果，两者是高度一致的，这就验证了模型能够根据函数的参数说明正确识别计算函数的参数格式，并输出对应的JSON Schema对象。

* **Step 5：利用Few-Shot提示法提升输出稳定性**

一套精心设计的提示词能极大地提升模型输出的稳定性和准确性。尽管如此，即便在GPT-3.5或GPT-4的接口下，输出仍有可能出现不稳定的情况。为了增加输出稳定性，结合系统角色（system role）和少量样本提示（Few-Shot prompting）是一种有效的策略。这种方法不仅明确地指导了模型的任务，还通过提供少量相关的样本，有助于模型更准确地理解期望的输出格式和内容。这样做更有可能使你得到稳定和准确的结果。

1. 定义system role的Few-Shot提示

     # 定义system role的Few-shot提示
     system_Q = "你是一位优秀的数据分析师，现在有一个函数的详细声明如下：%s" % function_declaration
     system_A = "计算年龄总和的函数，该函数从一个特定格式的JSON字符串中解析出DataFrame，然后计算所有人的年龄总和并以JSON格式返回结果。\
                 \n:param input_json: 必要参数，要求字符串类型，表示含有个体年龄数据的JSON格式字符串 \
                 \n:return: 计算完成后的所有人年龄总和，返回结果为JSON字符串类型对象"

1. 定义user role的Few-Shot提示

     # 定义user role的Few-shot提示
     ​
     user_Q = "请根据这个函数声明，为我生成一个JSON Schema对象描述。这个描述应该清晰地标明函数的输入和输出规范。具体要求如下：\
               1. 提取函数名称：%s，并将其用作JSON Schema中的'name'字段  \
               2. 在JSON Schema对象中，设置函数的参数类型为'object'.\
               3. 'properties'字段如果有参数，必须表示出字段的描述. \
               4. 从函数声明中解析出函数的描述，并在JSON Schema中以中文字符形式表示在'description'字段.\
               5. 识别函数声明中哪些参数是必需的，然后在JSON Schema的'required'字段中列出这些参数. \
               6. 输出的应仅为符合上述要求的JSON Schema对象内容,不需要任何上下文修饰语句. "  % calculate_total_age_function.__name__
     ​
     user_A = "{'name': 'calculate_total_age_function', \
                        'description': '计算年龄总和的函数，从给定的JSON格式字符串（按'split'方向排列）中解析出DataFrame，计算所有人的年龄总和，并以JSON格式返回结果。 \
                        'parameters': {'type': 'object', \
                                       'properties': {'input_json': {'description': '执行计算年龄总和的数据集', 'type': 'string'}}, \
                                       'required': ['input_json']}}"

1. 拼接messages

     messages=[
                 {"role": "system", "content": "Q:" +  system_Q + user_Q + "A:" + system_A + user_A },
     ​
                 {"role": "user", "content": 'Q:' + system_message + user_message}
     ]

看下最终的messages：
![](https://image.cubox.pro/cardImg/2023111018081043427/59343.jpg?imageMogr2/quality/90/ignore-error/1)

1. 输入模型进行输出测试

     response = openai.ChatCompletion.create(
                       model="gpt-3.5-turbo-16k-0613",
                       messages=messages
                     )

看下最终的输出结果：
![](https://image.cubox.pro/cardImg/2023111018081096454/74673.jpg?imageMogr2/quality/90/ignore-error/1)

经过大量测试也是发现：**大语言模型非常擅长这种按照格式输出文本语义理解内容的形式，所以在自动编写JSON Schema对象写时，Few-shot效果会明显好于Zero-shot过程。**

* **Step Final：函数封装**

上述步骤1-5的过程主要是使用人工编写的Few-Shot提示作为固定模板，以稳定和引导模型生成预期格式的JSON Schema对象。因此，一个用于自动生成并输出这种`functions`参数的封装类可以被视为这一过程的自动化实现，如下：

     class AutoFunctionGenerator:
        """
        AutoFunctionGenerator 类用于自动生成一系列功能函数的 JSON Schema 描述。
        该类通过调用 OpenAI API，采用 Few-shot learning 的方式来生成这些描述。

        属性:
        - functions_list (list): 一个包含多个功能函数的列表。
        - max_attempts (int): 最大尝试次数，用于处理 API 调用失败的情况。
        
        方法:
        - __init__ : 初始化 AutoFunctionGenerator 类。
        - generate_function_descriptions : 自动生成功能函数的 JSON Schema 描述。
        - _call_openai_api : 调用 OpenAI API。
        - auto_generate : 自动生成功能函数的 JSON Schema 描述，并处理任何异常。
        """
        
        def __init__(self, functions_list, max_attempts=3):
            """
            初始化 AutoFunctionGenerator 类。

            参数:
            - functions_list (list): 一个包含多个功能函数的列表。
            - max_attempts (int): 最大尝试次数。
            """
            self.functions_list = functions_list
            self.max_attempts = max_attempts

        def generate_function_descriptions(self):
            """
            自动生成功能函数的 JSON Schema 描述。

            返回:
            - list: 包含 JSON Schema 描述的列表。
            """
             # 创建空列表，保存每个功能函数的JSON Schema描述
            functions = []
            
            for function in self.functions_list:
                
                # 读取指定函数的函数说明
                function_description = inspect.getdoc(function)
                
                # 读取函数的函数名
                function_name = function.__name__
                
                # 定义system role的Few-shot提示
                system_Q = "你是一位优秀的数据分析师，现在有一个函数的详细声明如下：%s" % function_description
                system_A = "计算年龄总和的函数，该函数从一个特定格式的JSON字符串中解析出DataFrame，然后计算所有人的年龄总和并以JSON格式返回结果。\
                            \n:param input_json: 必要参数，要求字符串类型，表示含有个体年龄数据的JSON格式字符串 \
                            \n:return: 计算完成后的所有人年龄总和，返回结果为JSON字符串类型对象"
                
                
                # 定义user role的Few-shot提示
                user_Q = "请根据这个函数声明，为我生成一个JSON Schema对象描述。这个描述应该清晰地标明函数的输入和输出规范。具体要求如下：\
                          1. 提取函数名称：%s，并将其用作JSON Schema中的'name'字段  \
                          2. 在JSON Schema对象中，设置函数的参数类型为'object'.\
                          3. 'properties'字段如果有参数，必须表示出字段的描述. \
                          4. 从函数声明中解析出函数的描述，并在JSON Schema中以中文字符形式表示在'description'字段.\
                          5. 识别函数声明中哪些参数是必需的，然后在JSON Schema的'required'字段中列出这些参数. \
                          6. 输出的应仅为符合上述要求的JSON Schema对象内容,不需要任何上下文修饰语句. "  % function_name

                user_A = "{'name': 'calculate_total_age_function', \
                                   'description': '计算年龄总和的函数，从给定的JSON格式字符串（按'split'方向排列）中解析出DataFrame，计算所有人的年龄总和，并以JSON格式返回结果。 \
                                   'parameters': {'type': 'object', \
                                                  'properties': {'input_json': {'description': '执行计算年龄总和的数据集', 'type': 'string'}}, \
                                                  'required': ['input_json']}}"
                
                
                # 定义输入

                system_message = "你是一位优秀的数据分析师，现在有一个函数的详细声明如下：%s" % function_description
                user_message = "请根据这个函数声明，为我生成一个JSON Schema对象描述。这个描述应该清晰地标明函数的输入和输出规范。具体要求如下：\
                                1. 提取函数名称：%s，并将其用作JSON Schema中的'name'字段  \
                                2. 在JSON Schema对象中，设置函数的参数类型为'object'.\
                                3. 'properties'字段如果有参数，必须表示出字段的描述. \
                                4. 从函数声明中解析出函数的描述，并在JSON Schema中以中文字符形式表示在'description'字段.\
                                5. 识别函数声明中哪些参数是必需的，然后在JSON Schema的'required'字段中列出这些参数. \
                                6. 输出的应仅为符合上述要求的JSON Schema对象内容,不需要任何上下文修饰语句. "  % function_name
                
                messages=[
                            {"role": "system", "content": "Q:" +  system_Q + user_Q + "A:" + system_A + user_A },

                            {"role": "user", "content": 'Q:' + system_message + user_message}
                ]

                response = self._call_openai_api(messages)
                functions.append(json.loads(response.choices[0].message['content']))
            return functions

        def _call_openai_api(self, messages):
            """
            私有方法，用于调用 OpenAI API。

            参数:
            - messages (list): 包含 API 所需信息的消息列表。

            返回:
            - object: API 调用的响应对象。
            """
            # 请根据您的实际情况修改此处的 API 调用
            return openai.ChatCompletion.create(
                model="gpt-3.5-turbo-16k-0613",
                messages=messages,
            )
        
        def auto_generate(self):
            """
            自动生成功能函数的 JSON Schema 描述，并处理任何异常。

            返回:
            - list: 包含 JSON Schema 描述的列表。

            异常:
            - 如果达到最大尝试次数，将抛出异常。
            """
            attempts = 0
            while attempts < self.max_attempts:
                try:
                    functions = self.generate_function_descriptions()
                    return functions
                except Exception as e:
                    attempts += 1
                    print(f"Error occurred: {e}")
                    if attempts >= self.max_attempts:
                        print("Reached maximum number of attempts. Terminating.")
                        raise
                    else:
                        print("Retrying...")

这个`AutoFunctionGenerator`类的处理逻辑与步骤1-5基本一致，不过额外加入了一层错误处理机制。这是因为**在实际测试中发现，即使在提示词中明确要求"输出仅应为符合要求的JSON Schema对象内容，不需要任何额外的上下文修饰"，模型仍有可能输出不符合要求的描述性内容。这种偏离预期的输出会导致`json.loads(response.choices[0].message['content'])`执行时出错。**

1. 单个功能函数测试

提取calculate_total_age_function这个功能函数对应的JSON Schema对象描述，代码如下：

     if __name__ == '__main__':
         # 示例函数列表
         def calculate_total_age_function(input_json):
             """
             从给定的JSON格式字符串（按'split'方向排列）中解析出DataFrame，计算所有人的年龄总和，并以JSON格式返回结果。
     ​
             参数:
             input_json (str): 包含个体数据的JSON格式字符串。
     ​
             返回:
             str: 所有人的年龄总和，以JSON格式返回。
             """
     ​
             # 将JSON字符串转换为DataFrame
             df = pd.read_json(input_json, orient='split')
     ​
             # 计算所有人的年龄总和
             total_age = df['Age'].sum()
     ​
             # 将结果转换为字符串形式，然后使用json.dumps()转换为JSON格式
             return json.dumps({"total_age": str(total_age)})
     ​
         functions_list = [calculate_total_age_function]
         generator = AutoFunctionGenerator(functions_list)
         function_descriptions = generator.auto_generate()

输出如下：
![](https://image.cubox.pro/cardImg/2023111018081063504/42300.jpg?imageMogr2/quality/90/ignore-error/1)

1. 多个功能函数测试

接下来进一步测试，当添加多个功能函数时，能否能依次生成每个功能函数对应的JSON Schema描述，并组成functions列表。
> 新建了一个函数calculate_married_count()

     if __name__ == '__main__':
         # 测试函数1
         def calculate_total_age_function(input_json):
             """
             从给定的JSON格式字符串（按'split'方向排列）中解析出DataFrame，计算所有人的年龄总和，并以JSON格式返回结果。
     ​
             参数:
             input_json (str): 包含个体数据的JSON格式字符串。
     ​
             返回:
             str: 所有人的年龄总和，以JSON格式返回。
             """
     ​
             # 将JSON字符串转换为DataFrame
             df = pd.read_json(input_json, orient='split')
     ​
             # 计算所有人的年龄总和
             total_age = df['Age'].sum()
     ​
             # 将结果转换为字符串形式，然后使用json.dumps()转换为JSON格式
             return json.dumps({"total_age": str(total_age)})
         
         # 测试函数2
         def calculate_married_count(input_json):
             """
             从给定的JSON格式字符串中解析出DataFrame，计算结婚人数，并以JSON格式返回结果。
     ​
             参数:
             input_json (str): 包含个体数据（其中包括婚姻状态）的JSON格式字符串。
     ​
             返回:
             str: 结婚人数，以JSON格式返回。
             """
     ​
             # 将JSON字符串转换为DataFrame
             df = pd.read_json(input_json, orient='split')
     ​
             # 计算结婚人数
             married_count = df[df['IsMarried'] == True ].shape[0]
     ​
             # 将结果转换为字符串形式，然后使用json.dumps()转换为JSON格式
             return json.dumps({"married_count": str(married_count)})
         
     ​
         functions_list = [calculate_total_age_function, calculate_married_count]
         generator = AutoFunctionGenerator(functions_list)
         function_descriptions = generator.auto_generate()

看下输出结果：
![](https://image.cubox.pro/cardImg/2023111018081017435/27564.jpg?imageMogr2/quality/90/ignore-error/1)

**因此，到这个阶段，只需正确编写功能函数并附上详细的函数说明，便无需进行其他操作。这对开发效率已经有了非常大的提升。**

**三、优化二：如何实现中间过程messages的自动拼接**
-------------------------------

在编写这个封装类时，需要考虑以下几个关键逻辑：

* 首先，需要判断是否有可用的外部函数库。如果没有，程序将执行标准的聊天流程。
* 其次，当存在外部函数库时，与大模型交互的调用参数会有所不同，需要适当地修改。
* 最后，需要精确地管理`messages`的两轮输入和输出，确保它们被正确地拼接，同时只返回最终的聊天回复。

这些逻辑共同确保了封装类能够灵活地处理各种聊天和功能调用场景，参考代码如下：

     class ChatConversation:
         """
         ChatConversation 类用于与 OpenAI GPT-3 模型进行聊天对话，并可选地调用外部功能函数。
         
         属性:
         - model (str): 使用的 OpenAI GPT模型名称。
         - messages (list): 存储与 GPT 模型之间的消息。
         - function_repository (dict): 存储可选的外部功能函数。
         
         方法:
         - __init__ : 初始化 ChatConversation 类。
         - add_functions : 添加外部功能函数到功能仓库。
         - _call_chat_model : 调用 OpenAI GPT 模型进行聊天。
         - run : 运行聊天会话并获取最终的响应。
         """
         def __init__(self, model="gpt-3.5-turbo-16k-0613"):
             """
             初始化ChatConversation类。
             """
             self.model = model
             self.messages = []
             self.function_repository = {}
         
         def add_functions(self, functions_list):
             """
             添加功能函数到功能仓库。
     ​
             参数:
             functions_list (list): 包含功能函数的列表。
             """
             self.function_repository = {func.__name__: func for func in functions_list}
     ​
         def _call_chat_model(self, functions=None, include_functions=False):
             """
             调用大模型。
     ​
             参数:
             functions (dict): 功能函数的描述。
             include_functions (bool): 是否包括功能函数和自动功能调用。
     ​
             返回:
             dict: 大模型的响应。
             """
             params = {
                 "model": self.model,
                 "messages": self.messages,
             }
     ​
             if include_functions:
                 params['functions'] = functions
                 params['function_call'] = "auto"
     ​
             try:
                 return openai.ChatCompletion.create(**params)
             except Exception as e:
                 print(f"Error calling chat model: {e}")
                 return None
     ​
     ​
         def run(self, functions_list=None):
             """
             运行聊天会话，可能包括外部功能函数调用。
             
             参数:
             functions_list (list): 包含功能函数的列表。如果为 None，则只进行常规对话。
     ​
             返回:
             str: 最终的聊天模型响应。
             """
             try:
                 # 如果不传入外部函数仓库，就进行常规的对话
                 if functions_list is None:
                     response = self._call_chat_model()
                     final_response = response["choices"][0]["message"]["content"]
                     return final_response
                 
                 else:
                 
                     # 添加功能函数到功能仓库
                     self.add_functions(functions_list)
     ​
                     # 如果存在外部的功能函数，生成每个功能函数对应的JSON Schema对象描述
                     functions = AutoFunctionGenerator(functions_list).auto_generate()
     ​
                     # 第一次调用大模型，获取到first reponse
                     response = self._call_chat_model(functions, include_functions=True)
                     response_message = response["choices"][0]["message"]
     ​
                     # 检查在first reponse中是否存在function_call，如果存在，说明需要调用到外部函数仓库
                     if "function_call" in response_message:
     ​
                         # 获取函数名
                         function_name = response_message["function_call"]["name"]
     ​
                         # 获取函数对象
                         function_call_exist = self.function_repository.get(function_name)
     ​
                         if not function_call_exist:
                             print(f"Function {function_name} not found in functions repository.")
                             return None
     ​
                         # 获取函数关键参数信息
                         function_args = json.loads(response_message["function_call"]["arguments"])
     ​
                         # 获取函数逻辑处理后的结果
                         function_response = function_call_exist(**function_args)
     ​
                         # messages = 原始输入 + first reponse + function_response
     ​
                         # messages中拼接first response消息
                         self.messages.append(response_message)  
                         # messages中拼接函数输出结果
                         self.messages.append(
                             {
                                 "role": "function",
                                 "name": function_name,
                                 "content": function_response,
                             }
                         )  
     ​
     ​
                         # 第二次调用模型
                         second_response = self._call_chat_model()
     ​
                         # 获取最终的计算结果
                         final_response = second_response["choices"][0]["message"]["content"]
     ​
                     else:
                         final_response = response_message["content"]
     ​
                     return final_response
     ​
             except Exception as e:
                 print(f"An error occurred: {e}")
                 return None

测试一下：

* 不带入外部函数仓库

     if __name__ == '__main__':
         # 创建一个ChatConversation实例
         conv = ChatConversation()
         
         conv.messages = [
          {"role": "system", "content": "你是一位优秀的数据分析师, 现在有这样一个数据集input_json：%s，数据集以JSON形式呈现" % df_complex_json},
          {"role": "user", "content": "请在数据集input_json上执行计算所有人年龄总和函数"}
      ]
         # 运行对话
         result = conv.run()
         print(result)

看下模型的输出：
![](https://image.cubox.pro/cardImg/2023111018081118706/73591.jpg?imageMogr2/quality/90/ignore-error/1)

这个结果就非常明显是模型自身的推理。

* 传入外部函数仓库

     functions_list = [calculate_total_age_function, calculate_married_count]
     ​
     if __name__ == '__main__':
         # 创建一个ChatConversation实例
         conv = ChatConversation()
         
         conv.messages = [
          {"role": "system", "content": "你是一位优秀的数据分析师, 现在有这样一个数据集input_json：%s，数据集以JSON形式呈现" % df_complex_json},
          {"role": "user", "content": "请在数据集input_json上执行计算所有人年龄总和函数"}
      ]
      #    # 运行对话
         result = conv.run(functions_list=functions_list)
         print(result)

再次看下模型推理结果：
![](https://image.cubox.pro/cardImg/2023111018081139621/18852.jpg?imageMogr2/quality/90/ignore-error/1)

**四、实践：开发一个专属对话小助理**
--------------------

基于上述两个封装类，就可以进行很多上层应用的开发，比如开发一个专属的对话小助理，可以这样做：

     def chat_with_assistant(functions_list=None, 
                             prompt="您好！", 
                             model="gpt-3.5-turbo-16k-0613", 
                             system_message="你是我的专属小助理"):
         
         # 创建ChatConversation实例
         chat_conversation = ChatConversation(model=model)
         
         # 添加系统消息和用户输入到messages列表中
         messages = [{"role": "system", "content": system_message}]
         messages.append({"role": "user", "content": prompt})
         chat_conversation.messages = messages
         
         while True:
             # 调用run方法处理对话，并得到模型的回答
             answer = chat_conversation.run(functions_list=functions_list)
             
             # 打印模型的回答
             print(f"模型回答: {answer}")
             
             # 添加模型的回答到messages列表中
             messages.append({"role": "assistant", "content": answer})
             
             # 询问用户是否还有其他问题
             user_input = input("如何没有其他问题，可以输入'退出'结束对话): ")
             
             # 如果用户输入'退出'，则结束对话
             if user_input.lower() == "退出":
                 break
             
             # 添加用户的问题到messages列表中
             messages.append({"role": "user", "content": user_input})
             
             # 更新ChatConversation实例的messages列表
             chat_conversation.messages = messages

通过传入functions_list测试是否可以调用外部函数，代码如下：

     # 外部函数列表里
     functions_list = [calculate_total_age_function, calculate_married_count]
     ​
     # 调用chat_with_assistant函数开始多轮对话
     chat_with_assistant(functions_list=functions_list)

看下模型对话过程：
![](https://image.cubox.pro/cardImg/2023111018081178496/46986.jpg?imageMogr2/quality/90/ignore-error/1)

**五、总结**
--------

本文首先概述了Function calling流程的优化思路，接着分别详细介绍了两种主要的优化方法：自动编写函数和编写自动应答函数。这两种优化方法可以显著提高Function calling的效率和实用性。最后，演示了如何实现一个多轮对话函数。

最后，感谢您阅读这篇文章！如果您觉得有所收获，别忘了点赞、收藏并关注我，这是我持续创作的动力。您有任何问题或建议，都可以在评论区留言，我会尽力回答并接受您的反馈。如果您希望了解某个特定主题，也欢迎告诉我，我会乐于创作与之相关的文章。谢谢您的支持，期待与您共同成长！

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7122596338075700911)
