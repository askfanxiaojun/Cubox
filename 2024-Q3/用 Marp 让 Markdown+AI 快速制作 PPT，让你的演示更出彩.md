用 Marp 让 Markdown+AI 快速制作 PPT，让你的演示更出彩
======================================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/frKOjf4hb6yec8LzSmvQ7A)思辨view kate人不错


AI 生成 PPT 的介绍
-------------

之前我分享过[使用 AI 优化 PPT 的方法](http://mp.weixin.qq.com/s?__biz=MzI5MjQ3ODY3Mw==&mid=2247484254&idx=1&sn=72b2c9ed6c6c21db52af70b0c9bd6d02&chksm=ec0188e0db7601f6dad81c966582749dd0307ec350029204aec2e21fc8fd3ee6efa823ccd91d&scene=21#wechat_redirect)。今天要介绍一种通过 Markdown 快速制作 PPT 的工具。

我体验过的最好的 AI 生成 PPT 工具是百度文库的 AI 智能生成功能。它可以根据简短指令或完整文章，自动生成演示文稿。而且提供了多种适合不同场合的模板。

AI 生成 PPT 的局限性
--------------

但如果内容被 AI 平台判定为敏感，这些工具可能会拒绝制作 PPT。比如我曾用一段中国城市人才吸引力排名的摘要测试，但请求被拒绝了。

这引发一个问题：如何快速优雅地制作演示文稿?
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FVzoLjU1b4dibOEK95rRRsAszBgdt2OxBRGp3HMmwZ0iaIMC3jqOicOl2VHPCLsDdkRtMnYmFt9bUg8qXF6bicJrVnQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

Markdown 到 PPT 的转换流程
--------------------

如今，Markdown 格式在写作中的应用越来越广泛，大多数生成式 AI 产品产出的文本也默认采用这种格式。利用这一点，我们可以创造出一些有趣的内容。

对于较长的文章，我通常用以下方法将其转换为 PPT：

1.
   提示词：{上下文}---改编成 PPT

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FVzoLjU1b4dibOEK95rRRsAszBgdt2OxBRGIhDLmkibfDKhR21uZBy5icbJiaL1AZsehAl3V9Jv6JOGPa2iccmXrOKVw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

2.
   提示词：输出 Marp 的 md

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FVzoLjU1b4dibOEK95rRRsAszBgdt2OxBRzNXhLEh8bicAIW7P6oztaVExjcCWHnicWmvGjas9NsskM1Y1D7B11PLA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

3.
   提示词：将数据转换为表格格式
4.
   提示词：选择"gaia"主题，并确保表格居中显示，需要添加相应的样式代码。
5.
   将由 GPT 生成的 Markdown 格式文本复制到https://web.marp.app/ 中，以预览最终效果。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FVzoLjU1b4dibOEK95rRRsAszBgdt2OxBR4qLBuGQMPLMXcfgbrA7yAzpW75BVK2pz1z2ygQHKJX8AVycNnySQ6g%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

如果对渲染的样式不满意，你可以随时请求 GPT 进行调整，以满足你的需求。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FVzoLjU1b4dibOEK95rRRsAszBgdt2OxBRziaQcc6yOtE2gMQic3DVDGCSRibXgLNrvvByQIVCNEtHVjpy1nyluUxLw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

你也能创建类似的效果。所用的代码同样是以 Markdown 格式渲染，可以直接复制使用。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FVzoLjU1b4dibOEK95rRRsAszBgdt2OxBRwtnBdpbicfe59ea4FfYUpnEuWicBj6Dr1yZqldWzwFTnVEDMklyd5APw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

对于 xmind 格式文件，我使用 Python 程序来将其转换为 Markdown 文件。

https://github.com/TerraceCN/xmind2md

命令如下：

    pythonxmind2md.py/path/to/your/xmind/file.xmind-o/path/to/output/markdown/file.md

你也可以尝试用 GPT 将内容转为 Markdown 格式，但根据我的经验，这种转换有时可能会失败，可能是遵循指令存在问题导致的。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FVzoLjU1b4dibOEK95rRRsAszBgdt2OxBRznA8zlU1MM7UeD7Z2hoRdkWKJATB52w2qheic5CIohAMVTIy5EPicyicQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

一旦内容被转换为基本的 Markdown 格式，你可以进一步请求 GPT 将其调整为适用于 Marp 的 Markdown 格式。

那 Marp 是什么呢？这里详细介绍下。

Marp 工具详解
---------

查阅多方资料后，我发现了以下三种将 Markdown 转换为演示文稿的工具，其中前两种我已经深入使用过。

|    特性    |       Marp       |       Slidev       |      Quatro      |
|----------|------------------|--------------------|------------------|
| **定位**   | Markdown 幻灯片生成工具 | 基于 Vue.js 的互动幻灯片工具 | 基于 React 的幻灯片工具  |
| **核心技术** | Markdown + CSS   | Markdown + Vue.js  | Markdown + React |
| **优点**   | 简单易用，生态系统丰富      | 高度互动，实时预览和热重载      | 强大的自定义和互动能力      |
| **缺点**   | 功能相对简单           | 学习曲线较高             | 学习曲线较高           |
| **适用场景** | 简单的 Markdown 幻灯片 | 需要复杂效果和互动的演示       | 需要复杂演示的场景        |


#### Marp

https://marp.app/

1.
   **功能**：它提供了一个命令行工具、编辑器扩展（如 VS Code 扩展）和一个在线编辑器，以帮助用户从 Markdown 文件创建幻灯片。

2.
   组件

*
  **Marp CLI**：一个命令行工具，用于将 Markdown 文件转换为 HTML、PDF 或 PPTX 格式的幻灯片。
*
  **Marp for VS Code**：一个 Visual Studio Code 的扩展，允许用户在编辑器中预览和导出 Markdown 幻灯片。
*
  **Marp Web**：一个在线编辑器，允许用户直接在浏览器中创建和展示 Markdown 幻灯片。

https://web.marp.app/

对于初学者，我建议先使用 Marp Web，因为无需安装任何软件，直接在线体验即可。从中可以看到，"---"是 Marp 的主要格式，用于分隔 PPT 的各个页面。

此外，Marp Web 还支持导出功能。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FVzoLjU1b4dibOEK95rRRsAszBgdt2OxBRMEtfwzcIiaz2yRucTdctfjsheBFVnKVsWJMAAznBXNFibvIpA0RBVELQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

这篇文章写得非常详细，非常适合作为入门阅读材料，强烈推荐。

https://mp.weixin.qq.com/s/xKjNSxaJp1YxZvqEsz8yGQ

*** ** * ** ***

看完上文后，我再分享一些在使用 Marp 过程中值得关注的内容。

无需添加 "---"，只需设置 Heading Divider
-------------------------------

`headingDivider` 是 Marp 中的全局指令，用于根据标题级别自动划分幻灯片。

例如，`<!-- headingDivider: 4 -->` 表示从四级标题（`####`）开始为新幻灯片。

### 示例

1.
   **常规语法**

    #1stpage

    Thecontentof1stpage

    ---

    ##2ndpage

    ###Thecontentof2ndpage

    Hello,world!

    ---

    #3rdpage

    😃

2.
   **使用 `headingDivider`**

    <!--headingDivider:2-->

    #1stpage

    Thecontentof1stpage

    ##2ndpage

    ###Thecontentof2ndpage

    Hello,world!

    #3rdpage

    😃

这两种方法生成相同的输出。`headingDivider` 使 Markdown 文件更美观，没有多余的分隔线。

#### 应用场景

*
  将普通的 Markdown 文档创建为幻灯片。
*
  保持 Markdown 文件在普通编辑器中的美观。

碎片化列表
-----

碎片化列表就像在演示文稿中一个接一个地展示列表项，而不是一次性全部显示。就好比你在讲故事时，逐步揭示情节，而不是一次性把所有内容都说出来。

#### 在 Marpit 中的实现：

1.
   **无序列表（Bullet list）**：

   使用 `*` 作为标记符，列表项逐一出现。

2.
   **有序列表（Ordered list）**：

   使用 `)` 作为标记符，列表项逐一出现。

**示例**

使用 `)` 作为标记符，有序列表项会逐一出现：

    1)第一项
    2)第二项
    3)第三项

