LLM经典论文速读版，看完感觉自己通透了
====================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/HaXZedhdKmteN8zPSk-tmw)皇子 皇子谈技术


读不下去的，略读也是不错，美名曰"好读书，不求甚解；每有会意，便欣然忘食。"

##### 大家好，我是皇子。

对于渴望深入理解AI的爱好者和研究者来说，阅读经典论文不仅是获取知识的途径，更能让我们产生新的思维方式。

历史文章分享过一次`《Attention is All You Need》`论文的精读，我也不是算法和机器学习的从业者，有很多不解，但是不影响我在后面学习大语言模型（LLM）相关技术时提供了理论基础。

《Attention is All You Need》这篇论文堪称经典一点不为过，早期的`GPT`、`BERT`、`T5`大语言模型都是在此论文提供的Transformers框架上进行后续的模型设计和优化的。

所以今天，为大家推荐**31篇LLM的经典论文之作速读版，看完感觉自己通透了**，包含：大语言模型架构、RAG、预训练、微调、提示词等。

在此之前，先分享一个想看**中文翻译版原文**的高效办法：

*
  为了方便中文阅读：安装浏览器插件"沉浸式翻译（https://immersivetranslate.com）"，支持多种浏览器，多个翻译服务。

*
  PDF翻译后样式不方便阅读，调整为HTM版本：将 arxiv PDF 论文原地址域名中的 `x` 更换成 `5`即变成可访问的HTML版本链接，然后就可以愉快的使用"沉浸式翻译"进行原文阅读了。

> 例如：
>
> arxiv PDF 论文原地址：https://arxiv.org/abs/2109.01652
>
> 替换后HTML版本的链接：https://ar5iv.org/abs/2109.01652

*
  论文中看不懂的`公式`/`概念`，对于不是搞算法的可以不用专研，毕竟没有算法功底和更详细的上下文有些很难读懂，google或者AI一下知道是干嘛的就够了（个人阅读习惯，大佬跳过～）。

**31篇LLM的经典论文速读版清单**

**节选来源：劉智皓 \|https://tomohiroliu22.medium.com/66%E5%80%8B%E5%A4%A7%E5%9E%8B%E8%AA%9E%E8%A8%80%E6%A8%A1%E5%9E%8Bllm%E7%B6%93%E5%85%B8%E8%AB%96%E6%96%87-0fcdab74e822**

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIvzGUGumNhOq6pfg7ib2YUmiaLZvGricRrz4PJH5ePtzsicCXQ54hZUnNUg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

1. Transformer
--------------

> **论文名称：**《Attention is all you need》
>
> **发布时间**：2017/06/12
>
> **发布单位**：Google、多伦多大学
>
> **简单摘要**：所有LLM的始祖，迈向NLP新时代的基础架构
>
> **中文摘要**：传统的序列转换模型使用复杂的循环或卷积神经网络，包括编码器和解码器。表现最好的模型会透过注意力机制连接编码器和解码器。
>
> 而我们提出了一种新的简单网络结构，Transformer，完全基于注意力机制，不再使用循环和卷积。
>
> 我们在两个机器翻译任务上进行实验，发现这些模型在质量上的表现优越，并且更容易进行平行运算，训练所需时间明显减少。
>
> 我们的模型在WMT 2014年英德翻译任务上达到了28.4 BLEU，比现有最佳结果（包括整体模型）提高了超过2 BLEU。在WMT 2014年英法翻译任务中，我们的模型在八个GPU上训练3.5天后，取得了新的单模型最佳BLEU分数41.8，训练成本仅为文献中最佳模型的一小部分。
>
> 我们展示了无论是在大量或有限的训练数据下，Transformer在其他任务中的泛化能力，成功应用于英语组成句分析。
>
> **论文链接**：https://arxiv.org/pdf/1706.03762.pdf
>
> **核心技术**：模型架构
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIXGjKfyK2iatn9iaqKPEAKtbCicFtCStokBHY5kqwK0Fa6wicHFA5ax0xkQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

2. GPT-1
--------

> **论文名称**：《Improving language understanding by generative pre-training》
>
> **发布时间**：2018/06/11
>
> **发布单位**：OpenAI
>
> **简单摘要**：autoregreesive Transformer始祖
>
> **阅读重点**：多层Transformer解码器、自回归模型
>
> **中文摘要**：自然语言理解涵盖众多不同的任务，如文本蕴涵、问答、语义相似度评估和文件分类。
>
> 尽管有丰富的未标记文本资料，但用于这些特定任务的标记数据稀缺，使得训练有判别式的模型难以表现良好。
>
> 我们证明通过对未标记文本的语言模型进行生成式预训练，再对每个特定任务进行判别式微调，可以在这些任务上取得巨大进步。
>
> 与以往方法不同，我们在微调期间利用任务感知的输入转换，实现有效的转移，同时最大限度地减少对模型架构的更改。
>
> 我们展示了我们方法在自然语言理解的众多基准测试上的有效性。我们通用的任务无关模型在12个研究的任务中，有9个显著优于专门为每个任务设计的判别式训练模型表现。例如，在常识推理（Stories Cloze Test）上，我们实现了8.9％的改善，在问答（RACE）上为5.7％，在文本蕴涵（MultiNLI）上为1.5％。
>
> **链接论文**：https://arxiv.org/pdf/1810.03993.pdf
>
> **核心技术**：有监督微调架构
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIRfyvGSY4M4DIArm9QxdQD2xVvPuUX3a0uAqwWVl0Vd9O5sKdgPXv3A%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

3. BERT
-------

> **论文名称**：《BERT: Pre-training of Deep Bidirectional Transformers for Language Understanding》
>
> **发布时间**：2018/10/11
>
> **发布单位**：Google
>
> **简单摘要**：autoencoding Transformer始祖，迈向NLP fine-tuning时代
>
> **阅读重点**：自动编码模型、屏蔽标记和下一句预测。
>
> **中文摘要**：我们提出了一个名为BERT（从Transformer中得到的双向编码器表征）的新语言表征模型。
>
> 与最近的语言表征模型不同，BERT目标是从未标记文本中预训练深度双向表征，同时在所有网路层上联合考虑左右两侧的文本内容。
>
> 因此预训练的BERT模型只需进行一个额外的输出层微调，就可以创建出各种任务的最新模型，例如问答和语言推理，而无需大幅修改特定任务的架构。
>
> BERT概念简单且实验证明其效果非常好。它在包括GLUE得分提升至80.5％（绝对改善了7.7个百分点）、MultiNLI准确度提升至86.7％（绝对改善了4.6个百分点）、SQuAD v1.1问答测试F1提升至93.2（绝对改善了1.5个百分点）和SQuAD v2.0测试F1提升至83.1（绝对改善了5.1个百分点）等11项自然语言处理任务中取得了新的最佳结果。
>
> **链接论文**：https://arxiv.org/pdf/1810.04805.pdf
>
> **核心技术**：基于无监督特征的方法
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaI8iaoBiaMVL85iaucsjrzwrYr2IyBRckXuyPvs0dgic0PZz57IGlXjktfVA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

