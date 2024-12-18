Claude工程师聊prompt：不要把模型当小孩子、不需要角色扮演、实话实说
=======================================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/3GbkY87snrj5ih1rXW2WUg)Founder Park Founder Park

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_gif%2FqpAK9iaV2O3sAVsSPfCN9UX44XiaoicbUJIrOGuaujdMNY6iaQewDZEX1GY3tcVk3QGeKJyUMMHBSMALvO8B7DZwsA%2F640%3Fwx_fmt%3Dgif%26from%3Dappmsg)


一个「汉语新解」的 prompt 突然爆火。

在 Claude 3.5 里使用这个 prompt 后，输入一个中文词语，AI 会生成一张这个词语的吐槽解释图。Prompt 本身的写法很神奇，使用了[伪代码的写法](https://mp.weixin.qq.com/s?__biz=MzkzNDQxOTU2MQ==&mid=2247491570&idx=2&sn=1a5421b6105a3b429bdde0cac4a6ad74&scene=21#wechat_redirect)，也让很多人意识到，原来 prompt 可以这么写。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FqpAK9iaV2O3uPnh8SJ0WNhhc6jdZO0JU9ENBaEoEGb4FCibwwAfLomFM2dM8jdMjm46clpYmo8JCMR4QL1ZGth9Q%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)

如何写好 prompt，一直是一个难题。

在专业 AI 工程师眼里，好的 prompt 到底应该怎么写？prompt 需要怎么迭代？未来随着大模型的进化，我们还需要再为 prompt 绞尽脑汁么？

Anthropic 公司几位负责提示词的工程师们录制了一起播客，讨论了他们如何写 prompt，以及他们认为一份好的 prompt 应该怎么写。Founder Park 对播客进行了编译处理。

讨论嘉宾：

Amanda Askell：负责对齐微调

Alex Albert：负责开发者关系

David Hershey：负责 AI 应用与落地

Zack Witten：负责提示工程

一些有意思的点：

* 很多时候，需要做的只是写一个非常清晰的任务描述，而不是尝试构建抽象的东西。

* 你需要能够把事情讲得足够清楚，让模型明白你的任务是什么，并且擅长思考和描述概念。

* 你得把自己脑海中所有你知道但模型不知道的东西整理清楚，然后写下来。

* 有些任务确实很难，你的每一次调整可能都让结果更加偏离目标。这种情况下，我倾向于放弃。

* 随着模型的能力越来越强，对世界的理解越来越深入，我觉得其实没有必要对它们撒谎。

* 很多人都没有理解什么是提示词。很多人看到一个输入框时，会把它当成一个谷歌搜索框，输入几个关键词。

* 模型可以理解复杂的信息，不需要过度简化。


![](https://image.cubox.pro/cardImg/49ptyqcouzc9s3xbvbkji7igwiujtno1uzwe4pm8wftkt6j5kq?imageMogr2/quality/90/ignore-error/1)

**Founder Park**

来自极客公园，专注与科技创业者聊「真问题」。

302篇原创内容

公众号

，

点击关注，每天更新深度 AI 行业洞察

**01**
------

**好的 prompt：**
--------------

**足够清晰、持续迭代**
-------------


**Alex Albert：什么是提示工程？为什么它是「工程」？prompt 到底是什么？**

**Zack Witten**：我想我感觉提示工程是试图让模型去做一些事情，试图从模型中提取出最多的价值，试图与模型合作完成你原本无法完成的事情。其中很多只是清晰的沟通。我认为本质上，**与模型交谈就像与人交谈，深入其中并理解模型的心理。**

**Alex Albert：那为什么名字中有「工程」这个词？**

**Zack Witten**：我认为「工程」部分来自于**试错的过程**。与模型交谈和与人交谈不同，你随时可以重启这个对话，以独立的方式不断试错，一旦你有了试验和设计不同事物的能力，那就是工程部分有可能介入的地方。

**Alex Albert**：你的意思是，当你在编写这些提示词时，你正在向 Claude 或 API 或其他任何东西输入一条消息，能够来回与模型互动，对这条消息进行迭代，并每次都回到干净的起点，这个过程就是工程的部分。

**Zack Witten**：还有另一个方面，那就是将提示词集成到你的整个系统之中。David 和客户进行了大量的集成工作。很多时候，事情并不是随便写一个提示词，然后给模型就完事那么简单。实际上它要复杂得多。

**David Hershey**：你可以把提示工程看作是你对模型编程的一种方式，但这种解释这让它变得太复杂了，Zach 刚刚说得对，那就是**清晰地说话是最重要的**。但如果你稍微把它当作编程模型来考虑，你得考虑数据从哪里来，你能够访问哪些数据。

如果你在做 RAG 或者类似的东西，我实际上可以使用、执行并传递给模型的是什么？你得考虑延迟的权衡以及你提供的数据量等问题。所以，很多这样的思考都涉及到你如何围绕模型构建系统的思考。我认为这在很大程度上也是它可能值得作为一个独立领域来思考的核心原因，与软件工程师或产品经理等角色不同。这是一种关于如何推理这些模型的独立领域。

**Alex Albert：那么在这个意义上，提示词是否类似于自然语言代码？还是一种完全不同的东西？**

**David Hershey**：我认为，**试图让提示词过于抽象是一种使事情复杂化的方式**，提示词要写得更深入。但更多时候，需要做的只是写一个非常清晰的任务描述，而不是尝试构建抽象的东西。

但即便如此，很多时候你还是需要把一系列指令或者类似的东西编译成格式化的结果。因此，准确性变得非常重要，还有很多与编程相关的事，比如版本控制，以及在实验时如何跟踪你的实验过程等。这些东西像代码一样重要。所以，提示词是一种很特别的模式，你写的是一段文本，但是会像对待代码一样对待它。

**Alex Albert：那么，也许在此基础上，我们已经大致定义了什么是提示工程。那么，什么构成了一个好的提示工程师呢？**

**Amanda Askell**：最重要的能力，就是**清晰的沟通**。你需要能够把事情讲得足够清楚，让模型明白你的任务是什么，并且擅长思考和描述概念。我觉得这就是写作的那一部分。

不过我其实认为，**一个好的写作者不等于一个好的提示工程师**。我跟别人讨论过这个问题，有些人会觉得，或许提示工程师的名字里不该有「工程师」这个词，为什么不叫作家呢？人们认为你在做的工作只是写完一句话就结束了。实际上，为了写出一个还算不错的提示词，我可能会在短短 15 分钟内发出数百个提示，反复调整。

所以，我觉得关键是**要有迭代的意愿和观察的能力**，这也是大家可能误解的地方。如果提示词出问题了，你要去修正它。这种迭代能力很重要。同时，在写的时候提前考虑到你的提示可能会出错，也很关键。比如，如果你有一个提示要应用到 400 个案例中，人们往往会想到一些典型情况，看看提示在这些情况下是否能得到正确的结果，然后就继续往下走了。但我觉得这其实是个常见的错误。你真正要做的是找到那些不寻常的情况。

举个例子，你的提示可能是「我会发送一组数据给你，请提取所有名字以字母 J 开头的行。」接下来你可能会想，万一我发过去的数据集里根本没有以 J 开头的名字呢？或者我发的根本不是数据集，甚至只是一个空字符串。这些都是你需要尝试的情况，因为你需要知道，在这些特殊情况下，模型会怎么反应。然后，你可以根据这些情况，给它更多指示，告诉它该怎么处理。

**David Hershey**：我经常跟客户合作，我发现很多人在设计模型的时候总是想象着用户会在那个框里里输入完美的内容。可实际上，**用户可能连大写字母都从来不用，几乎每个词都有拼写错误**......

很多人以为这跟谷歌搜索一样，他们根本不会加标点符号，只是随意输入一堆没有逻辑的问题。在评估时，你很可能会根据那些理想化、非常结构化的文本进行判断。但实际上，**你需要进想清楚用户真正会输入的东西是什么**？人们实际会尝试做什么？这是需要从不同层次来深入思考的。

**02**
------

**要把你知道**
---------

**模型不知道的东西写出来**
---------------


**Zack Witten**：你刚刚说的一句话让我印象深刻，那就是「阅读模型的输出」。就像在机器学习领域，总是强调要检查数据，几乎成了陈词滥调。对提示工程来说也是一样，要仔细阅读模型的输出。**有些人懂思维链（CoT），会要求模型按步骤思考，但他们并没有检查模型是否真的按步骤思考了**。模型可能会用一种更抽象或广泛的方式来理解提示，而不是按照你的要求逐步思考。如果你不仔细阅读模型的输出，可能根本不会发现它哪里出错了。

**Alex Albert**：是啊，这很有趣。作为提示工程师，你需要有一种「心理预设」，你要揣摩模型会如何看待你的指令。同时，如果你还为企业写提示，你还得考虑他们的用户会怎么跟模型互动。

**David Hershey**：为一项任务写清楚指令确实很难。**你得把自己脑海中所有你知道但模型不知道的东西整理清楚，然后写下来**。这其实是非常具有挑战性的，因为你不仅需要剥离掉所有假设，还得非常清晰地传达出模型完成任务所需的全部信息。这就是为什么优秀提示工程师和平庸工程师之间有很大区别。

很多人写提示的时候，都是根据他们自己对任务的理解来写的，但他们并没有真正花时间去系统地分析任务的需求。**这就导致提示可能过于依赖于作者对任务的先验认知。**当他们把提示词展示给我看时，我常常会觉得这些话完全没有意义，因为我对他们的特殊用例一无所知。

因此，我觉得在思考提示工程时，有一个好的方法，也是一项重要的技能，那就是你能不能**从自己的知识中抽离出来，去思考如何把信息传达给模型**。模型虽然知道很多东西，但它不可能完全了解它需要知道的所有信息来完成任务。你需要找到这个平衡点，帮助模型理解并完成任务。

**Amanda Askell**：完全同意，我见过很多人写的提示词，**可那些东西连我这样一个人类都不明白，他们却指望着模型能帮你解决问题**......

**Alex Albert**：**现在的模型还不擅长像人类那样提出有深度的反问**。如果我现在给 Zack 指示该怎么做某件事，他可能会说：「这不太对劲啊。」然后他会问：「我是不是该在这一步或者那一步做点什么？」但模型不会这么做。所以你得自己想象，如果是人类会问什么问题，然后回头调整你的提示，去回答这些问题。

**Amanda Askell**：其实你可以要求模型这样做。我通常会在初始提示之后给模型一个补充，我会告诉它：「我不希望你按照这些指示操作。我只是想让你指出哪里不清楚，或者哪里有模糊之处，或者你不理解的地方。」虽然模型不总是能完全理解，但这确实是可以尝试的一种方法。

而且有趣的是，很多人在看到模型出错时，往往不会直接去问模型问题。他们只会告诉模型：「你做错了。」

**但其实你可以问模型：「你知道为什么出错吗？能帮我改改我的提示词，让你不再出错吗？」** 很多时候，模型会给出正确的建议。它可能会说：「哦，是的，这里不清楚。」然后它会给出修改后的指令。你把这些改进融入提示里，模型往往就能正确工作了。

**Alex Albert：我其实对这真的很好奇，模型能以那种方式发现它的错误吗？比如当它做错了什么，你问，你为什么会做错这个？然后它会告诉你它为什么做错了，这是真的吗？模型真的拥有这种「智慧」吗？**

**Amanda Askell**：我觉得如果你愿意跟模型解释它哪里出错了，有时候它确实能发现问题。不过这得看具体的任务情况。这种事情我不是特别确定它能有多大概率做对。但我还是会去试，因为有时候它真的能做到。

**David Hershey**：是啊，你能学到一些东西。所以每次你跟模型反复交流时，你都会了解一些它在做什么的情况。如果你不试试，可能会错过一些信息。

**Alex Albert**：Anthropic 有个 Slack 频道，大家通过它跟 Claude 对话，也可以看到别人写的提示词。我有一个频道，很多人关注我和 Claude 的互动。**我注意到 Amanda 经常会用模型来应对各种不同的场景，我很好奇，你是怎么培养出什么时候信任模型的直觉的？这是单纯靠使用经验，还是有其他原因？**

**Amanda Askell**：我从来不直接信任模型，我会不断地测试它。你会看到我经常这样做，因为会问：「我能信任你完成这个任务吗？」有些时候，当你稍微偏离模型的训练范围时，模型的表现会变得有点怪异，特别是当你进入它们没见过的领域或不寻常的情况时。即使是简单的任务，模型在这些情况下的可靠性也会降低。虽然随着模型的进步，这种情况变得越来越少，但你还是想确保自己不落入这些问题中。

好的提示设计可以在实验的成功和失败之间产生巨大差异。**如果你的实验代码很精细，但提示部分不花时间去优化，这对我来说是没有意义的**。提示可能是决定你实验成败的关键。

**Zack Witten**：部署时也是如此。是的。很容易就出现这种情况，哦，我们不能发布这个。然后你调整一下提示，突然它就工作了。

**David Hershey**：提示词是有点神秘的，你总觉得会有一个完美的提示在等着解决我的问题。我看到很多人陷入了这种对完美提示的幻想，觉得只要再努力一点，就能找到那个解决问题的关键。虽然你确实会从中学到东西，但提示的挑战在于，这个领域充满了未知。

**03**
------

**越调越偏，**
---------

**不如直接放弃**
----------


**Zack Witten：你们有没有什么启发式的方法来判断某件事是否可能通过完美的提示来实现？**

**Amanda Askell**：我通常会检查模型是否真正理解了任务。如果提示不能产生预期的效果，往往很快就会显现出来。如果模型显然无法完成某项任务，我不会在上面花太多时间。

**David Hershey**：你可以尝试了解模型是如何思考的，问它怎么思考以及为什么这样做。这可以帮助你判断它是否在正确的方向上。如果你感觉它在朝着正确的方向进展，即使不是完全准确，也可以稍微有些希望。**有些任务确实很难，你的每一次调整可能都让结果更加偏离目标。这种情况下，我倾向于放弃**。

**Amanda Askell**：这种情况现在很少见了，但当我遇到时，我会非常生气。因为它们真的很罕见，当模型在即使你推它向正确方向的情况下仍无法完成任务时，我会非常愤怒。

**David Hershey**：我最近做了个实验，把 Claude 连接到一个 GameBoy 模拟器上，想让它玩《宝可梦：火红》。最开始，它只是能做一些很基础的操作，比如按按钮。我试了很多复杂的提示，但还是遇到问题。有些地方就是完全做不到，特别是当需要它理解 Game Boy 屏幕的截图时。

我花了整个周末试图改进提示词，让它能更好地理解屏幕。虽然我逐渐看到了一些进展，从完全没有效果到有一点效果，但仍然不够好。最终，我觉得这可能不是最有效的方式。**与其花几个月的时间在这个问题上，不如等下一个更好的模型出来。**

**Zack Witten**：你尽力让模型理解它正处于《宝可梦》游戏中，并解释了游戏中的事物是如何被表示的。

**David Hershey**：我最后做的事情很麻烦，我在图像上叠加了一个网格，然后详细描述了网格的每个部分。接着我让它把图像重建成 ASCII 地图，尽量提供详细的信息。比如，玩家控制的角色总是在网格上的四号、五号位置之类的。这样你可以逐步积累信息。还有就是你需要告诉模型关于文本和图像的直觉其实差异很大。

**Zack Witten**：所以我觉得**提示的概念在图像和文本上的效果可能完全不同**。我不太确定，可能是因为训练数据中这种例子的确较少。

**Alex Albert**：我记得我们最初尝试多模态提示时，真的很难让它们起作用。似乎无论你怎么提示，Claude 在图像识别方面的实际视觉敏锐度都无法提高。这和你在宝可梦上的情况有点像，尽管你给它提供了很多提示，它还是无法在图像中正确识别出位置。

**David Hershey**：我大多数时候能让它识别墙和角色的位置，虽然有点偏差。但有时候，你会发现它真的无法做得更好，尤其是当它需要描述一个 NPC 时。玩游戏需要连续性意识，但如果不能识别每个 NPC 是否相同，模型基本上什么都做不了，只会继续和同个 NPC 对话，因为可能这是另一个 NPC。

尽管我尽力让它描述一个 NPC，比如说这是一个戴帽子的人，但它就是识别不出来。即使我放大到 3000 倍，只裁剪到 NPC 的部分，它还是搞不清楚。我给了它很多次机会，还是无法准确识别。这真的很令人沮丧。

**Amanda Askell**：我现在真的很想尝试这个。我在想我会怎么做。我希望你能把这些游戏中的角色想象成真实的人，然后描述给我他们是什么样子的。他们看起来怎么样？就像对着镜子看，然后看看结果如何。

**David Hershey** ：我尝试了很多方法。最后我告诉 Claude 它是一个为盲人服务的屏幕阅读器。我不确定这是否有效，但感觉是对的，所以我就坚持了这个方法。

**04**
------

**不需要角色扮演，**
------------

**和模型实话实说**
-----------


**Alex Albert**：我其实想深入讨论一下，这算是最常见的提示技巧之一，让语言模型扮演某种角色或身份。

不过我觉得这招现在的效果有点参差不齐。可能以前的模型对这个反应更好，但现在可能没那么灵光了。Amanda，我经常看到你对模型很诚实，比如直接告诉它整个情况。像是「我是个 AI 研究员，我在做这个实验。」你会告诉它你是谁，还会给它你的名字，像是「这是和你对话的人」。你觉得这种诚实的方式比起那些对模型撒谎、或者用「我会给你 500 美元小费」这种方式更好吗？还是说这只是你的直觉？

**Amanda Askell**：是的，随着模型的能力越来越强，对世界的理解越来越深入，**我觉得其实没有必要对它们撒谎**。我的意思是，我个人也不喜欢撒谎。

我觉得如果你正在构建一个机器学习系统或语言模型的评估数据集，这跟给孩子们出小测验是完全不同的事情。所以当有人和模型假装说「我是老师，我要出测验题」时，你要知道，模型知道什么是语言模型评估。你问它不同类型的评估，它甚至能给你虚构的例子，因为它了解这些内容，所以我更愿意直接针对我真正的任务去沟通。

比如说，我想让你构建的问题看起来就像是语言模型的评估，那么为什么不直接告诉它这就是我想做的事呢？为什么要假装自己要做一些不太相关的任务呢？我们也不会对同事这样做啊。我不会跟我的同事说「嘿，你是个老师，正在测试学生吗？」，我会直接说「嘿，你在做评估吗？」我觉得这是个启发，我倾向于直接让模型做我想要它做的事情，而不是绕弯子。

**Zack Witten**：但是有些时候我觉得并不完全是撒谎，更像是用比喻来解释思路。比如我试图让 Claude 判断一张图表或图像好不好，或者说它的质量高不高。我发现最有效的提示是问模型，如果这张图表作为高中作业提交，会打什么分。所以我并不是在说「你是一名高中老师」，而更像是「我希望你按照高中老师打分的标准来分析」。

**David Hershey**：这样的比喻其实不太容易想出来。大部分人还是会倾向于用默认的思维方式，你会经常看到大家找一些类似任务的仿制品，比如说你是一名老师，但其实很多时候这种做法忽略了你产品中的很多细节。

我在企业用的提示中见过太多这样的情况，大家喜欢写类似的东西，因为他们直觉上认为这样更好，可能是因为模型看过更多的内容，比如它看过的高中测验比 LLM 评估还多。这可能确实有道理，但就像你说的，随着模型变得越来越好，**我觉得更重要的是尽量具体地描述当前的场景**。我总是这样建议别人，这并不是说我觉得这些比喻完全没用，像「把图表打分就像给高中作业打分」这样的比喻也许有一定道理。但这些往往是人们喜欢用的简单化的思路，试图快速理解发生了什么，或许不适用于模型。比如我会直接告诉它，你是这款产品中的助手，代表公司在产品里与人沟通。你是产品中的那个支持聊天窗口。你是一种语言模型，而不是一个人。关键是要非常具体地描述出模型所在的使用环境。

我经常看到这种情况，因为我最担心的是大家总是用角色扮演类的提示词作为一种捷径，让模型完成某个类似的任务。而当模型没有按照预期完成任务时，他们就会感到困惑。但其实那个预设的角色根本不是你想要模型完成的任务本身。你让它去做了其他的事情。如果你没有给它提供足够详细的信息，那么你可能就漏掉了某些关键点。还是回到我们一开始说的，提示词最重要的是表达清晰准确。

**Amanda Askell**：我觉得有趣的是，我几乎从未使用过这种角色扮演的提示技巧。------即使以前是更糟糕的模型。我觉得它本质上并不太好。

我过去常常给人们这个思维实验：想象你有个任务，你雇了一个临时工机构派人来做这个任务。这个人到了，你知道他们相当能干。他们对你的行业了解很多，等等。但他们刚刚出现，对你们公司自己的情况不了解。然后和你说：「嘿，有人告诉我你们这里有份工作让我做。给我讲讲你们公司的大致情况。」然你可能会用一些比喻来解释，比如说：「我们希望你能识别出好的图表。这里的『好图表』并不意味着它得完美无缺，你也不需要确认所有细节是否正确。只要图表清晰，比如坐标轴有标记，整体没问题就行。」你可能会告诉他「想象一下高中水平的好图表」，但你不会说「你是高中生」，也不会说「你是高中老师，你在看图表。」

所以有时候，当我写一些提示词时，**我会想象对方是一个上下文很少但非常能干的人，他对世界有很多了解**。先假设这个人有一定的知识背景去尝试。如果不行，再做一些调整。但通常，我会先这么试，结果往往能奏效。

**David Hershey**：很多客户表示他们的提示不起作用，问我应该怎么修复。我就问：「你能描述一下这个任务是什么吗？」等他们跟我解释清楚之后，我建议他们：「你刚刚对我说的那些话，就像录音一样，把它转录下来，然后直接粘到提示词里。」这样做出来的效果往往比他们自己写的提示要好得多。**我觉得很多时候，人们在写提示时，其实就是在想走捷径，有点懒惰**。很多人真的就是图省事，不愿意花时间去写更具体的提示。

**Zack Witten**：我也遇到过一模一样的情况，我让他们把给我解释的话直接贴到提示词里，果然直接成功了。

**Alex Albert**：**我觉得主要是很多人都没有理解什么是提示词**。很多人看到一个输入框时，会把它当成一个谷歌搜索框，输入几个关键词。人们总是想在提示中偷懒，用一些简单的捷径，以为一两行文字就能起到很大的作用。

**David Hershey**：是的。在写提示词的时候不能依赖直觉、不能偷懒。

**Amanda Askell**：偷懒就会导致模型在很多边缘情况上犯错。比如刚刚评价表格的数据集里混进了一张山羊的图片，模型就不知道该怎么办了，这甚至不是一张图表。一张山羊的图片作为图表有多好？而如果你补充一下，比如「如果发生一些奇怪的事情，你真的不确定该怎么办，就输出：不确定」。

**Zack Witten**：而且你也通过这样做提高了你的数据质量，因为你找到了所有搞砸的例子。

**05**
------

**模型有推理，**
----------

**但不是人类的推理**
------------


**Alex Albert：你们觉得模型真的有推理能力吗？是否真的能够让模型在提供答案之前详细解释它的推理过程？**

**David Hershey**：这就是我在这个问题上挣扎的地方之一。

我通常支持拟人化，因为我认为它能帮助我们更好地理解模型的工作原理。但在这种情况下，**我觉得把模型的推理过度拟人化可能有点问题，甚至可能有害，因为它偏离了我们真正要做的事情。**比如，我们讨论的推理是否真实？这感觉像是进入了哲学领域，而不是直接解决「什么是最佳提示技术」这个问题。虽然我很乐意接受真正的哲学挑战，但实际上，我们应该关注的是模型的表现。

如果模型的结果更好，那就说明它的推理过程有效。我发现，通过构建和迭代推理过程，模型的表现确实会提高。虽然是否将这种过程称为推理或者如何分类它，可能会有不同的看法，但我只知道，这确实对模型的表现有帮助，我只在乎这个。

**Zack Witten**：一种测试方法是，去掉模型得出正确答案所依赖的所有推理，然后用一些看起来真实但导致错误答案的推理来替换它，然后看看模型是否会得出错误的答案。我是觉得是有某种程度上的「推理」的，我不确定用这个词是否合适，但是这个推导过程是有些东西存在的。

**Alex Albert**：我一时间想不起来那个例子了，但我记得出现过这种情况。模型列出了步骤，但其中一个步骤是错误的，但最后它还是得出了正确的答案。所以这种推理并不完全，我们不能真正将其拟人化为推理。

**Alex Albert：你们觉得良好的语法，标点，在提示中是必要的吗？这会影响模型进行推理吗？**

**Zack Witten**：我一般会尽量保持语法和标点正确。我觉得这并不是必须的，也不一定会有大的影响。

但我认为更重要的是要有一种对细节的关注。就像 Amanda 之前提到的，你应该对提示的细节投入像编写代码时一样的认真和爱意。写了很多代码的人对某些细节有很强烈的看法，比如制表符和空格的数量，或者不同编程语言的优劣。对于我来说，我对提示的格式也有自己坚定的看法。虽然我不能说它们是对是错，但我觉得尝试培养这种细节意识是有益的。

**Amanda Askell**：我完全不在意这些，我的提示词里面全是一大堆错别字。因为我觉得模型知道我的意思。

**我觉得如果概念表达得清晰，语法和标点问题就没那么重要了。** 我是那种更注重概念和用词的人，所以我会花很多时间去琢磨这些方面。我觉得在迭代过程中的提示词有错别字无所谓，但是我现在会在迭代到最后完成的提示词里会尽量改掉错别字。

**06**
------

**尝试做一些难的任务，**
--------------

**会有效提高 prompt 能力**
-------------------


**Alex Albert：你们有没有什么写提示词的小技巧？分享一下。**

**Zack Witten**：阅读你写的提示词，阅读模型给的输出。然后就是**多看别人写的优秀提示，多和模型沟通、尝试不同的提示词。**

**Alex Albert：你怎么知道它就是一个好提示呢？你只是看到输出的结果正确吗？**

**Zack Witten**：是的。

**Amanda Askell**：把你的提示给另一个人看可能会有帮助，尤其是那些对你的工作一无所知的人，这会很有帮助。然后也是：多看、多做。这很有帮助。

**David Hershey**：我觉得要尝试让模型做一些你认为自己做不到的事情。**最能让我学到提示技巧的，往往是在探索模型能力的极限时。**

比如说，写一封好邮件，看似简单，但实际上这过程中有很多细节需要考虑。如果你能找到一些挑战模型能力的任务，并尝试解决它们，你会发现自己学到了很多。真正的提示工程不仅仅是解决简单的任务，而是要推动模型能力的边界。即使你最终失败了，你也会获得很多关于如何使用模型的宝贵经验。所以，找一些你觉得最难的任务，尝试去完成它们，即使失败，也会从中学到很多。

**Alex Albert：这实际上是个很好的过渡。我的下一个问题正好围绕着这个主题。我最早了解提示工程的方式，主要是通过越狱和红队测试。这就像是试图找出模型的能力边界，了解它如何对不同措辞和用词做出反应，以及大量的试错。在讨论越狱时，模型内部到底发生了什么？**

**Amanda Askell**：我实际上也不太确定。很多人都在研究越狱背后的机制，比如说模型可能会遇到训练数据之外的输入分布。比如，当你越狱时使用很多 token 的长文本，这可能是在微调期间不常见的情况，这样可能会影响模型的表现。不过，我认为这是其中之一，但也有其他因素可能会影响模型。

**Alex Albert**：我记得一些最初的越狱提示，例如，尝试让模型翻译希腊语中的句子，然后直接翻译成英语。这样做时，模型不会直接用英语开始，而是用希腊语，然后就绕过了一些安全限制。这可能与模型训练中的某些机制有关。

**Amanda Askell**：对，有时越狱确实感觉像是一种奇怪的黑客行为。我认为，关键是了解系统如何运作，了解如何训练模型，以及如何利用这些信息规避模型的限制。对于多语言的情况，我们还需要考虑训练数据中的差异。总的来说，越狱不仅仅是黑客行为，它也涉及到对系统和训练过程的理解，并利用这些理解来绕过模型的限制。

**Alex Albert：我们来厘清一下企业级提示词、研究型提示词，或者仅仅是与 Claude AI 日常聊天中的提示词之间的区别。Zach? 可以为我们解释一下吗？**

**Zack Witten**：我认为对于研究来说，你更在**寻找多样性和差异性**。比如我发现 Amanda 的的提示里通常不会有什么例子，可能一两个就够了，因为模型很容易倾向于这些例子。

而在我写的，或者我见过 Daivd 写的提示词里，这个面向用户的提示词里例子会特别多。我甚至喜欢疯狂地加例子，直到觉得自己快要崩溃，因为想加进去的例子实在太多了。

这是因为在消费者应用中，**大家非常重视稳定性和一致性**。如果所有的答案都差不多，那反而是好事，你要的只是能很好地响应用户需求的答案。而在研究提示中，你更多是在探索模型的能力和潜力范围，所以太多的例子反而会限制它的表现。所以我觉得这可能是我注意到的最大区别：提示中例子的多少。

**Amanda Askell**：我就算给出示例，我也通常会尝试使示例与模型将要看到的数据不同。因为如果我给出的示例非常像它将要看到的数据，我只是认为它可能会给我一个非常一致的回应，这并不是我想要的。我并不想只是给我这种非常机械的输出。

如果我有一个任务，比如说我试图从事实文件中提取信息，我可能会给它一些听起来像儿童故事的例子。另外，我个人也不太喜欢「把话塞进模型嘴里」的方式。我不会用 few-shot learning 来让模型照搬我的示例。我觉得这种思路有点像是在依赖预训练模型的模式，而实际上现在的 RLHF 模型已经有所不同了。所以是的，我认为这些就是其中的一些区别。

**David Hershey**：我想补充一下，在进行一些日常对话的提示词迭代时，我会反复调整，直到某次结果是对的。而企业提示的情况就完全不一样了，它可能要被用上百万、上千万次，甚至上亿次。所以你在设计提示时，必须考虑得非常周全，确保它在各种输入情况下都能适用。所以对于企业提示词来说，考虑全边缘情况非常重要。

不过好的提示，在两种情况下都应该表现得很好。不管是你为自己调试，还是为企业项目设计，它们都应该达到一样的高标准。

**07**
------

**信任模型的能力，**
------------

**不要把它当小孩子**
------------


**Alex Albert：好的，我想转向另一个话题，那就是提示工程的历史。然后我会跟进一下未来的情况。在过去的三年里，提示工程发生了怎样的变化？从早期的预训练模型，到像 Claude 1 这样较为笨拙的模型，再到现在的 Claude 3.5 Sonnet，这些模型之间有什么不同？你现在与模型的对话方式有变化吗？模型对提示的注意点是否有所不同？你是否仍然需要在提示上投入同样多的工作？**

**Zack Witten**：每当我们找到一个很有效的提示工程技巧时，接下来就是要把这个技巧训练到模型里去。因此，那些最有效的小技巧总是很短暂的。

**David Hershey**：除了例子和思维链。这个一直都很有用。

**Zack Witten**：那不是一种小技巧。**思维链实际上已经训练到模型中了**。过去你必须告诉模型一步一步地思考数学问题，然后你会得到计算时巨大的提升。然后我们就想，如果我们让模型在看到数学问题时自然地想要一步一步思考会怎样？所以现在你不再需要这样做了。所以我认为很多这些技巧已经消失了，或者在它们还没有消失的时候，我们正在忙着训练让它们消失。但同时，这些模型拥有正在被解锁的新能力，它们正处于它们能做的事情的前沿。对于这些，我们还没有时间去深入探索，因为发展得太快了。

**David Hershey**：我最近开始更尊重和信任模型了。我现在觉得，我可以告诉它们更多的上下文信息。以前，我有意隐藏复杂性，担心模型会感到困惑或迷失，所以我会尽量简化任务。但是现在，**我相信模型能够处理更多的信息和背景，并将其融入到任务执行中。**之前我常常担心是否需要过滤掉一些信息，或者是否真的可以给它所有必要的信息。我不确定这是否只是我自己在提示词技巧上的变化，还是模型本身的能力真的有了变化。

**Amanda Askell**：是的，信任、诚实。

当我想让模型学习一种提示技巧时，很多人会开始描述这种技巧，而我通常会直接给它那篇相关的论文。我会告诉它：「这是关于提示技巧的论文，我想让你写出这篇论文中的 17 个例子。」然后它就会根据论文来完成任务。我觉得有时候人们没有意识到，这些论文已经存在。

另外，比如我想测试其他的大模型，我会直接告诉它我真正的目的，并要求它为我生成一些元提示词。这种方法很有效。

**David Hershey**：我经常给客户这样的建议，尊重模型的能力。很多经常有点溺爱模型，他们潜意识中说：「哦，这是个可爱的小东西，不太聪明，我需要像对待婴儿一样简化它。」但实际上，如果你把模型当作聪明的工具，它通常会表现得很好。比如，直接给它论文，而不是把论文简化成婴儿版。

**模型可以理解复杂的信息，不需要过度简化。** 这是我随着时间的推移逐渐学到的经验。

**Amanda Askell**：我发现我用来提示模型的方式可能随着时间有所不同，但基本的思路还是一样的。核心就是我会设身处地地想象自己是模型，试图理解它的能力如何随着时间变化。

我记得有人曾经嘲笑我，因为我在思考一个问题时会模拟作为预训练模型的思维方式。他们问我我认为模型的输出会是什么，我回答说：「如果我是一个预训练模型，我会这样思考。」他们就觉得很奇怪，难道我刚才是在模拟一个预训练模型的思维？我说：「是的，当然。」我已经习惯了从模型的角度去思考，进入不同的模型思维空间。

所以现在我更**倾向于直接给模型论文，因为我知道它不需要我像对待婴儿一样去简化。**模型可以直接理解复杂的机器学习论文。我可能还会问它是否需要更多的文献来更好地理解问题。这样的方法更有效。

**Zack Witten：当你试图站在模型的角度思考时，你有什么感觉？那这种感觉会根据你用的模型不同而有所变化吗？**

**Amanda Askell**：是的，预训练模型和现在的 RLHF 模型差别很大。当我试图模拟一个预训练模型的感受时，就好像我突然掉进了一段文本中。这感觉非常不像人类的体验。然后我会思考，接下来会发生什么？这个过程会怎么继续？相比之下，RLHF 模型则不同，我会注意到更多细微的差别。总体来说，我发现自己更容易进入 RLHF 模型的思维空间。

**David Hershey**：我发现更容易进入预训练模型的思维空间，不知道为什么。可能是因为 RLHF 模型比较复杂，我还没完全搞清楚我们理解了什么。所以在某种程度上，它更接近我的生活体验，更容易进入，但也有一些像未知的挑战。我对预训练模型在互联网上的表现有一定了解，虽然我不说自己完全懂，但有一定的把握。

**08**
------

**未来的模型可能会**
------------

**主动获取我们的想法**
-------------


**Alex Albert：我们聊了提示工程的过去，现在让我们来谈谈提示工程的未来。这是现在最热门的问题。我们将来都会成为提示工程师吗？那会是最后剩下的工作吗？有猜想说：未来我们除了整天和模型对话之外，什么也不剩了。还是说，将来这些模型会变得足够智能，不再需要提示词吗？**

**David Hershey**：**模型会越来越擅长理解你的意图，你需要投入的思考量可能会减少。**但信息论的角度来看，你总需要提供足够的信息来明确指定你的要求。这就是提示工程的本质，我认为它会一直存在。而且能够清晰地陈述目标始终很重要，因为即使模型在理解上下文方面变得更好，我们还是会需要能够明确预期结果的能力，这仍然需要技巧。

**Zack Witten**：我觉得未来我们会更多地利用提示工程来让模型为我们生成、调整提示词。尤其是对于那些没有太多提示工程经验的人来说，提示词生成器可以帮他们开始自己的「提示工程之旅」，我认为这是一个的重要的发展路径。

**Amanda Askell**：是的，我现在就在大量使用元提示。

关于提示工程将何去何从的问题，我认为这是一个非常难的问题。还记得之前那个例子吗？我觉得未来会像是那些请来的临时工会转变为更熟悉各种边缘情况的专业外包团队。至于提示工程是否会消失，我觉得对于一些领域如果模型做得足够好，还真有可能------它们能从你的大脑中提取信息，然后完成任务，那确实可能会发生这种情况。

**Alex Albert**：从你们的回答中，我看到未来的趋势可能是，**从用户那里提取信息将变得更加重要**。企业方面，这可能会变成提示生成的扩展，能够从客户那里获得更多信息，以便编写更好的提示。在云服务中，这可能不仅仅是文本框中的输入，而是更多的互动式引导。

**Zack Witten**：我觉得现在的提示有点像教学，你试图理解学生的思维方式，帮助他们清晰表达。而未来的提示可能更像是一种自省，模型会尝试理解你，理解你真正在思考什么、需要什么，而不是你去教它。

**Amanda Askell**：现在我在写提示词的时候，会用类似哲学家的方法来定义新概念。比如，我会用语言来表达我想要的东西，有时候这些要求很微妙，比如什么样的图表算好，或者在什么情况下我们应该判断某事对或错。我经常会发明一个概念，然后让 Claude 理解这个概念，总之我在试图把我脑中的想法传达给模型。

目前的模型不会主动去做这些，除非我们给它们提示。所以，**将来可能模型会直接从我们那里提取信息，而不是我们去为它们提供所有这些信息**。哲学在提示中的应用很有趣。我觉得哲学写作的风格很有帮助，因为它教我如何把复杂的想法变得简单明了，甚至让受过教育但对某个话题不了解的人也能理解。虽然不是每篇论文都能做到这一点，但这是我们在哲学写作中追求的目标。

**我习惯于把复杂的概念用简单的语言表达出来，这种方式也适用于提示工程** 。就像我以前对学生说的那样，如果他们写的论文我不理解，我会让他们解释一下他们的观点，然后让他们把解释整理成一篇文章。这种方法也适用于未来的提示工程，所以这种提示工程和人脑的工作很像------**从你的大脑中提取信息，充分理解它们，然后随便从大街上找一个受过良好教育的聪明人，把你大脑中的理解外化到他身上。**我觉得这就是提示词的核心。

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FqpAK9iaV2O3uZFIyK9yAG4nfYwqxWDcqRiabAZSMtMqSEicDc5qzCRs8Zmr9tYpqEoXyJQv9I3jX3l05Q22AAJqdw%2F640%3Fwx_fmt%3Dother)

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fsz_mmbiz_png%2FqpAK9iaV2O3sr5DM1ZXfrwBYuMUEd2y2aH7VgPwhRY5NVve78Io8WiaPEX9JsG2deNfmcfFZ6uRgq4EG8JpntdAg%2F640%3Fwx_fmt%3Dpng%26from%3Dappmsg)](http://mp.weixin.qq.com/s?__biz=Mzg5NTc0MjgwMw==&mid=2247507499&idx=1&sn=06f2cf36a3412f6d82b5acd8b5a9d24d&chksm=c0093817f77eb101b1a182a116dac9ac0f513c17585a915fbcf639407cd1a12df9c77c81b2f8&scene=21#wechat_redirect)


*** ** * ** ***

**更多阅读**


[8月份AI应用月活盘点，离超级应用有多远？ChatGPT还有机会吗？](http://mp.weixin.qq.com/s?__biz=Mzg5NTc0MjgwMw==&mid=2247508147&idx=1&sn=8e7321b2c2635b4db220e5fbcdbbb062&chksm=c009468ff77ecf99515a06cf0798d33df300fa4cc029089df6556088b0e5e1059151a39f4693&scene=21#wechat_redirect)   


[OpenAI o1是AGI下半场的开始，强化学习将成为新的 Scaling Law](http://mp.weixin.qq.com/s?__biz=Mzg5NTc0MjgwMw==&mid=2247508141&idx=1&sn=d952ee3baf2beb2b6443af7303a1bde0&chksm=c0094691f77ecf8780b1b13ebf3a598a81640a26101bd0f60f58d904a436eaabd2262b0f557b&scene=21#wechat_redirect)   


[OpenAI o1 团队在线答疑：o1的o指OpenAI，强化后的推理有泛化能力，未来模型思考时间可控！](http://mp.weixin.qq.com/s?__biz=Mzg5NTc0MjgwMw==&mid=2247507881&idx=1&sn=2d8fa20dfb6253e06eae3834e383cdae&chksm=c0093995f77eb08307c1e8de1984ccdbb0632326d17c1581f18f00049337cea64c449ac95fd8&scene=21#wechat_redirect)   


[AI创业者李博杰：小公司也能做RL，过几个月可能出现o1开源平替](http://mp.weixin.qq.com/s?__biz=Mzg5NTc0MjgwMw==&mid=2247507881&idx=2&sn=d8d3a3abc4588138a5740b4ec8147790&chksm=c0093995f77eb083401230c46d05c982acb5514fc9f64294e5c047b668d2a12168fa21b91a49&scene=21#wechat_redirect)

![](https://image.cubox.pro/cardImg/49ptyqcouzc9s3xbvbkji7igwiujtno1uzwe4pm8wftkt6j5kq?imageMogr2/quality/90/ignore-error/1)

**Founder Park**

来自极客公园，专注与科技创业者聊「真问题」。

302篇原创内容

公众号

，

转载原创文章请添加微信：founderparker

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7236270858514206716)
