中金 \| AI浪潮之巅系列：谷歌PaLM模型，迈向AGI愿景又一阶
==================================

[mp.weixin.qq.com](http://mp.weixin.qq.com/s?__biz=MzI3MDMzMjg0MA==&mid=2247637397&idx=4&sn=e60d48a1f91a1d2f7aacc6f2ffaf37d5&chksm=eade3f52dda9b6440daa5d30a76bed1236536eaccbb971c147d9ee9fc8ee921c2ad2a9bc15ee&mpshare=1&scene=1&srcid=0515hPnyiCkyJGEdsYgsltQG&sharer_sharetime=1684153356550&sharer_shareid=c58007142b3c8dd4da3163f5c61d6b7b#rd)陈昊 孔杨 彭虎 中金点睛

![图片](https://image.cubox.pro/article/2021081608551348670/42624.jpg?imageMogr2/quality/90/ignore-error/1)


**中金研究**


2023年5月，谷歌召开I/O大会推出新一代语言模型PaLM 2，其多语言、理解推理、代码生成等能力较初代PaLM又有了提升。谷歌宣称将PaLM 2大模型能力接入旗下25款应用中，以Bard、Workspace等为窗口触达个人与企业，赋能办公、医疗、网安等领域。我们认为，PaLM系列大模型彰显谷歌追求通用人工智能的愿景，背后有着算法、算力、系统架构等方面深厚的技术积淀。**本文梳理了谷歌在大模型领域的算法积累以及PaLM系列模型背后的算力支撑。谷歌作为AI的引领者，其新应用有望推动AI加速落地。建议投资者关注5月谷歌I/O大会给行业带来的潜在催化。**


**Abstract**


**摘要**


**谷歌是大模型的奠基者、通用人工智能的探索者。** 2017年Google提出的Transformer神经网络架构在自然语言处理领域有着优秀的表现，随后迅速成为各类预训练大模型的基础架构。2017年以来，谷歌相继推出BERT、T5、Switch Transformer、PaLM-E等大模型，参数规模从1亿个拉升至1.6万亿个。从BERT到PaLM-E，我们不仅看到了模型参数规模的扩大，也看到了模型通用能力的增强（T5在探索将所有的任务都转化归一；Switch Transformer在探索由一个模型执行不同任务；PaLM-E具备视觉语言多模态能力，能够沟通物理现实和虚拟模型两个世界）。**我们认为，这些大模型成果都以一种较为清晰的脉络，勾勒出谷歌想要实现通用人工智能的愿景。**

**应用落地是AI价值体现的关键，而推动AI落地离不开算力的支撑。**PaLM-E综合了ViT和PaLM两个大模型的能力。利用机器视觉和语言理解，PaLM-E能够驱动机器人执行复杂任务。我们认为PaLM-E将大模型能力由"决策层"延伸至"执行层"，赋予了AI大模型应用落地的更大可能。我们认为大模型能力仍需算力基础设施的支撑。以PaLM为例，其训练动用了2个Cloud TPU v4 Pods和6144块TPU，采用数据并行和模型并行相结合的方式提升训练效率，最终形成参数规模高达5400亿个、硬件使用效率达57.8%的大语言模型。此外，谷歌还搭建了Pathways架构，通过资源管理器合理调度数据与算力资源，使得整体训练系统能在更大程度上更充分地利用硬件资源。


**风险**


AI应用发展不及预期，AI算力需求不及预期。


**Text**


**正文**


**探索通用人工智能，谷歌一直在路上**


**Transformer一生万物，谷歌引领大模型规模竞赛**


**谷歌是大模型的奠基者，其提出的Transformer成为此后大模型的基础架构。**2017年Google发布《Attention is All You Need》，在人工智能史上具有里程碑意义。论文中提出的Transformer神经网络利用self-attention自注意力机制实现并行处理，使训练时间相较RNN大幅降低。随后谷歌BERT（2018年）、OpenAI GPT（2018年）、百度ERNIE（2019年）等基于Transformer的预训练语言模型相继提出，Transformer作为基础架构迅速在自然语言处理领域占据主导地位。


图表1：Transformer模型架构


![图片](https://image.cubox.pro/article/2023051610235879980/27595.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Vaswani A, Shazeer N, Parmar N, et al. Attention is all you need\[J\]. Advances in neural information processing systems, 2017, 30.，中金公司研究部


图表2：多头注意力机制直观图


![图片](https://image.cubox.pro/article/2023051610235894983/28766.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Jay Alammar，中金公司研究部


**谷歌和OpenAI引领大模型"规模竞赛"。**大模型是基于大量无标注语料信息进行预训练而形成的模型。直观上，语料规模越大，其蕴含的信息越丰富，模型所形成的参数越大，泛化能力也相应增强。为了获得效果更好的大模型，人工智能模型的语料规模越来越大，参数数量也呈指数级上升。Transformer（2017年）本身参数规模在1亿个，此后谷歌BERT（2018年，3.4亿）、OpenAI GPT-2（2019年，15亿）、谷歌T5（2019年，110亿）、OpenAI GPT-3（2020年，1750亿）、谷歌Switch Transformer（2021年，1.6万亿），参数规模的数量级不断刷新。我们看到，谷歌和OpenAI两者彼此超越，共同拉动大模型进入万亿时代。


图表3：国内外大模型参数量对比


![图片](https://image.cubox.pro/article/2023051610235865816/54440.jpg?imageMogr2/quality/90/ignore-error/1)


注：数据截至2023年3月；  
资料来源：北京智源人工智能研究院，中金公司研究部


**► BERT。**BERT是谷歌2018年提出的预训练语言模型，该模型基于Transformer编码器部分，采用自编码的方式进行预训练。简单来说，输入语料后掩盖部分字词，以类似于完形填空的方式训练语言模型的理解能力（与基于解码器部分的GPT有本质上的路线差异）。BERT学习了16GB的语料，形成3.4亿个参数（Large版本），在11项NLP基准测试中取得最佳结果（Devlin等，2018\[1\]）。

**► T5（Text-to-Text Transfer Transformer）。**T5模型旨在构建一个统一框架，将所有NLP任务都转化为"文本到文本"任务，再用同样的模型和训练过程来完成所有任务。T5完整地采用了Transformer的encoder-decoder架构（不同于BERT和GPT仅采用一部分）。T5语料规模增长到750GB，参数规模扩大到110亿个，在17个NLP任务中取得最佳成绩（Roberts等，2019\[2\]）。

**► Switch Transformer。**区别于此前的大模型，2021年提出的Switch Transformer最主要的特征之一在于模型稀疏。所谓"稀疏"，就在于接收到输入信号后，仅有部分的神经元会被激活；而并非稠密模型下，所有参数都会参与推理。Switch Transformer以MoE（Mixture of experts，混合专家系统）为技术基础，1.6万亿参数中内含了众多领域的知识；执行下游任务时会根据相关领域仅激活部分参数，使其尽管参数规模扩大至万亿水平，但算力需求并未同步膨胀。

**回顾谷歌在大模型方面的成果，我们认为谷歌想要实现通用人工智能的愿景跃然纸上。**AGI（Artificial general intelligence，通用人工智能）是人们对人工智能的终局畅想，彼时人工智能将拥有接近于人类水平的智能，不仅能够完成某一特定领域、单一模态的任务，更具备灵活解决更广泛的、更复杂问题的能力。从BERT到T5、Switch Transformer，我们不仅看到了模型参数规模的扩大，也看到了模型通用能力的增强（T5在探索将所有的任务都转化归一，Switch Transformer在探索由一个模型执行不同任务）。我们认为，这些大模型成果都以一种较为清晰的脉络，勾勒出谷歌通用人工智能的愿景。


图表4：Transformer、BERT、T5、Switch Transformer之间的对比介绍


![图片](https://image.cubox.pro/article/2023051610235813695/74615.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：ORKG，中金公司研究部


**PaLM系列大模型：谷歌向AGI愿景迈上的又一阶**


**PaLM：语言理解、逻辑推理、代码生成等能力进一步增强**

**2022年谷歌探索新的技术路线，发布仅基于Transformer解码器部分的大模型PaLM。**PaLM（Pathways language model）是首个由谷歌自研Pathways系统架构训练而成的预训练大模型，是仅基于Transformer解码器部分开发的一个稠密模型。其训练动用了2个Cloud TPU v4 Pods和6144块TPU，采用数据并行和模型并行相结合的方式提升训练效率，最终形成参数规模高达5400亿个、硬件使用效率达57.8%的大语言模型。


图表5：PaLM模型在两个TPU v4 Pod上进行训练


![图片](https://image.cubox.pro/article/2023051610235851921/36727.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Chowdhery A, Narang S, Devlin J, et al. Palm: Scaling language modeling with pathways\[J\]. 2022.，中金公司研究部


**在语言理解、逻辑推理以及代码生成等许多难度较大的任务上，PaLM模型都有着不俗的表现（Google Research，2022\[3\]）------**

**► 语言理解：**在29项常用的英文NLP任务中，PaLM-540B在自然语言推理、常识推理、上下文理解、问题解答等28项任务上超过此前性能最优的模型。此外，PaLM的优秀性能并非仅局限于英文语境下，尽管训练语料中非英语料仅占22%的比重，但是相比基于更多非英语料训练而成的大模型，其表现也丝毫不显逊色。


图表6：PaLM在28个英文NLP任务中获取SOTA


![图片](https://image.cubox.pro/article/2023051610235830748/69911.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：谷歌官网，中金公司研究部


图表7：PaLM非英文NLP任务表现并不逊色


![图片](https://image.cubox.pro/article/2023051610235855317/52083.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Chowdhery A, Narang S, Devlin J, et al. Palm: Scaling language modeling with pathways\[J\]. 2022.，中金公司研究部


**► 逻辑推理：** 在《[AI浪潮之巅系列：ChatGPT之后，大小模型如何推演](http://mp.weixin.qq.com/s?__biz=MzI3MDMzMjg0MA==&mid=2247627687&idx=3&sn=464b6a7c784f05875cb7c92f6e8583bb&chksm=eade1560dda99c76e6dcc755b300e48bc1e90a8ab5b87c16b6b9a334b925ffd7640fcc5f8245&scene=21#wechat_redirect)》中我们提到过，有研究认为，当模型参数规模上升到一定程度后会形成突现能力。例如利用思维链提示，PaLM能够更好地处理数理逻辑与常识推理相结合的复杂任务。


图表8：结合思维链提示，PaLM显现更优的逻辑推理能力


![图片](https://image.cubox.pro/article/2023051610235873884/64239.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Chowdhery A, Narang S, Devlin J, et al. Palm: Scaling language modeling with pathways\[J\]. 2022.，中金公司研究部


**► 代码生成。**代码生成任务一般包括人类语言向编程语言转换（text to code）、一种编程语言向另一种编程语言转换以及debug（code to code）。谷歌研究发现尽管PaLM-540B训练语料中仅有5%的内容的代码数据，但是它的测试表现依然媲美代码训练数据量是其50余倍的Codex-12B。


图表9：PaLM代码生成能力示例


![图片](https://image.cubox.pro/article/2023051610235847206/32993.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Chowdhery A, Narang S, Devlin J, et al. Palm: Scaling language modeling with pathways\[J\]. 2022.，中金公司研究部


**PaLM 2：较初代PaLM，性能得到进一步提升**

**2023年5月，谷歌于I/O大会上正式发布PaLM 2。**作为谷歌下一代语言大模型，谷歌在三方面实现大模型能力的升级，进一步优化计算效率、丰富训练语料、完善模型架构，使得性能相较初代PaLM模型呈现二次提升（谷歌，2023年\[4\]）。

**► 优化计算效率。**其基本思想在于精心筛选高质量数据，再将模型规模和训练语料规模成比例地缩放。利用这种方法，PaLM 2的参数规模较初代PaLM小得多（谷歌未明确其规模大小），但其整体计算效率得到提高。我们认为有望降低服务成本，为赋能更多下游应用场景提供可能。

**► 丰富训练语料。**初代PaLM的预训练数据集以英语文本为主。PaLM 2在训练语料中加入更多语言文本，包括数百种人类语言、编程语言、数学方程、科学论文等等。更优质且丰富的语料，增强了PaLM 2在多语言能力、理解推理、代码生成等方面的能力。

**► 完善模型架构。**PaLM 2在不同的任务上进行了训练，有助于PaLM 2从训练中积累更多信息。


图表10：PaLM 2与PaLM在不同语种熟练度测试中的对比


![图片](https://image.cubox.pro/article/2023051610235868224/36561.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：谷歌《PaLM 2 Technical Report》（2023年），中金公司研究部


图表11：PaLM 2逻辑推理能力示例


![图片](https://image.cubox.pro/article/2023051610235836036/49236.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：谷歌官网，中金公司研究部


图表12：PaLM 2代码生成能力示例


![图片](https://image.cubox.pro/article/2023051610235836907/11937.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：谷歌官网，中金公司研究部


**25款谷歌产品注入PaLM 2大模型能力。** 2023年谷歌I/O大会不仅发布PaLM 2大模型，还宣布将PaLM 2模型能力接入旗下25款产品中。例如**谷歌对话机器人Bard** 将通过PaLM 2提升多语言对话、理解推理、代码生成能力；**Workspace** 将AI能力落地企业办公，提高Gmail、Doc、Sheet等办公软件使用效率；支持**Duet AI** ，以生成式AI协作工具提升团队合作效率；在健康医疗以及网络安全领域，分别推出基于PaLM 2的、专注于细分场景的AI模型**Med-PaLM 2、Sec-PaLM 2。我们看到，谷歌PaLM 2深入下游应用场景，在企业办公、医疗、安防等多场景落地，我们认为应用落地是AI价值体现的重要方式。**


图表13：Med-PaLM 2在医疗测试中达到85.4%正确率


![图片](https://image.cubox.pro/article/2023051610235885165/58434.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：谷歌官网，中金公司研究部


图表14：PaLM 2赋能的应用生态


![图片](https://image.cubox.pro/article/2023051610235872073/85133.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：谷歌官网，中金公司研究部


**PaLM-E：视觉、语言多模态，大模型睁眼看世界**

**结合ViT的视觉能力，PaLM-E建立模型虚拟世界到物理实体世界的桥梁。**2023年，谷歌推出5620亿参数的大模型PaLM-E，参数规模迈上新台阶。其模型能力实际上综合了ViT（Vision Transformer，220亿参数）和PaLM（5400亿参数）两个模型的能力。前者将大模型能力泛化至CV领域，赋予大模型视觉能力；后者凭借优秀的语言理解、逻辑推理、代码生成等能力，赋予大模型思考能力。两相结合，PaLM-E模型具备多模态能力，能够观察物理实体世界的信息，由大模型进行分析理解，再将决策结果反馈至物理世界，由此沟通物理和虚拟两个世界。


图表15：PaLM-E模型的简要总结


![图片](https://image.cubox.pro/article/2023051610235899978/94853.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Danny Driess, Fei Xia et al. PaLM-E: An Embodied Multimodal Language Model\[J\]. 2023.，中金公司研究部


图表16：PaLM-E模型能力一览


![图片](https://image.cubox.pro/article/2023051610235840883/47468.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Danny Driess, Fei Xia et al. PaLM-E: An Embodied Multimodal Language Model\[J\]. 2023.，中金公司研究部


**以机器人为例，**当面对"从抽屉中取出薯片给我"任务时，人类的反应是一气呵成的；但是对于大模型来说，它需要将这个任务分解成三个子任务（任务与运动规划、桌面环境分析、移动操作），分别对应三个环节（决策层、感知层、执行层）。PaLM-E首先将大目标细化为多个小目标（去抽屉处---打开抽屉---取出薯片---将薯片送至我处---放下薯片），然后在每个小目标阶段通过机器视觉分析当前桌面环境，依此执行取放操作。


图表17：PaLM-E驱动机器人执行任务


![图片](https://image.cubox.pro/article/2023051610235880089/71728.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Danny Driess, Fei Xia et al. PaLM-E: An Embodied Multimodal Language Model\[J\]. 2023.，中金公司研究部


**我们认为，谷歌PaLM-E是其通往AGI愿景的又一重要里程碑。**一方面，PaLM-E以多模态为主要特征，切实地与物理世界产生交互。这与人类的行为方式相吻合，通过知觉器官感知世界并通过四肢与世界发生交互。另一方面，PaLM-E并非多个特定领域大模型的并集，而是初步实现了仅由一个大模型执行多个跨模态复杂任务，且不同任务中所积累的经验能够迁移至其他更多任务中，而非仅服务于单个任务，与人类的思维学习方式日趋接近。


图表18：PaLM-E展现出跨领域地迁移学习能力


![图片](https://image.cubox.pro/article/2023051610235837368/87471.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Danny Driess, Fei Xia et al. PaLM-E: An Embodied Multimodal Language Model\[J\]. 2023.，中金公司研究部


**TPU和Pathways，PaLM系列模型背后的能力底座**


如前所述，PaLM-E模型是PaLM、ViT模型能力的综合体，而PaLM模型是谷歌首个基于Pathways系统以及TPU v4开发的大模型，PaLM 2在PaLM的基础上实现性能的二次提升。**我们认为，大模型的能力来源于大数据、大算力、强算法，对于PaLM系列模型而言，训练过程中TPU芯片所提供的算力支持以及Pathways框架对算力资源的调度能力，是PaLM系列模型优秀能力所不可或缺的硬件端、系统端支撑。**


**TPU：提供算力的硬件基础**


**能够用于加速人工智能计算的芯片通常包括CPU、GPU、FPGA与ASIC等几个主要类别。**

**► CPU（Central processing unit，中央处理器）：**CPU是通用计算芯片，应用相当广泛。但由于CPU遵循传统冯·诺伊曼架构，每次计算均需要从内存中取数、执行计算、再将结果存入内存，内存访问速度较慢。因此当面对大规模计算时，CPU总吞吐量会受到限制。

**► GPU（Graphic processing unit，图形处理器）：**GPU内部包括数以千计个算术逻辑单元（ALU），因此可以并行处理数千个乘法与加法运算；而人工智能神经网络中包含大量矩阵运算，恰与GPU的工作原理相契合。但与CPU类似，每个ALU仍受吞吐量的限制。

**► FPGA（Field programmable gate arrays，现场可编程门阵列）：**FPGA能够根据使用场景调整电路编程，灵活性是其最重要的特点之一，但对使用者的编程能力提出了较高要求。

**► ASIC（Application-specific integrated circuit，专用集成电路）：**ASIC与可灵活编程的FPGA不同，它是专门为某一特定任务而开发的。尽管用途专一局限、开发周期较长，但其高效能、低功耗、低延迟的特点，仍吸引一些资金实力较强的厂商着力开发。


图表19：CPU、GPU、FPGA、ASIC对比


![图片](https://image.cubox.pro/article/2023051610235892117/59754.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：谷歌官网，华为官网，中金公司研究部


**硬件服务算法，TPU是谷歌专门为人工智能神经网络而设计的ASIC芯片。**TPU（Tensor processing unit，张量处理器）以矩阵计算为主要任务，内部包含数以千计的计算单元（ALU），左右ALU呈矩阵分布，且每个ALU均与上下左右四个方向的其他ALU直接连接，谷歌称之为脉冲架构（Systolic array）。进行计算时，TPU从HBM（High bandwidth memory，高带宽内存）中取出参数与数据后，数据在计算单元间流过时直接进行乘法与加法运算，不再与内存进行交互。由此TPU能够实现较大的总吞吐量，提升整体运算效率。


图表20：TPU硬件结构（以TPU v2、TPU v3为例）


![图片](https://image.cubox.pro/article/2023051610235822494/91381.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Nextplatform，中金公司研究部


**TPU v4是PaLM模型训练背后的算力基础。**2021年谷歌I/O大会上第四代TPU正式发布，其算力达275 TeraFLOPS，较第三代有2倍以上的提升。一般4096个TPU v4构成一个TPU v4 Pod，合计算力超过1 ExaFLOPS。从谷歌最新发布的TPU v4论文\[5\]可知，除了算力较前代有较大幅度升级外，TPU v4的亮点还在于采用了光路开关实现了可重配置的光互连，"以光代电"加快TPU v4群之间的传输速率，灵活性以及可拓展性均有较大程度提升。谷歌PaLM模型的训练基于2个TPU v4 Pod、6144块TPU v4芯片，我们认为高算力芯片以及提升数据传输速度的硬件设计是PaLM大模型重要的硬件支撑。


图表21：TPU v3与TPU v4性能对比


![图片](https://image.cubox.pro/article/2023051610235892690/46157.jpg?imageMogr2/quality/90/ignore-error/1)


注：表中算力精度均为bf16 or int8；  
资料来源：谷歌官网，中金公司研究部


**Pathways：调度算力的系统框架**


**愿景：构建一个通用、跨模、稀疏的AI框架**

**谷歌最初提出Pathways的愿景是构建通用人工智能的AI框架\[6\]，希望人工智能的实现方式尽可能地贴近人类思维------**

**► 通用。**"大炼模型"时代，各厂商针对各自细分行业的特点开发AI模型，使得全行业AI算法数量较多。这些模型虽然规模较小，但是更好地契合了特定任务的需求，用途也较为局限。但谷歌认为，人类在学习新技能时会基于以往积累下的经验进行迁移学习，例如看到一张航拍图像，不仅能够分析图片内容，还能了解背后的风土文化。因此，谷歌Pathways的愿景之一在于构建一个泛用性更强的人工智能模型。

**► 跨模。**Transformer架构最初应用于机器翻译，由于其在NLP任务中的良好表现而被广泛应用于自然语言处理领域。当前以GPT为代表的大模型多执行"A生B"式的任务，但无论是A还是B，目前均只能接收或输出单一模态，而不能接受同时包括文字、图片、语音等信息的输入。谷歌认为人类处理问题时某一瞬间接收到的信息是复杂、多样、跨模态的，人工智能也应当如此。因此，谷歌Pathways的愿景之一在于构建一个多模态的人工智能模型。

**► 稀疏。**GPT、BERT等当前主要大模型都是稠密模型，执行下游任务时所有参数都会参与训练与推理。但从人脑的思维方式出发，尽管我们脑中储备的经验知识很多，但是在处理不同下游任务时会根据情景调取不同的储备。因此，谷歌Pathways希望做一个稀疏且高效的模型。此外，稀疏模型在能效方面更有优势，例如GShard和Switch Transformer两个稀疏模型的能耗是同等规模稠密模型的十分之一。


图表22：谷歌希望构建一个通用、跨模、稀疏的人工智能框架


![图片](https://image.cubox.pro/article/2023051610235839349/45177.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：谷歌官网，中金公司研究部


**实际：优化TPU算力调度，AGI愿景阶段性成果**

尽管前文谈到谷歌设计Pathways的重要初衷在于构建一个通用、跨模、稀疏的AI框架，但其关于Pathways架构的论文\[7\]所展示的内容实际上围绕"如何通过架构设计提高TPU芯片计算效率"展开。**我们认为实现通用人工智能并非一蹴而就，其背后有芯片、架构设计等诸多细节的铺垫，谷歌当前的布局有望一步步补齐AGI的整个拼图。**

**Pathways旨在提高异构AI加速芯片集群上的数据处理效率。**随着大模型语料规模、算力规模、参数规模的不断上升，简单的数据并行（将数据分成不同份，每份在一个计算集群上进行训练）已难以满足大模型训练的需求，例如PaLM即采用了数据并行与模型并行（将模型按层分成不同份，每份在一个计算集群上进行训练）相结合的方式提升训练效率。我们认为，在这样的背景下，MPMD（多程序，多数据）\[8\]的编程范式将变得更为常见，对数据以及算力资源的调度能力的重要性逐步提升。Pathways架构中的资源管理器（Resource manager）可实现对多数据、多程序的调度，将数据处理程序映射到TPU硬件上，同一块TPU甚至可以同时分配给不同的数据处理任务中。由此，Pathways能够在更大程度上充分利用硬件资源，减少资源的空耗与浪费。


图表23：Pathways系统架构一览


![图片](https://image.cubox.pro/article/2023051610235824530/78839.jpg?imageMogr2/quality/90/ignore-error/1)


资料来源：Barham P, Chowdhery A, Dean J, et al. Pathways: Asynchronous distributed dataflow for ml\[J\]. Proceedings of Machine Learning and Systems, 2022, 4: 430-449.，中金公司研究部


**建议关注潜在催化作用**


**应用落地是AI价值体现的关键。**从谷歌2023年推出的两个大模型PaLM-E、PaLM 2，我们看到谷歌积极将AI落地实际场景。PaLM-E利用机器视觉和语言理解，能够驱动机器人执行复杂任务，将大模型能力由"决策层"延伸至"执行层"，赋予了AI大模型应用落地的更大可能。PaLM 2成为类似于OpenAI GPT-4的基础大模型，谷歌宣布将其应用于旗下25款产品中，以Bard、Workspace等为窗口触达个人与企业，赋能办公、医疗、网安等领域。

**而推动AI落地离不开算力的支撑。**以PaLM为例，其训练动用了2个Cloud TPU v4 Pods和6144块TPU，采用数据并行和模型并行相结合的方式提升训练效率，最终形成参数规模高达5400亿个、硬件使用效率达57.8%的大语言模型。此外，谷歌还搭建了Pathways架构，通过资源管理器合理调度数据与算力资源，使得整体训练系统能在更大程度上更充分地利用硬件资源。

**我们建议投资者关注5月谷歌I/O大会对产业链的潜在催化作用。**


**风险提示**


**► AI应用发展不及预期。**我们看到，随着全社会数字化转型及智能化渗透率的提升，人工智能持续赋能各行各业。而人工智能依赖于海量数据进行模型训练及推理应用，推动全社会算力需求的提升，服务器、存储器、通信网络设备等上游硬件基础设施有望受益于AI驱动的算力需求提升。如果人工智能发展及应用落地不及预期，可能会使上游硬件设备受到需求侧的压制，发展不及预期。

****►**AI算力需求不及预期。** 若AIGC因为伦理等问题遇到严格监管，则存在技术进步放缓、各厂商大模型开发节奏放缓的风险；此外，若AIGC应用端的推广不及预期，则我们对活跃用户数的假设也存在不及预期的风险。这些不确定性最终会导致大模型厂商对上游芯片需求不及预期。  

\[1\]Devlin J, Chang M W, Lee K, et al. Bert: Pre-training of deep bidirectional transformers for language understanding\[J\]. 2018.

\[2\]Roberts A, Raffel C, Lee K, et al. Exploring the limits of transfer learning with a unified text-to-text transformer\[J\]. 2019.

\[3\]Chowdhery A, Narang S, Devlin J, et al. Palm: Scaling language modeling with pathways\[J\]. 2022.

\[4\]谷歌《PaLM 2 Technical Report》（2023年）

\[5\]TPU v4: An Optically Reconfigurable Supercomputer for Machine Learning with Hardware Support for Embeddings

\[6\]https://blog.google/technology/ai/introducing-pathways-next-generation-ai-architecture/

\[7\]PATHWAYS: ASYNCHRONOUS DISTRIBUTED DATAFLOW FOR ML

\[8\]Multiple program multiple data（MPMD）：多个程序在多个处理器上执行，每个程序处理不同的数据；


**Source**


**文章来源**


本文摘自：2023年5月13日已经发布的《AI浪潮之巅系列：谷歌PaLM模型，迈向AGI愿景又一阶》

陈昊 分析员 SAC 执证编号：S0080520120009 SFC CE Ref：BQS925

孔杨 联系人 SAC 执证编号：S0080122110018

彭虎 分析员 SAC 执证编号：S0080521020001 SFC CE Ref：BRE806


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


![图片](https://image.cubox.pro/article/2023051610235812435/94314.jpg?imageMogr2/quality/90/ignore-error/1)


[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7057762853876402144)
