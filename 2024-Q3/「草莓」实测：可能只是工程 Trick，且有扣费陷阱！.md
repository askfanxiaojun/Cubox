「草莓」实测：可能只是工程 Trick，且有扣费陷阱！
===========================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/-DeHD6vjf0Tt5bwmeeQuXA)金色传说大聪明 赛博禅心

写在前面：

**实际测试 OpenAI 新发布的「草莓」后，发现问题很多**。

在本篇中，我将分几个章节，来进行全面解读，包括：

* 效果与特性

* 价格与限制

* 实现原理

* 一些判断


**长话短说**
--------

中国时间 9 月 13 日凌晨，OpenAI 发布了 o1 系列模型，包括 o1-preview 和 o1-mini，官方称其为「草莓」。《[OpenAI「草莓」今秋发布，随后是「猎户座」](http://mp.weixin.qq.com/s?__biz=MzkzNDQxOTU2MQ==&mid=2247491109&idx=1&sn=e3ebc55bc3ba5ace202dcc05911c0037&chksm=c2bcd323f5cb5a358f4d9a7f60c6c072c02facef672569becace7a334d1b6c74dc9bedf081cc&scene=21#wechat_redirect)》  

从 OpenAI 公布的数据来看，**o1 在STEM（理工科）领域进行了特别优化，在回答之前会进行思考**。在物理、生物和化学问题（GPQA）的基准测试中超越了人类博士水平的准确性。

**Plus 和 Team 的用户可在 ChatGPT 中访问**，o1-preview 限制在了 30 条/周，o1-mini 限制在了 50 条/周

**T5 级别的开发者可以访问其 API**，每分钟最多20并发，且价格昂贵。

目前，**这个模型还是个半成品，并没有工程化完整**：在 ChatGPT 里不支持联网、画图等功能；在 API 里不支持 system、tool 等字段和 json mode、结构化输出等方法。

同时，**这个模型有坑 -你可能会被百倍计费** ：从 pricing table 上看，o1 的价格是 4o 的 6 倍，但这是有迷惑性的！o1 计费并不按最终输出，其中间思考过程所消耗的 token，并被视作output tokens，这意味着 100 tokens 的内容输出，可能会被按 10000 tokens 计费。

这个**模型说是有 32k/64k 的最大输出，但真实输出远没有这么多** 。  

从实际测试的角度，发现 o1 与其说是一个模型，不如说是**基于gpt-4o 的agent，并且做的并不好**。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_jpg%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9d0cN5CUmktDZf3bsgT0lEbrcBziaW5biaeib2ZrGQeTAT2Ks88do434yWg%2F640%3Fwx_fmt%3Djpeg)

进行 structured 输出时，400 报错

**效果与特性**
---------

首先，o1 模型是 OpenAI 官方认定的「草莓🍓」

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dQ2hDzGgCVg4XRlsAzfyiblb135ZDS8EUibREFibupUgmC1RqneCZqGWBg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

其次，奥特曼对此很满意  

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dyDm6Os1ZsrUTiaGPUwbDibTDn4dR4P01YYZyhdPEInor4OWVZzCHDPBw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dbZ7Db5E8SL90iaicsR1cIBsCQl3FqbZ11sm0ITbTyp5iaicOhZ2kqosfUw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

在其测试结果中，o1 在绝大多数重推理任务中显著优于 GPT-4o，相关评估如下：

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dcc5zuVVmTYfQQhDZnbvicp8NfXDmPmzhw4triciahze7ib74cNicSuoibUhg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

结果上看，显著优于 gpt-4o

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dtSiaxzTiaX9YJfXt9wBib0IGj4OHrMO1PhjduGrrA9hfSDGia5tEWsrvEg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

在 MMLU 的多绝大多数子类别中，优于 gpt-4o

