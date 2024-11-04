专访 LanceDB 创始人：多模态 AI 需要下一代数据基建
===============================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/Sp7HtRIUxIHj6Paq71Brfw)拾象 海外独角兽


嘉宾：Chang She

访谈：penny，Cage


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMK2jbYib2mliapaLwdBnW2LValzBwZIibg60m2pyAlQ9nA26otkkoiaWhZgg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


AI 的飞速发展为 Data Infra 数据基建带来了前所未有的挑战和机遇。随着 LLM 和多模态AI的兴起，非结构化数据的规模指数级增长，这对数据存储、检索和分析提出了更高要求。就像在云计算时代，Snowflake 和 Databricks 成为了数据乃至整个软件行业最快增长的产品，而到了 AI 时代，我们也相信会诞生下一代的数据产品。

本篇内容是海外独角兽对 LanceDB 联合创始人 CEO Chang She 的专访。LanceDB 是为 AI 多模态数据设计的数据库，目前的客户包括 MidJourney、Character AI 等。他们开创了开源数据格式 Lance，专门解决传统数据格式 Parquet 不适合的大规模非结构化数据。基于 Lance 格式构建的多模态向量数据库 LanceDB 能够以更低的成本、更快的速度索引数十亿向量和 PB 级别的文本、图像和视频数据。让我们通过这次专访听听这位在数据行业相当资深和活跃的创始人对下一代 Data Infra 的洞见。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKbj6naFEuhHgFkmnrGF1Te1AoW4jzexib4RD86s6sXpmyXM3PHaokkjA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


💡目录 💡

01 AI-native data infra

02 About LanceDB   


03 访谈正文

• 多模态下的数据库机会

•Lance

•产品路线图


**01.**  


**AI-native data infra**


AI 的飞速发展为 Data Infra 数据基建带来了前所未有的挑战和机遇。随着 LLM 和多模态AI的兴起，非结构化数据的规模指数级增长，这不仅加剧了数据存储和管理的难度，也对数据的高效检索和分析提出了更高要求。

就像在云计算时代，Snowflake 和 Databricks 成为了数据乃至整个软件行业最快增长的产品，而到了 AI 时代，我们也相信会诞生新的数据产品。

新时代数据产品需要解决的第一个问题是多模态数据规模提高之后带来的 scalability 挑战：


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKu62Rpvol5qEt231WX9aM82RgayFPe8wMqnkRoibtEOBn1MXSkazI7Pw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

Source:LanceDB Data+AI Summit Talk


•非结构化数据在 AI 合成的加持下规模持续上升，Data Infra 需要能够灵活地横向扩展以支持不断增长的需求；

•不同模态的数据具有不同的特征和处理需求。例如文本数据需要全文索引，而图像数据则可能需要特征向量索引，而且为 AI 设计的索引和传统搜索的索引会有所不同；

•AI 应用对数据存储的实时性会提出新要求，实时语音交互和图像检索都会对数据库的读取查询性能提出极高的要求；

第二个问题是数据栈中的工作流还未确定，RAG 作为主流方案还在快速演进的阶段：

• RAG 数据栈涉及数据预处理、向量化、索引、检索和生成等多个环节，每个环节都有多种技术选择：


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKc6s3jibRDJFNJVr7czCXCmZTPdpgs1N3fNhibWahvvkPhibTkxCHiclDVg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

Source: LanceDB Data+AI Summit Talk


• RAG 中的 embedding model, retriever, reranker 等模型都最好用行业数据进行 fine-tune 达到最佳效果，使工作流高度复杂和模块化；

• 标准化和可复现性低，由于前面提到的长链条、高度定制化，这导致 RAG 本身难以端到端产品化

下一代数据产品的使命是要解决这些问题，LanceDB 也是其中的重要一员。


**02.**  


**About LanceDB**


LanceDB 是一个为多模态数据设计的数据库，目前的客户包括 MidJourney、Character AI、Airtable 等。他们开创了独特的开源数据格式 Lance，专门为解决 Parquet 这样传统数据格式面对多模态数据的无力。基于 Lance 格式构建的多模态向量数据库 LanceDB 能够以更低的成本、更快的速度索引数十亿向量和 PB 级别的文本、图像和视频数据。  

LanceDB 的两位联合创始人之一 Chang She 是 Pandas 的作者之一，Pandas 是最受欢迎的Python 数据科学库，被全球1000万数据科学家所使用，每月下载量高达1.7亿次。Pandas 就像是数据科学家的 Excel，是数据科学家处理数据的必备工具。Lei Xu 则是自动驾驶公司 Cruise 的数据基础设施的核心成员，有着丰富的多模态数据基建经验。LanceDB 最近完成了由 CRV 领投的种子轮融资。

在刚刚结束的 Databricks Summit 中，Chang She 提出了 AI 数据库时代的 CAP theorem，即传统数据库面对 AI 任务时的不可能三角：

• 随机读取（random access），可以直接访问任意位置或记录的能力，例如在训练模型时的 data shuffling；

• 大块数据（large blobs），高效地存储和检索大规模数据，例如在训练模型时的 data distribution；

• 快速扫描（fast scans），高效的全表或大范围扫描，例如在训练模型时的 data filtering。

而 LanceDB 的目标是为 AI 应用同时提供以上三种能力。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKk6SZooyua7YrZUtibE4ntlCJVWwQyCZQyxic3N5EOb9eKeKDZDuObLtQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

