创始人复盘：GitHub为什么能成功？
===================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/_IFCWNCikaW8eiGEghawzA)Founder Park Founder Park

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_gif%2FqpAK9iaV2O3sAVsSPfCN9UX44XiaoicbUJI6gOMAYyYuDxZ51FI70rCqWW323AoYLHYbdunn8eSQJYsh53EKoUssg%2F640%3Fwx_fmt%3Dgif%26from%3Dappmsg)


本文作者是 GitHub 联合创始人 Scott Chacon。网络上有很多分析 GitHub 成功的文章，他认为有些不太对，所以写了这篇文章，从内部人的视角分析了 GitHub 崛起与成功的原因。我们一起来看看他是怎么说的。

*** ** * ** ***

如果你想马上知道 GitHub 为何如此成功，以及你为何一直在使用它。我这儿有个精简版答案：

我将 GitHub 的成功归因于两个关键因素的完美结合。

* **GitHub 的推出时机堪称完美**

* **GitHub 很有品位**

GitHub 的四位联合创始人都有过失败的经历，无论是在 GitHub 之前还是之后。Chris 和 PJ 在 GitHub 之前没能让 FamSpam 成功，而 Tom 和我在 GitHub 之后也没能让 Chatterbug 火起来。

我认为这两个项目都很有品味，并且是很棒的产品，但它们都没能像 GitHub 那样成功。这可能是推出的时机不对，也可能是市场条件不成熟，或者还有其他原因。

GitHub 刚起步的时候，分布式开源版本控制工具开始变得既实用又稳定，逐渐被人们采纳，但在当时，几乎没有人（更不用说商业领域）真正认真地去托管这些工具。大公司看不上，小公司又因为不够专业够不着。

而那些后来注意到 Git 和 GitHub 崛起的竞争对手（比如 Sourceforge、Google Code 等）却缺乏那种独特的品味。他们似乎永远无法与一个以产品为中心的开源软件开发团队相抗衡。

我们非常注重开发者的体验，并且拥有足够的创造力，敢于打破常规，按照我们自己的理念去构建产品。而其他人则只是在构建他们认为能够吸引广告商或 CTO 的产品。

这就是 GitHub 能够胜出的原因。

原因已经说清楚了，如果你对具体细节感兴趣的话，请看下面内容。

文章转载自「AI 大模型实验室」。  

