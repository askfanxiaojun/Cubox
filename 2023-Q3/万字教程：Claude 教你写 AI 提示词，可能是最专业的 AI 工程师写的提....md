微信号
===

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/tfkpHOs2jhz3UORh0CvU4Q)op7418 歸藏的AI工具箱

前几天我发了一个Claude的提示工程师给出的五个提示词的书写建议的视频（放在了下面），他最后提议去看 Claude 的文档，我去看了一下文档里面还有很多更详细的技巧也比较成体系，所以这里就翻译整理了一下。这个文档和之前提到的 Open AI 的提示词书写文档可以相互补充和印证。  

整个文档包括两个部分第一部分是"提示设计"包括什么是提示（Prompt）和提示设计，提示是如何起作用的以及如何设计提示。第二部分是一些有用的提示词书写技巧。

歸藏2079

，赞 15


提示设计
----

介绍提示设计
------

Claude被训练成一名乐于助人、诚实且无害的助手。它习惯于对话，你可以用普通英语指导它。

你给 Claude 的指令的质量会对它的输出质量产生很大的影响，特别是对于复杂的任务。本提示设计指南将帮助你学习如何制作能够产生准确且一致结果的提示。

### Claude通过序列预测工作

Claude 是一个基于大型语言模型的会话助理。该模型使用你发送给它的所有文本（您的提示）以及迄今为止生成的所有文本来预测下一个最有帮助的标记。

这意味着 Claude 一次按顺序构造一组字符的响应。它在写入后无法返回并编辑其响应，除非你在后续提示中给它机会这样做。

Claude 也只能看到（并做出预测）其上下文窗口中的内容。它无法记住以前的对话，除非你它们放入提示中，并且它无法打开链接。

### 什么是提示（Prompt）？

给 Claude 的文本旨在引出或"提示"相关输出。提示通常采用问题或说明的形式。例如：

* 
* 

    Why is the sky blue?（为什么天空是蓝色的）


Claude 响应的文本称为"输出"。

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    由于空气中的分子散射太阳光，天空对我们来说呈蓝色。较短波长的光（蓝色）比较长波长的光（如红色和黄色）更容易散射，因此当我们抬头仰望天空时，我们看到的都是散射的蓝色光。这称为瑞利散射。天空的颜色根据太阳角度和空气中灰尘/水的量等条件而变化，但在晴朗的白天，光的蓝色波长对我们感知的颜色负有最大的影响。
    The sky appears blue to us due to how the molecules in the air scatter light from the sun. The shorter wavelength light (blue) scatters more easily than the longer wavelength light (like reds and yellows), so when we look up at the sky, what we see is all the scattered blue light. This is known as Rayleigh scattering. The color of the sky varies based on conditions like the angle of the sun and amount of dust/water in the air, but during the day with a clear sky, the blue wavelength of light is most responsible for the color we perceive.


### Human: / Assistant: 格式化

Claude 接受过训练，可以在人类用户 (Human:) 和 AI 助手 (Assistant:) 之间持续对话的过程中填写助理角色的文本。

通过 API 发送的提示必须包含\\n\\nHuman:和\\n\\nAssistant:作为发言者的信号。在 Slack 和我们的 Web 界面中，我们会自动为你添加这些内容。

例如，在控制台或 Claude-in-Slack 中，你可以直接询问 Claude：

* 
* 
* 
* 

    In one sentence, what is good about the color blue?
    用一句话说，蓝色的优点是什么？


它会回应：

* 
* 
* 
* 

    Blue is often seen as a calming and soothing color.
    蓝色通常被视为一种平静和舒缓的颜色。


如果你将相同的提示发送到 API，它可能会出现意想不到的行为，比如为提示中没有问及的内容提供答案。这是因为 Claude 被训练为在人类用户（Human:）和 AI 助理（Assistant:）之间的持续对话中扮演助理的角色，填充文本。如果没有这种结构，Claude 不知道该做什么或何时停止，因此它将继续延续已经存在的轨迹。

发送到 API 的提示应该是：

* 
* 
* 
* 

    Human: In one sentence, what is good about the color blue?
    Assistant:


为什么？Claude 已经使用 RLHF（强化学习与人类反馈）方法在此类数据上进行训练和微调，因此你需要在 API 中使用这些提示，以保持"在分布上"并获得预期的结果。重要的是要记住在 Human 和 Assistant 之前有两个新行，因为它是在这个基础上训练的。

### 提示词长度

