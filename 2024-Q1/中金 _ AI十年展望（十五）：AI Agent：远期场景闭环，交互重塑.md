中金 \| AI十年展望（十五）：AI Agent：远期场景闭环，交互重塑
=====================================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/Fkq3xvJ09myO_JRGm4OETw)于钟海 魏鹳霏等 中金点睛

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FfzHRVN3sYsicmoVBv4D0mPib68kWJVkDjnEM91ZO46IRCPDfIfFpMEn2BoxwUa2fguPicQ4WwvNibdnOL4IqZj4XTA%2F640%3Fwx_fmt%3Dgif)

**文/于钟海,魏鹳霏,游航,王之昊**


**中金研究**


年初至今的大模型浪潮席卷全球，推动AI Agent相关研究快速发展和应用加速涌现，有望进一步向通往AGI的道路迈进。**在本篇报告中，我们从概念界定、技术框架、应用实例、前瞻探讨四个维度对AI Agent进行梳理。**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_gif%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmaNvUGOicpn0tcpI7icbpTvGCt8hsMP5ibyia0d5O3yxp8OGa4A80DdjzPA%2F640%3Fwx_fmt%3Dgif%26from%3Dappmsg)


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkm98Je4JdmR5w3WtPsqExPC1dcPs30L1wlAD2Zic22w7YUicuae1icXlibIQ%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)

**[点击小程序查看报告原文]()**


**Abstract**


**摘要**


**概览：基于LLM的自主智能代理，朝AGI更进一步。**AI Agent是一种能够感知环境、自主决策并执行动作的智能实体，其发展基于主流AI算法框架变化而随之演进，目前正处于LLM-based Agent阶段。相较ChatGPT，AI Agent的进步之处在于：具备自主决策和行动能力；能够自主完成大部分工作，人类仅需设立目标并监督；是大模型在工程学上的进一步迭代。

**技术篇：以LLM为基座，拓展感知和行动等功能模块。**系统框架#1：AI Agent = Brain控制端 + Perception感知端 + Action行动端，其中控制端承担记忆、思考、决策等基础任务，感知端负责感知并处理外部环境的多模态信息，行动端负责利用工具执行行动。系统框架#2：AI Agent = LLM大模型 + Planning规划 + Memory记忆 + Tool Use工具使用，其中LLM作为核心控制器，充当Agent的大脑，而其他三个关键组件赋予LLM执行复杂任务的能力。

**应用篇：单代理和多代理并举，任务解决和游戏场景落地较快。** 年初至今Agent应用加速涌现，例如AutoGPT、GPT-Engineer、Voyager等单代理应用和MetaGPT、斯坦福虚拟AI小镇等多代理应用，**OpenAI的GPTs和GPT-Store则有望成为Agent生态雏形。**我们认为，目前Agent仍以任务解决型和娱乐型应用为主，在个人助理和游戏领域落地较快，未来有望向通用的企业服务、垂直的金融、医疗、电商等领域拓展。

**前瞻探讨：软件架构或将重塑，Agent as a Service有望成为潜在商业模式。**我们认为，目前Agent距离真正大规模商业化落地仍有较大距离，需要提升大模型的基础能力（复杂推理和泛化能力，幻觉和延时问题）、多模态能力和解决多模块、多代理交互问题，以及考虑实际部署中的成本管控等。长期维度看，Agent或是大模型时代重要的落地方向，有望重塑人机交互方式和软件架构，推动AI基础设施化和商业模式向代理即服务演进。


**风险**


技术发展不及预期，行业竞争加剧，商业化落地节奏不及预期。


**Text**


**正文**


图表1：AI Agent全文框架图


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmPWwX3P2iaMicTUbUDdzwHyuPTXqnvvQAUOT6Hqooiafk6Nt5fbiauNKK3A%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：中金公司研究部


**概览：基于LLM的自主智能代理，朝AGI更进一步**


**何为AI Agent？**


**AI Agent（人工智能代理）是一种能够感知环境、自主决策并执行动作的智能实体。** 由于Agent涵盖范围广泛且AI Agent的发展仍处于早期，目前学界对于AI Agent的定义尚未达成共识。2000年，赵龙文和侯义斌在《Agent的概念模型及其应用技术》中提出\[1\]，AI Agent是一个运动于动态环境的、具有较高自制能力的实体，该定义后续被国内多篇文献所接受。2023年，复旦大学NLP团队在《The Rise and Potential of Large Language Model Based Agents: A Survey》中提出\[2\]，AI Agent能够用传感器感知环境、做决策、用执行器来执行动作。基于上述定义，我们认为AI Agent应当同时具备**环境感知性、决策自主性和动作自为性。**


图表2：AI Agent示意图


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmuEugJClTjoexhxyuenQsJHpG9L6NOpjdwZmLLqFib0N1qKo96wFXuVA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：中金公司研究部


**AI Agent相较ChatGPT有何进步？**


**我们认为，AI Agent和ChatGPT均基于LLM大模型，具备理解和推理能力，而AI Agent的进步之处在于：1）从具体功能维度，具备自主决策和行动能力；2）从呈现效果维度，能够自主完成大部分工作，人类仅需设立目标并监督；3）从技术创新维度，是大模型在工程学上的进一步迭代。**

**从具体功能维度来看，AI Agent具备独立思考和自主决策的能力，输出结果不依赖于prompt的清晰程度。**ChatGPT的回答效果取决于用户prompt的清晰准确程度，对于相对复杂的任务，ChatGPT需要用户给出分步任务指令，才能输出令人满意的回复；而AI Agent具备感知环境、独立思考并做出行动的能力，只要用户设定初始目标，AI Agent即可自行拆解任务、调用工具并输出优质回复，从而提升了易用性和便捷度，降低了用户使用门槛。以股票研究领域为例，只要用户给出"请帮我生成某公司3Q23业绩点评报告"的初始任务目标，AI Agent即可自行拆分任务、设计报告框架，调用工具完成从数据搜集到数据分析、再到图表制作等一系列子任务，并最终输出一份令人满意的点评报告。


图表3：ChatGPT与AutoGPT处理任务的流程对比


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmdsynHqSWhZk3Uh8tjgbxLjIbvYCPribRXpVlKjzDEzk3FJH0HKBZMvw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：中金公司研究部


图表4：AI Agent处理业绩点评报告任务示例


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmNbgKg672A1QQLxb3mPzg8hxIP7VGiaDTFfeIrqUQNnNRNicGfasiczb3Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：中金公司研究部


**从呈现效果维度来看，AI Agent具备行动能力，能够帮助用户完成具体任务，人类只需进行目标设定和过程监督。** ChatGPT具有较强的文本理解和推理能力，能够对用户提出的问题做出详细解答；而具备行为能力的AI Agent不仅能够像ChatGPT一样指出"如何做"，还能够代替用户"帮你做"。真格基金管理合伙人戴雨森将AI和人类协作的程度类比为自动驾驶的不同阶段\[3\]，初代ChatGPT相当于自动驾驶的L2级别，Copilot相当于L3级别，而AI Agent则相当于L4级别，可以在人类的监督辅助下充当"驾驶员"自主完成大部分工作。腾讯研究院则将人类与AI的合作由初级到高级分为Embedding、Copilot和Agents三种模式。与Copilot模式下人类主导工作、AI协助完成部分任务初稿相比，在Agents模式下，AI具备更强的任务拆分、工具选择和进度控制能力，人类只需设立目标、提供资源并监督结果，工作的具体展开可全权交由AI代理。


