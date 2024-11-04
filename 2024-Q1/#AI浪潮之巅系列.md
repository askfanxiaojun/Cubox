#AI浪潮之巅系列
=========

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/PtwCiB0plIN6sj05T8P04A)温晗静 贾顺鹤等 中金点睛

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FfzHRVN3sYsicmoVBv4D0mPib68kWJVkDjnEM91ZO46IRCPDfIfFpMEn2BoxwUa2fguPicQ4WwvNibdnOL4IqZj4XTA%2F640%3Fwx_fmt%3Dgif)


**中金研究**


我们认为，端侧AI部署是当前AI实现规模化扩展及应用落地的关键。作为底层技术和上层应用之间的载体，我们看到AIPC在模型侧、硬件侧、软件及应用侧均存在产业升级趋势。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_gif%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2Lqu0jT9T9IhgcMY3hN5viceXlc3RIwYicz0lLGMibnBq848Jq7sZt0hmZQ%2F640%3Fwx_fmt%3Dgif%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2Ln7QDeYCRrzqR0VlHMEFcMSgujsH9TKQUaaNxcet0Fiab2Th6UqJ3OpA%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

**[点击小程序查看报告原文]()**


**Abstract**


**摘要**


**为什么要讨论移动AI？**在降本与安全的双重考量下，AI部署在逐渐从云端走向移动端。我们认为，终端和云端协同工作分流AI计算工作负载的端云混合模式或将成为主流部署方案。在此背景下，AIPC在模型侧、硬件侧、软件及应用侧均将发生变化。

**在模型侧，从"暴力美学"大模型，到"删繁就简"轻量模型，轻量化移动模型发展迅速。**谷歌2023年起相继发布Gemini Nano（1.8B/3.25B）、Gemma（2B/7B）等轻量化模型；Meta推出Llama 2、Mistral AI推出Mixtral 8x-7B等开源模型，引领移动模型轻量化发展趋势。此外，小米、OPPO、三星等手机厂商亦在轻量化移动模型开发及压缩方面努力。

**在硬件侧，关注Arm架构、异构计算和存储升级，AIPC带动散热、电池及结构件等变化。**根据Trendforce，微软计划在Windows12为AIPC设置最低门槛，需要至少40TOPS算力和16GB内存。结合端侧AI部署对算力、内存、功耗的要求，我们看到芯片端三大升级趋势：1）Arm架构以其低功耗、长续航的特点或将实现PC市场份额提升；2）异构计算或将成为主流方案；3）端侧AI运行亦对内存提出更高要求，将带动DDR5/LPDDR5渗透率提升及DRAM容量提高。此外，为了适配AIPC的计算及功耗需求，AIPC在散热、电池等环节亦或将带来升级变化。

**在软件及应用侧，Wintel联盟持续发力。**操作系统方面，新一代操作系统Windows11重点强调了AI的功能，并提供多项AI工具；应用方面，目前AI应用主要集中在云端，但我们看到英特尔本地运行diffusion模型的端侧应用，我们认为随着AI端侧部署的进一步落地，端侧AI应用或将持续丰富。


**风险**


AI算法技术及应用落地进展不及预期，AI变现模式不确定，消费电子智能终端需求低迷。


**Text**


**正文**


**AI的下一站：移动端AI的探索**


**为什么要讨论移动AI？**


大模型的发展成为了2023年的市场关注热点，在追求"大"的竞争趋势下，各大科技巨头纷纷在模型参数上追赶。但是过大的参数造成了在开发及使用过程中的成本高企，也在一定程度上限制了AI应用的变现与拓展。在此背景下，探讨能否将一部分算力下沉到端侧，尤其是与用户规模庞大的移动端设备结合，成为了AI发展的重要方向。作为底层技术和上层应用之间的载体，硬件终端承担了重要的枢纽作用。虽然目前AI处理重心主要集中在云端，但由于云端推理成本较高、能耗较大、可靠性及时延、用户隐私及数据安全等问题，**端侧AI部署成为AI实现规模化扩展及应用落地的关键。**


图表1：AI处理重心从云端向终端转移


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LUtbYjurJTav8wuOk9CVBOj1x4S3007zkc2384icej0FsAFoEt5hTjIA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：《混合AI是AI的未来》（高通，2023年），中金公司研究部


**从云端走向移动端：降本与安全的双重考量**

