中金 \| 漫谈AI应用：AI+代码，生产力领域的应用先锋
=============================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/BumD83VVWKIdh22dqxo_4w)于钟海 王之昊等 中金点睛

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FfzHRVN3sYsicmoVBv4D0mPib68kWJVkDjnEM91ZO46IRCPDfIfFpMEn2BoxwUa2fguPicQ4WwvNibdnOL4IqZj4XTA%2F640%3Fwx_fmt%3Dgif)

**本文作者：于钟海 , 王之昊 , 魏鹳霏 , 谭哲贤 , 王倩蕾**


**中金研究**


**近期，AI+代码应用Cursor以强大的功能引发市场关注；**9月12日，OpenAI发布OpenAI-o1模型，模型在数理和编程能力上提升明显\[1\]。我们观察到近两年AI+代码应用能力进步明显，涌现出以Cursor为代表的众多应用。本篇报告我们介绍AI+代码的应用现状和发展前景，并以Cursor的商业化成功为鉴，梳理我们对AI应用商业化落地的最新思考。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_gif%2FfzHRVN3sYs8xtLU6ibdbskELfuUXx80zzQIwJ82CKn4snGb6iclJZDK6xNJsX2V9QFc95nyGbzImLxhlvbU03A6Q%2F640%3Fwx_fmt%3Dgif%26from%3Dappmsg)


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYs8xtLU6ibdbskELfuUXx80zziaKib0RCJ57fvKBvHL16GKIaLT7Z4K7DGEa04JHxwDkmmBNN0NLsUpsg%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)

**[点击小程序查看报告原文]()**


**Abstract**


**摘要**


**AI+代码是产品实用、商业化领先的AI应用场景。**在主要的生成任务中，我们观察到无论从实用性、可用性，还是从用户的体验反馈、渗透率来看，AI+代码都是应用广度和深度较为领先的场景。CSDN在2023年的调研报告指出，样本中近90%开发者已开始使用代码生成工具，绝大多数认为其对开发效率有所提升\[2\]。以GitHub Copilot为例，其在2024年4月已经拥有超过180万付费用户数，2024财年收入规模已达到数亿美元。我们认为代码生成任务本质上是一类较为"标准化"的"语言"生成工作，相较纯文字生成而言复杂度更低，因此比较适合大模型来发挥。

**Cursor本质上是大模型赋能的IDE，大幅提升开发者效率。**从产品形态上看，目前多数AI+代码产品（如GitHub Copilot、Codeium、iFlyCode、aiXcoder等）以插件的形式在VSCode等集成开发平台（IDE）中使用，而Cursor本身即是集成了大模型能力的IDE，能够以本地部署的形式灵活调用GPT、Claude等大模型。从功能上看，我们将AI+代码的核心功能归纳为"生成"和"解释"两大项，除了基础的代码补全之外，Cursor还支持行内级、文件级、项目级的代码生成、编辑、解释。虽然在产品形态上并无明显变化，但是其凭借对开发流程的深刻理解实现了商业落地。

**Cursor的成功对AI应用有怎样的启发？1）深入理解应用场景，准确把握客户需求，**我们认为AI应用能力提升一方面依赖于模型的能力上限的提升，另一方面也依赖于对应用场景的深刻理解和对客户需求的准确把握。可以说模型能力能够提升AI应用的上限，但是对于场景的理解则决定了AI应用的上限能否兑现；**2）深度融合原生应用，实现AI的"无感应用"，**Cursor将AI能力自然引入应用当中，最大限度地保留了原生的产品形态。类似的在AI+文字领域，金山办公的WPS AI的伴写也在WPS原有产品形态下实现了体验的大幅提升。


**风险**


技术进展不及预期；行业竞争加剧；商业化落地不及预期。


**Text**


**正文**


**AI+代码产品领先实现落地，Cursor引发市场关注**


**AI+代码：产品实用、商业化领先的AI应用场景**