图表5：AI Agent可类比于自动驾驶的L4级别


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmdnM5EEJAAMJN3vIkUukBgD7ld0uo5dWs28oJ84O7ugURjZJqEKlNBA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：甲子光年，真格基金，中金公司研究部


图表6：人类与AI合作的三种模式


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmdM2I8s2KHTfwBn1OrnhwexenzhYyDC4a2P8kP8SLllVGjHZtVtcbuA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：腾讯研究院，中金公司研究部


**从技术创新维度来看，AI Agent是大模型在工程学上的进一步迭代。** 我们认为，大模型是基于工程方法的"大力出奇迹"，以数据、算法和算力等要素资源精巧组合的方式，实现了大模型从量变到质变的过程。而**AI Agent在LLM的基础上增加了规划、记忆和执行等功能模块，是工程方法上的延续性创新。**我们认为，AI Agent在工程学上的进步有望进一步推动AI学术研究和应用范式探索。


**发展历程：从符号逻辑到泛化学习，逐渐接近AGI**


自1965年首个专家系统DENDRA被提出以来，AI Agent在技术迭代方向上大致经历了从符号型Agent到反应型Agent，再到基于强化学习的Agent、基于迁移学习和元学习的Agent，最终到基于LLM的Agent的五个发展阶段。我们观察到，AI Agent的发展主要依赖于主流AI算法框架的演进，具有**从专用到通用，从基于符号逻辑到强调环境感知、再到重视泛化学习**的迭代特征。目前AI Agent的发展正处于基于LLM的Agent的阶段，各类Agent应用快速涌现。我们认为，基于LLM的Agent具体应用的落地有望迎来新一轮高潮。

就AI Agent的**未来发展前景** 而言，Yonatan Bisk等在《Experience Grounds Language》中提出\[4\]，从NLP走向AGI需要经历语料库、互联网、感知、具身及社会属性这五个阶段。复旦大学NLP进一步指出，目前LLM正处于第二阶段，具有互联网规模的文本输入和输出，**而在LLM基础上被赋予感知能力和行动能力的AI Agent则处于第三、第四阶段，**未来AI Agent或将基于LLM继续迭代具备社会属性，并有望组成Agent Society，带来有组织、有成效的合作，从而走向第五阶段，逐步接近AGI。


图表7：AI Agent的发展历程


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmicHnAy7zZBfFOaLLvJCKiaakGk5axn3jgz1RdGBiaCP0oT6KdX5b29zIg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Zhiheng Xi等（2023）《The Rise and Potential of Large Language Model Based Agents: A Survey》，中金公司研究部


图灵奖得主Yann LeCun在2023北京智源大会上指出，目前AI相较于人类和动物在逻辑推理和规划能力上仍有较大差距，而真正通往AGI的或将是**"世界模型"\[5\]** ；与目前主流的LLM模型相比，世界模型不但在神经水平和认知模块上贴合人脑，而且具备规划、预测和成本核算能力，能够真正理解世界\[6\]。我们认为，基于世界模型的AI Agent的概念设计和系统框架与人类的思维决策模式较为相似，**补齐了LLM大模型短板的AI Agent未来跨越式发展或可期。**


图表8：Agent Society


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmyHgwfh7icEWZtgldlt9dg1UkKu84JaHwAOzzr3jAxMQwTVIPbic1FVeQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Zhiheng Xi等（2023）《The Rise and Potential of Large Language Model Based Agents: A Survey》，中金公司研究部


图表9：世界模型


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkm5XCticicYHib7ibNe0j0DJFb9fX1iaEiaT8WQyGkGNeMaTRRk5oiaiaDB2mbVQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Anna Dawid和Yann LeCun（2023）《Introduction to Latent Variable Energy-Based Models: A Path Towards Autonomous Machine Intelligence》，中金公司研究部


**技术篇：以LLM为基座，拓展感知和行动等功能模块**


由于学界对AI Agent的理论研究仍处早期阶段，且过去更多专注于完成特定任务的专有领域Agent，所以现有文献对于Agent的整体技术框架讨论度相对较低。基于目前热度较高的两篇文章------复旦大学NLP团队的论文《The Rise and Potential of Large Language Model Based Agents: A Survey》和OpenAI安全团队负责人Lilian Weng的博客《LLM Powered Autonomous Agents》\[7\]，我们对AI Agent当前主流系统框架及观点进行梳理。**我们认为，目前AI Agent开发处于相对初级且快速进展的阶段，产品架构主要是在LLM大模型基础上叠加记忆、规划、行动等功能模块或组件，实则高度依赖大模型本身的能力，随着未来大模型和Agent相关研究逐步深入，AI Agent系统框架和组件形态或将发生较大的改变。**


**系统框架 #1：AI Agent = Brain控制端 + Perception感知端 + Action行动端**


**复旦大学NLP团队在今年9月提出\[8\]，AI Agent的概念框架包括Brain（控制端）、Perception（感知端）和Action（行动端）三个组成部分：**控制端承担记忆、思考、决策等基础任务，感知端负责感知并处理来自外部环境的多模态信息，行动端则负责利用工具执行，从而对外界环境产生影响。


图表10：AI Agent = Brain控制端 + Perception感知端 + Action行动端


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmLlQWjJvLP4bW7s0BIZC0IRqOKPV650gibZSSgqE4yRFJ8BUEELl6cQA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：基于复旦大学NLP团队的论文《The Rise and Potential of Large Language Model Based Agents: A Survey》（2023）总结  
资料来源：中金公司研究部


图表11：AI Agent的工作示例


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmBnQiamT6cJFufzS3UrWrY0U3L6WnqGrYEcOrGicvyJpFkLww5QhOtTOQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Zhiheng Xi等（2023）《The Rise and Potential of Large Language Model Based Agents: A Survey》，中金公司研究部


**系统框架 #2：AI Agent = LLM大模型 + Planning规划 + Memory记忆 + Tool Use工具使用**


OpenAI安全团队负责人Lilian Weng在今年6月提出\[9\]，在基于大模型的自主代理系统中，LLM作为核心控制器，充当AI Agent的大脑，具备推理能力，而其他三个关键组件Planning、Memory和Tool Use或将赋予LLM执行更加复杂的任务的能力。


图表12：AI Agent = LLM大模型 + Planning规划 + Memory记忆 + Tool Use工具使用


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmWM01icwyCOe5qxLDwY7BYOZQM7MlGNJMwicqvvb3fcymH2uRnnXD9dsw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：基于OpenAI安全团队负责人Lilian Weng的博客《LLM Powered Autonomous Agents》（2023）总结  
资料来源：中金公司研究部


**应用篇：单代理和多代理并举，任务解决和游戏场景落地较快**