**端侧AI部署有助于显著降低算力成本与功耗，跑通AI变现的商业模式。**在AI发展的未来，不可忽视的问题是，随着日活用户数量及使用频率的增长，若只依靠云端算力支撑模型推理，成本及能耗会显著增加。而终端运行AI方面，以高通全栈优化下可在手机端运行的Stable Diffusion为例，每次产生的成本较小或者可以忽略不计，这将有效降低应用厂商成本，促进软件应用商业模式落地。

**端侧AI部署通过将用户敏感信息留在本地，将有效减少隐私泄露、数据安全、时延等问题。**数据窃取攻击即通过目标模型的多次输出去获取训练过程中使用过的数据分布，当攻击者知晓大模型训练过程中使用过的数据是哪些，就会造成数据隐私损害。而终端侧AI部署将个人信息保留在本地，可以从根本上避免数据安全性问题的出现。此外，时延等使用体验感对终端用户也很重要，当云端大模型访问量达到高峰期时，会出现延迟反馈甚至拒绝服务。

**移动端模型部署方案：端云协同模式成为主流**

目前移动端AI部署的方式分为端侧部署、端云协同两种。

**► 端侧部署：**即在终端如手机、PC等上进行大模型本地部署；

**► 端云协同：**即终端和云端协同工作分流AI计算的工作负载，根据工作负载分流模式，高通提出三种云端混合的模式：1）以终端为重心的混合AI，其中终端将充当锚点，云端仅用于分流处理终端无法充分执行的任务；2）基于终端感知的混合AI，在边缘侧运行的模型将充当云端大语言模型（类似大脑）的传感器输入端（类似眼睛和耳朵），向云端处理输入文字信息；3）终端与云端协同处理的混合AI，终端向云端发送多个token，云端仅需读取一次完整模型参数来并行计算多个token输入，提升模型运算效率并节省功耗。


**从云端到移动端：移动AI将发生哪些变化？**


图表2：AI云侧及端侧部署体系架构情况


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2L05oC5yQPFaNu1GcI3EI4KPl1RtaaLx5j3Obibg0XGG6ykrTicYR6Q4xw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：各公司官网，中金公司研究部


**PC厂商陆续入局，2024年多款AIPC产品陆续发布**


**PC厂商抢滩AIPC，储备多款产品**


**AIPC指的是硬件上集成了混合AI算力单元，能够本地运行"个人大模型"、创建个性化的本地知识库，实现多模态人机交互，展现为为每个人量身定制个人AI助理，能够提升生产效率、简化工作流程的PC终端。**AIPC具有可实现终端大模型的"千人千面"个性化体验、可进行自然语言交互、内嵌智能混合算力、构建了开放生态、可确保数据的隐私性和安全性五大特征，可为用户带来全新体验。


图表3：AIPC行业主要进展


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2Lia3dMyRB5RjVtq9gh5CBicSXrhtRTqg2XGiaqWX81JsoW02tkfvZTgcpg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：各公司官网，中金公司研究部


**全球PC市场走出低谷，长期AIPC有望实现量价齐升**


根据Canalys，4Q23全球PC（不含tablet）出货量同比增长3%至6,530万台，结束了连续七个季度的同比下滑。同时，Canalys预测2024年全球PC出货量有望同比增长8%至2.67亿台，我们认为主要是Windows12的推出、众多AIPC上市或推动PC换机周期到来。考虑到AI在提高生产力、促进应用落地创新的潜在能力，**IDC预测，AIPC\[1\]有望在2027年渗透率达到85%。**


图表4：全球PC出货量及增速


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2L60Z6w7RJDoibEF25OhdG9ZSr6Ff2UMKwOic6OFZRlUoG4GvI4WYmSfvA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：Canalys，中金公司研究部


图表5：AIPC出货量预测


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2L5XXWcszB4icHKHPgxdY3ibAApchGU6mf9fmHaT0ErvoEBNicSlr5mJJOg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：IDC，中金公司研究部


**行业升级：关注算力芯片及存储升级趋势**


**模型侧：从"暴力美学"的大模型，到"删繁就简"的轻量模型，轻量化移动模型发展迅速**


**谷歌+Meta领军，轻量化模型迭代加速**

**近年来，大模型自身在快速迭代推新，文本、图像、视频等多种模态模型发展加速。**近期Sora视频模型的出现，也进一步打开了人们关于大模型应用方向的想象空间。**但另一方面，我们认为从模型自身所需要的算力来看，大模型也并非只朝着越来越大的方向发展。**


图表6：大模型轻量化发展情况


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LbGd2TNhym2ZKR9kd0p8R5XMcdMKZQO6uCDdqLKByicvKTYQhVERB42g%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：各公司官网，中金公司研究部