4. Transformer-XL
-----------------

> **论文名称**：《Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context》
>
> **发布时间**：2019/01/09
>
> **发布单位**：Google、卡内基麦隆大学
>
> **简单摘要**：让Transformer可以吃更长的句子
>
> **阅读重点**：上下文分片、段级递归机制、相对位置嵌入
>
> **中文摘要**：Transformer模型在学习长期依赖性方面具有潜力，但在语言模型的情境下受到固定长度上下文的限制。
>
> 我们提出了一种新颖的架构Transformer-XL，能够在不干扰时间连贯性的情况下实现超越固定长度的依赖性。它包括一个分段层级的循环机制和一种新颖的位置编码方法。我们的方法不仅能捕捉更长期的依赖性，还解决了上下文碎片化的问题。
>
> 在结果中，Transformer-XL学习的依赖性比RNNs长80%，比原本的Transformer长450%，并在短序列和长序列上都表现更好，且评估过程中比基本的Transformer快了1800倍以上。特别值得注意的是，我们在bpc/perplexity上将enwiki8改进到了0.99，text8改进到了1.08，WikiText-103改进到了18.3，One Billion Word改进到了21.8，Penn Treebank改进到了54.5（无需微调）。当仅在WikiText-103上进行训练时，Transformer-XL能够生成具有数千个标记的合理连贯的新文章。
>
> **链接论文**：https://arxiv.org/pdf/1901.02860.pdf
>
> **核心技术**：带状态重用的片段级递归
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIf65YNNfyiabuOTBjoiacAKXnNc0G1OpdKp8FC1kwh8wfb0AUyxSJ2meA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

5. GPT-2
--------

> **论文名称**：《Language models are unsupervised multitask learners》
>
> **发布时间**：2019/02/24
>
> **发布单位**：OpenAI
>
> **简单摘要**：不想fine-tune，我想要一个通用模型所有任务直接zero-shot
>
> **阅读重点**：multi-task pre-training、模型到底是达到generalization还是memorization
>
> **中文摘要**：自然语言处理任务，如问答、机器翻译、阅读理解和摘要，通常使用特定任务的监督式学习来处理。
>
> 我们展示了语言模型在没有明确监督的情况下，学习名为WebText的数百万网页数据集。
>
> 当语言模型在一个文档加上一个问题的情境下，生成的答案在CoQA数据集上达到55的F1分数，与4个基准系统中的3个相匹配或超越，而不需要使用超过127,000个训练范例。语言模型的容量对于zero-shot任务迁移的成功至关重要，增加容量能够以对数线性方式提升跨任务的性能。我们最大的模型GPT-2是一个拥有15亿参数的Transformer，在zero-shot设置下，在8个测试的语言模型数据集中有7个达到了最新的结果，但在WebText上仍然不够充分。模型产生的样本反映了这些改进，包含了连贯的文字段落。这些发现暗示了一条有前景的道路，即构建能够从自然发生的范例中学习执行任务的语言处理系统。
>
> **论文链接**：https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf
>
> **核心技术**：语言模型是无监督的多任务学习者
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIyOr7icOSjC7JLbKuMLwUppCqd2TUFZPreTwLmQibRmMhNLDeRRicicyJOg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

6. ERNIE
--------

> **论文名称**：《ERNIE: Enhanced Language Representation with Informative Entities》
>
> **发布时间**：2019/05/17
>
> **发布单位**：北京清华大学、华为
>
> **简单摘要**：把知识图谱一起整合在BERT上
>
> **阅读重点**：结构化知识编码、异构信息融合、知识编码器
>
> **中文摘要**：神经语言表征模型，例如在大规模文本语料库上预先训练的BERT，能够从纯文本中捕捉丰富的语义模式，并进行微调以持续提升各种自然语言处理任务的性能。
>
> 但是现有的预训练语言模型很少考虑将知识图谱（KGs）纳入其中，而KGs可以提供丰富的结构化知识事实，有助于更好地理解语言。
>
> 我们认为KGs中的讯息性实体可以增强语言表征的外部知识。所以我们同时利用大规模文本语料库和知识图谱来训练一个增强语言表示模型（ERNIE），它能同时充分利用词汇、句法和知识讯息。实验结果表明，ERNIE在各种知识驱动任务上取得了显著的改善，同时在其他常见的自然语言处理任务上与最先进的模型BERT相当。
>
> **链接论文**：https://arxiv.org/pdf/1905.07129.pdf
>
> **核心技术**：提出了具有信息实体的增强语言表示（ERNIE），该模型在大规模文本语料库和知识图谱上预训练了语言表示模型
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaI4RQiaibS84rLEj2lmqZKjHpvWJiaOghBR5xK0EyZ0ZGPyOfakqSvLwmlg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

7. DistilBERT
-------------

> **论文名称**：《DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter》
>
> **发布时间**：2019/10/02
>
> **发布单位**：Hugging Face
>
> **简单摘要**：利用知识蒸馏训练更小的BERT。
>
> **阅读重点**：Teacher-Student的架构、distillation loss
>
> **中文摘要**：随着大规模预训练模型在自然语言处理中变得更加普遍，将这些大模型应用在边缘运算或有限计算资源的情况下仍然具有挑战性。
>
> 在这项工作中，我们提出了一种方法来预训练一个较小的通用语言表征模型，称为DistilBERT，然后可以对其进行微调，使其在各种任务上表现的和大型模型一样好。
>
> 尽管大多数先前的工作都探讨了使用蒸馏方法来构建特定任务模型，我们在预训练阶段利用知识蒸馏，并展示了可以将BERT模型的尺寸减少40%，同时保留了97%的语言理解能力并且速度提升了60%。为了利用大型模型在预训练过程中学到的归纳偏差，我们引入了三重损失，结合了语言模型、蒸馏和余弦距离损失，让我们可以以更便宜的价格预训练更小、更快、更轻的模型，并且在概念验证实验和在设备比较研究中展示了其在设备上计算的能力。
>
> **链接论文**：https://arxiv.org/pdf/1910.01108.pdf
>
> **核心技术：**预训练语言模型。
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIb4uqibiaI56W7ueP5YFnnT72KGZvExUGeN7IjiaZ9Ob4pNo5EGBPaQ0zA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

8. T5
-----

