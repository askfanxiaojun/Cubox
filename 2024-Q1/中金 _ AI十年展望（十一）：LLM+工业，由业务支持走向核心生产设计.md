中金 \| AI十年展望（十一）：LLM+工业，由业务支持走向核心生产设计
=====================================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/Xl2fXCqJlkZ0SMpp0hH5HA)王之昊 于钟海等 中金点睛


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FfzHRVN3sYsicmoVBv4D0mPib68kWJVkDjnEM91ZO46IRCPDfIfFpMEn2BoxwUa2fguPicQ4WwvNibdnOL4IqZj4XTA%2F640%3Fwx_fmt%3Dgif)


**中金研究**


在工业领域，传统AI模型（如数据分析预测、工业视觉等）应用已经相对成熟，但大语言模型（LLM）应用方兴未艾。我们观察到LLM应用正按照**经营管理侧、生产控制侧、研发设计侧**的顺序逐步落地，早期落地以企业知识库应用和数据分析应用等业务支持系统为主，尚未涉及核心设计和生产环节。我们认为AI对工业软件的改造存在广阔空间，年初至今工业软件赛道的AI逻辑演绎尚未充分，建议持续关注工业软件领域的AI落地进展。


**Abstract**


**摘要**


**研发设计侧：海外巨头产品落地计划明晰，国内有望映射对标。**研发设计侧工业软件门槛较高，与AI大模型融合也相对更难，我们认为AI+3D模型或成为继AI+文字/图片/音频/视频后的高门槛的落地场景。我们观察到海外CAD巨头Autodesk在工业端3D大模型已经有布局规划，其正探索基于云平台沉淀的数据进行大模型训练，计划通过多模态输入（自然语言+草图+规则约束）实现3D模型的生成式设计。Autodesk预计未来6-12个月能够实现原型模型的运行，我们认为国内CAD/BIM龙头厂商亦有望跟进，建议持续关注AI+3D模型研发进展。

**生产控制侧：数据分析场景落地先行，核心生产场景有望持续渗透。**生产制造侧工业软件涉及工业生产核心场景，对软件的安全性和稳定性有较高要求，目前核心生产场景大模型落地进度较慢，但海外自动化厂商在车间数据交互分析这类生产支持场景中已经有AI应用落地。我们认为伴随大模型鲁棒性持续提升，未来核心生产场景也有望得到AI赋能，建议持续跟踪离散行业大模型生成PLC代码、流程行业装置级操作寻优等场景的落地。

**经营管理侧：知识库应用落地广泛，AI有望赋能管理全流程。**我们在[AI Answer：大模型助力B端落地先行范式](http://mp.weixin.qq.com/s?__biz=MzI3MDMzMjg0MA==&mid=2247645669&idx=2&sn=7b0af22b9e2983b8602252f5e641be67&chksm=eade5f22dda9d634f1c11b022525df10d509dc96ffe499232fff77643415bcce825afd4da092&scene=21#wechat_redirect)中提出，企业知识库类应用有望成为大模型在OA、ERP等B端管理软件落地的先行场景，我们认为未来AI有望充分融合管理流程，在财务、人力、采购、营销等模块中实现AI赋能。


**风险**


工业侧AIGC落地进展不及预期；国内工业软件对标落地进度不及预期。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxnlce8kekL2DXc88XMOqr0PkIcLprVofRlR1SciaII3x4zRVonl2Rnjg%2F640%3Fwx_fmt%3Djpeg)

**[点击小程序查看报告原文]()**


**Text**


**正文**


**研发设计侧：海外龙头先行，国内对标映射**


**现有AI方案：基于给定约束解决优化问题**


**3D CAD：基于AI算法给定可选设计方案**

**传统AI算法能够基于约束参数生成可选设计方案，助力设计效率提升。**三维场景下的创成式设计功能主要由AI赋能。AI能够根据工程师提供的一组设计约束条件（例如定义设计空间，规定载荷位置、添加约束条件、圈定生成范围、选定材料和制造方法），在较短的时间内自主创建一系列满足上述条件的可编辑设计方案，供工程师选择和作出改进，从而缩短设计时间，提升工程师设计效率。同时，AI还能够根据设定条件生成优化的约束驱动设计，在节约成本的同时进一步提升设计产品的性能。目前，PTC Cero、Autodesk Fusion 360和西门子Solid Edge等工业设计软件中均集成了创成式设计功能。


