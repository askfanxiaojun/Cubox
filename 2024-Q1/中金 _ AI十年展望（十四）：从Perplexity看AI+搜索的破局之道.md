中金 \| AI十年展望（十四）：从Perplexity看AI+搜索的破局之道
=======================================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/3qRaJ-o9H6U4QcRZcrGyKQ)于钟海 魏鹳霏等 中金点睛

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FfzHRVN3sYsicmoVBv4D0mPib68kWJVkDjnEM91ZO46IRCPDfIfFpMEn2BoxwUa2fguPicQ4WwvNibdnOL4IqZj4XTA%2F640%3Fwx_fmt%3Dgif)

**本文作者：于钟海,魏鹳霏,王之昊,游航**


**中金研究**


大模型（LLM）路线于2023年带来学术和产业界颠覆式变革，ChatGPT等应用依托领先模型技术而建立先发优势。在产业趋势下，Perplexity以"生成式+搜索"建立差异化优势。自 2023年2月1日至10月25日，网页端的周度访问量由275万增加至1,113万，增长3倍，彰显LLM+搜索引擎新业态的粘性和潜力。**本文以Perplexity为例，对其技术原理、商业模式及未来展望进行探讨，以期为国内搜索及C端生态演进借鉴参考。**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_gif%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzMuSicr1grCF7X6QMs7Ko5GB9XhJGQKb0FI4tkfdHMtfAZlL6d2qBY5Q%2F640%3Fwx_fmt%3Dgif%26from%3Dappmsg)


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykz2pCOd1tmKvMYIXGZvLgt8IcKOXquKZTk43Wwicc0XBSonWJmJU3asIg%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)

**[点击小程序查看报告原文]()**


**Abstract**


**摘要**


**Perplexity是AI+搜索引擎的创新者和领先者，卡位LLM+搜索引擎新业态。**Perplexity于2022年8月成立，公司创始人曾任职于OpenAI，公司获OpenAI、Meta内部AI负责人等注资。Perplexity基于GPT-3.5微调模型等通用智能生成能力及微软Bing搜索引擎构建，对比ChatGPT等生成式AI时效性更强、具备可溯源属性，对比谷歌等传统搜索引擎答案凝练、可实现上下文响应。我们认为，Perplexity依托于LLM+搜索的产品力、工程化能力、快速迭代能力在To C应用中突围。

**检索增强生成为核心技术，召回能力与响应速度树立差异化。**检索增强生成技术（RAG）包含检索、生成两个环节。RAG融合外部知识库与模型先验知识，外部知识库丰富且易于更新的数据有效弥补了大模型数据滞后、伴有幻觉的劣势。Perplexity以RAG为基，在算法侧对检索系统的核心"召回"环节进行创新，召回率和精确度在同类产品中排名第一；在响应速度方面，Perplexity采用自研推理堆栈pplx-api，并在推理端使用TensorRT-LLM加速，延迟大幅降低；模型侧，公司对GPT-3.5进行微调，在降低成本的同时进一步提升响应速度。

**展望未来，我们认为对话式搜索引擎新业态有望成长为主流生态，但竞争趋于多元化，场景和数据闭环为核心要素。**需求侧，Perplexity快速增长的用户数量验证了对话式搜索引擎的刚性需求，LLM+搜索的产品形态或将长期存在。供给侧，Perplexity产品定位对标New Bing、Bard，谷歌等互联网巨头具备数据和场景卡位优势，更易于实现AI Agent的场景闭环，竞争格局趋于多元化。但随着Perplexity社群、pplx-api生态的逐步完善，我们认为独立第三方的开放生态也有望助力公司夯实自身壁垒。


**风险**


商业化风险；数据闭环风险；行业竞争加剧风险。


**Text**


**正文**


**AI+搜索引擎，重塑知识发现新范式**


**Perplexity：AI对话式搜索引擎**


**Perplexity是大模型+搜索引擎的领先实践者，融合"生成"与"搜索"，相比于ChatGPT具备时效性强、支持溯源、支持垂类检索等特点。**Perplexity基于GPT-3.5或GPT-4的通用智能生成式能力，以及微软Bing搜索引擎构建。当用户输入prompt提问，Ask会生成引用来源、回答内容以及其他相关问题，用户可以直接点击来源链接查看。Perplexity与ChatGPT等大模型相比具备更强的时效性，与Bard等具备联网功能的对话机器人相比能够生成带有引用的答案支持用户溯源，与New Bing相比回答内容有用性突出。此外，Perplexity在搜索时可以选择学术、写作、YouTube等垂类领域，具备较强针对性。


图表1：Perplexity用户搜索界面及回答


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzJkYu0SXOVGKftHeNE8icSX2Y3XGMLRR34yiaKzL7ugQpnsuqRdIiaXNQg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：深思SenseAI公众号，中金公司研究部


