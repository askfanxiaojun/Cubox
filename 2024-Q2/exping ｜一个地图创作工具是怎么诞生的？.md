exping ｜一个地图创作工具是怎么诞生的？
=======================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/deLH0JFCHRZj4mA6m8B6YA)探索更多未知的 Exping World

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FFT0EakcgXOxPaJ5CWJibCwG8CgUUlkzGCOuJ9sCpJ401nzkvARZv4RDDDCR9zvIo6FFoSTZNibUAUgxoCqxY9aEg%2F640%3Fwx_fmt%3Dgif&valid=true)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKn3ibeBAdhqj0mU3DxbBo0NwNPUfT4vPZwEaXjk3H4eqEmROU4ibAiciafQ%2F640%3Fwx_fmt%3Dgif&valid=true)


大家好，我是 CLU，exping 地图标记工具的产品设计者。

一直想找个时间写一篇关于 exping 诞生和幕后故事，之前也只是在 Anyway.FM 播客中简单提及过。

所以还是借着「v1.1」的发布，写这一篇文章记录我个人和 exping 团队，从一个想法到团队组成至上线后历程。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FFT0EakcgXOwwET4icUS9qBTVApXuOR9Th3BrmwzPRb7RtHoQUXPibOibvwzDclFh0890yILKyZROrpSjOo6ASBN6A%2F640%3Fwx_fmt%3Dgif&valid=true)

***「一个想法」 的诞生***
----------------


最初有做 exping 的想法是源于很久以前（大约是 2014 年至 2016 年左右），当时我就有在地图上标记去过各个不同国家咖啡店的习惯。每次到这些咖啡店的时候，我也会「打卡」，然后分享到自己的社媒平台，描述每家店的机器、点评咖啡质量、推荐什么样饮品等。

久而久之，当我身边很多朋友再去到那些城市时，都会问我这个城市有哪些咖啡店值得去、适合去。大概是因为那时候我还是个自由职业者，经常会去不同咖啡厅办公，很在乎咖啡厅是否具备办公条件。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKjsKBlL98u2JsLoaQHxJkLIzBAaLwVkhKwrpick4KvDQhVsgdWITXR0Q%2F640%3Fwx_fmt%3Dpng&valid=true)

（2016 至 2018 年，各地图上标记过的咖啡店）

那时候纪录地点，用得最多就是 Google Maps 的 My Map 。

直到有一次，一位素未谋面的朋友提出，「我能否和你购买你的咖啡地图，我想跟着你的脚步一家家店去探索」。后来，他确实为我的地图付钱了，我才意识到，**原来有人认可并愿意为我选择地点的品味付费**。

这是「粉丝」相信我所精选（Curate）地点和体验标准而付费，和商家付费让我去体验测评是完全不一样的事情。

于是，这个 idea 一直埋在我脑里，但当时并没有付诸行动将其转化为一个「产品」或者「服务」。

***疫情突如其来，***
-------------

***一切停摆，生活照旧***
---------------

2020 年，疫情突如其来，身边许多马来西亚朋友收入明显减少了许多，但是生活依旧，该花的钱还是得花。虽然大家出门机会少了，但过往打卡过的地方还是有「库存」。

所以我在想，这些曾经探店记录，有没有可能成为疫情下的一种创新副业经营起来呢？就像前面提到，你去过的地方，探店、周边游、出境游攻略等，无论是好还是踩雷的，**任何与地点相关事物都可以标记在地图上，让** **喜欢且信任你品味的人可以为你精选（Curate）付费。**

在国内或许有知识付费的存在，但在调研东南亚这些我熟悉的地方时，貌似不存在这样的产品。于是，我开始在公司内孵化「exping」。
> 产品名字之所以叫 「exping」，是希望大家多去探索、体验，并在这些点和人之间进行连结。
>
> **Exploring, Expriencing, Ping** (编程人员应该都知道吧)。
>
> 而域名.world正是希望大家可以 exping the world。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKn3ibeBAdhqj0mU3DxbBo0NwNPUfT4vPZwEaXjk3H4eqEmROU4ibAiciafQ%2F640%3Fwx_fmt%3Dgif&valid=true)