同样在这次 Summit 上，LanceDB 团队也介绍了与 Databricks 产品耦合的 RAG 工作流，LanceDB 和 Databricks 的合作将主要聚焦在 retrieve 这一步上， LanceDB 将作为 data lake 中重要的补充组件，也有机会在 Databricks 生态中拓展用户。而在下文的访谈中，我们也会和 Chang 聊聊如何从这一模块往外拓展。  


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMK3SX1ic94ksZ7J0zuzYL3iawTIXeNQtEhnZ813clvaYs0xODU4AbkTZxg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

**03.**  


**访谈正文**


**多模态下的数据库机会**   

**海外独角兽：****请先简单介绍下 LanceDB 吧。**

**Chang She：**LanceDB 是为多模态 AI 设计的新一代数据库。在新的 AI 时代，企业需要处理海量的非结构化数据，包括向量嵌入（embedding）、图像和视频等。与之相对应的任务（workload），比如向量搜索、分布式训练、模型推理等，都会和传统的键值对查询不同。因此，传统的数据基础设施已经不能有效管理这些新的数据和 workload 。LanceDB 的核心理念和产品定位就是为这个 AI 时代打造全新的数据基础设施。

LanceDB 与 Databricks 等传统数据湖的区别在于底层数据格式。传统的数据湖大多基于 Parquet 格式或原始图像文件存储，但对于需要处理多模态数据的 AI workload 来说其实并不是理想的解决方案，因为需要维护更多的数据副本，并且还会遇到各种性能瓶颈。所以基于 Parquet 这种方式其实可扩展性比较差、成本很高、使用也更加复杂。也因此，我们正在重新设计一种全新的数据格式和系统来满足 AI，尤其是多模态场景下的数据需求。


💡


Parquet 是一种面向列存储的数据格式，专为大数据场景下的查询和分析而优化设计。与基于行存储的格式相比，Parquet的列式存储特性可以使用更高效的压缩和编码方案，大幅减少I/O，在分析型工作负载上实现更快的性能。

键值对(Key-Value)查询是一种简单而高效的数据检索方式。每条记录都由一个唯一的键(Key)和对应的值(Value)组成。查询时只需提供键，数据库就能快速定位并返回相关联的值，非常适合处理海量数据下的点查询操作。

以上两种方式都并非为非结构化、多模态数据的场景设计，兼容性不好。


如果某个团队的日常工作中存在大量的搜索和检索的需求，或者因为模型训练（包括 LLM、VLM 等在内）要处理规模庞大的数据，这些任务场景就都很适合 LanceDB，因为 LanceDB 在高性能和数据处理规模这两方面都处于行业领先位置。此外，我们也是市面上唯一能同一组数据上运行从检索到模型训练的各种关键 AI workload 的产品，而且它简单易用，和技术生态系统有最广泛的集成。  

总之，不管是搭建 AI 应用，还是训练新的多模态模型，都可以借助 LanceDB 来把项目的可拓展性提升 10 倍，同时成本降低一个数量级，在这个过程中，LanceDB 会帮助开发者实现更高的生产力、更快的迭代速度。

**海外独角兽：** **你一直在数据行业探索，除了创立 LanceDB， 也是数据行业中大家都很熟悉的 Python Pandas 库的核心作者。你对 data Infra 的兴趣来自于哪里？**

**Chang She：**我一直都对数据行业很感兴趣。我最早在对冲基金工作，作为量化分析师要承担很多数据工程的工作，当时我就意识到这个工作过程中没有好的工具可以使用，所以我们都会先写 Java 代码来读取 CSV 文件，再用 VB 脚本来做数据分析和处理。

当时我的一位同事 Wes 也遇到了和我一样的问题，于是他就写了一个闭源库，也就是今天的 Pandas。我用过 Pandas 之后相当喜欢这个项目，于是就把它推广到了整个团队，后来 Pandas 在我们整个公司都很受欢迎。Pandas 开源后也是在金融领域最先流行起来的，因为它对时间序列、统计等的支持特别好。

2012 年前后，随着相关学术研究和 互联网（web-scale）数据激增，数据科学家成为了新兴的热门职位。突然之间，对数据分析的需求猛增了 100 倍，Pandas 也因此获得了更多人的关注、可以说是人气飙升。

与此同时，Wes 和我也开始思考新的问题，比如那些不会写 Python 的数据分析师要怎么办？于是我们创办了 DataPad 做数据分析可视化，DataPad 后来被 Cloudera 收购了。

再之后我进入到机器学习领域、并加入了 Tubi。在机器学习领域，表格数据（tabular data）和非结构化数据之间存在一个相当明显的鸿沟。对于表格数据，有诸如 Python、 Spark 和 Pandas 这样很高质量的工具可以使用，但对于视频和图像这类数据处理工作就不太理想了。

因此， 2022年，我和我们的 co-founder 们决定创办 LanceDB，为非结构化数据打造新的存储层。这就是我从量化分析师到 LanceDB 以来的整个过程。

**海外独角兽：** **你之前的经历中很多是在为结构化表格数据（tabular data）打造工具，但在非结构化数据我们还没有见到很多好的工具。这背后是不是源于结构化数据分析、机器学习、LLM，对数据的需求是三阶段演进的过程？**

**Chang She：**我们可以先回顾一下历史上的重大技术趋势。90 年代，企业开始数字化、大规模使用数据，这让 Oracle 这样的数据库公司作为 infra 层兴起。

进入 2000 年代，互联网时代到来，先前的技术变得不够用了。随着 web-scale 数据的出现，从表格数据到 JSON 数据的转变使 MongoDB 兴起。

后来就进入到了云计算时代，出现了 Snowflake 和云数据仓库。差不多同一时期，机器学习也开始流行，所以不再只是单一的数据仓库，我们需要一种能够存储和连接不同工作负载的 infra，这就包括从简单的运行 SQL 查询，到深度学习训练、模型工作等复杂的数据管道，这也让 Databricks 成为了这个时代重要的 infra 公司。