图表2：ChatGPT回答界面


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzmODdId1Fb1WoZfmnOOM4jZXsxiaazhe66D1dBFtTRDfXHuYuyKialIGQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：深思SenseAI公众号，中金公司研究部


图表3：谷歌Bard回答界面


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzdNV3DeklGphNINbSyt2epxWeccYvbmwO0smm54vxcHiaMbEaMzXnv0g%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：深思SenseAI公众号，中金公司研究部


图表4：New Bing回答界面


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzfkFuYkiaDXCIvmpv2cd4WVryz2B74tZ6puWmoU8wR9QMhOicl2WUNjHQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：新智元公众号，中金公司研究部


图表5：Perplexity支持多个垂类领域搜索


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzKeUuPI9WjF4e9AXLocsMWSJrkTYnpHR1CCyu6SOfswcjbjQKMf6icUQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：深思SenseAI公众号，中金公司研究部


**周度访问量环比高增，用户基础持续扩张彰显高粘性和成长性。**Perplexity成立于2022年8月，致力于开发基于AI能力的对话式搜索引擎，以优化用户发现和共享知识的方式。2022年12月公司正式发布首个对话式搜索引擎Ask，此后其用户规模不断扩大，在四个月内月活跃用户数达到200万。根据Similar Web数据，截至2023年10月25日，Perplexity APP的日度下载量为14,163次；2023年2月1日至10月25日，Perplexity网页端的周度访问量由275万增加至1,113万，增长3x；与同类别的AI搜索应用YouChat相比增长势头强劲。


图表6：Perplexity APP下载量（日度）


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzbBCw2tzMIXnvTTbnFLTEdtMibOhoianMUrQrnaLjmr8K41XXkHo7OWzg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：数据截至2023年10月25日

资料来源：Similar Web，中金公司研究部


图表7：海外搜索网页端AI应用访问量（周度）


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzL7xzNlVefib8b4nlQ7KibRlYquOBSJXu10Mjia8z518UDB3lWlkchHOxw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：数据截至2023年10月25日

资料来源：Similar Web，中金公司研究部


**公司定位：LLM+搜索引擎的新业态，生成与检索兼容并包**


**Perplexity在ChatGPT与传统搜索引擎的基础上开发，兼具大模型的生成与推理能力，又囊括传统搜索引擎中内容的广度和时效性，是AI能力与搜索引擎的融合，定位与New Bing和Bard类似。**搜索引擎具备搜索的实时性，但信息颗粒度以网页来衡量，未能实现搜索目的的"最后一公里"；而ChatGPT以生成式LLM为基础，实现了信息粒度的细化和融合，但实时性与幻觉\[1\]问题随之而来。Perplexity定位于LLM+搜索引擎的中间态，将二者优点相结合，侧重搜索体验的产品力而非基模型。


图表8：Perplexity与ChatGPT、传统搜索引擎差异化定位


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzcPEFjoF24NKP5gasCJSTT0wDvv3C2lJKiacHjjwcxC6V1LWBzuv8cvg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


**► Perplexity vs ChatGPT具备以下核心优势：（1）信息时效性强：** ChatGPT等大模型只包含训练时的数据和语料，后续信息无法及时更新。Perplexity基于底层传统搜索引擎开发而得，具备时效性强的优点。**（2）易于溯源：** Perplexity生成的每一句话都附有引用链接，在保证可靠性的同时便于用户溯源或深入研究。**（3）减轻幻觉：**Perplexity检索内核及标示来源的方式大大降低了幻觉，没有查到相关内容时会主动表示，减少了大模型有时出现的"胡言乱语"的情况。

**► Perplexity vs Google等传统搜索引擎具备以下核心优势：（1）页面简洁凝练：** 输入一个问题时，传统搜索引擎呈现多个并列链接，其中穿插大量广告，而Perplexity会结合部分最相关的链接直接生成精炼答案。**（2）支持细分领域精细搜索：** Perplexity支持用户选择学术、写作、YouTube等垂类领域精确搜索，使结果更具针对性。**（3）上下文连贯响应：** 类似于ChatGPT，Perplexity可以进行上下文响应，而传统搜索引擎却无法保证逻辑的延续性。**（4）问题拆解和追问能力：** 基于大模型的理解能力，Perplexity可以对用户提问逐步拆解并追问澄清，精确把控用户需求。**（5）反馈功能：**Perplexity生成回答后，用户可以对其准确性进行反馈，以强化学习的反馈机制帮助其进一步提升模型准确性。