Claude 能看到的最大提示长度是它的上下文窗口。Claude 的上下文窗口当前约为 75,000 个单词/\~100,000 个标记/\~340,000 个 Unicode 字符。

目前，当API Claude的上下文窗口超出范围时，它可能会返回不连贯的响应。我们为这种"尖锐的边缘"表示歉意。

构建提示
----

### 使用正确的格式

下面是这个只针对 Claude API 生效，正常使用不需要打这两个标签，使用正确的\\n\\nHuman:和\\n\\nAssistant:格式非常重要。

Claude被训练成一名对话代理，使用这些特殊的标记来标记谁在说话。\\n\\nHuman:（你）提出问题或给出指示，\\n\\nAssistant:（ Claude ）做出回应。

因此，我们可以开始像这样编写提示：

* 
* 
* 
* 

    Human:
    Assistant:


我们将在这两个标记之间填充实际的提示文本。

### 很好地描述任务

在描述任务时，最好为 Claude 提供尽可能多的背景和细节，以及正确完成任务的任何规则。

Claude就像是第一天上班的实习生。Claude和那个实习生一样，很想帮助你，但对你、你的组织或任务还不了解。如果你提供清晰、明确的说明以及所有必要的细节，那么它更有可能满足你的期望。

比如下面这个示例，我们将要求 Claude 帮助我们从给定文本中删除任何个人身份信息。

我们可以尝试使用这个提示：

* 
* 
* 
* 

    错误的提示：请删除此文本中的所有个人身份信息：{{YOUR TEXT HERE}}Please remove all personally identifiable information from this text: {{YOUR TEXT HERE}}


下面是一些不太好的输出结果：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    以下是删除了所有个人身份信息的文本：患者的医疗报告[已编辑]\：[已编辑]患者出现 IPSALATERAL...
    Here is the text with all personally identifiable information removed:
    MEDICAL REPORT FOR PATIENT [REDACTED]\:  [REDACTED]  PATIENT PRESENTED WITH IPSALATERAL...


* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    以下是删除了所有个人身份信息的文本：乔：嗨[名字1]！[姓名 1]\：嗨，[姓名 2]！你过来吗？[姓名2]\：是的！嘿，我，呃，忘记你住在哪里了。[姓名1]\：没问题！它是[地址]、[城市] [州] [邮政编码]。[姓名2]\：明白了，谢谢！
    Here is the text with all personally identifiable information removed:
    Joe: Hi [Name 1]!  [Name 1]\: Hi [Name 2]!  Are you coming over?  [Name 2]\: Yup!  Hey I, uh, forgot where you live.  [Name 1]\: No problem!  It's [Address], [City] [State] [Zip Code].  [Name 2]\: Got it, thanks!


如果我们只想以任何方式删除 个人身份信息（尽管它漏掉了一个名称），那么此提示就可以正常工作。对于少量文本来说可能已经足够了，可以在处理后手动检查以纠正错误。

但是，如果我们需要 Claude 以特定格式进行响应，并通过各种输入一遍又一遍地正确执行任务，那么我们应该在提示中添加更多详细信息,下面是一个好的提示示例：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    我们希望通过从文本中删除所有个人身份信息来对某些文本进行去识别化，以便可以与外部承包商安全地共享。将姓名、电话号码、家庭地址和电子邮件地址等 PII 替换为 XXX 非常重要。这是你应该处理的文本：{{YOUR TEXT HERE}}
    We want to de-identify some text by removing all personally identifiable information from this text so that it can be shared safely with external contractors.
    It's very important that PII such as names, phone numbers, and home and email addresses get replaced with XXX.
    Here is the text you should process: {{YOUR TEXT HERE}}


在这个修订版的提示中，我们：

* 提供了上下文（例如为什么我们希望完成任务）

* 定义术语（PII = 姓名、电话号码、地址）

* 给出有关 Claude 应如何完成任务的具体细节（将 PII 替换为 XXX）

一般来说，Claude对您的请求了解的细节越多，就越能更好地预测正确的响应。

### 标记提示的不同部分

XML 标签，如\<tag\>这些\</tag\>有助于划分提示中的一些重要部分，比如规则、示例或处理的输入文本。Claude 经过微调，特别关注由 XML 标签创建的结构。

在我们的例子中，我们可以使用XML标签清楚地标记Claude需要去标识化文本的开始和结束。

部分提示：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    Here is the text, inside
          XML tags.
    {{TEXT}}

    这是
          XML 标记内的文本。
    {{文本}}



