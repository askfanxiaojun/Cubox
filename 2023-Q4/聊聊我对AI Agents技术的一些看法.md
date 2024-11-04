聊聊我对AI Agents技术的一些看法
====================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/YI7FX62yRV4-1qA8O3sH4g)小戏 夕小瑶科技说


![图片](https://image.cubox.pro/cardImg/2023120500132148914/24843.jpg?imageMogr2/quality/90/ignore-error/1) 夕小瑶科技说 原创  
作者 \| 小戏、兔子酱  

小伙伴们！我来兑现承诺啦～
![图片](https://image.cubox.pro/cardImg/2023120500132122752/99332.jpg?imageMogr2/quality/90/ignore-error/1) ps：接下来期待什么内容，欢迎在评论区留言！
![图片](https://image.cubox.pro/cardImg/2023120500132148090/77031.jpg?imageMogr2/quality/90/ignore-error/1)

今天，我们就来聊聊大模型 Agent。

最近这几个月，Agent 这一概念可谓火出天际，从 AutoGPT 一周 6 万 star 刷新 Github 涨星速度记录开始，AI Agent 项目如雨后春笋开始在各大技术平台涌现。
![图片](https://image.cubox.pro/cardImg/2023120500132294820/68531.jpg?imageMogr2/quality/90/ignore-error/1) ▲AutoGPT Github Star 数

**AI Agent 不断被冠以"大模型下半场"，"软件 2.0（ Software 2.0）"等等称号**，连 OpenAI 的创始成员 Andrej Karpathy 也在十月份的黑客马拉松演讲中也表示：
> 相比模型训练方法，OpenAI 内部目前更关注 Agent 领域的变化，每当有新的 AI Agents 论文出来的时候，内部都会很兴奋并且认真地讨论。

那么，所谓 AI Agent 到底是什么？它的源其何处？魔力又是什么呢？
![图片](https://image.cubox.pro/cardImg/2023120500132226176/39535.jpg?imageMogr2/quality/90/ignore-error/1)

AI Agent 源自何处
-------------

首先，Agent，Agent，这个在英文中过于常用的概念出现在 AI Agent 的语境里，到底代表着什么概念？让我们先来对 "Agent" 这个词做一个词源追溯。

Agent 的词根 ag- 来自于拉丁语动词 agere 意指做和行动，与词根 act- 一脉同源，加之形容词后缀 -ent 表示"正在做事的人"，其直译应为"做事者"，换言之，**Agent 的本意代指"做事的主体"，"可以做事之物"，强调"做"这一动作**。

相较于具有"主体性"的人，**Agent 更多具有一种"拟主体性"，即带有模仿人类主观能动性的去主动的有目的地进行"计划"，"组织"，"实施"，"学习"等直至完成一项工作或一件事情。** 回到 AI 研究的语境之中，相反于传统机械或软件被动的"给予输入------\>做出输出"的模式，**Agent 由于更加强调自主的发现问题、确定目标、构想方案、选择方案、执行方案、检查更新的特性，因此可以被认为是一类拥有"自主智能的实体"，而被广泛称之为智能体**。

在早期人工智能的研究中，对人工的智能进行抽象形成的概念大致上是一类"**利用传感器对周围环境做出感知，依据感知到的信息做出决策，并利用行动装置做出行动**"的人工实体，因此也被称为 AI Agent，AI Agent 拥有众多不同的类型，包含反射型、模型式，目标型等等，其中最出名也是最火出圈的可能就是强化学习的范式，依据 reward 指导，根据状态价值函数或动作价值函数的更新而构建的学习型智能体。
![图片](https://image.cubox.pro/cardImg/2023120500132299861/87121.jpg?imageMogr2/quality/90/ignore-error/1) ▲强化学习范式

区别于更加擅长于做"感知"的传统深度学习的方法，**Agent 的重心其实更加落子于"行动"也就是"决策"之上**，尽管强化学习领域以 PPO 为代表的策略梯度方法在游戏的许多领域取得了亮眼的成绩，但是基于各种特定神经网络架构的策略网络没有足够的"泛化"能力，无法实现通用的智能决策，同时，强化学习范式似乎有时候也要求着太多对"智能体"而言完全不合理的"试错"，Agent 本身似乎完全是一张白纸而没有任何"先天知识"。
![图片](https://image.cubox.pro/cardImg/2023120500132287354/78080.jpg?imageMogr2/quality/90/ignore-error/1) ▲乔姆斯基的转换生成语法说强调具有先天的普通语法

GPT-4为AI Agent带来转机
------------------

"通用性"与"先天知识"的结合似乎在今年 3 月 OpenAI 发布 GPT-4 后迎来转机，大规模语言模型（LLMs）的强大能力使得其可以轻松处理多个来自完全截然不同的领域的任务，同时其前身"预训练"的范式又似乎带有一定的"先天知识"而不必后天盲目的试错。

**因此使用 LLMs 作为 AI Agent 中的 Agent 成为一条极其有希望成功实现"自主智能体"的技术路径，从而延申出这半年来形形色色的基于 LLMs 的 AI Agent**。
![图片](https://image.cubox.pro/cardImg/2023120500132219431/20380.jpg?imageMogr2/quality/90/ignore-error/1) ▲大模型智能体飞速发展

事实上，当大家开始思考"大模型除了 Chat 以外还有什么应用"时，便已经有了基于大模型的 Agent 的想法。四月份我们报道过 CMU 发布的一篇使用大模型作为"自主科研智能体"的论文《[又一恐怖技能！卡耐基梅隆大学发布超强智能体，炸翻科研圈](https://mp.weixin.qq.com/s?__biz=MzIwNzc2NTk0NQ==&mid=2247548153&idx=2&sn=aa0611d604939e89d2d45cef930659b8&scene=21#wechat_redirect)》，**在其中大模型充当一个"核心协调器"的作用，向上对接人类的以 Prompt 为形式的输入，向下则以网络搜索，Python 脚本等为媒介沟通互联网或自动化实验仪器等工具，从而可以自主完成从实验设计、实验规划到执行复杂的科学实验等的一整套流程**。
![图片](https://image.cubox.pro/cardImg/2023120500132218452/48222.jpg?imageMogr2/quality/90/ignore-error/1) ▲基于大模型的科研智能体架构

基于类似这样自主科研智能体的形形色色的大模型垂直领域的 AI Agent 论文或工作，也是在四月份，清华大学瞄准"大模型使用工具"，发布了一篇"工具学习综述"：《[清华发布工具学习框架，让ChatGPT操控地图、股票查询，贾维斯已来？](https://mp.weixin.qq.com/s?__biz=MzIwNzc2NTk0NQ==&mid=2247548584&idx=2&sn=143119aed845b9a20a37b256cb69934d&scene=21#wechat_redirect)》，在这篇综述中，清华大学提出了一个叫"Tool Learning"的概念，将之前的各种垂直领域的智能体放置于一个统一的框架之下，**其中大模型仍然作为"控制器"，用于完成针对人类的"意图识别"，针对可选工具的"组织规划"，并且引入了"感知器"向大模型报告"执行结果"，当出现错误时指导大模型完成"自主纠错"**。
![图片](https://image.cubox.pro/cardImg/2023120500132384699/32138.jpg?imageMogr2/quality/90/ignore-error/1) ▲工具学习框架

而如果把眼界再打开，不局限于"工具使用"，而是将 AI Agent 建模为一个人脑智能与人工智能协同的过程，**面对一个"任务"，由人类站在高点描述一个"任务目标"，并将完成这一任务的工作交予 Agent，而 AI 接受目标并自主的进行"感知环境"，"形成记忆"，"完成规划"，"决策行动"，"观察纠错"等一系列以任务目标为导向的行动**，那么就形成了诸如 "AutoGPT"，"BabyGPT" 等基于 LLMs 的 AI Agent 模式。
![图片](https://image.cubox.pro/cardImg/2023120500132319700/25174.jpg?imageMogr2/quality/90/ignore-error/1) ▲基于 LLMs 的自主 AI Agent 模式

**与其说基于大模型的 AI Agent 是一种"新技术"，不如说基于大模型的 AI Agent 是一套面向 LLMs 的"新的管理方法"**，类似"思维链"等技术，大模型 Agent 通过一整套流程化，机制化的方式促使大模型模拟人类智能的决策过程，以代替人类完成一些具体的任务。
![图片](https://image.cubox.pro/cardImg/2023120500132353241/89913.jpg?imageMogr2/quality/90/ignore-error/1) ▲AutoGPT 核心代码

以 BabyAGI 的流程图为例，如下图所示，作为 User 的人类首先向 Agent 以"自然语言"的形式提供任务与目标的描述，放置于任务队列之中（1.），任务优先级 Agent 用于对任务队列任务列表、执行顺序等进行管理（5.）（6.），执行 Agent 不断从任务队列在提取任务（2.），向上联系具体的任务目标，向下联系具体可操作的如"实验设备"，"功能API"，"常用工具"等工具库，用于完成对任务的操作。

在执行过程中，执行 Agent 维护一个记忆库 Memory，储存当下此轮的任务信息，查询历史完成的任务信息。在操作完成后，执行 Agent 向任务创建 Agent 发送任务完成结果（3.），根据任务完成结果，任务创建 Agent 向任务队列增添为完成前项任务所必须先完成的"前置任务"，直到此项任务结束。
![图片](https://image.cubox.pro/cardImg/2023120500132327887/95349.jpg?imageMogr2/quality/90/ignore-error/1) ▲BabyAGI 流程图

如果对上述框架做一个抽象与总结，参考人大发布的 AI Agent 综述，一个 AI Agent 可以被认为由以下四部分组成：

*
  Profile：表示 Agent 属性
*
  Memory：存储历史信息
*
  Planning：生成计划决策
*
  Action：执行计划决策

各种不同的 AI Agent 的差异与区别也几乎都从上述四部分展开，譬如在 Profiling 模块，不同的 AI Agent 可以选择不同的角色定义方式，如手动定义"假设你是一个学生"，或者采用大模型对 Agent 角色进行生成。在 Memory 模块，是否区分长期记忆与短期记忆，记忆存储方式（自然语言？数据库？嵌入？）等也构成了不同的 AI Agent 的特征。在 Planning 模块，有无反馈？采用思维链 CoT？思维树 ToT？思维图 GoT？在 Action 模块，单轮互动还是多轮互动，如何定义 Agent 的动作空间，是否使用外部工具，如果定义外部工具集等等也都是 AI Agent 前沿的研究方向。
![图片](https://image.cubox.pro/cardImg/2023120500132484512/39262.jpg?imageMogr2/quality/90/ignore-error/1) ▲大模型 Agent 框架

**基于 Prompt 的与大模型互动的方式更像是静态的"输入-输出"，而 AI Agent 为大模型提供了一个进行"动态决策"的框架，使得大模型开始有能力处理任务更加复杂化，情境更加多样化的决策，为大模型从"语言"迈向"真实世界"提供了一个坚实的基础**。
![图片](https://image.cubox.pro/cardImg/2023120500132448934/65357.jpg?imageMogr2/quality/90/ignore-error/1) ▲LangChain 组件

相应的，类似 LangChain 的大模型开发框架应运而生随之爆火，LangChain 作为一个面向大模型的"管理框架"，连接了大模型、Prompt 模板、链等多种组件，基于 LangChain，香港大学余涛组发布了开源的自主智能体 XLANG Agent（[香港大学余涛组推出开源XLANG Agent！支持三种Agent模式](https://mp.weixin.qq.com/s?__biz=MzIwNzc2NTk0NQ==&mid=2247559025&idx=1&sn=de3575753ee5f6c525b6f96cdb078e94&scene=21#wechat_redirect)），在介绍的博客里，余老师如是描述大模型 Agent：
> 想象一下这个过程，将以日常语言为载体的人类的指示或问题转化为机器可以理解的动作和代码，随后机器在特定的环境中执行这些动作，从而改变该环境的状态。这些变化被观察、分析，并进而启动与人类下一步交互的循环
![图片](https://image.cubox.pro/cardImg/2023120500132411764/10851.jpg?imageMogr2/quality/90/ignore-error/1) ▲XLANG Agent 进行多轮互动

在 XLANG Agent 的基础上，余涛老师组进一步优化非专家用户的使用体验和应用设计，并将 Agent 平台化，便形成了十月份我们报道的 OpenAgents 《[开源智能体来啦！港大团队发布OpenAgents，可以搞数据分析、聊天、支持200+插件](https://mp.weixin.qq.com/s?__biz=MzIwNzc2NTk0NQ==&mid=2247563365&idx=2&sn=94c857507e5db56f7dab05e861cb55f6&scene=21#wechat_redirect)》，**OpenAgents 的出现也开始让 Agent 的发展朝向全面、透明与可部署化**。
![图片](https://image.cubox.pro/cardImg/2023120500132467329/71259.jpg?imageMogr2/quality/90/ignore-error/1) ▲OpenAgents 平台图

类似的，清华与面壁智能发布的 XAgent，**通过强化"子问题分解"与"人机协作"，在 AutoGPT 的基础上向着真实应用前进了一大步**，并在众多实际任务测试中全面超越 AutoGPT，拓展了 Agent 能力的边界。
![图片](https://image.cubox.pro/cardImg/2023120500132532562/42495.jpg?imageMogr2/quality/90/ignore-error/1) ▲XAgent 超越 AutoGPT

事实上，如果类比于传统软件工程管理与面向 AI 的软件工程管理（MLops），Agent 的出现进一步模糊了软件作为一个输入输出系统"软件内"与"软件外"的边界。由于 Agent 可以不断与与外部环境发生互动，不断的学习修正自己的任务规划，**因此当 AI Agent 出现以后，尽管牺牲了一些可靠性，但是这类应用的"灵活性"又迈上了一个新的台阶**。
![图片](https://image.cubox.pro/cardImg/2023120500132589033/49527.jpg?imageMogr2/quality/90/ignore-error/1) ▲智能水平与管理层级

这种跃升将直接导致管理层级（自上而下决策层------\>控制层------\>执行层------\>操作层）中越来越多的任务可以被 AI "自动化"了，如果说传统的自动化机械停留在让决策者在基层操作层执行时"自动化"，而以深度学习为代表的人工智能方法则可以再上一层完成任务执行方案生成时的方案选择"自动化"，**那么以大模型 Agent 为代表的新一代人工智能方法则真正实现了控制层一整套决策流程的"自动化"**。而这种层面的"自动化"恰恰带来了 Software 2.0 的曙光，软件开发将变成完全的"自动化工厂"，软件层面的"大规模定制"有可能到来。
![图片](https://image.cubox.pro/cardImg/2023120500132546970/43050.jpg?imageMogr2/quality/90/ignore-error/1) ▲AI 应用的五层基石

Seednapse AI 的创始人曾给了 AI 应用的五层基石，如果说之前的类似 AutoGPT 的智能体属于自主智能体（Autonomous Agent），其核心思想是"像人类智能一样去解决问题"，那么以斯坦福小镇为代表的生成智能体（Generative Agent）可能带来 Multi-Agent 的曙光，**区别于"像人类智能一样去解决问题"，生成智能体的核心在于"像社会智能一样去解决问题"**。在斯坦福 25 人小镇的论文中构建了生成智能体的架构如下图所示：
![图片](https://image.cubox.pro/cardImg/2023120500132522056/34207.jpg?imageMogr2/quality/90/ignore-error/1) ▲生成智能体架构

通过使用一种"记忆---计划---反思"驱动的智能体形态，以"社会事件"为动力源使得 Agent 间相互互动，直至模拟整个社会的分工体系。在这种生成智能体的思想下，一群导演与计算机工程师踏出了生成智能体应用的第一步《[AI自导自演的电视剧，每个角色都是一个大模型，斯坦福25人小镇精神续作](https://mp.weixin.qq.com/s?__biz=MzIwNzc2NTk0NQ==&mid=2247557280&idx=2&sn=c9b5972c432080775a5e27301dfa24ba&scene=21#wechat_redirect)》，尝试制作了一部完全由大模型自导自演、定制化的电视剧集 Westland Chronicles
![图片](https://image.cubox.pro/cardImg/2023120500132518911/95964.jpg?imageMogr2/quality/90/ignore-error/1) ▲Westland Chronicles 剧照

而从实验性质的模拟向下，类似 MetaGPT 等的多智能体 AI 框架逐渐诞生，通过模拟不同角色之间的"合作"，最终实现"**生成一个包含分析和设计的示例大约需要0.2美元（GPT-4 API的费用），而一个完整的项目大约需要2.0美元。**"
![图片](https://image.cubox.pro/cardImg/2023120500132653127/18802.jpg?imageMogr2/quality/90/ignore-error/1) ▲MetaGPT 框架

回到最开始，AI Agent 作为 "OpenAI 发力的下一个方向"，背后蕴含了一个天文数字量级的市场。**前两天爆出 OpenAI 已经在进行灰度测试，未来很快将放出一个可以使用所有工具的 GPT-4（All Tools）版本，真正成为一个"理解一切，处理一切，生成一切"的超级统一智能体** （[重磅！GPT-4又进化了！画图、插件、代码等能力被整合，超级智能体来了](https://mp.weixin.qq.com/s?__biz=MzIwNzc2NTk0NQ==&mid=2247564583&idx=1&sn=45dbe042a18dc176fae779d9ab4f9c28&scene=21#wechat_redirect)）
![图片](https://image.cubox.pro/cardImg/2023120500132647332/25375.jpg?imageMogr2/quality/90/ignore-error/1) ▲OpenAI 更新预告

当这样一种 AI Agent 出现，它对生活的改变很有可能不止于 ChatGPT 简单的 Chat，而是渗透入各行各业，在只要能用到大模型的地方就可以建立起相应的 Agent，各种科幻电影中的人机协作有可能真的会走进现实。
![图片](https://image.cubox.pro/cardImg/2023120500132623225/71461.jpg?imageMogr2/quality/90/ignore-error/1) ▲钢铁侠与贾维斯

当然，目前这样一种 AI Agent 的技术落地尚处于"婴儿时期"，如同 BabyGPT 的名字那样，**目前的 AI Agent 的技术还远远无法匹配我们宏大的想象** 。试错与学习能力不足、复杂推理能力不强、精确决策能力不够、响应时间过长、计算资源要求过高等等由限制着大模型 AI Agent 成为真正的"贾维斯"，但是，未来已来，引用迪迦奥特曼的主题曲《奇迹再现》的歌词："**新的风暴已经出现，怎么能够停滞不前......**"
> ps：别忘了，想看什么原创内容，欢迎在评论区留言哦！等小瑶翻牌子～

![图片](https://image.cubox.pro/cardImg/2023120500132661789/30334.jpg?imageMogr2/quality/90/ignore-error/1)![图片](https://image.cubox.pro/cardImg/2023120500132662259/39997.jpg?imageMogr2/quality/90/ignore-error/1)![图片](https://image.cubox.pro/cardImg/2023120500132763026/69078.jpg?imageMogr2/quality/90/ignore-error/1)

![](https://image.cubox.pro/cardImg/2023120500132785129/15199.jpg?imageMogr2/quality/90/ignore-error/1)

**夕小瑶科技说**

更快的AI前沿，更深的行业洞见。聚集25万AI应用开发者、算法工程师和研究人员。一线作者均来自清北、国外顶级AI实验室和互联网大厂，兼备媒体sense与技术深度。

675篇原创内容

公众号

，

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7131385580029478760)