图表7：Llama2帮助性及安全性强于主流开源模型


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LwtEm028iboVmicjmPkylhMQnpEMrkfhhBBCBW1UoWpbGuoiaS2icBSovuA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


注：横轴为帮助性，纵轴为安全性。Falcon-40b-instruct在Hugging Face的开源大型语言模型排行榜上排名1

资料来源：《Llama 2: Open Foundation and Fine-Tuned Chat Models》（Hugo Touvron, Louis Martin, Kevin Stone, et al. 2023），中金公司研究部


**大模型压缩技术亦逐渐成熟**

**为适配PC端侧运行需求，通过蒸馏及剪枝等方案将大模型压缩后的轻量化模型陆续发布。**联想基于大模型压缩技术，将LLM压缩至轻量化模型进行本地部署，目前Lenvo AI Now助手的大模型来自阿里云的通义千问（原始参数量7B，大小14.4GB），大模型压缩到4GB，电脑配置5-6GB的内存即可运行。此外，宏碁与英特尔合作通过OpenVINO工具开发宏碁AI库；Meta Llama 2开源模型也可借助MLC Chat工具，实现在手机、PC上本地部署。


**硬件侧：关注Arm架构、异构计算和存储升级，AIPC带动散热、电池及结构件等变化**


**微软或引领AIPC硬件定义，40TOPS算力，16G内存成为门槛**

在讨论芯片端变化之前，值得关注的，端侧模型的运行对PC芯片的算力和存储性能等提出了挑战，但同时作为移动设备，功耗续航等问题又需要满足消费者在移动场景下的使用需求。根据Trendforce，微软计划在Windows12为AIPC设置最低门槛，需要至少40TOPS算力和16GB内存。单从当前PC芯片的算力看，跨越40TOPS门槛将成为首要目标。因此AIPC在芯片端硬件升级主要目标是：提升算力，提高内存，同时要降低功耗，**基于这一目标，我们关注到了芯片侧的三大变化：架构变化、异构计算和内存升级。**

**此外，为了适配AIPC的计算及功耗需求，AIPC在散热、电池等环节亦或将带来升级变化。**由于这里的变化目前还处于早期，整体方案设计并未完全确定，但从发展的思路上，主要会围绕降低功耗、增加续航、减少整体机身重量等方向去演进，因此在电池（硅碳负极）、结构件（碳纤维）、散热（热管等）方面或将出现新的变化。


图表8：PC芯片算力持续提升


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LDBCSHic6KW8sR9ywR4hWqHmwK4qdTcGibre3ibwnGVuzqezj2DWVgA7FA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：高通官网，英特尔官网，AMD官网，苹果官网，中金公司研究部


**变化一：PC市场Arm架构份额有望提升**

**随着AI对PC芯片算力的需求提升，对应芯片的功耗问题也开始凸显，Arm架构以其低功耗、长续航的特点受到关注。**指令集决定处理器的运行逻辑，向底层硬件传达指令和数据，不同的指令集架构与操作系统、软件应用构成独立的生态体系。当前笔记本电脑的CPU指令集主要为X86和Arm两种，Intel和AMD采用X86架构，苹果采用ARM架构。从市占率看，由于微软与英特尔的联盟稳固，因此过去20年PC的软件和应用开发都是基于X86架构，Arm架构目前只由苹果的MacBook采用。


图表9：X86架构生态vs Arm架构生态


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LaEuTw1uR707Fdyxg5PGx52fXJB1AvYx2t3qiaBIBbNico1YjnZM68yXQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：亿欧智库，中金公司研究部


**从应用进展上，苹果基于Arm架构自研的M系列芯片具有功耗优势。**以最新一代M3芯片性能来看，M3芯片性能核速度比M1提升最高30%，比M2提升15%。尤其在功耗这一指标上，基于ARM架构的M3芯片展现出了优势：CPU在与M1提供相同性能，功耗几乎只有之前的一半，CPU与某最新的12核PC笔电芯片相比，相同性能功耗只需25%。因此在AIPC时代，随着算力提升带来的功耗问题越来越受到关注，Arm架构在功耗方面的优越性能或将得到更多关注。


图表10：当前PC市场中苹果主要采用ARM架构


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LbLPhQRnJxJuwKyVmdBQBtOyToN2iaicWdrQxOVDEMVhXDoj8M2ic3Aicbw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：IDC，中金公司研究部


