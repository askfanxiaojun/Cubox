5000字详解OpenAI超级对齐四年计划：定义、挑战与方法
==============================

[new.qq.com](https://new.qq.com/rain/a/20230829A07HKW00)智源社区2023-08-29 18:00:00发布于北京智源社区官方账号+关注


**导读**


超级智能是一把双刃剑，有助于解决许多重要问题，同时也可能削弱人类的权力并威胁我们的安全。为了治理这些风险，急需建立新的治理机构并解决AI模型的对齐问题。OpenAI于今年7月首次提出超级对齐的概念，并宣布投入20%的计算资源，花费4年的时间全力打造一个超级对齐（Superalignment）系统，意在解决超级智能的对齐问题。   


![图片](https://image.cubox.pro/cardImg/2023121514404178757/25462.jpg?imageMogr2/quality/90/ignore-error/1)

图：OpenAI官网宣布开始构建超级对齐系统

随着OpenAI官方团队的介绍和多方解析不断发布，超级对齐的面貌也逐渐清晰地呈现在大家的面前，**本文** **结合** **现有资料详细介绍超级对齐的概念、为什么要实现超级对齐以及如何实现超级对齐，希望这一愿景能够促进发展符合人类目标和价值观的安全AI，并不断吸纳更多研究者加入这一行列。**

**什么是超级对齐**


**1.1 超级对齐的目标**


**超级对齐旨在构建一个能够与人类水平相媲美的自动对齐研究器。**其目标是尽可能地将与对齐相关的工作交由自动系统完成。在使用LLM或构建通用AI系统时，人们意识到它们的技能组合并不一定与人类相同。它们在某些方面可能更为强大，例如现有的语言模型在翻译或知识储备方面表现出色。然而，AI系统在其他一些任务上可能相对薄弱，比如算术方面的能力。

因此，研究者们面临的问题是，应该将哪些类型的任务交由AI系统，并按照什么顺序进行？这样一来，这个系统可以预测人类将更多地专注于那些无法交由AI系统完成的任务。在这个过程中，AI系统完成的工作占整体工作的比例将会越来越大，而人类研究者将能够更有效地取得真正的进展。

在第一个阶段，研究者们希望这个研究器能够实现机器学习模型，进行实验并观察结果。第二个阶段，研究者们希望这个研究器能够解决更高级、更广泛的问题，例如确定需要进行哪些实验来提升可扩展监督，或者在可解释性方面取得进展。目前第一个阶段上已经有了卓有成效的研究，而第二个阶段研究者们仍尚在探索中。

![图片](https://image.cubox.pro/cardImg/2023121514404210943/88367.jpg?imageMogr2/quality/90/ignore-error/1)

图：GPT-4模拟输出从而提供可扩展监督的能力示例

**1.2 超级对齐的能力**


**对于相关研究者来说，自动对齐的长期目标在于模型的创造力。**OpenAI相关研究团队表示，至少对于语言模型或AI而言，它们比人类更具创造力。如果你去观察扩散模型生成的图像，或者从预训练的基础模型中采样，其中包含了很多奇思妙想，这些创意恐怕从单人或小团队身上很难获得。因此，它们实际上可以从整个分布中进行采样，而个人通常做不到这一点。就长期目标而言，研究者们可以将一些小而明确的任务交给AI系统，如果它们能够将这些任务真正做好，那么未来帮助很大。

目前，ChatGPT的对齐方式主要是通过强化学习从人类反馈中进行训练，但这种方法无法扩展，这已经是一种广泛共识，因为它从根本上假设了人类真正理解系统的详细运行方式。

如果系统进行了大量对齐研究，涉及数百万个虚拟人类的任务，很难看到其中所有的细节和详细反馈。但目前研究中所使用的方法，均对这些步骤进行扩展，从而打造一个大致与人类水平相当，且可以完成困难任务的对齐研究员。**例如，可扩展监督就是从人类强化反馈中让AI进行学习，从而具备该能力的一种方式。**

**为什么要实现超级对齐**


超级对齐的出现是由于当前生成式AI的热潮，引发了人们对于AI对齐能力的担忧。最近，Chris Olah发布了一系列推文，描述了Anthropic团队对于AI对齐困难的看法。根据这种观点，存在着一系列可能情景，**从"对齐非常容易"到"对齐不可能"**，我们可以将AI对齐研究视为逐步解决这些情景，增加有益结果概率的过程。在此基础上，提供了更详细的AI对齐困难程度划分，并解释了其中涉及的一些考虑因素。

当前关于AI安全的讨论主要集中在潜在AI系统及其故障模式的详细概念以及确保其安全的方法上。DeepMind安全团队的一篇文章提供了一些故障模式的概述。目前，**Sammy Martin提到可以通过"对齐困难"的视角理解这些不同的威胁模型，将各种导致AI失调的来源按照易于解决程度排序**，然后尝试将技术性的AI安全干预与具体的对齐失效模式场景匹配起来。这清晰地表明，这种不确定性使得对齐研究人员之间的一些辩论更容易理解。

一个相对简单的情景可能涉及AI模型以符合常识的方式进行泛化和学习目标。举个例子，我们可以将复杂程度不同的LLM理解为潜在作家的生成框架，而强化学习则通过人类反馈或发现AI在潜在作家中进行选择。这种情况有时被称为"默认对齐"。而一个较为困难的情景可能类似于"深度欺骗"，在这种情况下，系统会以快速且不可预测的方式进行泛化，从而迅速使先前的对齐技术过时，并且它们还会学习欺骗性的奖励操纵策略，这些策略在外部评估、红队测试、对抗测试或可解释性检查中表面上看起来与良好行为完全相同。

为了更好地理解解决对齐困难的情景，Sammy Martin将其分为三个层次，如下图所示，以便我们更容易理解。

![图片](https://image.cubox.pro/cardImg/2023121514404288824/67849.jpg?imageMogr2/quality/90/ignore-error/1)

图：不同难度层次的超级对齐

**2.1 简单场景**


**在容易对齐的情景中，我们应该投入更多资源来解决结构风险、经济影响、滥用和地缘政治问题。** 在该场景下，RLHF训练的系统通常会诚实而准确地追求过于简化的代理目标。具体来说，容易的场景可以分为三个等级。

**第一级是Alignment by Default：**当我们扩大规模应用人工智能模型时，如果没有对其进行特定的风险行为指导或训练，也没有设置有问题且明显不好的目标，那么它们不会带来重大风险。即使是超人级的系统，基本上也只是根据外部奖励或语言指令的常识版本来执行。这里的关键风险在于对训练目标的滥用行为以及对强大模型的强化学习朝着错误指定或反社会的目标方向进行。

**第二级是Reinforcement Learning from Human Feedback：**我们需要确保人工智能在各种边界情况下表现良好，通过在广泛的情境中更谨慎地使用人类反馈来进行引导，而不仅仅是粗略的指令或手动指定的奖励函数。如果我们认真进行强化学习的微调，就能够取得良好的效果。有一个原因让我们相信对齐将会如此简单，那就是如果系统本身在归纳上偏向诚实和代表人类给予其的目标。在这种情况下，它们往往会学习简单、诚实和服从的策略，即使这些策略并不是为了最大化奖励而是最优策略。

**第三级是Constitutional AI：**人类反馈并不足够清晰和丰富，无法对人工智能进行精细调整。必须利用人工智能提供的模拟人类反馈来涵盖边界情况。这就是"从人工智能反馈中进行强化学习"的方法。即使人类反馈足以确保模型大致按照监督者的意图执行，由于结构性原因，在广泛部署于经济中的系统可能最终被训练成追求粗略和反社会的代理目标，而无法真正捕捉我们真正想要的目标。

**2.2 中等场景**


中等情景是指行为安全性不够好，最容易产生转变性人工智能的方式导致危险的欺骗性失调。在这种情况下，系统会违背我们的利益，但会假装是有用和安全的。这种情况要求我们在对齐工作上加大努力，并探索可行的策略，如可扩展的监督、对齐研究中的AI辅助和基于可解释性的监督过程。我们还应专注于治理干预，以确保领先的项目有足够的时间来实际实施这些解决方案，并与政府和公民社会一起改变整体战略格局并消除不对齐AI的风险。具体来说，中等场景包含四个等级。

**第一级是Scalable Oversight：**我们需要确保即使在无法由人类监督的问题上，仍然能够对人工智能进行类似人类的监督。因此，我们需要一些方法，与宪法型人工智能不同，能够使人工智能比人类更有效地应用人类式监督。

**第二级是Scalable Oversight with AI Research Assistance：**在当前阶段，我们将使用类似于前面几级中所介绍的技术来使人工智能对齐，并让它们进行对监督方法的研究，并增强人类的理解能力。然后，我们将利用这些研究成果来改进我们的监督流程，或者改进监督人工智能对训练中的人工智能行为的理解。这里的关键风险在于人类反馈对于对齐超人工智能系统来说是一个不够清晰的信号，因此需要进行增强。同时具有情境意识的人工智能系统默认情况下会产生欺骗性的人类模拟器，但通过超人类行为反馈可以消除这种倾向。

**第三级是Oversight employing Advanced Interpretability Techniques：**在监督过程中，会使用概念性或机械性可解释性工具。与欺骗行为相关的人工智能内部过程可以通过在上述两级开发的人工智能或人类+人工智能监督者来进行检测和惩罚。

**第四级是Experiments with Potentially Catastrophic Systems to Understand Misalignment：**在这个层次上，即使我们使用了上述阶段的技术，人工智能系统仍然会常规性地击败监督，并继续出现不受欢迎的行为。它们通过改变内部过程以避免被可解释性工具检测，并通过"玩训练游戏"来看起来行为安全。然而，关键是，我们仍然可以控制这些系统。因此，我们可以对这些人工智能系统进行（潜在危险的）实验，以了解它们在部署后可能的泛化情况。在这里，我们将运用可解释性和监督工具，并尝试引发人工智能的误泛化和奖励破解行为。但我们不会试图使用基于监督的训练来消除这些行为。相反，我们尝试通过类似红队的技术来理解它们发生的基础，学习关于误对齐产生的如何以及为什么的实用技巧和新的理论见解，从而使我们能够开发新的缓解方法。

**2.3 困难场景**


相比而言，如果我们认为对齐转变性人工智能的困难程度如此之高，那么未来几年甚至几十年的研究努力可能无法给我们足够的信心。如果对齐确实如此困难，我们需要在前沿系统中应用强大的测试和可解释性技术，以减少不确定性，证明悲观情景的真实性，并建立起停止进展向转变性人工智能的动力。具体而言，困难场景可以分为两个层次。

**第一层是Theoretical Research for Understanding Misalignment：**所有的问题行为要么发生得太快以至于无法及时应对，要么只在系统部署后才显现，因此之前的实验是无用的或者不安全的。在这个层次上，我们需要事先了解人工智能模型如何推广学习。希望这些基础性的洞察能够激发出新的对齐技术。

**第二层是Coming up with a Fundamentally New Paradigm (abandoning deep learning)：**根据这种观点，即使我们改变了关于深度学习系统的基本要素，也无法对其进行对齐。这里的关键挑战在于存在一种"急剧转变"，在这个转变中，系统突然获得了新的概念和更高的智能和广泛性，使得之前的对齐技术变得过时。在急剧转变后的系统是超级智能的，无法安全地进行实验或控制。

正是因为当前对齐水平的低下，OpenAI决定投入大量人力和物力来实现超级对齐。

**如何实现超级对齐**


Superalignment 团队由OpenAI联合创始人Ilya Sutskever和Jan Leike共同领导。从OpenAI推特公布的信息来看目前也已有多位成员。为了构建超级对齐系统，开发团队需要进行一系列的工作。

**3.1 可扩展的训练方法**


**首先，我们需要开发一种可扩展的训练方法。**这种方法将利用人工智能系统来辅助评估其他人工智能系统，并将AI模型的监督能力扩展到人类无法监督的任务上。

在开发可扩展的训练方法时，我们需要考虑如何利用现有的人工智能系统来评估其他系统。这可能包括设计评估指标或开发评估算法，以确保对各种不同类型的系统进行准确评估。

此外，我们还需要思考如何将AI模型的监督能力扩展到人类无法监督的任务上。这意味着在没有人类监督的情况下，AI模型能够自主学习和提升自身能力。为了实现这一目标，我们可能需要探索一些自监督学习的方法，通过让AI模型从未标记的数据中学习，提高其在无监督任务上的表现。目前，由模型自动辅助的评估和人类评估相结合，已经被验证比单纯的人类评估取得了更好的效果。

![图片](https://image.cubox.pro/cardImg/2023121514404378118/83757.jpg?imageMogr2/quality/90/ignore-error/1)

图：模型自我评估对人类监督的提升

**3.2 验证系统**


**构建超级对齐系统还需要进行系统验证的工作**。验证系统的一致性非常重要，因此在开发过程中，我们会自动搜索有问题的行为和内部结构，以确保系统的稳健性和可解释性。

稳健性指的是系统在面对各种不确定性和异常情况时的表现能力。为了验证系统的稳健性，我们会设计一系列测试用例，模拟各种可能出现的情况，并观察系统的行为。这些测试用例可能包括输入数据的变化、噪声的存在、环境条件的改变等。通过对系统的行为进行分析和评估，我们能够发现系统在不同情况下的问题，并调整算法和模型，提高系统的稳健性。

另一方面，可解释性指的是系统的内部结构和决策过程能够被人理解和解释。为了验证系统的可解释性，我们会对系统的工作原理进行深入分析，并设计一些实验来验证系统的内部结构是否合理。我们可能会通过观察系统的决策过程、分析模型的权重和特征重要性，以及逐步解释系统的方式，来确保系统的可解释性。目前，OpenAI已经通过GPT-4来解释GPT-2的神经元，可以作为可解释性的初步尝试。

![图片](https://image.cubox.pro/cardImg/2023121514404398559/49810.jpg?imageMogr2/quality/90/ignore-error/1)

图：GPT-4自动生成解释

**3.3 压力测试**


**在构建超级对齐系统的过程中，对整个对齐管道进行压力测试是至关重要的一步。**这个步骤旨在使用未对齐的模型来测试整个流程，并确保所提出的方法能够检测到最严重的未对齐类型，即对抗性测试。

对抗性测试是一种针对系统的弱点和漏洞进行测试的方法。通过模拟各种恶意行为或攻击，对抗性测试可以帮助我们在系统中发现潜在的问题，并采取相应的措施来提高系统的鲁棒性和安全性。

在对整个对齐管道进行压力测试时，我们会使用多种未对齐的模型来模拟各种对抗性情况。这些模型可能包括有意伪造的信息、错误的标注、不一致的语义等。我们会将这些模型输入到对齐管道中，并观察系统的行为和输出结果。

通过对系统的行为进行分析和评估，我们能够判断系统是否能够正确地检测到未对齐类型，并采取相应的措施来处理这些情况。如果系统在对抗性测试中表现出不稳定性或错误的行为，我们会进行进一步的调整和优化，以提高系统的鲁棒性和适应性。

**四、总结**


总的来说，OpenAI为大家勾勒的超级对齐的蓝图，是值得期待且令人向往的。虽然我们当前的技术与这个理想仍有差距，我们有理由相信研究者们能开发出具有超级对齐的能力的AI系统。同时，虽然研究者们也担心AI替代他们的工作。但如果AI助手能够完成99%或99.9%的工作，而他们只需处理余下的核心工作，这仍是对他们工作效率的极大提升，从而促使他们更便捷、快速地打造更强大的人工智能。

参考链接

https://openai.com/blog/introducing-superalignment

https://80000hours.org/podcast/episodes/jan-leike-superalignment/#highlights

https://www.lesswrong.com/posts/EjgfreeibTXRx9Ham/ten-levels-of-ai-alignment-difficulty

https://arxiv.org/abs/2206.05802

https://openai.com/research/language-models-can-explain-neurons-in-language-models


**更多内容 尽在智源社区**


[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7135227697680092551)
