专访 Luma AI 首席科学家：我们更相信多模态的 Scaling Law
======================================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/waH6Vudo2uybXQZ8S4dwsQ)拾象 海外独角兽


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5icqrVQWfNIIChgAYicnooXQ1fFax6FYL1QYwiadNoy3HbfAvKK7HSg4Uw%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)](https://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247507749&idx=1&sn=1403008340bbe16dff1b9fc2d5ae6eae&scene=21#wechat_redirect "https://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247507749&idx=1&sn=1403008340bbe16dff1b9fc2d5ae6eae&scene=21#wechat_redirect")

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5OcSiaofa2ibwyhF2w5MvX5DN7vJ27uAicjTaON8U8mtCJQC1F4Lbgv50Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5kZpLgH1zDIhdlYIgM6QzQI7nUxbbad5YpcvtV7zcRYVQ6aCN6wu49g%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)

嘉宾：Jiaming Song

访谈：penny，Cage，Kefei


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5RTOWRELNF9D6oBk3Hc9jCE6IEvyiavgKiaXDtV03NGeRicH0phGqJJGJw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


视频生成和多模态是今年发展最快的领域之一，Luma AI 在上个月推出的视频生成模型 Dream Machine 的惊艳程度，让 Luma 在一夜之间跻身视频生成头部玩家行列。

[**我们此前对 Luma 进行过深度研究**](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247504262&idx=1&sn=845508fbe7361e6caff51ec3c2a2fb33&chksm=ce9b6e18f9ece70edbeb112bc8a10784e18887061c93e269e2d12055c8e8cd5fc69947d56775&scene=21#wechat_redirect)，Luma 从 NeRF 起家，产品和研究主要集中在 3D 领域。**如今选择进入视频生成领域的原因是什么？3D 与视频生成又有哪些关系？Luma 未来业务重心会逐渐从 3D 转向视频还是多方向同时进行？**都是我们关心的重要问题。

海外独角兽邀请到了 Luma 的首席科学家 **Jiaming Song** **（宋佳铭）**进行了一次深度访谈，也是继我们首次覆盖 Luma 一年之后对公司情况进行一次更新。Jiaming 提到："视频其实是通往 3D 的一条路径。" Luma 在探索 3D 的过程中完成了对视频生成模型的训练，效果也超出团队预期。

Dream Machine 与其他视频生成模型相比，主要亮点在于生成的动作幅度更大。这是 Luma 从用户需求出发而重视的能力。此外，Dream Machine 在训练过程中，自然涌现出对物理世界的理解，对三维空间、深度、光的反射和折射，以及光在不同介质、不同材质中运行的效果等都表现突出。

**The Bitter Lesson**也是 Luma 愿意下注多模态模型的原因。语言数据的压缩比高，更早有效果，而视频和多模态 token 量远大于语言，可能会对模型起到更大作用。他们相信多模态的 scaling law 能让模型更好得理解世界。

在和 Jiaming 讨论中，我们还感受到 Luma 团队虽然有很多背景华丽的 researcher，但除了看见未来并实现未来的技术能力外，团队对产品和市场的敏捷度也在提高。AI researchers 在尽力从提升模型能力的角度去满足产品和用户需求的同时，产品团队也在从产品角度把模型的表现形式做得更好。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5LiceAHENgJaia8SMydfrchyu3FTxBeYIOM1zfQaQdd5TOt2HgicPl7CeQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

**💡** 目录**💡**

01 Luma 的 Dream Machine模型

02 视频是通往 3D 的更好路线

03 Luma 如何定义自己


**01.**  


**Luma 视频生成模型 Dream Machine**


**海外独角兽：****Luma 最近推出的视频生成模型 Dream Machine 引发很多关注，你在其中参与了哪些工作？可以介绍下这个模型吗？**

**Jiaming：**我在整个项目中主要做模型训练相关的工作，包括模型、系统等相对比较全栈的工作，也负责协调训练方面的工作流。Dream Machine 现在还是个比较初期的模型，我们选择了 DiT 架构，这也是大家的一个共识。

**在做 Dream Machine 时候，我们想做的一个市面上已有模型不一样的点，是让动作幅度更大。**因为我们觉得今天用户已经不想去看只是让图片稍微动一动、没什么大幅度动作的所谓视频模型了，所以想让动作变大。虽然这又会带来可控性问题，或者说在某些情况下不那么完美，但我们觉得能让模型动得更多，对用户体验很重要。剩下的问题可能跟 scale up 数据、模型规模关系更大。

**海外独角兽：** **让动作幅度变大这一点，是来自产品洞察，还是想解决某个技术难题？**

**Jiaming：**更多还是从产品需求考虑。我们可以选择让模型动得多或者少一点，如果动得少一点，可能就跟文生图模型更像，这就要做取舍。从设计算法的角度来讲，没有太多特殊地方，最终落脚点还是"希望呈现一个什么样的model"。

**海外独角兽：** **如果想要把动作幅度做得更大，模型哪些部分最关键？**

**Jiaming：**更多是模型和数据规模驱动的。之前的模型从模型大小和训练数据上都相对欠缺，很难做到理想情况，或者说可以尝试去做，但效果完全不能看。大家比较保守的尝试方案是选择动作比较慢、没有太多镜头角度切换的一些视频。随着规模扩大，新的 feature 就会涌现。

**海外独角兽：** **和之前的视频生成模型，比如 Sora、Pika、Runway 相比，Dream Machine 有哪些不一样？**

**Jiaming：** **我们的方案和 Pika 可能不太一样，应该和 Sora、Runway Gen-3 比较类似，和 Sora 关联性更强一点，**都是 diffusion transformer 的架构。

**Sora 可能类似视频模型的 "ChatGPT Moment"，大家意识到这个方向是可以大力出奇迹的，接下来就是要行动。**和 language model 发生过的事很类似，大家以前还会对 Bert、GPT 存在一些争论，现在不少人还会继续做 language model 的底层架构研究，但整体已经 converge 到 transformer 架构，我觉得视频也基本上会往这个方向演进。

**海外独角兽：** **Dream Machine 发布后，你们观察到的 use case 主要集中在哪些场景？长期来看你们希望主要给用户提供什么样的价值？**

**Jiaming：** **我们目前主要还是 to C 的产品形态，这是出于需求量考虑，我们也希望更多人用到这个产品，但与此同时我们也收到很多关于 API 的需求，所以 to B 场景也存在一些可能性。**未来具体的产品形态今天还比较难预测，因为比较依赖于实际模型能力，以及市场的反馈。


**02.**  


**视频是通往 3D 的**

**更好路线**


**海外独角兽：** **Luma 之前一直做 3D 重建和 3D 生成，为什么现在要做视频生成？Luma 生成的视频空间感和物理呈现都很好，是因为 3D 的积累让视频生成效果更好吗？**

**Jiaming：** **我觉得这件事情可能是反过来的，我们是为了做更好的 4D，才选择做视频生成。**

我们在做 3D 时，意识到一些 3D 的方案，如果想把 3D 转成 4D （加上时间维度）会比较难做------现在比较明确的一个做 3D 生成的方案，是用大规模图片训练一个基础模型，再去做 fine-tuning，微调成一个多视角的 3D 模型，然后把它变成一个真正的 3D 场景。

如果我们想最终实现 4D，可能有两个路线，一种就是像刚说的那样，用图生成 3D，再把 3D 动画变成 4D，另一种是直接做一个视频模型，把视频模型再变成 4D。**我们觉得方案二更靠谱，所以即使不考虑视频生成本身的好处，只为了在 3D 领域更进一步，也是需要做视频的。**

沿着这个思路我们之前也针对一些 3D 场景对视频模型做微调，所以在 Dream Machine 之前，我们就已经搭建了一个视频转 3D 的 workflow。

**另一个直接原因是， 3D 数据相对于图片和视频的数据特别有限，所以需要依赖数据更多的大模型来驱动。**

**因此，我们最初的 motivation 不是从做 3D 这件事转向做视频，而是通过视频的方式去驱动更好的 3D。**

**海外独角兽：** **怎么理解通过视频的方式来驱动更好的 3D？**

**Jiaming：** 其实我们一直在用视频模型做一些测试，一开始没太期待模型的 3D 生成能力，结果发现视频生成 3D 的能力已经很强了，出乎我们意料。关键点在于，这个视频模型本身的 3D 一致性，以及和图形管线相关的、大家会关心的一些光学的东西，它都 follow 的不错。当然这个东西不完美，可能在跳体操这类例子上就会出问题，但现在能做的 feature 还是比较惊艳的。因为我们是 3D 背景，大家会更关注一些 3D 相关的 feature，发现 3D 一致性、光学、深度、一些动态的物理现象视频也是可以做的。

我们有一个例子是，把一个图片丢进 dream machine，直接转成一个视频，再把视频丢到我们之前就有的一个视频转 3D 的工作流里，直接就能做交互，效果非常惊艳。这肯定不是最理想的管线，但这个例子说明这个管线还比较 promising，这也回到刚说的那个点，**视频可能是更好的实现 3D 的路线。**

视频加载失败，请刷新页面再试

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACIAAAAqCAMAAADhynmdAAAAQlBMVEUAAACcnJycnJycnJyoqKicnJycnJycnJycnJycnJyfn5%2BcnJydnZ2enp6kpKSdnZ2cnJyenp6cnJycnJycnJybm5t8KrXMAAAAFXRSTlMAyeb3CNp3tJRvHIEtJhBgqztWRJ%2Bp5TqGAAABCklEQVQ4y5WTi27DIAxFAUMhgTzX8%2F%2B%2FurB2pdKI0x0pSoRuruyLbf7gF3PBaDE6X44LyY0D1SJQsfd9PpMM%2FCJx60v8SmV1HMSi1lKyA1n0jnwWSO08l04uJbxpBmTrpDtbGB6fmxC6Tc4BHv9aZDJdJsHW9w43Jez9x8T5M4l31WZsJn2bsYY%2BnUum2lQkGIVANPZ4FCLWOJImSTgjZE2SkU9crmu57mj9JBc93Qzj9R1d3HSG5bN5MRsnUzcGKK8Ns02z%2BDa7rYQE4bUE2PG1C6kVnkCyf0pwX8%2FjwbyxCLhcHpKTFkvkwK3pRmXtRrVFoTGYLvN%2Bt0EUl0qrRaF1pFBz0anp%2FptvNB4SY1XDAVMAAAAASUVORK5CYII%3D) 刷新