图表11：Counterpoint预计至2027年基于ARM架构的PC占比将达到25%


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2Lr8eANAC0OVLU14xGIRIPicbJ1jcR5uDkOyPwbqmSYoP8UbsKjt28Xyw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：Counterpoint，中金公司研究部


**Windows on Arm最大挑战是软件兼容性问题。**理想情况下，Windows on Arm既能享受Arm架构处理器带来的低功耗和长续航优势，又能延续x86 PC用户的软件使用习惯。但是由于缺乏苹果的软硬件一体化生态环境，无法在硬件上实现高转译效率。2021年，微软发布Windows 11 on Arm，引入x86-64位仿真技术，极大地扩展了在Arm平台上运行的应用程序范围。2022年微软推出Arm64版本的IDE工具Visual Studio2022正式版，方便直接编译可在Windows 11中运行的Arm程序，进一步加速Windows生态向Arm迁移。


图表12：Windows on Arm发展历程


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2Lia3EqPNBkficb2nZxwOmLyKicfIVW0GLZCibMhhB0WgEkxGnyWiap7LptpA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：各公司官网，中金公司研究部


**高通、微软联手推动Windows on Arm转型，促进Arm PC生态的迅速发展。**在苹果MAC问世前，Windows系统+Intel/AMD一直主导着几乎整个PC市场，被称作"Wintel"联盟。随着笔记本电脑朝低功耗、轻薄本的方向发展以及主打便携、续航时间长的平板电脑品类的出现，Arm低功耗的优势再次被重视，有望带来更长的电池寿命、更薄的机身甚至是无风扇的设计；1）产品端，微软在2012年推出全新的Surface系列平板电脑，在Intel Core i5处理器的Windows 8Pro版本以外，推出专为Arm设计的Windows RT版本；2）芯片端，高通2023年10月24日推出Arm架构的PC芯片X Elite；英伟达和联发科合作布局Arm PC处理器，根据路透社，预计该芯片最早2025年推出；AMD也进入了Arm PC处理器，根据路透社，预计最早2025年推出；英特尔2024年2月22日宣布与Arm合作，未来提供Arm架构的SoC芯片代工服务。随着24年Windows 12的升级，有望通过模块化底层设计更好地支持Arm架构，我们认为在软硬件适配度持续提升下，Arm PC有望在2024年迎来拐点。

**变化二：xPU异构计算兴起**

**后摩尔定律时代，通过提升CPU时钟频率和内核数量来提高计算能力的传统方式遇到散热和能耗瓶颈，因此异构计算应运而生。**异构计算指的是将CPU、GPU、NPU、DPU等不同架构或指令集的计算单元整合到一起的混合计算系统，其中CPU擅长管理和调度，GPU擅长处理并行计算，DPU可突破数据流量指数级增长带来的性能瓶颈的关键技术，通过算力卸载、算力释放和算力拓展，释放CPU的计算资源，提升整体计算效率；NPU是基于DSA领域专用架构技术的处理器，相比CPU、GPU等通用处理器，从硬件架构上更适合于神经网络运算，可专门用于给AI做硬件加速。


图表13：不同处理器AI运行性能对比


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LGbpxOlEdHOCTturerHWIdSHSa0OaMB5sTdicvulEYDSiasTqfxALuVibw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：Peyoot，中金公司研究部


**当前英特尔、高通等厂商均采用异构架构，尤其强调NPU的性能。**异构计算出现的背景在于，经过多年的发展，通过提升CPU时钟频率和内核数量来提高计算能力的传统方式遇到散热和能耗瓶颈，这一问题在AI时代将会更加严重，相应芯片厂商均采用集成NPU以提升计算能力的新方案：1）高通骁龙X Elite集成Hexagon NPU，算力达75TOPS，可支持超过130亿参数的模型运行；2）英特尔Meteor Lake SoC架构首次将NPU内置，支持200亿参数大语言模型运行。

**此外，英特尔推出了酷睿Ultra"分离式Tile"策略。**这是英特尔在消费级市场上第一次采用分离式模块化架构，将传统的单芯片一分为四：Compute Tile、SoC Tile、GPU Tile、IO Tile，进一步提高能效。


图表14：英特尔酷睿Ultra"分离式Tile"策略


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LglFoFNC1sps9kWIeKviaTRYxFcTvfy0XNezv4RQoAiaP03uRRbm4v9qQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：Digi-key，中金公司研究部


**变化三：内存容量及速率提升**

