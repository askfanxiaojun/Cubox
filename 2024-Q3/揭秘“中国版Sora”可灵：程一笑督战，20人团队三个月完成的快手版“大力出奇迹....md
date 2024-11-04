揭秘"中国版Sora"可灵：程一笑督战，20人团队三个月完成的快手版"大力出奇迹"
=========================================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/VGeGhw2-xkL5LQdrZldz_w)Yoky 硅星人Pro


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_jpg%2FjopKOlhibRBJByn3PANO10fLm3hLN0OxQKYyXWOmhWZMfaUznxZnNVPNPEIqWNjL934HFl8UoSCnasKXS3PtW6g%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1&valid=false)

作者｜Yoky   
邮箱｜yokyliu@pingwest.com

2023年10月，快手重启了一个当时看起来毫不起眼的项目「噗叽」，这是一款将静态图片通过AI生成2s Gif表情包的工具软件，由万鹏飞（现快手视觉生成与互动中心负责人）团队的一个小组打造，由于没有掀起太大水花，很快，「噗叽」又进入了搁置状态。

从某种程度上看，「噗叽」可以看做是如今最火的「可灵」的前身。

仅仅三个月，可灵一经发布，申请体验的用户数量已突破70万大关，累计生成的视频作品高达700万份。

今年2月，Sora爆火后，让万鹏飞看到了DiT（Diffusion Transformer）新型视频生成架构的可行性，从事视觉算法多年的他开始探索在快手打造"中国版Sora"。

3月初，快手内部开了一个小会，万鹏飞的想法得到了快手高级副总裁盖坤（于越）的肯定，他带着原本十几个人的视觉算法团队进行了小范围的人员补充，迅速确定了将噗叽作为预调研的产品，将一些基础算法在噗叽上进行测试，跑通一些路径后，开始着手打造视频生成模型。

直到5月份，还没有「可灵 Kling」这个名字，技术团队也并不确定何时上线，更不知道上线后会如此受欢迎。

据硅星人向多位知情人士了解到，至今为止，可灵团队规模非常小，仅20余人左右。其中算法团队的核心成员大部分是早年与万鹏飞一起研究视觉算法的队友。

正是这个神秘的"小"团队，在3个月的时间内，打造出了国内首个对标Sora的视频生成模型，可生成高分辨率、长达2分钟的视频。

快手是如何打造可灵的？

为什么这么快？为什么是快手？

可灵问世后，相信这些问题是每个关心可灵的人，最感兴趣的话题。

而我们在尝试着找到答案。


1

**谁在"创造"可灵？**

万鹏飞接到任务的第一件事，是快速组队。

硅星人了解到，万鹏飞负责的研究小组的10几个算法人是可灵团队的核心，其余几人分别在数据、推理、产品等层面对算法团队进行补充。

2021年，他接了前Y-tech技术中心负责人郑文的班，直到在今年的WAIC中才以视觉生成与互动中心负责人的新title亮相。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FjopKOlhibRBJByn3PANO10fLm3hLN0OxQKMNDOTpOmmJtxULPLcro5cKLUn1yDrz8FwFHdibKNKhXrrwLShWg7IA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1&valid=false)2021年论文中显示

公开信息显示，Y-tech AI 技术中心主要研究领域和方向包括图像处理、计算机视觉、计算机图形学、机器学习和人机交互等领域的交叉。

而万鹏飞本人也是名副其实的"技术大牛"，从2012年至今为止，万鹏飞已公开发表过67篇论文，万鹏飞任职快手期间，在国际会议和期刊上发表了多篇论文，如在IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR) ，大部分的研究方向为图像/视频信号处理、计算摄影和计算机视觉、减少Loss函数、视觉生成等方向。

在2022年，万鹏飞就发表了基于点云补全关注与预测不完整3D形状的缺失部分。并基于此设计了一种新的神经网络：PMP-Net＋＋，来模拟推土机的行为。简单地说就是让生成的结果更加精准的一种新的结构。万鹏飞的技术背景或许也是可灵在视频可控性方面表现效果好的原因之一。

有意思的是，2024年6月6日，可灵上线当天，万鹏飞及快手团队公开发表了名为《VideoTetris：Towards Compositional Text-to-Video Generation》的论文，在这篇论文中，清晰地展示了可灵的技术细节，包括生成的过程图、渲染图、如何保证一致性等等。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FjopKOlhibRBJByn3PANO10fLm3hLN0OxQr619ianlenvIS4eNEUqE0cNvHZH43ZnePl4iaj9rNOjI1FxsQGCqThlQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1&valid=false)

在2024年7月3日的最新论文中，显示了长视频生成的如何更准确、清晰，包括眼睛怎么睁开、嘴巴如何动起来、人物的表情如何变换等等。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FjopKOlhibRBJByn3PANO10fLm3hLN0OxQ4Ab3DIyGJxLZ7nrhIgy3kFK2vdqbiaDhiasxl1E3FvHNgCRib9b6Ohvqg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1&valid=false)