在演示中，这些列表项会一个接一个地显示，而不是同时出现。

#### 没有碎片化的列表：

1.
   **无序列表**：

   使用 `-` 或 `+` 作为标记符。

2.
   **有序列表**：

   使用 `.` 作为标记符。

Marp CLI 的使用很简单
---------------

详细信息请参考：https://github.com/marp-team/marp-cli

### macOS 安装：

    brewinstallmarp-cli

### 使用 Marp CLI 将 Markdown 文件转换为幻灯片：

    marp/path/to/your/slide/file.md-p

1.
   \*\*`marp`\*\*：调用 Marp 工具。
2.
   \*\*`/path/to/your/slide/file.md`\*\*：替换为你实际的 Markdown 文件路径。
3.
   \*\*`-p`\*\*：生成幻灯片的 HTML 文件并启动本地服务器进行预览。

Marp for VS Code 插件
-------------------

Marp for VS Code 插件为 Visual Studio Code 带来了专门用于创建和预览 Marp 幻灯片的功能。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FVzoLjU1b4dibOEK95rRRsAszBgdt2OxBRqHicfWJ4HWdHh6sRgvL0dibp88P59TKZPRakXq3twUKkRMT1KQwNY0MA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

### 特别功能

1.
   **实时预览**：

   实时显示 Markdown 文件转换后的幻灯片效果，编辑保存时自动更新。使用快捷键（`Ctrl+Shift+V` 或 `Cmd+Shift+V`）或点击 Marp 图标打开预览窗口。