**笔记本电脑侧CAMM2/LPCAMM2内存条或将取代SO-DIMM制式。**2023年12月5日，JEDEC组织正式发布压缩附加存储模块（CAMM2，Compression Attached Memory Module）通用规范。新发布的CAMM2标准有望替代SO-DIMM成为未来笔记本电脑的标配。CAMM2/LPCAMM2内存条可以适配DDR5颗粒或LPDDR5(X)颗粒。和SO-DIMM相比，CAMM2/LPCAMM2内存条具有更加轻薄、频率更高等优势，能够更好适配AI笔记本的需求。


图表15：SODIMM v.s. CAMM


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LfyshOt7MUO6QsDo744gugF46y9NDVRmswMvticRbaHWQh2BgNramzxw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：JEDEC，中金公司研究部


**新一代处理器将仅支持DDR5/LPDDR5，促进渗透率提升。**产业链一般认为2023年9月推出的Intel Meteor Lake（第14代酷睿）（具备约35TOPS算力）对AIPC的发展具有重大意义。而根据Microsoft的定义，AIPC的处理器需具备至少40TOPS算力。按照此标准，AMD Ryzen 8000系列（2024年1月发布）、Qualcomm Snapdragon X Elite（Qualcomm预计2024年年中推出）、Intel Arrow Lake（第15代酷睿）（Intel预计2024年下半年推出）才是"真正"的AIPC处理器。根据官网参数，无论是Intel Meteor Lake还是AMD Ryzen 8000系列或者Qualcomm Snapdragon X Elite都仅支持DDR5/LPDDR5。我们认为如果AIPC的渗透率快速提升，高性能处理器出货占比将会提升，相应将带动DDR5/LPDDR5渗透率的提升。

**单台PC平均DRAM容量有望从9GB提升至16GB以上。**根据TrendForce数据，2021年底单台PC的DRAM平均容量为7.49GB，我们认为2023年底单台PC的DRAM平均容量在9 GB左右（假设2021-2023年单机DRAM容量CAGR保持和2019-2021年相同约为10%）。


图表16：2019-2021年单台PC的DRAM平均容量增长趋势


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LeoL5JxVTnviblxrSiblgOHlWpPxcibN5JoZn431HGaZzWoRuH3vRR5X3A%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：TrendForce，中金公司研究部


**虽然目前各厂家对AIPC存储配置尚无统一规定，但是我们认为AIPC对于单台PC的DRAM容量的拉动趋势是确定的。**结合各厂家信息，我们认为16GB将成为AIPC单机DRAM的最低配置。


图表17：AIPC内存容量需求


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2Lxa8KnFOjdOG0sjY3uo9xNUlEQRttqArTa5pfW5nAxGh7vAicP8wmwJA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：Omdia，中金公司研究部


**变化四：关注散热、电池及结构件等变化**

**电池：硅碳负极提升电池能量密度。**传统PC或手机电池采用石墨作为负极，石墨负极理论克容量为372mAh/g，但硅基负极理论克容量可高达4200mAh/g，因此便出现了通过给负极掺硅碳复合材料的方式来提升电池能量密度的技术尝试。目前在小米、荣耀的新一代旗舰手机上，均出现了高密度硅碳负极电池的身影。其中小米"金沙江电池"容量达到5300mAh，最高硅含量6%，电池体积降低8%，续航提升高达17%。而在AIPC时代，随着算力提升带来的功耗提升，对电池续航能力的要求也更高，因此我们预计未来硅碳负极电池有望凭借更高的能量密度普及至AIPC领域。


图表18：小米新一代小米14 Ultra采用硅碳负极电池


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2L5iacluC9teEibUKMQvxWBS8GPvUbVjbghQTYGQ3yvxkPz7s85dle54nQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：小米官网，石墨资讯，中金公司研究部


**散热：随着AIPC计算带来的功耗增大，如何提升散热及屏蔽能力亦成为重点。**从结构上看，PC散热由多个散热部件组成，核心包括热管、散热鳍片、风扇、散热硅脂、均热板VC等。由于芯片算力提升，对应对散热的要求也会提升，但同时还要满足笔记本电脑在重量、厚度等方面的整体设计要求，因此目前各家PC厂商的散热方案并不完全一致，但通过提升散热能力降低发热的整体思路一致。

**结构件：碳纤维结构件等助力机身轻薄。**由于AIPC在算力、功耗、续航等方面均需升级，因此从整机设计角度，控制机身重量和厚度就具备必要性。与传统的金属件、模切件相比，碳纤维结构件具有轻质、高强度、散热性能好等特性，目前已经有多家PC厂商开始采用碳纤维作为背板。