**AI+代码是实用性较强、用户反馈较优的AI应用品类。**在文字、代码、图片、视频等主要的生成式AI创作场景中，我们观察到AI+代码无论是从产品的实用性、可用性，还是从用户的体验反馈、渗透率来看，都是应用广度和深度较为领先的场景。CSDN 2023 AI开发者生态报告（2023年12月）\[3\]中的调研指出，调研样本中近90%的开发者已经在使用代码生成工具（其中35%每天使用），且绝大部分开发者认为代码开发工具对开发效率有所提升。


图表1：代码生成工具使用满意度，CSDN 2023年调研


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41DMLGhHficIIL1QibQv8IAiaaldyZ2WzZTw78BoYWoqIIL17pkqyfw4YOSA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：《2023 AI开发者生态报告》（CSDN，2023.12），中金公司研究部


**以GitHub Copilot为例，无论从渗透率还是商业化来看均走在前列。**从具体的案例来看，微软的财报中连续几个季度都有对于Github Copilot较为正面积极的数据反馈，GitHub Copilot的付费订阅用户数在2023年10月、2024年1月、2024年4月分别超过100/130/180万，付费用户数加速增长。2024财年GitHub收入达到20亿美元，其中Copilot贡献超过40%的收入增长，公司表示GitHub Copilot收入规模已经超过2018年收购GitHub时整体业务收入（ARR约2\~3亿美元），我们认为Github Copilot的商业化进度走在Office Copilot之前。

**为什么AI+代码的应用场景商业化更加成功？**我们认为代码生成任务本质上是一类较为"标准化"的"语言"生成工作，虽然代码生成过程中有一些数理逻辑，但本质上还是比较固定的，相较纯文字生成而言复杂度更低，因此比较适合大模型来发挥。PapersWithCode的测评指出\[4\]在HumanEval（基础代码能力测试基准）评估基准下，多数大模型在基础代码任务上一次通过率达到75%以上，我们认为编程任务本身即是大模型比较擅长的领域，因此落地到应用层面或将也会有较好的效果。


图表2：主流大模型在基础代码生成任务上准确率普遍较高


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41DhXpgwEPLIPqa7ibhNiaRAkD4YJk79uAC2NrQofjDWeHG2exQW4F1BJ8g%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：PASS@1意为一次提交即通过测试  
资料来源：PapersWithCode，中金公司研究部


**目前有哪些较为流行的AI+代码应用？**由于以GPT为代表的LLM大模型在代码生成领域的出色能力，近两年代码编程一直是关注度较高的AI应用领域，除了ChatGPT、Claude、文心一言等对话类大模型本身可以通过Prompt交互进行代码生成之外，市场上还涌现出了Github Copilot、Codeium、Cursor等一批海外专业的AI+代码应用；国内北京大学软件工程研究所推出了aiXcoder代码生成应用，科大讯飞（iFlycode）、智谱（CodeGeeX）等大模型公司也有相应的代码生成应用。


图表3：国内外主要的AI+代码应用


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41DUKQ2wibt3tugtDORIx9UvHicN10Dlvw6DZslAhB9cAYle4lcM8kpZVOA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：各公司官网，中金公司研究部


**目前的AI+代码应用主要有哪些形态和功能？从产品形态上看，**除了ChatGPT等对话式AI生成应用可以通过交互生成代码之外，专业的AI+代码应用则主要呈现为IDE插件或者本地部署的形态。**从产品功能上看，**我们将AI+代码应用归纳为"生成"和"解释"两大核心功能，其中生成功能指通过"交互"或者自动"预测"形式来借助AI生成、补全、编辑代码和注释（Debug功能也可以归为此类）；解释功能则是对于开发者编写的代码内容的AI辅助解释和搜索（包括互动提问、文档查询等），此外部分AI+代码应用还可以对互联网内容和代码库进行搜索，从而更好地辅助开发者。


图表4：代码生成工具使用环境，CSDN 2023年调研


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41DFKQqercBUfh7xZOFCFywGApqjg0oe2MRccoqn4AnXibBUcsQjZjwYCA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：《2023 AI开发者生态报告》（CSDN，2023.12），中金公司研究部