图表1：创成式设计在3D CAD中的工作流程


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxozzicv6ufbUbAIbhgdtLlgnT4kO2kWr8iaxe7q4w3fqazx9rYib1b8icoA%2F640%3Fwx_fmt%3Dpng)


资料来源：西门子Solid Edge官网、中金公司研究部


**Autodesk Fusion 360创成式设计模块提高订阅费用。**Fusion 360中集成了CAD、CAE和CAM等功能，其创成式设计功能主要通过插件Generative Design Extension实现。该插件可基于工程师设定的约束条件要求，通过拓扑优化、人工智能和机器学习算法的组合，生成多个优化且可编辑的设计结果，并为每一结果估算制造成本。Fusion 360的创成式设计插件需额外订阅，根据公司官网，目前Fusion 360的年订阅费用为545美元（优惠后为382美元），月订阅费用为70美元；其创成式设计插件的年订阅费用为1,600美元，月订阅费用为200美元，我们认为创成式设计模块为Fusion 360拓展了提价空间。

**EDA：Synopsys.ai借助AI算法实现目标优化**

**Synopsys推出AI驱动型EDA解决方案，全面赋能芯片设计、验证、测试流程。**2023年4月，Synopsys在2020年3月推出的面向芯片设计空间优化解决方案DSO.AI基础上，又推出VSO.AI（验证空间优化）、TSO.AI（测试空间优化），共同构成全栈式AI驱动型EDA解决方案Synopsys.ai，该方案包含数字、模拟、验证、测试和制造模块，能够显著提升设计效率和芯片质量并控制成本。截至2023年1月，公司DSO.AI解决方案已经协助客户完成100次流片，其中覆盖了意法半导体、SK海力士等头部客户。借助DSO.AI，部分客户实现设计效率提高3倍以上、总功耗最多降低25%、裸晶芯片尺寸大幅缩减\[1\]。我们认为国内EDA头部厂商亦有望在AI赋能芯片设计领域持续研发布局。


图表2：Synopsys.ai通过使用AI算法解决芯片设计中的优化问题


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxdKyw6eEqNPhZC2rwDic2j4QMQQjYeiajtvlujzoyIMwnQZca1ibayvlKg%2F640%3Fwx_fmt%3Dpng)


资料来源：Synopsys官网，中金公司研究部


**AI应用展望：海外龙头先行布局，国内公司对标映射**


**工业端AI+3D模型研发进行时，Autodesk有望引领工业侧3D模型生成。**目前大模型在文字和图片生成任务上表现较优，而在3D模型生成领域仅依靠大语言模型的文字生成能力无法实现3D模型的构建。在海外3D CAD厂商中，我们观察到Autodesk布局较为领先，公司计划研发3D领域的大模型，基于Forma（AEC板块）、Fusion（制造板块）、Flow（媒体和娱乐板块）三大云平台沉淀的数据进行模型训练，并通过多模态的输入实现模型生成。

**基于多模态输入实现3D模型生成。**与文字生成任务不同，工业3D需要更为精确的输出，因此其对提示（Prompt）要求相对较高。纯文本的提示在描述精确的3D模型时实现的能力有限，因此在3D模型生成任务或需要一个多模态的输入，包括草图、源模型、文字描述、规范等；同时其需要对接LLM（大语言模型）的语义理解能力进行提示的理解和优化。公司计划未来6-12个月能够实现原型模型的运行，我们认为未来伴随海外工业软件龙头在AI方面的布局逐步转化，国内CAD/BIM龙头厂商也有望跟进研发。


图表3：AI+3D模型潜在的训练和推理过程


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZx1icOyn7JDQ3teLriaRKibraNonzmBBcEgiad03szSnibodicQndMcwCcN4Kg%2F640%3Fwx_fmt%3Dpng)


资料来源：Autodesk官网，中金公司研究部


**生产控制侧：从数据分析应用走向核心生产场景**


**现有AI方案：基于传统AI算法的数据分析和预测应用**


