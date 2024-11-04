AIGC(2)：让ChatGPT更聪明：使用Prompts进行语言模型优化
=====================================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/612587257)刘白做一个践行者，去接近那个狂妄自大的美梦

目录

**上一篇：**

[刘白：ChatGPT vs Perplexity AI：谁更老实？哪个更适合学习新领域？0 赞同 · 0 评论文章![](https://image.cubox.pro/article/2023040610331490877/45720.jpg?imageMogr2/quality/90/ignore-error/1)](https://zhuanlan.zhihu.com/p/612513616?)

### 简介：

词语翻译：

1. Prompt：提示词
2. Prompt Engineer：提示工程师
3. Prompt Engineering：提示工程，最近主流的意思是匹配内容需求和模型理解的词语选择。
4. AI：人工智能

1.Prompt Engineer
-----------------

一句话概括：提示工程是为 AI 模型开发和优化提示以有效地将语言模型 （LM） 用于各种应用程序的过程。

### 1.1 "Prompt"：人工智能的语言

这是人类与人工智能 （AI） 对话的方式 AI无法真正理解人类的语言，近几年的大语言模型（LLMs）对人类语言的理解能力逐渐上升，但目前依然需要依靠特定的提示词才能够更有效地完成

### 1.2"Prompt Engineering"：匹配自然语言和数据

*解释1：模型训练的过程的提示工程*，相当于为训练数据打上提示词标签。 它是对任务的描述作为问题嵌入到输入中，而不是隐式给出。GPT-2和GPT-3语言模型是提示工程的重要步骤。 2021年，使用多个NLP数据集进行的多任务提示工程在新任务上表现良好。在少样本学习示例中包含一连串的思路的提示表现出更好的语言模型推理能力的迹象。

*解释2：用户使用模型过程的提示工程*，相当于逆向使用为训练时的标签 这是提示工程师的工作当前流行称呼，以下默认提示工程师为这个概念下的解释。

### 1.3 提示工程对企业的好处

通过提供具体的提示，可以引导模型在上下文中生成最相关和连贯的输出。从而稳定生成需求文字、图片和视频等，提高效率的同时控制成本。

2.何开始提示工程
---------

### 2.1 提示工程的技巧

### 2.1.1 公式1：固定文本格式

这是一个 **MidJourney 提示公式**：
> (image we're prompting), (5 descriptive keywords), (camera type), (camera lens type), (time of day), (style of photograph), (type of film) Please respond with "yes" if you understand the formula

通过明确以上关键维度来生成图片
![](https://image.cubox.pro/article/2023040610331464913/34799.jpg?imageMogr2/quality/90/ignore-error/1)

完整Prompts 请看链接：[按照公式生成7组关于中国年的Midjourney的Prompts](https://link.zhihu.com/?target=https%3A//sharegpt.com/c/Qhj9W80)

### 2.1.2 公式2:成熟的理论或模型

公式的第二层理解是，在特定领域都有个字的成熟理论和模型，如果能够快速使用这些理论和模型来进行内容的构建，那么就可以大大提高内容生产的效率。 从主题创建高质量视频脚本的步骤和方法。需要完成四件事：

1. 角色扮演：使用Char GPT切换到特定的专业角色，如律师、会计师、CEO或营销经理，生成专业内容。
2. 提供模型：给ChatGPT一个特定的模型，如PAS公式，以快速吸引观众的注意力，吸引他们的痛点，并提供解决方案。
3. 使用有效的文案技巧：使用PAS公式编写有效的文案，吸引观众的情感，并为他们的问题提供解决方案。
4. 创建有效的模型：利用ChatGPT，创建有效的销售页面、着陆页面和产品描述模型，这在营销领域中是非常有价值的，因为有效的文案写作很少见。

通过遵循这些步骤和利用Char GPT的能力，可以创建能够吸引观众并提供有价值信息的高质量视频脚本。

### 2.1.3 角色扮演：提取领域知识

这就是前面步骤中的第一步角色扮演，给ChatGPT切换到特定领域的专业角色，这样可以更好地调动该领域地知识。 例如通过让ChatGPT扮演一个营销大师，然后把相关得信息喂给他，让它写一个故事去推广一款猫粮 !
![](https://image.cubox.pro/article/2023040610331445441/33408.jpg?imageMogr2/quality/90/ignore-error/1)

完整Prompts见：[使用ChatGPT进行故事营销文案生产](https://link.zhihu.com/?target=https%3A//shareg.pt/LbEwvPi)

以下是参考资料来源快速从 PerplexityAI 中获得，简单筛选就可以贴在文案后面！
![](https://image.cubox.pro/article/2023040610331462037/39708.jpg?imageMogr2/quality/90/ignore-error/1)

完整内容如下：[你觉得养猫好，还是养狗好？ - 知乎 (zhihu.com)](https://www.zhihu.com/question/444918505/answer/2927057683)

### 2.1.4 从描述中学习

参考上一小节的内容，其中提供猫粮商品信息，以及故事主题等就是通过描述来让ChatGPT学习人类的要求，这是人类常用的方式，如果可以**尽量多地提供相关信息**可以让输出更有针对性。

完整一点，甚至有人通过**2-3页Word文档**内容来让ChatGPT理解背景信息即用户需求。

再进一步，业界有一种模型应用叫做**Model tuning** 的应用方式，这是从模型层面去重新训练，让模型可以更有效应对垂直领域的问题。

### 2.2 实现Prompt Engineering解决方案的挑战

### 2.2.1 领域知识

知道领域内有哪些成熟的好用的方法，便可以更轻易地调动AI地能力，例如行为相关的2个模型： 1. 福格行为模型（MAP）：动机不可靠 福格行为模型 = 动机（M） + 能力（A） + 提示（P），该理论属于行为主义学派，认为人在某种程度上就是个机器，把机器训练好需要不断地重复。人有动机和主动性，但是不够稳定。 2. 认知行为模型（CBT）：行为+认知 认知行为疗法（CBT）是一种心理治疗方法，它整合了行为疗法和认知疗法。该方法的目标是帮助患者意识到不正确或消极的想法，并以更有效的方式应对挑战。 每一个模型都是特定领域特定场景的解决方案，当我们了解足够多的模型和使用场景之后，只需要匹配需求和模型即可，剩下的交给AI，文本生成领域如此，图像生成领域同理，只不过是模型的变量不同了而已，匹配的就是图像风格、镜头、 知道领域内有哪些风格、细节才能够自由匹配需求

### 2.2.2 模型原理

知道模型是如何训练的、Prompts是什么才能够更好地理解数据地产出，以及选择合适地prompts，相关资料如下：

视频：

1. [GPT，GPT-2，GPT-3 论文精读【论文精读】 - YouTube](https://link.zhihu.com/?target=https%3A//www.youtube.com/watch%3Fv%3Dt70Bl3w7bxY%26t%3D2700s)
2. [Transformer论文逐段精读 - YouTube](https://link.zhihu.com/?target=https%3A//www.youtube.com/watch%3Fv%3DnzqlFIcCSWQ)
3. [DALL·E 2【论文精读】 - YouTube](https://link.zhihu.com/?target=https%3A//www.youtube.com/watch%3Fv%3DhO57mntSMl0%26t%3D297s)
4. [InstructGPT 论文精读【论文精读】 - YouTube](https://link.zhihu.com/?target=https%3A//www.youtube.com/watch%3Fv%3DzfIGAwD1jOQ%26list%3DRDCMUC8WCW6C3BWLKSZ5cMzD8Gyw%26index%3D2)

文本：

1. [Introducing ChatGPT (openai.com)](https://link.zhihu.com/?target=https%3A//openai.com/blog/chatgpt)
2. [How BERT and GPT models change the game for NLP - Watson Blog (ibm.com)](https://link.zhihu.com/?target=https%3A//www.ibm.com/blogs/watson/2020/12/how-bert-and-gpt-models-change-the-game-for-nlp/)

### 3.结论和展望

Prompt Engineering是为AI模型开发和优化提示以有效地将语言模型用于各种应用程序的过程。Prompt是指在人工智能与人类对话中使用的语言，是将自然语言和数据匹配的过程。 Prompt Engineering的好处包括引导模型生成最相关和连贯的输出，提高效率的同时控制成本。要开始Prompt Engineering的关键是掌握领域知识和模型原理！需要掌握技巧，包括使用公式、成熟的理论或模型、角色扮演以及通过描述学习。

如今，很多意识到了Prompt Engineering的重要性，于是出现了许多Prompt 分享和聚合平台，见参考资料的4.5，甚至有人推出了自动优化Prompt 的服务，见参考资料的6

未来，随着模型规模越来越大，Prompt Engineering的重要性可能会随之降低，但是就如同计算机编程技能一样，永远都是有价值的，直接和系统的更底层进行对话，可以完成更多和更自由的操作！

### 参考资料

1. [Turn ChatGPT into a Powerful Midjourney Prompt Machine - YouTube](https://link.zhihu.com/?target=https%3A//www.youtube.com/watch%3Fv%3DE2XJgyWARW8)
2. [30分钟生产3个月全平台视频内容文案，用最牛2个AI工具Notion AI和ChatGPT最牛配合工作流程和模型（2023终极方案） - YouTube](https://link.zhihu.com/?target=https%3A//www.youtube.com/watch%3Fv%3DA760_yCp-wU%26list%3DLL%26index%3D3%26t%3D1038s)
3. [按照公式生成7组关于中国年的Midjourney的Prompts](https://link.zhihu.com/?target=https%3A//sharegpt.com/c/Qhj9W80)
4. [PromptHero - Search prompts for Stable Diffusion, DALL-E \& Midjourney](https://link.zhihu.com/?target=https%3A//prompthero.com/)
5. [PromptBase \| Prompt Marketplace: DALL·E, Midjourney, ChatGPT, Stable Diffusion \& GPT-3](https://link.zhihu.com/?target=https%3A//promptbase.com/)
6. [PromptPerfect - Elevate your prompts to perfection (jina.ai)](https://link.zhihu.com/?target=https%3A//promptperfect.jina.ai/)

下一篇：

[AIGC(3)：无限次数！轻松训练stable-diffusion生成精美图片15 赞同 · 8 评论文章![](https://image.cubox.pro/article/2023040610331435165/75825.jpg?imageMogr2/quality/90/ignore-error/1)](https://zhuanlan.zhihu.com/p/613483110)

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7043479274967272464)