图表5：代码生成工具功能使用分布，CSDN 2023年调研


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41D7gVzH2SWYXcrJINibPhR7sgCshQfGtxneFV374FNEuVn6tDQzD972FA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：《2023 AI开发者生态报告》（CSDN，2023.12），中金公司研究部


**Cursor：AI+代码的集成开发环境，开发者效率提升利器**


**Cursor是一款什么样的AI+代码应用？**从产品定义和形态上看，Cursor是一款由AI大模型驱动的编程集成开发环境（IDE），其最初是在2022年由四位来自于MIT的创业者开发，并在2023年开始通过与GPT、Claude等大模型集成，具备了强大的代码生成\&重写能力，能够帮助广大开发者迅速提升工作效率。截至2024年8月，Cursor已经在全球范围内积累了超过3万名企业客户，包括大型企业、知名研究机构以及各种初创公司\[5\]；2024年8月，Cursor背后的创业公司Anysphere完成了超过6000万美元的A轮融资，估值超过4亿美元\[6\]。

**商业化：Freemium模式，付费会员可解锁更高级别权益。**在定价方面，Cursor提供免费版本会员，拥有2,000次代码补全（completion）的额度。用户可以通过20美元每月的价格（年付费对应16美元/月）购买Pro版会员，付费会员可以拥有无限代码补全次数、无限量使用更高级别的模型（GPT-4、GPT-4o、Claude 3.5 Sonnet等）以及自研cursor-small模型等权益。更高级别的Business版会员月订阅价格为40美元（年付费对应32美元/月），权益包括集中计费、管理仪表板、强制隐私模式、零数据保留等，我们认为这些权益为企业用户提供了更高级别的管理、安全及隐私保护服务。


图表6：Cursor会员定价（2024年9月）


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41D1KHRic4quozdMiaqibcOez7hBkich6Kkcxkib8bGhwRB8yLJKCfGkxiayCuA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：年度付费的Pro和Business会员价格分别相当于每月付费16和32美元  
资料来源：公司官网，中金公司研究部


**Cursor和先前的AI+代码应用相比有何优势？**第一是在应用形态上，包括Github Copilot、Codeium等大多数AI代码应用都是以IDE插件的形式，通常是与VSCode等IDE结合进行使用；而Cursor其本身就是一个IDE，通过本地部署的方式使用，并且支持接入GPT、Claude等多种大模型，这使得其在使用中对于模型的应用选择能够更加的灵活，我们认为本质上Cursor = GPT+VSCode；第二是在产品功能上，对于AI代码应用核心的功能"生成"和"解释"，Cursor都有明显的优化提升。接下来我们将介绍Cursor的主要功能，以及Cursor和GitHub Copilot的部分功能的对比。

**► 代码补全（Tab）：**与GitHub Copilot类似，Cursor进行常见函数和方法自动补全，通过分析学习大量代码库，**可在用户输入时自动补全，**并展示相关参数列表或返回值类型等。这也是AI+代码应用的基础能力。与其他类似的产品相比，Cursor的Tab功能亮点在于**多行编辑、预测下一个改动的光标位置等。**

**► 对话（Chat）：**除了局部修改，Cursor也支持整个文件**可以通过对话的方式修改，还能全局检索和进行更多交互，**作用于单页面修改。Chat支持引入图片上下文、支持联网、支持基于代码库的问答。在Chat界面中，**用户可以利用@操作符来灵活地指定上下文（context）检索范围，**这是Cursor相较其他同类产品的特色之处。在Cursor完成响应后，开发者可以在编辑器中看到改动，通过点击"Accept"或"Reject"进行采纳或拒绝，并提出后续修改要求（类似"Pull request"），我们认为这项功能大幅提升用户体验。

**► 交互式编辑（Ctrl K）：**Cursor的生成补全过程中，**支持更为明确和直接的指令输入方式，允许用户通过快捷键Ctrl + K即时激活行内交互界面，作用于行内修改。**可以实现解释代码逻辑、自动化生成文档内容、快速构建测试案例，以及针对特定问题执行修复操作等。它允许开发者在编辑代码时，不仅能在当前光标位置进行补全或修改，还能自动识别并应用这些修改到代码库中的其他相关位置。类似Chat，**用户可以利用@操作符来灵活地指定上下文（context）检索范围。**