**► Perplexity vs Bard：** Bard为基于Gemini Pro大模型的AI助手，产品形态与ChatGPT类似，但集成了谷歌搜索引擎，具备时效性。生成答案后，用户可点击下方的"Google"按钮进行搜索，Bard同时对AI生成的内容进行核查，分别标注有、无搜索结果支持的内容（此功能目前只支持英语），用户可点击链接进一步查看。Perplexity对比Bard主要具备三点优势：**（1）易于溯源：** Bard提供的链接为Google搜索到的相关信息，并不代表其答案由该链接总结生成，用户无法对生成答案直接进行溯源验证。**（2）幻觉较低：** 生成式AI在Bard中发挥主要作用，需要外部信息时启动搜索功能，因此仍然具有幻觉。**（3）细分领域精细检索。**

**► Perplexity vs New Bing：** New Bing定位于AI搜索产品，功能与Perplexity较为接近，但Perplexity具备以下优势：**（1）性能更加强大。** 与New Bing相比Perplexity的生成速度和内容有用性更高，在第二章我们会对此进行详细说明。**（2）支持细分领域精细检索。**


图表9：Perplexity vs ChatGPT及传统搜索引擎


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzrH0DW879IFtJEy49ereQEcJibKw2MYoa9Qr02WEjsEtV9ibo6D6NKNOg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


**历史沿革：2022年成立即聚焦于AI+搜索引擎，踏浪生成式变革**


**Perplexity成立于2022年8月，早期即确定AI搜索引擎路径，侧重产品力及快速迭代。**成立之初，公司技术定位于text2sql（将自然语言翻译转化为SQL），但受制于技术的先进性以及SQL市场难以建立通用解决方案，这条路径并没有行通。2022年11月30日ChatGPT推出的背景下，业界迅速认可大模型的泛化通用能力。2022年12月，公司借势推出第一款核心产品Perplexity Ask，定位AI搜索引擎，并推陈出新，先后推出BirdSQL、Copilot、Profile、pplx-api等产品，同时对Perplexity Ask及Copilot进行了快速迭代。纵观整体产品矩阵，我们可以发现公司始终专注于支持引用的AI搜索引擎，通过创新迭代优化其性能，不断提升客户的用户体验。

**► Perplexity Ask：**全球首个对话式搜索引擎，基于GPT-3.5和微软Bing构建。用户输入问题后，Ask生成由大模型提炼后的回答，右上角附有引用链接，下方展示引用来源，用户可以直接点击链接溯源进行验证。此外，Ask还会提示后续相关问题，点击即可生成对应答案，帮助用户优化搜索闭环。

**► Copilot：**2023年5月份公司发布Copilot，由GPT-4提供支持。Copilot通过提出问题的形式对问题中的细节进行补充，可以精准把控用户需求，改善搜索体验。例如，用户让Copilot帮助挑选一款头戴式耳机，它会让用户选出理想的耳机类型、特征及价格区间，进而推荐合适的产品；通过选择目的地、活动类型等，Copilot还可以量身定制履行计划。在GPT-4的理解和规划能力赋能下，Copilot作为生产力工具切实提升用户的生产生活效率。2023年8月，公司对Copilot进行了更新，使用微调过的GPT-3.5达到与GPT-4在特定任务上的近似效果，在大幅降低成本的同时提升了整体性能。

**► BirdSQL：**BirdSQL是基于公司text2sql路线开发得到的Twitter搜索界面，使用OpenAI Codex将自然语言转换为SQL。输入需求后，Bird SQL会给出搜索结果及SQL代码，还能进一步对数据进行可视化产出统计图表，让不懂代码的人也可以实现轻松"爬虫"。但2023年2月底，Twitter关闭了相关接口，BirdSQL下架。


图表10：Perplexity发展历程


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzyaxGIhAsP2fb4Cc49UYTqhppCVjOnZNM2FJEUyVb9wd5llL7loFABw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


图表11：Copilot产品界面


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzgSUp9UuNS5gdPxbvgt6Wsicy48kEAE3CJWkFgTdeK2zDicSK82P6H6cA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：海外独角兽公众号，中金公司研究部


图表12：Bird SQL产品界面


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzdHicjbAV9TxnttqnzymURG8LyXwGpQtptYicwGyDIZCqYrCgPpSgm5YA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：海外独角兽公众号，中金公司研究部


**► Profile：**Profile为用户提供个性化的AI问答体验。通过自我介绍，用户可以输入自己的基本情况建立画像，Perplexity针对性地进行回答，成为个性化的AI助手。

**► Perplexity Labs：**Perplexity Labs为用户提供多种大模型交互体验，包含Mistral、Llama、CodeLlama等开源大模型以及Perplexity的自研模型pplx-7b、pplx-70b。pplx-7b和pplx-70b是在mistral-7b、llama2-70b模型基础上微调增强所得。2023年11月29日在Labs中开放了自研模型的online版本，可以使用Perplexity的内部索引获取互联网信息，保证信息的时效性。


图表13：Profile产品界面


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykz6ia4iaNlL1Ff8pFAcu97qdHiav9r7AgZc8uiaeURiaaXLRsNo9jE0fsnJ6A%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：海外独角兽公众号，中金公司研究部


