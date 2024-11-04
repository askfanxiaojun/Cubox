如何用 ChatGPT 帮你自动分析数据？ - 少数派
===========================

[sspai.com](https://sspai.com/post/79800)玉树芝兰

**Matrix 首页推荐**

[Matrix](https://sspai.com/matrix) 是少数派的写作社区，我们主张分享真实的产品体验，有实用价值的经验与思考。我们会不定期挑选 Matrix 最优质的文章，展示来自用户的最真实的体验和观点。   
文章代表作者个人观点，少数派仅对标题和排版略作修改。

*** ** * ** ***

![](https://image.cubox.pro/article/2023051514003810034/56037.jpg?imageMogr2/quality/90/ignore-error/1)

误**判**
------

好几天之前，我就在 ChatGPT 选单里看到了 Code Interpreter。它正在灰度测试中 ------ 先给一部分用户试用，如果反响不错并做了一定改进，就能推广给更多用户。
![](https://image.cubox.pro/article/2023051514003882971/31316.jpg?imageMogr2/quality/90/ignore-error/1)

可惜当时我没能正确理解它的含义，犯了一个大错误------望文生义。我以为 Code Interpreter 是指「代码解释器」，也就是给代码添加注释进行讲解的。可那不是 ChatGPT 早就有了的功能吗？干嘛还专门弄个新的模式出来呢？

后来经朋友提醒我才发现，Code Interpreter 的功能不是「解释代码」，而是**执行代码** 。在这个模式下，你可以上传文件作为输入，让 Code Interpreter 编写代码对输入文件做处理，并且**在自带的虚拟环境中执行**。根据代码内容的不同，它可以利用文本、数字、图形、表格等方式给你展示结果，甚至还可以给你一个下载链接，把你指定的输出以文件形式下载回本地。

当我意识到这一点时，真可以用「惊讶」和「懊恼」来形容。我迫不及待尝试后，赶紧写作本文，告诉你这个功能。以免你跟我一样望文生义，重蹈覆辙。

下面我用一个实际的例子给你演示。

**实**例
------

首先我们需要一个演示数据集。这里我选择了一个名为 `loans.csv` 的贷款安全数据集。它是一张表格，属于简单结构数据，其中包含若干行，每一行代表一条贷款记录；而每列则代表某一相关属性特征，例如贷款等级，房屋拥有情况，贷款时长等信息。

最后一列 `safe_loans` 代表贷款成功或失败，也即这次放款是否安全。其中 `-1` 代表不安全。`1` 代表贷款安全回收。
![](https://image.cubox.pro/article/2023051514003994744/36007.jpg?imageMogr2/quality/90/ignore-error/1)

首先我们需要将数据集上传到 Code Interpreter 中。上传按钮很不显眼，在输入框的旁边。
![](https://image.cubox.pro/article/2023051514003842070/95355.jpg?imageMogr2/quality/90/ignore-error/1)

上传后，Code Interpreter 会自动进行分析，并为每列数据提供解释。
![](https://image.cubox.pro/article/2023051514003979703/65362.jpg?imageMogr2/quality/90/ignore-error/1)

我点击了「show work」来看看究竟 Code Interpreter 是如何分析出上述结果的。
![](https://image.cubox.pro/article/2023051514003944779/35257.jpg?imageMogr2/quality/90/ignore-error/1)

原来，Code Interpreter 直接编写了 Python 代码，读取了上传后的 `loans.csv` 文件，然后执行 `head ()` 命令，打印出来前 5 行，根据列名称和具体显示的数据综合分析信息，然后做了回答。

**提**示
------

数据已经准备好，我们现在可以开始输入提示语了。我觉得使用英文与 Code Interpreter 对话很别扭，因此我提出：
> 请用中文翻译上面的内容，并且对于专业术语加以简单明了的解释。谢谢

你可能会纳闷儿，老师你干嘛要这么客气呢？不就是个机器......🤫，别瞎说。礼多人不怪，AI 也一样。你跟它客气，它回答起来也会比较认真。在《[人工智能这么强，我直接把工作都交给它可以吗？](https://sspai.com/link?target=https%3A%2F%2Fxiaobot.net%2Fpost%2Ffbff0743-6718-4ba7-89aa-629cde1cfd89)》一文中，我给你解释过具体的证据。

闲言少叙，这是 Code Interpreter 返回的结果。
![](https://image.cubox.pro/article/2023051514003959227/57704.jpg?imageMogr2/quality/90/ignore-error/1)

你看，用中文回答是不是感觉好多了？对比一下你就会发现，这里的「可循环信贷利用率」等专业术语，都已有具体解释了。Code Interpreter 还在最后提出「告诉我您希望对这些数据进行哪种分析或任务」。

此时，你可以要求 Code Interpreter 做一些简单分析，并要求绘制图表（如分布图）。但对于我而言，这样的机械操作实在太无趣了 ------ 每个步骤都需要我来提示，那我还要你这 AI 干啥？

**计划**
------

因此，我的下一个提示语，是这样的：
> 能否根据目前的数据集，思考它可以做哪些分析？请一步步思考，并且给我你有信心的答案。谢谢

注意这一段提示语中的两个技巧，你可以尝试吸收：「一步步思考」是尝试启动大语言模型的思维链；「有信心的答案」是指设定阈值，避免 ChatGPT 天马行空随意乱答。

这是 Code Interpreter 的反馈结果。
![](https://image.cubox.pro/article/2023051514003933543/99822.jpg?imageMogr2/quality/90/ignore-error/1)

Code Interpreter 列出了可能的分析类型。

第一步是描述性分析，比如基本数量分布等。

第二步是相关性分析，总结其他变量间的相关性。

第三步是建立预测模型，其中提到了决策树，随机森林和逻辑回归等方法。也提到必须将之分为训练及测试数据集，且要「使用测试级来评估模型性能」。这种意识非常棒，已经超出了机器学习常见入门水平。

第四步就有点儿莫名奇妙了，虽然 Code Interpreter 提出使用支持向量机 (SVM)、朴素贝叶斯等几个新模型，但要做的事情和第三步是重复的。

好在，**我们使用 AI 作为助手，而不是枪手**。我们大可以将第四种分析类型省略，只让 Code Interpreter 将前三个步骤做一下。这里为了方便展示，我让 AI 一次只做一个步骤。下面是执行各个步骤的效果。

**结果**
------

第一步，描述性分析。Code Interpreter 给出了这个数据集的一些基本统计信息。包括记录数量、最常见的贷款等级、平均被雇佣不足一年人员数量、平均雇佣年限、平均债务收入、最常见贷款期限数量等。
![](https://image.cubox.pro/article/2023051514003964202/89189.jpg?imageMogr2/quality/90/ignore-error/1)

第二步，相关性分析。Code Interpreter 识别出属于不同变量之间的正负相关关系。例如，短期雇佣与雇佣年限是相反的概念，因此 `short_emp` 和 `emp_length_num` 之间存在负相关性；债务收入比高的贷款申请者往往会使用循环信贷，因此 `dti` 和 `revol_util` 之间存在正相关性；而 `safe_loans` 和一些其他变量之间存在负相关性，这意味着对那些高债务收入比的人贷款，可能不太安全。
![](https://image.cubox.pro/article/2023051514003887211/87092.jpg?imageMogr2/quality/90/ignore-error/1)

Code Interpreter 还不忘提醒咱们，这些**相关性不意味着因果关系**，尚需要考虑更多变量的交互和非线性关系。如果是我的学生回答此题，仅仅最后这一句，就会让我非常欣慰。

第三步，构建预测模型。
![](https://image.cubox.pro/article/2023051514003912276/73228.jpg?imageMogr2/quality/90/ignore-error/1)

Code Interpreter 中规中矩地进行了数据预处理。
![](https://image.cubox.pro/article/2023051514003953471/75130.jpg?imageMogr2/quality/90/ignore-error/1)

我看了一下具体执行的代码：
![](https://image.cubox.pro/article/2023051514003813129/31933.jpg?imageMogr2/quality/90/ignore-error/1)

之后是模型的训练和性能测试环节。
![](https://image.cubox.pro/article/2023051514003948095/66114.jpg?imageMogr2/quality/90/ignore-error/1)

点开 `show work`，对应的代码是这样：
![](https://image.cubox.pro/article/2023051514003865590/35682.jpg?imageMogr2/quality/90/ignore-error/1)

之后，Code Interpreter 自动进行了结果的汇总输出与阐释。
![](https://image.cubox.pro/article/2023051514003857195/66330.jpg?imageMogr2/quality/90/ignore-error/1)

该模型在测试数据集上的准确率为 61.7%。虽然不高，但 Code Interpreter 指出相对于随机预测的准确率 50%，还是要好一些。有意思的是，它还自动提出了如何对准确率进行提升。例如超参数优化、特征工程、使用其他模型等。特别地，Code Interpreter 提出需要不仅仅关注准确率，还要考虑模型可解释性、训练和预测时间等其他指标。

非常好！不过你是说，让我自己去逐一尝试上述提升策略？那怎么可能？！Code Interpreter 既然你画了道儿，就得你来走嘛。

于是我这样提问：
> 你能否实施改进策略，并且在同样的测试集上进行测试？谢谢

这是 Code Interpreter 的回答。
![](https://image.cubox.pro/article/2023051514003986014/69418.jpg?imageMogr2/quality/90/ignore-error/1)

你看？AI 开始认真干起来了不是？

这是 Code Interpreter 一通改进之后的结果：
![](https://image.cubox.pro/article/2023051514003992250/22258.jpg?imageMogr2/quality/90/ignore-error/1)

从 61.7% 提升到了 64.9%，准确率高吗？我觉得谈不上。但是这是一个非常有意思的开端，意味着 Code Interpreter 可以自动帮助我们执行提升准确率的策略，而且获得了成效。

**小结**
------

我想跟你谈谈尝试 Code Interpreter 之后的感受。我想用「惊艳」二字来形容。具体来说，就是「分析得当，执行流畅」。

咱们应该思考一下 Code Interpreter 出现的意义。曾几何时，很多小伙伴拿到宝贵的一手数据，却不知道如何分析。在几年前，你会看到很多不同学科的人一窝蜂跑去学习 Python。因为在彼时，只有学会了 Python 或者 R 后，你才可能对数据进行功能丰富且合理可行的分析。很多人因为不具备相关的技术能力，往往坐拥金山，但就是不知道怎么挖掘。

要学完 Python 或者 R 的初级操作，你至少需要学一门课程，或者啃一本教材。但是现在，你只需要和 Code Interpreter 对话，就能把这样的分析结果保质保量快速做出来，甚至比数据分析师基础入门水平都要靠谱，不亦乐乎？

ChatGPT 的 Code Interpreter，目前还在 Alpha 阶段。功能非常初级，时常遇到环境更新导致的不稳定，还有各种限制。例如说你可以让它帮你绘制统计图，英文显示都很好，但所有中文显示都是这个样子：
![](https://image.cubox.pro/article/2023051514003985278/59258.jpg?imageMogr2/quality/90/ignore-error/1)

你当然可以让 Code Interpreter 自己去改进。但是它折腾一通，也只能给你展示这种无奈：
![](https://image.cubox.pro/article/2023051514003961425/42781.jpg?imageMogr2/quality/90/ignore-error/1)

但是，我们有理由相信，这些问题随着技术产品的迭代改进，都会逐步解决的。

你在数据分析的过程中，使用过其他的 AI 产品吗？有什么可以推荐给大家的？欢迎留言，咱们一起交流讨论。

祝（自动）数据分析愉快！

如果你觉得本文有用，请**充电**。

如果本文可能对你的朋友有帮助，请**转发**给他们。

欢迎**关注** [我的专栏「科研利器」](https://sspai.com/column/245)，以便及时收到后续的更新内容。

[点击这个链接加入少数派会员](https://sspai.com/post/%E7%82%B9%E5%87%BB%E5%8A%A0%E5%85%A5%E5%B0%91%E6%95%B0%E6%B4%BE%E4%BC%9A%E5%91%98%EF%BC%8C%E7%AB%8B%E4%BA%AB%209%20%E6%8A%98%E4%BC%98%E6%83%A0%EF%BC%81%E8%8E%B7%E5%BE%97%E4%B8%93%E5%B1%9E%E4%BC%9A%E5%91%98%E5%86%85%E5%AE%B9%E3%80%81%E4%BC%9A%E5%91%98%E6%92%AD%E5%AE%A2%E4%BB%A5%E5%8F%8A%E4%BC%9A%E5%91%98%E5%AE%9A%E5%88%B6%E5%91%A8%E8%BE%B9%E3%80%82%E5%9C%A8%E6%9B%B4%E5%A4%9A%E7%9A%84%E9%A2%86%E5%9F%9F%E5%92%8C%E6%96%B9%E5%90%91%E5%B8%AE%E4%BD%A0%E6%89%93%E5%BC%80%E8%84%91%E6%B4%9E%EF%BC%8C%E6%89%BE%E5%88%B0%E6%96%B0%E7%9A%84%E5%85%B4%E8%B6%A3%E7%82%B9%EF%BC%8C%E4%B8%8E%E5%B0%91%E6%95%B0%E6%B4%BE%E4%B8%80%E8%B5%B7%E6%B4%9E%E6%82%89%E5%BD%93%E4%B8%8B%EF%BC%8C%E6%8E%A2%E7%B4%A2%E6%96%B0%E7%9F%A5%E3%80%82)，立享 9 折优惠！获得专属会员内容、会员播客以及会员定制周边。在更多的领域和方向帮你打开脑洞，找到新的兴趣点，与少数派一起洞悉当下，探索新知。

![](https://image.cubox.pro/article/2022082814591164171/11602.jpg?imageMogr2/quality/90/ignore-error/1)

经验卷轴：入门学术论文写作

用二十余年的科研经验带你入门学术写作

¥59.00

**延伸阅读**
--------

* [AI 帮我找卡片挺好，但能不能帮我创作出新的相关卡片啊？](https://mp.weixin.qq.com/s/u9ynbqiviA79Uzy3wDLjVA)
* [摸索那么多工具后，怎样才能避免「效率成瘾」？](https://sspai.com/post/77552)
* [自己录制和剪辑视频，如何解决占用空间过大的问题？](https://sspai.com/post/74366)
* [想打造个性化高效工作流，可不会编程怎么办？](https://sspai.com/post/70656)
* [世界很大，英语不好的你如何去看看？](https://mp.weixin.qq.com/s/oLdU7312PUw8zvGpdlvtTg)

\> 下载 [少数派 2.0 客户端](https://sspai.com/page/client)、关注 [少数派公众号](https://sspai.com/s/J71e)，解锁全新阅读体验 📰

\> 实用、好用的 [正版软件](https://sspai.com/mall)，少数派为你呈现 🚀

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7057638013655842817)
