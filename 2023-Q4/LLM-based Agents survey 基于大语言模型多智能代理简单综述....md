LLM-based Agents survey 基于大语言模型多智能代理简单综述及展望
===========================================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/648376562)DerryChan游学者，港中文深圳PhD在读，主营ESG、双碳、电力、NLP

目录

收起

ss1. Agent介绍

1.1 介绍

1.2 理论基础

2. Agent实现思路

2.1 Thinking \& Planning

2.2 Action \& Tools

2.3 Review

2.4 Memory

2.5 Environment

2.6 Multi-Agents

3. 部分Data 整理

4. 总结

Ref

**ss1. Agent介绍**
----------------

### **1.1 介绍**

引用一下维基百科的定义：
> 智能代理Agent是以智能方式行事的代理；它感知环境，自主采取行动以实现目标，并可以通过学习或获取知识来提高其性能。   
> 本篇主要针对LLM-based Agent，即Agent基于大语言模型进行思考规划，获取信息，并从大模型与外界学习知识并自学习与利用。   
> 多智能体Multi-Agent则是可以通过多个Agent进行协作配合完成更复杂的工作。

<br />

特点：   
- 自主AI代理是根据给定的目标进行训练工作的   
- 拥有LLM（大语言模型）之外的规划、内存、工具使用、反思能力   
- 具有多模态感知的能力（文本、视频、图像、声音等）   
即：Agent = 大语言模型/多模态模型+记忆+规划+工具使用

|  Agent应用场景  |                                      解释                                       |
|-------------|-------------------------------------------------------------------------------|
| 个人助理        | 完成各种任务，如查找和回答问题，预订旅行和其他活动，管理日历和财务，监控健康和健身活动。如WebGPT                           |
| 软件及项目开发     | 使用多角色完成应用程序开发的编码、测试和调试工作，擅长自然语言作为输入处理任务。如MetaGPT、ChatDev                      |
| 游戏NPC       | 处理游戏任务，如创建更智能的NPC，开发自适应的反派角色，提供游戏和负载平衡，以及向玩家提供情境化帮助，并且NPC存在记忆对每个用户都有不同反馈。如逆水寒 |
| 智慧客服即销售     | 处理客户支持查询，回答问题，协助解答有关之前交易或付款的问题，或者引导潜在客户维护关系、宣传、销售及售后工作。                       |
| 金融管理        | 提供研究的金融建议，组合管理，风险评估和欺诈检测，合规管理和报告，信用评估，承保，支出和预算管理支持。                           |
| 仿真，如社会学、管理学 | 如模拟公司管理政策判断效益，模拟人类行为等                                                         |
| 智能文档处理      | 包括分类、深度信息分析和提取、问答、摘要、情感分析、翻译和版本控制等。比如chatPDF、chatPaper                        |
| 科研          | 帮助科研人员进行资料收集、文献综述、甚至进行实验。如GPT-researcher                                      |
| 更多          | 智慧交通信控、电力系统等，需要更多的场景挖掘                                                        |

### **1.2 理论基础**

<br />

为什么引入Agent？ 直接使用LLM有什么限制？

- LLM知识有限且更新不及时，可以使用Agent获取更新的信息；  
- LLM context有限，Agent是LLM context未达到无限之前的有效外置骨骼；  
- LLM无法同时担任多个角色，在需要协作的任务中无法发挥更好的能力；

在以下Paper有说明协作的有效性：

**Unleashing Cognitive Synergy in Large Language Models: A Task-Solving Agent through Multi-Persona Self-Collaboration**

大语言模型中发挥认知协同作用：通过多人格自我协作成为任务解决代理   
概述：人类智能依赖于认知协同的概念，在不同认知过程之间进行合作和信息整合，相比单独的认知过程，能够产生更优越的结果。尽管大型语言模型（LLMs）在作为通用任务解决代理方面表现出有希望的性能，但它们仍然在需要大量领域知识和复杂推理的任务中遇到困难。在这项工作中，我们提出了"Solo Performance Prompting"（SPP）的概念，它通过与多个人物进行多轮自我协作，将单个LLM转变为认知协同者。认知协同者指的是一种智能代理，它与多个思维合作，结合他们的个体优势和知识，以增强复杂任务中的问题解决和整体性能。通过根据任务输入动态地识别和模拟不同的人物，SPP释放了LLMs中认知协同的潜力。我们发现，在LLMs中分配多个细粒度的人物角色，相比于使用单个或固定数量的人物角色，能够激发更好的问题解决能力。我们在三个具有挑战性的任务上评估了SPP：创意性问答、Codenames协作和逻辑格子谜题，涵盖了知识密集型和推理密集型两种类型。与之前仅增强LLMs推理能力的作品（如Chain-of-Thought）不同，SPP有效地激发了内部知识获取能力，减少了幻觉，并保持了强大的推理能力。