而眼下，我认为 LLM 代表了一个新时代，尤其是多模态 AI 的出现。LLM 时代的特点是数据类型不同、数据规模远远更大、工作流程也大不相同。

另外还需要强调的是，目前还没有 killer app 出现。因为 AI 领域暂时还没出现类似 LAMP stack 这种标准架构作为基础设施，所以我也看到有很多 data infra 公司正尝试定义 AI 时代的 LAMP stack ，**但如果回顾之前的几次技术浪潮，就会发现每一代技术对应的 killer app 是先出现的，在这之后人们才去构建相应的 infra。**比如，互联网普及之后才有了 LAMP stack 。

对于现在的 AI 同理，我们仍处于这个技术时代的早期，人们还在寻找 AI 时代的 killer app 是什么。所以我认为现在下结论说 AI 的 LAMP stack 会是什么样子会为时过早。


💡


**LAMP stack：** Linux, Apache, MySQL 和 PHP 的缩写，是一组构建网络应用最常用的开源软件，代表互联网时代标准的基础设施。1998 年 LAMP 被首次提出。


**我们可以锚定一些不变量。比如我们都知道模型和数据都是必不可少的，** 如果我们能让数据存储和操作变得高效和可扩展，这件事是不会随时间消失的。而越往中间层，middleware infra 的不确定性就越大。**所以我认为，通过紧贴模型和数据这两个不变量，我们可以构建一些在本质上经得起未来考验的东西。**

**海外独角兽：** **2022 年你创办 LanceDB 时 ChatGPT 还没有推出，当时你看到的行业机会是什么？整个 data stack 中除了 RAG 还有很多方向，为什么最终选择了现在的方向?**

**Chang She：**在 ChatGPT 发布之前，我们就已经看到多模态数据很难管理了。尤其是对于自动驾驶厂商或者其他需要处理大规模 CV 数据的公司来说，他们可能会有数据的很多副本，一份用于训练，一份用于推理，还有一份用于数据发现和探索。

我的联合创始人来自 Cruise，他在 Cruise 参与搭建过一个大规模的机器学习平台。对于 Cruise 的工程师来说，要完成一个迭代周期，他们需要学习四种不同的编程语言、七种不同的系统，并管理大约三份不同的数据副本。而且他们必须"相信"整个 pipeline 没有出错，因此数据管理问题是我们一开始想要解决的问题。

到后来，因为我们是开源的，我们通过社区发现 RAG 和向量检索的需求很多，很多用户发现用 Lance 搭建的系统在 RAG 相关用例中很方便。

到了今年我们更明确的是，RAG 在生产环境中对产出质量的要求是很高的。这意味着除了向量搜索，用户还需要其他检索方法，比如全文搜索、SQL 过滤、借鉴推荐系统中的 reranking 技术，这需要更高的复杂度。此外，通过用户反馈，用户可以对 embedding 模型和 reranking 模型进行微调，从而用少量数据和成本获得更准确的检索结果，而不是预训练一个新的大型 embedding 模型。这一系列实现都比较复杂。

我们的早期用户们发现，要实现一个好用的检索需要用到很多个系统：一个用于全文检索，一个向量数据库，一个用于存储实际数据的系统，一些自定义代码进行 reranking，并且可能还需要数据的其他数据副本用于 fine-tuning，以及自定义工作流等等。

LanceDB 就是想解决这个问题，这些都是人们绝对需要做的事情，但让我们将其从五个系统简化成一个系统，从而降低管理成本。

**也因此，LanceDB 的 Lance 数据格式会是我们的独特优势之一，Lance 格式支持在一张表中存储原始数据、元数据、向量和用于 fine-tune 的用户反馈。**它的自动版本控制确保了可复制性，并提供各种检索方法。用户可以在一个地方运行 SQL 查询、全文搜索、向量搜索以及 reranking 和混合搜索功能。这大大简化了生产所需的复杂度。

**海外独角兽：** **所以当市场还没有讨论 RAG 的时候，你们实际上已经在提供相关需求的解决方案了？**

**Chang She：**是的，我们当时没有做完整的 RAG，但已经在做检索。当时的自动驾驶行业已经发展了十年，容易解决的问题都解决了，剩下的都是长尾问题。而每天有大量数据进来，但可能 target 长尾问题的只有 0.01%，挑战在于怎么把这 0.01% 的 corner case 找出来。于是我们为此增加了许多不同的 retrieval 和 indexing 的能力，而retrival 加上向量 indexing 本质上就是一个向量搜索系统了。

LanceDB 的第一批客户也都是和自动驾驶相关的团队，当时还有一些车厂以及制造飞机的公司都在尝试做自动驾驶。另外还有一些规模比较小的公司，这些公司有大量的图片或 PDF 文件进行信息提取和实体提取的需求。

**海外独角兽：** **今天 LLM 已经完全兴起了，这件事对于你们之前看到的机会带来了哪些变化？**

**Chang She：**越来越多的公司开始对更高质量的搜索能力提出需求。尤其是去年，推荐系统、电子商务和其他机器学习密集型行业的需求就出现了爆发式增长，人们认识到需要 embedding、向量搜索和数据管理，至少是对于文本数据而言。

今年则更多关于多模态。现在多模态已经是一个共识趋势了，并且他们正在想办法输入图像和视频。多模态的发展让数据规模的增长将比传统 AI 快得多。可能在四年前，只有 Google 或者 Meta 这样的公司的数据规模是在 PB 量级，但现在，我们客户中的一个视频领域的初创公司的数据规模就超过了 10PB 。