> **论文名称**：《Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer》
>
> **发布时间**：2019/10/23
>
> **发布单位**：Google
>
> **简单摘要**：把NLU和NLG全部都当成seq2seq任务来训练吧
>
> **阅读重点**：input and output format、架构比较、预训练任务目标、ensemble效果比较
>
> **中文摘要**：迁移式学习在NLP中崭露头角，其指的是模型先在数据丰富的任务上进行预训练，然后再微调用于后续任务，这种方式已成为一种强大的技术。
>
> 迁移式学习的有效性催生了多种方法、理论和实践。所以本文通过引入一个统一框架，将所有基于文本的语言问题转换成文本到文本的格式，来探索NLP的迁移式学习技术。
>
> 我们的系统性研究比较了数十种语言理解任务的预训练目标、架构、无标注数据集、迁移式方法等因素。通过将我们探索的见解与规模和新的"巨大清理爬取语料库"相结合，我们在许多涵盖摘要、问答、文本分类等领域的基准测试中取得了最先进的结果。
>
> **链接论文**：https://arxiv.org/pdf/1910.10683.pdf
>
> **核心技术**：对待每一个文本处理问题作为一个"文本的文字"问题，即把文字输入和生产新的文本作为输出。
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIjCGHgepShrz7IfLs54jIIS8h6rC3PXCv9RcPiaGWxgHITSTCFySH5ow%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

9. Retrieval-Augmented Generation (RAG)
---------------------------------------

> **论文名称**：《Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks》
>
> **发布时间**：2020/05/22
>
> **发布单位**：Facebook(Meta)、伦敦大学学院、纽约大学
>
> **简单摘要**：结合资料库检索，让LLM变得更强、回答讯息更正确
>
> **阅读重点**：RAG-序列和RAG-token模型，检索器和生成器架构
>
> **中文摘要**：大型预训练语言模型已证实在其参数中储存事实知识，并在微调后在下游自然语言处理任务中取得了最先进的成果。
>
> 然而它们访问和精确操作知识的能力仍然有限，在知识密集型任务上，它们的表现落后于特定任务架构。
>
> 此外为其决策提供出处讯息和更新其世界知识，仍是开放性的研究问题。虽然具有可微访问机制的预训练模型，能够使用明确的非参数化记忆，但到目前为止，这些模型仅用于探讨摘要性的下游任务。
>
> 所以我们探索了一种用于检索增强生成（RAG）的通用微调方法--- 这些模型结合了预训练的参数化和非参数化记忆以进行语言生成。
>
> 在RAG模型中，参数化记忆是一个预训练的seq2seq模型，而非参数化记忆是维基百科的密集向量索引，其通过预训练的神经检索器进行访问。另外我们比较了两种RAG形式，一种在整个生成序列中条件于相同的检索段落，另一种可以每个标注使用不同的段落。我们对一系列知识密集型自然语言处理任务进行了微调和评估，在三个开放领域的问答任务中取得了最先进的成果，优于参数化seq2seq模型和特定任务的检索和提取架构。对于语言生成任务，我们发现RAG模型生成的语言更加具体、多样且具有事实性，超过了最先进的仅参数化seq2seq基线。
>
> **链接论文**：https://arxiv.org/pdf/2005.11401.pdf
>
> **核心方法**：联合"预训练的检索器（查询编码器+文档索引）"+"预训练的seq2seq模型（生成器）"+"微调"端到端
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaILJJqyjFHCMDF9dic1a3hXe5SckwkXibAnaWOMWAUicu2Qujiabzapic3PVg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

10. GPT-3
---------

> **论文名称**：《Language Models are Few-Shot Learners》
>
> **发布时间**：2020/05/28
>
> **发布单位**：OpenAI
>
> **简单摘要**：别再玩fine-tune了，in-context learning和钱钱才是王道
>
> **阅读重点**：limitations、不使用fine-tune原因、data contamination、in-context learning
>
> **中文摘要**：最近的研究表明，通过对大量文本进行预训练，然后在特定任务上进行微调，可以在许多自然语言处理任务和基准测试中取得显著进展。
>
> 尽管在架构上通常是通用任务的，但这种方法仍需要数千甚至数万个特定任务的微调数据集。相比之下，人类通常可以仅凭几个例子或简单的指令来完成新的语言任务，而当前的自然语言处理系统在这方面仍然存在很大挑战。
>
> 所以在这里，我们扩展语言模型，来大幅改善了通用任务、少量样本的性能，有时甚至达到了与先前最先进的微调方法相竞争的水平。
>
> 具体而言，我们训练了GPT-3，其是一个自回归语言模型，具有1750亿参数，比之前的非稀疏语言模型多10倍，并在少样本情况下测试其性能。对于所有任务，GPT-3在没有任何梯度更新或微调的情况下应用，也就是任务和少量范例的情境，纯粹通过与模型的文本交互来指定。GPT-3在许多自然语言处理数据集上表现出色，包括翻译、问答和填空任务，以及一些需要即时推理或领域适应的任务，比如拼字、在句子中使用新词或进行3位数的算术运算。但是同时我们还发现了一些数据集，GPT-3的少样本学习仍然存在困难，以及一些GPT-3面临与在大型Web文集上训练相关的方法问题。最后我们发现GPT-3可以用来生成新闻文章样本，人类评估者很难将其与人写的文章区分。另外我们也讨论了这一发现和GPT-3整体对社会的更广泛影响。
>
> **链接论文**：https://arxiv.org/pdf/2005.14165.pdf
>
> **核心技术**：上下文学习
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIGNW4J4A0dBz7dkI19MbKQjcic9BrTvkX8KLCNPhvvWUwmkKkJFkJoibw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

11. AutoPrompt
--------------

> **论文名称**：《AutoPrompt: Eliciting Knowledge from Language Models with Automatically Generated Prompts》
>
> **发布时间**：2020/10/29
>
> **发布单位**：加州大学尔湾分校、加州大学柏克莱分校
>
> **简单摘要**：使用梯度搜寻自动产生prompt效果有时甚至比fine-tune好
>
> **阅读重点**：基于梯度的提示搜索、自动化标签标记选择
>
> **中文摘要**：预训练语言模型的卓越成功激励了对这些模型在预训练期间所学习的知识类型的研究。
>
> 将任务重新设定为填空问题（例如，完形填空测试）是评估此类知识的自然方法，但编写适合提示，仍受限于人工处理和猜测。
>
> 所以为了解决这个问题，我们开发了AutoPrompt，一种基于梯度引导搜索的自动方法，用于创建各种任务的提示。
>
> 使用AutoPrompt，我们展示了遮罩语言模型（MLMs）具有在没有额外参数或微调的情况下进行情感分析和自然语言推理的潜力，有时性能与最近最先进的监督式模型相当。我们还展示了我们的提示从MLMs中获得比LAMA基准测试上手动创建的提示更准确的事实知识，以及MLMs可以比监督式关系提取模型更有效地用作关系提取器。这些结果表明，自动生成的提示是现有探测方法的无参替代方案，随着预训练语言模型变得更加复杂和强大，这可能成为微调的替代方案。
>
> **链接论文**：https://arxiv.org/pdf/2010.15980.pdf
>
> **核心技术**：将AutoPrompt应用于探测掩码语言模型（MLM）进行情感分析的能力
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIEib12cvicvWgEzHTTPe7CeYAyk3pC12XCgmEVNGqdNWTS9R2ZkyqOp4Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

12. Rotary Position Embedding
-----------------------------

