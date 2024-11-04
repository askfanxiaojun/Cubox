Jambot - Figma 交出的 AI 答卷 - 少数派
==============================

[sspai.com](https://sspai.com/post/82441)ZHYuts

**Matrix 首页推荐**

[Matrix](https://sspai.com/matrix) 是少数派的写作社区，我们主张分享真实的产品体验，有实用价值的经验与思考。我们会不定期挑选 Matrix 最优质的文章，展示来自用户的最真实的体验和观点。

文章代表作者个人观点，少数派仅对标题和排版略作修改。

*** ** * ** ***

今年的 6 月份在 Config 2023 上，Figma 推出了许多新功能，但是唯独没有看到任何和今年大火的 AI 相关的功能。这并不代表 Figma 没有赶上 AI 这班列车，在大会的最后，Dylan 宣布了与 Diagram 团队（一个开发 AI 插件的团队）的合作，并提出了对于「在 Figma 中 AI 将会以什么形式出现？」的疑问。
![CleanShot 2023-08-25 at 17.02.59@2x.png](https://image.cubox.pro/cardImg/2023092014484847738/10989.jpg?imageMogr2/quality/90/ignore-error/1)

如今，已经两个月过去，Figma 也算是赶上了 AI 这趟末班车，并交出了一份在我看来可算是惊艳的答卷。

FigJam
------

我原以为，Figma 与 Diagram 合作后，会先加入类似 AI 生成 SVG 图标，AI 设计等非常硬核的功能，没想到他们压根不走寻常路，反而是在另外一项他们一直在力推的产品，FigJam 中加入了相关功能，而且加的恰到好处。

要来介绍这次加入的 AI 功能，我们首先需要了解一下其依赖的平台，FigJam。
![1_Qm7MlGyRWoANUfPK27_MNg.png](https://image.cubox.pro/cardImg/2023092014484955182/25404.jpg?imageMogr2/quality/90/ignore-error/1)

FigJam 是由 Figma 团队在 2021 年 4 月 21 日推出的一款内置于 Figma 软件中的产品。FigJam是一个在线白板工具，用于团队一起进行头脑风暴和构思。Figma 团队对于 FigJam 非常重视，从在创建文件的时候与传统设计文件同级就可以看出。

FigJam 和所有传统的在线白板一样，支持多人协作，有文本框，可以使用不同种类的笔，放置各种形状的「形状」，还可以放置胶带，和各种贴纸，但是它也有自己的思考，有不一样的地方。

比方说，FigJam 把线下头脑风暴等常用的工具，便签，搬到了电子白板上。所以你可以轻松地在 FigJam 中以较低的认知负担还原线下头脑风暴场景，比方说编排亲和图。
![CleanShot 2023-08-25 at 17.14.20@2x.png](https://image.cubox.pro/cardImg/2023092014484954951/33392.jpg?imageMogr2/quality/90/ignore-error/1)

既然把便签搬上大屏幕，那么肯定不能让它和在物理世界一样，只能写写画画。还记得 FigJam 的 Slogan 吗，里面提到了 Ideate，请记住这个词，后面还要考。

既然用来头脑风暴，那么没有思维导图怎么行，但是再加个思维导图功能会不会让整个产品变得复杂臃肿，一下子增加了认知负担。于是 Figma 团队想到，不如把每张便签都看成思维导图的一个节点，然后便签连接便签，成为了一个思维导图。所以，你只需要把鼠标放在便签周围，四周就会出现加号，然后点击就会出现一条连线。
![CleanShot 2023-08-25 at 17.27.27@2x.png](https://image.cubox.pro/cardImg/2023092014485025446/31767.jpg?imageMogr2/quality/90/ignore-error/1)

于是便签的功能得到了升华，也成为了 FigJam 中我个人觉得最好用的功能之一。当然了，除了便签之外，形状也可以成为节点和其他相连。
![FigJam-1.jpeg](https://image.cubox.pro/cardImg/2023092014485039937/74770.jpg?imageMogr2/quality/90/ignore-error/1)

Figma 另外一个让人备受好评的功能，在线插件和小组件也被搬入了 FigJam 中。
![a9cca8402668dd6b38460a798fc229568a6b8786-2120x1000.png](https://image.cubox.pro/cardImg/2023092014485039518/44091.jpg?imageMogr2/quality/90/ignore-error/1)

这就意味着，你可以在 FigJam 中加入了投票功能，快速绘制圆饼图，无需进行任何复杂的配置，只需要搜索你想要的功能，然后点击一下「Run」，就立马出现在了你的面前。

插件和小组件在 FigJam 中有许多妙用，但是由于本文的重点不在这里，就不过多阐述了。

除此之外，FigJam 还有个功能就是创建 Section，Section 可以帮助你分组不同的便签等内容。它类似于一个虚拟的分区或容器，可以帮助用户更好地组织和管理他们的想法和内容。
![CleanShot 2023-08-25 at 18.37.24@2x.png](https://image.cubox.pro/cardImg/2023092014485122958/97902.jpg?imageMogr2/quality/90/ignore-error/1)

那么，当小组件和便签结合可以发挥什么妙用呢？如果再加入 AI，会变成什么样呢？Figma 在前不久偷偷给了答案，那就是 Jambot。

Jambot 是一个只存在于 FigJam 的小组件，这就意味着你无法在传统的设计文件里使用它。此外，根据 Figma 官方文档，你需要在团队中并且对文档具有编辑权限才可以使用它。这是一个在 Beta 版本的新玩意，所以不排除在未来，它可能可以在更多地方被使用。

你可以通过在 FigJam 的小组件中搜索 Jambot 来使用它。
![CleanShot 2023-08-25 at 17.41.04@2x.png](https://image.cubox.pro/cardImg/2023092014485181353/83642.jpg?imageMogr2/quality/90/ignore-error/1)

当你点击它后，你会发现你的画板上出现了一个列表，这个列表左边还有个圆圈。

这是什么，这和 AI 有什么关系，我的聊天框呢？

首先，我们需要把这个列表看成一个处理器，你可以选择不同的处理方式。既然是个处理器，那么它肯定需要有输入和输出。那么如何输入呢？这时候，我们就不得不提到便签了。是的，这个处理器**使用便签作为输入**，并且是以一种非常符合直觉的方式来完成。下面我们就来演示一下。

### Ideate

Ideate 是我觉得最能够展现 Jambot 强大之处的功能，首先我们需要在 Jambot 上选择 Ideate 这个选项，然后它就会变成一个带有一个运行按钮的小组件。并且，左边的原点自动连接上了一个便签。
![CleanShot 2023-08-25 at 17.46.26@2x.png](https://image.cubox.pro/cardImg/2023092014485137802/32176.jpg?imageMogr2/quality/90/ignore-error/1)

Ideate 的作用是来一次性帮我们产生多个想法。所以我们在便签里输入「A product in the near future」，点击绿色运行按钮，等待一会，奇迹出现了。
![CleanShot 2023-08-25 at 17.48.44@2x.png](https://image.cubox.pro/cardImg/2023092014485297716/37858.jpg?imageMogr2/quality/90/ignore-error/1)

Ideate 小组件的右边出现了代表输出的圆圈，并连接了一个自动产生的 Section，Section 里面是不同的便签，里面分别是想法各异的未来产品。这简直就是神器啊，以后再也不怕没有想法了。

但这还没完，我们可以再创建一个便签写「A product that cares about humanity」，将其连接到 Ideate 组件的输入口。再次点击运行按钮，我们会发现 Section 里面的内容变了。
![CleanShot 2023-08-25 at 17.52.18@2x.png](https://image.cubox.pro/cardImg/2023092014485226108/33204.jpg?imageMogr2/quality/90/ignore-error/1)

这个时候 Section 里面给出的产品是未来的，又是关怀人性的，符合我们给它的两个输入。能接受多个节点成为上下文是我觉得 Jambot 最厉害的功能，因为这代表我们人类思考中的整合。而 Ideate 所输出的多个结果则代表了我们人类思考中的分流。

我们还可以更近一步，在新的 Jambot 组件中也选择 Ideate，然后，再次生成与之有关的更多想法，一步一步思考，一步一步细化。
![CleanShot 2023-08-25 at 17.59.09@2x.png](https://image.cubox.pro/cardImg/2023092014485365984/76757.jpg?imageMogr2/quality/90/ignore-error/1)

除此之外，我们还可以融合两个想法，我们新建一个 Jambot 组件，然后选择 Custom，使用「Combine two ideas」。生成一个结合了两个想法的 idea 后，我们可以再将其输入到 Ideate 组件上，生成更多类似的想法。
![CleanShot 2023-08-25 at 18.01.52@2x.png](https://image.cubox.pro/cardImg/2023092014485390602/15420.jpg?imageMogr2/quality/90/ignore-error/1)

当然，要注意的是，所有的 Jambot 组件都只支持一级上下文，也就是只将其左边直接连接的便签作为上下文。
![CleanShot 2023-08-25 at 18.33.33@2x.png](https://image.cubox.pro/cardImg/2023092014485438700/25567.jpg?imageMogr2/quality/90/ignore-error/1)

在上图中，我将我的信息拆分到两个连接的便签，然后将其连接到 Custom 组件，会发现它回答不出我的名字。

### Summarize

Summarize 也是一个非常强大，且直观的 Jambot 功能。

我们之前看到了使用 Ideate 组件，会输出一个包含多个想法的 Section，那么我们可不可以用 Section 作为输入呢？答案是可以的，我们可以通过 Summarize 来实现这一点。这也是为什么Summarize 使用起来非常直观的原因。

假设我们现在正在开发一款产品，我们通过多个便签来描绘我们的目标用户。
![CleanShot 2023-08-25 at 18.40.33@2x.png](https://image.cubox.pro/cardImg/2023092014485499445/76116.jpg?imageMogr2/quality/90/ignore-error/1)

这个时候我们希望可以有一段话来总结我们的目标用户，Summarize 就可以派上用场了。我们只需要使用 Section 工具选择所有的便签，然后将其连接到 Summarize 组件，并选择 TL;DR 选项，就大功告成了。
![CleanShot 2023-08-25 at 18.46.02.gif](https://image.cubox.pro/cardImg/2023092014485499283/12671.jpg?imageMogr2/quality/90/ignore-error/1)

不过这里有值得改进的点，那就是希望 Section 可以和便签一样，在其周围显示添加连接线的按钮。

Summarize 支持两种总结模式，一种是以文章方式输出，一种是以「点」方式输出。非常好的是，这两种输出方式不是互斥的，你可以同时以这两种方式输出。
![CleanShot 2023-08-25 at 18.49.13@2x.png](https://image.cubox.pro/cardImg/2023092014485545860/34637.jpg?imageMogr2/quality/90/ignore-error/1)

当然 Section 作为输入不是 Summarize 的独占功能，其他的 Jambot 组件也均可以使用。

### Give Me

Give Me 是一个非常神奇的组件，它可以给你提供与你输入的便签有关的人物，例子，想法，统计，和事实等。但是它具体会给你哪些选项以供你生成相关内容会随着你的输入而改变。比方说我的输入是需要一些历史名人，那么它就会给出一些相关选项，例如给我一些人，或者给我一些事件，然后我可以选择其中一项生成。
![CleanShot 2023-08-25 at 18.56.37@2x.png](https://image.cubox.pro/cardImg/2023092014485513727/89721.jpg?imageMogr2/quality/90/ignore-error/1)

如果，我的输入是一个由多位用户评分所组成的 Section，那么它的选项里会出现与这个 Section 内容有关的选项，比方说 Rating，选择之后会给我所有 Section 里面包含的评分，如同一个提取器。
![CleanShot 2023-08-25 at 18.58.10@2x.png](https://image.cubox.pro/cardImg/2023092014485575939/65952.jpg?imageMogr2/quality/90/ignore-error/1)

### 其他组件

鉴于篇幅，Jambot 的其他功能可能无法一一阐述，在下面我会列出所有 Jambot 支持的所有功能组件（翻译自 Figma 官网）：

|         名字          |                      使用                      |                                                          案例 Prompt                                                          |
|---------------------|----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| Ideate!             | 产生多个与输入相关的想法。                                | "Icebreaker questions for our weekly team sync."                                                                            |
| Quick question      | 询问与输入便签有关的问题。                                | "What can I cook with \[sticky text\]?"                                                                                     |
| Teach me about this | 让 Jambot 解释或者教导输入的便签。                        | "Impressionism", "Design systems"                                                                                           |
| Give me...          | 提供与输入便签相关的信息，包含人、例子、想法、数据和事实。                | "US Women's National Soccer Team", "Punk rock"                                                                              |
| Rabbit hole         | 正如其名，这是一个可以让你打破砂锅问到底，深入探索一个知识点的组件。           | "Flamenco" will offer you information on The history of Flamenco or Regional variations of Flamenco music                   |
| Similar stuff       | 展示相关主题的分支，开辟新的探索领域。                          | "Cacio e Pepe" will show you explanations of similar recipes like Aglio e olio                                              |
| Summarize           | 以 「点」 或者文章的方式总结一群便签。                         | \[Selection of stickies with action items\]                                                                                 |
| Rewrite this        | 让 Jambot 使用不同的语气等去重写一段话                      | "Thanks for your input, but I will be moving forward with the team's existing plan" as a polite but assertive Slack message |
| Turn this into a... | 可以将输入重写为一个玩笑，诗等。                             | "Variables in Figma" as a poem                                                                                              |
| Code this up        | 让 Jambot 以特定的语言去编写相关代码。                      | "12 column CSS flex box grid"                                                                                               |
| Custom              | 使用自己的 Prompt，可以将上面的看成 Jambot 提前为你写好的 Prompt。 | "Write me a song about the Black-Crowned Night Herons of Lake Merritt."                                                     |

Jambot 的问题
----------

Jambot 已经非常强大了，其交互方式在我看来是对传统的对话式 AI 的降维打击。但是它仍然有所不足。

首先，它无法理解上下文。Jambot 是一个一次性的 AI，它无法追溯之前的信息。但这也不是不能解决，你可以通过把之前生成的或者你自己写的便签连接到新的 Jambot 组件上，这样这个新的 Jambot 组件就可以获得之前的上下文了。不过还是希望 Jambot 在未来可以支持自动获得一整个链条的上下文。

其次，Jambot 在目前是有使用限制的（个人限制非团队），每 24 小时刷新一次，无法增加。在未来，可能会推出付费的方式来增加使用次数。此外，你只能在教育或者付费的团队中使用，也就意味着目前免费用户是无缘这项功能的。

然后就是，Jambot 无法将便签（或者带文字的形状或者 Section）以外的的内容作为输入。如果在未来，所有的小组件都可以连接上 Jambot，那么绝对可以大幅度提升效率和创造力。
![CleanShot 2023-08-25 at 19.24.39@2x.png](https://image.cubox.pro/cardImg/2023092014485579532/38562.jpg?imageMogr2/quality/90/ignore-error/1)

此外，不能选择使用 ChatGPT 3.5 还是 4.0，不过考虑到目前没有直接收费，这一点我们也不过于苛求了。

Flowith
-------

不过可能很多人不知道的是，在很早以前，有一个中国团队已经推出了类似于这样交互方式的产品，那就是 [Flowith](https://flowith.cc/)。Flowith 可以实现 Jambot 几乎所有功能，可能交互上面没有这么丝滑，不过理念也是一致的。并且其还能保存之前的上下文，使用变量的功能，比 Jambot 有更多的可玩性。甚至还有插件功能，可以直接让 ChatGPT 使用谷歌搜索信息。此外，Flowith 还有社区功能，上面有一些神奇的东西。不过，Flowith 在使用体验上可能真的不如 Jambot（据说会得到改进），不过如果你需要的是一个更加强大的，且更加本土化的节点式的 ChatGPT，那么还是非常推荐的。
![CleanShot 2023-08-25 at 19.36.01@2x.png](https://image.cubox.pro/cardImg/2023092014485651022/63560.jpg?imageMogr2/quality/90/ignore-error/1)

写在最后
----

Jambot 的推出可以看出 Figma 在生成式 AI 上面是有着自己的思考的，所以这让我更加期待，当它给自己的设计功能加上 AI 后会玩出什么花样，让我们拭目以待吧。

\> 下载少数派 [客户端](https://sspai.com/page/client)、关注 [少数派小红书](https://sspai.com/link?target=https%3A%2F%2Fwww.xiaohongshu.com%2Fuser%2Fprofile%2F63f5d65d000000001001d8d4)，感受精彩数字生活 🍃

\> 实用、好用的 [正版软件](https://sspai.com/mall)，少数派为你呈现 🚀

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7104055558604327893)