**► 项目修改（Composer）：**Cursor的重磅功能，**实现全局的修改，能够编辑和生成新文件。**如Cursor可以实现指令"帮我重构整个项目"、"提取页面中的组件，拆分到单独的文件夹中"、"给整个项目写上详细注释"等。目前Cursor可以适配包括typescripts、HTML、CSS、Python、Java、Csharp（C#）、C、Rust、PHP、GO在内的多种语言。


图表7：Cursor功能实例之Tab


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41D8iaIicF6rz2icfuZAew200NXCGOkoSiafurY168CnKhRMNiaIrYqxiaIoicMg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


图表8：Cursor功能示例之Chat


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41DSdSzrUA7NfTSbGciaibTyZjLf3brELicOqIO6FBnYQ6ju91K7xsH7pibqA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


图表9：Cursor功能示例之Ctrl K


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41DJX1LaTZkKEibPv5SYYM9JiaZhHK9OGfvuH5vNpTVJHWqlTrfS3GnexTw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


图表10：Cursor功能示例之Composer


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41DvYPJfbmYXyPib62BbKRKMjiaQ3dtTruY0ibpunFEhuQn7CXLJxgg85FAA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：以上案例来自我们实际测评  
资料来源：中金公司研究部


**其他AI+代码应用**


**GitHub Copilot**

**2022年6月，GitHub Copilot正式上线，个人版定价为10美元/月或100美元/年，对学生用户和开源项目维护者则免费提供，发布之初由GPT-3模型支撑。**2023年11月30日，GitHub宣布Copilot Chat更新为由GPT-4支持\[7\]，提供更为精确和实用的代码建议。至2024年4月，GitHub Copilot付费用户数达到180万，公司表示2024财年GitHub Copilot收入规模已经超过2018年收购GitHub时整体业务收入（ARR约2\~3亿美元）。


图表11：GitHub Copilot使用示例


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41DKTaW7eJpmQITceQqICjP4fJF3ibYlJ6QxCGha8U5PRZIK8IRBichKwiaA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：以上例子来自我们的测试案例  
资料来源：中金公司研究部


**Codeium**

Codeium是初创公司Codeium于2023年1月发布的一款AI智能编程助手，具有自动代码补全、搜索以及互动式聊天助手等功能，支持大部分主流编程语言和IDE。**Codeium对个人用户免费开放，Teams版本定价为15美元/人/月或144美元/人/年。**截至2024年8月，Codeium拥有超过70万活跃用户。2024年8月，Codeium完成1.5亿美元C轮融资，估值达到12.5亿美元\[8\]。

**Amazon Codewhisperer**

Amazon Whisperer是由Amazon公司基于数十亿行公开代码和Amazon内部代码进行训练的生成式AI代码助手。**Amazon于2022年6月推出CodeWhisperer预览版，并于2023年4月正式发布，**可在集成开发环境中提供代码生成、代码补全、代码审查等功能，并专注于为AWS API提供支持。商业化方面，Amazon Whisperer免费供个人用户使用。

**Replit Agent**

AI初创公司Replit 提供了一个基于云的协作式集成开发环境，**并于2024年9月推出其智能开发助手Replit Agent，支持在手机或电脑上通过自然语言提示，**完成编写代码、安装软件包、配置数据库和部署应用等开发任务，帮助用户快速构建软件项目。商业化方面，Replit的Core和Teams订阅分别定价为25美元/月（120美元/年）和40美元/月。目前Replit Agent处于早期体验阶段，Replit订阅者可以通过Web界面或移动应用访问Replit Agent。

**CodeGeeX**

CodeGeex基于智谱AI于2022年9月发布的130亿参数的多编程语言代码生成预训练模型。**2024年7月，CodeGeeX4大模型发布，参数量为90亿，**可以支持代码补全与生成、代码解释、联网搜索、函数调用、参数级代码问答等多项功能，其在VSCode插件市场可以免费下载使用。截至2024年7月，CodeGeeX智能编程助手的个人用户数量超过100万，企业版本也广泛用于科技、金融、医疗、制造等多个行业\[9\]。