传统数据 infra 的成本结构、效率和性能都无法应对这种新的规模，对于训练或大量定制模型的公司而言存在很大的痛点，急需一种更有效的解决方案来管理如此大量的数据。

**海外独角兽：** **LLM 时代中最流行的使用场景和 workload 是什么？**

**Chang She：**现在每个行业都在尝试用好 AI 能力，而且它们大多都需要 RAG 或语义搜索能力，这意味着我们的用户和客户群体大大拓宽了。同时 AI-native 公司需要预训练自己的大模型，这与传统工作负载不同，他们现在必须管理比以前更多的数据，甚至比之前自动驾驶的工作负载所处理的数据量还要多。这些使用场景和工作负载也非常适合 LanceDB 的优势。

**海外独角兽：** **多模态对 RAG 带来了哪些影响？**

**Chang She：**这个问题很有意思。现在多模态 RAG 也在成为一种趋势，多模态的模型层和应用层也在发生很大变化。传统方法中每种模态最终都会被映射到语言，但目前有很多研究绕过这种映射，通过创建不同模态之间更加原生的连接来实现更低的延迟和更复杂的用例。所以我认为 RAG 在多模态的语境下也会发生变化。

**但总的来说，就像人有五感一样，AI 也在朝着这个方向发展，在不久的将来，我们将拥有通用的输入和输出能力。对于 RAG 来说，prompt 和检索的上下文也会是多模态的。**在如何指令模型返回文本、音频、视频以及这几种模态的混合方面，会变得更加复杂，这意味着应用层会变得更厚，同时这些数据的管理也将成为一个相当有挑战的问题。

**Lance**


**海外独角兽：** **你在前面提到数据格式 Lance 会是 LanceDB 的重要优势。从历史上看，一种新的数据格式要成为行业标准，需要满足哪些条件？你认为 Lance 要做好这件事会面临哪些挑战？**

**Chang She：**我们是这样看待这个问题的：**任何想成为行业标准的技术，都必须是开源的，且需要能够很好地与生态系统中的其他工具集成。**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMK3snHMQuPFNn2RKef1sEpTpJOiacvCsQgKP8ia3jACh8qZvSMBUvu6hfA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

具体有两种方法：一种是，如果一个公司在生态系统中有足够的影响力和资源，就有机会和能力来自己定义一套标准，并且随着时间的推移，这个标准可能会被广泛接受。

但对于 Lance 来说，目前我们的 use case 其实还没有特别清晰，所以我们采取了另外一种方式，我们想以一种对各类 use case 都非常有价值的方式来做这件事，希望通过为社区提供巨大的价值，让它成为行业应用标准（de facto）。

开源数据格式的用户增长曲线会非常不同，一部分原因是 Apache Arrow 的流行。

Apache Arrow 出现之前，如果有人创建了一种新的数据格式，首先必须与市面上的工具进行一对一的集成，比如 Pandas、Polars、Spark 和 Snowflake。而 Arrow 作为内存格式标准，意味着所有这些系统都已经与 Arrow 实现了集成。


💡


Apache Arrow 是一个跨语言的内存列式数据格式标准，旨在提高大数据系统之间的互操作性和性能。Arrow 提供了标准化的内存布局和计算引擎，使得不同的工具和库能够高效地共享和处理数据,而无需序列化开销。


而 Lance 作为一种非磁盘格式，正是使用 Arrow 的标准类型系统和内存格式，Arrow 是我们的主接口。


💡


非磁盘格式是一种数据存储方式，数据存储在内存或高速缓存等非磁盘介质中，而不是直接存储在磁盘上。这种格式专为需要高性能数据访问和处理的场景而设计，如实时分析和机器学习。与磁盘存储相比，非磁盘格式具有访问速度快、延迟低等优势，但容量受限于内存大小。通常，非磁盘格式与磁盘存储结合使用,以在高性能和大容量之间取得平衡。


因此，对我们用户来说，他们甚至不需要考虑目前正在使用的是什么磁盘格式，就可以很低成本、快速实现性能和可拓展性的提升。比如，如果他们之前是用 Parquet 格式来存储数据，那么只需两行代码就可以转换为 Lance 格式。如果用的是 Polars 或 Spark，也不需要做太多代码更改。

**海外独角兽：** **在今天要让一个新的数据格式成为行业标准，会比之前更容易还是更难？**

**Chang She：**这件事上有不同的观点。有一些在数据行业经验很丰富的人会认为：我们可以通过修改 Parquet v3 这一格式来满足新的用例。

而我的观点是，如果所有东西都将与 Arrow 这一标准集成，是否存在一个单一的数据格式标准就无关紧要了。不同的用例可能会有不同的标准。也许三到五年后，一个数据湖中会部分是 Parquet，部分是 Lance，也许还有部分是像 CSV 这样的其他格式。但这对最终用户来说并不重要，你只需为具体用例选择最优的存储格式。

**海外独角兽：** **和 Parquet 相比，Lance 在快速随机访问上有很强的优势，这是如何实现的？可以通过修改 Parquet 来实现这一点吗？**

**Chang She：**我倾向于这样思考 Lance 的差异化。今天 AI 领域对数据有三个要求。首先，人们仍然需要快速扫描（fast scans）用于分析、查询、过滤等；其实是随机访问（random access），即搜索和检索需要快速随机查找；第三点是需要能够处理多模态数据，并高效处理大块数据（large blobs）。

这里其实存在一个 AI 数据的 CAP theorem，即其他系统或许擅长上面一点或者两点要求，但还没有一个能三者兼顾。Lance 的目标就是解决这三个问题。现阶段除了 Lance 之外，还没有其他系统能够同时很好地满足这三个方面需求。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMK7oK6lyR4aNN5vKpZVre26GFibISZUhb4EOACulFJTwOHs8GzItuB0iaA%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)