文本替换：通常，你的提示实际上是您希望反复使用的提示模板，其中指令保持不变，但要处理的文本会随时间变化。你可以将用于要处理的可变文本的占位符（如{{TEXT}}）放入提示中，然后编写一些代码以在运行时替换它。

我们还可以要求 Claude 在其响应中使用 XML 标签。这样做可以轻松地在自动处理输出的设置中提取关键信息。Claude 天生就很健谈，因此请求这些输出 XML 标记有助于将响应本身与 Claude 对响应的评论分开。

好的提示词：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    我们希望通过从文本中删除所有个人身份信息来对某些文本进行去识别化，以便可以与外部承包商安全地共享。将姓名、电话号码、家庭地址和电子邮件地址等 PII 替换为 XXX 非常重要。这是
          XML 标记内的文本。
    {{文本}}
    请将已删除 PII 的去识别化文本版本放入
          XML 标记中。
    We want to de-identify some text by removing all personally identifiable information from this text so that it can be shared safely with external contractors.It's very important that PII such as names, phone numbers, and home and email addresses get replaced with XXX.Here is the text, inside
          XML tags.
    {{TEXT}}
    Please put your de-identified version of the text with PII removed in
          XML tags.


至此，该提示已经构建得相当好，并准备好使用各种输入进行测试。但是，如果 Claude 的某些测试失败，请考虑添加以下提示组件。

### 示例（可选）

通过在提示中添加一些示例，可以让 Claude 更好地了解如何正确执行任务。这并不总是需要的，但可以大大提高准确性和一致性。如果你确实添加了示例，最好使用 \<example\>\</example\> 标签清楚地标记它们，以便将它们与你希望 Claude 处理的文本区分开来。

提供示例的一种方法是以先前对话的形式。在给 Claude 时使用不同的对话定界符，例如"H:"而不是"Human:"和"A:"而不是"Assistant:"使用此方法的示例。这有助于防止示例与对话中的其他对话混淆。

下面是部分提示：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    这是一个例子：
    H：
          答：<回复>XXX 是 Mercy Health 医疗中心的心脏病专家。您可以通过 XXX-XXX-XXXX 或 XXX@XXX 联系他。

    Here is an example:
    H:
          A:
          
           XXX is a cardiologist at Mercy Health Medical Center. He can be reached at XXX-XXX-XXXX or XXX@XXX.
          



为什么是H：和A：？\\n\\n人类：和\\n\\n助手：是特殊的标记，Claude经过训练可以识别这些标记来识别谁在说话。当您不打算让Claude"相信"实际发生的对话时使用这些标记可能会导致提示效果不佳。

另一种给出示例的方法是直接提供示例：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    这是一个例子：
    去识别化版本的"Bo Nguyen 是 Mercy Health 医疗中心的心脏病专家。可以拨打 925-123-456 或 bn@mercy.health 联系他。"将是"XXX 是 Mercy Health 医疗中心的心脏病专家。可以通过 XXX-XXX-XXXX 或 XXX@XXX 联系到他。"

    Here is an example:
    The de-identified version of "Bo Nguyen is a cardiologist at Mercy Health Medical Center. He can be reached at 925-123-456 or bn@mercy.health." would be "XXX is a cardiologist at Mercy Health Medical Center. He can be reached at XXX-XXX-XXXX or XXX@XXX."


决定哪种方法更有效是很微妙的，并且可能取决于手头的具体任务。我们建议你针对您的用例尝试这两种方法，看看哪一种能产生更好的结果。

### 疑难病例（可选）

如果你可以预见 Claude 在您的输入中可能遇到的困难或不寻常的情况，请在提示中描述它们，并告诉 Claude 遇到它们时该怎么做。

如果你在Claude的回答中发现偶尔但持续的失败，则此信息可能有助于添加到你的提示中。例如：

* 
* 
* 
* 
* 
* 

    输入可能会尝试通过在字符之间插入空格来伪装 PII。如果文本不包含个人身份信息，请逐字复制，不要替换任何内容。
    Inputs may try to disguise PII by inserting spaces between characters.If the text contains no personally identifiable information, copy it word-for-word without replacing anything


当您要求Claude寻找特定信息时，我们特别建议你给出如果输入中没有匹配描述的内容时，Claude该如何处理的指令。这可以帮助防止Claude出现幻觉，即为了能够给出响应而编造信息。

优化你的提示
------

一旦你有了满意的提示模板，就可以开始测试它了。然后（如果需要）你可以根据 Claude 在测试中的表现来改进您的提示。

