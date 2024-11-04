人机交互( HCI ) 是强人工智能的瓶颈。
======================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/X0etgDymhjA7pTOOm4yg7g)范阳 范阳


Borderline , Recondite

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FUw5TtAMCDZlFIdJBdUibao88TBbCQfVl7DfsExNicNib0lyTlmsiaHyMu6WCxu1TOgAxpia8g4rHBictZLzoXr9KnRaA%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)

在人工智能领域，有两种 "模型" 是最重要的，一个是机器学习模型本身的能力 ( machine models ），一个是人们看待人工智能的 "思维模型" ( mental models ), 而后者往往更重要，过去的突破是由于一些人改变了看待人工智能的思维模型引发的，而当下的一些瓶颈也是被人们自己的思维模型困住了。

比如**Human-in-the-loop** vs.**Human-AI-in-the-loop**   

比如**self-play** vs.**we-play**

比如**Sim2Real** vs.**Real2Sim**

比如**3D** vs.**2.5D** vs.**3.1415926D**

在我最近和国内国外的一些优秀的研究者和工程师交流的过程中，我发现最稀缺的是切换角度和维度看待自己领域的发展和在创造的东西，也就是思维模型的转变。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FUw5TtAMCDZlFIdJBdUibao88TBbCQfVl7w2icWg10jXVnt7Pkzv7jzlAofdhhg1GOkJ9GctJr3eVMDxIVlZJ5yYQ%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)

如果不进行实验，没有人能准确预测出来现在的人工智能会催生出来什么新事物，但是它大概率会和现在我们熟悉的东西和主流在炒作的东西不一样。而现在去解决人工智能领域底层的关键性问题 （ 架构，数据，计算效率等等 ），和开创性的创造新的用户界面和用户体验（ 新的软件，硬件，音乐，游戏，故事，艺术等等 ），都是最好的时候。

今天分享的这篇文章来自**Josh Pollock** 的个人博客，他是麻省理工学院计算机科学与人工智能实验室（ MIT-CSAIL ）的研究组 MIT Visualization Group 的四年级博士生，他的研究方向主要是 "领域特定的视觉语言" ( domain-specific languages for visualization) 和人机交互（ Human--computer interaction )。

人机交互研究过去在计算机和人工智能领域有点处在技术鄙视链的下游，以及主要是交互设计师的工作。但是现在更多机器学习和其他工程领域的人也开始和交互设计师合作，重新思考和设计整个系统。  

文章不长，我同意他的主要观点，希望也对你有启发。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FUw5TtAMCDZlFIdJBdUibao88TBbCQfVl77e3qDIGDibnJPIib0QKjTUdrlqvfX8rGO349QJTh8Jribq8LjxvMrqw9Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FUw5TtAMCDZmHDHwsWqDBdW8Ctic4oUIHDd8BHtNUIdQrl6rWOUVpnWFkCXG8DYquospVlcXOXF1lBaQHicqYt69g%2F640%3Fwx_fmt%3Dother)

**人机交互是强人工智能的瓶颈**

**HCI Is the Bottleneck**

作者：Josh Pollock

编辑：范阳

写作时间：2024年7月8日

**在一个拥有强大人工智能的世界中，人机交互是瓶颈。**

**HCI Is the Bottleneck in a World with Strong AI**

随着模型能力的进步，我们快速获得了从简单的文本提示词就能生成图像、视频和音频的能力，这些生成的内容与人类生成的内容几乎没什么分别。

然而，即使我们不考虑模型的现有缺陷，模型能力与实际有效的系统之间仍然存在巨大差距（ there's still a huge gap between model capabilities and systems that are effective in practice ）。我认为这种差距主要是由人机交互问题而非模型能力造成的，而且随着模型能力的提高，这种差距只会继续扩大。

这种差距完全是由于人机交互的不足（ failings of HCI ）造成的吗？不完全是。我认为这也是由于人们看待人工智能的思维模式造成的，尽管整合人工智能解决方案的问题越来越多，但这种思维模式依然存在（ due to the mental model of AI that persists despite growing problems with integrating AI solutions ）。

人们通常是这样看待人工智能的：

**输入 -\> 模型 -\> 输出**

**input -\> model -\> output**

机器学习的核心目标是，创建一个在给定输入的情况下优化输出的模型（ The goal of core machine learning is to create the model that optimizes the output given the input ），例如生成最能忠实代表输入文本提示的图像（ producing an output image that most faithfully represents an input text prompt ）。这种模型思维的核心局限性在于它忽略了输入的来源和输出的去向是什么（ The central limitation of this model is that it ignores where inputs come from and where outputs go to ）。

实际上，这个过程应该更像是这样：

**人类-输入 -\> 模型-输出 -\> 人类**

**human -input-\> model -output-\> human**

即使我们假设一个完美的模型可以优化输入和输出之间的相关性，该模型仍然在根本上受输入信息所包含内容的限制（ the model is still fundamentally limited by the information contained in the input ），而输出的有用性也在根本上受到人类解释和使用它的能力的限制（ and the usefulness of the output is still fundamentally limited by a human's ability to interpret and use it ）。