![](https://image.cubox.pro/cardImg/1ki1d6f6o4tz7kdwosiz6ag13q4x7nmixs0o6o1d7az2fx2del?imageMogr2/quality/90/ignore-error/1)

**AI大模型实验室**

关注大模型技术的创新与发展，探索大模型的实际应用，探讨 AI 未来对企业与社会发展的影响。

1131篇原创内容

公众号

，

**01**
------

****环境****
----------

让我们从开始一点一点的讲起。

我将站在 2005 年，一名软件开发人员的角度，来深入探讨「GitHub 的诞生时机恰到好处」这个主题。当时 Linus 提交了 Git 的第一个 commit，Olivia 提交 Mercurial 的第一个 commit。

20 年前软件开发是什么样的？又是怎样的环境让 Git 赢得了人心，并促使 GitHub 诞生的呢？

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FvHicVZXtcAzDaJWZ5wkYMsR2MYYxjCLNEnibribV78Asv0QOsppTo5P3S0VvriceMicgw9ADCTRmqlIX9iaadzDdjibiaQ%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

Mac OS Tiger，2005 年发布。如果你使用的是 Mac，它看起来像这样

如果你是 2005 年时的软件开发人员，你可能（希望）用的是 Subversion 这样的集中式版本控制系统。在 Git 出现之前，我用过 RCS、CVS、Subversion，还有 Perforce。记得我待过的一家公司，甚至直接用 FTP 把 PHP 文件传到服务器上。那时候，我们就是这么干的。

如果你当时在做商业专有软件开发，用 SVN 这样的集中式版本控制系统其实还算过得去。检出、修改、提交这些操作都很简单。虽然分支和合并做得不怎么样，但很多时候我们都能绕过去（说实话，我不确定自己是否真的在 Subversion 或 Perforce 里用过分支）。

说实话，现在人们抱怨 Git 的次数可能比当年抱怨 SVN 的还要多------毕竟，SVN 的用户界面和操作逻辑比 Git 要简单直观。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FvHicVZXtcAzDaJWZ5wkYMsR2MYYxjCLNE19OiaiaUGGFOjOb49CJ4ggR9icbPhNvfvf5aYCOGTuibDLh6KuwrGicqkmw%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

Perforce 2005.1 可视化客户端。我很讨厌这个软件。

我觉得当时最大的问题并不在于那些封闭、团队之间相互信任的专业开发环境。真正的挑战在于那个不断壮大的开源世界。

你可能不知道，开源在那时候亳不起眼，尤其是跟今天比起来。现在的人们可能都不记得开源项目还没那么多的时候，「开源」这个词直到 1998 年才被正式提出来。

为了让大家有个直观的感受，2008 年的时候，Dirk Riehle 发表了一篇论文，分析了全球开源项目的趋势。他估计那时候全球大概有 18，000 个活跃的开源项目。想想看，2005 年的时候，这个数字肯定还要更小。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_jpg%2FvHicVZXtcAzDaJWZ5wkYMsR2MYYxjCLNEpsFPGHyDAyPD5arKLsDqmPNn319IvQk2tW2gnsVia66SXJmFGwKz8Gw%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

开源项目总数。

摘自 2008 年 Amit Deshpande 和 Dirk Riehle 出版的《The Total Growth of Open Source》

比较一下，现在光是 GitHub 上就有超过 2.8 亿个公共代码库。

那么，为什么开源的兴起会推动 Git 和 GitHub 的流行呢？

主要是因为开源社区在快速扩张，而集中式版本控制系统在处理开放贡献方面表现很糟糕。简单来说，就是它们不擅长公开分享项目，也不擅长轻松地把外部的贡献整合进来。这对于开源项目来说，是个大问题。

**2005 年的开源贡献**

真的有那么糟糕吗？

通常是这样的，你可以让你的 Subversion 服务器对未认证用户设置为只读，这通常是托管开源项目的方式（或者你会偶尔把一个压缩包放在某个地方）。

如果你想要贡献代码，基本流程是这样的：

* 拉取最新版本

* 进行修改

* 通过 GNU diff 工具生成补丁文件

* 将该补丁文件上传到项目使用的工单系统或邮件列表中

接着，维护者需要：

* 下载补丁文件

* 应用到项目上，看看是否

<!-- -->

* 应用成功

* 工作正常

<!-- -->

* 然后提供反馈、做出修改，或者提交更改

现在网络上仍然可以看到这种流程的遗留痕迹。我曾在某个项目中使用 Trac 系统，你依然可以找到他们的「提交补丁」指南以及建议更改的示例。

这简直就是一场噩梦。

Rails 项目和我的那帮朋友们------也就是后来的 GitHub 联合创始人们------在 Err 公司用了一个叫做 Lighthouse 的工单系统，让人惊讶的是，它居然还在运行。我早期的一个开源项目是一个命令行工具，叫做 git-lighthouse，它的功能是简化从工单中下载和应用补丁的过程。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FvHicVZXtcAzDaJWZ5wkYMsR2MYYxjCLNEUKEv5qTxicc1iaLyljiacXQ1zZGqBeeryW7JnPD63bAGGr0fmicG3m2tQg%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

下面是早期提交给 Rails 项目的补丁的 3 个不同版本的示例。

这个过程实在是太糟糕了，所以当有个工具能够简化这个过程时，大家都迫不及待地用上了。这个工具就是 GitHub。不过，在这之前，我们得先有 Git。

**Git 的崛起**

Git 的诞生其实有点戏剧性，Linux 内核大佬。Linus Torvalds 当时特别喜欢一个商业的版本控制系统，叫做 BitKeeper。这个系统本来是为了简化内核开发流程设计的。

**如果 BitKeeper 是开源的，或者它的许可条款更友好一些，可能就不会有 Git 或者 GitHub 了。**

但事情就这么巧。有个 Linux 开发者违反了许可条款，反向工程破解了 BitKeeper 的协议。这搞得 BitKeeper 和 Linus 都很不爽，最后决定分道扬镳。

于是，Linus 就结合了 BitKeeper 的一些好想法，自己搞了个工具，他觉得这个工具能解决问题。他还开玩笑地叫它「来自地狱的信息管理器」，并将这个项目命名为 Git。

Git 很快就在 Linux 社区里火了起来，有几个人觉得这个项目不错，慢慢地，Git 就发展成了一个真正的版本控制系统。

当时 Git 之所以受到欢迎，有这几个原因：

* 分支和合并不再是噩梦，而是梦想

* 它速度飞快

* 权限管理变得非常简单

Git 刚出来那会儿，我做过一些现场演示，就是那种一边讲一边操作的。我会现场创建几个分支，提交些更改，然后在这些分支之间切换，最后再合并。整个过程一气呵成，60 秒搞定。我还记得，当时真的有人看得目瞪口呆，甚至有人怀疑我是不是作假了。

想想看，2006 年的时候，能这么快、这么轻松地切换和合并代码，真的就像魔术一样。相比之下，在 Subversion 里做这些，简直就是一场噩梦。

不用跟中央服务器来回协商就能提交代码，这感觉就像是在开火箭，一切都快得飞起。

可能最关键的是，你可以轻松地 fork 代码库，这意味着你可以自己托管一个副本，拥有写权限，在自己的分支里提交更改，别人也可以轻松地把这些更改拉到他们的 fork 里。Linux 项目很早就开始这么做了------对于较大的更改，他们可以请求 Linus 从他们托管的分支里拉取更改，而 Linus 做起来也是轻而易举。

实际上，如果你好奇「拉取请求（Pull Request）」这个词是怎么来的，答案就在这里。Git 里有个 git request-pull 命令，它会帮你格式化一封邮件，发送到邮件列表，简化这个过程。当 GitHub 加上这个功能后，我们决定就叫它「拉取请求」。

有些人觉得开发者喜欢 Git 是因为它分布式的特性，克隆时能拿到整个历史记录，这样你就可以在本地做各种操作，等等。但我不这么认为。分布式之所以酷，主要是因为操作快，你可以轻松地托管自己的完整可写 fork，权限管理变得超级简单。

确实，这种变化让贡献变得更简单了。不再是「谁有权限推送」，而是「谁有有趣的内容可以拉取」，这种转变直接推动了 GitHub 的诞生。

**GitHub 的崛起**

去年年底，我与我的 GitHub 合伙人 Tom 进行了详谈。我们聊了好多，他讲述了他最初是如何萌生开发 GitHub 的想法的。

当时他在 Powerset 工作，团队开始用 Git。但是，因为 Git 主要用 SSH 协议，给每个人设置 SSH 权限太麻烦了。大多数人觉得这事儿不值得费心。这个痛点让 Tom 有了灵感：得让这事儿变得简单点。

Git 是挺棒的，但托管 Git 却很麻烦。这就是 Tom 开始开发 GitHub 的原因。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FvHicVZXtcAzDaJWZ5wkYMsR2MYYxjCLNEnUicYsQdnmhL97amVL346fZxTdTunFVkibcSc11icM91WgrQjP7dBcMtA%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

为什么要创建 GitHub？为了减少麻烦。

我翻了翻旧邮件，想看看我第一次听说 Tom 的「GitHub」项目是啥时候。发现是 Chris 在 2007 年底回复我 Git 视频教程的邮件。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FvHicVZXtcAzDaJWZ5wkYMsR2MYYxjCLNEibxyB28ECPpAc1H40hMThnAVSaQzibYLtZiakicaM4gT3muHOorWyAAwLQ%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

那时候，GitHub 还是 Tom 和 Chris 的秘密项目（还有 Chris...... 为啥「h」是小写？），我开始和 Chris、Tom 聊 Git/Ruby 库和网站的事，慢慢也就参与进来了，最后加入了公司。

这个项目有几件有趣的事情。

首先，他们把 GitHub 和当时唯一一个真正的公共 Git 托管站 repo.or.cz 做了比较。但 GitHub 做了个关键的创新，就是它以用户为中心，而不是以项目为中心。以前在 Sourceforge 之类的地方托管项目，你得抢注名字。而在 GitHub，你可以随便给项目起名字，因为它是按用户命名空间划分的。

其次，他们关注的是「拉取」模型，而不是「推送」模型（这跟我之前说的权限问题有关）。

第三，「不丑」也是一大卖点。GitHub 的设计很有品味。

**02**
------

****Git 的胜利****
---------------

**Git 一开始之所以受欢迎，是因为它的设计理念和功能都很强大，而 GitHub 的创建则是为了让 Git 更加易于使用。**但问题是，为什么 Git 最终能在众多分布式版本控制系统（DVCS）中脱颖而出呢？当时有很多类似的工具，比如 Mercurial，在很多方面和 Git 很像，甚至在某些方面做得更好。那么，为什么在这场 DVCS 的竞争中，Git 笑到了最后？

**我认为答案是「PR」。**

在「为什么 Git 胜出」这个问题上，有两个非常强大的公关力量在起作用。首先是 Linux，可以说是 Linus 本人。其次是 GitHub，尤其是 Rails 社区。

**也许是 Linus/Linux**

Linux 项目选择了 Git，而且还是 Linus 发起的，这直接给了 Git 一个权威背书。

大家都知道 Linux，也都知道 Linus。如果他能搞出一个几乎人人都在用的优秀操作系统（至少在服务器领域是这样，而且每年都有人说明年就是桌面 Linux 的时代），那他肯定也能开发出一个顶尖的版本控制系统。就算 Git 一开始用着有点难，那也只能说明他比我们聪明，我们得多花点功夫学学，对吧？

2007 年的时候，有一个关于 Git 的在线讲座，当时 Linus 在 Google 园区里讲 Git 和 DVCS，那时候这还是个全新的概念。

视频链接：https://youtu.be/4XpnKHJAok8

视频发布的时候，正好是我刚开始用 Git（2005 年底）和我加入 GitHub（2008 年中）之间的那段时间。我看了好几遍，肯定还有几百万人也看过。谁不想听 Linux 的大神在 Google 说「CVS 是有史以来最傻的东西，不同意的人都是又丑又蠢」呢？

这是一个很棒的公关活动。

而且，如果你把 Linux 和 Linus 等同起来（大多数人确实这么认为），那可以说，Linux 通过 Android 间接地也推动了 Git 的普及。

在推动 Git 普及这方面，有时候真的很难说，是我或者 GitHub 的努力，还是 Android 成为趋势背后的这种巨大而低调的幕后推动力，哪个影响更大。毕竟，我自己多年来也一直在做 Git 的演讲和企业培训。

2008 年 9 月初，就在 Android 1.0 发布前夕（大约是这封邮件发出两周后，也是在我做培训之前），Git 生态系统的早期英雄之一 Shawn Pearce 给我发了封邮件，邀请我帮忙培训 Google Android 团队使用 Git。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FvHicVZXtcAzDaJWZ5wkYMsR2MYYxjCLNE78kEz3qFFialhPqHTY6Iiciaica39TaIyVSGwd8BXuFyKq0L3Voxrh0wOA%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

虽然很难精确衡量 Android 在推动企业采用 Git 方面的作用，但它的影响肯定不是零。Google/Android 团队是我以 GitHub 名义做的第一个企业培训对象，后来我还为摩托罗拉、高通、爱立信和博通等电信公司的工程团队做了 Git 培训。这还是在我们雇了全职团队专门来做这些培训之前的事。

**Linus 用他那广泛的超级极客公关效应推动了 Git，这种影响力是 Mercurial 从未获得的**。而 Android 通过它对 Linux 内核的依赖，进一步独特地推动了 Git 的传播，让它进入了大量企业，这些企业原本可能至少在十年内都不会采用 Git。

**也许是 GitHub**

带着一点谦虚和希望，我得说**，GitHub 很可能是让 Git 最终战胜 Mercurial 的关键。**

GitHub 真的很幸运，因为我们有一个非常支持我们、也很前卫的社区------Ruby 社区。从一开始，Ruby 社区就全力支持我们。没几个月，Ruby 社区的每个人都把他们的项目搬到了 GitHub 上。那时候，Rails 是非常火的技术，比 PHP 更酷，JS 框架还没出现，也没有 Node 这些技术。

所以，大家都在关注 Ruby 社区那些潮流开发者的动态，因为他们是软件世界里最前沿的开发者，而他们都在用 GitHub。

不只是我这么看，Linus 最近也说，从他的角度来看，Ruby 社区让 Git 一夜之间意外地火了。他虽然没有直接提到 GitHub，但我觉得没人能否认，Ruby 社区没有采用 Git，很大程度上是因为 GitHub 的存在。

通过一些推测和推理，我敢大胆地说**，Linus 实际上认为 GitHub 是让 Git 取胜的原因。**

当然，Ruby 社区的采用 GitHub 并非偶然。

我记得我们几个------Chris、Tom、PJ 和我------在 Ruby 会议上和 Ruby 社区的早期成员们坐在一起，向他们展示 GitHub，介绍 Git，做演讲。我们一起演讲，之后还会在旧金山的 Ruby 聚会上一起喝啤酒。这些人是 Rails、Heroku、Twitter、jQuery 等项目的创始人。

我们并不是在「推销」GitHub，而是在分享我们真正热爱的东西。这个社区非常信任彼此，GitHub 的创始人也是这个社区的深度且真诚的成员，我们都在尝试彼此的项目并互相支持。

Ruby 社区使用 GitHub 意味着每场会议的演讲都会提到 GitHub。这种免费宣传无处不在。随着越来越多的项目迁移到 GitHub 或者直接在 GitHub 上启动，即使是那些喜欢 Mercurial 的人也没有太多选择，最终他们不得不转向 Git。一段时间后，继续使用 Mercurial 就变得不太值得了。GitHub 在托管领域的主导地位在短短几年内就超越了 Mercurial。

在 Mercurial 那边，有 BitBucket，它是专门为 Mercurial 托管设计的，是用 Django 框架写的。但我觉得我们起步早，优势大，而且它们也没做出足够的差异化。Python 社区也没有像 Ruby 社区那样积极地采用它。

早在 2008 年 12 月，GitHub 就已经托管了大约 27,000 个公共仓库，而 BitBucket 只有 1,000 多一点。要追上我们，确实挺难的。

你可能会好奇我怎么记得这些数字。其实，我当时建了个网站叫 whygitisbetterthanx.com，有个叫 Jesper 的人给我发邮件，说我网站上有个错误------我当时的论点是，Git 有 GitHub，而 Mercurial 和 Bazaar 没有类似的托管平台。我当时挺傲慢地回他说，它们根本不是一个量级的。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FvHicVZXtcAzDaJWZ5wkYMsR2MYYxjCLNEF2jA6nogMMiciatCZtib5edS65CeZFbzbwQzzuI1YXUXbUKHWzuHicfcaw%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

年轻的 Scott 有点暴躁。对不起，Jesper。

很高兴 Jesper 并没有因为我的回应而生气，现在想起来我那时候语气确实有点冲。但最后证明，Jesper 其实是 BitBucket 的创始人。这真的很尴尬。

大概一年后，我们在阿姆斯特丹见了面，一起喝了几杯威士忌，从那以后我们就一直保持着友好的关系。

**竞争对手的消失**

最后，不管是 GitHub 帮了 Git 一把，还是 Git 帮了 GitHub 一把，这场竞争很快就有了结果。

2006-2007 年的时候，大家开始认识到分布式版本控制系统的好处，Git 和 Mercurial 也开始了正面交锋。

2008 年，GitHub 正式登场。

到了 2011 年，Google Code 和 BitBucket 都开始支持 Git，我觉得这差不多就是给 Mercurial 敲响了丧钟。Git 赢得了这场战争，GitHub 也变得几乎无人能敌。

仅仅 4 年后，2015 年，Google Code 彻底退出了历史舞台，关闭了服务。他们甚至在邮件里建议大家直接转移到 GitHub。如果我没记错的话，他们还联系了我们，寻求帮助进行迁移服务。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FvHicVZXtcAzDaJWZ5wkYMsR2MYYxjCLNEwWoHaLsSsW1CmbvWB02wssmPe90MDae7K8l4KIqQqaFc6cMQStAD3w%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26tp%3Dwebp%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1)