年初至今的大模型浪潮席卷全球，推动AI Agent相关研究快速发展和应用加速涌现，我们认为这些Agent应用不仅是对现有系统框架的初步验证，也是引导系统框架进一步完善的基础，从而有望推动AI Agent在理论和实践层面进一步加速发展。我们认为，AI Agent应用的目标应主要包括：**1）将人类从重复性的劳动中解放出来，提高工作效率；2）不依靠低级指令，自主分析、规划并解决问题；3）协助人类从事探索性和创新性的工作。**下文我们将梳理AI Agent的应用范式、能力评判标准和现有的应用实例。


图表13：应用篇：单代理和多代理并举，任务解决和游戏场景落地较快


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmTUqOVNW8VQajDB4l2H6bh0NK4Ond4iamibPklT4yvH8IZSFibKIHXGLgw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：中金公司研究部


**应用范式：单代理、多代理、人机交互**


AI Agent的应用范式一般可以分为单代理模式、多代理模式和人机交互模式三种。


图表14：AI Agent的三种应用范式


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmeXT01S2OXFfSZxqdn06OKxZ9Z67iahbOpECjElL202wU2V0pvj39MGw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Zhiheng Xi等（2023）《The Rise and Potential of Large Language Model Based Agents: A Survey》，中金公司研究部


**单代理模式：任务导向、创新导向、生命周期导向**

单代理目前一般被应用于某一特定的流程，或者具有特定场景的任务中，基于任务拆解、环境感知及交互等能力，目前单代理已在创意、代码生成、工作流程优化、游戏等领域中表现出较为出色的任务解决能力。按照**目标导向**不同，单代理一般可以分为任务导向、创新导向和生命周期导向三个层次。


图表15：单代理模式的三个层次


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmAyyGOdR58PAeRtdksSDouJzicN1liasXFIfOZbA5sEy4ufEicHiaYyQgLw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Zhiheng Xi等（2023）《The Rise and Potential of Large Language Model Based Agents: A Survey》，中金公司研究部


**► 任务导向层次：AI Agent需要理解高层次命令并帮助人类处理日常基本任务。** 随着LLM的发展，目前测试AI Agent任务处理能力的虚拟环境变得越发复杂真实，其大致可以分为网络环境和生活环境。**1）** 在**网络环境** 中，AI Agent需要处理填写表格、网购、发送电子邮件等网站导航任务，须具备在复杂网络环境中准确理解指令、适应网页变化、做出正确行动的能力，是未来AI Agent妥善处理未知任务的基础；**2）** 在**生活环境**中，AI Agent则需要处理洗衣做饭、开关电器等日常家务，须具备理解隐含指令、整体感知周围环境、应用常识知识和在不经额外训练的情况下将高级任务分解成子任务的能力。

**► 创新导向层次：AI Agent需要在前沿科学领域中展现出自主探索的能力。**根据Brian K. Lee等在《A Principal odor map unifies diverse tasks in olfactory perception》中的研究表明\[10\]，AI Agent可用于计算一张包含50万种不同气味的气味图谱，并能将气味表征和分子结构建立连接，从而初步验证了AI Agent在创新导向部署中的可能性。但考虑到前沿科学具有高度复杂性，术语难以用单一文本表示，且目前科学领域合适的训练数据集较匮乏，因此我们认为目前将AI Agent广泛应用于探索前沿科学或面临一定的技术局限。

**► 生命周期导向层次：AI Agent需要具备在开放世界中不断探索、学习、使用新技能，并长久生存的能力。**由于现实中的生命周期时间过长、成本过高，而游戏中的生存环境可以近似地被视作现实世界的缩影，所以科学家往往基于《我的世界》游戏平台开发并测试AI Agent的生存能力。我们认为，目前在LLM加持下，Voyager（英伟达，2023）等AI Agent已初步具备了处理复杂模拟生存任务的高级规划能力，这在一定程度上是生命周期导向AI Agent发展潜力的初步呈现；但游戏场景和现实世界之间的差异不可忽视，未来跳脱出游戏场景、且能适用于现实场景的生命周期导向AI Agent或是更值得期待的里程碑式跨越点。

**多代理模式：合作型交互、对抗型交互**

1986年，Marvin Minsky在《Society of mind》中前瞻性地提出\[11\]，智力是在众多小型的、具备特定功能的AI Agent的相互作用中产生的。这一思想之后通过多代理系统（Multi-Agent System，MAS）得到实践，而强化学习与深度学习算法的结合是开发能在复杂环境中运行的多代理系统的重要技术手段。我们认为，单代理缺乏从社会互动中获取知识的能力，故而无法部署于需要多代理合作或需要信息共享的复杂场景；而多代理可以通过专业分工深化各代理处理某一子任务的技能，消除子任务切换的时间，从而提高工作效率与输出质量，并拥有更广泛的应用场景。**多代理之间的交互一般可以分为合作型交互和对抗型交互。**


图表16：多代理模式的两种交互体系


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmtte4mPqkYicq9q71CoiaWfBxfiaa3Q7p4jWxZXiasNsHIIAXhnGwNTfI2Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Zhiheng Xi等（2023）《The Rise and Potential of Large Language Model Based Agents: A Survey》，中金公司研究部


**► 合作型交互：** 合作型交互被普遍认为是目前应用最广泛的形式，可以提高工作效率、改进集体决策并解决单代理无法解决的复杂现实问题。在合作型交互体系中，每一个AI Agent都需要评估其他AI Agent的需求及能力，并积极分享信息、实施合作行为。目前合作型交互一般可以分为无序合作和有序合作：**1）** 在**无序合作** 时，所有的AI Agent都将直接接触任务本身并自由发表观点；**2）** 而在**有序合作**时，只有少数AI Agent会接触任务本身并主导任务开展，其余绝大部分的Agent则只需关注来自其他同伴的输出结果，同时，Agent之间的交流需要遵循某种规则，例如以流水线的方式或角色扮演的方式依次发表观点。


图表17：合作型交互的两种形式 ：无序合作和有序合作


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmJmg8ibicMdHDXIos1qQGpEggsQicficR9xbHvcpibvZv7icuy8YeibUOFtupw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmOibljFIG7xGXU1QDNHNA23Eic05GokUcDm0ZY1vyTmxhx0gf668ZtZTg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：上图为无序合作模式，下图为有序合作模式  
资料来源：Rui Hao等（2023）《ChatLLM Network: More brains, More intelligence》\[12\]，Varun Nair等（2023）《DERA: Enhancing Large Language Model Completions with Dialog-Enabled Resolving Agents》\[13\]，中金公司研究部


**► 对抗型交互：**在对抗型交互体系中，AI Agent通过竞争、谈判、辩论等"针锋相对"的形式进行互动，从而帮助它们更好地反思自己之前的行动，并最终提升整个体系的回复质量，适用于需要高质量回复和准确决策的场景。Chi-Min Chen等在《ChatEval: Towards better LLM-based evaluators through multi-agent debate》中提出了一种对抗型交互体系ChatEval\[14\]。ChatEval建立了一个基于角色扮演的多代理裁判团队，通过自我发起的辩论，AI Agent能够对文本质量产生与人类更一致的评估结果。同时，对于裁判团队中的每一个AI Agent，只有要求其扮演不同的角色，ChatEval体系才能有效提高评估质量。


