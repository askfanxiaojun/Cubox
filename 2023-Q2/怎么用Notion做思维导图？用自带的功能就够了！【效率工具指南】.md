怎么用Notion做思维导图？用自带的功能就够了！【效率工具指南】
=================================

[penghh.fun](https://penghh.fun/2022/11/27/2022-11-27-notion_mindmap/)Angola Peng

本文首发于微信公众号「[效率工具指南](https://mp.weixin.qq.com/s/LGb-13wwZEcp5yKo_3APwQ)」  
文/彭宏豪

Hello 各位好，我是小豪。

众所周知，Notion 非常强大，集成了多种功能，但唯独少了思维导图。

关于这个问题，我之前也找了一些方法，思路都是在 Notion 中嵌入带有思维导图功能的第三方网页应用，例如：

* BoardMix博思白板
* Miro
* Whimsical

👉想了解使用第三方导图应用的方法，可以查看我之前在 B 站发布的视频：

[活久见！笔记软件Notion也能制作思维导图啦！【效率工具指南】](https://www.bilibili.com/video/BV18e411u7RR/)

除了这些，我最近还看到了另外一个不错的方法，不需要借助第三方应用，使用 Notion 的**代码块**，就能直接在 Notion 中创建思维导图。

创建的思维导图如下：

[![](https://image.cubox.pro/imtwg9/cover/2023020317140177341/article.jpg)](https://article-picbed-1302715071.cos.ap-guangzhou.myqcloud.com/2022/11/27/16695237621440.jpg)

这个方法的优点：

* 不需要借助外部应用，完全免费
* 不需要创建或登录账号
* 可以随时修改
* 可以添加无限多的导图节点

当然，这种方法也存在一些缺点，譬如：

* 无法在导图节点中插入图片
* 功能不如专业的思维导图软件那么丰富
* 还有可能少数人会觉得绘制起来比较麻烦（这个我还能接受）

看完使用 Notion 代码块绘制思维导图的优缺点，接下来就来看看如何绘制吧～

在 Notion 中输入斜杠 `/code`，点击下方返回的 Code，添加一个代码块。

[![](https://image.cubox.pro/imtwg9/cover/2023020317140170061/article.jpg)](https://article-picbed-1302715071.cos.ap-guangzhou.myqcloud.com/2022/11/27/16695241623814.jpg)

点击代码块左上角「向下」的小箭头，在弹出面板的搜索框输入 **Mermaid** 并单击，将代码块所使用的语言设置为 Mermaid。

[![](https://image.cubox.pro/imtwg9/cover/2023020317140162163/article.jpg)](https://article-picbed-1302715071.cos.ap-guangzhou.myqcloud.com/2022/11/27/16695242610462.jpg)
> 补充一点小知识：
>
> 这里选择的 Mermaid 语言，是一个基于 JavaScript 的图表和图表工具，它使用受到 Markdown 启发的文本定义和渲染器，来动态创建和修改图表，例如**流程图、时序图、类图、状态图、用户旅程图、甘特图、饼状图、需求图、Git 分支图、思维导图**等。
>
> Mermaid 的主要目的是帮助文档跟上开发的步伐。
>
> 了解更多与 Mermaid 有关的内容，可以在浏览器中打开 Mermaid 的帮助文档：<https://mermaid-js.github.io/mermaid/#/README>

选择 Mermaid 语言后，在代码块中输入类似下图的内容，就能渲染得到一个思维导图。

    graph LR;
    公司架构-->商务
    公司架构-->研发
    公司架构-->设计
    公司架构-->运营
    公司架构-->产品

[![](https://image.cubox.pro/imtwg9/cover/2023020317140265659/article.jpg)](https://article-picbed-1302715071.cos.ap-guangzhou.myqcloud.com/2022/11/27/16695286652598.jpg)

简单解释一下输入的这些内容/符号的含义：

第一行的 graph LR;

graph 是告诉程序我要开始绘图了；  
LR 是绘制从左到右的图形，这里的 L 和 R 分别是 Left 和 Right 的缩写。

LR 还可以更改为其他 3 个值：

* RL：从右到左
* TB：可不是指某宝哦，而是从上到下，T 和 B 分别是 Top 和 Bottom 的缩写
* BT：可不是指种子哦，而是从下到上

后面的就比较好理解了，从一个节点到下一个节点，节点内容中间加 2 个短横线 - 和 1 个大于号就好了，即 `-->`。

如果我们想在节点间的连接线上添加内容，如下面导图圈出的文本，则是在两个节点中间的 `-->`插入 `--你想在导图连接线上添加的内容`。

掌握使用 Mermaid 的这几个要点，**在 Notion 中绘制一个简单的思维导图**就绰绰有余了。

[![](https://image.cubox.pro/imtwg9/cover/2023020317140285362/article.jpg)](https://article-picbed-1302715071.cos.ap-guangzhou.myqcloud.com/2022/11/27/16695303427924.jpg)

用 Mermaid 在 Notion 中绘制其他的图形
---------------------------

前面说到 Mermaid 可以绘制多种图形，除了思维导图，如果你想在 Notion 中绘制其他的图形/图表，也可以考虑使用 Mermaid 来绘制：

### 绘制流程图

流程图中不同的形状有着相对应的含义，例如：矩形/圆角矩形表示流程图的开始，菱形表示判断，柱形表示数据......

[![](https://image.cubox.pro/imtwg9/cover/2023020317140142814/article.jpg)](https://article-picbed-1302715071.cos.ap-guangzhou.myqcloud.com/2022/11/27/16695320089639.jpg)

绘制流程图时，在第一行输入流程图对应的英文 flowchart，且在后面写上流程图的方向，上图的方向是 TB，即从上往下。

如果是像前面创建思维导图一样，**直接输入文本** ，在流程图中渲染得到的就是**矩形**。

其他形状对应的写法如下：

* 菱形：id{这是菱形}
* 圆角矩形：id(这是圆角矩形)
* 圆形：id((这是圆形))
* 柱形：id\[(这是柱形)\]
* 类似跑道外形的圆角矩形：id(\[这是类似跑道外形的圆角矩形\])
* 六边形：id

### 绘制饼状图

用 Mermaid 绘制饼状图，则在第一行输入表示饼状图的 pie，后面跟上 title 和饼状图的名称。

下面的则是组成饼状图的每一项，遵循程序中「**键值对** 」的写法，左侧是**项目名称** ，中间隔一个英文冒号，右侧是对应的**比例** 或者**数值**（绝对值）。

如果为数值，Mermaid 会自动计算数值在数值在总和中所占的比例，而不需要我们手动计算对应的比例。

[![](https://image.cubox.pro/imtwg9/cover/2023020317140130664/article.jpg)](https://article-picbed-1302715071.cos.ap-guangzhou.myqcloud.com/2022/11/27/16695325577276.jpg)

关于 Mermaid 的用法，就简单介绍到这里咯，介绍它并不是说大家都要用它来绘制图形，而是提供一种选择：

如果你想在 Notion 中绘制一些简单的图形/图表，例如思维导图或者饼状图，那么可以考虑用它，但对于一些复杂的图形，建议还是**用更专业的工具**，而不是被自己所掌握的语言、工具甚至是思维所束缚～

让工具回归工具，让你成为你。

订阅我在竹白上创建的 Newsletter
---------------------

如果对你有帮助的话，别忘了点击下方的链接，订阅我的 Newsletter，之后发布了新的内容，就能第一时间收到通知啦～

[👉在竹白上订阅效率工具指南](https://penghh.zhubai.love/)

欢迎关注
----

以上，就是本次想和你分享的内容，希望能够对你有一点帮助。

[![公众号：效率工具指南](https://image.cubox.pro/article/2021122923391444480/41029.jpg)](https://article-picbed-1302715071.cos.ap-guangzhou.myqcloud.com/2021/05/28/gong-zhong-hao-wei-bu-er-wei-ma-dailogo.png)

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7066738575781398366)