**传统AI算法侧重于数据分析预测和工业视觉检测等方面。**传统AI在生产控制侧工业软件的一大应用是基于数据训练预测性模型，例如在离散工业领域，罗克韦尔在2019年推出AI赋能的FactoryTalk Analytics LogixAI模块，LogixAI是罗克韦尔ControlLogix控制器的附加功能模块，可以通过内置AI算法模型对工厂生产操作过程中的数据变化趋势进行预测性分析\[2\]；在流程工业领域，横河电机与ENEOS材料公司合作，于2022年将基于强化学习的人工智能算法应用于后者的化工厂蒸馏塔，成功实现了人工智能自动控制工厂\[3\]。在数据分析预测之外，工业视觉检测也是传统AI的一大应用方向，例如施耐德电气武汉工厂通过AI工业视觉检测平台对各类工业控制元器件产品进行质量检测，将产品过检率稳定控制在0.5%以内\[4\]。


图表4：罗克韦尔LogixAI模块功能定位图


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxg3rW6nqMemicWLHibkyVJ1icqlJrK7ich69mvE7f2FQQC3gXhHbkAyo3MA%2F640%3Fwx_fmt%3Dpng)


资料来源：罗克韦尔自动化公司官网，中金公司研究部


**ABB与微软携手推出GPT赋能的自然语言交互式数据分析产品。**2023年7月，电气与自动化领军企业ABB宣布与微软合作推出Genix Copilot，将Azure OpenAI服务整合至ABB Ability Genix工业分析平台中，利用AIGC技术帮助工业企业客户提升数据分析和治理能力。整合了GPT-4等大语言模型的ABB Genix软件将可以生成代码、图像和文本等多种内容，通过自然语言交互的方式较大改善用户体验，为客户实时提供数据分析服务。根据ABB官网，Genix Copilot提供的数据分析洞见有望将资产生命周期延长20%，将设备意外停机时间减少60%\[5\]。


图表5：Genix Copilot用户界面


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxmTbwMmpcdW5f6Db5roVVo9CBtCxYWlmsGJo64uvGTU5DlgOWJj765A%2F640%3Fwx_fmt%3Dpng)


资料来源：ABB公司官网，中金公司研究部


**AI应用展望：离散行业GPT+PLC，流程行业装置级大模型**


**离散行业：西门子与微软合作打造离散行业GPT赋能PLC范例。**2023年4月，西门子宣布与微软达成合作，将AIGC能力全面应用于工业设计、制造和运营全流程中，其中的一大合作重点是通过生成式AI能力实现可编程逻辑控制器（PLC）的代码自动开发\[6\]。在德国汉诺威工业博览会上，西门子和微软演示了通过ChatGPT和其他Azure AI服务高效率生成PLC代码，从而减少工程团队的开发时间和错误概率；此外，GPT大语言模型还可辅助工程师完成后续的PLC代码优化和调试等工作，从而加速PLC代码开发全过程。

**流程行业：中控技术打造流程行业装置级大模型supGPT。**2022年，中控技术发布自研的流程工业过程模拟与设计平台iAPEX，覆盖工程设计、建设实施、生产运营、全生命周期运维等流程工业全过程。公司计划基于在iAPEX平台上运行得到的海量数据来训练类GPT大模型supGPT，通过supGPT实现装置推优等目的，同时利用装置运行数据微调优化supGPT模型，实现模型动态优化；supGPT也将赋能公司的全流程智能管理与控制系统i-OMC 2.0，全面助力产品智能化。


图表6：中控技术supGPT示意图


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxlutNao2z6h67hBBMWlOYdksAz2UYyRmXagKic0iaDwKckoIGxxJ1rGjg%2F640%3Fwx_fmt%3Dpng)


资料来源：中控技术2022年及1Q23公开业绩交流会，中金公司研究部


**经营管理侧：知识库广泛落地，AI有望赋能管理全流程**


**现有AI方案：知识库是AI大模型在B端落地最快的应用**