***想法落地***
----------

既然之前已经有过对产品雏形的想象，那是时候组建团队了。

于是我在公司内部做了一次提案和宣讲，挑选有能力并且有共同想法的人组建团队。在开发之前，刚好公司有 Flutter 预研团队，并且开发也认同这个产品价值，再加上一个产品和设计，这个团队很快就组成了。

整个团队一共就五个人，内部孵化实验的试错成本也有限，所以 Flutter 跨平台框架，对于我们小团队去做一个产品来说是有利，可以在有限开发资源的同时，兼顾双平台开发。（成也 Flutter ，败也......）

***从「品味」开始***
-------------

团队组建好后，我们花了差不多一个月时间去调研市场，调研竞品。其中比较有趣的是，我们花了蛮多时间在讨论「**推荐算法** 」和「**品味**」。

对于算法，我相信所有互联网使用者都有接触，无论是刷短视频还是在搜索栏输入我们想搜索的自动补全，这一切都是为了能够让使用者更「高效」。推荐算法的逻辑是从使用者行为或是具有相同画像的人群关系，作为你潜在「感兴趣」的可能去进行推荐，比如协同过滤算法。

这和我们要做的「产品」有什么关系？我喜欢算法带给我便利，但很多产品的推荐引擎会误以为我曾经点开过一个「内容」 ，并认为那是我所喜欢，于是反复推荐相同的东西。不排除那或许是我感兴趣的内容，但不一定是我想一直都刷到相同内容，这点在推荐算法侧重非常大的产品，你或许会有所体会。

行业内也有一种推荐算法，是我比较欣赏。**这种推荐方式具有相似的关联，而且有额外惊喜发现。**比如 Spotify 的 Discover Weekly 歌单，更多是透过歌曲的特征，节奏、音调、歌手等等，是通过自然语义、机器训练处理的结果。这些算法不只是简单的数据输入输出，还会根据很多不同的模型来影响最终结果。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKbUdfyanzuh9cgXc7X18OcLVUpDo7bmA3mtkCaEKyAh78rENNia9fTHg%2F640%3Fwx_fmt%3Dpng&valid=true)（图源自：Quartz）

最终我们选择把这一切交给用户，像挑选杂志或在音乐平台选择网友创建的歌单一样。

前面提到是以个人选择为本的方式，和推荐算法是有区别。**在我们看来，技术应该更多是帮助创作者如何发现「地点」，而不是告诉用户该做什么，仅是提供洞察。**每个人对地点的「决策」受很多主观因素影响，可能是地点比较近、菜品有家乡味，又或者是第一次尝试具有新鲜感的活动所以好感度比较高等等。

**那「品味」或许能更好地诠释每个选择背后的关键抉择点。**

在黄炜东的《品味沉思》里关于品味提及：
> "  
> 品味 = 99%的知识厚度+ 1%的审美判断。
>
> ---------Notes ontaste,Brie Wolfson
>
> <br />
>
如何体现品味？或者构建地点画像？是图片还是文字？话题能否起到标签的作用？如何将这些点与人的抉择关联在一起？

这些都是我们早期构建一个品味社区时的思考点，当然无论是透过以上哪一种都会存在缺失，更何况任何推荐算法都需要大量的数据才能进行。若依靠图文表达，纯粹的算法是不足够，再说，这岂不是和小红书竞争。

如果用户喜欢分享的都是人物图片，而非该地点的信息，那该如何获取有效的数据？还是设置某种机制，凡是检测到自拍照就禁止发布？（开玩笑的，但在会议上确实提及过）

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKYSsAXIVpvxs8Ipoib3xZzYI1vtDFTiaiaglxty4GpmYXNsQUTNOtcUBNA%2F640%3Fwx_fmt%3Dpng&valid=true)

在设计 exping 的过程中，也是在不断地挑战着我们团队的「品味」。我们希望以什么形式呈现，并让大家能够更好地把这个抽象的想法，在产品中表达。