> **论文名称**：《RoFormer: Enhanced Transformer with Rotary Position Embedding》
>
> **发布时间**：2021/04/20
>
> **发布单位**：追一科技
>
> **简单摘要**：目前在LLM上最普遍使用的embedding方式
>
> **阅读重点**：旋转位置嵌入、长期衰减性质、线性自注意力
>
> **中文摘要**：这篇论文研究了位置编码在Transformer结构中的有效性。它能够为序列中不同位置的元素建立关联，提供有价值的监督。
>
> 我们首先探讨了将位置讯息整合到基于Transformer的语言模型学习过程中的各种方法。接着我们提出了一种新方法，名为Rotary Position Embedding（RoPE），以有效利用位置讯息。
>
> 具体而言，RoPE使用旋转矩阵编码绝对位置，同时在自注意力机制中结合了明确的相对位置依赖。值得注意的是，RoPE具有一些优势，包括序列长度的灵活性、随着相对距离增加而减弱的标注间依赖性，以及线性自注意力机制配备相对位置编码的能力。最后我们在多个长文本分类基准数据集上评估了使用Rotary Position Embedding的增强Transformer，也称为RoFormer。我们的实验显示它稳定地优于其他方法。此外我们提供了理论分析来解释一些实验结果。
>
> **链接论文**：https://arxiv.org/pdf/2104.09864.pdf
>
> **核心技术**：旋转位置嵌入（RoPE）
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIIfNuaBXTBP0ibO1h1ocAMvMicyoWx8pU4V3iaQCLVqhIBZgibKoaHpVC7A%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

13. LoRA
--------

> **论文名称**：《LoRA: Low-Rank Adaptation of Large Language Models》
>
> **发布时间**：2021/06/17
>
> **发布单位**：Microsoft
>
> **简单摘要**：Fine-tune不了整个LLM，那fine-tune一点点就好
>
> **阅读重点**：低秩自适应、推理延迟和适配器问题、LoRA 应用到 Transformer、实际好处和局限性
>
> **中文摘要**：这篇论文探讨了自然语言处理的重要范式，即在通用领域数据上进行大规模预训练，然后适应特定任务或领域。
>
> 随着我们预训练更大型的模型，重新调整全部模型参数（fine-tuning）的成本变得越来越高。例如使用GPT-3 175B，部署独立已微调好的模型实例成本过高。
>
> 所以我们提出了低秩适应（LoRA）的方法，冻结预训练模型权重，并将可训练的秩分解矩阵注入到Transformer架构的每一层中，大大减少下游任务所需的可训练参数数量。相较于使用Adam进行的GPT-3 175B的全模型重新调整，LoRA可将可训练参数数量减少10,000倍，GPU记忆体需求减少3倍。除了可训练参数更少、训练吞吐量更高，并且不像适配器那样存在额外的推理延迟，LoRA在RoBERTa、DeBERTa、GPT-2和GPT-3模型上，与全模型重新微调有相当或更优的结果。我们还对语言模型适应中的秩缺陷进行了实证研究，这有助于我们更好地理解LoRA的有效性。
>
> **链接论文**：https://arxiv.org/pdf/2106.09685.pdf
>
> **核心技术：**低秩适应（LoRA）
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaI2TAYleGzPeiaxoyIVdpQIBrbOWj93QcqayhaBQLH2FhMa5iaz4NiccgdQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

14. Codex
---------

> **论文名称**：《Evaluating Large Language Models Trained on Code》
>
> **发布时间**：2021/07/07
>
> **发布单位**：OpenAI
>
> **简单摘要**：会写程式的GPT
>
> **阅读重点**：HumanEval、unbiased estimator、code fine-tuning
>
> **中文摘要**：我们推出了Codex，这是一个在GitHub上公开可用的代码进行微调的GPT语言模型，并研究了它在Python代码编写方面的能力。
>
> Codex的特定生产版本为GitHub Copilot提供支持。另外我们发布了一个名为HumanEval的新评估数据集，用于测量从文档字符串合成程序的功能正确性。
>
> 在这个评估数据集中，我们的模型解决了28.8%的问题，而GPT-3解决了0%，GPT-J解决了11.4%。此外我们发现从模型中重复取样对于生成复杂提示的可行解决方案非常有效。使用这种方法，我们在每个问题中通过100次取样解决了70.2%的问题。仔细研究我们的模型显示了它的一些限制，包括难以处理描述一长串操作的文档字符串以及绑定操作到变量的困难。最后我们讨论了部署强大的代码生成技术可能带来的潜在广泛影响，涵盖了安全性、保密性和经济性。
>
> **论文链接**：https://arxiv.org/pdf/2107.03374.pdf
>
> **核心技术**：在GitHub上公开可用的代码进行微调的GPT语言模型
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIqiaia5fdvqsSFdVKCaHia1DCWP7V35qImibozQ5uyj8DnsEicictiaype9OLQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

15. FLAN
--------

> **论文名称**：Finetuned Language Models Are Zero-Shot Learners
>
> **发布时间**：2021/09/03
>
> **发布单位**：Google
>
> **简单摘要**：instruction-tuning让模型更了解你想干嘛
>
> **阅读重点**：instruction-tuning、task clusters、instruction templates
>
> **中文摘要**：这篇论文探讨了改善语言模型零样本学习能力的简单方法。
>
> 我们展示了指令微调的方法，即在语言模型上进行微调，使用一系列通过指令描述的任务，显著提高了对未知任务的零样本性能。
>
> 我们拿一个拥有137B参数的预训练语言模型，并在超过60个自然语言指令模板的帮助下，针对多个NLP任务进行微调。我们将这个经过指令微调的模型命名为FLAN，在未见过的任务类型上进行评估。
>
> FLAN大幅提升了其未修改版本的性能，并在我们评估的25个任务中，有20个超越了零样本175B GPT-3。FLAN 在 ANLI、RTE、BoolQ、AI2-ARC、OpenbookQA 和 StoryCloze 等任务上甚至大幅优于少样本的 GPT-3。消融研究显示，微调数据集的数量、模型规模和自然语言指令是指令微调成功的关键因素。
>
> **论文链接**：https://arxiv.org/pdf/2109.01652.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIlBeM1RWaFmCvUTfIXaHDCaK34iaIkjp8XMoXtFhEr2dJORpKHpJia3iag%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

16. GLaM
--------

> **论文名称**：《GLaM：Efficient Scaling of Language Models with Mixture-of-Experts》
>
> **发布时间**：2021/12/13
>
> **发布单位**：Google
>
> **简单摘要**：用MoE架构通过专家混合模型高效扩展语言模型，设计LLM准确率更高、训练速度更快
>
> **阅读重点**：gating module、MoE和dense models比较、数据质量影响、scaling studies
>
> **中文摘要**：我们在自然语言处理领域中，通过增加数据、计算和参数量，提升了语言模型的规模。
>
> 例如GPT-3在上下文学习任务上取得了出色的成果，这归功于模型规模的扩大。但是训练这些大型密集模型需要大量的计算资源。所以本文中我们提出并开发了一系列名为 GLaM（通用语言模型）的语言模型，采用了稀疏启动的混合专家架构来扩展模型容量，同时与密集变体相比，大幅降低了训练成本。
>
> 最大的GLaM模型拥有1.2万亿参数，大约是GPT-3的7倍大小。它的训练能耗只有GPT-3的三分之一，且推理时需要的计算量也减少了一半，同时在29个自然语言处理任务中实现了更好的零样本和单样本学习表现。
>
> **论文链接**：https://arxiv.org/pdf/2112.06905.pdf
>
> **核心技术**：GLaM 模型架构
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIphCCNQRamxzPakMSxsfmUAc96WUTXa2JtsKMNGozzgdrJEctAicAyuA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