**iFlyCode**

**iFlyCode智能编程助手基于科大讯飞星火大模型，最早在2023年8月15日与讯飞星火2.0大模型同时发布。**iFlyCode可以通过自然语言描述需求，快速生成代码片段，同时具备智能问答、代码补全、代码解释、文档注释、单元测试、代码调试等功能，支持上百种编程语言和主流IDE。商业化方面，iFlyCode个人版和团队的SaaS版定价分别为69元/月和129元/人/月，同时面向金融、工业、教育行业提供私有化部署的定制版本。

**aiXcoder**

**aiXcoder来自孵化于北京大学软件工程研究所的硅芯科技。**其最早可追溯至2018年的1.0版本（在线代码智能补全与搜索），2019年和2020年分别发布2.0版本（提供本地+云端代码补全能力）、3.0版本进一步完善支持语言种类；2022、2023年陆续发布aiXcoder XL和aiXcpder Europa（130/160亿参数量），功能持续进阶；2024年4月9日，aiXcoder推出全新自研7B代码大模型并开源，在多个主流评估标准评测集中，实现优异的代码生成、代码补全、跨文件上下文代码生成效果。商业化方面，aiXcoder免费版支持每月200次代码生成功能，专业版每月可以使用1,000次代码生成功能，定价为每月99或每年999元\[10\]。


**以Cursor等代码应用为鉴，AI应用如何加速落地？**


**Cursor的成功对于AI应用有何启发？**我们认为，Cursor等AI+代码应用以较快的进度实现落地，实现商业回报的关键在于：**1）深入理解应用场景，准确把握客户需求；2）深度融合原生应用，实现AI的"无感应用"。**

**关键之一：AI应用需要深刻理解场景和用户的需求。**我们认为，成功的AI应用还是要自下而上的从场景和需求出发而非自上而下，Cursor的核心优势就是能够深度理解开发者的工作习惯和工作流程，因此Cursor在交互体验上是有很多的优势，在这个方面相较微软等大厂的产品具备优势。**因此我们认为模型能力限制并不是AI应用落地慢于预期的全部原因，**其真正的效果需要模型能力和场景理解的相向而行，一方面模型的能力上限需要模型的持续迭代来提升（如9月13号最新发布的OpenAI-o1在数学问题和代码生成任务表现有明显提升），另一方面场景和现有AI能力的融合度、契合度也需要提升，可以说模型能力能够提升AI应用的上限，但是对于场景的理解则决定了AI应用的上限能否兑现。


图表12：模型能力决定AI应用能力的上限，对场景的理解则决定上限能否兑现


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41Dr5xOYk0pO9W6NJDu7mV0OluklGZxJAW3D5fhR0cWd6hPVCM0uzSvMg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：中金公司研究部


图表13：OpenAI-o1在数学问题、代码生成任务上表现优异


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41DA9xk1KhYS129icMDXUNhJcDYawQGZtbIWwcTJV2n0wqc7CDTsica3vnQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：OpenAI-o1技术报告，中金公司研究部


**关键之二：融入AI之后产品功能的优化和体验的提升或比产品形态更为重要。**我们认为现阶段做出成功的AI应用可能并不需要在形态上进行较大创新，单体验和功能的创新就已经可以做到很好的正向反馈。比如产品形态来看，Cursor本质就是一个融合大模型能力之后的IDE，将AI能力自然引入应用当中，最大限度地保留了原生的产品形态。与ChatGPT需要生成之后复制粘贴到IDE中不同，无论是代码的自动补齐、自动纠错，还是通过对话的方式实现代码的生成、修改、采纳，其都是将大模型的生成能力与工作流程天然融合，大幅提升了用户体验，实现AI的"无感应用"。