2.
   **Markdown 语法高亮**：

   支持 Marp 专有的 Markdown 语法高亮，便于编辑。

3.
   **讲师备注**：

   支持添加讲师备注，方便演示时提供额外说明。

4.
   **导出功能**：

   通过命令面板（`Ctrl+Shift+P` 或 `Cmd+Shift+P`）将 Markdown 文件导出为 PDF、PPTX、PNG 或 JPEG 格式。
   ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FVzoLjU1b4dibOEK95rRRsAszBgdt2OxBRPBhdcZ920p3MK6icvNaFXykHaJ4wG9IvRZDUSZBfliaQpbTJJLc1DREA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)
5.
   **主题支持**：

   支持自定义和内置主题，可在 Markdown 文件中使用 `theme` 指令或在设置中选择。

图片语法
----

详细信息请参考：https://marpit.marp.app/image-syntax

Marp 的图片命令很直观，例如：

*
  `bg` 表示背景。
*
  `right:40%` 表示将图片定位在幻灯片右侧，宽度占幻灯片的 40%。

示例：

    ![bgright:40%](https://example.com/image.jpg)

还有更多图片样式可以探索，详情请查看 Marp 官方文档。

开头案例中的 Marp 设置
--------------

    ---
    marp:true
    theme:gaia
    paginate:true
    header:"市场行情"
    _class:lead
    style:|
    table{
    width:100%;
    border-collapse:collapse;
    margin:auto;
    }
    th,td{
    border:1pxsolid#dddddd;
    text-align:center;
    padding:8px;
    }
    ---

    #<!--fit-->市场行情

#### Markdown 语法说明


|          语法           |          作用说明           |
|-----------------------|-------------------------|
| `marp: true`          | 启用 Marp 渲染 Markdown 幻灯片 |
| `theme: gaia`         | 使用 gaia 主题样式            |
| `paginate: true`      | 为幻灯片添加页码                |
| `header: "市场行情"`      | 为每页添加页眉文字               |
| `_class: lead`        | 第一页应用 lead 样式           |
| `style: | ...`        | 定义表格的 CSS 样式            |
| `---`                 | Markdown 分隔符，新起一页幻灯片    |
| `# <!-- fit --> 市场行情` | 一级标题，自动缩放字号适应页宽         |


#### CSS 代码说明


|           CSS 代码            |                作用说明                 |
|-----------------------------|-------------------------------------|
| `table`                     | 表示以下样式应用于表格 table 标签                |
| `width: 100%`               | 表格宽度设置为 100%，即撑满其所在的容器              |
| `border-collapse: collapse` | 合并表格的边框，去掉单元格之间的间隙，使边框相邻            |
| `margin: auto`              | 表格在其所在容器中水平居中显示                     |
| `th, td`                    | 群组选择器，应用于表格的表头 (th) 和单元格 (td)       |
| `border: 1px solid #dddddd` | 为单元格添加 1 像素宽的实线边框，颜色为 #dddddd (浅灰色) |
| `text-align: center`        | 单元格内的文本居中对齐显示                       |
| `padding: 8px`              | 单元格内边距均设置为 8 像素，使文字与边框有一定间距         |


其他
---

### Marp 也支持 Obsidian：

https://github.com/samuele-cozzi/obsidian-marp-slides

### 安装主题

详细指南请参阅：https://yoanbernabeu.github.io/MARP-Template-Library/docs/intro/

Markdown 文件写好后，只需复制开头的主题设置，即可快速生成可演示的文档。

结语
---

不论是内部分享还是公开演示，这些工具都能帮助你高效完成。

如果你对效果不满意，还可以利用 GPT进行调整，确保达到理想的展示效果。

希望这篇文章对你有所帮助。如果觉得有用，欢迎点赞、分享。

*** ** * ** ***

精选历史文章，请看这里：

[借助ChatGPT的12种Python库，轻松搞定高质量图表制作，中文显示无压力](http://mp.weixin.qq.com/s?__biz=MzI5MjQ3ODY3Mw==&mid=2247487427&idx=1&sn=4327ecab120af9db5879b4d7edaa2231&chksm=ec01847ddb760d6bd56c32f925bb9f7bcce38218e123bf234608b17197c6ea2e17234c0cd630&scene=21#wechat_redirect)

[](http://mp.weixin.qq.com/s?__biz=MzI5MjQ3ODY3Mw==&mid=2247487320&idx=1&sn=265574e0d9057f1872f1399b5c8fe229&chksm=ec0184e6db760df0c233ac6a93d507d24be4c48d4e8850f3cf42e317bc47d1074cc45ee2a8d2&scene=21#wechat_redirect)[你还在手动排版公众号文章？看看 ChatGPT 怎么轻松搞定 \| PPT、MD、CSV 批量转公众号排版](http://mp.weixin.qq.com/s?__biz=MzI5MjQ3ODY3Mw==&mid=2247487364&idx=1&sn=8109d2955dd940ac803527dc4faf02ab&chksm=ec01843adb760d2c64d5e1ba79a815f14a66f8ecf4c99cc13c010457eadf07cca73a300de593&scene=21#wechat_redirect)

[不只是快，新版 ChatGPT 数据分析体验全记录，分享超实用 AI 提示词，助你轻松驾驭复杂数据分析](http://mp.weixin.qq.com/s?__biz=MzI5MjQ3ODY3Mw==&mid=2247487320&idx=1&sn=265574e0d9057f1872f1399b5c8fe229&chksm=ec0184e6db760df0c233ac6a93d507d24be4c48d4e8850f3cf42e317bc47d1074cc45ee2a8d2&scene=21#wechat_redirect)  

[](http://mp.weixin.qq.com/s?__biz=MzI5MjQ3ODY3Mw==&mid=2247487296&idx=1&sn=51bbed62f709d0d68aa47d4a52445504&chksm=ec0184fedb760de885e7183f610f4b2e7cf2fc3f5fa8fdf77bea21a6e5b987bd555dbe5881fc&scene=21#wechat_redirect)[推荐一个自动生成复杂提示词的模版：思考链（CoT）如何通过分步推理提升AI任务准确性](http://mp.weixin.qq.com/s?__biz=MzI5MjQ3ODY3Mw==&mid=2247487267&idx=1&sn=5b7fe56894049262c9dc578962edd208&chksm=ec01849ddb760d8bf76da76e34d00190804400cac4feb26a3ca7ad81241485c4c3bc79c3f800&scene=21#wechat_redirect)

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7217420605379841479)