我在《创意选择》里受到了很大启发。
> 我们很多的抉择不能完全依靠数据作为唯一评判标准。
>
> 除了需要阅读大量与人类抉择思考相关文章，还需要整个团队在产品设计的理解上磨合出我们的品味。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKiceeCiabHlXRuhRmkxz4Dp68ribUahbh5gubZHoUJFUgjbEWyPhHM1pNg%2F640%3Fwx_fmt%3Dpng&valid=true)

**![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKAbIhCcpSunWpRFVnd4F6KDELhFFyeOnm9q6E2GUmib9rtiat2NCyGkjg%2F640%3Fwx_fmt%3Dpng&valid=true)**   

**（** **2021 年 7 月发的一条朋友圈，关于我对品味的想法）**

***从社区到工具***
------------

在 2021 年下半年，我们基本完成了社区雏形的开发，版本号为**v0.1**。

这只是从想法到实践拿到手上的第一步，我对这个版本号特别在意，因它完全不到我所想的 「v1」阶段，与此同时我们邀请了约 100名内测用户体验测试。

在开发期间，世界也有了很大的变化。我们知道 Delta 出现了，Omicron 也悄悄来了。海外的用户也没法出门，东南亚多个地区都处于封禁状态。于是最开始打算在海外上线 exping 的想法不得已暂时搁置了，或许可以先从我们身边的环境开始？这样我们也能够在自己的城市进行冷启动。这个决定也让我们的部分界面交互，在国内推行的时候有些不适应。

在这里穿插一下，我们冷启动前，是先开设公众号，联系广州本地有意思、有理想的独立店铺主理人们，进行访谈。希望可以把这些特色的店与喜欢他们的人群连接在一起，我们相信喜欢这些店的客户群体，是具有一定相似度的标签画像，并可以互相发现。我们把这个专栏名为《EXPert 专访》。

直至2022年，我观察到，如果 exping 需要在国内落地，社区所面对的挑战和资源要求，不是我们小团队几个人就能完成。

**所以在 Q1 季度，我决定调整产品方向，暂时把品味社区的想法先放下。回到我们初衷，如何让大家更好地在地图上创作，并且让地图内容有价值。**

***地图创作，另类内容创作载体***
-------------------

在做 exping 过程中，我们也发现市面上越来越多人开始尝试成为内容创作者。无论是为了对抗平台的不公，或是想发展自己的粉丝群体。

同时，国内帮助内容创作者分发、创作、收费的工具也在不断地发展中（比如最近 Newsletter 复兴），有小部分的群体可以自主选择内容，并有意愿为产出内容的创作者付费，这是一个很好的现象。

无论对创作者或读者来说，都是很健康的交易。

***Everyone is Curator***
-------------------------

***人人都是Curator***
-----------------

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKh2xVSFHKkOkqGJ4NEDmMtyAMEKpsExXlnSgj3waGgZujE03BCFRJRQ%2F640%3Fwx_fmt%3Dpng&valid=true)

**平台与内容消费者和创作者的关系**

**（图** **来自The Quibbler** **）**

过去，网络的内容依靠平台产出（PGC），演变成如今用户生产内容（UGC），再由平台推送给用户（内容消费者）。当大量的信息摆在消费者面前，依靠推荐算法筛选内容给到用户，渐渐地出现了一些 Curator4 ， 扮演中间人，将这些信息过滤一遍，再结合自身的观点甚至稍加编辑给到信任他们的内容消费者（粉丝或关注者）。

**exping 最初构建，就是以「地图」为画布，作为另类的创作载体。** 而地图创作者，我愿称在 exping 上的创作者为 Curator（策展人虽然是契合的称呼，毕竟是始于展览策划的词语，但我还是觉得不能够很好的表达这类创作者）是同样的以个人品味去精选地点，并把这些地点聚合在一个主题下。

* **Curate 标记（策划）**

* **Curation 地图（作品）**

* **Curated （标记过的地点）**