**以知识库为代表的AI Answer类应用落地广泛。**我们在[AI Answer：大模型助力B端落地先行范式](http://mp.weixin.qq.com/s?__biz=MzI3MDMzMjg0MA==&mid=2247645669&idx=2&sn=7b0af22b9e2983b8602252f5e641be67&chksm=eade5f22dda9d634f1c11b022525df10d509dc96ffe499232fff77643415bcce825afd4da092&scene=21#wechat_redirect)中提出，企业知识库类应用有望成为大模型在B端落地的先行场景，企业管理软件赛道已陆续落地知识库应用。目前除OA厂商外，部分ERP赛道公司陆续推出大模型赋能的企业知识库应用，助力企业知识高效流转和使用。

**ERP中AI Answer落地展望：大模型助力下AI Answer赋能生产流程管理。**与OA相比，ERP与业务和生产联系更紧密且具有更明显的行业属性，在业务运行过程ERP沉淀的行业垂类数据有望助力大模型的训练。

**鼎捷软件：联手OpenAI发布B端个人助理\&企业知识库应用**

**联手微软发布METIS，落地多应用场景。**6月16日，鼎捷软件中国台湾子公司鼎新电脑与微软Azure OpenAI举办战略合作发布会，介绍了今年7月即将正式发布的GPT大模型赋能的PaaS平台METIS，并基于此平台推出个人智能助理（预约会议、汇总信息、催办任务、提示行程等功能）、企业知识大脑（METIS ChatFile，能够解析文件并智能分类，基于GPT大模型实现自然语言问答交互）、AI辅助开发（AI赋能需求分析、系统设计、程序开发）三大功能。


图表7："娜娜帮我"个人助理应用


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxTOtzPpPxRAVGIc6icDo5N0cVticKRmgmqS3V6CeQJjq4mcibzOwy0AIEA%2F640%3Fwx_fmt%3Dpng)


资料来源：鼎新电脑x微软Azure OpenAI战略合作发布会，中金公司研究部


图表8：ChatFile企业知识库应用


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxU9R5WQhqWWHte2jzK6MGyO9NFOuDiaXIomyJAE743sdQhdWsfrNwx2g%2F640%3Fwx_fmt%3Dpng)


资料来源：鼎新电脑x微软Azure OpenAI战略合作发布会，中金公司研究部


**汉得信息：基于AIGC中台打造知识管理和AI助手应用**

**基于第三方大模型打造知识平台\&智慧交互平台。**汉得信息计划7月底发布AIGC中台\[7\]，将在汉得HZERO融合中台上预留第三方大模型接口和通用AI应用功能，并提供低代码AIGC应用编排工具。公司计划将在营销、物流、车间、财务等场景布局AI应用，目前公司已具备知识平台、智慧交互平台等应用：

**► 汉得AI知识中台：帮助企业更方便构建知识库。**汉得AI知识中台提供构建企业私有知识库的大模型基础应用能力（账号管理、Token配额管理等），以及向量数据库、文档管理、权限管理等能力。

**► 汉得智慧交互平台：个人AI助手应用。**基于自然语言交互，汉得智慧交互平台能够完成数据分析、业务处理（如提交请假申请）等功能，成为客户的"AI助手"。


图表9：汉得AIGC中台技术框架


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxTHodeQFYphw3ficr0Oj5yRgeQ4O3THicbNtqteicbyjCamAFFLFHdsVPg%2F640%3Fwx_fmt%3Dpng)


资料来源：汉得信息微信公众号，中金公司研究部


**赛意信息：谷神工业aPaaS平台融入AI能力**

**谷神aPaaS平台融入AI，助力开发者提升研发效率。**谷神aPaaS工业平台融合大模型，具备智能对话、文本处理、图片和图表生成、代码处理、AI翻译、聚合搜索等能力，助力企业数字化团队完成研发过程中的市场调研、需求提炼、解决方案撰写、代码生成优化等工作，助力研发人员提升研发效率。其融合AI能力的低代码平台能够根据用户需求自动生成相应的数据模型，自动匹配表单模板库、创建业务表单、AI辅助编码，公司计划未来将谷神工业aPaaS平台融合更多产品研发和工业应用场景。


图表10：谷神工业aPaaS平台AI引擎架构


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxC8e95CAXICnlos2hvyjyyXgYBpOjU4bPmQXGg9UYbcJraR7WBjWGCQ%2F640%3Fwx_fmt%3Dpng)


资料来源：赛意信息微信公众号，中金公司研究部


**AI应用展望：以Dynamics 365 Copilot为例看AI重塑企业服务场景**