17. WebGPT
----------

> **论文名称**：《WebGPT：Browser-assisted question-answering with human feedback》
>
> **发布时间**：2021/12/17
>
> **发布单位**：OpenAI
>
> **简单摘要**：可以上网查资料的GPT-3变得更强大
>
> **阅读重点**：environment design、资料demonstrations和comparisons、强化学习和reward modeling
>
> **中文摘要**：我们使用基于文本的网页浏览环境对 GPT-3 进行微调，让它可以回答长篇问题并搜索网页。
>
> 透过设置一个可以由人类执行的任务，我们可以使用模仿学习训练模型，并通过人类反馈来优化回答的质量。
>
> 为了让人类更容易对事实准确性进行评估，模型必须在浏览时收集相关参考来支持它们的答案。另外我们在 ELI5 数据集上训练和评估模型，该数据集包含 Reddit 用户提出的问题。我们最佳的模型是通过行为复制微调GPT-3后，使用拒绝采样与预测人类喜好的奖励模型进行比较得到的。对于这个模型，人类在56%的情况下更喜欢这个模型的答案，而在69%的情况下更喜欢Reddit上得票最高的答案。
>
> **论文链接**：https://arxiv.org/pdf/2112.09332.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIy3reBdtg6ITwp7cgxqdPibPoEoUnJttibVDn7DYibDlia4Z9ibviaDfrlBXw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

18. Chain-of-Thought（CoT）
-------------------------

> **论文名称**：《Chain-of-Thought Prompting Elicits Reasoning in Large Language Models》
>
> **发布时间**：2022/01/28
>
> **发布单位**：Google
>
> **简单摘要**：给答案要给详解，让LLM回答变得更有逻辑、更正确
>
> **阅读重点**：chain-of-Thought Prompting、讨论CoT有效原因
>
> **中文摘要**：我们探索了如何通过生成一系列中间推理步骤，即"思维链"，来显著提高大型语言模型执行复杂推理的能力。
>
> 特别是我们展示了在足够大的语言模型中，这种推理能力是如何通过一种称为"思维链提示"的简单方法自然产生的，该方法在提示中提供了一些思维链范例。
>
> 在三个大型语言模型上的实验表明，思维链提示提升了在一系列算术、常识和符号推理任务上的性能。实验效果惊人，例如对一个具有540亿参数的语言模型进行思维链提示，仅使用八个范例，在数学单词问题的GSM8K基准上达到了最先进的准确率，甚至超过了经过微调的GPT-3与一个验证器的表现。
>
> **论文链接**：https://arxiv.org/pdf/2201.11903.pdf
>
> **核心技术：**思维链
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaITv7Vcs6IucxSa9FibdD2kKAU2rsINH7bic61WEGQyljYgAmarUWXbSTw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

19. PaLM
--------

> **论文名称**：《PaLM: Scaling Language Modeling with Pathways》
>
> **发布时间**：2022/04/05
>
> **发布单位**：Google
>
> **简单摘要**：训练LLM的大型系统
>
> **阅读重点**：pathways system、discontinuous improvements
>
> **中文摘要**：大型语言模型已被证明能够在各种自然语言任务上取得卓越表现，使用了少样本学习（few-shot learning），显著减少了适应特定应用所需的特定训练样本数量。
>
> 为了进一步了解规模对少样本学习的影响，我们训练了一个名为 Pathways Language Model（PaLM）的 5400 亿参数的密集激励 Transformer 语言模型。
>
> 我们使用Pathways这个新的ML系统在6144个TPU v4芯片上进行了PaLM的训练，该系统能够实现跨多个TPU Pod的高效训练。我们也展示了通过规模扩展所带来的持续效益，PaLM 540B 在数百个语言理解和生成测试中实现了最新的少样本学习结果。在其中一些任务中，PaLM 540B 实现了突破性的性能，优于一系列多步推理任务的微调最新技术，并在最近发布的 BIG-bench 测试中超越了人类的平均表现。大量的 BIG-bench 任务显示模型规模的增大带来了不连续的改进，这意味着随着我们扩展到最大的模型，性能会急剧提高。我们也在各种测试中进行了展示，PaLM 在多语言任务和代码生成方面也具有强大的能力。此外我们还对偏见和恶意讯息进行了全面分析，并研究了模型规模对训练数据记忆的程度。最后我们讨论了与大型语言模型相关的道德考量，并探讨了潜在的缓解策略
>
> **论文链接**：https://arxiv.org/pdf/2204.02311.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIriaWgdjm3z5x3wJ5wMzAqQ6BDOaUL8IcBvXh50nlrSAB4mbBXAb1ibRQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

20. InstructGPT
---------------

> **论文名称**：《Training language models to follow instructions with human feedback》
>
> **发布时间**：2022/05/04
>
> **发布单位**：OpenAI
>
> **简单摘要**：ChatGPT的前身，让人类来教GPT-3社会化
>
> **阅读重点**：supervised policy、reward model训练、用PPO优化针对reward model的policy
>
> **中文摘要**：扩大语言模型的规模并不一定会使其更能理解用户的意图。
>
> 举例来说，大型语言模型可能产生不真实、恶意，或者对用户没有帮助的输出。换句话说，这些模型与其用户并不完全一致。
>
> 所以在这篇论文中，我们展示了一种通过人类反馈来对语言模型进行微调，从而使其在各种任务中与用户意图保持一致的方法。我们首先从一组由标注者编写的提示和通过OpenAI API提交的提示开始，收集了一组标注者展示所需模型行为的数据集，然后使用监督学习对GPT-3进行微调。接着我们收集了模型输出的排名数据集，进一步使用来自人类反馈的强化学习对这个监督模型进行微调。我们称最终生成的模型为 InstructGPT。
>
> 在我们的提示分发的人工评估中，尽管其参数数量少了100倍，拥有13亿参数的InstructGPT模型的输出优于175亿参数的GPT-3的输出。此外InstructGPT模型在真实性上有所提高，在减少恶意输出产生的同时，在公开NLP数据集上几乎没有性能退步。尽管InstructGPT仍然会犯一些简单的错误，但我们的结果显示，通过人类反馈进行微调是使语言模型与人类意图保持一致的一个有前景的方向。
>
> **论文链接**：https://arxiv.org/pdf/2203.02155.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIF2c1QEkVdHsxESuM3zWdd6YibIjicV03QpaPTicvYP6rDibW3auTkMB1xg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

21. Verify Step by Step
-----------------------