图表14：Perplexity Labs产品界面


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzDQGdOlHWhuFuw5TAVrJVuKSxkgasH1Xib7fDiab0xPoUBCqm01Zn4IbQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：新智元公众号，中金公司研究部


**创始团队：具备AI基因+搜索行业经验，获产业界名人注资**


**创始人兼具技术实力与行业洞察力。**Perplexity创始人为Aravind Srinivas、Denis Yarats、Andy Konwinski以及Johnny Ho四位。Srinivas曾于Google、DeepMind实习且曾就职于OpenAI。Yarats曾在微软Bing、问答网站Quora、Facebook担任人工智能研究人员或工程师。Konwinski为DataBricks的联合创始人。Johnny Ho曾在Quora担任工程师，研究排名与后端系统，引领系统快速迭代。

**团队成员经验丰富，对LLM及搜索引擎有深入见解。**截至2023年10月，Perplexity团队不足50人，但大多数员工都拥有在谷歌、英伟达、Quora等科技企业的工作经验，对大模型及搜索引擎有着独到而深入的理解，为公司开发出性能优异的产品及后续的高速迭代夯实基础。


图表15：Perplexity创始人团队


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzomlibIiaCeY11DqFBWFEON7Am8jGoTfWYIW0TUzbX4DklUGw1uwWHZvQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


**Perplexity获多位AI产业界名人投资。**2022年9月，公司完成种子轮融资，金额共计310万美元；2023年3月，公司完成2,560 万美元的 A 轮融资。Perplexity吸引了诸多AI领域的知名人物投资，其中包括Meta 首席AI科学家及图灵奖获得者 Yann LeCun 、微软前总裁Bob Muglia、前GitHub 首席执行官 Nat Friedman、Open AI创始成员Andrej Karpathy等。


图表16：Perplexity融资状况及投资者


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzQsKUeRfDJGRFAuMiawkdGcTAicXFoJKrBy2CsxeibFN6qWRIhg5elWRsA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


**以检索增强生成技术为基，召回能力树立差异化**


**技术原理：以RAG为技术核心，召回与生成式AI优点兼容并包**


**我们认为以RAG（Retrieval Augmented Generation，检索增强生成）技术为核心的对话式搜索引擎有望成为新产品形态。**前文中，我们将以ChatGPT为代表的通用大模型与Perplexity进行了对比，LLM主要的问题为内容时效性差和缺乏索引带来的潜在幻觉风险。LLM无法生成训练数据与语料库之外的内容，也无法为生成内容提供精确索引和参考依据。2020年，Meta的研究人员通过引入RAG解决了这一问题，把与问题相关的事实交给LLM加工和学习，不仅结合了生成模型的先验知识，也汲取了检索模型的实时性和内容丰富性优势。


图表17：传统搜索引擎、问答引擎与大模型技术对比


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzgaNxNg3oOkWqibhsaOib557JGicfiaoQPWoEpnEsS2Ige7ZM3I24LeKmvw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：中金公司研究部


**生成式AI语言理解与生成能力突出，但存在幻觉、数据缺乏实时性等劣势。**生成式AI（Generative AI）是一种基于AI技术的机器学习模型，它对海量训练数据进行学习并根据其特征生成与原始数据相似的全新内容，生成内容可以为图像、视频、音乐、语音和文本等。近年来计算机硬件性能的提升和预训练技术的发展使生成式AI能力实现跃迁，以ChatGPT为代表的大型语言模型具备语言理解能力强大、多样化生成能力等优点，被广泛应用于各行各业。但生成式AI无法做到实时更新，且受限于训练数据，可能无法覆盖相对小众、缺乏通用性的长尾知识。同时，生成式AI对生成内容的可控性较差，存在"幻觉"问题，用户也难以对答案进行直接验证。

**检索增强生成（RAG）融合外部知识与模型先验知识，有效弥补生成式AI缺陷。**检索增强生成（Retrieval Augmentation Generation）由检索和生成两部分组成，首先在知识库中根据需求召回最匹配的文档内容，再作为提示词输入模型生成答案。


图表18：检索增强生成（RAG）技术原理


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzGxog2uJjProaWhVOvUgIKZeENA7O6EAw4ZcbxbEllG9ic7nZab3TGuQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Lewis, Patrick, et al. "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks." ArXiv abs/2005.11401 (2020): n. pag.，中金公司研究部


**► 检索系统（Retriever）：**检索环节包括需求编码器（Query Encoder）和文档索引（Document Index）。使用两个不同的BERT模型将需求q与文档z分别编码为q(x)和d(z)，进而使用最大内积搜索算法获取内积最大的文档，将其与需求共同输入生成部分。