同时，根据官方报告，在许多需要推理的测试中，o1 的表现已经达到了人类专家的水平。因为最近一些模型在 MATH 和 GSM8K 测试中表现得非常出色，这些测试已经不足以有效地区分它们的优劣。为了更严谨地评估模型的数学能力，选择了 AIME（美国数学邀请赛），这是一项专门为美国顶尖高中数学学生设立的挑战性考试。

在 2024 年的 AIME 考试中，GPT-4o 的平均成绩只有 12%（1.8/15），而 o1 的平均得分却达到了 74%（11.1/15）。在只用一个答案的情况下，o1 在 64 个样本上的平均正确率达到了 83%（12.5/15）。当使用学习算法对 1000 个样本进行优化排序后，o1 的得分进一步提高到 93%（13.9/15）。这个成绩相当于进入全国前 500 名学生的水平，甚至超过了美国数学奥林匹克的入围标准。  

**价格与限制**
---------

目前 o1 系列模型可通过 ChatGPT 网页版，或者是 API 进行访问：

* o1-preview

  * 128k 上下文

  * 32k 最大输出

  * 旨在解决各个领域复杂问题的推理模型  

  * 训练数据截止于 23 年 10 月

* o1-mini：

  * 128k 上下文

  * 64k 最大输出

  * 一种更快速、更经济的推理模型，特别擅长编程、数学和科学  

  * 训练数据截止于 23 年 10 月

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dNd7Y6xugKYW6409uCeKd6p3KI5Ax6akZL1kUSwWXuha8QXnUpgqnNA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

对于 ChatGPT 网页版，目前仅 Plus 和 Team 用户目前已经可以访问了。对于 Enterprise 以及 Edu 的用户，还需要再等一周：  

* o1-preview：30 条/周

* o1-mini：50 条/周

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dBs4oD0WJ3iaJlz5elS6gqdicA5aB4tufFvXwzmoricicBI0bh6AnomYFbw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

对于 API 用户，如果你的等级在 Tire5 （支付金额\>1000 美金），目前已经可以通过接口进行调用：

* o1-preview：20 RPM，30,000,000 TPM

* o1-mini：20 RPM，150,000,000 TPM

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dWWFUAiaibR9Yj3RDPKeggc4nCRyPEIM5dXrbSSzYpKBkxgoJrtOKTicnw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

**需要注意**

经测试，o1 模型不支持以下内容，并报错：

* system 字段：400 报错

* tools 字段：400 报错

* 图片输入：400 报错  

* json_object 输出：500 报错

* structured 输出：400 报错  

* logprobs 输出：403 报错

* stream 输出：400 报错  

* o1系列：20 RPM，150,000,000 TPM，很低，随时429报错

* 其他：temperature, top_p and n 被固定为1；presence_penalty 和 frequency_penalty 被固定为 0.

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dx1mlXJQNLCSsff6GnZnXgiaC0FHEhvvXGbP1uNKEf9CvEHNGSK8ewnQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

进行 structured 输出时，400 报错

**更需要注意**

对于api，**文档说 o1 可以输出 64k，但实测远非如此**

如：我的 prompt 为「写一部「黑神话悟空」的同人小说，不少于2万字」，但返回的内容只有 1000+字

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9d0WhkmxGR2NonlUvHL89frgbOsiaRVb0KcVZvssew3jLujcIGUtDpLWg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

"谨防电信诈骗"

**实现原理**
--------

简而言之，o1 系列模型，在回答的过程中，本身经历了多次对话，并根据对对话的评估，进行后续生成。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dbJ41XH0Zt1rBMZicIbyNsJnTbfzh7SOqhprHXksqOOwKAFpibZTEFl9w%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

他会先思考，然后总结输出

思考可能不止一步，最长思考步骤为 128k，具体步骤如下：  

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dC0W80A83mHxdAAGWbjZeCD2eUkykN9U7KkMaBTwRnnJGnjjHhNib3Iw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

他会先思考，然后总结输出