Created by @Theop-Luma

3D 的 case 是技术上比较有意思的点，并不是每次都能成功，成功的时候很惊艳，不成功有时候是因为我们对视频镜头的焦距，以及镜头的状态假设没有设定得特别死，这并不是一个 100% 能成功的工作流，但它能做到这个 case 已经是视频模型相比传统方案更惊艳的一个点。

**海外独角兽：** **你提到的这些生成视频中惊艳的效果有哪些，是否能给我们详细介绍和展示一下？**

**Jiaming：**第一，只看视频就能学习到所谓的深度知识。以前在 3D 领域大家比较关心深度，就是预测这个物体距离镜头有多深。在文生图阶段就已经有人尝试做这件事，比如有一篇很出名的文章 MVDream 做的内容是直接用文生图模型作为一个起点，再把它微调到一些深度数据中，结果发现不需要加很多深度数据，模型已经效果很好。

今天的视频模型不需要我们再做特殊处理，也不需要加入深度等3D相关的数据，只通过学习视频数据就能学习到深度知识、知道视频里面物体的远近，这也是深度的一种涌现方式。甚至不仅真实的图片能产生好的效果，**即使是一些非常抽象的图片，比如毕加索风格的图片，**效果也很好。

下面是把一张非常抽象的旋转木马图片放进视频模型中，模型生成的视频依然能模拟旋转木马的旋转状态，这说明即使是抽象的图片，模型也能理解关于深度的信息。

视频加载失败，请刷新页面再试

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACIAAAAqCAMAAADhynmdAAAAQlBMVEUAAACcnJycnJycnJyoqKicnJycnJycnJycnJycnJyfn5%2BcnJydnZ2enp6kpKSdnZ2cnJyenp6cnJycnJycnJybm5t8KrXMAAAAFXRSTlMAyeb3CNp3tJRvHIEtJhBgqztWRJ%2Bp5TqGAAABCklEQVQ4y5WTi27DIAxFAUMhgTzX8%2F%2B%2FurB2pdKI0x0pSoRuruyLbf7gF3PBaDE6X44LyY0D1SJQsfd9PpMM%2FCJx60v8SmV1HMSi1lKyA1n0jnwWSO08l04uJbxpBmTrpDtbGB6fmxC6Tc4BHv9aZDJdJsHW9w43Jez9x8T5M4l31WZsJn2bsYY%2BnUum2lQkGIVANPZ4FCLWOJImSTgjZE2SkU9crmu57mj9JBc93Qzj9R1d3HSG5bN5MRsnUzcGKK8Ns02z%2BDa7rYQE4bUE2PG1C6kVnkCyf0pwX8%2FjwbyxCLhcHpKTFkvkwK3pRmXtRrVFoTGYLvN%2Bt0EUl0qrRaF1pFBz0anp%2FptvNB4SY1XDAVMAAAAASUVORK5CYII%3D) 刷新

Created by @simonxxo,@ring_hyacinth


第二，除了深度，**光的反射、折射，以及光是如何在不同介质中运行，**视频也能理解。下面展示几个例子：