通过对论文作者的整理我们发现，6月6日发表论文的作者团队包括：Haotian Yang、Yuan Gao、Xintao Wang、Xin Tao、万鹏飞、张迪，在2024年更早的论文中，还包括了Kanle Shi、Jinchao Zhu、Siyuan Pan、Yuxuan Wang、Yuan Gao、Jianzhu Guo、Zhizhou Zhong、Dingyun Zhang等人。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FjopKOlhibRBJByn3PANO10fLm3hLN0OxQEyeibfB0UYU56teNCJtID12qp1un8qmj5cPpiaul8FN1a1L0nxlJ97Dg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1&valid=false) ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FjopKOlhibRBJByn3PANO10fLm3hLN0OxQ3CI614ayzgnsBghjOgA1QWwOIn7ccFxdhL6cMJ99tc49IOMPLOD2jA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1&valid=false)

我们通过进一步核实，确认了他们中的大部分都参与了可灵的核心开发。这些核心人员几乎是万鹏飞的"固定队伍"，从2022年开始合作，几乎不用再磨合，快速上手。

基于此前的研究团队，很快，可灵的团队雏形已现。

据硅星人了解到，在可灵项目开始后不到一个月，就获得了程一笑的支持，将可灵项目视为公司战略级项目。

"盖坤常说的就是，公司的卡都给你们用，公司全力支持。"可灵团队的技术人员讲道，"张迪（快手多媒体与大模型部负责人）是万鹏飞名义上的＋1，但老万经常直接向盖坤汇报，有时候一笑也会参与。"

甚至程一笑亲自发话："可灵要大做"，AI是一定要跟紧的方向。

一位接近可灵的技术人员也提到："有时候有部门协作，我们需要给可灵的技术团队开账号和权限，和一些数据整理和共享，大家都很配合。"

上至程一笑下至快手每一位员工，都在期待和加速着可灵的诞生。


1

**3个月，快、糙、猛**

硅星人了解到，"做可灵的时候，执行层面有个共识，就是快、糙、猛。"

"Sora出来以后，我们既坚定了这个路线也很着急，你要抢先市场，赶在前面，如果是最后一个做出来的就没意义了。"

万鹏飞在WAIC中讲到了可灵的定义：通过生成式AI的技术，将用户的多模态输入转化为视频信号。"用户可以输入他对于这个内容各种各样的想法，可以是文本，可以是图像，也可以是动作以及其他的控制信息，最终输出是一个视频的信号，计算机就是2D的空间上+3维信号。"
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FjopKOlhibRBJByn3PANO10fLm3hLN0OxQoIw6PPctTC7IIQ61cWrQbmgguot3VsJzVrYjhicETH8X5eBQhd9mwmQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1&valid=false)

而这需要有多维度的数据、AI平台，数据平台和评测平台等Infra层做支撑。可灵的快，首先也是快在Infra层。

另一位快手的数据团队成员告诉我们："快手做视频这么多年，最大的优势是在快手内部，数据都被'洗'得很干净整整齐齐地放在那里，做模型的时候可以直接拿过来用。"

作为短视频内容平台，快手本身拥有着海量的视频数据，同时基于推荐算法的逻辑，快手常年对视频进行清晰地标注，也会为用户做好标签，进行更精准的双向匹配。

"最早，快手在全国各地都有很多标注基地，纯劳动密集型，一部分做审核、一部分做标注。最近几年算法越来越精准，从「一个男人」是或否，进化到了「一个外国男人、穿着西装、金发」是或否，这些视频数据，是训练基础模型的第一步。"上述技术人员讲道。

上述技术人员也为我们举了个例子："你会发现可灵生成'吃饭' 的视频效果特别好，无论是吃什么，一定要大口。这就和快手里大量的吃播视频有关系，而且他们经常吃些奇怪的食物，可灵生成的吃播视频，人物在吃东西时，也经常会出现夸张的表情。"

数据的储备和预处理，让快手不用从"头"开始。另一个层面的快，体现在GPU调度上。

早在几年前开始，快手就与英伟达基于视频处理有着深度合作。

2022年5月，快手便与英伟达共同开发了针对深度神经网络高效部署的 GPU 量化框架，当时深度神经网络（DNN）应用在快手的视频处理和深度推荐中，为了降低DNN的计算成本和推理延迟，英伟达基于Pytorch和TensorRT构建的GPU量化框架：Haquant。目前Haquant支持多种量化算法，在快手特征检测、短视频超分辨等多项业务，可实现模型部署的数倍加速。

2024年的GTC中，快手也公布了基于Hopper架构的推荐系统的最新进展：通过将部分CPU负载迁移到GPU、深入分析和优化GPU性能瓶颈、实施面向吞吐量的内核融合以及其他一系列措施，成功解决了系统瓶颈问题，进而将推荐效率提升了整整20%。

