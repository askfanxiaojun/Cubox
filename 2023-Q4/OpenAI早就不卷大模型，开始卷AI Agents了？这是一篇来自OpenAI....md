OpenAI早就不卷大模型，开始卷AI Agents了？这是一篇来自OpenAI应用研究主管关于Agent的万字长文
==========================================================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/640634046)AI的潜意识

> "如果一篇论文提出了某种不同的训练方法，OpenAI内部的Slack上会嗤之以鼻，因为这些都是我们玩剩下的。但是当新的AI Agents论文出来的时候，我们才会认真兴奋的讨论。"

最近Andrej Karpathy这位OpenAI联合创始人在一个开发者活动上发表简短讲话，谈论了自己和OpenAI内部对AI Agents （人工智能代理人）的看法。
![](https://image.cubox.pro/cardImg/2023111518272862954/76508.jpg?imageMogr2/quality/90/ignore-error/1)

Andrej Karpathy对比了过去开发AI Agent的困难和现在新技术工具下开发的新机会，他还不忘调侃自己在特斯拉的工作，是"被自动驾驶分了心"，他认为自动驾驶和VR都是糟糕的AI Agents的例子。

另一方面，Andrej Karpathy认为普通人、创业者和极客在构建AI Agents方面相比OpenAI这样的公司更有优势，大家目前处于平等竞争的状态，因此他很期待看到这方面的成果。Karpathy完整的分享视频在文章结尾。

6月27日，OpenAI应用研究主管LilianWeng撰写了一篇万字长文，其中还有部分章节是ChatGPT帮她起草的。她提出Agent = LLM（大型语言模型）+ 记忆 + 规划技能 + 工具使用，并对Agent的每个模块的功能作了详细的说明，最后她非常看好Agent未来的应用前景，但也表明挑战无处不在。
![](https://image.cubox.pro/cardImg/2023111518272880646/25058.jpg?imageMogr2/quality/90/ignore-error/1)

我把这篇长文翻译了下，并加上自己的一些理解和体会，接下来让我们一起看看大佬都说了些什么吧！文章篇幅较长，希望小伙们可以耐心看完。原文链接在文章结尾。

以LLM（大型语言模型）作为其核心控制器构建代理是一个很酷的概念。几个概念验证演示，如AutoGPT、GPT-Engineer和BabyAGI，都是鼓舞人心的例子。LLM的潜力不仅限于生成写作、故事、论文和程序等优秀的副本，它可以被构建为一个强大的通用问题解决器。

**代理系统概述**
----------

在以LLM驱动的自主代理系统中，LLM作为代理的大脑，辅以几个关键组件：

* **规划**
  * 子目标和分解：代理将大型任务分解为较小，可管理的子目标，从而有效地处理复杂的任务。
  * 反思和改进：代理可以对过去的行动进行自我批评和自我反思，从错误中学习并改进未来的步骤，从而提高最终结果的质量
* **记忆**
  * 我将所有的上下文学习（参考Prompt Engineering）都看成是利用模型的短期记忆来学习。
  * 长期记忆：长期记忆为代理提供了长期存储和召回（无限）信息的能力，它们通常通过利用外部的向量存储和快速检索来存储和召回（无限）信息。
* **使用工具**
  * 代理通过学会调用外部API来获取模型权重（通常在预训练后很难修改）中缺少的额外信息，包括当前信息，代码执行能力，访问专有信息源等。  

![](https://image.cubox.pro/cardImg/2023111518272938762/71087.jpg?imageMogr2/quality/90/ignore-error/1)

### **组件一：计划**

复杂的任务通常涉及许多步骤。代理需要知道具体的任务是什么并开始提前计划。

**任务分解**

**「思维链** （CoT，Chain of thought）**」**已成为一种标准prompting技术，用于增强复杂任务上的模型性能。指示该模型"逐步思考"，以利用更多的测试时间计算将困难任务分解为更小，更简单的步骤。COT将重大任务转换为多个可管理的任务，并将注意力放到对模型思考过程的可解释性中。

**「思维树** （Tree of Thoughts）**」**通过探索每个步骤的多种推理可能性来扩展COT。它首先将问题分解为多个思考步骤，并且每个步骤都生成多个想法，从而可以创建一个树形结构。思维树的搜索过程可以是BFS（广度优先搜索）或DFS（深度优先搜索），每个状态都由分类器（通过prompt）或多数投票决定。

拆解任务可以使用三种方式：

（1）使用简单的提示让LLM拆解，例如："XYZ的步骤"，"实现XYZ的子目标是什么？"。

（2）使用特定任务的指令，例如"写一个故事大纲。"用于写小说。

（3）人类自己拆解。

另一种截然不同的方法是 **LLM+P**，它涉及依赖外部经典规划器来进行长期规划。该方法利用规划领域定义语言（PDDL）作为描述规划问题的中间接口。在此过程中，LLM (1) 将问题转化为"问题PDDL"，然后 (2) 请求经典规划器基于现有的"领域 PDDL"生成 PDDL规划，最后 (3) 将 PDDL 规划转化回自然语言。本质上，规划步骤被外包给外部工具，假设特定领域的PDDL和合适的规划器都是可用的，这种假设在某些机器人设置中很常见，但在许多其他领域并不常见。

**反思**

自我反思是一个很重要的方面，它允许自主代理通过改进过去的行动决策和纠正以前的错误来进行迭代改进。它在不可避免的出现试错的现实任务中发挥着至关重要的作用。

**「ReAct」**通过将行动空间扩展为特定任务的离散行动和语言空间的组合，将推理和行动集成到 LLM中。前者使 LLM 能够与环境交互（例如使用维基百科搜索API），后者能够促使LLM 生成自然语言的推理轨迹。

ReAct提示模板包括LLM思考的明确步骤，大致格式为：

    Thought: ...
    Action: ...
    Observation: ...
    ... (Repeated many times)

![](https://image.cubox.pro/cardImg/2023111518272931145/35139.jpg?imageMogr2/quality/90/ignore-error/1)

在知识密集型任务和决策任务的两个实验中，ReAct的表现优于仅包含行动的基准模型，其中基准模型去除了"思考：..."步骤。

**「反思」**是一个框架，它为代理提供动态记忆和自我反思的能力，以提高它的推理技能。反思采用标准的强化学习设置，其中奖励模型提供简单的二元奖励，行动空间遵循 ReAct 中的设置，同时特定任务的行动空间通过语言来增强复杂的推理步骤。在每个行动at之后，Agent会计算一个启发式值ht，并根据自我反思的结果决定是否重置环境以开始新的试验。

启发式函数用于判断LLM的行动轨迹什么时候开始低效或者包含幻觉，并在这个时刻停止任务。低效计划是指花费了大量时间但没有没有成功的路径。幻觉的定义为LLM遇到了一系列连续的相同动作，这些动作导致LM在环境中观察到了相同的结果。

通过向LLM展示两个例子来创建自我反思，每个例子都是一个pair对（失败的轨迹，用于指导未来计划变化的理想反思）。然后将反思添加到代理的工作记忆中，反省的数量最多三个，主要用作查询 LLM 的上下文。
![](https://image.cubox.pro/cardImg/2023111518272982847/11732.jpg?imageMogr2/quality/90/ignore-error/1)
![](https://image.cubox.pro/cardImg/2023111518272949582/44855.jpg?imageMogr2/quality/90/ignore-error/1)

为了避免过拟合，CoH添加了一个正则化项来最大化预训练数据集的对数似然。为了避免捷径和复制（因为反馈序列中有许多常见单词），他们在训练期间随机mask 0%-5%的历史token。

实验中的训练数据集是 WebGPT的对比、人类反馈摘要和人类偏好数据集的组合。
![](https://image.cubox.pro/cardImg/2023111518273062964/56346.jpg?imageMogr2/quality/90/ignore-error/1)

CoH的思想是在上下文中呈现一系列逐步改进的历史，并训练模型能够跟随趋势产出更好的结果。**算法蒸馏** （**Algorithm Distillation**）将相同的思想应用于强化学习任务中的跨剧情轨迹，其中算法被封装在一个长期历史条件策略中。考虑到代理与环境的多次交互，每一集中代理都会表的更好一些，AD 将这个学习历史连接起来并将其输入到模型中。因此，我们应该期望下一个预测的动作比之前的试验表现更好。我们的目标是学习强化学习的过程，而不是训练一个用于特定任务的策略本身。
![](https://image.cubox.pro/cardImg/2023111518273095334/23097.jpg?imageMogr2/quality/90/ignore-error/1)

该论文假设，任何生成一系列学习历史数据的算法都可以通过对动作执行克隆行为来蒸馏成神经网络。历史数据是由一组源策略生成的，每个源策略都是针对特定任务进行训练。在训练阶段，每次强化学习运行时，会随机抽样一个任务，并使用多集历史记录的子序列进行训练，使得学习到的策略与任务无关。

实际上，该模型的上下文窗口长度是有限的，因此使用的剧集应该足够短，以方便构建多剧集历史数据。要学习几乎最优的上下文强化学习算法，需要2-4个剧集的多剧集上下文。上下文强化学习往往需要足够长的上下文。

与三个基线包括 ED（专家蒸馏，使用专家轨迹而不是学习历史数据的行为克隆）、源策略（用于生成UCB蒸馏的轨迹）和 RL\^2（用作上限，因为它需要在线强化学习）相比。尽管AD只使用离线强化学习，但依它然展示了性能和 RL\^2接近的上下文强化学习的能力，并且学习速度比其他基线快得多。在给定源策略的部分历史训练数据的条件下，AD的改进速度也比ED基线多。
![](https://image.cubox.pro/cardImg/2023111518273074974/97104.jpg?imageMogr2/quality/90/ignore-error/1)

**组件二：记忆**
----------

非常感谢 ChatGPT 帮助我起草本节。在与 ChatGPT 的对话中，我学到了很多关于人脑和快速 MIPS 的数据结构的知识。

### **记忆的类型**

记忆可以定义为用于获取、存储、保留以及随后检索信息的过程。人脑中有多种记忆类型。

1. **「感觉记忆」**：这是记忆的最早阶段，提供在原始刺激结束后保留感觉信息（视觉、听觉等）印象的能力。感觉记忆通常只能持续几秒钟。感觉记忆的子类别包括图像记忆（视觉）、回声记忆（听觉）和触觉记忆（触摸）。
2. **「短期记忆」**或者工作记忆：它存储我们当前意识到的以及执行学习和推理等复杂认知任务所需的信息。短期记忆被认为具有大约 7 个物品的容量（Miller 1956）并且持续 20-30 秒。
3. **「长期记忆」**：长期记忆可以存储相当长的时间信息，从几天到几十年不等，存储容量基本上是无限的。LTM 有两种亚型：

* 显示/陈述性记忆：这是对事实和事件的记忆，是指那些可以有意识地回忆起来的记忆，包括情景记忆（事件和经历）和语义记忆（事实和概念）。
* 隐含/程序性记忆：这种类型的记忆是无意识的，涉及自动执行的技能和程序，例如骑自行车或在键盘上打字。

![](https://image.cubox.pro/cardImg/2023111518273164514/26499.jpg?imageMogr2/quality/90/ignore-error/1)

我们可以大致考虑以下映射：

* 感觉记忆作为学习嵌入表示的原始输入，包括文本、图像或其他模态；  
* 短期记忆作为上下文学习。它是短暂和有限的，因为它受到Transformer有限上下文窗口长度的限制。
* 长期记忆作为代理可以在查询时关注的外部向量存储，可通过快速检索访问。

### **最大内积搜索 (MIPS)**

外部记忆可以缓解有限注意力广度的限制。一个标准做法是将信息的embedding表示保存到一个向量存储数据库中，该数据库可以支持快速最大内积搜索（MIPS）。为了优化检索速度，常见的选择是近似最近邻 (ANN)算法，它能返回大约前 k 个最近邻，以牺牲一点精度来换取巨大的加速。

以下几种常见的ANN算法都可以用于MIPS：

**「LSH」** （Locality-Sensitive Hashing）**」**它引入了一种哈希函数，使得相似的输入能以更高的概率映射到相同的桶中，其中桶的数量远小于输入的数量。

**「ANNOY** （Approximate Nearest Neighbors）**」**它的核心数据结构是随机投影树，实际是一组二叉树，其中每个非叶子节点表示一个将输入空间分成两半的超平面，每个叶子节点存储一个数据。二叉树是独立且随机构建的，因此在某种程度上，它模仿了哈希函数。ANNOY会在所有树中迭代地搜索最接近查询的那一半，然后不断聚合结果。这个想法与 KD 树非常相关，但更具可扩展性。

**「HNSW** （Hierarchical Navigable Small World）**」**它受到小世界网络思想的启发，其中大多数节点可以在很少的步骤内被任何其他节点到触达；例如社交网络的"六度分隔"理论。HNSW构建这些小世界图的层次结构，其中底层结构包含实际数据。中间的层创建快捷方式以加快搜索速度。执行搜索时，HNSW从顶层的随机节点开始，导航至目标。当它无法靠近时，它会向下移动到下一层，直到到达最底层。上层中的每个移动都可能覆盖数据空间中的很长一段距离，而下层中的每个移动都可以细化搜索质量。

**「FAISS** （facebook AI Similarity Search）**」**它运行的假设是：高维空间中节点之间的距离服从高斯分布，因此这些数据点之间存在着聚类点。faiss通过将向量空间划分为簇，然后在簇内使用用向量量化。faiss首先使用粗粒度量化方法来查找候选簇，然后进一步使用更精细的量化方法来查找每个簇。

**「ScaNN** （Scalable Nearest Neighbors）**」**的主要创新在于各向异性向量量化。它将数据点量化为一个向量，使得它们的内积与原始距离尽可能相似，而不是选择最接近的量化质心点。
![](https://image.cubox.pro/cardImg/2023111518273184881/74800.jpg?imageMogr2/quality/90/ignore-error/1)

**组件三：使用工具**
------------

懂得使用工具是人类最显著和最独特的地方。我们创造、修改和利用外部事物来完成并超越我们身体和认知极限的事情。同样地。我们也可以为 LLMs 配备外部工具来显著扩展模型的能力。
![](https://image.cubox.pro/cardImg/2023111518273186293/78142.jpg?imageMogr2/quality/90/ignore-error/1)

**「MRKL」**是"模块化推理、知识和语言"的缩写，是一种用于自主代理的神经符号架构。MRKL 系统包含一组"专家"模块，同时通用的LLM会作为路由器将查询路由到最合适的专家模块。这些模块可以是神经模块（例如深度学习模型）或符号模块（例如数学计算器、货币转换器、天气 API）。

MRKL的研究团队对微调 LLM进行了实验，以调用计算器为例，使用算术作为测试案例。实验结果表明，解决口头数学问题比明确陈述的数学问题更难，因为LLMs（7B Jurassic1-large 模型）无法可靠地提取基本算术的正确参数。实验结果也同样强调了当外部符号工具能够可靠地工作时，知道何时以及如何使用这些工具是至关重要的，这取决于 LLM 的能力。

**「TALM」** （工具增强语言模型）和 **「Toolformer」**都通过微调一个LM来学习使用外部工具 API。该数据集是基于新添加的 API 调用注释是否可以提高模型输出质量而扩展的。

ChatGPT 插件和 OpenAI API 函数调用是具有工具使用能力的 LLM 在实践中的最好的例子。工具 API 的集合可以由其他开发人员提供（如插件中的情况），也可以自定义（如函数调用中的情况）。

**「HuggingGPT」**是一个框架，它使用 ChatGPT 作为任务规划器，根据每个模型的描述来选择 HuggingFace 平台上可用的模型，并根据模型的执行结果总结生成最后的响应结果。
![](https://image.cubox.pro/cardImg/2023111518273118888/12552.jpg?imageMogr2/quality/90/ignore-error/1)

该系统由下面四个阶段组成：

(1) **「任务规划」**：LLM 作为大脑，将用户请求解析为多个任务。每个任务都有四个属性：任务类型、ID、依赖关系和参数。他们使用少量示例来指导 LLM 进行任务解析和规划。

具体指令如下：
> AI助手可以将用户输入解析为多个任务：\[{"task": task, "id", task_id, "dep": dependency_task_ids, "args": {"text": text, "image": URL, "audio": URL, "video": URL}}\]。"dep"字段表示前一个任务的ID，该任务生成了当前任务所依赖的新资源。特殊标记"-task_id"指的是具有任务ID为task_id的依赖任务中生成的文本图像、音频和视频。任务必须从以下选项中选择：{{可用任务列表}}。任务之间存在逻辑关系，请注意它们的顺序。如果无法解析用户输入，则需要回复空的JSON。以下是几个示例供您参考：{{演示}}。聊天记录记录为{{聊天记录}}。从这个聊天记录中，您可以找到用户提到的资源的路径，以进行任务规划。

(2) **「模型选择」** ：LLM 将任务分配给专家模型，其中请求被构建为多项选择题。LLM 提供了一个模型列表供选择。由于上下文长度有限，需要基于任务类型进行过滤。  

具体指令如下：
> 根据用户请求和调用命令，AI助手帮助用户从模型列表中选择一个合适的模型来处理用户请求。AI助手仅输出最合适模型的模型ID。输出必须采用严格的JSON格式："id": "id", "reason": "您选择该模型的详细原因"。我们为您提供了一个模型列表{{候选模型}}供选择。请从列表中选择一个模型。

(3) **「任务执行」**：专家模型在特定任务上执行并记录结果。

具体指令如下：  
> 根据输入和推理结果，AI助手需要描述过程和结果。前面的阶段可以形成如下 - 用户输入：{{用户输入}}，任务规划：{{任务}}，模型选择：{{模型分配}}，任务执行：{{预测结果}}。您必须首先以简单明了的方式回答用户的请求。然后以第一人称描述任务过程，并向用户展示您的分析和模型推理结果。如果推理结果包含文件路径，则必须告诉用户完整的文件路径。

(4) **「响应生成」**：LLM 接收执行结果并向用户提供总结结果。

要将HuggingGPT应用于实际场景中，需要解决一些挑战：(1) 需要提高效率，因为LLM推理轮次和与其他模型的交互都会减慢处理速度；(2) 它依赖于长上下文窗口来传达复杂的任务内容；(3) 需要提高LLM输出和外部模型服务的稳定性。

**「API-Bank」** 是用于评估工具增强LLM性能的基准。它包含53个常用的API工具、完整的工具增强LLM工作流程以及264个带有568个API调用的注释对话。API的选择非常多样化，包括搜索引擎、计算器、日历查询、智能家居控制、日程管理、健康数据管理、账户认证工作流程等等。由于API数量众多，LLM首先访问API搜索引擎以找到正确的API进行调用，然后使用相应的文档进行调用。  
![](https://image.cubox.pro/cardImg/2023111518273210315/97610.jpg?imageMogr2/quality/90/ignore-error/1)

在API-Bank工作流程中，LLM需要做出一些决策，而在每个步骤中，我们都可以评估该决策的准确性。这些决策包括：

1. 判断是否需要进行API调用。
2. 确定要调用的正确API：如果不够好，LLM需要迭代修改API输入（例如，为搜索引擎API决定搜索关键字）。
3. 根据API结果进行响应：如果结果不满意，模型可以选择进行改进并再次调用。

该基准评估了代理程序在三个层面上的工具使用能力：

* Level-1评估调用API的能力。在给定API的描述的情况下，模型需要确定是否调用给定的API，正确调用它，并对API返回做出适当的响应。
* Level-2检查检索API的能力。模型需要搜索可能解决用户需求的API，并通过阅读文档学习如何使用它们。
* Level-3评估计划API超越检索和调用的能力。在用户请求不明确的情况下（例如，安排团队会议，为旅行预订航班/酒店/餐厅），模型可能需要进行多个API调用来解决问题。

**案例分析**
--------

### **科学发现代理程序**

**「ChemCrow」**是一个特定领域的示例，其中LLM通过13个专家设计的工具增强，以完成有机合成、药物发现和材料设计等任务。在LangChain中实现的工作流程反映了之前在ReAct和MRKLs中描述的内容，并将CoT推理与与任务相关的工具相结合：

* 给LLM提供一个工具名称列表，包括它们的效用描述以及有关预期输入/输出的详细信息。
* 指示LLM在必要时使用提供的工具来回答用户给出的提示。指令建议模型遵循ReAct格式：思考、行动、行动输入、观察。

一个有趣的观察是，虽然基于LLM的评估得出结论表明GPT-4和ChemCrow的表现几乎相当，但面向解决方案的化学正确性的专家进行的人类评估表明，ChemCrow的表现远远优于GPT-4。这表明，在使用LLM评估自己在需要深入专业知识的领域中的表现时存在潜在问题。缺乏专业知识可能会导致LLM不知道其缺陷，因此无法很好地判断任务结果的正确性。

Boiko等人（2023年）还研究了LLM增强的科学发现代理程序，以处理复杂科学实验的自主设计、规划和执行。该代理程序可以使用工具浏览互联网、阅读文档、执行代码、调用机器人实验API并利用其他LLM。

例如，当要求"开发一种新型抗癌药物"时，该模型提出了以下推理步骤：

1. 询问当前抗癌药物发现的趋势；
2. 选择一个目标；
3. 请求一个针对这些化合物的支架；
4. 一旦化合物被确定，模型尝试合成它。

他们还讨论了风险，特别是非法药物和生物武器。他们制定了一个测试集，包含已知的化学武器代理列表，并要求代理合成它们。11个请求中有4个（36％）被接受以获得合成解决方案，并且代理尝试查阅文档以执行该过程。11个请求中有7个被拒绝，在这7个被拒绝的案例中，5个是在Web搜索后被拒绝的，而2个仅基于提示被拒绝。

### **生成代理模拟**

**「生成式代理** （Generative Agents）**」**是一个非常有趣的实验，它包含25个虚拟角色，每个角色由LLM驱动的代理程序控制，它们在一个沙盒环境中生活和互动，受到《模拟人生》的启发。生成代理为交互式应用程序创建了可信的人类行为模拟。

生成代理的设计将LLM与记忆、规划和反思机制相结合，使代理能够根据过去的经验进行操作，以及与其他代理进行交互。

* **「记忆」**流：是一个长期记忆模块（外部数据库），它主要记录代理在自然语言中的经验列表。
  * 每个元素都是一个观察结果，是代理直接提供的事件。代理之间的通信可以触发新的自然语言陈述。
* **「检索」**模型：根据相关性、新近性和重要性，呈现上下文以通知代理的行为。
  * 新近性：最近的事件得分更高。
  * 重要性：区分平凡的记忆和核心记忆。直接询问LM。
  * 相关性：基于它与当前情况/查询的相关程度。
* **「反思」**机制：随着时间的推移，将记忆综合成更高层次的推断，并指导代理的未来行为。它们是过去事件的更高级别摘要（请注意，这与上面的自我反思有些不同）。
  * 提示LM使用最近的100个观察结果，并在给定一组观察结果/陈述的情况下生成3个最显著的高级问题。然后要求LM回答这些问题。
* **「规划和反应」**：将反思和环境信息转化为实际行动。
  * 规划的本质是为了在当前时间和未来时间优化可信度。
  * 提示模板：{介绍代理X}。这是X今天的大致计划：1）
  * 代理之间的关系以及一个代理被另一个代理观察到的情况都被考虑在内，用于规划和反应。
  * 环境信息以树形结构呈现。

![](https://image.cubox.pro/cardImg/2023111518273258763/18533.jpg?imageMogr2/quality/90/ignore-error/1)

这个有趣的模拟产生了"涌现的社会行为"，例如信息扩散、关系记忆（例如两个代理人继续谈论话题）和社交事件的协调（例如主办聚会并邀请许多其他人）。

### **概念验证的例子**

AutoGPT引起了很多人对建立以LLM为主控制器的自主代理的可能性的关注。虽然在自然语言层面它具有相当多的可靠性问题，但它仍然是一个很酷的概念验证演示。AutoGPT中的很多代码都是关于格式解析的。

这是AutoGPT使用的系统消息，其中{{...}}是用户输入：

    You are {{ai-name}}, {{user-provided AI bot description}}.
    Your decisions must always be made independently without seeking user assistance. Play to your strengths as an LLM and pursue simple strategies with no legal complications.

    GOALS:

    1. {{user-provided goal 1}}
    2. {{user-provided goal 2}}
    3. ...
    4. ...
    5. ...

    Constraints:
    1. ~4000 word limit for short term memory. Your short term memory is short, so immediately save important information to files.
    2. If you are unsure how you previously did something or want to recall past events, thinking about similar events will help you remember.
    3. No user assistance
    4. Exclusively use the commands listed in double quotes e.g. "command name"
    5. Use subprocesses for commands that will not terminate within a few minutes

    Commands:
    1. Google Search: "google", args: "input": "<search>"
    2. Browse Website: "browse_website", args: "url": "<url>", "question": "<what_you_want_to_find_on_website>"
    3. Start GPT Agent: "start_agent", args: "name": "<name>", "task": "<short_task_desc>", "prompt": "<prompt>"
    4. Message GPT Agent: "message_agent", args: "key": "<key>", "message": "<message>"
    5. List GPT Agents: "list_agents", args:
    6. Delete GPT Agent: "delete_agent", args: "key": "<key>"
    7. Clone Repository: "clone_repository", args: "repository_url": "<url>", "clone_path": "<directory>"
    8. Write to file: "write_to_file", args: "file": "<file>", "text": "<text>"
    9. Read file: "read_file", args: "file": "<file>"
    10. Append to file: "append_to_file", args: "file": "<file>", "text": "<text>"
    11. Delete file: "delete_file", args: "file": "<file>"
    12. Search Files: "search_files", args: "directory": "<directory>"
    13. Analyze Code: "analyze_code", args: "code": "<full_code_string>"
    14. Get Improved Code: "improve_code", args: "suggestions": "<list_of_suggestions>", "code": "<full_code_string>"
    15. Write Tests: "write_tests", args: "code": "<full_code_string>", "focus": "<list_of_focus_areas>"
    16. Execute Python File: "execute_python_file", args: "file": "<file>"
    17. Generate Image: "generate_image", args: "prompt": "<prompt>"
    18. Send Tweet: "send_tweet", args: "text": "<text>"
    19. Do Nothing: "do_nothing", args:
    20. Task Complete (Shutdown): "task_complete", args: "reason": "<reason>"

    Resources:
    1. Internet access for searches and information gathering.
    2. Long Term memory management.
    3. GPT-3.5 powered Agents for delegation of simple tasks.
    4. File output.

    Performance Evaluation:
    1. Continuously review and analyze your actions to ensure you are performing to the best of your abilities.
    2. Constructively self-criticize your big-picture behavior constantly.
    3. Reflect on past decisions and strategies to refine your approach.
    4. Every command has a cost, so be smart and efficient. Aim to complete tasks in the least number of steps.

    You should only respond in JSON format as described below
    Response Format:
    {
        "thoughts": {
            "text": "thought",
            "reasoning": "reasoning",
            "plan": "- short bulleted\n- list that conveys\n- long-term plan",
            "criticism": "constructive self-criticism",
            "speak": "thoughts summary to say to user"
        },
        "command": {
            "name": "command name",
            "args": {
                "arg name": "value"
            }
        }
    }
    Ensure the response can be parsed by Python json.loads

**「GPT-Engineer」**是另一个项目，旨在根据自然语言中指定的任务创建整个代码库。GPT-Engineer被指示考虑构建一系列更小的组件，并要求用户输入以根据需要澄清问题。

下面是一个简单的用于任务澄清的示例对话，它使用OpenAI ChatCompletion端点发送给GPT-Engineer。用户的输入被包装在{{user input text}}  

    [
      {
        "role": "system",
        "content": "You will read instructions and not carry them out, only seek to clarify them.\nSpecifically you will first summarise a list of super short bullets of areas that need clarification.\nThen you will pick one clarifying question, and wait for an answer from the user.\n"
      },
      {
        "role": "user",
        "content": "We are writing {{a Super Mario game in python. MVC components split in separate files. Keyboard control.}}\n"
      },
      {
        "role": "assistant",
        "content": "Summary of areas that need clarification:\n1. Specifics of the Super Mario game (e.g. level design, characters, gameplay mechanics)\n2. Details about the MVC components (e.g. which components are in each file)\n3. Keyboard control implementation (e.g. which keys to use, how to handle input)\n\nClarifying question:\nCan you provide more details about the Super Mario game, such as level design, characters, and gameplay mechanics?"
      },
      {
        "role": "user",
        "content": "{{There are 10 levels in total. The main character is a plumber named Mario, who can walk and jump. It is a classical platform game just like Super Mario. The main character moves from left to right, trying to get to the destination, where there are many obstacles and attacks from enemies in the process.}}\n\nIs anything else unclear? If yes, only answer in the form:\n{remaining unclear areas} remaining questions.\n{Next question}\nIf everything is sufficiently clear, only answer \"Nothing more to clarify.\"."
      },
      {
        "role": "assistant",
        "content": "Remaining unclear areas: 2 remaining questions.\nCan you provide more information about how the MVC components are split into separate files?"
      },
      {
        "role": "user",
        "content": "{{Make your own assumptions and state them explicitly before starting}}"
      }
    ]

在澄清这些之后，代理进入了代码编写模式，并显示了不同的系统消息。具体系统消息如下：
> You will get instructions for code to write. You will write a very long answer. Make sure that every detail of the architecture is, in the end, implemented as code. Make sure that every detail of the architecture is, in the end, implemented as code.   
> Think step by step and reason yourself to the right decisions to make sure we get it right. You will first lay out the names of the core classes, functions, methods that will be necessary, as well as a quick comment on their purpose.
>
> Then you will output the content of each file including ALL code. Each file must strictly follow a markdown code block format, where the following tokens must be replaced such that FILENAME is the lowercase file name including the file extension, LANG is the markup code block language for the code's language, and CODE is the code:
>
> FILENAME
>
> **CODE**
>
> Useful to know: You almost always put different classes in different files. For Python, you always create an appropriate requirements.txt file. For NodeJS, you always create an appropriate package.json file. You always add a comment briefly describing the purpose of the function definition. You try to add comments explaining very complex bits of logic. You always follow the best practices for the requested languages in terms of describing the code written as a defined package/project.
>
> Python toolbelt preferences:
>
> pytest   
> dataclasses

对话样本：

    [
      {
        "role": "system",
        "content": "You will get instructions for code to write.\nYou will write a very long answer. Make sure that every detail of the architecture is, in the end, implemented as code.\nMake sure that every detail of the architecture is, in the end, implemented as code.\n\nThink step by step and reason yourself to the right decisions to make sure we get it right.\nYou will first lay out the names of the core classes, functions, methods that will be necessary, as well as a quick comment on their purpose.\n\nThen you will output the content of each file including ALL code.\nEach file must strictly follow a markdown code block format, where the following tokens must be replaced such that\nFILENAME is the lowercase file name including the file extension,\nLANG is the markup code block language for the code's language, and CODE is the code:\n\nFILENAME\n```LANG\nCODE\n```\n\nYou will start with the \"entrypoint\" file, then go to the ones that are imported by that file, and so on.\nPlease note that the code should be fully functional. No placeholders.\n\nFollow a language and framework appropriate best practice file naming convention.\nMake sure that files contain all imports, types etc. Make sure that code in different files are compatible with each other.\nEnsure to implement all code, if you are unsure, write a plausible implementation.\nInclude module dependency or package manager dependency definition file.\nBefore you finish, double check that all parts of the architecture is present in the files.\n\nUseful to know:\nYou almost always put different classes in different files.\nFor Python, you always create an appropriate requirements.txt file.\nFor NodeJS, you always create an appropriate package.json file.\nYou always add a comment briefly describing the purpose of the function definition.\nYou try to add comments explaining very complex bits of logic.\nYou always follow the best practices for the requested languages in terms of describing the code written as a defined\npackage/project.\n\n\nPython toolbelt preferences:\n- pytest\n- dataclasses\n"
      },
     #  ... same conversation as earlier, ended with "Make your own assumptions and state them explicitly before starting".
      {
        "role": "assistant",
        "content": "Assumptions:\n1. Model: The model will contain the game's data, such as level information, character states, and enemy positions.\n2. View: The view will handle the game's visuals, including rendering the game objects, backgrounds, and updating the display.\n3. Controller: The controller will manage user input, such as keyboard controls, and update the model accordingly.\n\nWith these assumptions in mind, is there any specific aspect of the keyboard control implementation you would like me to clarify?"
      },
      {
        "role": "user",
        "content": "Please now remember the steps:\n\nThink step by step and reason yourself to the right decisions to make sure we get it right.\nFirst lay out the names of the core classes, functions, methods that will be necessary, As well as a quick comment on their purpose.\n\nThen you will output the content of each file including ALL code.\nEach file must strictly follow a markdown code block format, where the following tokens must be replaced such that\nFILENAME is the lowercase file name including the file extension,\nLANG is the markup code block language for the code's language, and CODE is the code:\n\nFILENAME\n```LANG\nCODE\n```\n\nPlease note that the code should be fully functional. No placeholders.\n\nYou will start with the \"entrypoint\" file, then go to the ones that are imported by that file, and so on.\nFollow a language and framework appropriate best practice file naming convention.\nMake sure that files contain all imports, types etc. The code should be fully functional. Make sure that code in different files are compatible with each other.\nBefore you finish, double check that all parts of the architecture is present in the files.\n"
      }
    ]

**挑战**
------

在了解构建以LLM为中心的代理的关键思想和演示之后，我开始看到一些共同的限制：

* **有限的上下文长度**：受限的上下文容量限制了历史信息、详细说明、API调用上下文和响应。系统的设计必须与这种有限的通信带宽配合工作，而像自我反思这样的机制可以从很长甚至无限的上下文窗口中获益良多。虽然向量存储和检索可以提供对更大知识库的访问，但它们的表示能力不如完全注意力强大。
* **长期规划和任务分解的挑战**：在漫长的历史上进行规划并且有效地探索解决方案空间仍然具有挑战性。当面临意外错误时，LLM很难调整计划，使它们与不断试错学习的人类相比不太稳健。
* **自然语言接口的可靠性**：当前的代理系统依赖于自然语言作为LLM和记忆、工具等外部组件之间的接口。然而，模型输出的可靠性是有问题的，因为LLM可能会出现格式错误并偶尔表现出叛逆行为（例如拒绝遵循指令）。因此，许多代理演示代码都集中在解析模型输出上。

**我的观点**
--------

OpenAI发布了ChatGPT这款堪比"iphone"的划时代产品后，OpenAI的"野心"不止于此。他们还想更进一步成为AI时代的苹果公司。OpenAI此前推出基于ChatGPT的插件，引起了大量关注，被称为 ChatGPT的App Store时刻，但从目前的使用数据来看，插件带来的影响力很有限，无法和ChatGPT相提并论。

和插件相比，Agent能够带来更大的影响力，能真正重构当下的很多应用场景，它的想象空间更大更丰富。Agent背后都是通过LLM驱动的，它是LLM（大型语言模型）+ 记忆 + 规划技能 + 工具使用的集大成者。这也不难理解为什么OpenAI现在重点发力Agent，因为有了大模型作为硬件支撑之外，Agent作为软件应用的重要落地产品，它完全可以建立起一道软件生态的壁垒，App Store时刻才有可能真正来临。

不过当前Agent还是存在诸多问题，我个人觉得其中最主要的问题是交互方式过于单一，对自然语言的准确性依赖较高，同时也受限于LLM有限的注意力窗口。不过只要有大佬不断跟进，相信这些问题未来一定会解决！

原文《LLM Powered Autonomous Agents》[https://lilianweng.github.io/posts/2023-06-23-agent](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-06-23-agent)

**参考文献**
--------

1.AutoGPT:[https://github.com/Significant-Gravitas/Auto-GPT](https://link.zhihu.com/?target=https%3A//github.com/Significant-Gravitas/Auto-GPT)

2.GPT-Engineer:[https://github.com/AntonOsika/gpt-engineer](https://link.zhihu.com/?target=https%3A//github.com/AntonOsika/gpt-engineer)

3.CoT.[https://arxiv.org/abs/2201.11903](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2201.11903)

4.Tree of Thoughts:[https://arxiv.org/abs/2305.10601](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2305.10601)

5.LLM+P:[https://arxiv.org/abs/2304.11477](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2304.11477)

6.ReAc:[https://arxiv.org/abs/2210.03629](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2210.03629)

7.Reflexion:[https://arxiv.org/abs/2303.11366](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2303.11366)

8.CoH:[https://arxiv.org/abs/2302.02676](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2302.02676)

9.MRKL [https://arxiv.org/abs/2205.00445](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2205.00445)

10.TALM [https://arxiv.org/abs/2205.12255](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2205.12255)

11.Toolformer:[https://arxiv.org/abs/2302.04761](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2302.04761)

12.HuggingGPT:[https://arxiv.org/abs/2303.17580](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2303.17580)

13.API-Bank:[https://arxiv.org/abs/2304.08244](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2304.08244)

14.ChemCrow:[https://arxiv.org/abs/2304.05376](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2304.05376)

15.Generative Agents:[https://arxiv.org/abs/2304.03442](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2304.03442)

欢迎大家关注微信公众号：AI的潜意识，了解最新的大模型技术和推荐算法！

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7124413143324820106)