视频加载失败，请刷新页面再试

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACIAAAAqCAMAAADhynmdAAAAQlBMVEUAAACcnJycnJycnJyoqKicnJycnJycnJycnJycnJyfn5%2BcnJydnZ2enp6kpKSdnZ2cnJyenp6cnJycnJycnJybm5t8KrXMAAAAFXRSTlMAyeb3CNp3tJRvHIEtJhBgqztWRJ%2Bp5TqGAAABCklEQVQ4y5WTi27DIAxFAUMhgTzX8%2F%2B%2FurB2pdKI0x0pSoRuruyLbf7gF3PBaDE6X44LyY0D1SJQsfd9PpMM%2FCJx60v8SmV1HMSi1lKyA1n0jnwWSO08l04uJbxpBmTrpDtbGB6fmxC6Tc4BHv9aZDJdJsHW9w43Jez9x8T5M4l31WZsJn2bsYY%2BnUum2lQkGIVANPZ4FCLWOJImSTgjZE2SkU9crmu57mj9JBc93Qzj9R1d3HSG5bN5MRsnUzcGKK8Ns02z%2BDa7rYQE4bUE2PG1C6kVnkCyf0pwX8%2FjwbyxCLhcHpKTFkvkwK3pRmXtRrVFoTGYLvN%2Bt0EUl0qrRaF1pFBz0anp%2FptvNB4SY1XDAVMAAAAASUVORK5CYII%3D) 刷新

Created by @daken_ and @gravicle


在这个视频中，背景里有一个红色的霓虹灯，当镜头移动时，人背后的光影颜色的深度和光影覆盖的区域大小会改变。同时，当镜头移动时，这个人戴的眼镜与人脸的距离、镜片的厚度等等都会随之调整。再有，塑料材质基于光的反射，在传统意义上也不是那么容易去模拟，但这个视频表现出来的效果，包括一致性都很不错。

视频加载失败，请刷新页面再试

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACIAAAAqCAMAAADhynmdAAAAQlBMVEUAAACcnJycnJycnJyoqKicnJycnJycnJycnJycnJyfn5%2BcnJydnZ2enp6kpKSdnZ2cnJyenp6cnJycnJycnJybm5t8KrXMAAAAFXRSTlMAyeb3CNp3tJRvHIEtJhBgqztWRJ%2Bp5TqGAAABCklEQVQ4y5WTi27DIAxFAUMhgTzX8%2F%2B%2FurB2pdKI0x0pSoRuruyLbf7gF3PBaDE6X44LyY0D1SJQsfd9PpMM%2FCJx60v8SmV1HMSi1lKyA1n0jnwWSO08l04uJbxpBmTrpDtbGB6fmxC6Tc4BHv9aZDJdJsHW9w43Jez9x8T5M4l31WZsJn2bsYY%2BnUum2lQkGIVANPZ4FCLWOJImSTgjZE2SkU9crmu57mj9JBc93Qzj9R1d3HSG5bN5MRsnUzcGKK8Ns02z%2BDa7rYQE4bUE2PG1C6kVnkCyf0pwX8%2FjwbyxCLhcHpKTFkvkwK3pRmXtRrVFoTGYLvN%2Bt0EUl0qrRaF1pFBz0anp%2FptvNB4SY1XDAVMAAAAASUVORK5CYII%3D) 刷新

NeRF-based algorithm: 100 images

视频加载失败，请刷新页面再试

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACIAAAAqCAMAAADhynmdAAAAQlBMVEUAAACcnJycnJycnJyoqKicnJycnJycnJycnJycnJyfn5%2BcnJydnZ2enp6kpKSdnZ2cnJyenp6cnJycnJycnJybm5t8KrXMAAAAFXRSTlMAyeb3CNp3tJRvHIEtJhBgqztWRJ%2Bp5TqGAAABCklEQVQ4y5WTi27DIAxFAUMhgTzX8%2F%2B%2FurB2pdKI0x0pSoRuruyLbf7gF3PBaDE6X44LyY0D1SJQsfd9PpMM%2FCJx60v8SmV1HMSi1lKyA1n0jnwWSO08l04uJbxpBmTrpDtbGB6fmxC6Tc4BHv9aZDJdJsHW9w43Jez9x8T5M4l31WZsJn2bsYY%2BnUum2lQkGIVANPZ4FCLWOJImSTgjZE2SkU9crmu57mj9JBc93Qzj9R1d3HSG5bN5MRsnUzcGKK8Ns02z%2BDa7rYQE4bUE2PG1C6kVnkCyf0pwX8%2FjwbyxCLhcHpKTFkvkwK3pRmXtRrVFoTGYLvN%2Bt0EUl0qrRaF1pFBz0anp%2FptvNB4SY1XDAVMAAAAASUVORK5CYII%3D) 刷新

Dream Machine: 1 image

这个咖啡机的例子，上下两个我们用传统 NeRF 和视频生成做了对比。如果用传统 NeRF 去做，需要围绕咖啡机周围采集上百张图片，才能得到比较好的 3D 重建效果。但同样的咖啡机，今天把一张图片放进视频模型中，它就能够很好地模拟咖啡机的钢铁材质，包括光在钢铁材质上的反射。这实际上就可以是一张图片转视频再转成 3D 的工作流，这样的工作流比此前采集上百张图片、用 NeRF 的方式进行重建要方便得多。

视频加载失败，请刷新页面再试

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACIAAAAqCAMAAADhynmdAAAAQlBMVEUAAACcnJycnJycnJyoqKicnJycnJycnJycnJycnJyfn5%2BcnJydnZ2enp6kpKSdnZ2cnJyenp6cnJycnJycnJybm5t8KrXMAAAAFXRSTlMAyeb3CNp3tJRvHIEtJhBgqztWRJ%2Bp5TqGAAABCklEQVQ4y5WTi27DIAxFAUMhgTzX8%2F%2B%2FurB2pdKI0x0pSoRuruyLbf7gF3PBaDE6X44LyY0D1SJQsfd9PpMM%2FCJx60v8SmV1HMSi1lKyA1n0jnwWSO08l04uJbxpBmTrpDtbGB6fmxC6Tc4BHv9aZDJdJsHW9w43Jez9x8T5M4l31WZsJn2bsYY%2BnUum2lQkGIVANPZ4FCLWOJImSTgjZE2SkU9crmu57mj9JBc93Qzj9R1d3HSG5bN5MRsnUzcGKK8Ns02z%2BDa7rYQE4bUE2PG1C6kVnkCyf0pwX8%2FjwbyxCLhcHpKTFkvkwK3pRmXtRrVFoTGYLvN%2Bt0EUl0qrRaF1pFBz0anp%2FptvNB4SY1XDAVMAAAAASUVORK5CYII%3D) 刷新

Created by @hyperparticle

这个例子展示的是高速动态场景下保持物体的一致性，并且在高速状态的的镜头移动和切换的模拟效果也很不错。对于远处的物体，或者道路它的 simulation 还不太完美，但我觉得通过 scale up 模型大小是可以解决的。