通过快手多年积累的GPU算力调度平台，在训练和推理速度上也有了一定的基础。

当然，开发团队也几乎一刻不停。据硅星人了解到，快手内部只有可灵团队一周上六天班，早十晚十。"周六按加班算，按加班费算。零食一大堆，几乎是给了最好的资源"。

除了资源支持和加快开发进度外，可灵的开发思路是："先不揪技术细节，粗糙一点没关系，做出来再优化。"

上述技术人员举了个例子："比如说我统计这个球落在桌子上，我先调研这个结果，并不深究它为什么会掉在桌子上。有些时候哪怕我对这个结果不是很满意，但是达到了可用的程度就先用。"

而"猛"则是能用"钞能力"解决的绝不多耽误时间。"10个工程师做一天的活，花10万块钱也能做的话，就直接花钱，保证速度。"

在"快、糙、猛"的执行战略下，从3月份到6月份，仅仅3个月的时间，可灵就能够面向公众正式发布。


1

**为什么是快手？**

一个公司想要快速发布一个模型的必备条件包括：有足够的多足够干净的数据、有够强的算法大牛和团队和有足够多的卡，而这三个恰好快手都具备。

这样也就不难理解，为什么是快手先做出了中国版Sora。

而更重要的是，可灵之所以被定义成快手集团战略级的产品，可灵最关键的任务并不仅仅是抢一个时间窗口或者纯粹的面向C端成为一款创作工具。可灵拥有着快手的生态力量而诞生，也将服务于快手生态。

据知情人士透露，在快手内部，打造可灵的目的有两个：一是服务于快手的内容生态。快手内部推断AIGC时代下的短视频产品将与现在的产品形态完全不同，可灵只是探索的第一步。同时能够对现有快手的原创内容生态做补充。

快手大数据研究院的数据显示，2020年快手内容创作者比例为26%、2021年内容创作者比例为25%，呈微弱的下降趋势，但在2022年以后的年度数据报告中，便没有披露这一数据维度。据硅星人观察，可灵上线后，迅速出现了一大批新的"AI创作者"，他们通过使用可灵生成好玩的创意视频，在快手和抖音中快速起号，部分创作者推测，可灵生成的视频内容可能会有一些流量倾斜。

除了对原创内容进行补充和盘活创作者生态外，另一个重要的目标，是服务快手的电商生态。

早在内测期间，快手不仅面向C端发出了内测申请，更将可灵的内测名额给了电商合作比较频繁的MCN机构如遥望科技和大品牌。

"电商行业的各个平台，都面临着素材不够用这样的痛点。你让一个人跳舞可能比较难，但是展示一个杯子的视频素材是很简单的，图生视频很容易就做到了。"可灵团队的技术人员告诉我们。

WAIC中，快手也首次公开了可灵的用户数据：截至2024年7月5日，可灵大模型上线一个月以来，累计申请用户数超过50万，开通用户数超过30万。

不过，大规模用户涌入之后，新一轮的压力也来了。

我们发现，即便可灵已经在7月6日宣布了全面公测，但是新用户注册仍然需要提交审核等待结果。当大规模的用户涌入对算力成本、能源的成本消耗比预想的要大很多。

同时当我们测试同一张图片生成的效果也并不是很稳定，对于此，上述技术人员讲道："可灵背后其实有很多个模型，效果最好的模型受资源限制，还无法给每个用户使用。"

据一位参与内测的创作者透露，他使用的模型版本是快手性能更佳的内部版本，也侧面证明了这一点。

正如同任何一场游戏的前两分钟都不可能决定比赛的胜负一样，可灵也只是快手技术长跑的开始。

[](http://mp.weixin.qq.com/s?__biz=MzkyNjU2ODM2NQ==&mid=2247582720&idx=1&sn=bcc835a1d8fb56d868f2fb22f1e80fe7&chksm=c2369ec2f54117d45cbb326aa56910f955a99516b95c9bf5a7f70403f0b713ea1cfdb7d9c436&scene=21#wechat_redirect)[](http://mp.weixin.qq.com/s?__biz=MzkyNjU2ODM2NQ==&mid=2247582137&idx=1&sn=0c392a36583ef78e6df411a739339966&chksm=c2369b7bf541126dd41e64dcd33d53e25e868435c5848e3a219ac33bd9d40c094650cc993d1a&scene=21#wechat_redirect)[](http://mp.weixin.qq.com/s?__biz=MzkyNjU2ODM2NQ==&mid=2247581558&idx=1&sn=c58cf863048ca8c4756558fbe8cd7aa6&chksm=c236a5b4f5412ca2930bea1361f843cdd4632c93f1ce4fd39414f514f978dfaddc557941f6d4&scene=21#wechat_redirect)点个"**在看** "，再走吧

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7213867617205882101)
