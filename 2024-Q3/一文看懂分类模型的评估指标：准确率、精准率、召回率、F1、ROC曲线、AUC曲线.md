一文看懂分类模型的评估指标：准确率、精准率、召回率、F1、ROC曲线、AUC曲线
========================================

[mp.weixin.qq.com](https://mp.weixin.qq.com/s/h8z8bvoVNauOmGZHtbzMHQ)easyAI 中科北纬


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyiccuWeick2fEAOZ7iaXpPazfkKfomyhvdg06gKlIuZaf6Xsu6via7icWHJUA%2F640%3Fwx_fmt%3Dpng)


**"**


机器学习模型需要有量化的评估指标来评估哪些模型的效果更好。

本文将用通俗易懂的方式讲解分类问题的混淆矩阵和各种评估指标的计算公式。将要给大家介绍的评估指标有：准确率、精准率、召回率、F1、ROC曲线、AUC曲线。


***机器学习评估指标大全***


所有事情都需要评估好坏，尤其是量化的评估指标。


* 高考成绩用来评估学生的学习能力

* 杠铃的重量用来评估肌肉的力量

* 跑分用来评估手机的综合性能


机器学习有很多评估的指标。有了这些指标我们就横向的比较哪些模型的表现更好。我们先从整体上来看看主流的评估指标都有哪些：


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicAAb1ZqGACsOIJbTx9rlNsWZhVUZJCKVfdE22Bna17ezSKU3H03IqFQ%2F640%3Fwx_fmt%3Dpng)

分类问题评估指标：


1. 准确率 -- Accuracy

2. 精确率（差准率）- Precision

3. 召回率（查全率）- Recall

4. F1分数

5. ROC曲线

6. AUC曲线


回归问题评估指标：


1. MAE

2. MSE


***分类问题图解***


为了方便大家理解各项指标的计算方式，我们用具体的例子将分类问题进行图解，帮助大家快速理解分类中出现的各种情况。


举个例子：


我们有10张照片，5张男性、5张女性。如下图：


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicTB4haZlxeIAJ90kgWPp1BH5zHsvlWfz8HhuB62nrMbw8MYX1dWoIIg%2F640%3Fwx_fmt%3Dpng)

有一个判断性别的机器学习模型，当我们使用它来判断「是否为男性」时，会出现4种情况。如下图：


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyic0tyQtAv0QyXhAlN98RcdBYibEhJ0Hz7PicyI2pzx1rWbrPmckQLgLu0w%2F640%3Fwx_fmt%3Dpng)

1. 实际为男性，且判断为男性（正确）

2. 实际为男性，但判断为女性（错误）

3. 实际为女性，且判断为女性（正确）

4. 实际为女性，但判断为男性（错误）


这4种情况构成了经典的混淆矩阵，如下图：


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicBBWvkbwOrKmLEIKeq7yrSN2CnxugOd11UYETkYcYmRkqkmFuLdrglA%2F640%3Fwx_fmt%3Dpng)

TP -- True Positive：实际为男性，且判断为男性（正确）

FN -- False Negative：实际为男性，但判断为女性（错误）

TN -- True Negative：实际为女性，且判断为女性（正确）

FP -- False Positive：实际为女性，但判断为男性（错误）


这4个名词初看起来比较晕（尤其是缩写），但是当我们把英文拆分时就很容易理解了，如下图：


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyic11ABdk3O31iaF9xL1M5KcWD62xiblxGLTVjMfELhbUNy4936Rf64GpzA%2F640%3Fwx_fmt%3Dpng)

所有的评估指标都是围绕上面4种情况来计算的，所以理解上面4种情况是基础！


***分类评估指标详解***


下面详细介绍一下分类分为种的各种评估指标详情和计算公式：


准确率 -- Accuracy


预测正确的结果占总样本的百分比，公式如下：


**准确率 =(TP+TN)/(TP+TN+FP+FN)**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyic1WdnTmv3Nqxh5IjlGyibnmiau3AHaAP1yHkGsDDSC43771sYMO3jUf5g%2F640%3Fwx_fmt%3Dpng)


**"**


虽然准确率可以判断总的正确率，但是在**样本不平衡** 的情况下，并不能作为很好的指标来衡量结果。举个简单的例子，比如在一个总样本中，正样本占 90%，负样本占 10%，样本是严重不平衡的。对于这种情况，我们只需要将全部样本预测为正样本即可得到 90% 的高准确率，但实际上我们并没有很用心的分类，只是随便无脑一分而已。这就说明了：**由于样本不平衡的问题，导致了得到的高准确率结果含有很大的水分。即如果样本不平衡，准确率就会失效。**


精确率（差准率）- Precision


所有被预测为正的样本中实际为正的样本的概率，公式如下：


**精准率 =TP/(TP+FP)**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicvOLicx3UsCJicPZzyFgMeIic8q9tK3xrFRCbCx7gGwepPefG0MGuI7HhA%2F640%3Fwx_fmt%3Dpng)


**"**