**03**
------

****那么，为什么不是 Google Code 胜出呢？****
---------------------------------

这是个好问题。尽管 BitBucket 是在我们之后启动的，我们有一些先发优势。不过，在我们之前也有其他托管网站。那么，为什么它们没有胜出呢？  

2009 年初，Google Code 增加了 Mercurial 支持，Sourceforge 也增加了 Git 和 Mercurial 支持。因此，如果这些行业巨头拥有用户群优势，并在我们上线几个月后就支持了 DVCS，为什么他们没有击败我们这些小公司？

2009 年初，Google Code 开始支持 Mercurial，Sourceforge 也开始支持 Git 和 Mercurial。这些行业巨头拥有用户群优势，而且我们刚上线没几个月他们就支持 DVCS 了，怎么就没把我们这个小团队比下去呢？

我们不仅小，还没啥钱。Chris 当时拿出了一点钱来启动公司（如果我没记错的话），其他人包括我都是两手空空，我们也没有筹集到任何外部资金。

Google Code 增加 Mercurial 支持时，我们四个开发者还在南海滩的咖啡馆里敲代码呢，连风险投资都没有。我们与 Engine Yard 的伙伴达成了协议（2008 年 5 月），他们帮我们支付托管费，因为我们是真的没钱。

那我们这个又小又没钱的团队是怎么在几年内让 Google Code 这样的大团队倒下的呢？

