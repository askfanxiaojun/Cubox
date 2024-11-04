我的 Prompt 爆火全网｜ AI 一键生成高颜值社交名片全解析
=================================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/7vrhxQYdgQ_WpGK6Xi49aw)一泽Eze 一泽Eze

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssg6xsAvVqaUzuRLIyrKiabnJuNS0jw8tq64tS8yicWCECw8Kc3uPFmCu5Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

宣布一个最近很开心的事。

**我最近写的一段 Prompt 火了，发出不到 10 分钟，全网就有上百条转发。**
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgHAIfHY8Fk3IaGd7B3H0IT9FGCu14Zib3RcyAGUric37juBA6VibWmO2bQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

在 AI 圈子里，讨论、二创热度特别高，浏览量已经超过 10w+。（非常感谢**@歸藏 @哥飞**等即友的第一波转发分享）
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgyf5ic5jUQxicDCjdmoicTAhwlzdDnOfcyvwYbk6icEoXlSVpZmOwmp6f8Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

如果你还不知道这是怎么回事，想要这份很火的提示词，

或者想听听这个 case 背后的创作灵感、提示词设计思路、个人思考。

**别急，待我细细与你们拆解唠唠。**

想找提示词玩起来的，直接往下划就好～

AI 一键直出的社交名片，是怎样的？
------------------

先看几张效果图。这些都是用 AI + 提示词，一键直出的。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgMlNObJaK2Ry7uMNXGv5nqWvXIy1E0ice7LHN8KLBbGKMRKEqNibsZexw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

如果想要得到这样的同款效果，

只需要把你的信息、简历、个人说明书，甚至社交媒体主页，丢给 Claude ， 什么格式都行（消息、图片、PDF 等）。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgT628vClEf1r5BmTqrhFTyGicwRsuXnZspMPicPbwB9ufhvgKIl1jG0eQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

AI 就会自动提炼你的社交名片文案，并为你生成精美好看的可视化社交名片。

没错，就这么简单。