精准率和准确率看上去有些类似，但是完全不同的两个概念。精准率代表对正样本结果中的预测准确程度，而准确率则代表整体的预测准确程度，既包括正样本，也包括负样本。


召回率（查全率）- Recall


实际为正的样本中被预测为正样本的概率，其公式如下：


**召回率=TP/(TP+FN)**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicYkIib7GHPFC275oCSyA7WmYQp1tJHIXyBUVZAS6KIrWbsaDD1BlGRKA%2F640%3Fwx_fmt%3Dpng)


**"**


**召回率的应用场景：** 比如拿网贷违约率为例，相对好用户，我们更关心坏用户，不能错放过任何一个坏用户。因为如果我们过多的将坏用户当成好用户，这样后续可能发生的违约金额会远超过好用户偿还的借贷利息金额，造成严重偿失。**召回率越高，代表实际坏用户被预测出来的概率越高，它的含义类似：宁可错杀一千，绝不放过一个。**


F1分数


如果我们把精确率（Precision）和召回率（Recall）之间的关系用图来表达，就是下面的PR曲线：


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicVvdn2sHf98gL4Ib5qGibspB49Lu0OuNBREsfiaYFRbAVobWDJHPbtaKQ%2F640%3Fwx_fmt%3Dpng)

可以发现他们俩的关系是「两难全」的关系。为了综合两者的表现，在两者之间找一个平衡点，就出现了一个 F1分数。


**F1=(2×Precision×Recall)/（Precision+Recall）**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicR2oSxetMqUSlYnM9J4ogtXTuLYAicXpjXIgAG11CHb6LMKIYibulRx0A%2F640%3Fwx_fmt%3Dpng)

ROC曲线、AUC曲线


ROC 和 AUC 是2个更加复杂的评估指标，下面这篇文章已经很详细的解释了，这里直接引用这篇文章的部分内容。


上面的指标说明也是出自这篇文章：《一文让你彻底理解准确率，精准率，召回率，真正率，假正率，ROC/AUC》


**1. 灵敏度，特异度，真正率，假正率**


在正式介绍 ROC/AUC 之前，我们还要再介绍两个指标，**这两个指标的选择也正是 ROC 和 AUC 可以无视样本不平衡的原因。** 这两个指标分别是：**灵敏度和（1- 特异度），也叫做真正率（TPR）和假正率（FPR）。**


灵敏度（Sensitivity） =**TP/(TP+FN)**

特异度（Specificity） =**TN/(FP+TN)**


其实我们可以发现灵敏度和召回率是一模一样的，只是名字换了而已。

由于我们比较关心正样本，所以需要查看有多少负样本被错误地预测为正样本，所以使用（1- 特异度），而不是特异度。


真正率（TPR） = 灵敏度 =**TP/(TP+FN)**

假正率（FPR） = 1- 特异度 =**FP/(FP+TN)**


下面是真正率和假正率的示意，我们发现**TPR 和 FPR 分别是基于实际表现 1 和 0 出发的，也就是说它们分别在实际的正样本和负样本中来观察相关概率问题。** 正因为如此，所以无论样本是否平衡，都不会被影响。还是拿之前的例子，总样本中，90% 是正样本，10% 是负样本。我们知道用准确率是有水分的，但是用 TPR 和 FPR 不一样。这里，TPR 只关注 90% 正样本中有多少是被真正覆盖的，而与那 10% 毫无关系，同理，FPR 只关注 10% 负样本中有多少是被错误覆盖的，也与那 90% 毫无关系，所以可以看出：**如果我们从实际表现的各个结果角度出发，就可以避免样本不平衡的问题了，这也是为什么选用 TPR 和 FPR 作为 ROC/AUC 的指标的原因。**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyic5DRnkibJdwFlYFfDDKVXeRaBOIOybicGxXvSdBeONu9f4gJfOaKDMkOw%2F640%3Fwx_fmt%3Dpng)

或者我们也可以从另一个角度考虑：条件概率。我们假设X为预测值，Y为真实值。那么就可以将这些指标按条件概率表示：


**精准率 = P（Y=1 \| X=1）**

**召回率 = 灵敏度 = P（X=1 \| Y=1）**

**特异度 = P（X=0 \| Y=0）**


从上面三个公式看到：**如果我们先以实际结果为条件（召回率，特异度），那么就只需考虑一种样本，而先以预测值为条件（精准率），那么我们需要同时考虑正样本和负样本。所以先以实际结果为条件的指标都不受样本不平衡的影响，相反以预测结果为条件的就会受到影响。**


**2. ROC（接受者操作特征曲线）**


**"**


ROC(Receiver Operating Characteristic)曲线，又称接受者操作特征曲线。该曲线最早应用于雷达信号检测领域，用于区分信号与噪声。后来人们将其用于评价模型的预测能力，ROC 曲线是基于混淆矩阵得出的。


ROC 曲线中的主要两个指标就是真正率和假正率，上面也解释了这么选择的好处所在。其中横坐标为假正率（FPR），纵坐标为真正率（TPR），下面就是一个标准的 ROC 曲线图。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicWBTfiaf6qJaTOrNrtTxZ3W1zTKlibsibShVEvRRuejFMzK0a9iak9XTibvg%2F640%3Fwx_fmt%3Dpng)