每个人都是一个 Curator，我们会在各平台 Curate （收藏）不一样的东西。这些收集最终可以呈现为一个 Curation，也就是将这些你在乎的、喜欢的、对此了解的事物，带着自己见解、描述进行组织收藏。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKWEXtbnGGvsCAMTqTictXktibRsficOG2km5aib5ngDyItwYuEpoBZdsPZA%2F640%3Fwx_fmt%3Dpng&valid=true)

地图内容有很明确的主题，以 Curator 品味精选地点，聚合在一个主题下，并在这些点之间进行描述、点评、评分等。

比如：适合办公的咖啡地图、快闪差旅城市体验地图、理发店避雷地图、设计师名宿、建筑师旅行地图等等。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKrhia0ytGBicCgAADZ60h82bGhuUZDmjomrdplTTAiapTz4KfDiboOWqc3g%2F640%3Fwx_fmt%3Dpng&valid=true)![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKMic1ibZIEemaXHZO7ERv5ZMWUlNho20WfPXFE6QPsAeNOVUsosPLQruQ%2F640%3Fwx_fmt%3Dpng&valid=true)

**（以上内容均来自 exping 社区公开地图）**

有了前面说的这些基础，我们决定，从构建一个品味社区转变成服务好 Curator （创作者）更好地呈现地图内容的工具。

**我们不希望创作者最终内容只能存在于 exping ，而是帮助创作者更好地呈现与地图相关内容，可以发至创作者本身正在经营的其他平台。**

***正式上线***
----------

前面话痨说了那么多，该奔主题了。最终 exping 是什么？**一个地图标记工具，可以让你更好地呈现你的探店、旅游、户外等各类主题的地图内容。**

**地点标记** ：一个标记可不止定位这么简单，创作者可以用 Emoji 在地图上标记该地点印象。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKf9kbdvSc0AIYzHiajmImAgLZysWw9BLN8w0vuoV5Mic2AD7vkiaFklicKw%2F640%3Fwx_fmt%3Dpng&valid=true)

**路线标记** ：同一张地图，不仅可以标记地点，也可自由地绘制专属路线，将一个地图内多个地点串联在一起。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tK3GUg9a55VelgvnmrY8MEgNkfDOWL7OwTkzPB833DO6VqSKm97AYjZA%2F640%3Fwx_fmt%3Dpng&valid=true)

**自定义体验标签** ：我们以地点类别提供不同的选项，不涵盖的标签，也可以自己创建。

比如，一张展览地图的体验标签，可以是信息卡片，展示一些有效信息：展览时间，票价，值得看的内容等等。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tK4q1fDRUlVvhp10PbgD5hPlmGBqWc7cZf9wjcyIuUgRueKRfYKkibeRw%2F640%3Fwx_fmt%3Dpng&valid=true)

**可视化呈现地点评分** ：这个idea 是，不是所有地方都可以通过简单1-5分来代表真实想给的分数。这分数不在于该地点的总分是多少，而在于其中一个的影响整体体验的分数。

无论好坏，通过可视化的雷达图，看到一个全面。就像有些地方确实隐秘，交通也不方便，但胜在其他体验是不错的。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKTQlUP4dggkiaVxp8ZgNH3vEdOial0rQqy4oeM37b5WVaibJ7phsbzgnDw%2F640%3Fwx_fmt%3Dpng&valid=true)

所有地点或路线都可生成海报，一键导出。这功能是让大家能带着地点的标签、描述、图片、点评导出一张海报。或许创作者是希望将内容发到朋友圈，或其他社交平台。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tK1GgC4V9X7SmMTTKjLkafAcY5q8iatGFiaDZbFYVJSIco0h24yzBhAjsA%2F640%3Fwx_fmt%3Dpng&valid=true)

除了海报分享，也支持 Web 链接，这功能是为了方便大家分享给只想看一下内容的朋友，而不需要注册或下载app就能简单浏览地图内容。

最后，我们还是保留了原来的 「**品味社区**」，或许在社区内你可以找到志同道合。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKblYhDYBpnxcMELP5kBDlAiaZhoe8za32lsZnxfExQPf7ax6Q077icXKw%2F640%3Fwx_fmt%3Dpng&valid=true)