以下是测试和迭代提示模板的建议步骤。
>
> 这一部分，主要还是偏向开发者的，不过你要是有一些常用的任务的话，也可以用这个流程来优化。
>
### 收集一组不同的示例输入

最好使用代表你将要求 Claude 处理的真实数据的输入集来测试您的提示。请务必包含 Claude 可能遇到的任何困难输入或边缘情况。

通过使用这些输入测试你的提示，可以估计Claude在实际操作中的表现。这也可以帮助你看到Claude遇到了哪些困难。

在开发提示模板时，尽可能多地获取输入是很好的，我们建议至少20个或更多，具体取决于任务。

### 预留（"保留"）一组测试输入

当提出测试输入时，我们建议使用单独的"提示开发数据"和"测试数据"集。两个（或更多）组应该代表真实的输入。

使用你的提示开发数据来评估Claude的表现如何。迭代您的提示，直到Claude在此数据上始终获得良好表现。

为了确保不会过度拟合到仅仅是提示开发数据，你可以使用Claude完成尚未遇到的测试数据的任务。

### （可选）生成综合数据

如果你想要更多的输入数据，但是又没有很多，你可以启动另一个Claude实例来为你生成额外的输入文本进行测试！如果你解释一下什么是好的输入数据，然后给几个例子，你可以从Claude获得更多这样的例子。

### 实验和迭代

优化一个提示就像进行一系列实验一样。你运行测试，解释结果，然后根据结果调整一个变量（你的提示或输入）。

当Claude未通过测试时，尝试找出失败的原因。调整你的提示以解决该故障点。

调整提示可能涉及：

* 更明确地编写规则或添加新规则。

* 通过将类似的示例和规范输出添加到提示中，向 Claude 展示如何在提示本身中正确处理示例。

当Claude在新提示下对某一类输入做出持续良好表现时，尝试用另一种输入类型进行测试。务必尝试边缘情况。

在提示中添加规则和示例，直到你在代表性输入集上获得良好的性能。我们建议还执行"保留测试"。

### 奖励：请Claude评估其输出

可以使用 Claude 来"自我评估"它之前给出的答案。

比如：

* 如果你认为模型可能犯了错误，请让模型检查其工作

* 添加一个额外的尽职调查步骤到一个任务

* 根据你的指示，将响应分类为好或坏，或者说出它更喜欢两个初始响应中的哪一个以及原因（例如，以便你可以决定使用哪一个）

在下面的示例中，我们要求 Claude 找出给定文本中的任何语法错误。

提示词：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    这是一篇文章，包含在 
       
        
       
           
         标签中：
       
        
       
           

       
        
       
           
        

       
        
       
           {{文章}}
    请指出文章中的任何语法错误。
    Here is an article, contained in 
       
        
       
           
         tags:
       
        
       
           


       
        
       
           
        

       
        
       
           {{ARTICLE}}

    Please identify any grammatical errors in the article.


输出结果：

* 
* 
* 
* 
* 
* 

    1. There is a missing fullstop in the first sentence.2. The word "their" is misspelled as "they're" in the third sentence.
    1. 第一句缺少句号。2. 第三句中的"their"一词被错误地拼写为"they're"。


如果 Claude 在第一次尝试中未能识别出一些错误，你可以尝试添加第二遍：

提示词：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    这是一篇文章，包含在 
       
        
       
           
         标签中：
       
        
       
           

       
        
       
           
        

       
        
       
           {{文章}}

       
        
       
           
        

       
        
       
           请指出文章中缺少以下列表中的任何语法错误：
    1. 第一句缺少句号。2. 第三句中的"their"一词被错误地拼写为"they're"。
    如果列表中没有遗漏文章中的任何错误，请说"没有其他错误"。
    Here is an article, contained in 
       
        
       
           
         tags:
       
        
       
           


       
        
       
           
        

       
        
       
           {{ARTICLE}}

    Please identify any grammatical errors in the article that are missing from the following list:
    1. There is a missing fullstop in the first sentence.2. The word "their" is misspelled as "they're" in the third sentence.

    If there are no errors in the article that are missing from the list, say "There are no additional errors."


你可以通过下面会说到的"提示链接"自动执行这样的"额外注意"步骤。

避免产生幻觉：当要求Claude在文本中查找某物时，最好"给它一个出路"，即描述如果在提示中没有匹配描述的内容时该如何做。这可以帮助防止它制造出一些东西以便给出答案。

有用的提示技巧
-------

让Claude说"我不知道"以防止出现幻觉
---------------------