我们一开始也尝试在 Parquet 上面来构建，也考虑过修改 Parquet，但考虑到 Arrow 和生态系统的变化，从头设计一个新的数据格式可能更有价值。

如果你现在依然采用 Parquet，并在旁边想添加偏移量或索引（这是很多人的做法），索引可以快速定位到正确的行。但是由于 Parquet 固有的局限性，获取特定一行记录会很慢，因为你需要读取整个块或整个行组才能获得所需的一行数据。这是 Parquet 难以克服的根本问题。

快速随机访问之所以重要，是因为只有实现这一点，index 才能发挥真正价值。Lance 不仅提供了一种数据格式，还内置了索引格式，从而为各种用例（不仅限于向量搜索）提供更优的查询性能。

**海外独角兽：** **在 RAG 上， Lance 数据格式有什么优势？和 Parquet 比有什么不同？**

**Chang She：**在 LanceDB 的一个 row 中，我们可以同时存储图像、文本、音频、视频，以及与原始数据不同部分对应的任意数量的向量，在此基础上也能实现任意模态跨数据检索，并使用任意模态的方法处理检索到的数据，这是 Parquet 无法高效实现的。大多数向量数据库也不允许每行超过一个向量，因为它们是为提供 API 服务而设计的，而不是作为表格。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKKm7lRHtoKtsRBZnrzyWfPUdIFicZ9vlqZia1ibpv43XI8KnZrOPRSZUMA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

**海外独角兽：** **传统数据库的数据迁移成本很高。向量数据库的数据迁移成本是什么样的？举个例子，因为 embedding model 的切换会让之前存储的 embedding 数据失效，所以如果我们 embed 了workspace 的 Notion 页面并频繁更新它，我们就需要反复重新 embed 更新数据。新一代向量数据库如何面对这个差异？**   

**Chang She：** 如果只存储向量，那就没有任何 gravity，因为表只是一个索引，当你重新 embed 并创建新索引时，旧索引就会被丢弃。**数据迁移成本来自于源数据，源数据并不会被改变，确实在实践中可以改变 embedding 模型，但存储待 embed 的原始数据（文本、图像等）的那个系统是难以迁移的。**

关于 Lance，我们没有讨论到的一个有趣方面是它对模式演化（schema evolution）的支持。在创建新的 embedding 时，你不需要复制源数据。而有了 Lance，你可以在不复制源数据的情况下，删除旧的 embedding 列并添加一个新的，这在 Parquet 中是做不到的。此外，Lance 支持时间回溯，让你可以回溯到之前的 embedding 状态，这也有助于调试。

Lance 有一个元数据（metadata）层，不同的列和模式部分可以存在于不同的数据文件中。然后不同的版本会写出指示该版本相关文件、模式及 blob 的元数据。通过这种方式，就可以在不重写数据的情况下进行模式演化。

**海外独角兽：** **现在行业中也有很多关于混合搜索的讨论，即把关键词搜索和语义向量搜索结合。长期来看，向量搜索会完全取代关键词搜索吗？还是二者持续共存？**

**Chang She：**我认为它们更可能长期共存。有些数据集和用例中，关键词搜索效果更好，而另一些则更适合向量搜索。有效结合这两者也是一个有趣的领域，比如说见证式搜索（testimonial search）等。我认为在未来，各种应用都将拥有语义搜索能力，而且更可能是这两种搜索方式的结合。

即使在 RAG 之外，AI 也正在引发巨大的搜索革命。上一代 Web 应用都有响应关键词搜索的搜索框，人们不得不接受它的搜索质量，因为那是我们当时所能获得的最佳选择。现在，有了更好的搜索能力和 RAG，人们看到那种陈旧的关键词搜索框将会觉得效果很糟糕。所以我认为很快就会进入一个新时代，如果你的应用不支持语义搜索功能，用户体验就会变得糟糕。因为自然语言搜索、对话式交互模式由于 ChatGPT 的兴起变得更加核心，搜索本身也已成为用户体验的更核心部分。这种转变可能没有受到太多关注，因为听起来并不那么 sexy，但它对行业来说也是有很大影响的。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKf18ibXefstefdJLcJFibiagwZyo2Jsic82PEhRJy7ZltM5OoswtuFyMaLw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


**海外独角兽：** **如果没有 Lance 这个数据格式，像 Chroma 和 Weaviate 这样的其他向量数据库在处理这个问题上是不是难度会大很多？**   

**Chang She：**它们并没有表模式（schema）的概念。在它们看来，一切更像是一个集合，集合有一个 record ID，可以有多个向量或者只有一个向量，外加元数据形成类似 JSON 的数据块。所以不存在所谓的模式演化和版本控制，在这种情况下，你只需要显式地进行数据快照，但这时你必须复制数据。

**海外独角兽：** **我们交流的企业客户提到，从 AWS S3 bucket 取数之后，企业自己没有使用 LanceDB 类的产品，而是通过 ETL 也可以将其用于训练。在这个场景如果使用 LanceDB 有什么优势？**

**Chang She：**对于分布式训练，你需要进行过滤、分发和随机化等预处理。现有格式在随机化和数据混洗（shuffling）方面效果非常糟糕。此外，你还需要一个大规模的引擎来处理过滤和其他任务。因此，直接从对象存储流式传输数据会使 ETL 变得复杂，并可能严重影响 GPU 利用率。由于 GPU 是最宝贵的资源，最大化它们的效率至关重要。这就是 LanceDB 的独特价值所在，它可以确保高效的数据处理，让 GPU 得到充分利用，并在分布式训练中表现非常出色。