**AI+文字生成领域的案例：WPS AI伴写功能实现AI能力的无感调用。**2024年7月5日，金山办公在世界人工智能大会上宣布升级至WPS AI 2.0战略\[11\]，其中全新发布的写作助手支持"AI伴写"功能。与AI+代码类似，WPS AI能对用户接下来编写的内容进行建议，用户可以按Tab键进行采纳。我们认为WPS AI的伴写功能深度理解了用户在撰写文案中的实际需求，提供无感的AI应用体验。需要注意的是，WPS AI的伴写本身在产品形态上也没有明显改变，在原有的产品形态下实现了用户体验的提升，且相较对话式编辑使用体验更优。


图表14：WPS AI 2.0支持伴写功能


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs8IexaUO9iamyQJ2pJtTM41DGErmiabr0EQF9YHrQhDyuOtfbZkicxAcRJUlLe3JNQuK9rKmIKHOAtlw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：以上测评来自WPS官方社区测评  
资料来源：WPS社区，中金公司研究部


**风险因素**


**技术进展不及预期。**大模型能力本身仍然处于快速迭代时期，AI+代码应用的能力部分取决于模型能力。若大模型能力迭代速度放缓，可能会导致应用能力更新也放缓。

**行业竞争加剧。**近两年涌现出较多AI+代码应用，且部分应用呈现出同质化。若竞争加剧，可能会导致AI应用降价，从而影响相关公司的盈利能力。

**商业化落地不及预期。**当前AI+代码的商业化落地仍处于早期，商业模式和盈利能力的前景尚不明晰，存在商业化落地不及预期的风险。


\[1\]https://openai.com/index/introducing-openai-o1-preview/

\[2\]https://gitcode.net/csdnnews/2023-ai/-/blob/3cb87faeea8d7f667bab5c63150a4c77092679d9/CSDN_AI%E5%BC%80%E5%8F%91%E8%80%85%E7%94%9F%E6%80%81%E6%8A%A5%E5%91%8A1214.pdf

\[3\]https://gitcode.net/csdnnews/2023-ai/-/blob/3cb87faeea8d7f667bab5c63150a4c77092679d9/CSDN_AI%E5%BC%80%E5%8F%91%E8%80%85%E7%94%9F%E6%80%81%E6%8A%A5%E5%91%8A1214.pdf

\[4\]https://paperswithcode.com/sota/code-generation-on-humaneval

\[5\]https://www.cursor.com/blog/series-a

\[6\]https://www.thesaasnews.com/news/anysphere-raises-over-60-million-in-series-a

\[7\]https://github.blog/changelog/2023-11-30-github-copilot-november-30th-update/

\[8\]https://codeium.com/blog/series-c-annoucement

\[9\]https://developer.volcengine.com/articles/7389112569987858444

\[10\]https://developer.aliyun.com/article/1244398

\[11\]https://mp.weixin.qq.com/s?__biz=MzIwNTU0NDE1Ng==\&mid=2247498839\&idx=1\&sn=c31daf8a056691c93b929733adf848a9\&chksm=96b421f1710f251903d37097574d7cc43ecda06af4e67fc1251d934df4c67ea4f214de020cf8\&mpshare=1\&scene=1\&srcid=0914wFudWC5ur2pnfBswGQeh\&sharer_shareinfo=8d5353cc00bac38eebb3d9c1eb6a70d2\&sharer_shareinfo_first=8d5353cc00bac38eebb3d9c1eb6a70d2\&version=4.0.8.6027\&platform=win\&nwr_flag=1#wechat_redirect


**Source**


**文章来源**


本文摘自：2024年9月14日已经发布的《漫谈AI应用：AI+代码，生产力领域的应用先锋》

于钟海 分析员 SAC 执证编号：S0080518070011 SFC CE Ref：BOP246

王之昊 分析员 SAC 执证编号：S0080522050001 SFC CE Ref：BSS168

魏鹳霏 分析员 SAC 执证编号：S0080523060019 SFC CE Ref：BSX734

谭哲贤 分析员 SAC 执证编号：S0080524060005

王倩蕾 联系人 SAC 执证编号：S0080122090111


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


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYs8xtLU6ibdbskELfuUXx80zzFu9FicErmSM40xiaxrfhiaV68O3g6DcmjAq8qXG6yjKQgd6MX2veTBrfA%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)


[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7236271353093950720)