**软件\&应用侧，Wintel联盟发力，系统优化+应用端侧落地**


**Windows系统对AI应用的适配是继硬件成熟之后的另一重要前提**

**Windows在新一代的Windows11重点加强了AI的功能，并提供多项AI工具。**微软新版Windows11 23H2版本于2023年9月26日上线，集成了基于Bing Chat和GPT-4的Copilot，并对一些操作系统中的基础功能进行了AI升级，包括画图（Point）、视频编辑器（Clichamp）、截图工具（Snipping Tool）和照片等。

**硬件成熟后，关注AI应用端侧落地进展**

**当前AI应用主要在云端运行，应用主要聚焦于AIGC领域，长期AI应用端侧落地或加速。**我们统计了2023年全球热门的AI工具，以及当前一级投资聚焦的领域，目前AI应用的最快落地场景仍聚焦在图像生成、AI对话、视频生成等AIGC领域，几乎所有的应用也是基于云端算力运行。但长期看，如前文所述，考虑AI应用的日益丰富，同时不断增长的用户规模带来的算力成本，AI应用在端侧的落地或成为趋势，英特尔已经展示了通过OpenVINO插件，离线在本地运行的Diffusion软件。

**此外，英特尔亦提出AIPC加速计划，并通过OpenVINO工具套件帮助开发者在端侧部署和运行AI应用。**根据AIPC计划，英特尔指出2025年将有超过1亿台电脑配备AI加速器，他们计划与100多家ISV合作，利用300多种人工智能驱动的功能，增强跨多个领域的PC功能，目前已经与Adobe、zoom等厂商进行合作。在提升软件开发效率方面，开发者可以通过OpenVINO插件提供支持。


图表19：英特尔AIPC加速计划


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LL5VAicsGQsOvECUP4dCibOBoUanm0dl1q5Dl9ia4JicickLaxhPeJCf8Tdg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


资料来源：英特尔官网，中金公司研究部


**风险提示**


**AI算法技术及应用落地进展不及预期：**ChatGPT\\GPT-4等模型不开源，同时存在着隐私数据泄露、模型窃取、数据重构、Prompt Injection攻击等数据安全性问题、回答准确性问题、道德问题，威胁着模型应用的落地。

**AI变现模式不确定：**虽然AI的出现或将改变数字内容生产关系，但是：1）ToC端，除了GPT-4，其他部分AI模型的用户还处于免费体验的模式，同时New bing等应用也仍处于免费体验的模式，收费模式尚不确定；2）ToB端，目前大量初创企业接入的ChatGPT、GPT-4 API接口收费较低，未来的收费标准和模式也不确定。

**消费电子智能终端需求低迷：**受整体宏观经济、国际地缘政治冲突及半导体周期下行等因素叠加影响，消费电子市场受到较大冲击，国内外市场需求均呈现不同程度的疲软。根据IDC，2023年全球智能手机出货量同比下降3.4%至11.65亿台，创2013年以来新低。根据IDC，2023年中国智能手机出货量同比下降5.1%至2.71亿台。若2024年消费电子需求回暖不及预期，我们认为硬件端受益AI的进展或将不及预期。

\[1\]IDC对AIPC的预测数据包括处理器集成AI加速引擎的笔记本电脑和台式机


**Source**


**文章来源**


本文摘自：2024年3月2日已经发布的《AI浪潮之巅系列：AIPC，AI端侧落地第一站》

分析员 温晗静 SAC 执证编号：S0080521070003 SFC CE Ref：BSJ666

分析员 贾顺鹤 SAC 执证编号：S0080522060002 SFC CE Ref：BTN002

联系人 查玉洁 SAC 执证编号：S0080122120012

分析员 胡炯益 SAC 执证编号：S0080522080012

分析员 曹佳桐 SAC 执证编号：S0080523120004

分析员 黄天擎 SAC 执证编号：S0080523060005 SFC CE Ref：BTL932

分析员 李澄宁 SAC 执证编号：S0080522050003 SFC CE Ref：BSM544

分析员 彭虎 SAC 执证编号：S0080521020001 SFC CE Ref：BRE806


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


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FfzHRVN3sYs9n7JqRicTfNj7L0PbahCf2LWI1UJIoGaldFp9jK0Np58xxia36TMQoymYkbr7R0qqUOibeYk6apag1A%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)


[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7166702976738788944)