**海外独角兽：** **在你们的产品路线图上，你们提到将与 Spark 和 Ray 计算引擎兼容。你对这些计算引擎是怎么看的，未来计划如何？LanceDB 和 Databricks 、 Snowflake 之间的关系是什么样的？**

**Chang She：**我们希望为多模态数据培养一个蓬勃的开源生态系统。与任意计算引擎实现好的集成对我们来说很重要。我们已经发布了对 Ray 的集成，它现在已经正式成为 Ray 的一部分。我们正在推进与 Spark 的集成，与 Trino/Presto 的集成也在同步进行。这有点回到了数据湖的概念，即客户将数据以 Lance 格式存储数据在对象存储中，并且应该能够使用任何处理系统对其进行处理，以满足不同目的。

我们会是他们的合作伙伴。例如，我们已经与 Spark 集成，并通过 Apache Arrow，使 Snowflake 能够读写 Lance 数据。可以设想，如果 Snowflake 加入一个 pushdown，他们就可以允许客户连接到 LanceDB，并使用 Snowflake SQL 进行向量搜索，而 LanceDB 实际上在处理这些底层操作。

**海外独角兽：** **现在针对向量数据库的竞争非常激烈，你认为处理文本数据与其他模态数据之间的区别是什么？**

**Chang She：**文本确实与其他模态不太一样，但需要注意的是，每个模态都有自己的特殊需求，文本与图像间的区别可能并不比图像与视频间的差异大很多。对于文本来说，问题不一定在于原始数据本身更难操作，而是在于数据的规模，一家专注文本的模型公司可能需要爬取整个互联网并摄取能获得的一切信息，全网的视频数据规模则要大很多。规模问题也是现有数据 infra 面临的一个大挑战。

**海外独角兽：** **现在很多公司都面向文本数据做向量数据库，你们会不会想占住多模态数据处理的心智？LanceDB 的技术优势怎么能够体现在多模态的处理上？**

**Chang She：**是，也不是。因为多模态数据的规模更大，所以优势更加明显。所以从这个意义上说，是的我们的确希望抓住多模态数据处理这个定位。

但如果你看现在的向量数据库，它们也无法处理大规模的文本数据，因为它们无法有效存储长文本。大多数向量数据库是专门为语义搜索而设计的，由向量 ID、元数据的 blob 等构成，这个 blob 适用于 MongoDB 式的存储和元数据过滤，而不是用于长文本的有效存储、检索和管理。对于短文本比如单个句子，差别不大，但如果要检索的是整个文档的长度，也会很快遇到规模的问题。

**海外独角兽：** **我们注意到 Elasticsearch 和 PostgreSQL 这些公司也推出了向量搜索相关的产品，作为一个 start-up，在下一代数据基础设施中，哪种技术会为 LanceDB 创造更多竞争壁垒？**

**Chang She：**从长远来看，向量搜索更可能成为一个更独立、完整的产品中的一部分，而不只是增量式地加入现有系统作为功能扩展。

对于那些正在添加向量搜索功能的现有数据库，由于架构已经确定，它们只是添加了一种新的索引能力。但这种索引与 B-tree 或 bitmap 索引有很大不同。这对于像 PostgreSQL 这样的产品来说，在工作负载特征等方面都会产生很大的影响。

我们听到很多用户表示，他们最初使用 PostgreSQL，但一旦数据超过了1000万或2000万行，延迟就会变得非常糟糕。如果他们稍微修改 SQL 查询的构建方式，查询就不再使用索引进行预过滤。所以添加这种新功能会带来很多问题，对于许多其他现有产品也是如此。

**我认为，一个更完整产品的未来发展路径将是为 AI 和管理 AI 数据而设计的，而不仅仅是增量式地添加向量索引。**这并不是说 PostgreSQL 的向量索引不好。在很多场景下，如果你的数据已经在 PostgreSQL 里面了，并且数据规模并不大的话最高优先级只是尽快推出产品，那么它就是一个不错的选择。我非常欣赏 PostgreSQL，但在达到一定规模后，你还是需要不同的解决方案。

**海外独角兽：** **所以 LanceDB 既有使用多模态数据的客户，也有只使用文本模态的客户？**

**Chang She：**是的，我们目前正在与各个模态领域的领先公司合作。例如，我们正在与 MidJourney 合作处理图像，与 Character AI 合作处理文本。我们也正在与一家暂时不能公开的大型视频公司合作。在所有这些模态中，共同的特点是庞大的数据规模、复杂的检索与数据管理需求，以及需要与分布式训练无缝集成。

**海外独角兽：** **这会回到我们之前提到的 Lance 数据格式的优势吗？它已经在为多模态 RAG 或未来的技术栈做准备了吗？以及与 Parquet 相比，在该用例上有何不同？**

**Chang She：**在 LanceDB 的一个 row 中，你可以存储图像、文本、音频、视频，以及与原始数据不同部分对应的任意数量的向量，这允许你能够使用任意模态跨数据检索，并使用任意模态的方法处理检索到的数据，这是 Parquet 无法有效实现的。大多数向量数据库也不允许每行超过一个向量，因为它们是为提供 API 服务而设计的，而不是作为表格。

**海外独角兽：** **LanceDB 的客户是如何使用产品的？可以分享一些有趣的用例吗？**

**Chang She：**我们在开源社区里看到很多用户用 LanceDB 来处理各种任务的 RAG，比如，有人将 LanceDB 用于开源的代码生成工具，也有用户用 Lance 开实现生成 SQL 语句、自动化数据分析、常规 chatbot 以及 chat with doc。