视频加载失败，请刷新页面再试

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACIAAAAqCAMAAADhynmdAAAAQlBMVEUAAACcnJycnJycnJyoqKicnJycnJycnJycnJycnJyfn5%2BcnJydnZ2enp6kpKSdnZ2cnJyenp6cnJycnJycnJybm5t8KrXMAAAAFXRSTlMAyeb3CNp3tJRvHIEtJhBgqztWRJ%2Bp5TqGAAABCklEQVQ4y5WTi27DIAxFAUMhgTzX8%2F%2B%2FurB2pdKI0x0pSoRuruyLbf7gF3PBaDE6X44LyY0D1SJQsfd9PpMM%2FCJx60v8SmV1HMSi1lKyA1n0jnwWSO08l04uJbxpBmTrpDtbGB6fmxC6Tc4BHv9aZDJdJsHW9w43Jez9x8T5M4l31WZsJn2bsYY%2BnUum2lQkGIVANPZ4FCLWOJImSTgjZE2SkU9crmu57mj9JBc93Qzj9R1d3HSG5bN5MRsnUzcGKK8Ns02z%2BDa7rYQE4bUE2PG1C6kVnkCyf0pwX8%2FjwbyxCLhcHpKTFkvkwK3pRmXtRrVFoTGYLvN%2Bt0EUl0qrRaF1pFBz0anp%2FptvNB4SY1XDAVMAAAAASUVORK5CYII%3D) 刷新

Created by@valleeduhamel

这个 case 核心是后面的布料模拟，传统意义上游戏管线里的布料模拟计算成本很高，因此大家不会做得太复杂。但用视频模型就可以在成本较低的情况下模拟得很好、很真实，包括布料的材质和光影都模拟得很好。

视频加载失败，请刷新页面再试

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACIAAAAqCAMAAADhynmdAAAAQlBMVEUAAACcnJycnJycnJyoqKicnJycnJycnJycnJycnJyfn5%2BcnJydnZ2enp6kpKSdnZ2cnJyenp6cnJycnJycnJybm5t8KrXMAAAAFXRSTlMAyeb3CNp3tJRvHIEtJhBgqztWRJ%2Bp5TqGAAABCklEQVQ4y5WTi27DIAxFAUMhgTzX8%2F%2B%2FurB2pdKI0x0pSoRuruyLbf7gF3PBaDE6X44LyY0D1SJQsfd9PpMM%2FCJx60v8SmV1HMSi1lKyA1n0jnwWSO08l04uJbxpBmTrpDtbGB6fmxC6Tc4BHv9aZDJdJsHW9w43Jez9x8T5M4l31WZsJn2bsYY%2BnUum2lQkGIVANPZ4FCLWOJImSTgjZE2SkU9crmu57mj9JBc93Qzj9R1d3HSG5bN5MRsnUzcGKK8Ns02z%2BDa7rYQE4bUE2PG1C6kVnkCyf0pwX8%2FjwbyxCLhcHpKTFkvkwK3pRmXtRrVFoTGYLvN%2Bt0EUl0qrRaF1pFBz0anp%2FptvNB4SY1XDAVMAAAAASUVORK5CYII%3D) 刷新

Created by@next_on_now

这个例子展示的是不同场景的关联性。可以看到这个小女孩的表情是比较惊恐的，她之所以会有惊恐的表情，是因为在前一帧展现的是她看到一个恐怖的东西。另外，小女孩的发型、裙子的颜色和样式在两个镜头中展现的都是一样的。这都是关联性的体现，也就是说在一个连续空间里，模型对于一些非连续的画面和场景也可以模拟。


💡


点击查看更多[Dream Machine 视频生成案例]()


除了上面的图生视频案例外，Dream Machine 生成中，也会有一些不完美的案例，下面是一些能体现出模型当前局限的例子：  

视频加载失败，请刷新页面再试

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACIAAAAqCAMAAADhynmdAAAAQlBMVEUAAACcnJycnJycnJyoqKicnJycnJycnJycnJycnJyfn5%2BcnJydnZ2enp6kpKSdnZ2cnJyenp6cnJycnJycnJybm5t8KrXMAAAAFXRSTlMAyeb3CNp3tJRvHIEtJhBgqztWRJ%2Bp5TqGAAABCklEQVQ4y5WTi27DIAxFAUMhgTzX8%2F%2B%2FurB2pdKI0x0pSoRuruyLbf7gF3PBaDE6X44LyY0D1SJQsfd9PpMM%2FCJx60v8SmV1HMSi1lKyA1n0jnwWSO08l04uJbxpBmTrpDtbGB6fmxC6Tc4BHv9aZDJdJsHW9w43Jez9x8T5M4l31WZsJn2bsYY%2BnUum2lQkGIVANPZ4FCLWOJImSTgjZE2SkU9crmu57mj9JBc93Qzj9R1d3HSG5bN5MRsnUzcGKK8Ns02z%2BDa7rYQE4bUE2PG1C6kVnkCyf0pwX8%2FjwbyxCLhcHpKTFkvkwK3pRmXtRrVFoTGYLvN%2Bt0EUl0qrRaF1pFBz0anp%2FptvNB4SY1XDAVMAAAAASUVORK5CYII%3D) 刷新

Created by @alexyu00,

Possibly inferred as shot change

这个例子前一秒钟看上去还算正常，但下一秒钟后面突然出现一块大石头，还多了一些闪电。这肯定不符合正常的物理原理。

视频加载失败，请刷新页面再试

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACIAAAAqCAMAAADhynmdAAAAQlBMVEUAAACcnJycnJycnJyoqKicnJycnJycnJycnJycnJyfn5%2BcnJydnZ2enp6kpKSdnZ2cnJyenp6cnJycnJycnJybm5t8KrXMAAAAFXRSTlMAyeb3CNp3tJRvHIEtJhBgqztWRJ%2Bp5TqGAAABCklEQVQ4y5WTi27DIAxFAUMhgTzX8%2F%2B%2FurB2pdKI0x0pSoRuruyLbf7gF3PBaDE6X44LyY0D1SJQsfd9PpMM%2FCJx60v8SmV1HMSi1lKyA1n0jnwWSO08l04uJbxpBmTrpDtbGB6fmxC6Tc4BHv9aZDJdJsHW9w43Jez9x8T5M4l31WZsJn2bsYY%2BnUum2lQkGIVANPZ4FCLWOJImSTgjZE2SkU9crmu57mj9JBc93Qzj9R1d3HSG5bN5MRsnUzcGKK8Ns02z%2BDa7rYQE4bUE2PG1C6kVnkCyf0pwX8%2FjwbyxCLhcHpKTFkvkwK3pRmXtRrVFoTGYLvN%2Bt0EUl0qrRaF1pFBz0anp%2FptvNB4SY1XDAVMAAAAASUVORK5CYII%3D) 刷新

Created by @gravicle


多头问题也是模型的一个局限性。3D 里面也常常出现多头问题，是之前大家需要通过文生图模型去生成 3D 的时候，会存在比较多类似问题，尤其是当动作幅度较快时，多头问题就容易出现，Janus 是希腊神话里一个有很多脸的神，所以大家把多头问题称为 Janus。


💡


点击查看[更多案例]()