图表18：ChatEval流程


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmu5mAX0boXuKYcRepxEoEfu47CjibVbNYObTnemKj6hQrDJxmS6ou32A%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Chi-Min Chen等（2023）《ChatEval: Towards better LLM-based evaluators through multi-agent debate》，中金公司研究部


**多代理模式仍需进一步发展。** 我们认为，多代理模式目前尚不成熟，以对抗型交互体系为例，虽然对抗型交互体系前景广阔，但是仍然面临以下三大挑战：**1）** 对于过长的辩论，LLM无法完整输入上下文；**2）** 多代理环境下计算成本显著提升；**3）**多代理可能达成一个错误共识。

**人机交互模式：不平等交互、平等交互**

在人机交互模式下，AI Agent需要与人类交互，并合作完成任务。一方面，人机交互可以有效弥补数据缺失问题，使得AI Agent处理任务的过程更为顺畅；另一方面，我们认为，目前AI Agent的可解释性稍显不足，可能存在安全性、合法性、道德性等方面的隐患，客观上需要人类参与监督并进行规范。**目前人机交互一般可以分为不平等交互和平等交互。**


图表19：人机交互模式的两种体系


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmmnebPQ9puTQdqw2OSib8Oe70RcwbKVE88K03AvfBgELOtzkBPtmYuyA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Zhiheng Xi等（2023）《The Rise and Potential of Large Language Model Based Agents: A Survey》，中金公司研究部


**► 不平等交互（指导者-执行者）体系：人类作为指导者给出指令并反馈意见，而AI Agent作为执行者执行指令并根据指令和反馈意见动态优化执行行动。**这种体系需要人类付出大量努力，甚至需要高水平知识以帮助AI Agent完成部分任务。为了缓解人力投入过高的问题，AI Agent可以被授权自主完成任务，并由人类提供定量或定性的反馈。

**► 平等交互体系：AI Agent与人类没有地位上的差异，而是以合作伙伴的形式参与并完成日常工作。**在消费者偏好和使用体验层面，人们或许更希望AI Agent具备共情能力，以伙伴而非机器的角色参与工作；在技术层面，目前学界不仅成功赋予AI Agent从人类表情中理解情绪并输出情感共鸣的能力，而且Agent能够动态调节自身的情感基调，并调整自身的语气和表情。而在应用层面，目前AI Agent已经在围棋、象棋、谈判等场景中展现出类人、甚至超人的能力。我们认为，上述现象表明人机平等交互模式已经展现出在日常生活场景中一定的应用潜力，未来有望进一步融入人类社会。


**AI Agent应用分类及实例**


年初至今的大模型浪潮席卷全球，基于大模型的Agent应用也随之涌现并获热烈反响，例如今年3月单代理应用AutoGPT发布仅一个月即登顶GitHub Trending第一名\[15\]，8月斯坦福大学发布的虚拟AI小镇亦引发人们对Agent Society的诸多联想。**我们认为，目前AI Agent仍以任务解决型和娱乐型应用为主，在个人助理和游戏领域落地较快，未来有望向通用的企业服务、垂直的金融、医疗、电商等领域拓展。**下文我们将分别从单代理和多代理场景，介绍AI Agent的应用分类和现有实例。


图表20：GPT大模型浪潮带动AI Agent应用大量涌现


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmyVdcf4T2SoRDgCC6ZTeewwmErh8GUcU2fnHibZq3hdsOYkqSliar6jicw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Lei Wang等（2023）《A Survey on Large Language Model based Autonomous Agents》\[16\]，中金公司研究部


**单代理应用**

**► OpenAI发布类Agent应用**

**OpenAI支持用户自定义GPT，AI Agent或将是未来大模型应用角逐焦点。**自ChatGPT推出以来，用户一直期待能够实现定制化应用，在2023年11月的开发者大会上，OpenAI推出一系列类Agent应用，向用户提供走向定制化Agent领域的必需品。我们认为，OpenAI此举大大降低了自定义开发的门槛，并有望充分挖掘社区开发者的力量。

**面向开发者：Open AI推出Assistants API，帮助开发者在自己的应用中构建AI Agent。**Assistants API提供代码解释器（Code Interpreter）、检索（Retrieval）、函数调用（Function calling）等新功能，能帮助开发者构建编码助手、旅游计划制定助手等AI应用，简化繁重复杂的开发流程。目前Assistants API测试版已经开放，所有开发者均可使用。

**面向个人用户：OpenAI发布GPTs、GPT-Store，支持个人自定义版本ChatGPT。**GPTs赋予每个用户代理权，针对个性化需求，用户可以通过自然语言对话GPT进行编程，而无需代码能力。例如，用户可以帮助教师制作包含课程和专业知识的教学规划GPT，或创建专门为创业者提供建议的咨询服务GPT等。而GPT-Store则为GPTs提供共享平台，OpenAI将与GPTs开发者共享收入。


图表21：Assistants API功能


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmEZ7Rl3cDIZTpEshxsBr25IECEQPgvL277WbNYrxQIMMibxQC85QJKcA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：OpenAI开发者大会，中金公司研究部


图表22：GPT-Store界面


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmPnE3SKMTJ7EUMTpiaZe33tU1d2DM7KW4tW3mm5UKf8bmJJUcj2B313w%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：OpenAI开发者大会，中金公司研究部


**► AutoGPT：通用型自动化GPT助手（实验性项目）**

**AutoGPT是一款以GPT-4为基础开发的自动文本生成软件，目前在众多AI Agent应用中拥有最高的GitHub热度。**它能够在用户给定目标的情况下，自主分解、操作并最终完成任务，其功能包括自动化信息检索、文本生成、内存管理、信息总结归纳等。

**作为Agent开源领域领先项目，AutoGPT逐渐收获开发者以及投资人关注。**2023年3月16日，为实验GPT-4能否在人类商业世界中获利，Significant Gravitas在GitHub上首次提出该项目，4月3日登顶GitHub Trending第一名，截至目前在GitHub获星已超过15.5万。特斯拉前AI总监、现OpenAI技术人员Andrej Karpathy称AutoGPT为"提示工程的下一个前沿"\[17\]。2023年10月14日，专注于早期阶段科技公司的风投公司Redpoint Ventures为AutoGPT投资1200万美元，新资金将用于扩建团队，继续开发开源项目。


图表23：网页版AutoGPT接口


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmsm3RqcHvtXQ68RXBjg2A96Fglp8bPQkJ6gCcy6743AibWLV8aqZJJZw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：AgentGPT为基于AutoGPT搭建的网页版Agent  
资料来源：ArronAI公众号，中金公司研究部


图表24：AutoGPT在GitHub获收藏数量


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmHVmia4f2N8qW8Sf5syhL7KGsCxBFMPnLIzh0MZ3DdfQFkDicibx9miaSgg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：GitHub官网，中金公司研究部