如果将我们所提供的不同语言包项目计算在内，我们目前每月的收入已经超过了 100 万美元。

我们也和咨询公司交流过，他们会把 LanceDB 用在财务报告分析上，通过提取出关键信息和数据，来让系统自动化回答例如"为什么这家上市公司的营业利润会上升"或"运营支出为什么突然增加"等等问题。

通常情况下，他们会发现由于能够在向量与被提取的原始数据旁边存储更多数据，因此会更容易对原始数据进行扩展以用于提取，并将其提供给模型进行总结，从而获得更准确、更丰富的 RAG 结果。我们还可以简化混合搜索和全文搜索，从而为那些需求超出基本向量搜索的用户提供更高质量的检索。

此外，大型企业也使用 LanceDB 来存储和管理他们所有的训练数据，用于分布式模型训练，比如在自动驾驶行业中进行数据挖掘、场景提取、模型训练。现在多模态 AI 的文本、图像、视频模型都使用相同的 pipeline 来做模型训练中的数据处理。

**海外独角兽：** **其实很多行业存在一个普遍性的需求，即如何从未数字化的非结构化数据中提取数据，比如 PDF 文件、收据等等，但传统的 OCR 等效果并不理想，多模态会对这个场景带来颠覆性变化吗？这件事对于 LanceDB 是什么样的机会？**

**Chang She：** LanceDB 是这些应用场景下的基础设施。在我看来，围绕不同垂直领域和高价值数据源的通用数据进行数据提取和分析会出现很多解决方案，我不太认为某一家公司可以同时处理法律、医疗保健和政府合同等不同领域的需求，最是由不同的公司来做。

我们的目标是为开发这些应用的公司提供基础设施，创建易于使用的工具和可组合的构建块模块。与其让这些公司编写复杂的管道来完成所有这些工作，不如只需编写一个 SQL 查询，就能从 PDF 中提取并使用信息，运行该查询即可在它们的计算集群中自动分配作业。这是我们希望在基础设施层面实现的，就是要为构建此类工具的公司提供超级简单的体验。

**海外独角兽：** **LLM 时代的数据栈中，包括数据存储、模型训练、推理部署等，以及离线\&在线用例中，LanceDB 能在哪个环节捕获到最大的价值？**

**Chang She：**我不认为这些是彼此割裂的部分。有效存储大规模多模态数据是我们的核心，但存储本身没有价值。它必须针对特定用例类型进行优化，比如说从分布式训练的用途而言，存储的优化非常重要。对于那些大规模且复杂的需求，我们通常是唯一的解决方案。存储对于部署也是同样有价值的。

关于离线和在线用例，其他数据格式和过去的数据基础设施通常只适用于其中一种，但 LanceDB 是唯一能在两方面都表现出色的，我认为它对训练和检索是同等重要的。当然，在检索方面也有其他选择，但在这两个领域我们都有非常独特的优势，特别是针对处理多模态数据的公司。

**产品路线图**

**海外独角兽：** **你计划如何进行市场推广和商业化运作？是从小型企业、中型企业和开发者开始，然后再瞄准大型企业客户，还是已经在专注于大客户了？**

**Chang She：**我们的开源社区已经拥有相当大的规模，一些重要的科技公司和领先的生成式 AI 公司也都在与我们合作，所以这是一种面向开发者社区和大客户的双峰策略。最终，更多大型的的非技术企业可能会在采用多模态 AI 并将其进入生产阶段时，可能会稍晚一些加入我们的客户群体，但到那时我们将已经为他们做好充分准备。

**海外独角兽：** **LanceDB 对于开源项目的商业化有什么想法？**

**Chang She：**LanceDB 的商业化不会是对数据格式本身进行商业化，而是关于构建数据管理层、工作流层和向量数据库层。这是针对真正拥有大规模数据的大型企业，无论是在推理服务（serving）还是在模型构建中。我们的企业产品旨在提高生产力，减少维护负担，并实现扩展，而无需团队在开源解决方案之上进行大量管理和构建工作。

**海外独角兽：** **你一直在强调 LanceDB 是唯一一个能够完全满足客户需求的解决方案，为什么只有 LanceDB 能做到这一点？**

**Chang She：**要创建一个真正适合 AI 的数据库系统，需要对数据库和机器学习有深入的专业知识。我们团队的优势是在这个交叉领域积累了大量经验。我们处理的数据是多模态的，我们在处理非结构化数据和结构化数据上都经验丰富；查询和 workload 也是多模态的，包括 OLAP、检索和训练；上下文也可以是多模态的，涵盖离线数据集和在线服务用例。

我们团队在重要开源数据和机器学习项目中的经验是独一无二的。我们是 Pandas、 HDFS、Apache Arrow、Delta 和 Polars 等重要项目的核心贡献者。这些过往经历让我们在数据库和机器学习的交叉点上站在独特的位置上。

**海外独角兽：** **你认为未来 1-3 年中，Lance 的发展将会经历哪些哪些重要里程碑?**

**Chang She：**我们的目标是成为处理多模态数据的行业标准，成为各种任务的最佳选择。在未来一到三年内，我们将看到建立在 LanceDB 之上的更完整的多模态 AI 数据湖产品。这将为整个数据处理 pipeline 提供更多的价值。企业的心智将会是：我想搭建AI应用，我有一些数据，那么我可以使用 LanceDB 来存储这些数据。只需一点工作，他们就可以使用我们的工具完成生产级 AI pipeline。