虽然Claude被训练成一个诚实的助手，但它仍然偶尔会产生"幻觉"------编造不真实的事实或细节，或者在输入中"找到"实际上并不存在的东西，以尽可能提供帮助。。

防止这种情况的一种方法是明确允许 Claude 在不知道你问题的答案时说"我不知道"。

你可以把 Claude 看作是非常字面上地去做你要求它做的事情。所以如果你问它一个问题而它不知道答案，它会"努力帮助你"，这就涉及到了幻觉。它没有人类所具有的隐含的社会语境，即说谎比说"我不知道"要糟糕得多。

例如，下面这个错误的提示：

* 
* 
* 
* 

    What is the heaviest hippo ever recorded?
    什么是有记录以来最重的河马？


错误的输出：

* 
* 
* 
* 
* 
* 
* 
* 
* 

    The heaviest hippo ever recorded was a bull named Hubert, who weighed 5,000 kg or 11,023 lbs. Hubert was measured in Kenya in the early 20th century. Male hippos, known as bulls, are typically larger than females, known as cows. Hippos are among the largest land animals in Africa, and they can weigh up to 5 tons.
    Hubert，一头公河马，是迄今为止记录中最重的，重达5000公斤（11,023磅），于20世纪初在肯尼亚被测量。公河马通常比母河马（又称母牛）更大，它们是非洲最大的陆地动物之一，体重可达5吨。


好的提示：

* 
* 
* 
* 
* 
* 
* 
* 

    Answer the following question only if you know the answer or can make a well-informed guess; otherwise tell me you don't know it.
    What was the heaviest hippo ever recorded?
    如果你知道答案或可以做出精确的猜测，请回答以下问题；否则告诉我你不知道。有史以来最重的河马是多少？


好的输出：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    I'm sorry, I don't know the exact weight of the heaviest hippo ever recorded. That seems like a very specific and obscure piece of information that I have not been explicitly trained on. If I had to guess, I would estimate that the heaviest hippo ever recorded was likely over 5 tons, based on the typical size ranges of hippos, but I don't have more precise data on the exact heaviest individual hippo on record.
    抱歉，我不知道最重的河马记录重量的准确数字。这似乎是一个非常特殊而模糊的信息，我没有被明确训练。如果我要猜，我会估计最重的河马记录可能超过5吨，基于河马的典型尺寸范围，但我没有更精确的关于记录中最重的个体河马的数据。


在回应之前给Claude"思考"的空间
-------------------

我们已经讨论了许多技术来削减Claude经常伴随着响应而包含的任何"闲谈"，解释或序言。但也有情况下明确指示Claude去生成额外的文本，它可以认真思考问题。

例如，以下是提示的一部分，旨在通过写下常见问题解答文档中的相关引用来让 Claude 需要"思考"问题：

下面是部分提示：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    When you reply, first find exact quotes in the FAQ relevant to the user's question and write them down word for word inside
          XML tags.  This is a space for you to write down relevant content and will not be shown to the user.  Once you are done extracting relevant quotes, answer the question.  Put your answer to the user inside
          XML tags.
    当你回复时，首先在FAQ中找到与用户问题完全相符的引用，并逐字将其写入
          XML标签中。这是你写下相关内容的空间，不会显示给用户。完成提取相关引用后，回答问题。将你的答案放入
          XML标签中。


Claude 通过序列预测工作。通过首先提示它记录相关的背景信息（在本例中是引用），我们可以增加它预测相关答案的机会。

Claude的响应中的XML标签仍然可以自动处理它并删除"推理"部分。

让 Claude 一步一步思考
---------------

如果你要求 Claude 执行一项包含许多子任务的复杂任务，那么单独列出子任务会很有帮助。

当你自己不清楚子任务时，也就是你正在要求 Claude 解决问题，你可以通过明确地告诉 Claude 逐步思考来显著提高回答的推理和准确性。

为了获得最佳效果，我们建议将此请求放在提示的另一部分。

错误的提示：

* 
* 
* 
* 
* 
* 

    I have two pet cats. One of them is missing a leg. The other one has a normal number of legs for a cat to have. In total, how many legs do my cats have? Think step-by-step.
    我有两只宠物猫，其中一只缺少一条腿，另一只有正常的猫腿数量，总共我的猫有多少条腿？一步一步思考。


好的提示：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    Human: I have two pet cats. One of them is missing a leg. The other one has a normal number of legs for a cat to have. In total, how many legs do my cats have?Assistant: Can I think step-by-step?Human: Yes, please do.Assistant:
    人类：我有两只宠物猫。其中一只缺少一条腿。另一只有正常数量的腿。总共我的猫有多少条腿？助手：我可以一步一步地思考吗？人类：是的，请这么做。助手：我的猫有三条腿。