需要注意：在 api 调用的过程中，并不会返回中间的思考，比如相同的问题「安徽牛肉板面，为什么是石家庄特产？」，api 侧的返回如下：

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dZZic0mgThStva7ibsaBXRIK16icuqibvk5yDIAgibAf6FZerH9m6hkGUzKA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

我把 id 等信息给 \*\*\* 了

这个时候，你会发现一个严重问题：此处产生了 896 tokens 作为推理。

换个例子，当问题是很简短的「你好」时，其返回如下：  

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dlWUliahzzqLvZRfWtFgchWGDUDouxz4rDKFj0qd0bZL9Dgv1olmuiboQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

输出 471 tokens，其中 448 tokens 为推理，23 tokens为真实输出

同样的问题，问 4o：  

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dw0Gia6PvuFzUEibXoPhKZwMx5gm9PlWMk4bDGtjnzlRdp0h2g9hkFgUg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

输出为 9 tokens

要知道，o1 模型的价格，时 4o-0806 的 6 倍。再加上对推理的消耗（额外n倍），以及这个模型里，token 计算可能比 4o 要多（猜测），api 开支可能会炸！  

以「你好」为例，4o-0806 的费用为($10\*9+$2.5\*8)\*10\^(-6) = 110 \* 10\^(-6)美金；而 o1 模型中，费用则为 ($60\*471+$15\*10)\*10\^(-6)= 28410\*10\^(-6)美金。**在这个案例中，完成相同的任务，o1 比 4o 贵了足足 258 倍！！！**

对于非极端问题，且在 prompt 较短的情况下，比如「安徽牛肉板面，为什么是石家庄特产？」，4o-0806 的开销为2192.5 \* 10\^(-6)美金，而 o1 的开销为 86835 \* 10\^(-6)美金。**在这个案例中，完成相同的任务，o1 比 4o 贵了 40 倍！！！**

**有理由认为：在正常使用中，o1 的开销，会比 4o 贵百倍！**

**一些判断**
--------

首先，我保持一个观点：**这次的「草莓」，与其说是模型优化，不如说是工程优化**

从训练数据，以及训练时间来看，o1-preview，o1-mini，4o，4o-mini的训练数据，都是截止到 2023 年 10 月（而更早的 gpt-4-0125 和gpt-4-turbo 则是截止到 2023 年 12 月）

在抛去 CoT 行为后，可以发现 o1 和 4o 的行为/语言风格高度相似，甚至可以猜测：**这次的「草莓」o1有可能是 gpt-4o 在进行一些微调/对齐后的agent**

当我询问「我的猫为什么不会汪汪叫」的时候，出现了典型的「意图识别」  

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dESffiakKm03lBfvybYciclur9jsQGX9pDxZaRgBLp2Ml1SxGkzcDzBNw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

同时，这个 Agent 做得并不好，甚至不能算是及格。当我用 o1-mini 进行「完整输出千字文」的时候，无论是语言识别、意图识别还是指令遵循，都非常的不尽如人意：  

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9dIQYenUz7RFho7m1fBloVj1R2aEvDaD6smI7cajG44nmFKv3teem7xg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

o1-mini

即便是换用所谓更强的 o1-preview，结果也不尽如人意（选中文字是错的），并且输出也不全。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2F2icSMc1VBIYrQg97EbRJELQ8PzcGWVib9d50jSxGOaXb0aFjqq7S9wWicQAMbExVIzia1baDV3bYKFdfibbx8RQicfjA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

o1-preview

**综上**
------

这个版本的草莓，**远低于预期，甚至不如民间的工程化**。

作为 AI 从业者，有种难以言表的伤感：**我们会喜欢看 OpenAI 的乐子，但绝对不希望看到 OpenAI 塌...**

如果你看到了这...建议返回上一级，看下本次推送的次条：宝玉老师对「汉语新解」的原理解读，相信会更有收获

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7234090100466912159)