如今，正在构建 AI 的公司雇佣专家，经历大量的试错，才能拥有在生产中真正良好运行的系统。我们未来一到三年的目标是，让客户无需雇佣一支 OpenAI 级别的团队，就能在企业内运行一个完整而精密的 AI 应用栈。我认为 AI 的民主化不仅仅是覆盖到更多公司，还包括减少公司所需的努力。我预测 AI 可以在企业内的各个领域提供价值。目前，大多数团队雇佣一大批专家，只专注于一个应用。我们希望达到这样一个状态：AI 应用非常易于管理和开发，一个数据基础设施可以支持企业内的多种不同应用，只需很少的维护和运营工作。

**海外独角兽：** **我们发现基础模型公司在微调或训练模型时，常常缺乏使用、整理和准备数据的知识。如果数据存储在 LanceDB 中，如何为模型微调 选择和准备数据？**

**Chang She：**这个问题很有意思。6 月底我们会和 Character AI 将就这一主题进行联合技术讲座。我们将讨论如何在 LanceDB 中处理数万亿的 token，以及后续工作，比如如何考虑过滤。我喜欢用雕刻来类比，LanceDB 中的数据就像是一团原始材料，Character AI 团队将讨论如何从中选择合适的数据，把它雕刻成一个鼻子，也就是得到创造出最优模型的成品。这是一个非常吸引人的话题，我们将就此进行讨论。

**海外独角兽：** **模型越来越多由它们所使用的数据所定义，和数据越来越相关。这是否意味着"雕刻"的过程仍然需要一些专业的 know-how？LanceDB 可能提供的是一个很方便的工具，类似于雕刻用的刀，而这可能是你们的下一步，现在还没有做这个产品，对吗？**

**Chang She：**是的，提供更高层次的工具还不是当前产品的一部分。但未来模型会 commoditize，对于采用机器学习的企业来说，差异化的因素是他们如何融入自己的专有数据。虽然开源模型还没有完全跟上，但它们现在已经相当不错而且进步很快，所以我认为我们很快就会看到模型的 commoditize，然后我们回到一个 data-centric 的世界。企业如何用自己的数据进行微调或预训练，如何用自己的专有数据定制化应用，这些问题就会变得更加重要。

**海外独角兽：****从接下来团队发展的角度，你们希望什么样的人加入？**

**Chang She：**我们团队正在寻找各个领域的专家，尤其是那些以前曾在数据库领域工作或构建过数据库的人。我们团队远程工作，正在打造真正全新事物，希望找到高度自驱、好奇，对新挑战感到兴奋的人才。


如果你有兴趣加入 LanceDB，请点击**阅读原文**查看详情。

排版：Doro


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKOCvFHfPkOypl8Ctw4iaa4BAXKXveP1ib3Z3nibYJkGd12oHngK879GCJA%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)


延伸阅读


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKuEn0uicUVtnrUqIjOXBCbqsS49v9v7yY4bQmv4djrshflsAvicny1sOQ%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247508115&idx=1&sn=3a897e184295128abbe124f8db6524b4&chksm=ce9b1f0df9ec961b90749b66452bb56cc9ac6fbf328b9149a377698299fa27e985a83e0dfab5&scene=21#wechat_redirect)


Kore.ai：LLM能否为AI客服带来新一轮洗牌与机遇


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKostIqvRZrGOLzIDjI88M2MZdQy4YalTJiao24Oc5iafLEBuG97A2Wllg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKuOGWmjoO6IIG4GN4hgib5IgDN5HYicXMeVwcpz1ibwgrjBeky75paibMrw%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247508064&idx=1&sn=1f60f9c685f92ca914c2d4a128f83880&chksm=ce9b1ffef9ec96e8f15c7f7ea91ecea5ae6509dcdc32c804b41f1ad167471c80f51771f7ef83&scene=21#wechat_redirect)


为什么 AGI 应用还没有大爆发？


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKostIqvRZrGOLzIDjI88M2MZdQy4YalTJiao24Oc5iafLEBuG97A2Wllg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKxo5lwMIqQoOgbOibVBtVqM2f05fHZw5c8L6nL4icqrrzG4eBHmfG4tgA%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247507950&idx=1&sn=64c3d23960ec8e4cf91dccdece8aa4e1&chksm=ce9b6070f9ece96648ed9da6b2d4953fe2b8897629285b688253fa2e4a72473a7747d91baa74&scene=21#wechat_redirect)


互联：让数据中心成为新一代计算单元


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKostIqvRZrGOLzIDjI88M2MZdQy4YalTJiao24Oc5iafLEBuG97A2Wllg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKIzPMVVXs7TLYv0pSjQnoU0PtMUHwUD7RzsMZS428k01aagpia8J04MA%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247507749&idx=1&sn=1403008340bbe16dff1b9fc2d5ae6eae&chksm=ce9b60bbf9ece9ad6b7028fd2aa90e43dba20a6a92f9202cdd88b806dd9a18f3e0e17ce7e8e1&scene=21#wechat_redirect)


拾象AGIX指数发布：AI 时代的纳斯达克100


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKostIqvRZrGOLzIDjI88M2MZdQy4YalTJiao24Oc5iafLEBuG97A2Wllg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKTsTDalqoSLOwhAqqUreyZG4KgTop7z4CI1sm7gDwqTXL7ekdA8DbwQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247507542&idx=1&sn=9f8e8d83d2571b209f11a2d9e11bc236&chksm=ce9b61c8f9ece8dee01b9c8f59a9528934d68a9dc02a199ae5647c4dc5be4ad0bf980093b6c3&scene=21#wechat_redirect)


OpenAI联创：RLHF是超级智能的秘密武器


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgyKFeMXsyCCXbooqmYrGUMKostIqvRZrGOLzIDjI88M2MZdQy4YalTJiao24Oc5iafLEBuG97A2Wllg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7210902833669867370)