我自己也试了一下这个提示词，Claude 还展示了思考过程：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    我来用中文解释一下逻辑:
    你有2只宠物猫其中一只猫缺了一条腿正常情况下,猫有4条腿所以缺腿的那只猫有3条腿另一只猫有正常数目的腿,也就是4条所以一只猫有3条腿,另一只有4条腿3 + 4 = 7因此,你的2只猫总共有7条腿。
    这样理解是否清楚?如果需要我解释得更详细一点,请告诉我


把话放到克劳德嘴里：你可以使用\\n\\nHuman: 和 \\n\\nAssistant: 的格式在提示中给Claude更多的指令，以前的对话形式（即使没有发生）。Claude将从最后一个\\n\\nAssistant: 标记继续对话。

将复杂的任务分解为子任务
------------

Claude 在由多个子任务组成的"复杂"任务上表现不佳。如果你已经知道这些子任务是什么（即你理解问题很好），你可以通过将提示分解为步骤来帮助 Claude。

错误的提示：

* 
* 
* 
* 
* 
* 

    I want you to write an essay about the statement {{STATEMENT}}, with three topic sentences arguing for the statement, three topic sentences arguing against the statement, and a conclusion at the end.
    根据{{STATEMENT}}写一篇论文，包括三个支持该陈述的主题句，三个反对该陈述的主题句，以及最后的结论。


好的提示：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    Please follow these steps:1. Write three topic sentences arguing for {{STATEMENT}}.2. Write three topic sentences arguing against {{STATEMENT}}.3. Write an essay by expanding each topic sentence from Steps 1 and 2, and adding a conclusion to synthesize the arguments. Please enclose the essay in 
          tags.
    请按照以下步骤操作：	1.	写出三个支持{{STATEMENT}}的主题句。	2.	写出三个反对{{STATEMENT}}的主题句。	3.	根据步骤1和2的主题句，扩展写出一篇文章，并添加一个结论来综合提出的论点。请将文章用
          标签括起来。


更进一步：如果你无法通过将提示分解为子任务获得可靠的结果，则可能需要将其拆分为多个提示。前面的输出可以在过程中被提供给其他提示，这称为提示链接。

提示链接（Prompt Chaining）
---------------------

另一种完成具有已知和明确分解任务的方法是将 Claude 的响应输入到另一个提示的输入中。这种技术称为提示链接。

提示链接可以使你通过将多个较小和较简单的提示传递给Claude而完成一项复杂任务，而不是一个非常长且详细的提示。它有时可以比将任务的所有子任务放在单个提示中更有效。

将长而复杂的提示变成提示链有几个优点：

* 你可以编写不太复杂的指令。

* 你可以隔离 Claude 遇到问题的部分问题，以集中精力进行故障排除。

* 你可以分阶段检查 Claude 的输出，而不仅仅是在最后检查。

以下是提示链接的一些用例。

### 使用文档和引用回答问题

在这个例子中，我们给Claude一份文档，以及我们想要它根据文档回答的问题。让Claude使用文档文本和相关引用来回答问题，通常比单独使用文本或引用更准确。

请Claude提取与我们问题相关的文件引用：

提示 1：提取与问题相关的直接文档引用：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    Here is a document, in
          XML tags:

    {{DOCUMENT}}

    Please extract, word-for-word, any quotes relevant to the question {{QUESTION}}. Please enclose the full list of quotes in
          XML tags. If there are no quotes in this document that seem relevant to this question, please say "I can't find any relevant quotes".
    请从以下文档中提取与问题{{QUESTION}}相关的引用，并将完整的引用列表放在
          XML标签中。如果没有与此问题相关的引用，请说"我找不到任何相关的引用"。


然后我们可以将 Claude 给我们的引号（包括\<quotes\>\</quotes\>XML 标记）替换为另一个提示：

提示 2：使用文档和引用来回答问题

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    I want you to use a document and relevant quotes from the document to answer the question "{{QUESTION}}"
    Here is the document, in
          XML tags:
    {{DOCUMENT}}

    Here are direct quotes from the document that are most relevant to the question "{{QUESTION}}": {{QUOTES}}
    Please use these to construct an answer to the question "{{QUESTION}}" as though you were answering the question directly. Ensure that your answer is accurate and doesn't contain any information not directly supported by the document or the quotes.
    请使用文档和文档中相关的引用来回答问题"{{QUESTION}}"。以下是XML标签
          中的文档：
    {{DOCUMENT}}
    以下是与问题"{{QUESTION}}"最相关的文档中的直接引用：{{QUOTES}}请使用这些内容来构建一个对问题"{{QUESTION}}"的回答，就像你直接回答问题一样。确保你的答案准确，不包含文档或引用中没有直接支持的任何信息。