最后再提一下关于如何通过视频模型去做 4D 的一个展望，一个简单的思路是去收集多视角的视频数据，这些数据也许可以把当前的视频模型优化成一个多视角的视频模型，再利用多视角视频模型生成的数据去生成 4D 事件。

**海外独角兽：** **感谢展示，这些 Dream Machine 输出的视频质量都很高，不管是清晰度、动作幅度，还是镜头的深度、光线等。**

**Jiaming：**我还有一些其他例子没有放，因为这里所有的例子都是用户生成的，需要credit，需要联系作者获得允许才能放。有些我觉得非常好的例子，因为没有联系到他们，不能放出来。

**海外独角兽：** **对于视频生成的效果，是否有一个 evaluation 框架？是否能对特定方面针对性提升？**

**Jiaming：**现在大家做 evaluation 的方法，更多还是基于人的体验。提升肯定是可以做的，因为 Dream Machine 还是个比较早期的产品，所以有很多明显的问题是接下来可以被迭代的。提升可以从不同角度，比方说和数据相关的，就主要提升数据；和模型本身效率更相关，就要提升模型架构。

**海外独角兽：** **这些例子里，镜头对物理世界的理解，是模型自然而然学到的，还是你们专门做了很多工作？**

**Jiaming：**我们没有针对这个事情做什么东西，这也是为什么它比较神奇的点。

**海外独角兽：** **围绕视频生成，整个社区也开始讨论 World Model、World Simulator 的概念，在做 Dream Machine 的时候，你们也发现 3D 是意料之外的能力涌现。未来 3D 和视频生成会取代今天的光学计算、图形学吗？**

**Jiaming：**有些管线是可以帮助的，比如毛发模拟、布料模拟这种计算量很高的东西相对来说就比较合适，但如果是做传统的人脸渲染，不涉及头发，必要性不一定那么大，甚至今天头发模拟也已经做得很不错了，所以还要看具体的场景。如果想要去整体替代图形学还有不小的距离，但是可能可以用来辅助一些图形学的管线。

**海外独角兽：** **视频生成模型要实现 World Model、理解世界物理规则，是一个会随着模型的 scaling up 涌现的过程，还是需要我们对模型本身进行升级改造？**

**Jiaming：** 我觉得前者的可能性更大，这其实也和 scaling law，我们说的 **"Bitter Lesson"**有很强的相关性。

**Bitter Lesson**是 Richard Sutton 提出来的，他是强化学习领域的泰斗级人物，大部分时间都在研究算法，怎么用算法的方式提高模型训练效率。2019 年的时候他说过一句话：**从历史进程来看，一般来说简单但是能更好利用计算量的方法，在长期来讲会优于加入人类先验知识但是计算量比较少的方法。**

Richard Sutton 当时举的例子是 AlphaGo，围棋 AI 在用 deep learning 之前还是下不过人类的，随着 AlphaGo、AlphaZero 出现，大家才开始觉得围棋这个问题被解决了。但是它的一个区别是，更多先验的设计，即以前会基于人类先验的一些算法，可以更好地利用计算的算法去突破。

**语言模型也是类似，大家花了这么多时间去研究 language model、language understanding，做了很多语法、分词、情感分析、段落整理的任务，结果发现只要计算量上来，很多任务 language model 都能做。**

我觉得 Video model 也有这个发展趋势。以前针对每个图像学问题，我们都需要单独去设计一套方案解决，基于先验经验去做，这样确实能做得不错，但确实有它的上限。在这个过程中，我们也发现对于一些相对复杂的情况，有的时候用 scaling up、用计算量更高的思路，对于它的长远发展可能会有更好的突破。现在还不能说视频模型已经完全比图形学好，但至少已经看到比较有前景的一些观测。

回到更复杂的物理 simulator，我觉得也是类似的情况，**随着计算资源的增多，大家可能也会发现视频模型有类似涌现的现象，现在解决不了的问题也就自然而然解决了** **。**

**海外独角兽：** **从研究进展到大家能用的最终效果上来说，是否存在某些问题属于即使模型 scaling up 也特别难解决的？**

**Jiaming：**很多现在看起来不是很容易解决的问题，可能随着范式迁移，随着做法或者思路转变，加上更多的计算，都可以得到不错的解决方案。当然现在这些 model 都有各种各样的局限，但现在对于视频模型、3D 以及可控性的解决还是一个非常初期的阶段，往后总是可以往上加一些 feature 的。

**海外独角兽：** **过去一年有不少公司都做视频生成的模型，有 Runway、Pika、快手可灵等等，Luma 来做视频生成，跟这些公司相比最大的优势或者区别是什么？会有不同的技术路线吗？**

**Jiaming：** 从技术路线角度来讲，接下来要做的事情其实是**生成速度以及生成效率的优化。**

生成速度一是跟成本挂钩，二是跟用户体验相关，我觉得**用户体验带来的影响比成本更重要。**因为从成本来看，只要我卖一个视频的价格比生成成本高，我总可以赚钱，但是这里面不一定能够产生太多的新东西。

但假设我们现在有一个视频模型，它生成 5 秒钟视频只需要 5 秒，这里面可以做的事情就比我们现在能做的事情多很多，首先它可以去 serve 更多用户，其次是用户体验也会变得不一样。**我自己未来比较期待的一个点是我们在效率上有很大的提升，如果能做出来，可以开发一些新的产品思路。**

另外一个点也是大家比较老生常谈的，就是对可控性，或者说可编辑性的期待。快手可灵的例子可以说明，在大家已经知道 ChatGPT moment 和 scaling law work 的情况下，国内做模型的能力是很强的，大家都做得很好，给了市场一些强心剂。

不过我们和快手的市场不太一样，从市场的角度来讲可以有两种解读，第一种是根据现在 model 去创造什么样的产品，另外一种解读，是根据未来 model 的趋势能去研发哪些新产品？后者是更值得期待的。

**视频模型现在相当于 language model 赛道刚做出来 ChatGPT 的阶段，往后还有很长一段增长空间。**继续去 improve model 能力肯定是很重要的，包括可控性以及生成速度，因为生成速度影响 business model，但是单纯提升速度可能不够，因为我总可以堆更多的 GPU 去提升生成速度，如果堆了更多 GPU，并没有节省 cost。所以最终的 business model 可能还不太一样。

之后我们也会期望做一些跟现在大家做的不太一样的事情、内容或者思考。**当下模型和产品都很重要，如果没有 model，就是套壳公司，如果没有产品，那可能就变成 model serving 公司，最终还是跟大家卷成本。我们是一个 model 和产品两方面人数差不多的公司，我们会通过用户需求和我们对未来产品的 vision 去导向。有时候我们的产品思路不一定是现在大家觉得非常靠谱的，但是在模型相对成熟的时候，就会变得 mature。**

**海外独角兽：** **有观点认为，成本是 Sora 至今都没有真正开放给大众用户的重要原因，但 Luma 的 Dream Machine 一发出来大家都能用到，并且体验也很好，你们是怎么解决成本问题的？多模态模型是否也和 language model 一样，存在一个成本下降和能力升级之间明确的变化规律？**