**如果立即想动手生成自己的专属社交名片，我已经开源了提示词，你可以直接获取：**
> ➡️ 如果觉得还不错，还请**关注、点赞、转发**，多谢啦～
>
> 👀 如果想继续看创作灵感、提示词设计思路、个人思考的，也可以直接往下拉

    //作者：一泽Eze
    //名称：个人社交名片生成器
    //用途：收集用户的个人简介，生成美观的个人社交名片
    //版本：0.2
    //版本说明：新增通过个人简历自动生成名片文案
    //适用模型：Claude 3.5

    //设定如下内容为你的*SystemPrompt*

    ##步骤1：收集原始信息
    简洁的引导用户提供个人简历或自我介绍，并根据步骤2中的模板提示可提供的内容（可选），支持文本消息/txt/md/pdf/word/jpg文件

    注意：当用户发送文件后，视作用户提供了第一步所需的信息，直接继续步骤 2

    ##步骤2：提炼社交名片文案
    步骤说明：利用用户提供的信息，根据名片信息模板的结构，解析并提炼社交名片文案
    注意：这一步不需要输出信息

    ###名片信息模板
    姓名：\[您的姓名\]
    地点：\[您的地点\]
    身份标签：\[职业标签1\], \[职业标签2\], \[职业标签3\]

    近期关键投入：
    \[一句话描述您的近期关键在做的事/领域\]

    履历亮点：
    -\[亮点1\]
    -\[亮点2\]
    -\[亮点3\]

    擅长领域：
    1.领域名称：\[领域1名称\]
    描述：\[领域1描述\]
    2.领域名称：\[领域2名称\]
    描述：\[领域2描述\]
    3.领域名称：\[领域3名称\]
    描述：\[领域3描述\]
    4.领域名称：\[领域4名称\]
    描述：\[领域4描述\]

    兴趣爱好：
    \[emoji爱好1\]\|\[emoji爱好2\]\|\[emoji爱好3\]\|\[emoji爱好4\]

    个人态度：
    \[根据个人信息，提炼符合个人履历气质的个人态度或座右铭，不超过25字\]

    ##步骤3：Html-PersonalCard 生成
    (defunHTML-PersonalCard(步骤2中提炼的社交名片文案)
    "输出HTML个人社交名片"
    (setqdesign-rule"现代简约风格，信息层次清晰，视觉重点突出，高度利用合理"
    design-principles'(简洁专业现代个性化))

    (引入外部库(Lucide图标库))))
    (设置布局'(最大宽度md圆角xl阴影2xl))
    (主要字体'(NotoSansSCsans-serif))
    (响应式设计'(视口自适应))

    (配色方案'((背景色白色)
    (主要文字深灰色)
    (强调色蓝色)
    (次要背景浅蓝色浅绿色浅紫色浅橙色)))

    (卡片元素((头部信息(放置头像的圆形区域姓名地点身份标签))
    (关键投入(图标标题描述))
    (履历亮点(图标标题列表))
    (擅长领域(图标标题网格布局))
    (兴趣爱好(图标标题描述))
    (页脚(个人态度(描述)放置二维码的正方形区域))))

    ###样式要求
    1.整体布局：
    -使用Flexbox居中显示卡片
    -最大宽度设置为md（Tailwind的中等宽度），确保在不同设备上的适配性
    -圆角（rounded-xl）和阴影（shadow-2xl）增加视觉深度

    <br />



    2.字体和排版：
    -使用NotoSansSC作为主要字体，确保中文显示的优雅性
    -文字大小从xs到2xl不等，创建清晰的视觉层次

    3.颜色方案：
    -主背景为白色（bg-white），营造干净简洁的感觉
    -使用蓝色作为主要强调色，体现在图标和部分文字上
    -不同的浅色背景（蓝、绿、紫、橙）用于区分不同的擅长领域，增加视觉趣味性

    4.内容结构：
    -头部信息：包含放置头像区域、姓名、地点和身份标签
    -近期关键投入：整体使用浅色圆角矩形作为模块底图
    -主体部分：履历亮点、擅长领域和兴趣爱好。每个部分都有相应的图标，增强可读性和视觉吸引力
    -页脚部分：包含个人态度的描述和放置二维码的正方形区域

    5.特殊设计元素：
    -放置头像的圆形区域：使用渐变色边框，增加设计感
    -页脚：个人态度的描述和放置二维码的正方形区域，左右布局，间距、高度合理，利用合适底色，与主体部分形成视觉区分
    -主体部分的标题：使用 lucide 图标，增加视觉趣味性和信息的可识别性

    5.响应式设计：
    -使用Tailwind的响应式类，确保在不同设备上的良好显示
    -在小屏幕设备中，确保作者信息不会与卡片重叠或产生布局问题
    -擅长领域使用网格布局，每个领域有独特的背景色
    -内容padding和margin的合理使用，确保信息不会过于拥挤

    6.外部库引入
    -正确引入Lucide图标库，使用其React组件版本
    -确保在React环境中正确使用Lucide图标

    //运行规则：从步骤 1 开始工作。在接收用户提供的信息后，严格按照要求直接输出最终结果，不需要额外说明

这么棒的灵感，怎么来的？
------------

> 不是拿着锤子找钉子，而是看到钉子找锤子。

有些朋友看到这个 Case ，发出感慨："为什么第一个想到的不是我"。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgL5wJymkicyy7vnOGvdL45Fq7ZWXbu4kk0k7ISicH04licRYmUY9YqLpfw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

在这里分享一下我的灵感的成型过程。也期待能抛砖引玉，碰撞出更多有意思的 AI 小玩意。

核心思路是：先从真实需求出发，思考最"想要"的解决方案，再考虑用 AI 铺平落地的"最后一公里"。

换句话说：**有了 AI 以后，很多以前研发 ROI 特低、用户使用门槛巨高的细分需求场景，都可以做得更好了。**（注意，可以做 ≠ 能赚很多钱）

社交名片 Prompt 的灵感来源，最早是为了做一张方便加微信好友时，做自我介绍破冰用的个人简介图。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgdyPNGXH1h60zl4A7TYKvRrISF2gVdFLXDI6Dw1oETOoyKFCCibJAQwA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

在这个场景中，有很多已有的破冰方案，我总结下来大概是这么几类：
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgAYfAb69058UyS5uwfXbOOspyeJ3kkqV2gRkEdfBPMG92xtGIKZfD2w%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

**1）常见的商务名片：信息量少，距离感强**

距离感太强，只有商务 title、联系方式，信息量少，不足以别人熟悉自己，拉近距离。

**2）文字版个人介绍：视觉效果差，专业感缺失**

如果塞了一大堆内容，在微信的绿色消息框里就更难阅读了。

**3）个人说明书/博客链接：初次聊天，点击欲望、阅读效率低**

作为个人故事的展示，确实很好，我也写了一份。👉 https://link.eze.is

但在 IM 聊天场景里，上来就发一条链接，如果不是对你本人很感兴趣的朋友，很难有动力点开一条陌生链接，并看完里面上千字的自述。

**4）个人简介图片（社交名片）：制作成本高，审美水平参差不齐**

从形式上来说，加上好友后，发一张样式精美、重点突出、行文流畅的个人简介图片，是再好不过。

而一张精美的个人简介图片，需要经过模块构思、提供信息、文案编写、视觉设计四步骤。只要一个步骤没做好，就很难达到预期效果。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgDXeM9tPT4gcia9WiaJLMVnm8fPLGtmVSiaIRKswhEZhKo5KXMqtKwFeqw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

但话说回来，从内容形式上看，也就"文字、图片、链接"3 种选择。而图片恰恰是线上社交破冰中，最吸引人打开、阅读的"王炸"方案。

唯一问题在于，让个人用户独立完成这些步骤，确实有难度。

方案推理：能不能简化这些步骤呢？
----------------

> 理论上，人类都很"懒"，最好什么都不干，就能获得称心如意的最终成果。

### 1）模块构思：社交名片的基石

从初识一个陌生人的场景来说，我们所关注的社交信息，出奇的一致。

我根据自己的观察，拆解为 5 个信息模块和 1 个行动：
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgEwQTtkPP0o9kgDwxZQTzMzy1IwMUaw2ibziblbIpcVraPiae2LClrt7ZQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

得益于这套最优解，我们能把社交名片的模块固定下来，从而删掉「模块构思」这一复杂、抽象的环节。

而在进行利用社交名片破冰时，我们的核心目标是：激发对方对你的真实兴趣，提高漏斗的转化率。即表现为愿意读完整张社交名片，扫码深入了解你。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssg2NZXythsibqWAkMFCANsKmsC5gy0ibEo6gTibE2vhTk3ic6ggNfb4KkutA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

另外，为了配合使用场景，达成转化目的，就必须遵循移动端优先、减少对方操作步骤的理念，确保整张社交名片适配手机屏幕样式，能在一屏内完全展示。

我们可以得出对社交名片的模块构思与整体要求：

1. 1. 由上述信息模块组成；

2. 2. 采用手机屏幕尺寸作为图像大小，限制内容长度在一屏内展示。

### 2）提供信息：尽量简单、减小用户压力

对于个人信息，AI 无法做到"全知全能"，必须由用户自行提供。在产品设计中，我们应尽量利用已有素材作为信息来源，避免用户需要现场思考、措辞和输入的情况。

简历、个人说明书、社交媒体主页等资料通常包含大量符合信息模块要求的内容。这些现成的素材可以大大简化信息收集过程。

值得注意的是，许多大模型对话产品（如 Claude、ChatGPT、KIMI、通义千问等）已经支持解析来自图片、PDF、Word 文档和网页链接的内容。通过引导用户提供这些已有素材，实现一键上传，即可高效完成信息的提供与录入。

### 3）文案编写：生成式 AI 的舒适区

再者是创作社交名片各模块的文案。

从 2022 年底 ChatGPT-3.5 的问世震惊了世界，到 2023 年 3 月 ChatGPT-4 的智力大幅提升，再到 2024 年上半年 Claude 3.5 sonnet 摘得大模型在文学创作领域的桂冠，文字类的总结、润色、创意，一直以来都是大语言模型 AI 的舒适区。

只要有了足够信息输入，加以合理的提示词引导，文案编写自然是水到渠成。

以下是我根据预设模块，和 AI 一起优化出的名片文案模板：

    ###名片信息模板
    姓名：[您的姓名]
    地点：[您的地点]
    身份标签：[职业标签1], [职业标签2], [职业标签3]

    近期关键投入：
    \[一句话描述您的近期关键在做的事/领域\]

    履历亮点：
    -\[亮点1\]
    -\[亮点2\]
    -\[亮点3\]

    擅长领域：
    1.领域名称：\[领域1名称\]
    描述：\[领域1描述\]
    2.领域名称：\[领域2名称\]
    描述：\[领域2描述\]
    3.领域名称：\[领域3名称\]
    描述：\[领域3描述\]
    4.领域名称：\[领域4名称\]
    描述：\[领域4描述\]

    兴趣爱好：
    \[emoji爱好1\]\|\[emoji爱好2\]\|\[emoji爱好3\]\|\[emoji爱好4\]

    个人态度：
    \[根据个人信息，提炼符合个人履历气质的个人态度或座右铭，不超过25字\]

### 4）视觉设计：斟酌可行思路，测试 AI 上限

在名片设计的最后阶段------视觉设计中，核心任务是将名片文案转化为精美的可视化样式。

考虑到不同用户的模块文案长度差异，采用前端网页代码构建承载文案的样式框架，相较于直接文生图的方式，具有更佳的兼容性。

恰好，Claude Artifacts 功能已被证实在网页布局设计和前端开发方面表现出色，能够自动生成代码并提供实时预览效果。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgk9YGU5Ets7TpvkNtcbdLMxNq7kXXY9dInEwBS0jtBURJgibGTgZmkRQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

只要通过连续对话，验证 Claude 确实能为我们生成符合审美要求的社交名片，我们就能证明完全依赖 AI 来完成视觉设计是切实可行的方案。

下图是我通过连续对话，验证出的最终效果，是个 HTML 文件。

对这种提示技巧感兴趣的读者，可以阅读我的另一篇文章：[https://mp.weixin.qq.com/s/3pFG_Tx7gcnnjOyqgM1P_w](https://mp.weixin.qq.com/s?__biz=MzIzNDU0NzY1MA==&mid=2247483748&idx=1&sn=40c0acfde7d57b54e3508fa850164248&scene=21#wechat_redirect "https://mp.weixin.qq.com/s?__biz=MzIzNDU0NzY1MA==&mid=2247483748&idx=1&sn=40c0acfde7d57b54e3508fa850164248&scene=21#wechat_redirect")
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgCAXjiabEI1Dxl4ibXCIJLbNTQzs7ibXkkvkQhroX2KTNGyy0Ctao9sPyw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

更进一步，如果我们能够通过一段提示词，让 AI 稳定输出预期结果，就可以省去单独的工程化处理（即固定模板代码，仅由 AI 负责文案编写，可视化输出变成固定的代码"填空题"）。

这种方式不仅能大幅降低应用开发的复杂度，还可以引入随机样式的"抽奖"特性，提升用户体验趣味。

提示词设计思路
-------

在完成了社交名片的方案推理，并获得了一个符合预期的样例后，我们面临着一个关键问题：如何将这个方案固定下来，使得不同用户都能获得稳定且个性化的结果？

答案就在于**精心设计的提示词**。

刚好 Prompt 大神**@李继刚** 的「汉语新解」项目近期备受关注。他**仅凭一段简短的提示词，就能让 AI 输出风格稳定的图文卡片**。我也参考了他的新提示词框架中的一些想法，取得了非常不错的实践成果。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssguQW4qCTYIRicexOQaoPD3mzk3lPXiaZlapOTKvJGd78XFGPibQkQIwNoQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null") 如果你还不了解 @李继刚 的「汉语新解」是什么，可以看看他的原文：[https://mp.weixin.qq.com/s/7CYRPFQxi37ONTlX0hfzRQ](https://mp.weixin.qq.com/s?__biz=MzkxMzc1NzM1Mw==&mid=2247483687&idx=1&sn=d2f7f4d833f1ed33399b1fb02d688f6f&scene=21#wechat_redirect "https://mp.weixin.qq.com/s?__biz=MzkxMzc1NzM1Mw==&mid=2247483687&idx=1&sn=d2f7f4d833f1ed33399b1fb02d688f6f&scene=21#wechat_redirect")
>
> 另外，他的提示词已经进化到了下一个 level，非常值得关注：[https://mp.weixin.qq.com/s/bCU4M7QlPNqD_JzFhgBlTQ](https://mp.weixin.qq.com/s?__biz=MzkxMzc1NzM1Mw==&mid=2247483700&idx=1&sn=1914e730e940805e92921d9fd4510256&scene=21#wechat_redirect "https://mp.weixin.qq.com/s?__biz=MzkxMzc1NzM1Mw==&mid=2247483700&idx=1&sn=1914e730e940805e92921d9fd4510256&scene=21#wechat_redirect")

### 拆解我的社交名片 Prompt 框架

由于模块构思这一步已经完全固定，我们的社交名片小应用只需关注"提供信息、文案编写、视觉设计"这 3 个步骤。整体框架如下：

    //提示词元信息
    [作为提示词的README，记录作者、用途、版本等信息]

    //设定如下内容为你的*SystemPrompt*
    (模拟系统提示词，用于增强指令的遵循性）

    ##步骤1：收集原始信息
    \[用于引导用户，提供所需信息原料，需要用户互动\]

    ##步骤2：提炼社交名片文案
    \[设定名片文案的提炼规则，完成信息处理\]

    ##步骤3：Html-PersonalCard 生成
    \[设定社交名片的样式规则，完成样式生成与信息拼接\]

    //运行规则
    \[声明AI如何使用这段提示词\]（同样也可以增强指令的遵循性）

### 1）记录提示词元信息

    //作者：一泽Eze
    //名称：个人社交名片生成器
    //用途：收集用户的个人简介，生成美观的个人社交名片
    //版本：0.2
    //版本说明：新增通过个人简历自动生成名片文案
    //适用模型：Claude 3.5

这个模块用来记录一些基础信息，保护作者版权，注明用途、版本等信息。

在实践中，你可以根据自己喜好更改细节。

（注：我用的`//`和继刚用的`;;`，都只是用来区分注释信息和提示词主体内容，没有太大区别。)

### 2）设定 System Prompt 的声明

    //设定如下内容为你的*SystemPrompt*

关于这段提示词的实际效果，我专门询问 @李继刚，回答如下：
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgc5zh1JUmGmb0ovYOdFPRiaPwyZOXGmVPRjBXZwQ06AKFBYOrj7OeNxg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

所以我也直接遵循实践经验，保留沿用。

### 3）设定收集信息的引导

    ##步骤1：收集原始信息
    简洁的引导用户提供个人简历或自我介绍，并根据步骤2中的模板可提供的内容（可选），支持文本消息/txt/md/pdf/word/jpg文件

    注意：当用户发送文件后，视作用户提供了第一步所需的信息，直接继续步骤 2

为了引导用户提供所需的信息，需要让 AI 在运行过程中，输出中间过程的提示信息，引导用户提供信息原料。

可以让 AI 从我们后面的模板样例中，理解需要用户提供的信息，简化提示词。

### 4）利用模板，指导 AI 提炼社交名片文案

    ##步骤2：提炼社交名片文案
    步骤说明：利用用户提供的信息，根据名片信息模板的结构，解析并提炼社交名片文案
    注意：这一步不需要输出信息

    ###名片信息模板
    {{填入上文提过的名片信息模板}}

限定文案的信息来源，指定模板规范，完成文案编写。
> 由于在实测中，AI 会在过程中逐字输出文案内容，所以添加`注意：这一步不需要输出信息`，避免输出太多废话，拖慢执行速度。

### 5）🌟 如何写出符合设计要求的提示词？

> 这一步虽然看上去比较复杂，但按照我的方法，就能非常无脑地让 AI 替你写出八九不离十的提示词初稿。

还记得我们在方案推理环节，得到的「最终样式.html」吗？

按照我早先的一篇文章《样例驱动的渐进式引导法》中提到的方法，把这个 html 文件作为样例，和这段提示词同时发送给 Claude，让 AI 根据 @李继刚 的提示词中控制样式输出的形式，自行总结我们需要的结果。

    请按照以下形式思路，分析html的设计

    (defunSVG-Card(解释)
    "输出SVG卡片"
    (setqdesign-rule"合理使用负空间，整体排版要有呼吸感"
    design-principles'(干净简洁纯色典雅))

    (设置画布'(宽度400高度600边距20))
    (标题字体'毛笔楷体)
    (自动缩放'(最小字号16))

    (配色风格'((背景色(蒙德里安风格设计感)))
    (主要文字(楷体粉笔灰)))

    (卡片元素((居中标题"汉语新解")
    分隔线
    (排版输出用户输入拼音英文日文)
    解释)))

你将会获得一份这样形式的答卷：
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgXaZmcia9EmN16UiaYlSpTO1WfQ2u32fTGP1hSplHcwJqW1drYFhOvNmQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null") ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgeib1fnhMnjribRGpA5KicuGlPrJtxjAibDPbicAmSW3OEG0f8rhU0jNOO9g%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

只需要稍微调整一下文本结构与引用细节，就可以嵌入到我们的提示词中。这样基本也能让提示词按照预期运行起来：

    ##步骤3：Html-PersonalCard 生成
    (defunHTML-PersonalCard(步骤2中提炼的社交名片文案)
    ......

    ###样式要求
    1.整体布局：
    ......

当然，想要更好地控制生成结果，尤其是视觉样式的稳定性，还得经过多次调试，并根据测试 bug 微调提示词，直至稳定运行。

### 拓展：Lisp 、Markdown 格式是否必需？

不是。

经过两年的蓬勃发展，大语言模型的提示工程已经呈现出百花齐放的局面。

无论 LangGPT 结构化提示词，还是 CRISPE 和 CARE 等框架，业界涌现出了多种提示词方法论。

在格式方面，我们看到了 LangGPT 在用的 Markdown 格式，也有像刚哥最近青睐的 Lisp 伪代码格式，甚至还有像我那样灵活混搭的方案。

但真正重要的不是提示词的外在形式，而是内容是否与 AI 的"理解机制"相契合。

**如果要我推荐提示词的写法：**

对于刚入门的朋友：首推 LangGPT 结构化提示词，直观易懂，可以快速上手。

对于想要进阶的用户：

一方面，LangGPT 依然是一个可靠的选择；

另一方面，有额外的精力和好奇心，不妨尝试一下刚哥推崇的 Lisp 伪代码格式，能够强迫自己精炼提示词，对措辞理解、概念认知也有很大帮助。

丰富的二创玩法与衍生思考
------------

这波 AI 可视化输出的 Prompt 热度，从刚哥的「汉语新解」，经过一泽Eze 「社交名片」的思路拓展，再到后续的持续发酵，已经产生更多丰富的二创玩法。

我把最近观察到的 Prompt-based Case 也贴在下方，供大家学习与思考。

**@云中江树**：个人简历生成
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgKm6g2q2TU28nlmLl42eibk8QdVPxiaYal3YLtTp1mZMyHmBhYVtlIS5w%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

**@七只路**：文章内容的可视化总结
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_jpg%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgkIILjeQicRQw8wgwg9Akn7sB4jWicFvoY9sr8jCuYib2zia3Hf2degFB2g%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg "null")

**@laughing哥_hYb8**：万物名片，生成精美的概念解释
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_jpg%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssg1icNrygrm6eu6Ts4Qqg3FloE9srDy8OwDnSLgsDKrfMwdO1uYUxS4Sw%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg "null")

**@宇宙大烧卖**：视频内容总结
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_jpg%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssg2NL3REoiaQFeXyFZlQjCer2Sib62clR6mTjTV1yUvAH5A6nIYO2ibKcLg%2F640%3Fwx_fmt%3Djpeg%26from%3Dappmsg "null")

**@一泽Eze**：AI 图表生成
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnvQBiaFyFB5XpYadWiaPVOssgRw6lwx0LN7gKhv4Hw6TDUcV6d5hp5kiaytbSCib5exgUpyEPo3Syut6w%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg "null")

我们可以看到：

1）大模型的文本生成+可视化输出，大大提升了复杂、大段信息的呈现效果（互联网发展到 2024 年，信息本就该如此多姿多彩）

2）基于 Claude Artifacts 不错的网页布局设计和样式实现能力，正在进一步推动设计、研发的民主化。（无论是直接用提示词生成，还是工程化手段固化 AI 样式代码，都能有效降低应用设计与研发门槛）

根据这两天圈内讨论与读者反馈，我们甚至可以大胆期待，基于大模型的 Artifacts 能力，很可能会迎来一波 AI 创意图文、AI 图表、AI PPT 、AI 产品原型等需求的 Prompt-based 应用的新解法。

结语：关于这波 Prompt 热度的思考
--------------------

提示词当然不是万能的。

随着模型能力提升，提示工程的难度会有所降低，但仍然重要。

AI 无法"管中窥豹"，没有预置训练或引导，再聪明的大模型，也很难完美执行人类任务。

针对每个需求场景，预置系统提示词，依然是 AI 应用面向普通用户推广时的必需品。

但无论是**提示词、RAG，亦或是大模型，都只是可以用来解决需求的一类技术**。这个经验与教训，我们其实已经在多次技术热潮中看到过。

比如，曾经让全球疯狂的区块链，被吹捧为将彻底改变金融体系的革命性技术。然而，除了加密货币交易外，其在实际应用中的突破仍然有限。

再看 5G 技术，它曾被誉为跨时代的通信技术，承诺带来超高速、低延迟的连接。但现实是，普通用户很难感受到与 4G 有质的飞跃，多数需求场景仍在摸索中。

**技术的浪潮永不止息，而人的需求却相对恒定。**

**"看到钉子找锤子"，才能真正尊重人的需求，追求人类最"想要"的解决方案。**

**前 20 年的互联网时代是如此，以后的 AI 时代，同样也是如此。**

*** ** * ** ***

**以上，既然看到这里，如果觉得不错，不妨随手点个赞、在看、转发三连，这将对我有很大的帮助。**

**谢谢你的阅读🌟**

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F7ck8FnyVQnuhpQ7c7yicC34IvgeiagR8kg7eq45vAJ8Vc0xR3Ya0xbtnEk6Ode7iaGy7sJuXAVGYLfzzrFvPXiaxNg%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1%26tp%3Dwebp)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FtcBjXg0JL2SSF9cTk3LcEPmhbW5EGJVJKInqEyCgKRfYNK0kmbGGa65IIlk05BDCMq7vy6ICOZHnxCcibTcUDkQ%2F640%3Fwx_fmt%3Dgif%26wxfrom%3D5%26wx_lazy%3D1%26tp%3Dwebp)

**点击下方账号**

**👇 关注更多精彩内容分享**👇****

![](https://image.cubox.pro/cardImg/4btz1kxpl6ht949kqydqb7y1qdt9lzsmlswyyiegjap9hhr9z4?imageMogr2/quality/90/ignore-error/1)

**一泽Eze**

💎 Build in public，关注 AI 智能体 🧬 本职是产品 🐮 力求多讲"人话" 🎐 初心仍在，希望能「做自己认同的内容，改善一小撮人的生活」

5篇原创内容

公众号

，

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7234507409564106779)