**GitHub 有品味**

上面提到了，其他托管平台关注的是分发和赚钱。**我们关注的是开发者。**问题不在于他们什么时候支持 Git，那不重要。他们不懂什么是品味，也不关心开发者的工作流程。他们可以加 Git 支持，但我觉得即使加了，最后也会失败。

这不仅仅是功能或「增值服务」的问题，对于今天的初创公司来说，真正有价值的核心经验比活动提要或个人页面这些功能更根本。我觉得我们做的最根本的事情是：我们为自己而构建。我们有品味，我们在乎用户体验。

我们都是开发者**，我们做的是我们自己****想要的工** **具，支持我们理想中的工作方式。**我们是唯一一个**为开发者而不是为赚钱优化**的工具，没有产品经理、会计师或 CEO 在那儿想着怎么利润最大化，我们真正关心的是开发者体验。

最后我们赢了，因为开源社区开始转向分布式版本控制系统，而我们是唯一真正关心开发者工作方式的托管平台。我们是唯一质疑现状、从第一性原理出发、尝试整体改进体验的平台，而不是仅仅在现有基础上加更多功能来销售。

**04**
------

****总结****
----------

总结一下，我们之所以能赢，是因为我们抓住了时机，而且我们的产品有品味。我们站在了新范式的前沿，并且我们是以开发者体验为核心来帮助大家接受这个新范式的，这点别人都没做到。