**► 生成系统（Generator）：**在此环节，生成器根据检索器总结输出最终答案。大模型会根据输入预测下一个词的出现概率，并生成概率最大的单词。共有两种方式计算生成概率：1）RAG-Sequence：使用同一个文档预测，先确定文档再计算候选词概率；2）RAG-Token：使用不同文档预测，每个候选词的概率为所有文档的条件概率之和。

**RAG技术下知识源于非参数记忆与参数记忆，覆盖范围广且易于更新。**非参数记忆为检索系统召回的文档链接，参数记忆为预训练模型储存的知识，对应Meta的技术论文中，二者分别为维基百科和BART模型\[2\]。相较于生成式AI，RAG路径下源于外部知识库的非参数记忆更新可以轻松实现，确保了生成内容的覆盖广度和实时性。在生成答案时，RAG技术也可以将引用的外部来源进行标记，便于溯源。

**RAG在开放域知识问答及生成式问答中性能领先。**Meta的技术论文对RAG技术进行了详细测评，包括开放域问答、开放域问题生成、抽取式问答及分类推理任务。在开放域问答中，RAG-Token和RAG-Seq得分处于领先地位；在生成任务和分类任务中，RAG表现优于BART模型。


图表19：RAG在开放域问答测试中成绩领先


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykziaQ2HuVPFbPEicBLXJ2ukdFfdKzIJ7xrwHicWH7ibeLWfI776a1GFxZw5A%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：NQ、TQA、WQ、CT分别为Natural Questions、Trivia QA、Web Questions和Curated Trec四个数据集。

资料来源：Lewis, Patrick, et al. "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks." ArXiv abs/2005.11401 (2020): n. pag.，中金公司研究部


图表20：生成任务和分类任务中各模型能力对比


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzzoRlxEm4sbaia3fIuUhZNHHQcicHa1VbyEm3z2oSSCiaMaJV4iavJno92Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：1）Jeopardy为开放域问题生成数据集；2）MSMARCO为抽取式问答数据集；3）FVR3、FVR2为分类任务数据集，分别表示三分类与二分类数据集。

资料来源：Lewis, Patrick, et al. "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks." ArXiv abs/2005.11401 (2020): n. pag.，中金公司研究部


**Perplexity的RAG技术路径是"搜索引擎检索---高效召回相关内容---大模型推理---生成具备索引定位的回答"。**用户输入查询时，Perplexity会对查询进行理解重构，然后将需求发送到Bing搜索引擎，从外部索引中"召回"最相关的链接，再将用户提问与检索答案合成Prompt（提示）提交给大模型，由大模型完成整合、生成简洁回答及标注来源的任务。在此技术路径下，Perplexity将传统搜索引擎的知识广度与大模型的推理、生成能力相结合，为用户提供精简可溯源的答案，优化了用户的搜索体验。


图表21：Perplexity技术路径，"检索-召回-大模型推理"


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykz6wkdDYybFxfYZxicpfATYjXF5c5fDZr590k8e9xqnswibAhWst4oqzyQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


**"召回"和"排序"为传统搜索引擎的决定性环节。** 传统搜索引擎的技术路线分为数据、检索以及匹配三步：1）收集互联网上的海量数据并进行初步处理；2）为每个数据打上合适的"标签"并设计一套精妙的检索方案以便随时找到合适的数据；3）收到搜索指令后，对其进行拆解分析，把与指令有关的数据按照相关性进行排序，最终呈现最佳答案。而在搜索引擎的设计中，最核心的技术则是"召回"和"排序"，他们决定了搜索引擎的精确程度和性能上限。其中，"召回"指根据搜索指令从数据库中获取尽可能多的正确结果，"排序"指根据用户搜索内容的相关性对召回结果进行排序。


**技术优势：Perplexity召回与响应速度领先，夯实差异化产品力**


图表22：传统搜索引擎技术路线


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykz8WgMFMtsHsKCpxhxPtdFGTic7jibiaLrgMx1vBVSUoKK5XMWFdxaGMKXw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：昆仑万维公众号，中金公司研究部


图表23：生成式搜索引擎能力对比


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzNMgz2IANjX2hVQnupLyu3ib6HlsghxemPHHC5uHBmACLoRZUDPGPicaA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：1）有用性(perceived utility):回复对用户查询来说是否是有用且有信息量的；2）引用召回(citation recall):指由其相关引文完全支持的、值得验证的句子的比例。

资料来源：Liu, Nelson F., Tianyi Zhang and Percy Liang. "Evaluating Verifiability in Generative Search Engines." ArXiv abs/2304.09848 (2023)，中金公司研究部