**Jiaming：**关于 Sora 没有办法猜具体是什么原因，成本可能是众多原因中的一个，但他们可能也在一定程度上有产品方向上思考，比如他们需要思考 Sora 怎么跟 OpenAI 已有的产品结合，比如像 Dall-E 3 这样整合到现有的产品里，还是做一个独立产品等等。

**我个人觉得大家最后都会把成本降下来，下降多少倍不一定确定，但是一定能够下降，并且一定能产生一些新的应用状态，我自己很相信这件事一定会发生，**所以如果我们预期会有这样的未来，那么可能我们对于产品或者对于模型的一些思考，也会跟这个预期挂钩，跟大家做投资或者买股票一样，其实很多时候大家做的其实是对预期的一个判断，并不是对现在时的判断。

**海外独角兽：** **从生成效率提升、成本下降一定会发生的角度看，除了要增加 GPU，还需要做哪些准备？**

**Jiaming：**算法创新肯定是需要的，现在有很多东西并不像 LLM 探索得那么透彻，但是随着大家去研究更多方案，算法的创新肯定可以做得更好。

**海外独角兽：** **Luma 未来的重心会因为视频模型的表现超过预期发生变化吗？你们接下来要如何在探索视频生成和 4D 这两个方向做平衡？**

**Jiaming：** 我觉得这两件事并不彻底冲突，我们最终要实现的目标就是**多模态的理解和生成一起做。** 从数据角度来讲，视频数据比文字数据的 token 量多很多，我们当时做了一个预测，**不管是从数据集的 size 还是 token 的数量看，多模态模型都是现在最大文本预训练模型的百倍以上。**现在原生文本数据已经枯竭了，大家一方面在做合成数据，另一方面把 model size 不断提高。如果 model size 无限提高，也会有 cost 的问题。

从多模态的角度来讲，因为多模态信号的数据量很多，scaling law 会更倾向于数据，可能不需要那么大的模型去 scale up，就可以达到不错的效果。

这里还值得再提一遍**Bitter Lesson，** **它的核心是少用人类的先验，多用数据、多用计算。一定程度上，我们可以认为人类语言其实也是人类的某种先验，**因为不同的人说的语言都不太一样，并不影响大家去理解物理世界、在这个世界里面做操作。

一定程度上语言本身也是对于这个世界所展示现象的一种压缩或者先验。因为语言是可以利用更多先验的点，它压缩率比较高，所以它利用计算的效率会比较高，那么它肯定会先起飞，大家在语言领域先做出成果，就像大家之前用搜索在象棋中做出成果，然后围棋做不出成果一样。之前大家普遍认为语言做出成果，视频不一定做出成果。

但随着数据量提高，对于世界的理解也会随着多模态 token 的数量提高而超越之前 language model 所能够达到的能力。当然 language 的重要性还是有的，并不是说完全甩掉 language，让 model 自己去开发新的语言。但我用这个类比是想说明，**我们比较相信未来是以多模态为主的发展趋势，这个模态具体是视频、4D、语言、action 或是其他等等，相对来说不那么重要。**

**海外独角兽：** **多模态数据确实在很多 researcher 看来都很重要，现在也有观点认为，我们最易获取的视频数据都是经过精心剪辑、偏娱乐项的，很难帮助 AI 理解真实世界和人类的第一视角，不像语言那么好学。你怎么看？多模态数据的应用会存在哪些 bottleneck？**

**Jiaming：** 我觉得核心看应用场景。首先，多模态数据的量还远没有被cover，另外，多模态数据相对文本数据比较容易生成，比如做自动驾驶的时候只要增加摄像头，就能获得更多数据，但如果用文本生成数据，就需要人去写。低质量的数据容易写，但高质量的 fine-tune 数据，或教科书水平的数据，大家一整年也写不出太多，**从收集效率来讲，收集文本数据就比收集摄像头以及其他媒介的数据要** **慢一些。**

4D 多视角数据和 3D 数据也难收集。但也许可以开发出新的 idea，比如上面提到的从图像到视频再到 3D，这是一条可能解决数据问题的路径。

并且，在 4D 世界中，大部分也是视频输出，视频的可交互性更强。在 4D 世界我们也许可以直接用一个大模型去做这样的设置，但要求模型生成速度要更快，延迟要够低，这样就可以去做所谓的流处理。这些都是技术上的一些展望。

**海外独角兽：** **3D 生成有好几种技术路线，你们现在比较相信什么样的路线？**

**Jiaming：**我觉得从视频走到 4D 的路线相对更 promising，成功的可能性会大一点，但是也不排除有一些我们自己没有想到的路径被其他人想出来了。

**海外独角兽：** **你们之前发的 Gaussian Splatting 产品也很受关注，在 Gaussian 方向你们也做了一个可交互的场景，这块目前在你们的 research 方向和公司层面会是一个重点吗？**

**Jiaming：**这件事很依赖于这个领域本身的进展，很多文章在 CVPR 等会议上发，但实际上没有太多本质的突破。一方面因为大家精力有限，没有办法去把所有 idea 都试一遍。另一方面，在工业中考虑的问题和做 research 考虑的问题不太一样，比方说我们在 Gaussian 产品里面考虑更多的其实是用户采集数据质量的事情。例如用户的手机视频可能会有不同程度的模糊或者噪声，这跟之前学术中大家做的一些假设不太一样。

**海外独角兽：** **从学术角度来看，最近 Gaussian Splatting 比 NeRF 的热度还高一些，大家提到它在效率、质量等方面表现更好。从你们产品使用的角度来看，是否也有类似的感受？**

**Jiaming：**我个人感觉是的，因为 Gaussian Splatting 相比 NeRF，主要优势在于它在移动端或者网页端的渲染能力更强，但有的时候更不一定符合物理规律。而且 Gaussian Splatting 继承了 NeRF 的一些 idea。NeRF 是 2020 年出来，Gaussian Splatting 是去年比较火，对于学术界来说，追一些新的 idea 是正常的。

**海外独角兽：** **你刚刚提到，4D 的视频能带来多角度的数据，现在不管是自动驾驶还是机器人，其实也面临高质量数据缺失的挑战。未来做 4D 多视角是不是能够从根本上去解决这个问题？**

**Jiaming：**可能可以，但解决这个问题也可能不需要 4D 视角数据。从人的角度来讲，好像从来也不需要往脑袋里面注入一个 4D 视角数据，理论上人通过视频数据就可以学到所有 3D 相关的东西。人虽然能够理解世界中的 3D 物体，但是你让一个人去做 3D 建模，难度还是挺大的。


**03.**  


**Luma 如何定义自己**


**海外独角兽：** **大家会经常讨论一个公司到底是 research lab，还是做产品的公司，你自己觉得 Luma 属于哪一类？**