![](https://image.cubox.pro/cardImg/2023111518283964922/89275.jpg?imageMogr2/quality/90/ignore-error/1)
![](https://image.cubox.pro/cardImg/2023111518283958149/70770.jpg?imageMogr2/quality/90/ignore-error/1)

**2. Agent实现思路**
----------------

类似强化学习，Agent可以分为内在的Think与Planning，Action，Review，Memory

以及外在的Environment，及多Agent之间的协调

这里引用了lilianweng blog的图片和大致框架：
![](https://image.cubox.pro/cardImg/2023111518283935653/71583.jpg?imageMogr2/quality/90/ignore-error/1)

### **2.1 Thinking \& Planning**

**Chain-of-Thought Prompting Elicits Reasoning in Large Language Models**   
通过prompt要求LLM Think Step by Step，让LLM有将困难任务逐步分解成更小更简单的步骤，赋予了LLM Planning能力；  
![](https://image.cubox.pro/cardImg/2023111518283982865/12869.jpg?imageMogr2/quality/90/ignore-error/1)

**Tree of Thoughts: Deliberate Problem Solving with Large Language Models**   
在CoT过程中通过在每一步探索多种推理可能性来扩展CoT；  
首先将问题分解为多个思考步骤，每一步产生多个想法，形成树形结构；  
搜索过程可以是BFS或DFS，每个状态由分类器或多数投票评估。  
![](https://image.cubox.pro/cardImg/2023111518284016953/50817.jpg?imageMogr2/quality/90/ignore-error/1)

**LLM+P: Empowering Large Language Models with Optimal Planning Proficiency**

LLM+P 依赖于一个外部经典规划器来进行长期规划。

该方法利用规划域定义语言(PDDL)作为描述规划问题的中间接口。

LLM(1)将问题转换为"problem PDDL"，(2)请求经典规划器基于已有的"Domain PDDL"生成PDDL计划，(3)将PDDL计划转换回自然语言
![](https://image.cubox.pro/cardImg/2023111518284041281/80969.jpg?imageMogr2/quality/90/ignore-error/1)

### **2.2 Action \& Tools**

关于Agent如何调用工具

**ToolFormer**   
![](https://image.cubox.pro/cardImg/2023111518284014547/51022.jpg?imageMogr2/quality/90/ignore-error/1)

**HuggingGPT**   
![](https://image.cubox.pro/cardImg/2023111518284158308/10086.jpg?imageMogr2/quality/90/ignore-error/1)

**Tool Learning with Foundation Models**   
![](https://image.cubox.pro/cardImg/2023111518284187792/33972.jpg?imageMogr2/quality/90/ignore-error/1)

**Gorilla: Large Language Model Connected with Massive APIs**
![](https://image.cubox.pro/cardImg/2023111518284122615/71590.jpg?imageMogr2/quality/90/ignore-error/1)

**TPTU: Task Planning and Tool Usage of Large Language Model-based AI Agents**
![](https://image.cubox.pro/cardImg/2023111518284179048/19548.jpg?imageMogr2/quality/90/ignore-error/1)

在本文首先提出了一个为基于 LLM 的人工智能代理量身定制的结构化框架，并讨论了解决复杂问题所需的关键功能。在此框架内，设计了两种不同类型的代理（即一步代理和顺序代理）来执行推理过程。随后，使用各种LLM实例化该框架，并评估他们在典型任务上的任务规划和工具使用（TPTU）能力。

目标是为研究人员和从业者提供有用的资源，以在其人工智能应用中利用LLM的力量。

### **2.3 Review**

**Self-Refine: Iterative Refinement with Self-Feedback**   
![](https://image.cubox.pro/cardImg/2023111518284254539/32729.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

像人一样，LLM并不一定在第一次尝试中生成的最佳文本(例如摘要、答案、解释)。  
其主要思想是使用一个LLM生成一个输出，然后让同一模型为自身的输出提供多方面反馈；最后，同一模型根据自身的反馈对之前生成的输出进行优化。  
在所有任务中，Self-REFINE生成的输出都比使用GPT-3.5和GPT-4直接生成的输出更喜欢，平均提高了20%。

**ReAct: Synergizing Reasoning and Acting in Language Models**   
ReAct框架聚合了Action与Reasoning，如下图，让LLM可以通过思考与行动(查询)对环境做出反馈  
![](https://image.cubox.pro/cardImg/2023111518284219906/72180.jpg?imageMogr2/quality/90/ignore-error/1)

**Reflexion: Language Agents with Verbal Reinforcement Learning**   
Reflex框架引入了Reward，让Environment对当前行动给出一个具体的Reward。Agent会计算一个启发函数h，决定是否重启env，开启新实验（当前决策路径无效、冗余等）。  
Reflection包含失败的反思，会加入新的Query的context中  
![](https://image.cubox.pro/cardImg/2023111518284239912/46748.jpg?imageMogr2/quality/90/ignore-error/1)

**Chain of Hindsight Aligns Language Models with Feedback**   
通过显式地向模型展示一系列过去的输出，每个输出都带有反馈注释，鼓励模型改进自己的输出。  
![](https://image.cubox.pro/cardImg/2023111518284239458/87367.jpg?imageMogr2/quality/90/ignore-error/1)

**Let's Verify Step by Step**

一步步验证
![](https://image.cubox.pro/cardImg/2023111518284262017/72112.jpg?imageMogr2/quality/90/ignore-error/1)

### **2.4 Memory**

![](https://image.cubox.pro/cardImg/2023111518284397897/10679.jpg?imageMogr2/quality/90/ignore-error/1)

| 记忆类型 |                               映射                                |                    例子                     |
|------|-----------------------------------------------------------------|-------------------------------------------|
| 感觉记忆 | 学习原始输入的嵌入表示，包括文本、图像或其他形式，短暂保留感觉印象。                              | 看一张图片，然后在图片消失后能够在脑海中回想起它的视觉印象。            |
| 短期记忆 | 上下文学习（比如直接写入prompt中的信息），处理复杂任务的临时存储空间，受Transformer有限的上下文窗口长度限制。 | 在进行心算时记住几个数字，但短期记忆是有限的，只能暂时保持几个项目。        |
| 长期记忆 | 在查询时智能Agent可以关注的外部向量存储，具有快速检索和基本无限的存储容量。                        | 学会骑自行车后，多年后再次骑起来时仍能掌握这项技能，这要归功于长期记忆的持久存储。 |

目前Agent主要是利用外部的长期记忆，来完成很多的复杂任务，比如阅读PDF、联网搜索实时新闻等。

这里的学术问题是**Maximum Inner Product Search (MIPS)，**（Scalable Nearest Neighbors算法效果最好），标准做法是将信息的嵌入表示保存到向量存储数据库中。

常见的一些向量数据库：

* FAISS
* HNSW
* milvus
* weaviate

### **2.5 Environment**

Environment部分主要讲Environment的设定，以及如何将Agent与Environment进行关联结合，Agent如何影响到Environment。

**WebArena**   
WebArena是一个独立的、可自主托管的用于构建自主代理的网络环境。WebArena创建包含四个热门类别的网站，这些网站具有功能和数据，模仿其真实世界的对应物。  
为了模拟人类问题解决，WebArena还嵌入了工具和知识资源，作为独立的网站。WebArena引入了一个基准测试，用于解释高水平的现实自然语言命令，并转化为具体的基于网络的交互。研究员们提供了注释过的程序，用于编程验证每个任务的功能正确性。  
![](https://image.cubox.pro/cardImg/2023111518284323005/24519.jpg?imageMogr2/quality/90/ignore-error/1)

**Learning to Model the World with Language**
![](https://image.cubox.pro/cardImg/2023111518284332088/70685.jpg?imageMogr2/quality/90/ignore-error/1)
![](https://image.cubox.pro/cardImg/2023111518284348612/59695.jpg?imageMogr2/quality/90/ignore-error/1)

目标是构建利用多种语言的智能体，这些语言可以传达一般知识、描述世界状态、提供交互式反馈等等。

核心思想是语言帮助智能体预测未来：将观察什么，世界将如何表现，以及哪些情况将得到奖励。

这种观点将语言理解与未来预测结合起来，作为一个强大的自我监督学习目标。

Dynalang是一种学习多模态世界模型的代理，该模型可以预测未来的文本和图像表示，并学习从想象的模型展示中采取行动。

与仅使用语言来预测动作的传统代理不同，Dynalang 通过使用过去的语言来预测未来的语言、视频和奖励，从而获得丰富的语言理解。

除了从环境中的在线交互中学习之外，Dynalang 还可以在文本、视频或两者的数据集上进行预训练，而无需操作或奖励。

### **2.6 Multi-Agents**

此部分主要参数多Agent之间如何协作共同完成一个目的。

**CAMEL: Communicative Agents for "Mind" Exploration of Large Scale Language Model Society**   
本框架聚焦于以任务为导向的角色扮演，它包含一个 AI 助手 (AI assistant) 和一个 AI 用户 (AI user)。  
在多智能体系统接收到人类用户的初步想法 (preliminary idea) 和角色分配 (role assignment) 后，一个 任务说明智能体 (task-specifier agent) 会提供详细的描述以让这个想法更具体。  
然后 AI assistant 和 AI user 会通过多轮对话进行合作，并完成给定的任务。对话会一直持续，直到 AI user 认为这个任务已经完成了。  
AI user 负责给出指令并根据任务完成情况引导对话，而 AI assistant 则需要遵循指令并且做出回答，给出具体的方法。  
![](https://image.cubox.pro/cardImg/2023111518284422057/91567.jpg?imageMogr2/quality/90/ignore-error/1)

**Generative Agents: Interactive Simulacra of Human Behavior**   
![](https://image.cubox.pro/cardImg/2023111518284458550/55687.jpg?imageMogr2/quality/90/ignore-error/1)

**Ghost in the Minecraft: Generally Capable Agents for Open-World Environments via Large Language Models with Text-based Knowledge and Memory**   
![](https://image.cubox.pro/cardImg/2023111518284444050/17089.jpg?imageMogr2/quality/90/ignore-error/1)

**METAGPT: META PROGRAMMING FOR MULTI-AGENTCOLLABORATIVE FRAMEWORK**
![](https://image.cubox.pro/cardImg/2023111518284487851/32734.jpg?imageMogr2/quality/90/ignore-error/1)

输入一句话需求，它就可以运行一个软件公司，输出产品文档 / 设计文档 / 任务 / 代码 REPO

在内部，它抽象了多个不同角色，包括产品经理、架构师、项目经理、工程师、QA 等等。

它将有效的人类工作流程注入 LLM 驱动的多智能体协作中的元编程方法。

特别是，MetaGPT首先将标准化操作程序 (SOP) 编码为提示，促进结构化协调。

然后，它进一步要求模块化输出，使用与人类专业人员平行的领域专业知识的代理来验证输出并减少复合错误。

通过这种方式，MetaGPT 利用装配线工作模型为不同的代理分配不同的角色，从而建立了一个可以有效和连贯地解构复杂的多智能体协作问题的框架。

**3. 部分Data 整理**
----------------

**ReAct :**

综合QA、简单文字游戏、网页浏览互动等
![](https://image.cubox.pro/cardImg/2023111518284535564/68577.jpg?imageMogr2/quality/90/ignore-error/1)

对应Prompt
![](https://image.cubox.pro/cardImg/2023111518284514378/89611.jpg?imageMogr2/quality/90/ignore-error/1)

在知识密集型任务和决策任务的实验中，ReAct比Act-only基线效果更好，其中Thought:...步骤被删除。

**Reflection**
![](https://image.cubox.pro/cardImg/2023111518284623689/16127.jpg?imageMogr2/quality/90/ignore-error/1)

**COH**

[WebGPT comparisons](https://link.zhihu.com/?target=https%3A//huggingface.co/datasets/openai/webgpt_comparisons)

[summarization from human feedback](https://link.zhihu.com/?target=https%3A//github.com/openai/summarize-from-feedback)

[human preference dataset](https://link.zhihu.com/?target=https%3A//github.com/anthropics/hh-rlhf)

**Camel**

[https://huggingface.co/datasets/camel-ai/code](https://link.zhihu.com/?target=https%3A//huggingface.co/datasets/camel-ai/code)

**4. 总结**
---------

本篇主要介绍Agent与多Agent的基本介绍、理论以及实现思路。

未来如何发展，个人觉得可能以下方向都挺有潜力：

多模态大模型的Agents：跨模态能力，解决更多事情

LLM信息的结构化：限制于LLM幻觉与context，在长期对话中需要记录关键信息结构化存储

**Ref**
-------

<https://zhuanlan.zhihu.com/p/647836219>

[https://lilianweng.github.io/posts/2023-06-23-agent/](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-06-23-agent/)

[https://mp.weixin.qq.com/s?__biz=Mzg2NzEyMjY1OA==\&mid=2247486596\&idx=1\&sn=03f3d77f277218c1aacfb5c6d3663579\&chksm=ce412009f936a91f09f537e41e10a2100ec2defb048ed416119faee122e867590f5a1d44ecd7\&mpshare=1\&scene=1\&srcid=0802OcoH4v7jyrRFF3uQb2CF\&sharer_sharetime=1691013034758\&sharer_shareid=3e153ae498db7427cf9df2e7c06d830f#rd](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s%3F__biz%3DMzg2NzEyMjY1OA%3D%3D%26mid%3D2247486596%26idx%3D1%26sn%3D03f3d77f277218c1aacfb5c6d3663579%26chksm%3Dce412009f936a91f09f537e41e10a2100ec2defb048ed416119faee122e867590f5a1d44ecd7%26mpshare%3D1%26scene%3D1%26srcid%3D0802OcoH4v7jyrRFF3uQb2CF%26sharer_sharetime%3D1691013034758%26sharer_shareid%3D3e153ae498db7427cf9df2e7c06d830f%23rd)

[https://mp.weixin.qq.com/s?__biz=Mzg2NzEyMjY1OA==\&mid=2247486422\&idx=1\&sn=045129ed57e103bfe004f99eeb271c7c\&chksm=ce41275bf936ae4d87f8c9b7b0087d1b20c82796d0df76fef818dfa781eb8dc72db3f3a9ed68\&mpshare=1\&scene=1\&srcid=0803qywjCuW1fCF2kW6OuZ3z\&sharer_sharetime=1691014101029\&sharer_shareid=3e153ae498db7427cf9df2e7c06d830f#rd](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s%3F__biz%3DMzg2NzEyMjY1OA%3D%3D%26mid%3D2247486422%26idx%3D1%26sn%3D045129ed57e103bfe004f99eeb271c7c%26chksm%3Dce41275bf936ae4d87f8c9b7b0087d1b20c82796d0df76fef818dfa781eb8dc72db3f3a9ed68%26mpshare%3D1%26scene%3D1%26srcid%3D0803qywjCuW1fCF2kW6OuZ3z%26sharer_sharetime%3D1691014101029%26sharer_shareid%3D3e153ae498db7427cf9df2e7c06d830f%23rd)

[https://app.tavily.com/#form](https://link.zhihu.com/?target=https%3A//app.tavily.com/%23form)

[https://github.com/geekan/MetaGPT](https://link.zhihu.com/?target=https%3A//github.com/geekan/MetaGPT)

[https://github.com/assafelovic/gpt-researcher](https://link.zhihu.com/?target=https%3A//github.com/assafelovic/gpt-researcher)

[https://huggingface.co/spaces/microsoft/HuggingGPT](https://link.zhihu.com/?target=https%3A//huggingface.co/spaces/microsoft/HuggingGPT)

[https://github.com/lucidrains/toolformer-pytorch](https://link.zhihu.com/?target=https%3A//github.com/lucidrains/toolformer-pytorch)

[https://en.wikipedia.org/wiki/Intelligent_agent](https://link.zhihu.com/?target=https%3A//en.wikipedia.org/wiki/Intelligent_agent)

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7124413427136594012)