**客服场景：助力业务人员"对答如流"**

**深度打通企业服务和工具软件，客户服务效率提升。**销售和客服应用Dynamics 365 Sales、Viva Sales、Dynamics 365 Customer Service中均深度集成了AI能力，并能够和Teams、Outlook实现打通，如AI能够自动提取CRM中产品和报价等信息，在Outlook中快速生成给客户的邮件回复。在客服咨询过程中，Copilot能够针对聊天对话和电子邮件记录自动生成复合语境的答案。


图表11：Copilot AI赋能销售和客服场景


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxmywzb6uFLiclbucWic9hCnOSh6EPIicDEWbenUPibwJOWv66sPTibwvRxlw%2F640%3Fwx_fmt%3Dpng)


资料来源：微软官网、中金公司研究部


**市场营销场景：AI赋能实现营销提效**

**Copilot赋能下快速找到目标受众和生成推荐内容。**在Dynamics 365 Customer Insights和Dynamics 365 Marketing中，市场推广人员通过简单的自然语言指令就能够借助Copilot实现快速分析数据、分析受众并快速定位目标客户。另一方面，通过给定客户群体的自然语言描述，Copilot能够快速生成市场推广电子邮件的内容建议。


图表12：Copilot赋能市场营销场景


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxYNoVBpjcI0N6KSOOlwTMicQZdx1IUicwqpoP8MuqPzC3Up6voNQHtoRw%2F640%3Fwx_fmt%3Dpng)


资料来源：微软官网，中金公司研究部


**供应链场景：AI赋能降低供应链风险**

**Copilot赋能下供应链敏捷性实现提升。**在Dynamics 365 Supply Chain Management中，Copilot能够主动对可能影响供应链的事件（如极端天气、财务状况、地理环境等）进行预警，将可能受影响的订单详细信息进行呈现。与此同时，其能够自动撰写预警邮件发送给供应链伙伴，降低供应链风险。


图表13：Copilot赋能供应链管理场景


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxtj5hFgGOJJ2AcZ0kKiaicp44uBdBacpJsibLXIZJUklHY3ym6oKPIRpGQ%2F640%3Fwx_fmt%3Dpng)


资料来源：微软官网，中金公司研究部


**风险提示**


**工业侧AIGC落地进展不及预期。**目前大语言模型（LLM）在工业端的落地尚处于起步阶段，未来技术演进仍然具有不确定性。若技术进展不及预期，则工业侧AIGC落地进度或有所延后。

**国内工业软件对标落地进度不及预期。**目前国内高端工业软件相较海外技术仍具有一定差距，与大模型的应用结合或慢于海外工业软件龙头厂商，或导致国内工业软件对标落地进度不及预期。

\[1\]https://mp.weixin.qq.com/s/WbgaB1TopW8RtoXiuq6f9Q

\[2\]https://www.rockwellautomation.com/en-us/products/software/factorytalk/operationsuite/analytics-logixai.html

\[3\]https://mp.weixin.qq.com/s/iuR4JcDtZQu-0dbkBFU2dg

\[4\]https://mp.weixin.qq.com/s/6kWJ6jQRrtXTZyF0o9ovYQ

\[5\]https://new.abb.com/news/detail/104829/abb-and-microsoft-collaborate-to-bring-generative-ai-to-industrial-applications

\[6\]https://mp.weixin.qq.com/s/s1_ZtARadefx9vceOxPpbg

\[7\]https://mp.weixin.qq.com/s/tNG3A8z0wP2g20gG_tRnlw


**Source**


**文章来源**


本文摘自：2023年7月14日已经发布的《人工智能十年展望（十一）：LLM+工业，由业务支持走向核心生产设计》

王之昊 分析员 SAC 执证编号：S0080522050001 SFC CE Ref：BSS168

于钟海 分析员 SAC 执证编号：S0080518070011 SFC CE Ref：BOP246

谭哲贤 联系人 SAC 执证编号：S0080122070047


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


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYsibrjY79dTiaM2cCKqHnVTKZxFToCjPts5PWjmwzZnbDFbApd6ibAzPDE4gpHs0EbNKBwRzEDmricf2Tw%2F640%3Fwx_fmt%3Djpeg)


[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7166705415567183173)