**Perplexity算法侧进行创新，召回率和准确率领先。**当大模型被引入后，它对搜索技术的重塑贯穿每一个环节。例如，在召回环节，大模型能够模仿人类的识别判断能力，更有效地召回结果；在排序环节，大模型可以考虑更多语言细节，提升排序性能。据Perplexity创始人Aravind Srinivas公开演讲\[3\]，Perplexity在召回和排序环节都对算法侧进行了创新，保证内容的有用性及引用的精确程度。在2023年4月的论文中，斯坦福的研究人员对YouChat、Perplexity.AI、NeevaAI及BingChat四个生成式搜索引擎进行了人工评估\[4\]。结果显示，Perplexity.ai生成内容有用性的评分为4.56分，排名第二；引文召回率和精确度为68.7，排名第一；在泛搜索引擎类的体验中，综合能力位于最前列。

**公司自研推理堆栈，大幅提升响应速度。**除引用内容精确外，Perplexity的生成速度快于GPT类通用模型。从技术路径分析，一方面，Perplexity检索后由大模型总结，而检索本身响应速度快于预训练大模型的推理速度；另一方面，在采访中Aravind Srinivas表示Perplexity未使用Hugging Face等第三方推理栈，而是基于自定义的简化推理堆栈，即pplx-api，进一步提升响应速度。公司使用英伟达的TensorRT-LLM对大模型推理进行精心设计和优化，底层基础设施为英伟达A100提供支持的AWS P4d实例。在于其他API的对比中，pplx-api的总延迟降低了65%，初始响应延迟降低了77%，处理token的速度较TGI领先47%-85%。除内部使用外，pplx-api还面对开发人员提供开源大模型集成服务，使其可以轻松地集成Mistral 7B、Llama2 13B、Code Llama 34B、Llama2 70B、replit-code-v1.5-3b等尖端开源LLM，易用优势显著。


图表24：Perplexity API其他API的延迟对比


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzwzxcF5BQOuvLGNfHEo3Y4Kx971X7b8mPia9WQW1Pfnyp3hCsYhwsHBg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


**模型侧，基于GPT-3.5 API进行微调，降低成本、进一步降低延迟性。**2023年8月，Perplexity宣布对Copilot进行重大更新，由微调的GPT-3.5提供支持，在性能、速度和成本三方面显著改进。在性能方面，公司考虑对复杂查询的精确响应，在搜索的特定领域显著优于GPT-3.5，基本与GPT-4对等。在速度方面，微调模型能够将延迟减少80%，将平均输出结果的时间由3.15秒缩短至0.65秒。在成本方面，微调模型的输入/输出成本分别为0.012/0.016美元/1K tokens，而GPT-4 Turbo的输入/输出成本分别为0.01/0.03美元/1K tokens。在用户不额外为GPT-4付费的高阶版本下，基于微调GPT-3.5版本的推理性能已和GPT-4相近，根据创始人公开演讲，公司预计基于微调GPT-3.5版本推理性有望在2024年中达到GPT-4水平。


图表25：GPT-3.5微调模型性能大幅超过GPT-3.5，与GPT-4接近


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzicufhFEft5rB18djVMynnjpR5JkhuG3YQRm3ck0qjYSyVg3WYoAJXWw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


图表26：GPT-3.5微调模型将延迟减少80%


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzxMFHaPJgtR8DoY6svoyU9WHFVsUz2myFmdbibuNINJIqzlnCf3U2wRQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


图表27：GPT-3.5微调模型大大降低推理成本


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykz07PNGESuASn2FOnxvoRdGgibaibAKJjBYK0A4dZesAyyY1iaXJXsicBia8Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


**订阅制与API调用为商业模式之基，广告收入未来可期**


**商业模式：收入源于订阅付费和API调用，广告有望成为增长点**


**订阅付费为收入主要来源。** 目前，公司的收入来源为Perplexity Pro订阅付费项目，定价为20美元/月或200美元/年，月费价格与ChatGPT Plus相同。**付费会员主要享有四大权益：**（1）单日使用Copilot的次数多达300+，而免费用户为5次/4小时。（2）更加强大多元的模型选择：付费用户可以选择Copilot底层模型，包括微调的GPT-3.5、GPT-4、Claude-2.1与Perplexity 70B，能够使用更强大的大模型生成更精准的答案。（3）无限制的文件上传，付费用户能够无限制地上传文件，Perplexity可以对文档进行解析进而回答相关问题。（4）API积分，每月可以免费获得5美元的pplx-api额度。Perplexity Pro目前付费用户数量已达到约15,000人，为其商业化打开了良好开端。

**API调用基于使用情况付费。**pplx-api根据输入输出tokens数量计费，不同参数的模型对应不同价格。结合搜索功能的online模型输入tokens免费，但除输出外每千个请求额外收取5美元。7B参数模型为pplx-7b-chat和Mistral-7b，13B参数模型为Llama2-13b，34B参数模型为Codellama-34b，70B参数模型为pplx-70b-chat和Llama2-70b。Online模型中，7B和70B参数模型分别为pplx-7b-online和pplx-70b-onlie。其中，pplx-7b和pplx-70b是在mistral-7b、llama2-70b模型基础上微调增强所得。