那么问题来了，下一个改变开发者工作流的大变革会是什么？谁又会有那种品味，让它能像 GitHub 那样一炮而红呢？

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FqpAK9iaV2O3sAVsSPfCN9UX44XiaoicbUJIqSBuicUxZh7Gk9P7e64GsY96M2ibY3fSgldrt7WbtLdkzZHLh4Npeu3A%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1%26tp%3Dwebp)](http://mp.weixin.qq.com/s?__biz=Mzg5NTc0MjgwMw==&mid=2247498686&idx=1&sn=73438da0762cdc2b2f77097a24804dfb&chksm=c0091d82f77e9494acd591196c48d2c197348d95d19b8590e1c43dc26e7bb10bc367506b6e93&scene=21#wechat_redirect)


*** ** * ** ***

**更多阅读**

[2030年，Scaling Law会到达极限吗？GPT-6能出来吗？](http://mp.weixin.qq.com/s?__biz=Mzg5NTc0MjgwMw==&mid=2247506735&idx=1&sn=09918a43c08c2b2ba8666517f9e9a433&chksm=c0093d13f77eb405a99a98dd1735226958d331712628867aeb8855220926b5129ac83b0ff9d6&scene=21#wechat_redirect)

[离开OpenAI，独自创业之后，Karpathy对AI更乐观了](http://mp.weixin.qq.com/s?__biz=Mzg5NTc0MjgwMw==&mid=2247506781&idx=1&sn=ad818307eef6a43ad08037737e0c1134&chksm=c0093d61f77eb4771377cdf6a9113e2eaac85e3915d64b78d56d94211c369f9de7982f358bf6&scene=21#wechat_redirect)  


[去 Discord 做社交游戏吧，这是 a16z 的 AI 创业建议](http://mp.weixin.qq.com/s?__biz=Mzg5NTc0MjgwMw==&mid=2247506542&idx=1&sn=604d5d679b095e887a39fb960163c235&chksm=c0093c52f77eb544b3443af3ab07c8af8f75b7869449bd2cf5509bcd9b3eb4b1872cd7a477d5&scene=21#wechat_redirect)

[Cursor创始人万字访谈：全球爆火的AI编程应用，真正找到PMF](http://mp.weixin.qq.com/s?__biz=Mzg5NTc0MjgwMw==&mid=2247506734&idx=1&sn=b2de13297470bbeb0ddff10df27c289e&chksm=c0093d12f77eb404ba3e3f19308ce82c0d2eb95cb553c6f83fe8cc77360a1f06cf09d91a4b64&scene=21#wechat_redirect)


![](https://image.cubox.pro/cardImg/49ptyqcouzc9s3xbvbkji7igwiujtno1uzwe4pm8wftkt6j5kq?imageMogr2/quality/90/ignore-error/1)

**Founder Park**

来自极客公园，专注与科技创业者聊「真问题」。

299篇原创内容

公众号

，

转载原创文章请添加微信：founderparker

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7233715633983064280)