**Jiaming：** **我们既要有 research lab 的创新能力，看到未来并且实现未来的技术能力，也需要有产品的敏捷度，这两个少一个都不行，两边的重要性是一样的。**从我们 researcher 的角度来讲，肯定是尽力去填补产品需求和我们能实现的事之间的 gap。相反，去做传统的学术研究并不是我们的重点，但不管哪一种，大家遇到的挑战都是类似的，都是在解决一些前人没有解决的一些问题，所以这里面就是 research 的程度也很重要。

对于 Luma 来说，我们有一个背景是公司的 co-founder 以及早期同事都是从 Berkeley 或者 Stanford 出来的，大家很容易接触到优秀的 researcher，和这些人来讨论 ideas。产品的同学也很优秀，他们可以从产品的角度去帮我们把 model 的表现形式做得更好。

**海外独角兽：** **从团队角度看，做 Dream Machine 需要多大的团队，原来有一些做 3D、NeRF 的人转型容易吗？是否遇到人才上的挑战？**

**Jiaming：** 总共有十几个人参与 Dream Machine 模型，我觉得科研背景没有那么重要，工程能力是比较重要的，**有 3D 背景的人做工程的能力通常更强，所以团队能力上没有遇到太大问题。面临的更大挑战在于，你如何说服这些人做视频模型这件事，做一个新的、完全不一样的东西，重点其实是调动大家去做这个事，虽然已经有很多信号证明这件事值得做，但还是需要在内部来 align 这个目标。**

**海外独角兽：** **听起来更多是一个战略和组织的问题。谁是 Luma 内部最先、最强烈提出这个 idea 的人？**

**Jiaming：** 当时内部其实有好几个人都觉得这个事是要做的，所以也不是其中某一个人去主要 push。**3D 生成做得多了，自然而然会意识到视频生成的重要性。**当时做 3D 生成主要是我跟 CTO Alex 在做，我们两个对于生成模型的细节了解较多，所以对视频生成的认知也会相对更快一些。

**海外独角兽：** **Luma 之前很专注于做 3D ，今天又有了视频生成产品 Dream Machine，你们会把自己定义成一家什么样的公司？**

**Jiaming：** **我们没有定义自己是一家 3D 公司、视频公司，或者具体做某个赛道的公司。AI 发展很快，如果想要利用好更多的 value，需要有多角度的思考模式。**

相比于 language 的 scale up，我们会更相信 vision 或多模态的 scaling law，这当然有很多新的挑战，不管是模型产品形态，还是 API 应用的一些新的 idea。

现在的研究现在都还比较初期。我们之后想做的事更 general，理想更大。产品也很重要，不能只做模型。我们需要时刻意识到技术在发展，要根据用户反馈和技术发展趋势，去定义这个公司当下应该做什么。但我们整体还是 AI 背景，应该不会突然转型去做硬件。

**海外独角兽：** **从成本角度，如果做一个付费产品，现在的成本达到你们觉得可以去做 business model 的水平了吗？**

**Jiaming：** 我们现在的付费用户状况以及 ARR 都还不错。但从 AI 创业公司的逻辑来想，未必要在这个阶段就获得正现金流，市场也不希望你这么做。如果现在想做正现金流肯定是可以的，但对于公司今天的优先级来说，没有必要这么做。而且模型能力提升可能带来 business model 的变化，**几个月之后的展现形式可能跟现在我们看到的形式不太一样，**所以也没有必要拘泥于当下的 business model。

**海外独角兽：** **我们了解到，OpenAI 的 API 和 ChatGPT 的 Gross Margin 其实并不高，包括大家都在质疑 API 这个商业模式。很同意你说未来的收费方式可能会和现在不一样，比如说分层收费，或者把它真的当成是 agent 按照它创造的价值收费等等，这个可能是未来需要探索的。但是你们对于大的商业方向做 to C 还是 to B，现在也还没有很明确的想法吗？**

**Jiaming：** **用现在的 model 去想 to C 或者 to B 的商业模型，可能过了几个月有新的 model 之后，商业模式又变了。所以我觉得商业模式是计划没有变化快，现在的重点还是先把模型和产品做得更好。**我觉得大家不会质疑这个策略，因为有 OpenAI 的成功例子作为参考。在 ChatGPT 之前，他们几乎没有特别好的正向现金流，但这个产品一出现，大家的兴趣都被激发出来了，商业模式也很容易推广。我觉得多模态模型也是类似的情况，我们可能还需要再等一等。

**海外独角兽：** **多模态的生成未来也会是一个 end to end 模型吗？比如这换个可以生成图、视频、3D 甚至音频，更进一步，是不是能把理解和生成都放到一个模型中？**

**Jiaming：**我觉得应该是可以做的。

理解和生成放在同一个模型里，这件事已经有原型出现了，就是 Meta 的 Chameleon，虽然 Meta 做的更多是一个研究，它并没有 focus on 生成的一些特点。

但这个过程中要考虑的是，从效率看不确定是不是一个好的方案，可能要分场景去看，并不是所有场景都适合做通用模型，根据不同需求工程上也需要做一些取舍。

**海外独角兽：** **最近在 Vision Pro 和空间计算大家有很多尝试，这和你们在 3D 方向想做的事情会不会有一些耦合？**

**Jiaming：**我们之前也会思考这个问题，到底要不要做一个 Vision Pro 的 APP，后来因为现在 Vision Pro 的用户太少，还不值得去做，也许时机成熟的时候可以去做。

**从整个泛硬件角度来看的话，**不只 3D，4D 关系更大。因为大家 care 的很多应用场景，比方说虚拟场景交互，4D 都是必要的。只做 3D 可能会更偏向于 AR 的一些场景，目前来讲好像没有看到太好的商业场景。但如果 4D 能够做得很好，那就是一个质的飞跃。

**海外独角兽：** **你怎么看李飞飞的创业项目？他们也很强调"空间智能"，核心是让 AI 拥有视觉、进一步理解世界。**

**Jiaming：**我觉得他们的想法也挺有意思，团队背景也很强。我个人感觉他们跟我们不太一样的点在于他们的创始团队更多是 researcher，做工程和产品的人较少，有待观察。不过我自己的观点是，research 跟产品都是非常重要的部分。

至于技术路线，我并不知道他们具体的技术路线，但一般出现一个相对比较成熟的技术路线，大家就都会 converge，之所以大家会去做 transformer 或者 DiT，一定程度上是因为它有效。**不排除可能会有新范式，但目前我们还没有把已有的范式挖够，还能做不少东西。**有时候一个范式被成功验证之后，大家很快会去复现，research 方面大家都会交流，很难出现一个人或者几个人突发奇想，做出一个其他人都想不出来的 idea。

**之前从 GPT3 到 GPT4，大家所谓的追赶或者超越花了一年多的时间。但从 Sora 到可灵，或者 Dream Machine，其实中间也就过了大概 4 个月。我觉得如果有新的范式出现，接下来大家模仿的速度可能会更快。**当然这是假设，这个方案是一个相对来说简单的方案，这个如果是一个特别复杂的方案，可能它复现的难度会大很多。但是从 Bitter Lesson 的角度来讲，现在大体趋势还是更倾向于简单方案。