**广告有望成为新增付费点。**传统搜索引擎的商业模式为广告分成，公司创始人认为当用户需要Perplexity推荐相关商品时，广告模式仍有可能被嵌入对话式搜索引擎中，公司也将继续探索广告在AI搜索引擎中的可能性。


图表28：Perplexity商业模式


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzTXqf8PKL6owJCnRAg54XbdMaZAibKmqm7Du0qEvarvfCwZcr2RGV1Eg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


图表29：截至12月10日，API调用定价情况


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzhMB4NNITG4OIKVlV8ZichnmBAmYxxOyW2tp0LWicvxZyRQbCdAP15StQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


**潜在方向：自研大模型与内部搜索引擎或为未来探索方向**


**据我们测算，Perplexity调用Bing搜索引擎及GPT-4的单个问题成本约为0.03美元，年成本约为6,000万美元。**Perplexity成本主要来源于两部分，即调用Bing Search API查找相关内容的成本、调用GPT生成答案的成本。由于免费用户也享有每4小时使用5次Copilot的权益，因此在测算GPT API成本时直接使用最新的GPT-4 Turbo成本，即输入0.01美元/1k tokens，输出0.03美元/1k tokens。按照输入问题50个、输出答案为400个英文单词，添加调用Bing Search API的费用，得出单次提问成本为0.03美元。考虑潜在增长，若周度访问量为1200万次，每次访问提问问题个数为3，每年所需成本为5,944万美元。

**使用GPT-3.5微调模型降低成本，自研模型与内部索引或为未来探索方向。**Perplexity官网显示，目前Copilot已经可以基于自研的GPT-3.5 微调模型提供服务，与GPT-4性能基本对等，且能减少4-5倍延迟，输入成本可以控制在0.012美元/1k tokens，输出成本可以控制在0.016美元/tokens。按照同样的计算方法，单次提问成本降至0.02美元，年成本4568万美元。此外，公司创始人也表明，除使用自研模型之外，搜索引擎API调用成本受到Bing和Google的防御性机制而走高，我们认为建立内部搜索引擎也有望使得成本端下降，公司也计划在这两方面持续探索更加健康的发展方式。


图表30：Bing Search API进行防御性提价


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzTA9T5O0N7HHaZLtY5x5sQMpwHmBhLsLPszfGvian3g74icQUKnLuCnnQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：Microsoft官网，中金公司研究部


图表31：调用GPT-4 Turbo及GPT-3.5微调模型的成本测算


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzfaoWZYUg5jgfsNpITbSRMTjs50Fo7ryKlnRFvhzeVc0d3zoEnjibtXQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


注：1）英文词数与tokens转换比例为750words-1000tokens；2）综合未来成长性假设周度访问量为120万次；3）假设单次访问提问次数为3  
资料来源：OpenAI，Microsoft，公司官网，Similar Web，中金公司研究部


**LLM+搜索引擎的模式探讨**


**未来展望：竞争多元化，Perplexity有望通过生态夯实先发优势**


**需求侧，对话式搜索引擎模式或将长期存在。**Perplexity的出现及高热度验证了大模型与传统搜索引擎结合的刚性需求，对比之下LLM的幻觉与时效性、传统搜索引擎的繁琐链接与大量广告均限制了使用效果。虽然目前，Perplexity在短期内无法撼动商业模式完备成熟的搜索引擎市场，但我们认为未来以Perplexity为代表的对话式搜索引擎模式或将长期存在。

**供给侧，随着传统搜索引擎与大模型厂商的入局，我们认为未来格局有望呈现百花齐放态势。**Perplexity的主要竞争对手可以分为两大类别，一类是以谷歌为代表的传统搜索引擎厂商，另一类是以OpenAI为代表的通用智能大模型厂商。

**► 传统搜索引擎厂商：**对搜索技术富有独到见解，在多年发展过程中持续打磨搜索技术，积累大量用户基础，在对话式搜索引擎中具有天然优势。即使在ChatGPT热度高增的同时嵌入New Bing，谷歌搜索的领先优势并未受到冲击。此外，谷歌不断拓展AI边界，发布Gemini等性能同样领先的大模型，Bard也将在2024年由Gemini Ultra提供支持\[5\]，具备AI赋能搜索引擎的能力。短期来看，对话式搜索引擎目前仍处于发展的早期阶段，尚无完善的商业化落地方式，传统搜索引擎厂商此时大力研发可能对其传统业务产生冲击，转型需要依赖内部较大战略变革。长期来看，虽然目前Perplexity有较好的产品性能和用户体验，我们认为谷歌等搜索引擎厂商仍有可能基于前期沉淀实现弯道超车，并凭借自建数据闭环、场景闭环建立优势。