> **论文名称**：《Let's Verify Step by Step》
>
> **发布时间**：2022/05/31
>
> **发布单位**：OpenAI
>
> **简单摘要**：通过监督LLM的每一步，让LLM数学推理逻辑更强
>
> **阅读重点**：outcome-supervised reward models、process-supervised reward models、active learning用在PRM
>
> **中文摘要**：近年来大型语言模型在进行复杂的多步推理方面取得了很大进步。然而即使是最先进的模型仍然经常产生逻辑错误。
>
> 为了训练更可靠的模型，我们可以采用结果监督或过程监督。结果监督提供对最终结果的反馈，而过程监督则提供对每个中间推理步骤的反馈。
>
> 考虑到训练可靠模型的重要性，以及人类反馈的高成本，仔细比较这两种方法是很重要的。近期的研究已开始进行此比较，但仍有许多问题待解决。
>
> 我们进行了自己的调查，发现过程监督在训练模型解决来自具有挑战性的MATH数据集的问题时，显著优于结果监督。我们的过程监督模型能解决MATH测试集中代表性子集中78%的问题。此外我们展示了主动学习显著提高了过程监督的效果。为了支持相关研究，我们还释出了PRM800K数据集，其中包含了80万个步骤级别的人类反馈标签，用于训练我们最佳的奖励模型。
>
> **论文链接**：https://arxiv.org/pdf/2305.20050.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIGrcXOWXgiaNPkvCQqZibAyd90X9uEQNrL1KX7oIMHKf6WSb5MxjRfJaA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

22. LLM.int8()
--------------

> **论文名称**：《LLM.int8(): 8-bit Matrix Multiplication for Transformers at Scale》
>
> **发布时间**：2022/08/15
>
> **发布单位**：Facebook（Meta）、华盛顿大学、Hugging Face
>
> **简单摘要**：把float16/32精度的LLM转成int8，GPU就跑得动了
>
> **阅读重点**：8-bit quantization、matrix nultiplication、vector-wise quantization、mixed-precision decomposition
>
> **中文摘要**：大型语言模型被广泛采用，但推断过程需要大量GPU内存。
>
> 所以我们开发了一种Int8矩阵乘法程序，适用于transformer中的前馈和注意力投影层，将推断所需的内存减少了一半，同时保持完整的精确度表现。
>
> 透过我们的方法，可以加载175B参数的16/32位检查点，转换为Int8，并立即使用，而不会有性能下降。这是因为我们理解和处理了transformer语言模型中高度系统化的新特征，这些特征主导了注意力和预测性能。
>
> 为应对这些特征，我们开发了LLM.int8（）的两部分量化程序。首先我们使用矢量量化，为矩阵乘法中的每个内积使用单独的归一化常数，对大多数特征进行量化。然而对于新出现的极端值，我们还包括一种新的混合精度分解方案，将这些特异特征维度分离出一个16位矩阵乘法，而仍然有超过99.9%的值在8位中进行乘法。透过LLM.int8（），我们实证表明可以在具有175B参数的LLMs中进行推断，而不会有任何性能下降。这一结果使得这样的模型更加易于使用，例如在单个使用消费级GPU的服务器上使用OPT-175B/BLOOM。
>
> **论文链接**：https://arxiv.org/pdf/2208.07339.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIATvBTkWOrVicmiawVfT8mR1AghJoUf0yAfY11YkichkuMVMb3C7fQw0HA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

23. ReAct
---------

> **论文名称**：《ReAct: Synergizing Reasoning and Acting in Language Models》
>
> **发布时间**：2022/10/06
>
> **发布单位**：Google、普林斯顿大学
>
> **简单摘要**：结合思维链提示和行动计划生成，防止LLM胡言乱语
>
> **阅读重点**：Synergizing Reasoning、Acting、knowledge-intensive reasoning tasks
>
> **中文摘要**：大型语言模型（LLMs）在语言理解和互动决策方面展现了令人印象深刻的能力，但它们的推理能力（例如思维链提示）和行动能力（例如行动计划生成）主要是作为独立的主题来研究的。
>
> 所以本文探讨了LLMs以交叉方式生成推理跟踪和特定任务的行动，让两者之间更协同：推理跟踪帮助模型诱导、追踪、更新行动计划并处理异常情况，而行动则允许它与知识库或环境等外部来源互动，收集额外讯息。
>
> 我们的方法名为ReAct，在多种语言和决策任务上展示了比最先进基准更有效的效果，同时相较于没有推理或移动元件的方法，具有更好的人类可解释性和可信度。
>
> 具体来说在问答（HotpotQA）和事实验证（Fever）方面，ReAct通过与简单的维基百科API互动，克服了思维链推理中出现的幻觉和错误传播问题，生成了更具可解释性的人类化任务解决轨迹，优于没有推理跟踪的基准。在两个交互式决策基准（ALFWorld和WebShop）上，即使只提示了一两个上下文示例，ReAct的成功率分别比模仿学习和强化学习方法提高了34%和10%。
>
> **论文链接**：https://arxiv.org/pdf/2210.03629.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIoV2dgXFhY9j0YMsbdqKxXHnuxYT2F9yEI5iaz4Ux2BUE5O86guN5IaA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

24. Toolformer
--------------

> **论文名称**：《Toolformer: Language Models Can Teach Themselves to Use Tools》
>
> **发布时间**：2023/02/09
>
> **发布单位**：Facebook（Meta）、庞培法布拉大学
>
> **简单摘要**：会使用外部工具的LLM
>
> **阅读重点**：sampling API calls、executing API calls、filtering API calls、annotation with self-supervised learning
>
> **中文摘要**：这份研究探讨语言模型（LMs）在解决新任务时展现出的惊人能力，仅需少量范例或文本指令即可，并尤其在大规模下表现卓越。
>
> 然而相反地，它们在基本功能上表现出困难，例如算术或事实查询，这些功能在更简单、更小型的模型中表现出色。
>
> 所以在这篇论文中，我们展示了语言模型可以通过简单的API，自我学习使用外部工具，实现两者之间的最佳结合。
>
> 我们引入了Toolformer，这是一个训练过的模型，能够决定调用哪些API、何时调用它们、传递什么参数，以及如何最佳地将结果整合到未来的标记预测中。这是通过自我监督的方式完成的，每个API仅需少量范例即可。我们包含了一系列工具，包括计算机、问答系统、两种不同的搜索引擎、翻译系统和日历。Toolformer在各种下游任务中取得了显著提升的零样本性能，通常与更大的模型竞争力相当，同时也不损害其核心语言模型能力。
>
> **论文链接**：https://arxiv.org/pdf/2302.04761.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIHrv1dWg8SsESiam4qW40C6Vx0SBgEIMCpWtjibgECexMfeTImaB6chpA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

25. LLaMA
---------