**海外独角兽：** **你自己现在最感兴趣的研究方向和最想突破的问题是什么？**

**Jiaming：**我最近比较感兴趣的方向，跟系统，或者说 transformer 本身的范式更相关。大家现在基本不否认 scaling law 会创造更多智能，但 transformer 本身随着 sequence 变长，它的二阶 performance 限制了 sequence length 的长度。如果有更有效的算法去解决这个 sequence 问题，会是个非常有意思的方案。

现在有一些基于 RNN 的方案，像 RNN RWKV Mamba，或一些基于线性 transformer 的方案，但好像最终在大规模实验中的效果都不如 transformer。**所以我觉得现在大家要去思考，如何能在保证之前 performance 的情况下，让 sequence length 从现在的百万级变成千万级或者亿级。**

我自己的一个深刻体会是，**任何问题乘以 10 或者乘以 2，解决方案都会变得非常不一样，无论从算法或者从系统上都需要重新设计一遍。**如果在这个领域能够实现更大的突破，那对于训练的效率和多模态理解，都会很有帮助。

第二个我关心的点是，对于现有的 transformer 或者 model 本身它们在做什么的理解，或者看这些 model 真的学到什么东西的一些理解，可以帮我们更好地理解或预测 scaling law，使得我们能够更加低成本或者高效率去训练模型。

**第三个我自己比较感兴趣，但是也比较难的一个点是，diffusion 的 scale，**相比于 Autoregressive，它的主要问题是它在一个连续空间。在信息论层面，连续空间跟离散空间的逻辑非常不一样，我不知道这是不是一个因果关系。但最后导致的一个情况是，你很难在 diffusion model 去算 perplexity，也不能去衡量 token 效率。很难像 language model 里面，你看到这个 loss 就知道它是什么样，我觉得现在 diffusion model 上大家有 scaling law 的意识，但是真正 scaling law 还是一个非常模糊的阶段，数学上真的还不太好做，如果有人能做出来还挺有意思的。

**海外独角兽：** **DiT 已经用了 transformer，是否某种程度上解决了 diffusion scale的问题？**

有一个常见的误解是， diffusion 跟 transformer 是并列概念。但其实他们并不是并列的概念，所以 DiT 的出现并不是说把两个不同的概念放在一起，只是说把一个之前在 autoregressive 被验证成功的方法用在 diffusion 的训练过程中。

类似的情况，我对于 transformer 这个结构的 improvement，或者我刚才所说的对于长序列理解的这个工作，在自回归模型上能做，在 diffusion 上应该也能做，这个模型架构的 idea 应该是互通的。但是 diffusion跟 autoregressive 一个是离散，一个是连续，他们的训练方式还有推理方式，还有 scaling law 本身是不一样的。

我们知道 diffusion 肯定有 scaling law 存在，只是我们找不到它这个系数，相当于说你要推一个定理，你需要搞一些常数，对吧？现在是我们认为常数存在，但我们并不知道这个常数是什么，大概是这样一个问题。

我觉得这也不是无法实现，只是现在有能力做的人没有功夫做，有功夫做的人可能没有足够资源做。很难说这个系数对实际生产作用有多深远的影响，但从 researcher 角度说，如果能把这个做得更好，训练这种 model 会更像科学而不是玄学。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5WKDLPwMcrphQ4AibeKX6nQWOEuAu9tWH7fhek0PvEesiaQSycTbxlL1A%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5RbHjb7CET5W0WJWzwhEQRob94tJ12s2VibBwbClNkD31MzF7Ll9iaszw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5NwNDvGtEpuC47XEr04tVPNr3ka51TfOibf7RTpgUP9SYePygRo7A6Dw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

排版：Doro


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5SvxRfQMOQJ1pGZWtHApFibrmDib6VjiaRVicUNB0pI9bUd9FqqRPshS4Ww%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)


延伸阅读


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5luDEFmUfTXBYxdf6zf8kECRGkKt7ct5YIaDImOjiavJG0O7kSVS0rTw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247508588&idx=1&sn=6f48ab2576f486b9365d9435c4d8c2e6&chksm=ce9b1df2f9ec94e437ee22ca0dc5d050b8a53b3e6df4c4442baf7ae293b54f4afc48414ccb64&scene=21#wechat_redirect)


AGIX ETF 上线：构建 AI-native 的投资工具


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5fYSWoicBKtbckTibdOEuq3oia25RFDP26ia6JqcHQ5V1YlE6csaLegd9Kg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5L6MhQCdBkd7Ir14rdZVnNZhnk5WibmrrXs1M9CEEJWrp5A3eZE6XzTg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247508533&idx=1&sn=97b7b0e0440164f45bda9a03d17ae806&chksm=ce9b1dabf9ec94bd32ba6ed939dca5b18c2c49632c6344ec6b117c54e743674e07b91a26bef8&scene=21#wechat_redirect)


10 万卡集群：通往 AGI 的新门票


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5fYSWoicBKtbckTibdOEuq3oia25RFDP26ia6JqcHQ5V1YlE6csaLegd9Kg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5micP9WSCgAgqVmNNk2WVoicy67C44I10cIkPytrDic4s92TiaMmnoKREQA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247508357&idx=1&sn=e00726dddc2ea74111fecb8faee23c86&chksm=ce9b1e1bf9ec970d937685132547a0f18157ae704ff581e97c05bf36136602f37ff44d84fb87&scene=21#wechat_redirect)


通用机器人是 AI 时代的新 "iPhone" 吗？


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5fYSWoicBKtbckTibdOEuq3oia25RFDP26ia6JqcHQ5V1YlE6csaLegd9Kg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5r6OgnM8mklEcGtKoC1jWcnFfH0bfUVa8iasGGqpfe5SNN1ThAZk8aUw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247508283&idx=1&sn=1a096e4d2f545784a749b1cc018a6043&chksm=ce9b1ea5f9ec97b3f0272d4ad0b58ada6db7fbca8013cd67269eaf5946145a26d090eeb6ba15&scene=21#wechat_redirect)


专访 LanceDB 创始人：多模态 AI 需要下一代数据基建


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5fYSWoicBKtbckTibdOEuq3oia25RFDP26ia6JqcHQ5V1YlE6csaLegd9Kg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5RLL6MXqQkHoFN39mibpV9dSDKj8iabwkaoTRsg1NcXPGMiaWbpAAYI7TA%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg2OTY0MDk0NQ==&mid=2247504262&idx=1&sn=845508fbe7361e6caff51ec3c2a2fb33&chksm=ce9b6e18f9ece70edbeb112bc8a10784e18887061c93e269e2d12055c8e8cd5fc69947d56775&scene=21#wechat_redirect)


Luma AI 会是3D领域的Midjourney吗？


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2F3tHNibnJ2jgxC6wv9pks5ichxNlcRgqIib5fYSWoicBKtbckTibdOEuq3oia25RFDP26ia6JqcHQ5V1YlE6csaLegd9Kg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)


[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7216117716543864918)