**► OpenAI等大模型破局者：**具备先进的模型能力，引入搜索引擎并进行调整优化即可打造对话式搜索引擎。2023年5月，OpenAI向ChatGPT Plus用户推出网络浏览插件，赋予大模型联网能力，未来也可能将通用智能与搜索引擎相结合，与Perplexity直接竞争。

**Perplexity有望打造知识平台，成为生态入口。**基于对话式搜索引擎，Perplexity支持用户将搜索问题及答案分享至社区，供其他用户学习讨论。2023年9月，公司发布Collections，可以根据项目、主题或其他分类创建收藏夹，整合梳理查询对话并拓展新问题，还可以邀请其他参与者协作管理Collections，创建知识共享平台。随着Collections、pplx-api等业态的逐步成熟，我们认为Perplexity有望建立特定社群，进一步夯实对话式搜索引擎的领先生态优势。


图表32：Perplexity推出Collections


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzXMIbfVKMtnic2pia7FJCQoVFuaE7Kfn0BjfY1L2OTx0OhZHN2Qs3b6Uw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：SkyNet AI公众号，中金公司研究部


**风险探讨：AI时代，产品形态与场景闭环为发展关键**


**商业化风险：对话式搜索引擎仍需进一步探索明晰的商业化路径。**从成本端来看，Perplexity采用的GPT-3.5微调模型与Bing搜索引擎均为外部API，2023年5月微软上调Bing Search API定价，加高产品使用门槛。随着Perplexity用户数量的持续增长，若未来Bing及GPT API费用再次增加，将对公司成本造成不利影响。从收入端来看，目前Perplexity的唯一收入来源为订阅付费，pplx-api和广告都处于早期阶段，盈利路径尚未明晰。而谷歌等搜索引擎均建立了成熟的商业机制，"用户-商家-内容创作者"和广告生态形成业务及场景闭环，支撑搜索引擎持续更新高质量内容以留存用户，谷歌获取大额广告收入。按照Perplexity的技术路线，谷歌搜索引擎的闭环生态难以借鉴，仍需进一步探索。


图表33：谷歌搜索引擎商业模式


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzZ6nlf3ibSRO8libvt5qVXzFTN1viacS4Syc3DntXFWycKj0vQ8xnXLOeA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


资料来源：公司官网，中金公司研究部


**数据闭环风险：对话形式下反馈机制有效性降低，难以打造数据飞轮。**网页端搜索引擎通常具有完备严谨的指标体系，根据用户的浏览和点击行为总结偏好，并反馈至排序和广告竞价系统提升搜索性能。而对话形式下用户通常缺乏主动性点击Like/Dislike进行反馈，且用户自发反馈缺乏公允标准，难以反映生成结果的真实价值，意味着Perplexity也难以根据先发优势和海量用户数据打造数据飞轮，进行模型快速迭代。

**行业竞争加剧风险：AI Agent为AI落地下半场，落地需实现场景闭环，数据量及应用场景丰富的传统互联网巨头具备优势。**为进一步拓宽用户客群、打造产业生态，谷歌已于海量垂类应用厂商建立场景闭环，实现购物、订票、资料检索等多元化需求。虽然Perplexity Copilot具备购买产品、制定旅行计划等功能，但在生活助手或购物助手等应用场景下，场景卡位丰富的互联网巨头更具优势，Perplexity作为独立第三方企创业公司在完成"旅行路线规划"类的后续"订票、订酒店"功能难以短期形成场景闭环，亟待差异化破局之道。

\[1\]指模型生成的内容与现实世界事实或用户输入不一致的现象

\[2\]Lewis, Patrick, et al. "Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks." ArXiv abs/2005.11401 (2020): n. pag.

\[3\]https://raysummit.anyscale.com/agenda/sessions/344

\[4\]Liu, Nelson F., Tianyi Zhang and Percy Liang. "Evaluating Verifiability in Generative Search Engines." ArXiv abs/2304.09848 (2023): n. pag.

\[5\]https://blog.google/products/bard/google-bard-try-gemini-ai/


**Source**


**文章来源**


本文摘自：2023年12月14日已经发布的《人工智能十年展望（十四）：从Perplexity看AI+搜索的破局之道》

于钟海 分析员 SAC 执证编号：S0080518070011 SFC CE Ref：BOP246

魏鹳霏 分析员 SAC 执证编号：S0080523060019 SFC CE Ref：BSX734

王之昊 分析员 SAC 执证编号：S0080522050001 SFC CE Ref：BSS168

游航 分析员 SAC 执证编号：S0080523010001 SFC CE Ref：BTI822


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


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYsibXdwomXdI2BwINjAEGgykzibttZ0QQwG5I7tx07FXWCx620OIa8h5ttkGKVOMPmia1Kdq3bFwCSXBw%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)


[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7166705474098692337)