> **论文名称**：《LLaMA: Open and Efficient Foundation Language Models》
>
> **发布时间**：2023/02/27
>
> **发布单位**：Facebook（Meta）
>
> **简单摘要**：最有名的开源LLM第一代
>
> **阅读重点**：pre-training data、architecture、efficient implementation
>
> **中文摘要**：我们推出了LLaMA，这是一系列参数从7B到65B的基础语言模型。
>
> 我们使用公开可用的数据集训练这些模型，并展示了可以在仅使用公开数据集的情况下训练出最先进的模型，无需使用专有或无法取得的数据集。
>
> 特别是LLaMA-13B在大多数基准测试中优于GPT-3（175B），而LLaMA-65B与最佳模型Chinchilla-70B和PaLM-540B竞争力相当。我们将所有模型释出给研究社区使用。
>
> **论文链接**：https://arxiv.org/pdf/2302.13971.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIAAv6nfolw7vv1bhNuRU9yVxmBKBHuBrUxY9icdWuzicnCMbMO9hlkIPQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

26. GPT-4
---------

> **论文名称**：《GPT-4 Technical Report》
>
> **发布时间**：2023/05/15
>
> **发布单位**：OpenAI
>
> **简单摘要**：目前世界上最强的LLM
>
> **简单摘要**：目前世界上最强的LLM
>
> **中文摘要**：我们开发了GPT-4，这是一个大规模、多模态模型，能够接受图像和文字输入并生成文字输出。
>
> 虽然在许多现实情境中比不上人类的能力，但在各种专业和学术基准测试中，GPT-4表现出与人类相当的水平，包括在模拟的律师考试中取得了排名前10%左右的成绩。
>
> GPT-4是一个基于Transformer的模型，预先训练来预测文件中的下一个标记。后训练对齐流程改进了模型的事实性和符合期望行为的表现。这个项目的核心部分是开发了在各种规模下都表现稳定的基础设施和优化方法。这使我们能够根据使用不到GPT-4 1/1,000的计算资源所训练的模型，准确预测GPT-4的某些性能方面。
>
> **论文链接**：https://arxiv.org/pdf/2303.08774.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIQMCJAic08qqgvQ8Jnbg7STRUkh35zhicibl6lsUkXKoQicBZ9yvDt3IAGw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

27. QLoRA
---------

> **论文名称**：《QLoRA: Efficient Finetuning of Quantized LLMs》
>
> **发布时间**：2023/05/23
>
> **发布单位**：华盛顿大学
>
> **简单摘要**：quantization+Lora让我一张显卡就可fine-tune LLM
>
> **阅读重点**：4-bit NormalFloat、double quantization、paged optimizers
>
> **中文摘要**：我们提出了QLoRA，一种有效的微调方法，可以减少内存使用量，让一个65B参数的模型在一个48GB的GPU上进行微调，同时保持完整的16位微调任务性能。
>
> QLoRA通过一种称为Low Rank Adapters（LoRA）的方法，将梯度反向传播到冻结的4位量化预训练语言模型。我们最佳的模型家族名为Guanaco，在Vicuna基准测试中表现优于以往所有公开发布的模型，并仅需在单个GPU上进行24小时的微调即可达到ChatGPT 99.3%的性能水平。
>
> QLoRA引入了几项创新，以节省内存而不影响性能：（a）4位NormalFloat（NF4），这是一种对于正常分布权重的训息理论最优的新数据类型; （b）双重量化，通过量化量化常数来减少平均内存占用; （c）标签优化器，管理内存峰值。我们使用QLoRA对1000多个模型进行微调，提供了对8个指令数据集、多种模型类型（LLaMA、T5）以及使用常规微调不可行的模型规模（例如33B和65B参数模型）的指令遵从和聊天机器人性能的详细分析。我们的结果表明，QLoRA在一个小而高质量的数据集上进行微调，即使使用的模型比以前的模型更小，可以达到最新技术水平的性能。除此之外我们提供了基于人类和GPT-4评估的聊天机器人性能的详细分析，并显示GPT-4评估是一种便宜且合理的替代方法。此外我们发现当前的聊天机器人基准测试不能准确评估聊天机器人的性能水平。通过某些方面的分析，我们展示了Guanaco相对于ChatGPT的不足之处。最后我们释出了所有模型和代码，包括4位训练的CUDA核心。
>
> **论文链接**：https://arxiv.org/pdf/2305.14314.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIgrPBN39km5bfBIHlhWM47tfcvcSg7Yp16IhnupvGtusZibaNvD9TWUQ%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

28. Phi-1
---------

> **论文名称**：《Textbooks Are All You Need》
>
> **发布时间**：2023/06/20
>
> **发布单位**：Microsoft
>
> **简单摘要**：高品质的小数据胜过大数据和大模型
>
> **阅读重点** ：importance of high-quality data、用transformer过滤datasets、synthetic textbook-quality datasets、data pruning**中文摘要**：我们推出了 phi-1，一款针对代码的新型大型语言模型，规模远小于竞争对手的模型：phi-1是一个基于 Transformer 的模型，拥有 13 亿参数，在 8 个 A100 GPU 上训练了 4 天，使用了来自网络"教科书级别"的数据（60亿标记）和使用 GPT-3.5 合成生成的教科书和练习题（10亿标记）。
>
> 尽管规模小，phi-1 在 HumanEval 上达到了 50.6% 的 pass@1 准确率，以及 MBPP 上的 55.5%。与 phi-1-base 相比（我们在编程练习数据集上进行微调之前的模型），phi-1 也展现了令人惊讶的新特性，以及与 phi-1-small（另一个具有 3.5 亿参数的较小模型）相比的性能，后者在 HumanEval 上仍然达到了 45%。
>
> **论文链接**：https://arxiv.org/pdf/2306.11644.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaICJI2L2ll5ic046v0icOPvoXJIDicTjlIjZkEIOcs8eOh3Nkz4DK5YRiccw%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

29. RLAIF
---------

> **论文名称**：《RLAIF: Scaling Reinforcement Learning from Human Feedback with AI Feedback》
>
> **发布时间**：2023/08/24
>
> **发布单位**：Google
>
> **简单摘要**：让社会化的LLM来社会化LLM
>
> **阅读重点**：reference labeling with LLMs、addressing position bias、distilled RLAIF、direct RLAIF、evaluation
>
> **中文摘要**：强化学习从人类反馈中学习（RLHF）已被证明能有效让大型语言模型（LLMs）与人类偏好保持一致。
>
> 然而收集高质量的人类偏好标签可能耗时且昂贵。前人所提出的AI反馈强化学习（RLAIF）提供了一种有希望的替代方案，它利用强大的现成LLM来生成偏好，取代了人类标注者。
>
> 在摘要、有帮助的对话生成和无害对话生成等任务中，RLAIF获得了与RLHF相当或更优的表现。此外在另一个实验中，直接向LLM提供奖励分数的提示方法，即使LLM偏好标注生成器与策略大小相同，也能比典型的RLAIF设置获得更好的表现。最后我们对生成符合AI偏好的技术进行了广泛研究。我们的结果表明，RLAIF能达到人类水平的性能，为克服RLHF的扩展性限制提供了潜在解决方案。
>
> **论文链接**：https://arxiv.org/pdf/2309.00267.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIVXBc5CJvvrMtfIqdsINfs8Siayu7KdaDylWzShpIzdhg8REq24wvROA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

