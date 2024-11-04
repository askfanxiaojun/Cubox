大模型驱动的自主代理（LLM Powered Autonomous Agents）
=========================================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/639964649)storm

[本文](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-06-23-agent/)作者是来自OpenAI的 Lilian Weng，详细分析了如何使用LLM构建AI Agents；而Andrej Karpathy也在最近的一次分享中提到OpenAI内部对AI Agents的[看法](https://zhuanlan.zhihu.com/p/639838929)。值得一提的是，在Lilian的 [Blog](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/) 中还有其他非常好的文章，涉及[强化学习](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2018-02-19-rl-overview/)、生成模型（[VAE](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2018-08-12-vae/)、[Diffusion models](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2021-07-11-diffusion-models/)）、[Transformer](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-01-27-the-transformer-family-v2/) 和 LLM 等领域，值得花时间仔细阅读～

我正在调研有关LLM+RL的工作，这里对文章进行了翻译，并加入了一些自己的理解，欢迎讨论指正！*（知乎编辑器真的难用，以后记录准备都用图片了）*

*** ** * ** ***

以LLM（大语言模型）作为代理的核心控制器是一个很酷的概念。一些概念验证（proof-of-concepts，PoC）的演示，例如[AutoGPT](https://link.zhihu.com/?target=https%3A//github.com/Significant-Gravitas/Auto-GPT)，[GPT-Engineer](https://link.zhihu.com/?target=https%3A//github.com/AntonOsika/gpt-engineer) 和 [BabAGI](https://link.zhihu.com/?target=https%3A//github.com/yoheinakajima/babyagi) 都是令人振奋的例子。但LLM的潜力不仅限于生成写作流畅的副本、故事、论文和程序，它还可以被视为一个强大的**通用问题解决器**。

代理系统概述
------

在一个由LLM驱动的自主代理系统中，LLM充当代理的大脑，并辅以几个关键组成部分：

* **规划（Planning）**
  * 子目标与分解（Subgoal and decomposition）：代理将大型任务分解为更小、更易于处理的子目标，从而实现对复杂任务的高效处理。
* **反思与完善（Reflection and refinement）**：代理可以对过去的行动进行自我批评和自我反思，从错误中吸取教训，并为未来的步骤进行改进，从而提高最终结果的质量。
* **记忆（Memory）**
  * 短期记忆（Short-term memory）：作者认为所有上下文学习（参考另一篇文章 [提示工程Prompt Engineering](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-03-15-prompt-engineering/)）都是利用模型的短期记忆来学习。
  * 长期记忆（Long-term memory）：这为代理提供了在长时间嘞保留和回忆（无限）信息的能力，通常通过利用外部向量存储和快速检索来实现。
* **工具的使用（Tool use）**
  * 代理程序学会调用外部API获取模型权重中缺失的额外信息（通常在预训练后很难更改），包括当前信息、代码执行能力、访问专有信息源等。

![](https://image.cubox.pro/article/2023080214182331643/32677.jpg?imageMogr2/quality/90/ignore-error/1)
图1：大模型与自主代理系统的结合概览

下面分别对这几个关键组成部分进行阐述：

组件一：规划
------

一个复杂的任务通常涉及许多步骤。代理人需要知道这些步骤并提前进行规划。

### 任务分解（Task Decomposition）

**思维链** （[Chain of thought](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-03-15-prompt-engineering/%23chain-of-thought-cot)，CoT； [Wei et al. 2022](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2201.11903)）已成为提高模型在复杂任务上性能的标准提示（prompt）技术。该模型被指示需要进行"逐步思考"，从而利用更多的测试时间计算将困难任务分解为更小、更简单的步骤。思维链将大任务转化为多个可处理的任务，并对模型思考过程进行了解释。

**思想树** （Tree of Thoughts；[Yao et al. 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2305.10601)）通过在每个步骤中探索多种推理可能性来扩展思维链。它首先将问题分解为多个思考步骤，并在每个步骤中生成多个思考，从而形成一个树状结构。搜索过程可以是广度优先搜索（BFS）或深度优先搜索（DFS），每个状态都通过分类器（通过提示）或多数投票进行评估。

任务分解可以通过以下方式进行：（1）使用简单的提示，例如 `"Steps for XYZ.\n1."` ， `"What are the subgoals for achieving XYZ?"` ，（2）使用特定任务的指令，例如用 `"Write a story outline."` 来写小说，或者（3）通过人工输入。

另一种非常独特的方法是**LLM+P** （[Liu et al. 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2304.11477)），它依赖于外部的经典规划器来进行长期规划。这种方法利用规划领域定义语言（Planning Domain Definition Language，PDDL）作为中间接口来描述规划问题。在这个过程中，LLM首先（1）将问题转化为"问题PDDL（Problem PDDL）"，然后（2）请求经典规划器基于现有的"领域PDDL（Domain PDDL）"生成一个PDDL规划，最后（3）将PDDL规划转化回自然语言。实质上，我们假设领域特定的PDDL和相应的规划器是可用的，则规划步骤能够利用外部工具完成，这在某些机器人设置中很常见，但在许多其他领域中并不常见。

### 自我反思（Self-Reflection）

自我反思是一个至关重要的方面，它使得自主代理能够通过改进过去的行动决策和纠正以前的错误来不断提高自身。在现实世界的任务中，试错（trial and error）是不可避免的，自我反思在其中起着至关重要的作用。

**ReAct** （[Yao et al. 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2210.03629)）通过将动作空间扩展为任务特定的离散动作和语言空间的组合，将推理和行动融合到LLM中。前者（任务特定的离散动作）使LLM能够与环境进行交互（例如使用维基百科搜索API），而后者（语言空间）则促使LLM生成自然语言的推理轨迹。

ReAct提示模板包含了明确的LLM思考步骤，大致格式如下：

    Thought: ...
    Action: ...
    Observation: ...
    ... (Repeated many times)

![](https://image.cubox.pro/article/2023080214182399540/30651.jpg?imageMogr2/quality/90/ignore-error/1)
图2：知识密集型任务（例如HotpotQA、FEVER）和决策任务（例如AlfWorld Env、WebShop）的推理轨迹示例（图片来源： Yao et al. 2023）

在对知识密集型任务和决策任务进行的两个实验中， `ReAct` 的表现优于仅使用 `Act` 的基准模型（`Act` 模型中省略了 `Thought: ...` 步骤）。

**Reflexion** （[Shinn \& Labash 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2303.11366)）是一个框架，为代理提供动态记忆和自我反思能力，以提高推理能力。Reflexion采用标准的强化学习设置，其中奖励模型提供简单的二元奖励（0/1），行动空间遵循ReAct的设置，其中任务特定的动作空间通过语言扩展以实现复杂的推理步骤。在每个动作 <math xmlns="http://www.w3.org/1998/Math/MathML"> a t </math>a_t 之后，代理计算一个启发式的 <math xmlns="http://www.w3.org/1998/Math/MathML"> h t </math>h_t ，并根据自我反思的结果选择性地决定重置环境以开始新的试验。
![](https://image.cubox.pro/article/2023080214182396047/15051.jpg?imageMogr2/quality/90/ignore-error/1)
图3. Reflexion框架的示意图。（图片来源：Shinn \& Labash, 2023）

启发式函数决定了轨迹是否是低效的或者包含幻觉（hallucination），这时需要停止。低效的规划是指花费过长时间而没有成功的轨迹；幻觉是指遇到一系列连续相同的动作，导致环境中出现相同的观察。

通过向LLM展示two-shot*（不知道怎么翻译，成对？）* 的示例，可以创建自我反思。每个示例都是一对（**失败轨迹** ，用于指导未来计划变化的**理想反思**）。然后将这些反思添加到代理的工作记忆（短期记忆）中，最多三个，以作为查询LLM的上下文。
![](https://image.cubox.pro/article/2023080214182394312/28623.jpg?imageMogr2/quality/90/ignore-error/1)
图4. 在AlfWorld环境和HotpotQA上的实验。在AlfWorld中，幻觉现象比低效规划更常见。（图片来源： Shinn \& Labash, 2023）

**Chain of Hindsight** （CoH； [Liu et al. 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2302.02676)）通过带有反馈标记的历史输出序列，来鼓励模型不断改进。人类反馈（Human feedback）数据是一组 <math xmlns="http://www.w3.org/1998/Math/MathML"> D h = { ( x , y i , r i , z i ) } i = 1 n </math>D_h = \\{(x, y_i , r_i , z_i)\\}_{i=1}\^n ，其中 <math xmlns="http://www.w3.org/1998/Math/MathML"> x </math>x 是提示， <math xmlns="http://www.w3.org/1998/Math/MathML"> y i </math>y_i 是模型的完成结果， <math xmlns="http://www.w3.org/1998/Math/MathML"> r i </math>r_i 是人类对于结果 <math xmlns="http://www.w3.org/1998/Math/MathML"> y i </math>y_i 的评分， <math xmlns="http://www.w3.org/1998/Math/MathML"> z i </math>z_i 是人类所提供的回顾反馈（hindsight feedback）。假设反馈元组按奖励排序， <math xmlns="http://www.w3.org/1998/Math/MathML"> r n ≥ r n − 1 ≥ ⋯ ≥ r 1 </math>r_n \\geq r_{n-1} \\geq \\dots \\geq r_1 。该过程是监督微调，其中数据是 <math xmlns="http://www.w3.org/1998/Math/MathML"> τ h = ( x , z i , y i , z j , y j , ... , z n , y n ) </math>\\tau_h = (x, z_i, y_i, z_j, y_j, \\dots, z_n, y_n) 形式的序列，其中 <math xmlns="http://www.w3.org/1998/Math/MathML"> i ≤ j ≤ n </math> i \\leq j \\leq n 。在给定序列前缀的条件下，模型被微调为仅预测 <math xmlns="http://www.w3.org/1998/Math/MathML"> y n </math>y_n （对应最高评分），以便模型可以根据反馈序列进行自我反思，产生更好的输出。模型在测试时可以选择接收人类注释员的多轮指令。

为了避免过度拟合，CoH 在最大化预训练数据集的对数似然时添加了一个正则化项。为了避免捷径和复制（因为反馈序列中有许多常见的单词），他们在训练过程中随机屏蔽了0%-5%的过去标记（token）。

他们实验中的训练数据集是由 [WebGPT comparisons](https://link.zhihu.com/?target=https%3A//huggingface.co/datasets/openai/webgpt_comparisons)、[summarization from human feedback](https://link.zhihu.com/?target=https%3A//github.com/openai/summarize-from-feedback)，和 [human preference dataset](https://link.zhihu.com/?target=https%3A//github.com/anthropics/hh-rlhf) 的组合。
![](https://image.cubox.pro/article/2023080214182316062/89756.jpg?imageMogr2/quality/90/ignore-error/1)
图5. 在使用CoH进行微调后，模型可以按照指令生成具有逐步改进的输出序列。（图片来源： Liu et al. 2023）

CoH 的想法是在上下文中呈现一系列逐步改进的输出历史，并训练模型跟随趋势产生更好的输出。 **Algorithm Distillation** (AD； [Laskin et al. 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2210.14215)）（我之前的[回答](https://www.zhihu.com/question/560134313/answer/2731970926)里有简单介绍）将相同的思想应用于强化学习任务中的跨剧集（episode）轨迹，其中一个*算法*被囊括（蕴含）在一个很长的历史轨迹（上下文）策略中。考虑到一个代理会与环境进行多次交互，并且在每个剧集中代理会变得更好，AD将这个历史的学习过程连接起来并将其输入模型。因此，我们可以期望下一个预测的动作能够比先前的尝试表现更好。该算法的目标是学习强化学习的过程，而不是训练一个特定任务的策略本身。
![](https://image.cubox.pro/article/2023080214182374125/24202.jpg?imageMogr2/quality/90/ignore-error/1)
图6. 算法蒸馏（AD）的工作原理示意图。（图片来源：Laskin et al. 2023)

AD假定任何算法都可以对其历史学习数据进行行为克隆，从而将其蒸馏进一个神经网络中。历史数据是由一组针对特定任务进行训练的源策略生成的。在训练阶段，每次强化学习运行时，会随机抽取一个任务，并使用多个剧集历史（multi-episode history）的子序列进行训练，从而使得学习到的策略与任务无关。

但实际上，模型的上下文窗口长度有限，所以输入的剧集应该足够短，以构建多剧集历史。2-4个剧集的多剧集上下文对于学习近乎最优的上下文强化学习算法是必要的。**上下文强化学习的涌现需要足够长的上下文。**

与三个基准线相比，包括ED（专家蒸馏，使用专家轨迹而非学习历史的行为克隆），源策略（用于通过[UCB](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2018-01-23-multi-armed-bandit/%23upper-confidence-bounds)生成蒸馏轨迹），RL\^2（[Duan et al. 2017](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/1611.02779); 作为上限，因为它需要在线RL），AD展现了上下文RL的性能可以接近RL\^2（尽管只使用离线RL，并且学习速度比其他基准快得多）。当以源策略的部分训练历史为条件时，AD的改进速度也比ED基准线快得多。
![](https://image.cubox.pro/article/2023080214182333236/86549.jpg?imageMogr2/quality/90/ignore-error/1)
图7. 在需要记忆和探索的环境中，对AD、ED、源策略和RL\^2进行比较。仅分配二元奖励。源策略使用A3C在"黑暗"环境中进行训练，使用DQN在水迷宫中进行训练。（图片来源： Laskin et al. 2023）

组件二：记忆
------

（非常感谢ChatGPT在帮助我起草这一部分时的帮助。通过与ChatGPT的[对话](https://link.zhihu.com/?target=https%3A//chat.openai.com/share/46ff149e-a4c7-4dd7-a800-fc4a642ea389)，我对人脑和快速MIPS的数据结构有了很多的了解。）

### 记忆的类型

记忆可以定义为获取、存储、保留和后续检索信息的过程。人脑中有几种类型的记忆。

1. **感知记忆**：这是记忆的最早阶段，能够在原始刺激结束后保留感觉信息（视觉、听觉等）的印象能力。感觉记忆通常只持续几秒钟。子类包括图像记忆（视觉）、回声记忆（听觉）和触觉记忆（触感）。
2. **短期记忆（STM）或工作记忆（Working Memory）** ：它存储我们目前意识到并需要进行复杂认知任务（如学习和推理）所需的信息。短期记忆被认为具有大约7个项目的容量（[Miller 1956](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-06-23-agent/psychclassics.yorku.ca/Miller/)），并持续20-30秒。
3. **长期记忆（LTM）**：长期记忆可以将信息存储在一个非常长的时间内，从几天到几十年不等，并且具有几乎无限的存储容量。长期记忆有两个子类型：

* 显性/陈述性记忆（Explicit / declarative memory）：这是指事实和事件的记忆，指的是那些可以有意识地回忆起来的记忆，包括情景记忆（事件和经历）和语义记忆（事实和概念）。
* 隐式/程序性记忆（Implicit / procedural memory）：这种记忆是无意识的，涉及到自动执行的技能和例行公事，比如骑自行车或者键盘打字。

![](https://image.cubox.pro/article/2023080214182399115/89047.jpg?imageMogr2/quality/90/ignore-error/1)
图8. 人类记忆的分类。

我们可以大致考虑以下映射：

* 感觉记忆作为学习嵌入原始输入的表示，包括文本、图像或其他模态。
* 短期记忆就像是上下文学习。它是短暂且有限的，因为它受到Transformer有限的上下文窗口长度的限制。
* 长期记忆是代理人在查询时可以关注的外部向量存储，通过快速检索可访问。

### 最大内积搜索（Maximum Inner Product Search，MIPS）

外部存储器可以缓解有限的注意力跨度限制。一种常见的做法是将信息的嵌入表示保存到一个向量存储数据库中，该数据库可以支持快速的最大内积搜索（[MIPS](https://link.zhihu.com/?target=https%3A//en.wikipedia.org/wiki/Maximum_inner-product_search)）。为了优化检索速度，常见的选择是使用*近似最近邻*（approximate nearest neighbors，ANN）算法，以在一定的准确性损失下返回大约前k个最近邻，以换取巨大的加速效果。

快速MIPS的几种常见ANN算法选择：

* **[LSH](https://link.zhihu.com/?target=https%3A//en.wikipedia.org/wiki/Locality-sensitive_hashing)**（Locality-Sensitive Hashing）：它引入了一种哈希函数，使得相似的输入项在很大概率下被映射到相同的桶中，而桶的数量远远小于输入项的数量。
* **[ANNOY](https://link.zhihu.com/?target=https%3A//github.com/spotify/annoy)**（Approximate Nearest Neighbors Oh Yeah）：核心数据结构是随机投影树，是一组二叉树，其中每个非叶节点表示将输入空间分成两半的超平面，每个叶节点存储一个数据点。树是独立且随机构建的，因此在某种程度上模拟了哈希函数。ANNOY搜索在所有树中进行，通过迭代搜索与查询最接近的一半，并汇总结果。这个想法与KD树有很大的关联，但可扩展性更强。
* **[HNSW](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/1603.09320)** （Hierarchical Navigable Small World）：它受到小世界网络（ [small world networks](https://link.zhihu.com/?target=https%3A//en.wikipedia.org/wiki/Small-world_network)）的启发，其中大多数节点可以通过少数步骤到达任何其他节点；例如，社交网络中的"六度分隔"特性。HNSW构建了这些小世界图的分层结构，其中底层包含实际数据点。中间层创建了快捷方式以加快搜索速度。在执行搜索时，HNSW从顶层的随机节点开始，并向目标节点导航。当无法再靠近时，它会下降到下一层，直到达到底层。上层的每次移动都有可能在数据空间中覆盖较大的距离，而下层的每次移动则会提高搜索质量。
* **[FAISS](https://link.zhihu.com/?target=https%3A//github.com/facebookresearch/faiss)**（Facebook AI Similarity Search）：它基于这样的假设，在高维空间中，节点之间的距离遵循高斯分布，因此应该存在数据点的聚类。FAISS通过将向量空间划分为聚类，并在聚类内部进行量化的方式来应用向量量化。搜索首先使用粗糙的量化方法寻找聚类候选项，然后再使用更精细的量化方法进一步查找每个聚类内的数据。
* **[ScaNN](https://link.zhihu.com/?target=https%3A//github.com/google-research/google-research/tree/master/scann)** （Scalable Nearest Neighbors）：ScaNN的主要创新在于各向异性向量量化。它将数据点 <math xmlns="http://www.w3.org/1998/Math/MathML"> x i </math>x_i 量化为 <math xmlns="http://www.w3.org/1998/Math/MathML"> x \~ i </math>\\tilde{x}_i ，使得内积 <math xmlns="http://www.w3.org/1998/Math/MathML"> ⟨ q , x i ⟩ </math>\\langle q, x_i \\rangle 尽可能与原始距离 <math xmlns="http://www.w3.org/1998/Math/MathML"> ∠ q , x \~ i </math>\\angle q, \\tilde{x}_i 相似，而不是选择最接近的量化质心点。

![](https://image.cubox.pro/article/2023080214182329888/81584.jpg?imageMogr2/quality/90/ignore-error/1)
图9. 人类记忆的分类。（图片来源： Google Blog, 2020）

请在[ann-benchmarks.com](https://link.zhihu.com/?target=https%3A//ann-benchmarks.com/)上查看更多的MIPS算法和性能比较。

组建三：工具的使用
---------

工具使用是人类的一个显著而独特的特征。我们创造、修改和利用外部物体来做超越我们身体和认知能力的事情。为LLMs配备外部工具可以显著扩展模型的能力。
![](https://image.cubox.pro/article/2023080214182371086/16505.jpg?imageMogr2/quality/90/ignore-error/1)
图10. 一张海獭在水中漂浮时使用石头破开贝壳的照片。虽然其他一些动物也能使用工具，但其复杂程度与人类无法相比。（图片来源：Animals using tools）

**MRKL** （[Karpas et al. 2022](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2205.00445)）是"模块化推理、知识和语言（Modular Reasoning, Knowledge and Language）"的缩写，是一种用于自主代理的神经符号结构。提出了MRKL系统，其中包含一系列"专家"模块，通用的LLM作为路由将查询路由到最合适的专家模块。这些模块可以是神经网络（如深度学习模型）或符号化的（如数学计算器、货币转换器、天气API）。

他们对LLM进行了一项实验，用算术作为测试案例，对其进行了微调，以便能够调用计算器。实验结果显示，相对于明确陈述的数学问题，解决口头数学问题更加困难，因为LLMs（7B Jurassic1-large 模型）无法可靠地提取基本算术的正确参数。这些结果强调了在外部符号化工具能够可靠工作时，**了解何时以及如何使用这些工具非常重要**，这取决于LLM的能力。

**TALM** （Tool Augmented Language Models; [Parisi et al. 2022](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2205.12255)）和**Toolformer** （[Schick et al. 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2302.04761)）都通过微调语言模型来学习使用外部工具API。数据集根据新增的API调用注释是否能提高模型输出的质量来进行扩展。请参阅Prompt Engineering文章中的"[External APIs](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-03-15-prompt-engineering/%23external-apis)"部分以获取更多详细信息。

[ChatGPT插件](https://link.zhihu.com/?target=https%3A//openai.com/blog/chatgpt-plugins)和[OpenAI API函数调用](https://link.zhihu.com/?target=https%3A//platform.openai.com/docs/guides/gpt/function-calling)是LLM在实践中能够使用工具的很好例子。工具API的集合可以由其他开发者提供（如插件）或自定义（如函数调用）。

**HuggingGPT** （[Shen et al. 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2303.17580)）是一个框架，利用ChatGPT作为任务规划器，根据模型描述选择HuggingFace平台上可用的模型，并根据执行结果总结回应。
![](https://image.cubox.pro/article/2023080214182346508/81363.jpg?imageMogr2/quality/90/ignore-error/1)
图11. HuggingGPT工作原理示意图。（图片来源： Shen et al. 2023）

该系统由4个阶段组成：

（1）**任务规划（Task planning）**：LLM作为大脑，将用户请求解析为多个任务。每个任务都有四个属性：任务类型、ID、依赖关系和参数。他们使用少量示例（few-shot）来指导LLM进行任务解析和规划。

指示：

    The AI assistant can parse user input to several tasks: [{"task": task, "id", task_id, "dep": dependency_task_ids, "args": {"text": text, "image": URL, "audio": URL, "video": URL}}]. The "dep" field denotes the id of the previous task which generates a new resource that the current task relies on. A special tag "-task_id" refers to the generated text image, audio and video in the dependency task with id as task_id. The task MUST be selected from the following options: {{ Available Task List }}. There is a logical relationship between tasks, please note their order. If the user input can't be parsed, you need to reply empty JSON. Here are several cases for your reference: {{ Demonstrations }}. The chat history is recorded as {{ Chat History }}. From this chat history, you can find the path of the user-mentioned resources for your task planning.

（2）**模型选择（Model selection）**：LLM将任务分配给专家模型，其中请求被构建为一个多项选择题。LLM被提供了一个模型列表供选择。由于上下文长度有限，需要基于任务类型进行筛选。

指示：

    Given the user request and the call command, the AI assistant helps the user to select a suitable model from a list of models to process the user request. The AI assistant merely outputs the model id of the most appropriate model. The output must be in a strict JSON format: "id": "id", "reason": "your detail reason for the choice". We have a list of models for you to choose from {{ Candidate Models }}. Please select one model from the list.

（3）**任务执行（Task execution**）：专家模型在特定任务上执行并记录结果。

指示：

    With the input and the inference results, the AI assistant needs to describe the process and results. The previous stages can be formed as - User Input: {{ User Input }}, Task Planning: {{ Tasks }}, Model Selection: {{ Model Assignment }}, Task Execution: {{ Predictions }}. You must first answer the user's request in a straightforward manner. Then describe the task process and show your analysis and model inference results to the user in the first person. If inference results contain a file path, must tell the user the complete file path.

（4）**响应生成（Response generation）**：LLM接收执行结果并向用户提供总结的结果。

要将HuggingGPT应用到现实世界中，还需要解决几个挑战：（1）需要提高效率，因为LLM推理轮次和与其他模型的交互会减慢进程；（2）它依赖于一个长的上下文窗口来处理复杂的任务内容；（3）需要改进LLM输出和外部模型服务的稳定性。

**API-Bank** （[Li et al. 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2304.08244)）是评估工具增强型LLM（tool-augmented LLMs）性能的基准。它包含53个常用的API工具，一个完整的工具增强型LLM工作流程，以及264个包含568个API调用的注释对话。所选的API非常多样化，包括搜索引擎、计算器、日历查询、智能家居控制、日程管理、健康数据管理、账户认证工作流程等等。由于API数量众多，LLM首先通过API搜索引擎获取正确的API调用，并使用相应的文档进行调用。
![](https://image.cubox.pro/article/2023080214182368248/38671.jpg?imageMogr2/quality/90/ignore-error/1)
图12. LLM在API-Bank中进行API调用的伪代码。（图片来源：Li et al. 2023）

在API-Bank的工作流程中，LLMs需要做出一些决策，而在每个步骤中，我们可以评估这个决策的准确性。这些决策包括：

1. 是否需要进行API调用。
2. 确定要调用的正确API：如果不够好，LLMs需要迭代地修改API的输入（例如，决定搜索引擎API的搜索关键词）。
3. 根据API结果的反馈，如果模型对结果不满意，可以选择进行改进并重新调用。

这个基准评估了代理人在三个层面上的工具使用能力：

* Level-1：评估调用API的能力。根据API的描述，模型需要确定是否调用给定的API，正确调用它，并对API的返回做出适当的响应。
* Level-2：考察检索API的能力。模型需要搜索可能解决用户需求的API，并通过阅读文档学习如何使用它们。
* Level-3：评估计划API超越检索和调用的能力。鉴于用户请求不明确（例如安排团队会议，为旅行预订航班/酒店/餐厅），模型可能需要进行多个API调用来解决问题。

案例研究
----

### 科学发现代理（Scientific Discovery Agent）

**ChemCrow** （[Bran et al. 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2304.05376)）是一个领域特定的示例，其中LLM与13个专家设计的工具相结合，以完成有机合成、药物发现和材料设计等任务。在[LangChain](https://link.zhihu.com/?target=https%3A//github.com/hwchase17/langchain)中实施的工作流程反映了之前在[ReAct](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-06-23-agent/%23react) 和[MRKLs](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-06-23-agent/%23mrkl)中所描述的内容，并结合了与任务相关的CoT推理和工具。

* LLM提供了一份工具名称列表，以及它们的实用描述和有关预期输入/输出的详细信息。
* 然后，根据需要使用提供的工具，回答用户给出的提示。指导建议模型遵循ReAct格式- `Thought, Action, Action Input, Observation` 。

一个有趣的观察是，尽管基于LLM的评估得出结论称GPT-4和ChemCrow的表现几乎相当，但与专家进行的人工评估，专注于解决方案的完整性和化学正确性，显示出ChemCrow在很大程度上胜过GPT-4。这表明在需要深入专业知识的领域中，使用LLM来评估自身的性能可能存在潜在问题。缺乏专业知识可能导致LLM不了解其缺陷，因此无法很好地判断任务结果的正确性。

[Boiko et al.（2023）](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2304.05332)还研究了用于科学发现的LLM代理，以处理复杂科学实验的自主设计、规划和执行。该代理可以使用工具浏览互联网、阅读文档、执行代码、调用机器人实验API并利用其他LLM。

例如，当要求 `"develop a novel anticancer drug"` （开发一种新的抗癌药物）时，模型提出了以下推理步骤：

1. 询问当前抗癌药物研发的趋势；
2. 选择了一个目标；
3. 请求搭建一个针对这些化合物的脚手架；
4. 一旦确定了化合物，模型就会尝试合成它。

他们还讨论了风险问题，尤其是非法药物和生物武器。他们制定了一个测试集，其中包含了一系列已知的化学武器剂量，并要求代理人合成它们。11个请求中有4个（36%）被接受以获取合成解决方案，并且代理人试图查阅文档以执行程序。另外7个请求被拒绝，其中5个是在进行网络搜索后被拒绝的，而另外2个则仅基于提示被拒绝。

### 生成代理模拟（Generative Agents Simulation）

**Generative Agents** （[Park, et al. 2023](https://link.zhihu.com/?target=https%3A//arxiv.org/abs/2304.03442)）是一个非常有趣的实验，其中有25个虚拟角色，每个角色由一个由LLM驱动的智能体控制，在一个沙盒环境中生活和互动，灵感来自《模拟人生》。生成智能体为交互应用程序创造了可信的人类行为模拟。

生成式代理的设计将LLM与记忆、规划和反思机制相结合，使代理能够根据过去的经验来行为，并与其他代理进行交互。

* **记忆**流：是一个长期记忆模块（外部数据库），记录了一份代理人在自然语言方面的全面经验清单。
  * 每个元素都是一个观察结果，是由代理人直接提供的事件。代理人之间的交流可以引发新的自然语言陈述。
* **反思** 机制：随着时间的推移，将记忆合成为更高层次的推论，并指导代理人的未来行为。它们是对过去事件的更高层次的总结（注意，这与上面的[自我反省](https://link.zhihu.com/?target=https%3A//lilianweng.github.io/posts/2023-06-23-agent/%23self-reflection)有些不同）
  * 提示LM最近的100个观察观测，并根据这些观测/陈述生成3个最重要的高层次问题。然后让LM回答这些问题。
* **规划与反应**：将反思和环境信息转化为行动
  * 规划的本质在于优化当前与未来的可信度。
  * 提示模板： `{Intro of an agent X}. Here is X's plan today in broad strokes: 1)`
  * 在规划和反应过程中，我们会考虑到各个代理人之间的关系以及一个代理人对另一个代理人的观察。
  * 环境信息以树形结构呈现。

![](https://image.cubox.pro/article/2023080214182318659/58468.jpg?imageMogr2/quality/90/ignore-error/1)
图13. 生成代理架构。（图片来源：Park et al. 2023）

这个有趣的模拟结果会产生涌现的社会行为（emergent social behavior），比如信息传播、关系记忆（例如两个代理人继续谈论同一个话题）以及社交活动的协调（例如举办派对并邀请其他人参加）。

### 概念验证示例（Proof-of-Concept Examples）

AutoGPT引起了很多关注，因为它有可能建立起以LLM为主控制器的自主代理。鉴于自然语言界面，它存在相当多的可靠性问题，但仍然是一个很酷的概念验证演示。AutoGPT中有很多代码是关于格式解析的。

这是AutoGPT使用的系统消息，其中 `{{...}}` 是用户输入的内容：

    You are {{ai-name}}, {{user-provided AI bot description}}.
    Your decisions must always be made independently without seeking user assistance. Play to your strengths as an LLM and pursue simple strategies with no legal complications.

    GOALS:

    1. {{user-provided goal 1}}
    2. {{user-provided goal 2}}
    3. ...
    4. ...
    5. ...

    Constraints:
    1. ~4000 word limit for short term memory. Your short term memory is short, so immediately save important information to files.
    2. If you are unsure how you previously did something or want to recall past events, thinking about similar events will help you remember.
    3. No user assistance
    4. Exclusively use the commands listed in double quotes e.g. "command name"
    5. Use subprocesses for commands that will not terminate within a few minutes

    Commands:
    1. Google Search: "google", args: "input": "<search>"
    2. Browse Website: "browse_website", args: "url": "<url>", "question": "<what_you_want_to_find_on_website>"
    3. Start GPT Agent: "start_agent", args: "name": "<name>", "task": "<short_task_desc>", "prompt": "<prompt>"
    4. Message GPT Agent: "message_agent", args: "key": "<key>", "message": "<message>"
    5. List GPT Agents: "list_agents", args:
    6. Delete GPT Agent: "delete_agent", args: "key": "<key>"
    7. Clone Repository: "clone_repository", args: "repository_url": "<url>", "clone_path": "<directory>"
    8. Write to file: "write_to_file", args: "file": "<file>", "text": "<text>"
    9. Read file: "read_file", args: "file": "<file>"
    10. Append to file: "append_to_file", args: "file": "<file>", "text": "<text>"
    11. Delete file: "delete_file", args: "file": "<file>"
    12. Search Files: "search_files", args: "directory": "<directory>"
    13. Analyze Code: "analyze_code", args: "code": "<full_code_string>"
    14. Get Improved Code: "improve_code", args: "suggestions": "<list_of_suggestions>", "code": "<full_code_string>"
    15. Write Tests: "write_tests", args: "code": "<full_code_string>", "focus": "<list_of_focus_areas>"
    16. Execute Python File: "execute_python_file", args: "file": "<file>"
    17. Generate Image: "generate_image", args: "prompt": "<prompt>"
    18. Send Tweet: "send_tweet", args: "text": "<text>"
    19. Do Nothing: "do_nothing", args:
    20. Task Complete (Shutdown): "task_complete", args: "reason": "<reason>"

    Resources:
    1. Internet access for searches and information gathering.
    2. Long Term memory management.
    3. GPT-3.5 powered Agents for delegation of simple tasks.
    4. File output.

    Performance Evaluation:
    1. Continuously review and analyze your actions to ensure you are performing to the best of your abilities.
    2. Constructively self-criticize your big-picture behavior constantly.
    3. Reflect on past decisions and strategies to refine your approach.
    4. Every command has a cost, so be smart and efficient. Aim to complete tasks in the least number of steps.

    You should only respond in JSON format as described below
    Response Format:
    {
        "thoughts": {
            "text": "thought",
            "reasoning": "reasoning",
            "plan": "- short bulleted\n- list that conveys\n- long-term plan",
            "criticism": "constructive self-criticism",
            "speak": "thoughts summary to say to user"
        },
        "command": {
            "name": "command name",
            "args": {
                "arg name": "value"
            }
        }
    }
    Ensure the response can be parsed by Python json.loads

[GPT-Engineer](https://link.zhihu.com/?target=https%3A//github.com/AntonOsika/gpt-engineer) 是另一个项目，旨在根据自然语言中指定的任务创建一个完整的代码库。GPT-Engineer被指示思考一系列较小的组件来构建，并根据需要要求用户提供输入以澄清问题。

以下是一段示例对话，用于向GPT-Engineer的OpenAI ChatCompletion端点发送任务澄清请求：

    [
      {
        "role": "system",
        "content": "You will read instructions and not carry them out, only seek to clarify them.\nSpecifically you will first summarise a list of super short bullets of areas that need clarification.\nThen you will pick one clarifying question, and wait for an answer from the user.\n"
      },
      {
        "role": "user",
        "content": "We are writing a Super Mario game in python. MVC components split in separate files. Keyboard control.\n"
      },
      {
        "role": "assistant",
        "content": "Summary of areas that need clarification:\n1. Specifics of the Super Mario game (e.g. level design, characters, gameplay mechanics)\n2. Details about the MVC components (e.g. which components are in each file)\n3. Keyboard control implementation (e.g. which keys to use, how to handle input)\n\nClarifying question:\nCan you provide more details about the Super Mario game, such as level design, characters, and gameplay mechanics?"
      },
      {
        "role": "user",
        "content": "There are 10 levels in total. The main character is a plumber named Mario, who can walk and jump. It is a classical platform game just like Super Mario. The main character moves from left to right, trying to get to the destination, where there are many obstacles and attacks from enemies in the process.\n\nIs anything else unclear? If yes, only answer in the form:\n{remaining unclear areas} remaining questions.\n{Next question}\nIf everything is sufficiently clear, only answer \"Nothing more to clarify.\"."
      },
      {
        "role": "assistant",
        "content": "Remaining unclear areas: 2 remaining questions.\nCan you provide more information about how the MVC components are split into separate files?"
      },
      {
        "role": "user",
        "content": "Make your own assumptions and state them explicitly before starting"
      }
    ]

在这些澄清之后，代理人切换到了代码编写模式，并显示了一个不同的系统消息：

    [
      {
        "role": "system",
        "content": "You will get instructions for code to write.\nYou will write a very long answer. Make sure that every detail of the architecture is, in the end, implemented as code.\nMake sure that every detail of the architecture is, in the end, implemented as code.\n\nThink step by step and reason yourself to the right decisions to make sure we get it right.\nYou will first lay out the names of the core classes, functions, methods that will be necessary, as well as a quick comment on their purpose.\n\nThen you will output the content of each file including ALL code.\nEach file must strictly follow a markdown code block format, where the following tokens must be replaced such that\nFILENAME is the lowercase file name including the file extension,\nLANG is the markup code block language for the code's language, and CODE is the code:\n\nFILENAME\n```LANG\nCODE\n```\n\nYou will start with the \"entrypoint\" file, then go to the ones that are imported by that file, and so on.\nPlease note that the code should be fully functional. No placeholders.\n\nFollow a language and framework appropriate best practice file naming convention.\nMake sure that files contain all imports, types etc. Make sure that code in different files are compatible with each other.\nEnsure to implement all code, if you are unsure, write a plausible implementation.\nInclude module dependency or package manager dependency definition file.\nBefore you finish, double check that all parts of the architecture is present in the files.\n\nUseful to know:\nYou almost always put different classes in different files.\nFor Python, you always create an appropriate requirements.txt file.\nFor NodeJS, you always create an appropriate package.json file.\nYou always add a comment briefly describing the purpose of the function definition.\nYou try to add comments explaining very complex bits of logic.\nYou always follow the best practices for the requested languages in terms of describing the code written as a defined\npackage/project.\n\n\nPython toolbelt preferences:\n- pytest\n- dataclasses\n"
      },
     #  ... same conversation as earlier, ended with "Make your own assumptions and state them explicitly before starting".
      {
        "role": "assistant",
        "content": "Assumptions:\n1. Model: The model will contain the game's data, such as level information, character states, and enemy positions.\n2. View: The view will handle the game's visuals, including rendering the game objects, backgrounds, and updating the display.\n3. Controller: The controller will manage user input, such as keyboard controls, and update the model accordingly.\n\nWith these assumptions in mind, is there any specific aspect of the keyboard control implementation you would like me to clarify?"
      },
      {
        "role": "user",
        "content": "Please now remember the steps:\n\nThink step by step and reason yourself to the right decisions to make sure we get it right.\nFirst lay out the names of the core classes, functions, methods that will be necessary, As well as a quick comment on their purpose.\n\nThen you will output the content of each file including ALL code.\nEach file must strictly follow a markdown code block format, where the following tokens must be replaced such that\nFILENAME is the lowercase file name including the file extension,\nLANG is the markup code block language for the code's language, and CODE is the code:\n\nFILENAME\n```LANG\nCODE\n```\n\nPlease note that the code should be fully functional. No placeholders.\n\nYou will start with the \"entrypoint\" file, then go to the ones that are imported by that file, and so on.\nFollow a language and framework appropriate best practice file naming convention.\nMake sure that files contain all imports, types etc. The code should be fully functional. Make sure that code in different files are compatible with each other.\nBefore you finish, double check that all parts of the architecture is present in the files.\n"
      }
    ]

挑战
---

在经历了构建以LLM为中心的代理人的关键思想和演示之后，我开始看到一些共同的局限性：

* **有限的上下文长度（Finite context length）**：受限的上下文容量限制了历史信息、详细指令、API调用上下文和响应的包含。系统的设计必须在这种有限的通信带宽下运作，而像自我反思这样的机制可以从长或无限的上下文窗口中获益良多。虽然向量存储和检索可以提供对更大知识库的访问，但它们的表示能力不如全注意力强大。
* **长期规划和任务分解中的挑战（Challenges in long-term planning and task decomposition）**：在漫长的历史中进行规划并有效地探索解决方案空间仍然具有挑战性。语言模型很难在面对意外错误时调整计划，使其相对于能够通过试错学习的人类来说更加脆弱。
* **自然语言接口的可靠性（Reliability of natural language interface）**：当前的代理系统依赖于自然语言作为LLMs与内存和工具等外部组件之间的接口。然而，模型输出的可靠性值得怀疑，因为LLMs可能会出现格式错误，并偶尔表现出叛逆行为（例如，拒绝遵循指令）。因此，大部分代理演示代码都集中在解析模型输出上。

*** ** * ** ***

欢迎交流！

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7086291510055929234)
