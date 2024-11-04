Vol.008：如果大语言模型是电，灯泡之外还会有什么应用？
==============================

[xiaobot.net](https://xiaobot.net/post/d33e740f-3441-4ce6-aefe-3eecabbc9bab)

> 本期概要：
>
> * 产品：Notion AI 的启发与边界
>
> * 产品 ：ChatGPT 是怎么工作的？
>
> * 方法：字母表的思考方法
>
> * 思考：思想的乐高
>
> * 松节油 ：觉察本身就是答案

![](https://image.cubox.pro/cardImg/7b5q2i5eudxfi9mwlmync493ej4bmuaw8ythrtx9omdsmhhy8.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

**卷首语**
-------

* 本期有两篇关于 AI 的，一篇来自于对 Notion AI 的研究，另一篇则是深入了解，ChatGPT 背后最基本的工作原理是什么。前者代表了应用层的思考和现状，后者则是让我们更好理解大语言模型这个基建到底是怎么来的。AI 是一场技术革命，但也是一场界面革命。

* 本期还有两篇关于思考方式的文章，从字母表做限制和用卡片做记录，共同之处在于「涌现」的可能性，即通过在大量最小单位之间建立联系，而获得不一样的结果。

* 喜欢一件事，就要接受后面的代价，才是真正的喜欢。就像詹姆斯 · 索特在《光年》中写到的，若果你想要牛奶，就必须接受奶牛、牲口棚、田野，诸如此类。

* 如果你一直没有收到投递邮件，那么大概率是因为没有在小报童的「投递设置」中打开邮件投递，[点此查看教程](https://help.xiaobot.net/reader.html#%E5%9C%A8%E9%82%AE%E7%AE%B1%E4%B8%AD%E9%98%85%E8%AF%BB)。

------ @Plidezus \& fonter

❧

✍🏻 **来自** [asgardusk@gmail.com](mailto:asgardusk@gmail.com) 、[hazel.hu086@outlook.com](mailto:hazel.hu086@outlook.com) 等 **的 Worthy Five**
-------------------------------------------------------------------------------------------------------------------------------------------

**❶.近期有什么值得再试的菜谱？**

坐标杭州，近期吃过还不错的：老鸭集+的老鸭煲，鲜香醇厚；纯味斑鱼府的斑鱼，鲜嫩爽口，不过蘸水建议自己调，店里自带的蘸水一言难尽。

**❷.近期你的城市中有什么值得再去的地方？**

在杭州，以前很喜欢的一条线。定安路地铁站下车，沿西湖边经过柳浪闻莺雷峰塔到太子湾，然后往之江路方向，沿着江边一直走到宋城那个位置，转头上山去云栖竹径，从人声鼎沸走到人影寥寥。比较远可能得有十几公里，要走一个下午。不过以前在学校的时候很喜欢一个人这么一路晃荡，最后下山坐公交看着夕阳回学校。准备趁哪天不这么热了再出门走走

**❸.近期有什么值得独自或者和友人做的活动？**

推荐一款以前玩的游戏吧，the room 3（中文翻译成迷室，第3部），神作；近期计划去打VR游戏，和攒钱买VR眼镜，求同好

**❹. 可以说一说你最近见过的朋友吗？**

最近，参加了一个前同事的婚礼，一个无论遇到什么变故都永远充满能量的妹子；在杭州参加业内会议，遇到了正在做加密艺术创业的学妹，共同慨叹了一下国内做做这块儿的环境之逼仄，希望今后一切顺利吧

**❺.推荐一本近期你读过或者想读的很棒的书吧**

《回归故里》从播客节目痴人之爱里面听到的，一本社会学的书但是不难读。我赞颂工人阶级，借此在更大程度上远离真实的工人阶级。在阅读马克思和托洛茨基时，我相信人民的先锋性。我进入了特权阶级的世界，也就是那些有兴趣拜读马克思和托洛茨基的人的世界，走进了他们的历史观和主体化的方式。我对萨特关于工人阶级的论述十分着迷，却讨厌我身处的这个工人阶级，这个限制我视野的工人阶级。我对马克思和萨特感兴趣，并想象自己是如何比父母更加清楚地理解他们自己的生活，我通过这样的方式走出那个世界，走出我父母的世界。读到这一段的时候对我产生了巨大的冲击，且不论作者的自我剖析是否真的真诚，但的确是让我自己开始反思一直以来异常坚定的出门离家的想法的来源，对故乡的看法的偏激，以及当下所做的各种选择到底是否真的是在掌握了正确的选择机制后做的决定还是因为被某种背景思潮所影响等等。我想大概每个从小镇独身一人来到大城市的人或多或少都能从这本书中找到些共鸣吧。
> 请你也分享你的 Five ，[Worthy Five, Give Me Five](https://airtable.com/shrxz4uz68hVw4dCQ) [更多朋友 Five 的分享](https://www.notion.so/Give-Me-Five-c38aba942d9a4b70b4215f5d107c2a6a)，同时也欢迎来我们 [随便玩玩日报社](https://www.notion.so/a698e7df3f7c44399186ea9755f6688d) 看看。

❧

产品：Notion AI 的启发与边界
-------------------

by shaonan

随着 Open AI 宣布大幅降低接口调用价格，越来越多产品开始「内置」AI 功能，国内最近不少文档工具都对外宣布正在开发类似 Notion AI 的功能。

不过我们迟迟未动手，原因是和 light 曾经讨论过：这种 AI 能力将来是特色，还是标配？到底提供了什么额外的价值？

在一些我们有限的定性调研中（局限在文档类工具场景），会发现一些现象：

* 提出 AI 需求的人，更多是希望 AI 帮助自己完成自己都无法完成的事情，比如分析出来自己的思维方式，又或者按照自己的风格撰写精彩的文章等；

* 大多数受访者即使有能力频繁使用 AI，但很少人能在现实生活和工作中，应用到 AI 相关的能力。

从个人观察上也是如此，虽然我调用 Notion AI 的频次远高于 ChatGPT，但实际上用的最多的功能，是总结、翻译和修改部分句子语气等功能，而之前在沉思录中关于 Figma 收购价格的错误，就是第一次「盲信」了 AI 给的结果。

那么回到原点， Notion AI 到底是什么？最近 Notion CEO Ivan zhao 正好有一期播客提到相关内容，结合一些 Twitter 上的更新，整理如下：

**▎Notion AI 的介绍**

![](https://image.cubox.pro/cardImg/5tvoztze9iahepg6q59q8wsqa795lus80dafb0obo3v56l6moa.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

Notion AI 比较巧妙的设计，在于有明确的使用场景和语境，嵌入到了上下文之中。只需在空文本拍一下空格，或者选中文本后，就能出来这个界面。

目前主要的功能包含四大部分，具体截图如下：

* 续写

* 从页面中创建内容

* 编辑或者审阅内容

* 从 AI 创建草稿

![](https://image.cubox.pro/cardImg/4tkil9x8n5dqeqaen4hpwcrhix76znspcf9o9svop66pso4rib.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

从上面的场景能看到，Notion AI 和 ChatGPT 的侧重点截然不同，Ivan Zhao 这样解释到：

* Bing 和 ChatGPT 都是你要去哪些地方聊天，而 Notion 是把 AI 带到眼前；

* Notion AI 的优势在于，具有上下文，比如帮忙总结会议记录，以及将其转化为待办；

* **Notion AI 不擅长从零创建，而是在帮助编辑、协作或者完善已经完成的的工作更有用。**

但他也坦然目前 AI 有许多局限性，比如他认为 Notion AI 的边界：

* 无法作为搜索引擎，得到正确答案，比如让其生成一份年度报告，或者回答近半年的事情；

* 不应该用在极其严谨或高风险的事情，比如法律、金融、医疗；

* 通过不当的引导，可能会得到极其冒犯的回答；

* 更好地方式是用来解决「创建职位描述」等重复性高，容错强的需求；

这其实也是现实和理想差距的地方 ------ **AI 不应该用来生成和创造，而是用来进行对于已有内容进行编辑、修改、提炼等。**换句话说，AI 暂时还是一个助手，而非主角。

这在其他几个类似的文档产品中，也能看到一些草灰蛇线：

![](https://image.cubox.pro/cardImg/6666u0mi0xq9pywukgh5lhl4uqafmzfsk66r75fb0tifaugh8i.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

**▎现状是什么**

让我们回到现实来看，在专栏 「Plaformer」的《**Winners and losers in the race to add AI** 》 一文中，作者 Casey Newton 提出了一个很尖锐的问题：**AI 究竟是给新应用带来持续优势，还是变成了给 OpenAI 掏腰包的理由？**

![](https://image.cubox.pro/cardImg/1khyiu0i91mjymm5ybqo9btr07r717q7tow31sqbgi39b7udp1.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

在他来看，目前的事实是：

* 大多数集成 AI 的产品都是 ChatGPT 的 OEM 版本，相当于转售。只不过由于不同应用，涵盖不同的上下文，所以会有不同的应用场景，比如 Snap 的 My AI 和 Notion AI 就不在一个场景。

* 现有海量规模用户的产品引入 GPT 后，也许能帮助 AI 找到新的应用场景。但目前看起来，这些服务只是在复制粘贴，你大可在 ChatGPT 中免费获取相应的内容。

补充一个观点：

* GPT 把许多关于文本的插件都给集成了（比如翻译、语法纠正等），会让许多垂类插件消亡，但提高引入 AI 产品用户的使用便利性。

**所以这些引入 AI 的产品，都是在销售便利性而已，并未建立自己的护城河。**

而未来取决于两个问题：

* 大多数公司是否能找到更有价值的场景，获得额外的利润；还是无法提供差别服务，利润都流向少数提供基础服务的公司？

* 生成式人工智能，究竟是台式电脑到手机的转变，激发起新一代的应用？就像云计算，少数几个公司廉价提供基础设施，然后激发新一代创业公司；还是一组更有限的创新，好处归少数大赢家所有？

目前能看到 OpenAI 宣布，不再使用开发人员的数据来改变模型，而是需要开发人员授权。这意味着更像是往平台范式进行转变。

**▎未来在哪里**

对于直接尝试做 2C 产品的小团队来说，目前基于 GPT 的应用，大多数都没有解决人们真正的问题，更像是一些娱乐工具 ------ 就像 iPhone 时代的「手电筒」应用。

而作为应用型公司，与其追逐风口，倒是不如像 Notion AI 一样，结合自己具体的场景，找到新的优势。

Ivan Zhao 对未来有两个有趣的观察：

**一方面，大语言模型就是电，而 Notion AI 只是第一个灯泡而已，将来还会有许多其他的电器。**所以我们能看到，将来各个应用程序通过提供特殊的数据，来完善从 OpenAI 租用的模型。

另一方面，他认为：**AI 虽然是一场技术革命，也是一场界面革命。**通过创建比竞争对手更容易使用的界面，为语言模型增加持久价值。Siri 停滞不前，是因为用户很难记住他们能用来做所有事情。而在创建界面这件事上，Notion 非常擅长。

当然这并不是没有隐忧，目前 Notion AI 还是一个很贵的服务（10 美金/人/月），如果大公司的产品如 GoogleDocs 免费提供类似的服务，会怎么样？

**推荐阅读：**

* [**Winners and losers in the race to add AI**](https://www.platformer.news/p/winners-and-losers-in-the-race-to)

* [**Ivan zhao 的访谈**](https://www.undigital.news/p/an-interview-with-notions-ceo-ivan)

* [**Notion AI 的介绍**](https://www.notion.so/help/guides/using-notion-ai)

* [**MEMX 的介绍**](https://get.mem.ai/mem-x)

* [**Who Owns the Generative AI Platform?**](https://a16z.com/2023/01/19/who-owns-the-generative-ai-platform/)

❧

产品 ：ChatGPT 是怎么工作的？
-------------------

by liufei

本期我们回归一下 AI 相关的话题，聊一聊 ChatGPT 的工作原理。本文内容主要编译自科学搜索引擎 [WolframAlpha](https://www.wolframalpha.com/) 的作者 Stephen Wolfram 的文章，以及其他参考资料，具体详见文末。

**▎一切都是统计概率**

人工智能历史的发展，大致可以分为几个阶段：

* 符号阶段（20世纪50年代-70年代）

* 学习阶段（20世纪70年代-90年代）

* 统计阶段（20世纪90年代-21世纪初）

* 深度学习阶段（21世纪初-）

在符号阶段，早期的科学家试图找出人类推理的法则，并且让机器学会这些逻辑。我们怎么思考计算的，机器也要怎么思考计算。这一阶段当然也有成果，但科学家们发现了最大的问题：**我们无法把世间万物的知识和法则都灌输给机器**，很多信息是无法良好抽象的（被称为形式主义），也很难批量地输入。因此早期的人工智能往往解决确定性的问题，比如下棋，棋谱的输入是可控的，下棋的规则也是可控的。

当科学家们发觉这点困难后，机器需要自我学习就提上了日程。起初，科学家们还是想让机器通过归纳演绎这种推理的手段学习，比如使用决策树算法，发现依然很难（这被称为**基于规则的机器学习** ）。有一派的科学家，就致力于统计学习的方法了（**基于统计的机器学习**）。

统计学习的原理，就是把所有信息掰开揉碎了，塞给机器。机器在做判断时，更多是预测下一个元素出现的概率。如果是语句，那就是预测单词；如果是绘图，那就是预测像素。

比如，机器手里有半句话：The best thing about AI is its ability to

它会搜寻所有的预料库，查阅接下来出现哪个单词的概率更高。

![](https://image.cubox.pro/cardImg/qfjluudoqbodhsre80kcq2xd07hx57p7ivzfitz5vpmqq90tu.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

然后写出来。这是一个极简的例子，实际操作，当然要复杂得多，有时未必会选择概率最高的词汇。

那么深度学习是什么意思呢？它引入了神经网络的算法，让机器学习可以接受的概率预测的复杂度提升了，也可以说同样效果的计算和存储成本大大降低了。这是一个黑盒，跟符号派是南辕北辙的两种范式。但它很有效果，也是如今所有大模型所采用的方法。

再回到开始说的四大阶段，也可以简化为两大阶段：

* 基于规则的阶段；

* 基于统计的阶段。

说到 ChatGPT，没错，哪怕很多人恐惧于它是否有意识、惊叹于它多么聪明和耐心，但它的运作原理，依然还是「靠猜」。就像一个经典的比喻，**它就像一个读遍了世间所有信息的三岁小孩，不懂任何道理和规则，但它可以谈吐如流。**

**▎计算概率**

预测是要看当前的内容为前提条件下，各种内容的概率，那这个概率怎么计算呢？

这里我们就要引入一个概念 n-grams。

如果是 Bi-grams/2-grams，意思就是我们只关心词对出现的概率。比如：
> 当 to 出现时， be 出现的概率。

如果是 Tri-grams/3-grams，意思就是我们关心3个词同时出现的概率。比如：
> 当 to be 出现时，or 出现的概率。

像这个句子：

**The cat is running away。**
> 2-grams 的方式是计算以下词对的概率：
>
> The 出现时，cat 出现的概率
>
> cat 出现时，is 出现的概率
>
> is 出现时，running 出现的概率
>
> running 出现时，away 出现的概率
> 3-grams 的方式是计算以下词对的概率：
>
> The 和 cat 出现时，is 出现的概率
>
> cat 和 is 出现时，running 出现的概率
>
> is 和 running 出现时，away 出现的概率

很显然，n-grams 中的 n 足够长的话，预测出来的句子的可靠性就会更高。

但是，他们遇到了符号派当年试图把知识塞进机器同样的问题：数据量过于庞大。

如今互联网上流传的信息里，已经有大约千亿级的单词量，在数字化的书籍里，也有至少 1000 亿的单词。而哪怕我们退而求其次，只计算 40000 个常用单词（英文），所需的 2-gram 的概率统计量是多少呢？16 亿。

如果是 3-gram，则会变成 600000 亿。如果是 20-gram，这个统计量会比宇宙中的所有物理粒子加起来还要多。这是永远不可能被机器记录的。

所以，机器并不能直接「查表」。而是通过「搭建模型」来对概率本身进行预测，也可以说是预测之上的预测了。

**▎神经网络模型**

在中学物理里，我们就体会过最简易的模型搭建。比如，一个炮弹从不同的高度落下所需要的时间，根据统计数据，我们能得到一张图：

![](https://image.cubox.pro/cardImg/62c0tbsubwfukxeaku9n035f50ycihufxpjk6tryuaujzlcfl6.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

我们如果用一条线拟合的话，大概是这样：

![](https://image.cubox.pro/cardImg/3ahxqyegyrmmgqlz0pqukyiuvt09mzynhyml1kv3048dquh3vp.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

看起来不够准确。于是我们可以用更复杂一些的公式拟合，比如

![](https://image.cubox.pro/cardImg/4gis0oqtoj8frlnvgn6013cyxswcol0anekc6nagq656jh56ol.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)![](https://image.cubox.pro/cardImg/6cvgovnprflv76au1eodpximaq6kcxuz792z564gjxnbchg69f.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

而神经网络的逻辑，与此相通。

我们拿最简单的一个课题来举例，机器识别图像中出现的数字。记录世界上每个手写数字的像素分布，显然是不可能也不高效的。于是机器可以训练着记住大概的「规律」，也就是对于每个位置的像素来说，给哪个数字加「权重」。

![](https://image.cubox.pro/cardImg/5pql687z764u38751ykq8th73bhru5n3w4u9gq91vvh9jawmbg.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

当整个画面中央没有像素点时，就可以考虑给「0」加个权重，因为大多数 0 中间就是空的；同时可以给很多数字减权重。每个像素点的权重情况，加总起来就可以预测数字。

要达成这个数字识别的效果的神经元，大约需要 2160 个。最原始的数字识别机器叫做「感知机」，早在 1957 年就被制造出来了。

![](https://image.cubox.pro/cardImg/4rzx436i5auvn26pxcni3e9kftsdqpwd53jj2bbfrrggbwj5eg.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

为什么到这些年神经网络才能再次焕发新春？简单粗暴地说，就是计算机性能随着产业发展，而达到了全新的层次。体会下上图中最早的感知机的连线，若是没有如今的 GPU，根本是无法想象的。

区分猫和狗是对人来说无比轻松的课题，对于机器来说，则需要 60650 个神经元。神经元与神经元之间在多个层次上需要形成网络，是一个根本画不出来的多维复杂矩阵，因为维度就有 60650 个。

而且到这个程度，你会发现我们是无法解释过程中发生了什么的（科学家和工程师们也无法解释）。因为神经网络是一个完全的黑盒，且机器并不像人一样去理解事物。

设想一下，我们分辨猫和狗，可能的流程是：先看到是动物 - 判断出是小型动物 - 看到五官或者毛皮的样子 - 判断出是狗或者猫。

机器并非如此，它关注的点是当前人类无法理解的。

* 比如在第一层，通过机器的关注点，可以意识到它是在看大致的轮廓：

  ![](https://image.cubox.pro/cardImg/635siw2dycqcd0d8e10hpfoaq7rwy6pka86gdpkb73lu9t25n7.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)
* 到了第 10 层，已经完全不知道它在看什么了：

  ![](https://image.cubox.pro/cardImg/5sk3ydy5vhsrna67zm8ies3wrt5ftbyxlah33zaxlfi0gijow0.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

而我们做的，就是把一堆猫和狗的图片给机器看，并且告诉它哪些是猫、哪些是狗。是为训练过程。

在这个过程中，机器整理出了一堆的跟

![](https://image.cubox.pro/cardImg/18yy44o4xegzqxg5td2xak7lg05iyuu00y6tp5is0sl4oc9ub.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

一样的参数公式。大量的参数公式，就构成了一个模型。

所以常听到说 GPT-3 达到了 1750 亿个参数量，指的就是这个神经网络的公式，**具备了 1750 亿个权重。**

**▎把文本变成数字：Embeddings**

我们刚刚讨论的是图像的处理，在图像处理上有效果很好的卷积神经网络（CNN）。而在文本处理上，也需要有特别的处理。道理很简单，神经网络本质上处理的全部都是数字，我们要有一个有效的方法，让文本也能高效地在神经网络里流通。

Embeddings 就是一种表征「附近」的方法。就像前面说的，我们记录不同词语之间共同出现的概率，不如干脆有一个附近的概念，让不同的词语的关系，变成向量距离。

例如，这就是一个简化 2D 版本的词语 embedding 的结果：

![](https://image.cubox.pro/cardImg/3roeo3ocarhzm6dmmpuqnzg3gyx4yg2ykl79aa7g4fba88x20m.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

这个是为了可视化方便做成了二维的。但很显然，机器可以处理非常大规模的维度的向量，在各个维度上，一个词语和另一个词语，都可以有距离。

那么这个所谓的「距离」该怎么计算呢？

可以还是拿简单的手写数字图像举例，这里是一个真实的 11 层的数字识别神经网络（这里不关心实现细节）：

![](https://image.cubox.pro/cardImg/40es7lbntf7sd7k54t2qxvwb0kx0lwewczj6fu3g88kj794t0x.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

除了最后一层，在每一层我们都可以计算一个数值，该数值大概可以理解为机器关心的不同的特征维度（类比到人类关心的点，就是这个数字是否是闭合的？比划之间有没有交叉？等等）。

当每层特征计算之后，都会有一个数值给每个输入值。于是我们可以用不同的颜色来代表值的大小，这样对不同的手写数字，就有了一个 embedding 的特征：

![](https://image.cubox.pro/cardImg/43a2qx9xxvedsib9ba1p3jf2yhb40buqt22e32s6dtw57iw4vh.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

使用相同的方法，我们就能计算文本在多个维度下的特征值了。单词的特征，明显会比数字要多。这就是 GPT-2 的三个词语的 embedding 的值：

![](https://image.cubox.pro/cardImg/3m2jm0u38w3fvcmcabo3k2ukpuzvlmde5526a2tbh8chny5tlo.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

而 ChatGPT 的逻辑是，每次生成的文本（不仅仅是当下的单词，回想下上文提到的 2-grams）都会生成一个 embedding 的向量，去匹配更可能出现的单词。这就是让文本变得可计算的方法。

说个题外话，ChatGPT 严格来说不是处理单词的，而是处理单词的模块（也就是常说的 tokens），比如 pre、ing、ized 等组成部分也会单独处理。

**▎ChatGPT 的运转逻辑**

如刚刚所说，在 ChatGPT 中，「猜词」的过程是这么运作的：

* 首先，到目前为止所有的文本（tokens），都生成各自的 embedding 数组（即上文的那个颜色深浅各异的图）。

* 接下来，这些数组都通过神经网络的方式（也就是在大神经网络之下的独立功能神经网络），再次 embedding 成一个新的向量组。

* 最后，根据新的向量组的最后一部分，生成一个有大约 50000 个数值的数组，这些值代表着最初我们提到的------统计概率。

这里面提到的向量组的长度（前面用案例展示过数字和单词的向量组长度），也就意味着效果的优劣了。GPT-2 的长度是 768，而 GPT-3 直接跃升到了 12288。

在 embedding 的过程中，Transformer 起到了很关键的作用。Transformer 是 Google在 2017 年提出的算法。向前溯源，Transformer 中用到的 Attention 机制由 Bengio 团队在2014 年提出。

在把当前文本的所有 tokens 用 embedding 算出向量组之后，会有一些 attention blocks 开始工作。在 GPT-2 中有 12 个，在 GPT-3 中有 96 个。

![](https://image.cubox.pro/cardImg/31bazt5qwfb9cnwquno4gfmo1tn35jz85px4zcwmhgf7v9ye3f.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

它们的任务，是去寻找之前文本中相对重要的那些部分。回想一下，n-grams 机制是，n 越大，代表可以回想（参考）的部分就越多。attention blocks 可以考虑到全部的文本，不受 n 的限制，甚至它会把词汇之间的距离都默认为 1，可以考虑到距离很远的词汇之间的关联，让整个文本之间都互相产生影响，为词汇加权之后把这些因素也添加进新的向量数组当中。算是非常有效的一种处理长文本特征的方法。

这样得到的向量数组，就是最终的向量数组，用它来得到真正要预测的 tokens 的概率数组。

了解了这种计算逻辑，我们就知道，ChatGPT 在计算时都在做什么了。其实每个输出的 token（有的是单词，有的是单词的模块），都是在对当下的特征向量组进行计算，把当下的 token 加入进去，embedding 形成新的向量组。且由于存在着 1750 亿个权重，接下来出现的这个 token 也必须是完成了 1750 亿次计算才得到的。

**所以，下次在用 ChatGPT 认为它太慢时，不妨想一想，它已经在努力了。**

**推荐阅读：**

* [**What Is ChatGPT Doing ... and Why Does It Work?**](https://writings.stephenwolfram.com/2023/02/what-is-chatgpt-doing-and-why-does-it-work/)

* [**详解Transformer （Attention Is All You Need）**](https://zhuanlan.zhihu.com/p/48508221)

❧

方法：字母表的思考方法
-----------

by fonter

**我喜欢把学习摄影技巧想象成学习字母表，学完之后就可以创造自己的语言。**

当初自己对 No/Low - Code 感兴趣的时候就问过自己一个问题，解题思路上，我是喜欢画布派还是表格派？

最终一个小点让我选择了表格，即绝大多数普通人是不适合无限制条件的自由创作的，创造来自有限制的表达。

我在工作业余也会为我的工作去思考它的字母表是什么。

![](https://image.cubox.pro/cardImg/18c130dw1q68enlo90rzcejc46nvjq70cow3lp1k9g5szon95j.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

本期推荐的文章来自最近很喜欢的 [**Gordon Brander**](https://substack.com/profile/1245173-gordon-brander)**《Alphabets of Emergence》**

他的人生目标是创造一套系统，该系统能创造一个涌现系统（emergence）出来。

Minecraft、 Web、 wiki、电子表格和乐高都是涌现系统。那么，如何才能激发涌现出现?
> Christopher Alexande 说，涌现（emergence）是由生成系统（generating systems）产生的。用简单的语言来说，涌现源于字母表。字母表是一套部件，连同组合它们的规则。字母表是组合的，它们让你把东西组合在一起，创造出新的东西。

一个产品只能服务于那些 PM 可以想象的用例，但是字母表可以用来创建超出任何一个人可能预期或想象的东西。

![](https://image.cubox.pro/cardImg/1ad6e3hkk5sfm5zufxed1vl4dbxtd3je8yep3g611dk58nm9yv.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

一些例子

* 英文字母有26个字母，还有把它们组合成单词的语音规则。

* Minecraft 允许你用新的属性制作新的物品。

* 化学定义了如何将分子结合起来，从而产生具有不同于部分之和的性质的新材料。

* DNA 有一个微小的 ATCG 字母表，但这个字母表可以产生的意义尚未穷尽。

网络最初是一种思考工具，一种在计算机之间共享科学论文的小型简单工具。

然而，它已经演变成一个通用的应用平台，并且已经被应用于从电子商务、社交媒体到流媒体视频的各个领域。

这种进化怎么可能发生？网络被设计成一个字母表。

这可以从 Tim Berners-Lee 的 [Weaving the Web](https://www.w3.org/People/Berners-Lee/Weaving/Overview.html)
> 正在进行的物理学探索之一就是找到描述非常小的简单物体行为的简单规则。一旦发现，这些规则通常可以扩展到描述不朽系统的行为... ... 对于 Web 来说，这些元素按照重要性的递减顺序是通用资源标识符(Universal Resource Identifier，URI)超文本传输协议(HTTP)和超文本标记语言(HTML)。

这些片段组成了一个字母表，HTML 组成了自己的字母表。

这些字母表的片段已经被重新组合，以创造 Tim Berners-Lee 无法预料或想象的新事物。

* URLs + HTTP + HTML = web

* URLs + HTTP + RSS = Podcasts

* URLs + HTTP + JSON = REST APIs

* URLs + P2P + HTML = Web3

DNA 只有4个字母，但是却生成了你。

从涌现的角度来看，重要的不是字母表中字母的数量。

重要的是组合的机制，以及如何将这些片段组合成新片段的规则。

一个复杂的有效系统总是从一个简单的有效系统演化而来。

一个从零开始设计的复杂系统永远不会正常工作，也不能通过修补来使其正常工作。

你必须从一个简单的系统开始。

限制字母表，但不要限制可以用它写什么。

推荐

* [**Alphabets of Emergence**](https://subconscious.substack.com/p/provoking-emergence-with-alphabets)

❧

思考：思想的乐高
--------

by fonter

卡片（Cards）仍然是最好的个人思考工具之一。

在计算机出现之前，作家和研究人员收集成箱的索引卡片笔记是很普遍的，这其实就是一种原始的超文本。

**▎卡片有什么好的？（这里的卡片也可以换成数据库里一行记录来思考）**

![](https://image.cubox.pro/cardImg/3a0lpyth1jzb6xfqcyhmnjoyfp2n5kpknvuct70wcy62xz2yl9.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

* One card = One idea

* 你可以收集它们，而不用担心它们如何融入整体中

* 您可以分组，重组，变形，排序，集群，连接，重新排序它们

**▎能用卡片做什么？**

* [让他们重新排序，变成一个故事乃至多个故事。](https://twitter.com/imagetextimage/status/1379641362652528641)（有一本有趣的书[《**一个故事的99种讲法**》](https://book.douban.com/review/14290619/)）

  ![](https://image.cubox.pro/cardImg/2vk25ibpijly5at15ycrxx7n1pwn9ykucs75zpasue6mz84gg8.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)![](https://image.cubox.pro/cardImg/242089c6kenj4zr75pvggo3krf3hi23lyja5i2zslq6u5yfyhe.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)
* **获得非线性。**

  ![](https://image.cubox.pro/cardImg/2id0nwmoipuayxy2jd3tuemz4m7ozc0o8hx1e56p2nrcyjqcje.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

  [以非线性方式分组和重新分组。](https://twitter.com/Lauracsc_/status/1380203587804991491)
* **把你所有的想法都展现在你面前。**

  ![](https://image.cubox.pro/cardImg/3av4ru0xmjqr589v6ovkwiivalwi6ecoasy2omr01otg066at0.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

  [生活的审计](https://www.notion.so/a8ba1426342342d2a6deb31ad6e1def3)
* **按主题建造 decks 或者 mix decks。**

* 随机抽一张卡片来寻找灵感（塔罗牌）。

  ![](https://image.cubox.pro/cardImg/5gcf5ik7t70z9iab5lrkji3xz26f7vjjpjxzciysjs1j6ntadu.jpeg!post?imageMogr2/quality/90/format/gif/ignore-error/1)
* 把几张卡片并列起来，画出新的含义。

* 数据聚类。

  ![](https://image.cubox.pro/cardImg/1e82ltaq9hk7m6i0333i5k59coyslhogjtn40vnwhr7xo4nzpd.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)
* 进行模拟版本跟踪。

  ![](https://image.cubox.pro/cardImg/2ijw670wbb84esq8necc74yihfsjttaf52w8nh83z0akizoq62.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

  <https://youtu.be/vrvawtrRxsw>
* 创建一个[算法故事生成器](https://situationlab.org/project/the-thing-from-the-future/)。

  ![](https://image.cubox.pro/cardImg/1a8slnomcfqptrjmge2zq74kgzzjk4i4pd46nhkw29303x4uwn.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)
* 把一本书浓缩成一副卡片牌。

  ![](https://image.cubox.pro/cardImg/55px61kg913m86hh12unna2w8orsupc9b7mfbnol62kd3ihsv.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)
* 写一本新书。

* 写一个剧本。

  大卫 · 林奇说: "如果你有70张记事卡，每张代表一个场景，你就得到了一部电影。
* 写下一个意图，一首诗，一个愿望，并随身携带。

  ![](https://image.cubox.pro/cardImg/4v7e2fqds8fr8wkzuogyyautxikwfodbq1rljouy63jksrusp1.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)
* 给某人一张卡片作为礼物。

  ![](https://image.cubox.pro/cardImg/3pjxepjfcpjnxuz8ra1btsm82oxfblfm9q8exsr2iaqht9vsk6.png!post?imageMogr2/quality/90/format/gif/ignore-error/1)

  <https://youtu.be/NWBS0dTpWUM>

**推荐：**

* [**Thought Legos**](https://subconscious.substack.com/p/thought-legos)

❧

松节油 ：**觉察本身就是答案**
-----------------

by shaonan

朋友从新加坡回国，多年未见，一起在从五柳巷走到了雷峰塔。一路上聊得最多的，主要是对于自己的认识，以及和这个世界上其他一切的「关系」。

但这次对话中，却让我意识到一件事：**觉察本身就是答案。**

以对于亲密关系的思考为例。

我们都是在三十多岁才意识到亲密关系的重要性，而自己对这件事一无所知，基本上都是从上一代人那边继承下来，或者受到社会风气所影响，充满了各种缺陷与惯性。

但我们却以此用来指导自己生活，甚至将这种对于「亲密关系」有偏见的定义，作为重要的人生目标，没有考虑到其本身的定义是否有问题，以及如何花精力去改善。
> 朋友问我，你是怎么解决这个问题的。
>
> 我说，其实自己没有解决这个问题，而是觉察到了这个问题。
>
> 觉察到了之后呢？朋友继续问。
>
> 我说，觉察到本身就已经是答案了。剩下的，首先需要全然地观察，在观察的过程中，行动将会自然而然地孕育。

听起来很玄学，讲个具体的例子：
> 自己很爱出门溜达，妻却喜欢待在家里；有时候想出门散散步，但念及平时经常工作到很晚，鲜少陪伴，内心愧疚，所以渐渐地也就不怎么提这件事，但每逢阳光正好却只能宅在家里时，内心总觉得有些不悦。
>
> 但一次争吵后，两人静心来谈，她很惊讶于我会有这种「愧疚」，因为在她来看，我忙碌了一周，想出去散散步，很正常，她也不需要我周末无时无刻不陪在身边。
>
> 继而，她说提到了一个我从未觉察的观点：不要像父母一样那样通过牺牲自己来「爱」家人，其实是苛责自己但还是渴望回报。你先把自己收拾好了，再去爱别人，不要陷入自我牺牲的怪圈。自己过的拧巴，然后非把这种拧巴当做为别人的付出，这是道德绑架。

你看，觉察到自己总有「牺牲」的想法，就能带来全新的视角：

* 观察上一代人，有许多所谓的「对你好」，背后都会附带一些这样通过「牺牲」自己带来的道德压力；

* 观察自己之前在工作中的一些无名怨气，更多的是觉得自己「牺牲」了这么多，但是结果不如人意。

* ......

而只要觉察到了，问题其实直接就浮现出来了，该怎么做，也很明确了。

许多时候我们都爱求一个答案，却鲜少提醒自己增加觉察。**因为答案，意味着可以这个问题永远以这种方式解决掉，这太诱人了，让人难以抗拒。**

但所有的问题都只有一个临时性的答案。因为问题本身随着时间会变化，曾经有用的答案，只不过是探索道路上的临时注脚而已。

比如最近自己的焦虑，其实无非源自于：

* AI 到底如何和 flomo 结合？

* 面对竞争对手的抄袭该怎么反应？

* ......

觉察到这个焦虑，就会发现答案也浮现在眼前了 ------ 去问问真实世界的用户，他们到底需要了么？在用了么？------ 当调研越来越多，内心就越来越平静。

持续保持不断地觉察，那么就能跟随问题一起变化，看到不同的行动方法，也就才是最终的解决方案。

所以说，**觉察本身就蕴藏着答案。**

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7250762992730506069)