**AutoGPT可以自行拆解复杂任务，并在每个步骤实现自主决策，无需用户参与即可解决问题。**AutoGPT处理复杂任务的具体流程可拆分为下发任务、理解任务、生成方案、生成指令、执行指令、输出结果和评估结果这七个步骤。当用户输入指令后，AutoGPT会自动根据上述步骤处理任务，并实现AutoGPT对任务的全权托管。

**AutoGPT可调用多个外部工具，增强任务处理和任务反思能力。1）** AutoGPT能够克隆GitHub仓库，从而调用其他AI Agent辅助完成文本翻译、图片生成等任务；**2）**AutoGPT通过集成Pinecone数据库具备长期内存存储能力，从而能够保存上下文并基于此进行决策改进。但是，AutoGPT使用工具的范围受到API接口的限制，目前AutoGPT在GitHub上完全开源，支持JavaScript、Python等多种语言，并可接入GPT-4、GPT-3.5模型。

**AutoGPT与ChatGPT的能力区别主要体现在：**1）AutoGPT具备浏览网页、获取信息功能，更类似GPT-4赋能下的微软Bing搜索引擎。2）AutoGPT执行任务过程中的多轮提问环节交由机器完成，具备自主判断决策、连续进行多个操作的能力，而ChatGPT需要用户不断输入提示词才能完成任务；3）AutoGPT拥有更长时期的记忆以及自主迭代能力，在运行过程中可以自主进行更多轮的对话。

**AutoGPT的应用场景包括开发代码程序、整理工作计划、市场研究等。**根据不同功能，AutoGPT可以被分成TravelGPT（旅行规划助手）、CalculusGPT（微积分学习助手）、HustleGPT（市场调查助手）等细分应用。以要求TravelGPT提供去夏威夷旅行的详细指引为例，用户在输入相应指令后，TravelGPT会自动拆解任务，并为用户提供详细的旅行日程安排、食宿解决方案及信息来源，大幅降低了用户旅行规划的难度和成本。


图表25：AgentGPT输入任务目标


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmCvWnic3bUCr63gcg9jiaNCWrAjXWdqpcl0ZSpo6RX0micjQq7c7f920Cg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：ArronAI公众号，中金公司研究部


图表26：AgentGPT理解、拆分任务


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmtibkxbt2IdvVxibjZce8vlyicjeA4WSmzoiaq43ba002I81w7Gia2eVqnIg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：ArronAI公众号，中金公司研究部


**► Adept.AI：2B领域工作流构建器（落地应用）**

**Adept.AI的目标是基于生成式AI建立全新的通用操作工具，致力于自动化任何软件程序，充当"AI Teammate"角色来帮助人类完成工作，** 即用户可以通过使用语音或文字下达指令，由AI理解后帮助用户完成各种操作和任务。根据SimilarWeb数据，2023年2-11月内，Adept.AI周度访问量一度超过20万。目前Adept的功能主要依托其**自研大模型Action Transformer(ACT-1)**实现，该模型经过对Fuyu模型的微调和优化，不但具有UI理解、图形图表理解和执行任务的能力，而且可以连接Chrome浏览器，并执行点击、输入、滚动等操作。Adept的运行特点集中在以下几方面。

* **Adept是一种多模态AI代理，能够模拟人类使用软件的方式。**Adept能够通过像素直接感知屏幕，并通过坐标和按键在计算机上执行操作，从而实现在无需创建数百个API集成、管理用户登录凭据的情况下扩展功能。

<!-- -->

* **Adept的每一个操作步骤均在用户可视化监督的情况下进行。**Adept会提示用户提供所需的信息，并保证每个操作步骤对用户可见，我们认为，此项特性体现出公司对于完全自主代理安全性的高度重视。


图表27：用户命令Adept寻找房源


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmG98EiaSZwTpHmJ5ibYfUOj2oIotL2Libv5zgT0iciaiagBh17ibE8NR7FB4XQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Startup Research公众号，中金公司研究部


图表28：Adept分步骤执行命令


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmicIdgPdwHR6jFJfBic47zdrZbxC9Y99gxFBgurJJNOpibaNRhK81ZRtTg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Startup Research公众号，中金公司研究部


**Adept.AI创始团队包括Transformer架构提出者，最新估值超10亿美元。**Adept.AI创始团队包括Ashish Vaswani、Niki Parmar和David Luan，其中Ashish Vaswani和Niki Parmar曾就职于谷歌AI研究部，于2017年提出Transformer模型；David Luan于2017年加入OpenAI，并基于Transformer模型构建GPT-2和GPT-3模型，后于2019年加入谷歌研究部门担任技术主管。在2022年底Ashish Vaswani和Niki Parmar离开Adept.AI后，David Luan接任管理层职能。自2022年成立以来，Adept AI先后得到包括Linkedln创始人Reid Hoffman、特斯拉前AI总监Andrej Karpathy在内的多名业界名人注资。2023年3月，Adept.AI宣布获得来自微软、英伟达等公司的3.5亿美元融资，累计融资4.15亿美元，最新估值突破10亿美元\[18\]。

**► Voyager：终生学习的游戏智能体（实验性项目）**

**Voyager是英伟达于今年5月推出的首款基于GPT-4的嵌入式终生学习代理。**Voyager能够在《我的世界》游戏中自主探索，并能根据环境反馈修正错误、迭代技能，从而展现出更强的终生学习能力和更高的游戏掌握水平。根据Guanzhi Wang等在《Voyager: An Open-Ended Embodied Agent with Large Language Models》中的研究表明\[19\]，Voyager在游戏中获得的独特物品增加3.3倍，行进距离增加2.3倍，解锁关键科技树里程碑的速度则加快15.3倍。


图表29：Voyager获取独特物品的能力大幅提升


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmPY7QeS35n8lficT24CfVHdyz0P44NAHdOexCrx2Y5KOM0WX5E1UVeBA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Guanzhi Wang等（2023）《Voyager: An Open-Ended Embodied Agent with Large Language Models》，中金公司研究部


**Voyager主要包含自动教程、迭代提示机制和技能库三大组成部件。**其中，自动教程由GPT-4根据"尽可能多地发现不同的东西"的总体目标生成，它会在考量自身状态和目前的探索进度后提出难度逐步上升的探索任务。迭代提示机制引入环境反馈、错误追踪和检查任务完成状态的自我验证这三种反馈，基于上述反馈，GPT-4将自行迭代提示直至自我验证通过，即完成当前任务。技能库则储存了用于完成任务的行动程序，每一个行动程序都通过相应的内嵌描述进行标注，从而可以在将来类似的情况下被检索并调用。


图表30：Voyager的三大组成部件


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmdyr5dICdeVCsB5fl8stE1fgicuHibt1gExnnYWcu6HCJiaTdj6uCcFSvA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Guanzhi Wang等（2023）《Voyager: An Open-Ended Embodied Agent with Large Language Models》，中金公司研究部


**► 澜码科技（未上市）：国内2B领域的垂直场景Agent（落地应用）**