30. Superalignment
------------------

> **论文名称**：《Weak-to-Strong Generalization: Eliciting Strong Capabilities with Weak Supervision》
>
> **发布时间**：2023/12/14
>
> **发布单位**：OpenAI
>
> **简单摘要**：要人类能监督超级AI，先从小LLM监督大LLM开始
>
> **中文摘要**：广泛使用的对齐技术，比如从人类反馈中进行强化学习（RLHF），依赖于人类监督模型行为的能力，例如评估模型是否忠实地遵从指令或生成安全的输出。
>
> 但是未来的超级人工智能模型将表现出复杂的行为，对人类来说难以可靠地评估，对于人类对超级人工智能模型进行弱监督，我们研究了这个问题的类比：弱模型监督是否能唤起更强大模型的全部能力？
>
> 我们在自然语言处理、西洋棋和奖励建模任务上使用了一系列GPT-4系列的预训练语言模型进行测试。
>
> 我们发现，当我们用弱模型生成的标注来简单微调强大的预训练模型时，它们的表现一直优于弱监督模型，我们称之为弱到强泛化现象。然而仅仅通过简单微调，我们仍然离完全发挥强大模型的能力很远，这表明像RLHF这样的技术在不进一步研究的情况下可能无法应对超级人工智能模型的挑战。我们发现简单的方法通常能显著提高弱到强泛化能力：例如当用GPT-2级别的监督模型和辅助的置信损失来微调GPT-4时，我们在NLP任务上可以接近GPT-3.5的性能水平。我们的结果表明，当前在解决对齐超级人工智能模型方面是有可能取得实际进展的。
>
> **论文链接**：https://cdn.openai.com/papers/weak-to-strong-generalization.pdf
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIPK6JecZm8jWsvOsaVW3fJD1qXyZz5amrJdibCibmJ8dfhYZWHsFH0vhA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

31. graphRAG
------------

> **论文名称**：《From Local to Global: A Graph RAG Approach to Query-Focused Summarization》
>
> **发布时间**：2024/04
>
> **发布单位**：Microsoft
>
> **简单摘要**：面向查询的知识图谱检索增强
>
> **中文摘要**：使用检索增强生成（RAG）从外部知识源检索相关信息，使大型语言模型（LLM）能够回答关于私人和/或以前看不到的文档集合的问题。
>
> 然而，RAG在针对整个文本语料库的全局问题上失败了，例如"数据集中的主要主题是什么？"，因为这本质上是一个以查询为重点的总结（QFS）任务，而不是一个明确的检索任务。与此同时，以前的QFS方法未能扩展到典型的RAG系统索引的文本数量。
>
> 为了结合这些对比方法的优势，我们提出了一种图形RAG方法，在私人文本语料库上回答问题，该方法可根据用户问题的一般性和要索引的源文本的数量进行缩放。
>
> 我们的方法使用LLM分两个阶段构建基于图形的文本索引：首先从源文档中导出实体知识图形，然后为所有密切相关的实体组预先生成社区摘要。给定一个问题，每个社区摘要都用于生成部分响应，然后将所有部分响应再次汇总到对用户的最终响应中。对于一类关于100万令牌范围内数据集的全球意义问题，我们表明，Graph RAG在生成答案的全面性和多样性方面比天真的RAG基线有了实质性改进。
>
> **论文链接**：https://arxiv.org/pdf/2404.16130
>
> ![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRsvL4lJF8rwdYPBuIm7giaIryTTjDcgibNotwKZXfVicS5DHFGDEPDpiahWe0qUMMNpbMn0TJrWdYOzA%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

以上，点亮【`赞`与`在看`】**让我们心中充满力量、披荆斩棘。**

**推荐阅读**

[讲清 Transformer 模型架构论文（一）](http://mp.weixin.qq.com/s?__biz=MzkyMzYyNjQxOQ==&mid=2247484263&idx=1&sn=37821df657d05674ba0a6cc2abf1b8d3&chksm=c1e37dbbf694f4ad65c20c4e16e12d52ffda412c5e02ebf214489ebdb43fa13600e6dd923ddc&scene=21#wechat_redirect)  

[讲清 Transformer 模型架构论文（二）](http://mp.weixin.qq.com/s?__biz=MzkyMzYyNjQxOQ==&mid=2247484268&idx=1&sn=62696c624c63386228c43f45fdd6e4bc&chksm=c1e37db0f694f4a61fd7fcf6835535c06ec226c5e8286d3d5eb5a160ae931ef251702a677e3a&scene=21#wechat_redirect)  

[讲清 Transformer 模型架构论文（三）](http://mp.weixin.qq.com/s?__biz=MzkyMzYyNjQxOQ==&mid=2247484275&idx=1&sn=fdfb26405964ff708d5d696a81bacfe9&chksm=c1e37daff694f4b9c89936565c7eb497c661cc86905cf37c63c7ea58edfb07e6105fd97b2429&scene=21#wechat_redirect)  

[讲清 Transformer 模型架构论文（四）](http://mp.weixin.qq.com/s?__biz=MzkyMzYyNjQxOQ==&mid=2247484298&idx=1&sn=d638818dab71ce80a5e9426a0393cfc9&chksm=c1e37d56f694f440291b7cf5f233cfebea0696f76d838d28fb6854f2e40150c4411e9bf2a76b&scene=21#wechat_redirect)

[认识大模型Embedding技术，加代码实战](http://mp.weixin.qq.com/s?__biz=MzkyMzYyNjQxOQ==&mid=2247485082&idx=1&sn=b57589e1f0eb32c7f68b7ab3b29fa2f0&chksm=c1e37846f694f150a1942f298107cc548e6ceee285e206642b9556ce0de5396ab868b0d755be&scene=21#wechat_redirect)  

![](https://image.cubox.pro/cardImg/387c1b7yzc5bmdbva1wbjjrsmbpsxi72chlch1urdi91ruw4w3?imageMogr2/quality/90/ignore-error/1)

**皇子谈技术**

一个纯粹的技术人，关注我，一起成长

99篇原创内容

公众号

，

**关于作者**：一位热爱技术，并在职场与自媒体间探索的实践者，希望通过分享个人经验和见解，帮助更多人实现自我成长和价值。

如果您对我的公众号内容感兴趣，欢迎关注我。

也可以在下方添加我微信和一支烟花AI社区技术群，一起交流技术、职场心得。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FgUG9rZB5YvRiau2cIKnEQicMVCNxUwibHe4iasJQkMicBT6tLmqpUhndDYuIoa5UlDpjIQfUMy66ic85ibZf7AY4cLYGw%2F640%3Fwx_fmt%3Dother%26from%3Dappmsg%26wxfrom%3D5%26wx_lazy%3D1%26wx_co%3D1%26tp%3Dwebp) 图片

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7218935374645561105)