### 响应验证/额外注意

提示链接也可以方便地自动要求 Claude 重新检查之前对提示的响应。

使用 Ask Claude 中的示例来评估其输出：

提示 1：识别语法错误的第一步

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    Here is an article, contained in 
       
        
       
           
         tags:
       
        
       
           


       
        
       
           
        

       
        
       
           {{ARTICLE}}

    Please identify any grammatical errors in the article. Please only respond with the list of errors, and nothing else. If there are no grammatical errors, say "There are no errors."
    这是一篇文章，包含在 
       
        
       
           
         标签中：
       
        
       
           

       
        
       
           
        

       
        
       
           {{ARTICLE}}
    请指出文章中的任何语法错误。请只回复错误列表，不要回复其他内容。如果没有语法错误，请说"没有错误"。


我们可以将提示 1 中 Claude 的响应替换为提示 2 中的{{ERRORS}}占位符：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    Here is an article, contained in 
       
        
       
           
         tags:
       
        
       
           


       
        
       
           
        

       
        
       
           {{ARTICLE}}

    Please identify any grammatical errors in the article that are missing from the following list:
    {{ERRORS}}

    If there are no errors in the article that are missing from the list, say "There are no additional errors."
    请在以下列表中识别文章中缺失的任何语法错误：
    {{ERRORS}}
    如果文章中没有缺少列表中的错误，请说"没有其他错误。


### 并行任务

多步骤提示可以并行、串行或组合运行。

让我们说，我们想要以三个不同的水平向读者解释某个概念：一年级学生、八年级学生和大学新生。此外，我们希望 Claude 先写一个大纲，然后将这个大纲扩展成一个完整的解释。

我们可以从以下提示模板开始：

提示 1：为指定的阅读水平写一个关于概念的大纲

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    Here is a concept: {{CONCEPT}}
    I want you to write a three sentence outline of an essay about this concept that is appropriate for this level of reader: {{LEVEL}}
    Please only respond with your outline, one sentence per line, in
          XML tags. Don't say anything else.
    请描述一下概念：{{CONCEPT}}为适合{{LEVEL}}程度的读者，请写出一篇关于这个概念的三句话大纲请仅使用
          XML标签，一句话一行，不要说其他内容。


我们已经知道了我们想要为学生编写解释的水平，因此我们可以为每个阅读水平创建三个不同版本的提示（一个提示一个阅读水平）。然后，我们可以给 Claude 一个概念，并让每个阅读水平的提示并行运行以生成三个大纲。

随后，我们可以将 Claude 生成的每个提纲（包括\<outline\> \</ outline\>XML标签）传递给另一组三个提示，其阅读水平不同。这第二组提示可以再次并行运行，将提纲中的每个句子扩展为一个段落。

提示 2：扩展提示1生成的概要

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    Here is an outline:{{OUTLINE}}
    Please expand each sentence in the outline into a paragraph. Use each sentence word-for-word as the first sentence in its corresponding paragraph. Make sure to write at a level appropriate for this type of reader: {{TYPE}}
    这是一个概要：{{OUTLINE}}请将概要中的每句话拓展成一个段落。使用每句话的原词作为相应段落的第一句。请确保用适合这种读者的水平写作：{{TYPE}}


检查Claude的理解力
------------

确定Claude是否理解你的指示的最佳方法是询问Claude。

下面是提示词：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    I am going to give you a sentence and you need to tell me how many times it contains the word "apple". For example, if I say "I would like an apple" then the answer is "1" because the word "apple" is in the sentence once. You can reason through or explain anything you'd like before responding, but make sure at the very end, you end your answer with just the final answer in brackets, like this: [1].
    Do you understand the instructions?
    我给你一句话，你需要告诉我里面有多少个"苹果"字。例如，如果我说"我想要一个苹果"，那么答案就是"1"，因为句子中只有一次出现了"苹果"这个词。在最后给出答案之前，你可以用任何方式解释，但是最后一定要用括号把答案括起来，比如这样：[1]。
    你明白了吗？


它通常会通过向你解释任务来做出回应，下面是输出结果。