**ROC 曲线的阈值问题**


与前面的 P-R 曲线类似，ROC 曲线也是通过遍历所有阈值来绘制整条曲线的。如果我们不断的遍历所有阈值，预测的正样本和负样本是在不断变化的，相应的在 ROC 曲线图中也会沿着曲线滑动。


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicOwKoOYspURBJMbvAZfdNUvaPutXXO9ictFmWp1ldR4d4QzEBmuFOhdQ%2F640%3Fwx_fmt%3Dgif)

**如何判断 ROC 曲线的好坏？**


改变阈值只是不断地改变预测的正负样本数，即 TPR 和 FPR，但是曲线本身是不会变的。那么如何判断一个模型的 ROC 曲线是好的呢？这个还是要回归到我们的目的：FPR 表示模型虚报的响应程度，而 TPR 表示模型预测响应的覆盖程度。我们所希望的当然是：虚报的越少越好，覆盖的越多越好。所以总结一下就是**TPR 越高，同时 FPR 越低（即 ROC 曲线越陡），那么模型的性能就越好。**参考如下：


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicBfth2sEbMCIibc5dnGoyuzF76C2iaTjict1IXlEZZscowwLS8YgxMJsNQ%2F640%3Fwx_fmt%3Dgif)

**ROC 曲线无视样本不平衡**


前面已经对 ROC 曲线为什么可以无视样本不平衡做了解释，下面我们用动态图的形式再次展示一下它是如何工作的。我们发现：**无论红蓝色样本比例如何改变，ROC 曲线都没有影响。**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicsxMw1kTIO7LQVPyHeoibLHz24GSo3TMJiaPb4MTGgWvkmHOaHIWSMoOg%2F640%3Fwx_fmt%3Dgif)

**3. AUC（曲线下的面积）**


为了计算 ROC 曲线上的点，我们可以使用不同的分类阈值多次评估逻辑回归模型，但这样做效率非常低。幸运的是，有一种基于排序的高效算法可以为我们提供此类信息，这种算法称为**曲线下面积（Area Under Curve）。**

比较有意思的是，如果我们连接对角线，它的面积正好是 0.5。对角线的实际含义是：**随机判断响应与不响应，正负样本覆盖率应该都是 50%，表示随机效果**。ROC 曲线越陡越好，所以理想值就是 1，一个正方形，而最差的随机判断都有 0.5，所以一般 AUC 的值是介于 0.5 到 1 之间的。


**AUC 的一般判断标准**

**0.5 -- 0.7：** 效果较低，但用于预测股票已经很不错了

**0.7 -- 0.85：** 效果一般

**0.85 -- 0.95：** 效果很好

**0.95 -- 1：** 效果非常好，但一般不太可能

**AUC 的物理意义**


**"**


曲线下面积对所有可能的分类阈值的效果进行综合衡量。曲线下面积的一种解读方式是看作模型将某个随机正类别样本排列在某个随机负类别样本之上的概率。以下面的样本为例，逻辑回归预测从左到右以升序排列：


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9ZVibfKibHyslkzJnL2A5ZUyicKS6M1FAkwqlCPTE9T9jQ2d7GjZlTYlKeCzcLBr0BQBEYf8weM5wibZQ%2F640%3Fwx_fmt%3Dpng)


END  

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_gif%2FLjib4So7yuWiaW4x6oIKgkCz54emrkwTzUk5fj346Z4XDnmOMibOWVWSgSdG5zwbeYDUIc2WuLm8ia6bqePLFAMZwQ%2F640%3Fwx_fmt%3Dgif)


**中科北纬**


中科北纬（北京）科技有限公司，是一家集应用软件研发、技术服务于一体的科技创新型企业，也是测绘地理信息全产业链的解决方案提供商。

公司是国家和中关村双高新企业、双软认证企业，具有测绘、土地规划、林业调查规划等资质，拥有多项专利和十余项软件知识产权，已通过质量管理体系和企业信用3A等级认证，并连续多年获得测绘百强商家称号。

公司长期专注于国产地理信息类软件的研发与推广，银河点点通点云处理平台、悟空调查软件等产品在各省市测绘、国土、林业等相关部门得到广泛应用。现阶段，公司依托大数据、云计算、深度学习等技术，自主研发了遥感智能视觉平台，对变化特征及多种地类等目标信息进行智能解译，可实现"快速、准确、灵活"的数据处理和发布任务，满足自然资源、农业监测、环境监测等领域对遥感信息提取的需求。

**企业理念：诚信敬业发展共赢**

**企业使命：整合地信前沿技术提供行业精细服务**


![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fmmbiz.qpic.cn%2Fmmbiz_png%2FWxycGpN8c9YVrhJAribRCMA3pAOR7ozh2fKxtGcfsNQibtiau3GickStJz8uISM6xbKejLIKYoHAibpk5oZGRq5g9tw%2F640%3Fwx_fmt%3Djpeg)

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7218511812658990538)