随着模型能力的提升，改进输入和输出接口成为了瓶颈（ Improving input and output interfaces is the bottleneck as models get more capable ）。

这可以被视为一个信息论的问题（an information-theoretic problem ）。如何将更多的信息比特传入输入流？如何让人类从输出流中解读更多的信息比特？解决这些问题不仅仅是算法上的，还需要现有的上下文才能理解（ require existing context to understand ）。也就是说，不仅仅是塞进更多的信息，还需要以一种让人类能够创造和理解这些信息的方式进行（ it's not as simple as cramming in more information, but also in doing so in a way that allows humans to create and understand that information ）。

**人机交互在不完美的模型中扮演什么角色？**

**What's the role of HCI with imperfect models?**

即使在不完美的模型下，人机交互（ HCI ）依然有着深远的作用，甚至可能发挥更重要的作用。我们可以把一个 "不完美的模型" 视为一个 "完美模型" 加上一些额外的（ 有可能/ 很有可能有偏见的 ）噪音。因此，不完美模型下的人机交互问题与完美模型下的人机交互问题是一样的，只是增加了让人类理解和处理模型输出中的 "噪音" 的难度。

**强人工智能不会解决人机交互（ HCI ） 问题吗？**

**Won't strong AI solve the HCI problem?**

即使模型可以在自己生成界面方便做得更好（ Even as models get better at producing interfaces ），它们的能力仍然局限于人类\<-\>模型的反馈回路（ their capabilities are still limited to the human\<-\>model feedback loop ）。这种回路可能会被用来设计这些界面（ 例如，Copilot 和 Figma AI 已经开始这样做 ），但这并不能完全绕过这个问题。

**用户界面不是会一直被即时生成吗？**

**Aren'tUIs just going to be ephemerally generated all the time?**

像 Blender 和 Photoshop 这样复杂的界面仍然可能是半稳定的界面（ semi-stable interfaces ），而不是即时生成的界面（ generated on the fly ），因为学习这些用户界面的难度较大，并且人类在使用他们深入理解、技能娴熟、反复实践和精通的工具时会有很大的优势（ the benefits humans have when using tools they have deep knowledge/skill/practice/craft around ）。因此，这些界面仍然受到反馈回路问题的影响。

**那如何提高输入和输出的保真度？**

**How do we improve input and output fidelity?**

我想我会把这个话题留到下次再讨论。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FUw5TtAMCDZlFIdJBdUibao88TBbCQfVl7g9LVf0pYgoX6RdplTWD5U3BOMkVe5kzXg6ic4dkGNQLF6urOvMqHakQ%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg)

原文链接：

https://joshmpollock.com/blog/hci-bottleneck/

人工智能与人机交互的延伸阅读：  

[思维的合成器 \| AI 改变软件只刚刚开始](http://mp.weixin.qq.com/s?__biz=MzU4MzY1MDg5NQ==&mid=2247487484&idx=1&sn=57f9d4cea31fe2076908ce7e0798bb2a&chksm=fda494dccad31dcad57ede3d87c3e30f1cebf2e7535164dcf2a55128d93e0c698b84329c2461&scene=21#wechat_redirect)  

[AI 需要开创性的用户界面和产品: 从苹果说起，深度访谈 Daniel Gross 和 Nat Friedman（3万字)](http://mp.weixin.qq.com/s?__biz=MzU4MzY1MDg5NQ==&mid=2247487364&idx=1&sn=b2d922dbb96e775b7f2e433e076c60c5&chksm=fda494a4cad31db2ed92be23b8dfedc83042534c5e69ac96601eeefb0f1a391ba5a9b6fe88b8&scene=21#wechat_redirect)  

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FUw5TtAMCDZmHDHwsWqDBdW8Ctic4oUIHDd8BHtNUIdQrl6rWOUVpnWFkCXG8DYquospVlcXOXF1lBaQHicqYt69g%2F640%3Fwx_fmt%3Dother%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

****前文阅读：****

[《AI 在把传统软件当早餐吃掉》](http://mp.weixin.qq.com/s?__biz=MzU4MzY1MDg5NQ==&mid=2247487272&idx=1&sn=a165897d2346804a9a3b7d31ca7fbd0e&chksm=fda49408cad31d1eb947a2adde95a342dc9b48e39de0ac7942be7f3e2e4cbb1c4739348a9d9e&scene=21#wechat_redirect)

[《与 Nat Friedman 和 Daniel Gross 推演人工智能的发展 \| 3万字采访, Stratechery 3月》](http://mp.weixin.qq.com/s?__biz=MzU4MzY1MDg5NQ==&mid=2247487082&idx=1&sn=5903e8c6d149fb45df8a35c25432f11b&chksm=fda4954acad31c5ca20dfd8e2694e41a65c738984315fdeb6f576527363075088d5f45f2ecae&scene=21#wechat_redirect)

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7210902756029107962)
