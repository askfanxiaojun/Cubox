AIGC（4）：ChatGPT 为什么避免不了胡说八道？
============================

[www.zhihu.com](https://www.zhihu.com/column/c_1617102776697348096)刘白

目录

收起

1. ChatGPT 为什么避免不了胡说八道？

2. ChatGPT原理：基于Tokenize和概率分布

2.1 升级版的输入法

2.2 搜索引擎式沟通

3.Prompting：简单的任务

1.零样本提示：Zero-Shot Prompting

2.少样本提示：Few-Shot Prompting

4.复杂推理：思维链

4.1 Chain-of-Thought Prompting

4.2 自洽性

5. 结论

1.关键词对知识的引导非常关键

2. 分析思路引导很重要

3. ChatGPT需要用户不断细化问题

6. 参考资料

该专题下前3篇文章：

[刘白：ChatGPT vs Perplexity AI：谁更老实？哪个更适合学习新领域？0 赞同 · 0 评论文章![](https://image.cubox.pro/article/2023040610331490877/45720.jpg?imageMogr2/quality/90/ignore-error/1)](https://zhuanlan.zhihu.com/p/612513616)

[让ChatGPT更聪明：使用Prompts进行语言模型优化24 赞同 · 5 评论文章![](https://image.cubox.pro/article/2023040610331289306/22313.jpg?imageMogr2/quality/90/ignore-error/1)](https://zhuanlan.zhihu.com/p/612587257)

[无限次数！轻松训练stable-diffusion生成精美图片15 赞同 · 8 评论文章![](https://image.cubox.pro/article/2023040610480326761/20502.jpg?imageMogr2/quality/90/ignore-error/1)](https://zhuanlan.zhihu.com/p/613483110)

1. ChatGPT 为什么避免不了胡说八道？
-----------------------

当然，这个问题我也问了ChatGPT，链接放在文末参考资料了，我来总结一下：

我们可以用一个生动的比喻来解释。ChatGPT就像一个只有三岁的孩子，他虽然看了很多书，但并不真正理解书中的内容。

他只是通过强大的记忆力将这些知识存储在大脑中，并根据一些模糊的规律来联想相关的词汇和短语。

每当他听到一些话时，他就会按照这些模糊的规律组织出一些语句，然后从中选择一段来说出来，这些语句看起来符合语法规则，但有时候可能会胡说八道。
![](https://image.cubox.pro/article/2023040610480389261/50554.jpg?imageMogr2/quality/90/ignore-error/1)

**2.** ChatGPT原理**：**基于Tokenize和概率分布
------------------------------------

### 2.1 升级版的输入法

ChatGPT的工作原理可以类比于输入法，但是它是一种**大数据下**的数据处理方法。

在输入法中，我们需要输入一些相关的拼音、字母、词语，这是输入法就会快速联想出下一个词或者下一句话。
![](https://image.cubox.pro/article/2023040610480368798/29194.jpg?imageMogr2/quality/90/ignore-error/1)

上图中，我只输入了"小朋友们"，然后剩下内容"今天我们一起出去玩吧"都是输入法，一步一步提示出来的，所以前几年大家可能会觉得搜狗输入法特别好用，打字特别顺滑，不像windos自带的输入法，贼难用！原理就是学习了足够多的文本数据，知道大家通常想要说什么，默契如火烧眉毛，心领神会。

而在ChatGPT中，我们输入的文本会被切分成一个个的"token"翻译过来叫做令牌，也就是模型识别文本的基本单位，然后传入一个黑箱模型中，这个模型会输出概率最大的下一句话，在学习了500G巨量（GPT3）的数据之后，ChatGPT拥有类升级版的输入法能力，可以对一段话进行逐步预测！

### 2.2 搜索引擎式沟通

所以，我们不能仅仅凭借直觉来输入关键词，而应该使用精准的关键词来获取符合需求的结果。和搜索引擎类似，我们需要输入相关的关键词来得到我们想要的结果。

由于ChatGPT的原理基于概率分布，它并不能理解具体的话语，而是根据输入的内容找到概率最大的下一句话。因此，特殊的提示词非常重要，就像文本生成图片那样，某些特别的概念可以实现某种效果。

但是，如果**用太简单的概念或者陌生的描述，就可能无法达到预期的效果**。

**因此，我们仍需要深入研究不同的"咒语"。**

最新的ChatGPT4已经发布，据传其各种学术测试能力大幅提升，但仍可能会出现常识性错误，这是由模型原理本身决定的，因为模型是基于数据训练得出的概率分布。

所以，Prompting 的研究还是非常有意义的，因为模型原理决定它无法避免错误，并且需要更精细的描述才能调用准确的领域知识。

**从官网给出的图片显示，无论是GPT3.5还是GPT4在做LeetCode题目的时候，正确率都是随着难度的提升而提升。**

**所以简单的任务，甚至不需要提示就可以很好完成，但是随着逻辑变得更复杂，其完成的概率会逐渐降低。**   
![](https://image.cubox.pro/article/2023040610480363323/86314.jpg?imageMogr2/quality/90/ignore-error/1)
GPT4和GPT3.5的对比

**3.** Prompting：**简单的任务**
--------------------------

### **1.零样本提示：Zero-Shot Prompting**

输入：分类词性任务  
输出：正确输出结果
![](https://image.cubox.pro/article/2023040610480354792/90017.jpg?imageMogr2/quality/90/ignore-error/1)

### **2.少样本提示：Few-Shot**Prompting

如果零样本提示效果不好，那就可以考虑增加样本，  
如果一个样本效果不好，可以多加几个样本

输入：一个案例+造句任务  
输出：正确输出结果
![](https://image.cubox.pro/article/2023040610480394545/99015.jpg?imageMogr2/quality/90/ignore-error/1)

**4.复杂推理：思维链**
--------------

### **4.1 Chain-of-Thought Prompting**

Chain of Thoughts,有一种现象称为"思维链"，如果给出诸如"仔细考虑并显示您的步骤"之类的提示，大型AI语言模型的性能会好得多。如果增加这样的提示，难倒 ChatGPT 的数学和单词问题通常都能被解决。

**关键** **Prompts**：让我们逐步思考 Let's think step by step.
![](https://image.cubox.pro/article/2023040610480352437/64996.jpg?imageMogr2/quality/90/ignore-error/1)

### 4.2 自洽性

自洽[1](https://link.zhihu.com/?target=https%3A//learnprompting.org/docs/intermediate/self_consistency%23fn-1) 是 思维链的衍生产品，可生成多个思维链的答案而不是一个，对输出的结果进行统计得到的多数结果更有可能接近正确答案。

**下图是思维链引导的例子：**

通过简单提示"Let's think step by step."  
就可以让ChatGPT逐步思考，形成一个思维链条  
结果表明，在这项任务上的结果是很不错的！
![](https://image.cubox.pro/article/2023040610480335537/26863.jpg?imageMogr2/quality/90/ignore-error/1)

而，**自洽是指通过充分地思维链提示，对ChatGPT进行训练，然后多次计算得到结果**

会发现ChatGPT可以从多种思路进行思考，虽然有时推理错误，但是多数结果是正确的，只需要多运行几次取多数结果即可。
![](https://image.cubox.pro/article/2023040610480361867/40236.jpg?imageMogr2/quality/90/ignore-error/1)

**结果1：第一种思维链，70-6+3 = 67**
![](https://image.cubox.pro/article/2023040610480381967/42823.jpg?imageMogr2/quality/90/ignore-error/1)

**结果2：第二种思维链，70-（6-3）= 67**
![](https://image.cubox.pro/article/2023040610480320905/84305.jpg?imageMogr2/quality/90/ignore-error/1)

完整内容参考这里：[https://shareg.pt/w4fjr4A](https://link.zhihu.com/?target=https%3A//shareg.pt/w4fjr4A)

5. 结论
-----

### **1.关键词对知识的引导非常关键**

ChatGPT 模型基于 Tokenize 和概率分布，类比于输入法，在输入的文本中切分成一个个的"token"，然后传入模型中，模型会输出概率最大的下一句话。

### **2. 分析思路引导很重要**

通过Prompting 技术包括零样本提示、少样本提示和思维链路引导等，可以帮助提高 ChatGPT 模型的准确性。但是，ChatGPT 模型仍有可能出现错误，需要更精细的描述才能调用准确的领域知识。

### 3. **ChatGPT需要用户不断细化问题**

ChatGPT是基于概率分布生成内容，所以一开始的回答可能会很泛泛，但是随着问题的聚焦，ChatGPT可以掌握更具体地情景和上下文信息，从而更有效地从它地领域知识库中调用相关知识。

6. 参考资料
-------

1. [Chain of Thought Prompting \| Learn Prompting](https://link.zhihu.com/?target=https%3A//learnprompting.org/docs/intermediate/chain_of_thought)
2. [Zero Shot Chain of Thought \| Learn Prompting](https://link.zhihu.com/?target=https%3A//learnprompting.org/docs/intermediate/zero_shot_cot)
3. [Self-Consistency \| Learn Prompting](https://link.zhihu.com/?target=https%3A//learnprompting.org/docs/intermediate/self_consistency)
4. [翻电Special 建立当下与chatGPT协作的迫切性、想象力和技术 feat.雍福会•碎片谈 VOL.113 - 翻转台电（翻电） \| 小宇宙](https://link.zhihu.com/?target=https%3A//www.xiaoyuzhoufm.com/episode/63f34f445835080b932bb172)
5. [刘白：让ChatGPT更聪明：使用Prompts进行语言模型优化](https://zhuanlan.zhihu.com/p/612587257)
6. [【问ChatGPT】：ChatGPT 为什么避免不了胡说八道？](https://link.zhihu.com/?target=https%3A//flowgpt.com/chat-share/983672cd-d31e-4645-92a1-5385394aba04)

<br />

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7043479414411100923)