上线后，有许多地图案例是我们未曾想过。

*
  有中介用 exping 标记自己的房屋资源，并把所有房子的尺寸信息租金都以「标签」的形式展示，并分享给想租房的人；
*
  连锁餐厅老板把每一个加盟店都标记在地图上，完善地点信息，发在他们的社群；
*
  慈善团体标记当月的慈善活动；
*
  情侣把自己与另一半去过的地方标记起来，记录彼此的爱请故事；
*
  还有父亲将孩子成长的经历，像写日记一样把去过的地方记录起来......

这让我们看到很多不同用户的故事，不同的用法，特别感动做到了**让每一个地图内容更有价值。**

很开心在上线当周，被苹果每周编辑推荐，这无疑给予了我们很大的认可。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tK3fD0MwJgYtuibfkOOHoQD1GiavqvodaRwm9De3STYRF2oJodUZ1mYKibA%2F640%3Fwx_fmt%3Dpng&valid=true)

（上线第一周被苹果收录）

最近上线「重磅更新」活动，也被苹果推荐到首页。同时，再次被苹果每周编辑推荐，这些认可给我们带来了无限的动力。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKoYKAI0nun9hKmeGnCw1TfK3tib0NbMLhaKoPlTFvw6QIjILNkkzic5Ww%2F640%3Fwx_fmt%3Dpng&valid=true)

**（v1.1 新增路线功能）**

***挖的坑，填的坑***
-------------


正式上线后，也收到了很多人的反馈，怎么那么卡？为什么不支持高刷？等等。

绝大部分是因为我们可以高效2.5人（还有半个我，贡献Bug，负责多语言部分）开发的Flutter 框架，可以在同一时间兼顾双平台开发。

即便上线后，iOS 用户占比例最大，但还是存在各种小问题（比如薛定谔的bug，就是无法复现），影响了体验。但在前期调研中，有地图创作需求的潜在用户也在使用安卓。

所以我们还是继续努力把这些坑都填了。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKeicjWiaaDL2YB44GIUkjR01sjHbgE9aB6OMCzIR4wjANBiaPqzTWKwcuw%2F640%3Fwx_fmt%3Dgif&valid=true)

Flutter 的 Dart 单线程处理，在一些复杂交互中，会比起纯使用 SwiftUI 开发更容易发生性能问题。

比如：图片选择器，使用了开源 picker 后无法满足性能，以及我们在产品设计之初预期的交互（虽然时间有限，资源有限，但大家都不想妥协），所以我们自己重造了轮子，并且开源回馈给社区。

毕竟开源社区对我们帮助特别大，解决了我们很多问题。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKKicABvKSl6rVyUXl3WCEUQ28uedgVicibtbTDdWgMLlIPLHYhiafWhVYxg%2F640%3Fwx_fmt%3Dgif&valid=true)

这些不足或许是我们对 Flutter 认识不够深，但也在上线后的第二个版本紧急优先处理性能问题、卡顿问题。

我们全栈工程师（顶梁柱）写了篇优化总结文章，复盘解决思路。

在前期 Web 版本也是使用 Flutter for Web 生成，但无奈依旧有许多组件未能和核心库一样运作正常，甚至可能纯文本渲染都会有些问题。只能在半路放弃重新以 Web 技术栈写了一遍。

***未来计划***
----------


exping 下一步依旧会**持续地完善对地图创作者有利功能，也会在浏览地图的体验上做好。**

虽然很多朋友都希望我们能够持续完善做好社区，我们也很在乎社区的价值，不希望只是一个嗮图分享社区，更多是帮助普通人也可以自定义标记地图，有灵活的表达方式。精力有限还是先专注打磨好基础功能。

我们有很长的待办需求比如：

*
  完善海外数据
*
  导入第三方地图数据
*
  数据导出
*
  数据统计
*
  个人数字名片
*
  嵌入式地图
*
  更好分享模式（大家提及最多是希望拥有小程序支持）
*
  地图收费或订阅制
*
  原创内容确权
