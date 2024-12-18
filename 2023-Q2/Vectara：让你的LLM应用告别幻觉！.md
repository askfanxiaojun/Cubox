Vectara：让你的LLM应用告别幻觉！
=====================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/626544154)博而不士博览AI的奥秘，博学AI的知识，博交AI的朋友

LLM的幻觉

你是否曾经遇到过这样的情况：你想用一个智能的LLM（大型语言模型）来帮你生成一些文本，比如一个对话、一个答案、一个摘要等，但是你得到的结果却让你大失所望？它可能跟你给的输入或源内容完全不搭边，或者根本就是胡说八道。这就是LLM幻觉，它会让你的LLM应用变得不可靠、不可信，甚至可能有害。那么，有没有办法可以避免或减少LLM幻觉，让你的LLM应用变得更有意义、更忠实、更好玩呢？答案是肯定的，而且还很简单，只要用Vectara平台就行了！
![](https://image.cubox.pro/article/2023050610170488315/14722.jpg?imageMogr2/quality/90/ignore-error/1)

首先，让我们来了解一下什么是LLM幻觉。LLM幻觉是指LLM生成的内容与给定的输入或源内容不一致，或者完全没有意义。这种现象会严重影响LLM应用的可靠性和可信度，甚至可能造成误导或危害。例如，当你问一个LLM"谁拥有硅谷银行？"时，它可能会回答："硅谷银行（SVB）不是由单一的个人或实体拥有的。它是SVB金融集团的子公司，SVB金融集团是一家上市公司（纳斯达克：SIVB）。SVB金融集团的所有权分散在拥有其股票的个人和机构股东之间。作为一家上市公司，其所有权会随着股票市场上的买卖而频繁变化。"听起来很专业，对吧？但实际上，这是一个错误的答案，因为硅谷银行已经于2022年12月宣布破产了。如果你相信了这个答案，你可能会做出一些错误的决定或行动。

那么，为什么LLM会产生幻觉呢？主要原因是LLM的训练数据集有限、过时或矛盾。由于LLM通常使用大量但不全面的文本数据进行训练，它们无法覆盖所有可能的输入或问题，也无法及时更新数据中发生的变化或事件。此外，由于数据中可能存在不一致或错误的信息，LLM也无法区分真假或优劣。这些因素导致LLM在理解和回答用户问题时，往往依赖于自己学习到的统计规律或模式，而不是基于事实或逻辑。因此，当用户提出一些超出LLM知识范围或与数据不符合的问题时，LLM就可能产生错误或无意义的回答。

那么，如何解决LLM幻觉呢？目前常用的方法有以下几种：

* 人工审核：这种方法是在LLM生成内容后，由人工进行审核和修改，以确保内容的正确性和合理性。这种方法的优点是可以有效地避免或纠正幻觉，提高内容质量；缺点是需要耗费大量的人力和时间成本，而且可能存在人为的错误或偏见。
* 数据过滤：这种方法是在LLM生成内容前，对输入或源内容进行过滤和清洗，以去除不相关、不准确或不一致的信息。这种方法的优点是可以减少幻觉的可能性，提高内容的相关性和一致性；缺点是需要耗费大量的计算资源和算法技巧，而且可能存在数据丢失或过度简化的风险。
* 知识图谱：这种方法是在LLM生成内容时，利用一个结构化的知识库（知识图谱）来提供事实信息和逻辑推理，以增强LLM的理解和回答能力。这种方法的优点是可以提高内容的有意义性和忠实性，提供更丰富和更深入的信息；缺点是需要构建和维护一个大规模且高质量的知识图谱，而且可能存在知识图谱不完备或不更新的问题。

这些方法各有利弊，但都不能完全解决LLM幻觉的问题。那么，有没有一种更好的方法呢？Vectara平台也许就是答案。

Vectara平台
---------

Vectara是一个专注于对话体验的平台，它提供了强大的检索、摘要和生成功能，以及简单易用的开发者接口。Vectara平台使用了一种叫做基于事实的生成（Grounded Generation）的方法，在生成文本之前和之后都进行事实检索和验证，确保生成内容是有意义且忠实于源内容的。具体来说，基于事实的生成方法包括以下几个步骤：
![](https://image.cubox.pro/article/2023050610170585644/97769.jpg?imageMogr2/quality/90/ignore-error/1)

* 输入：给定一个文本或语音输入，例如一个问题、一个指令、一个话题等。
* 检索：根据输入，在互联网或其他数据源中检索相关的事实信息，例如网页、文章、数据库等。
* 验证：根据检索到的事实信息，对输入进行验证，判断其是否合理、准确、完整等。如果输入不符合要求，可以提出修改或补充的建议。
* 生成：根据验证后的输入和检索到的事实信息，使用LLM生成相应的文本或语音输出。
* 验证：根据检索到的事实信息，对生成的输出进行验证，判断其是否有意义、忠实、一致等。如果输出不符合要求，可以进行修改或重写。

通过这样一个循环的过程，基于事实的生成方法可以有效地避免或减少LLM幻觉，提高LLM生成内容的质量和可信度。

Vectara平台具有以下特点：

* 基于事实：Vectara平台在生成文本之前和之后，都会在互联网或其他数据源中检索相关的事实信息，并对输入和输出进行验证，以确保内容是正确、合理、完整、一致的。这样，你就不用担心你的LLM会产生幻觉，或者给你一些错误或无意义的回答。
* 对话式：Vectara平台支持多轮对话，可以根据用户输入和上下文动态地调整生成内容和风格，提供更自然、更流畅、更人性化的对话体验。例如，当你问一个LLM"谁拥有硅谷银行？"时，Vectara平台不仅会给你一个正确且及时的回答："根据最新的网页信息，硅谷银行（SVB）已经于2022年12月宣布破产。它目前正处于清算阶段，其资产和债务由美国联邦存款保险公司（FDIC）管理。"而且还会根据你的反应和兴趣，给你一些相关或有趣的信息或建议。例如，"你是否对硅谷银行破产的原因感兴趣？我可以给你一些网页链接。"或者"你是否想知道硅谷银行破产对科技行业有什么影响？我可以给你一些数据分析。"
* 开发者友好：Vectara平台提供了简单易用的开发者接口，可以让开发者快速地集成和部署基于事实的生成应用，无需复杂的配置或代码。Vectara平台支持多种数据源和LLM，可以根据不同的应用场景和任务，选择最合适的数据源和LLM，以提供最优的生成效果。Vectara平台还允许开发者根据自己的需求和偏好，定制生成内容的参数和选项，例如长度、语言、领域、风格等。
* 可扩展：Vectara平台不仅可以用于文本生成，还可以用于语音生成。Vectara平台可以将文本转换为语音，或者将语音转换为文本，以满足不同的用户需求和偏好。Vectara平台还可以将文本或语音翻译成不同的语言，以支持跨语言的对话体验。

Vectara平台是一个基于事实的生成方法的平台，它为开发者提供了一个方便、高效、可靠的平台，来构建高质量的LLM驱动的应用。

LLM是一种强大的技术，它可以在各种NLP任务中产生令人惊叹的结果。但正是因为它的强大，也使得LLM的"幻觉"问题更具有危害性。"幻觉"不仅会影响LLM的性能和可信度，还可能会对用户和社会造成负面的影响。Vectara平台一个有前景的方法，它是一个集成的环境，可以让用户创建、测试和部署基于LLM的应用程序，并提供了一些工具和指导来帮助用户避免幻觉。我们希望，通过探索不同的方法，我们可以开发出更可靠和更有用的基于LLM的应用程序，从而为人类带来更多的价值和便利。如果您想了解更多关于Vectara平台的信息，请访问[https://vectara.com/](https://link.zhihu.com/?target=https%3A//vectara.com/)。

吴恩达提示工程教程:[https://mp.weixin.qq.com/s?__biz=MzkwMjQ5MzExMg==\&mid=2247483714\&idx=1\&sn=5e905f5ec6196f6dc2187db2a8618f02\&chksm=c0a5e795f7d26e831292e3e5d468e8287696425d420bb81965a50dcff89986fb435e54dc98d1#rd](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s%3F__biz%3DMzkwMjQ5MzExMg%3D%3D%26mid%3D2247483714%26idx%3D1%26sn%3D5e905f5ec6196f6dc2187db2a8618f02%26chksm%3Dc0a5e795f7d26e831292e3e5d468e8287696425d420bb81965a50dcff89986fb435e54dc98d1%23rd)

没有魔法，无法访问却想体验ChatGPT的朋友，可以尝试：[https://mp.weixin.qq.com/s?__biz=MzkwMjQ5MzExMg==\&mid=2247483733\&idx=4\&sn=187c2bb8981c8de4628ee1275632cd53\&chksm=c0a5e782f7d26e940099ce730332f5665134001033fcf1956253682630d3c0cb973e2c0ef5f3#rd](https://link.zhihu.com/?target=https%3A//mp.weixin.qq.com/s%3F__biz%3DMzkwMjQ5MzExMg%3D%3D%26mid%3D2247483733%26idx%3D4%26sn%3D187c2bb8981c8de4628ee1275632cd53%26chksm%3Dc0a5e782f7d26e940099ce730332f5665134001033fcf1956253682630d3c0cb973e2c0ef5f3%23rd)

原创性承诺：G3（内容由人工列出提纲，AI对提纲进行扩充内容完成文章）

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7054348329257274638)