* 
* 
* 
* 
* 
* 
* 
* 

    Yes, I understand. For a given sentence, I should count how many times the word "apple" occurs in the sentence and provide the count as my response in brackets. For example, given the input "I would like an apple", my response should be "[1]".
    是的，我明白。对于给定的句子，我应该计算出单词"苹果"在句子中出现的次数，并将计数结果用括号括起来作为我的回复。例如，给定输入"我想要一个苹果"，我的回复应该是"[1]"


### 奖励：使用Claude的解释来扩展你的提示

如果 Claude 给出了正确的任务解释，您可以使用该响应来扩展您的提示。以这种方式重复指示可以提高Claude的表现。

提示词：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    I am going to give you a sentence and you need to tell me how many times it contains the word "apple". For example, if I say "I would like an apple" then the answer is "1" because the word "apple" is in the sentence once. You can reason through or explain anything you'd like before responding, but make sure at the very end, you end your answer with just the final answer in brackets, like this: [1].
    Do you understand the instructions?
    Assistant: Yes, I understand. For a given sentence, I should count how many times the word "apple" occurs in the sentence and provide the count as my response in brackets. For example, given the input "I would like an apple", my response should be "[1]".
    Human: Correct. Here is the sentence: I need one apple to bake an apple pie, and another apple to keep for later.
    人类：我给你一个句子，你需要告诉我它里面有多少个"苹果"这个词。例如，如果我说"我想要一个苹果"，那么答案是"1"，因为句子里只有一个"苹果"这个词。在最后给出答案之前，你可以自由推理或者解释，但是最后一定要在括号里给出最终的答案，比如这样：[1]。你明白指令吗？
    助手：是的，我明白。对于给定的句子，我应该计算它里面有多少个"苹果"这个词，然后以括号里的数字作为我的回答。例如，对于输入"我想要一个苹果"，我的回答应该是"[1]"。
    人类：正确。这里有一个句子：我需要一个苹果来烤苹果派，还有一个苹果留着以后吃。


参考之前的对话：Claude无法记住以前的对话或看到当前上下文窗口之外的任何内容。您可以通过使用\\n\\nHuman: 和 \\n\\nAssistant: 格式在提示中包含先前对话的内容。

请Claude重写
---------

如果Claude的回答接近但不完全符合你的要求，你可以要求Claude重写它。

在 Slack 中，只需要告诉 Claude 说"再试一次"（当它给出不满意的答案时）即可。（如果你给出更多指示，比如"请重写，包含更多细节"，它的重写效果会更好。）除非你首先发送一个/reset命令，否则你的消息将被添加到现有的上下文窗口中。这样 Claude 就可以将其先前的答案作为提示的一部分进行处理。

避免产生幻觉：当使用Claude-in-Slack时，在要求重写之前不要发送/reset命令，除非你打算明确将Claude之前生成的响应传递到提示中。Claude往往会在没有文本可以重写时制造不相关的文本。

如果通过 API 发送提示（包括在 Sheets 中使用 Claude 调用 CLAUDE 或 CLAUDEFREE 函数），则必须始终在提示中包含之前生成的文本。这是一个提示模板示例：

好的提示示例：

* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 
* 

    Human: Here's a paragraph:
    {{PARAGRAPH}}

    I'd like you to rewrite it using the following instructions:
    {{INSTRUCTIONS}}

    Please put your rewrite in
          tags.
    Assistant:
          
    Human: 这里有一段：
    {{PARAGRAPH}}
    我希望你按照以下说明重写它：
    {{INSTRUCTIONS}}
    请将你的重写放在
          标记中。Assistant:
          

如果需要低量使用，可以将要重写的段落粘贴到{{PARAGRAPH}}的位置。为了自动化，可以设置一个提示链，以便Claude对先前提示的响应可以替换{{PARAGRAPH}}占位符中的内容。

如果你在Sheets中使用Claude，则可以在Sheet中设置行，以便在每行中将不同的指令集替换为{{INSTRUCTIONS}}占位符。通过这种方式，您可以一次生成多种类型的重写。
>
> 好了这就是 Claude 文档中关于提示工程的主要内容，通过这次详细翻译我也对之前很多不太理解的概念有了一些了解，比如"提示链"。里面还有一些其他关于开发的补充信息我没有翻译，感兴趣的可以去看英文原文。
>
整理不易，各位觉得有帮助可以帮忙点个"赞"或者"在看"，感谢。

原文链接：

https://docs.anthropic.com/claude/docs/constructing-a-prompt

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7098350888778992441)