**澜码科技致力于将专家知识数字化，打造企业智能大脑。**区别于其他Agent通过公开信息渠道获得显性知识的能力，澜码科技Agent与垂直行业领域专家开展合作，通过积累专家行为数据及与专家的互动反馈数据，具备习得隐形知识（即专家多年工作积累的行业经验）的能力，从而有助于提高Agent在特定行业的精确度和工作效率。澜码科技在2023年8月完成千万人民币级A轮融资，投资者包括IDG资本、Atom Capital等。

**依托CEO周健在工作流程自动化领域的深厚经验，公司有望迎接LLM模型提升自然语言理解能力的历史机遇。**创始人周健曾在RPA软件厂商弘玑Cyclone 担任CTO，并在Google美国总部、阿里云盘古和MediaV等企业拥有丰富的分布式系统研发经历。周健认为，出于降本增效需求，B端客户对高精确度、高效率Agent具有强付费意愿，而LLM大模型能力飞跃拓宽了企业业务智能化范畴，为传统RPA无法解决的复杂规则场景自动化提供了可能，Agent可以通过自然语言习得专家经验，在企业全局角度实现业务流程优化。


图表31：澜码科技专家Agent应用场景


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkm5MspyE1f0RiciceFvkwml244pNlCcibZ0FV6CibCk3u3ibqRhyDmm1uphPQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：甲子光年，中金公司研究部


**澜码科技提供将企业员工标准工作流程（SOP）自动化的智能中台，提升业务推进效率。**以招聘场景为例，经过该领域专家（即资深HR）提供的隐形知识的赋能，Agent平台能够分析企业招聘需求，从而协助一线招聘员工以自然语言对话方式筛选候选人简历，降低平均对话轮次，进而减少招聘员工的工作量。同时，Agent平台可根据运行实际情况通过进行候选人标签个性化匹配，在简历筛选优先级、筛选标准条件等方面反馈建议。


**多代理应用**

**► 斯坦福虚拟AI小镇：人类行为的交互式模拟（实验性项目）**

**为探索多代理智能体的能力边界，斯坦福大学的研究团队创造了名为Smallville沙盒虚拟城镇。**25个具有自己的个性和背景故事AI Agent在其中生存、交互、从事复杂行为，组成数字化的西部世界。这些智能体模拟人类行为，在小镇中工作、闲聊、组织社交活动、结交新朋友，目标是创造出一个具有连贯记忆和行为的代理社会，能够进行社交互动和响应环境变化。

**斯坦福虚拟AI小镇自推出后便受到广泛关注，其在RPG、模拟类游戏领域的前景尤其令人期待。**目前项目已在GitHub开源，英伟达资深科学家Jim Fan评价："斯坦福的虚拟小镇可谓2023年最令人震撼的AI Agent试验之一，一群AI能够共同演绎一部完整的文明进化史\[20\]。"


图表32：Smallville小镇场景


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkm7kRpQfTJAkIA2FRJyaFTnSgB16cv8yrr9icBltMgSOR63iagQ3YDvnfA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Joon Sung Park等（2023）《Generative Agents: Interactive Simulacra of Human Behavior》\[21\]，中金公司研究部


**研究者提出了包括记忆流、反思和计划三个模块的Agent架构。**它扩展了大语言模型，能够使用自然语言存储Agent的经历，进行高层次推理，并利用相关记忆制定行动计划，最终用户可以使用自然语言和全镇的25个Agent实现交互。


图表33：智能体的生成代理架构


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmFQmhQ7hmaev5Fflb4nPLNCUDPlrYrkjSj8XiaD126xLLBxmMZpu2KibQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Joon Sung Park等（2023）《Generative Agents: Interactive Simulacra of Human Behavior》，中金公司研究部


**► 面壁智能ChatDev：国内多代理软件开发的SaaS平台（落地应用）**

**ChatDev是业内首款将AI Agent群体智能协作技术应用于软件开发的SaaS平台产品。**ChatDev由清华大学联合面壁智能、北京邮电大学和布朗大学于2023年7月正式推出，凭借帮助用户以极低成本和门槛高效完成软件开发工作的功能收获全球热烈反响，并屡次登顶GitHub Trending。11月15日，面壁智能正式推出基于群体智能的AI原生应用"面壁智能ChatDev"智能软件开发平台。


图表34：ChatDev界面


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmO63fygEEQbkP0oxJBC0BskBmOgVibx69OMao6wfnvMCFHO4MGz0Xr5w%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：面壁智能公众号，中金公司研究部


图表35：ChatDev在GitHub收获热烈反响


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmNbqxgwvLg4wRzibYArnyAytAsnacMBJKCh8SK9KYZeayAPk5EtPjV2w%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：GitHub官网，中金公司研究部


**ChatDev构建了全流程自动化软件开发框架，可理解为"对话驱动的虚拟软件开发公司"。**ChatDev借鉴软件工程瀑布模型，将软件开发分成软件设计（Designing）、系统开发（Coding）、集成测试（Testing）和文档编制（Documenting）四个主要环节，并对这些环节做进一步分解，最终形成由若干子任务构成的交流链（Chat Chain），其中每个子任务均由一个扮演产品设计师、测试工程师等不同角色的AI Agent负责执行。当用户通过自然语言提出任务需求后，扮演不同角色的Agent将进行对话式信息交互和决策，从而生产出一个包括源代码、环境依赖说明书、用户手册等在内的完整软件。


图表36：ChatDev软件开发流程


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmm1yHn3tc447cAIfbjPdbeoj60umXWzzX7BUkEJDEgewgAJTF7QWJuA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Chen Qian等（2023）《Communicative Agents for Software Development》\[22\]，中金公司研究部


**ChatDev大幅降低了软件开发的时间成本和技术门槛，有望进一步赋能生产力提升。** 我们认为，ChatDev的优势主要包括：**1）效率高：** 使用ChatDev时无需进行专业复杂的prompt探索或具备专业知识，只需简单的需求说明即可全权交由AI Agent完成工作，大大缩短了软件的开发时间；**2）可共创：** 用户不仅可以监督软件开发过程，还可实时参与AI Agent的工作实现人机共创；**3）可定制：** 用户可以根据个人喜好更改AI Agent在交流链中扮演的角色，并调整软件的部分功能，实现软件开发的私人定制。**我们认为，未来随着大模型逐渐迭代更新，类ChatDev产品的应用场景有望从软件开发领域拓展至工业、医疗、教育等众多领域，从而带来生产效率的进一步提升。**


**前瞻探讨：软件架构或将重塑，Agent as a Service有望成为潜在商业模式**