*
  等等......  

***怎么盈利？卖数据吗？***
----------------


所有盈利模式，无非是交易，与谁交易。商家？广告主？这些都不在我们第一考虑范畴内。
> 我们希望建立起一个更健康的模式，
>
> 把 exping 视为创作者工具，为创作者产生价值。

在未来的迭代中，以附加值功能进行收费，可全包订阅使用所有功能，又或者按需功能付费。若工具能帮助创作者更好的创作，拥有收益，相信这会是一个比较健康的形式。

至于数据，也是我们最关心。前面提到，将创作者的数据仅保留在 exping 不是我们目的。所有地图公开与否，完全交给用户决定。

我们甚至在产品设计之初，已构思如果哪天无法持续经营下去，该如何保证这些数据依然可以优雅地呈现，就像在应用内的浏览一样。在区块链持续发展中，我们也在研究如何将这些数据去中心化，不仅仅在 exping，也可以在未来你的其他 Web3 应用中被读取。

***最终，感谢你们。***
--------------


从上线至今，我们一直缺乏市场运营人员，缺乏许多推广知识。同时，很幸运有许多朋友转发，Newsletter 创作者在我们上线后，帮助我们宣传，非常感谢。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKZgrLQQNN0qVmceh1Ddt5v9AZjHEcH9ztDetgDr52NbV7ficqrXPm2Hg%2F640%3Fwx_fmt%3Dpng&valid=true)

***最后最后：***
-----------


感谢你花时间看到这里，我想分享一个对我起到很大鼓舞的鸡汤。

当很多人告诉我没人愿意下载应用了、这行不通、市场规模不够大等等担忧时，而这是让我们坚持做下去的原因：
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwn2z5va7cHWVg7kSUe30tKAJrXLkgHAqaBZ3SVcic4RgJDiao7ssd6AVn8UJAUvpd50ypNSdnJibiaCQ%2F640%3Fwx_fmt%3Dpng&valid=true)We choose to the moon演讲 我们决定在这十年间登上月球并实现更多梦想，并非它们轻而易举，而正是因为它们困难重重。
>
> 因为这个目标将促进我们实现最佳的组织并测试我们顶尖的技术和力量，因为这个挑战我们乐于接受，因为这个挑战我们不愿推迟，因为这个挑战我们志在必得，其他的挑战也是如此。  

我们正在招人！正寻找愿意接下挑战

一起把坑填了的**Flutter 工程师**

和想一起让更多人成为 Curator 的**运营负责人**

感兴趣欢迎找我聊聊：

hello@exping.world (备注：Clu收)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOwrEfPkm6zpGPspiaNmHzaQDFico8LliaxRhCoJsrIm2noGbhPqL5k43ZOBUtXmUgXp7wY54iatE3zmfw%2F640%3Fwx_fmt%3Dpng&valid=true)

**如** **何下载**

**长按下图识别二维码**

👇

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FFT0EakcgXOxQ9kLxybahNyvovkeibBPj5NhvPH2cODfOLssl6rsrfVuKfky6g8eYiaZicOoV8HpT5qaC8PVkN0y8g%2F640%3Fwx_fmt%3Dpng&valid=true)

**【 支持 iOS / 安卓系统 】**

**可在 App Store 或应用市场下载**

**也可在官网 exping.world 直接下载**

**-**

对 exping 有任何的想法或建议

欢迎加入用户反馈群

你每一次反馈，都是促进 exping 前进的动力

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_jpg%2FFT0EakcgXOwjEVr5kb10epupgHxcnGIo1TiaNAuQ2OE6hVt8wF0nmmlOdr2GDwLpUgeicjZyZIBDxofMlZdhCFLg%2F640%3Fwx_fmt%3Djpeg&valid=true)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_jpg%2FFT0EakcgXOwZL99kU6ehuuH5q7JibX800kxic2P0uymYzfIFYpmXfeickTkswD2cPWblZaItPITulHEOHPFloIwnA%2F640%3Fwx_fmt%3Djpeg&valid=true)

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7188493514227846046)