**展望未来5-10年，我们认为AI Agent或将是大模型时代重要的落地方向，有望重塑人机交互方式和软件架构，推动AI基础设施化和商业模式向代理即服务（Agent as a Service，AaaS）演进，或将为人们的生产生活方式带来全新可能。**仅就当下发展阶段而言，我们认为虽然目前Agent的项目分类较多，但大多以简单的任务解决型应用和娱乐型应用为主，均未达到PMF( Product Market Fit）节点\[23\]，距离真正大规模商业化落地仍有较大距离，同时我们认为应持续关注潜在的安全与伦理风险。


**长期展望：有望带来人机交互范式、软件架构、商业模式等全方位革新**


**理想状态下，AI Agent应兼具工具属性和人格属性，有望带来人们观念的跃迁。**目前大多数AI应用的定位是提高效率、解放生产力和提升创造力的生产工具，以满足人们的信息需求，具备明显的工具属性；同时也存在部分如Character.AI角色扮演型聊天机器人等AI应用，满足人们社交、陪伴、支持等情感社交需求，具备一定的类人属性。我们认为，长期来看，AI Agent应同时具备工具属性和人格属性，有望引发人们思想观念的跃迁。


图表37：AI Agent有望在长期增强人格属性，带来人们观念的跃迁


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmOHc1Cy1VJFLGEVDrwyL6ku60B7cL8CgR0wqbOvCumbx4dZcrZtoQHA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：聆心智能，清华大学，中金公司研究部


**AI Agent有望带来人机交互方式的变革。** 目前的人机交互方式主要以图形界面和触控交互为主，我们认为未来AI Agent有望成为操作系统级别的入口，实现"对话即接口"的全新人机交互范式，或将带来全新的软件服务形态。


图表38：AI Agent有望带来人机交互方式的变革


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmJcMHbSkBXjib6ROPzzDGw9oFhTXSW5ovGu7SbYKsqicJmHvdz5qxjAcw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：聆心智能，清华大学，中金公司研究部


**AI Agent或将使得软件架构从过程导向迁移到目标导向，推动AI基础设施化。** 从软件架构角度，现有的软件通过一系列预定义的指令、逻辑将流程标准化沉淀，具有明显的过程导向特征，软件具备高确定性、可靠性，但不具备跨领域泛化能力。我们认为，未来软件产品形态有望以AI Agent为核心，将传统软件预定义的部分调整成由Agent自主生成，**化过程导向为结果导向，** 并将任务解决范围拓展至无限域。同时，Agent所具备的能够自主完成大多数任务、人类进行目标设定和过程监督的特征**有望推动AI基础设施化，生产方式或将从以人为核心、AI为辅助，向以AI为核心、人为辅助演进，在长期有望迎来Agent-Centric时代。**


图表39：软件架构从过程导向迁移到目标导向，长期有望迎来Agent-Centric时代


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmaWIgIP3vXSDY7LKNprNNH3kLhwQ14YliaWMVJnI3zWEOhFYzIqiarL5Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：腾讯研究院，深度学习公众号，中金公司研究部


图表40：RPA范式与APA范式的比较


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkm3cwVR7YPjNGrZgD7WMMqK89GcgQOjZSLNa6g6wHt1Fibk8paBvr65dw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：RPA即Robotic Process Automation；APA即Agentic Process Automation  
资料来源：Yining Ye等（2023）《Proagent: From Robotic Process Automation to Agentic Process Automation》\[24\]，中金公司研究部


**在商业模式上，代理即服务（Agent as a Service，AaaS）或是潜在方向。**Zhiheng Xi等指出\[25\]，由于AI Agent比LLM模型本身更为复杂，未来中小型企业或个人很难依靠自身力量在本地独立构建。因此，我们认为未来海内外科技大厂或将逐步构建AI Agent生态体系，为广大开发者自主构建、自由交易Agent具体应用提供底层算力基础设施并打造Agent共享平台，从而逐渐把先发优势转化为生态壁垒。2023年11月，OpenAI在首届开发者大会上重磅宣布将推出GPTs的共享平台GPT-Store\[26\]，我们认为，这不仅有望为OpenAI构建生态繁荣筑基，还有望引导商业模式向构建类Agent生态的方向演进。


图表41：AI Agent有望推动云+AI基础设施厂商着力建设生态，以代理即服务为商业模式


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmsdhYHdiaGPguvmYWTZ7ibknrcf7o6gAziagqnE9zYXe5Qz5BUicmeCBWYw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：中金公司研究部


**从迭代方向上，AI Agent下一步有望朝着多方向、多维度同时发展。**我们认为，随着后续AI Agent系统框架逐渐完善、大模型基础能力和多模态能力的提升，AI Agent应用有望从垂直行业场景发展到通用领域，从完成特定任务拓展到创新任务，在互补流程、任务范围等层面与人类更紧密地合作，最终逐步形成Agent Society，进一步向通向AGI的道路迈进。


**潜在风险和落地难点：道阻且长，面临技术、成本、监管等多方面挑战**


**落地难点：跨越PMF节点需要在技术、成本等多方面共同发力**

**我们认为，AI Agent距离真正大规模商业化落地仍有很长一段路程要走。** **1）** 从**技术角度，** 由于大模型是AI Agent的重要基座，因而大模型的基础能力提升尤为关键，其中，复杂推理、泛化等能力提升和"幻觉"、延时等问题的解决几乎势在必行；同时，在多模态方向取得显著进展是AI Agent未来发展的前提条件；此外，Agent各模块之间如何配合、多个Agent如何交互、人类与Agent如何互动等方面均存在较大的技术提升空间。**2）** 从**成本角度** ，Agent产品需要将真实业务场景和工作流转化为底层大模型能理解的数据、进行多模块和多代理之间的交互，或将产生高昂的推理成本。一个好的Agent产品不仅需要解决用户的需求，同时也要考虑实际部署中的成本管控问题。**3）** 如果Agent能在**具身智能**方向取得较大进展，从而影响真实物理世界，有望带来巨大发展潜力。


图表42：大模型"幻觉"现象示例


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmTGN7GEALVMGFwA36hIL71lpIDneKvxKCnjJOjhVO3Hsy4AJFLR0g8g%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Yue Zhang等（2023）《Siren's Song in the AI Ocean: A Survey on Hallucination in Large Language Models》\[27\]，中金公司研究部


**风险提示**


**技术发展不及预期。**AI Agent作为人工智能领域的前沿新兴概念，目前仍处于技术的快速发展期，其进展有一定的不确定性，若技术进展不及预期，可能导致产业化进展缓慢。

**行业竞争加剧。**AI Agent是大模型的重要落地方向，未来商业价值显著，海内外科技巨头、初创公司均在此领域布局，未来垂类及应用层的行业竞争可能会进一步加剧。

**商业化落地节奏不及预期。**商业化落地是AI Agent能否顺利走向下一阶段的关键点，若商业化落地节奏不及预期，对人工智能的进展将带来负面影响。


\[1\]赵龙文,侯义斌.Agent的概念模型及其应用技术\[J\].计算机工程与科学,2000(06):75-79.

\[2\]Zhiheng Xi. et al. The Rise and Potential of Large Language Model Based Agents: A Survey 2023. https://arxiv.org/abs/2309.07864.

\[3\]https://mp.weixin.qq.com/s?__biz=MzU5OTI0NTc3Mg==\&mid=2247526426\&idx=1\&sn=1cd7561db146e9df5cb61cdef4332ce2

\[4\]Bisk, Y., A. Holtzman, J. Thomason, et al. Experience grounds language. In B. Webber, T. Cohn, Y. He, Y. Liu, eds., Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing, EMNLP 2020, Online, November 16-20, 2020, pages 8718--8735. Association for Computational Linguistics, 2020.

\[5\]https://cloud.tencent.com/developer/news/1100246

\[6\]Anna Dawid, Yann LeCun. Introduction to Latent Variable Energy-Based Models: A Path Towards Autonomous Machine Intelligence 2023. https://arxiv.org/abs/2306.02572.

\[7\]https://lilianweng.github.io/posts/2023-06-23-agent/

\[8\]Zhiheng Xi. et al. The Rise and Potential of Large Language Model Based Agents: A Survey 2023. https://arxiv.org/abs/2309.07864.

\[9\]https://lilianweng.github.io/posts/2023-06-23-agent/

\[10\]Brian K. Lee. et al. A principal odor map unifies diverse tasks in olfactory perception 2023. https://www.science.org/doi/10.1126/science.ade4401.

\[11\]Minsky, M. Society of mind. Simon and Schuster, 1988.

\[12\] Rui Hao. et al. ChatLLM Network: More brains, More intelligence 2023. https://arxiv.org/abs/2304.12998.

\[13\]Varun Nair. et al. DERA: Enhancing Large Language Model Completions with Dialog-Enabled Resolving Agents 2023. https://arxiv.org/abs/2303.17071.

\[14\]Chi-Min Chen. et al. ChatEval: Towards better LLM-based evaluators through multi-agent debate 2023. https://arxiv.org/abs/2308.07201.

\[15\]https://www.yicai.com/news/101734133.html

\[16\]Lei Wang. et al. A Survey on Large Language Model based Autonomous Agents 2023. https://arxiv.org/abs/2308.11432.

\[17\]https://mp.weixin.qq.com/s/b04F8oQfRaY2z-FjzA4pMw

\[18\]https://news.pedaily.cn/202308/519817.shtml

\[19\]Guanzhi Wang. et al. Voyager: An Open-Ended Embodied Agent with Large Language Models 2023. https://arxiv.org/abs/2305.16291.

\[20\]https://mp.weixin.qq.com/s/tiZTxYn6Qo0ciizV5N5Irg

\[21\]Joon Sung Park. et al. Generative Agents: Interactive Simulacra of Human Behavior 2023. https://arxiv.org/abs/2304.03442.

\[22\]Chen Qian. et al. Communicative Agents for Software Development 2023. https://arxiv.org/abs/2307.07924.

\[23\]注：PMF是指产品和市场达到最佳契合点，该点所提供的产品刚好能够满足市场的需求，这通常是创业成功的第一步。

\[24\]Yining Ye. et al. Proagent: From Robotic Process Automation to Agentic Process Automation 2023. https://arxiv.org/abs/2311.10751.

\[25\]Zhiheng Xi. et al. The Rise and Potential of Large Language Model Based Agents: A Survey 2023. https://arxiv.org/abs/2309.07864.

\[26\]https://finance.sina.com.cn/tech/2023-11-07/doc-imzttzhu2557260.shtml

\[27\]Yue Zhang. et al. A Survey on Hallucination in Large Language Models 2023. https://arxiv.org/abs/2309.01219.


**Source**


**文章来源**


本文摘自：2023年12月18日已经发布的《人工智能十年展望（十五）：AI Agent：远期场景闭环，交互重塑》

于钟海 分析员 SAC 执证编号：S0080518070011 SFC CE Ref：BOP246

魏鹳霏 分析员 SAC 执证编号：S0080523060019 SFC CE Ref：BSX734

游航 分析员 SAC 执证编号：S0080523010001 SFC CE Ref：BTI822

王之昊 分析员 SAC 执证编号：S0080522050001 SFC CE Ref：BSS168


**Legal Disclaimer**


**法律声明**


特别提示

本公众号不是中国国际金融股份有限公司（下称"中金公司"）研究报告的发布平台。本公众号只是转发中金公司已发布研究报告的部分观点，订阅者若使用本公众号所载资料，有可能会因缺乏对完整报告的了解或缺乏相关的解读而对资料中的关键假设、评级、目标价等内容产生理解上的歧义。订阅者如使用本资料，须寻求专业投资顾问的指导及解读。

本公众号所载信息、意见不构成所述证券或金融工具买卖的出价或征价，评级、目标价、估值、盈利预测等分析判断亦不构成对具体证券或金融工具在具体价位、具体时点、具体市场表现的投资建议。该等信息、意见在任何时候均不构成对任何人的具有针对性的、指导具体投资的操作意见，订阅者应当对本公众号中的信息和意见进行评估，根据自身情况自主做出投资决策并自行承担投资风险。

中金公司对本公众号所载资料的准确性、可靠性、时效性及完整性不作任何明示或暗示的保证。对依据或者使用本公众号所载资料所造成的任何后果，中金公司及/或其关联人员均不承担任何形式的责任。

本公众号仅面向中金公司中国内地客户，任何不符合前述条件的订阅者，敬请订阅前自行评估接收订阅内容的适当性。订阅本公众号不构成任何合同或承诺的基础，中金公司不因任何单纯订阅本公众号的行为而将订阅人视为中金公司的客户。

一般声明

本公众号仅是转发中金公司已发布报告的部分观点，所载盈利预测、目标价格、评级、估值等观点的给予是基于一系列的假设和前提条件，订阅者只有在了解相关报告中的全部信息基础上，才可能对相关观点形成比较全面的认识。如欲了解完整观点，应参见中金研究网站（http://research.cicc.com）所载完整报告。

本资料较之中金公司正式发布的报告存在延时转发的情况，并有可能因报告发布日之后的情势或其他因素的变更而不再准确或失效。本资料所载意见、评估及预测仅为报告出具日的观点和判断。该等意见、评估及预测无需通知即可随时更改。证券或金融工具的价格或价值走势可能受各种因素影响，过往的表现不应作为日后表现的预示和担保。在不同时期，中金公司可能会发出与本资料所载意见、评估及预测不一致的研究报告。中金公司的销售人员、交易人员以及其他专业人士可能会依据不同假设和标准、采用不同的分析方法而口头或书面发表与本资料意见不一致的市场评论和/或交易观点。

在法律许可的情况下，中金公司可能与本资料中提及公司正在建立或争取建立业务关系或服务关系。因此，订阅者应当考虑到中金公司及/或其相关人员可能存在影响本资料观点客观性的潜在利益冲突。与本资料相关的披露信息请访http://research.cicc.com/disclosure_cn，亦可参见近期已发布的关于相关公司的具体研究报告。

本订阅号是由中金公司研究部建立并维护的官方订阅号。本订阅号中所有资料的版权均为中金公司所有，未经书面许可任何机构和个人不得以任何形式转发、转载、翻版、复制、刊登、发表、修改、仿制或引用本订阅号中的内容。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYs9ldKLEKEia3KFpdkicXEzgkmcp8yQuFRGd4jzuL9X5ibpTwS8hibPrHgjg2mAOMX0XGggqMHCDyibCWMQ%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)


[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7166705501206481192)
