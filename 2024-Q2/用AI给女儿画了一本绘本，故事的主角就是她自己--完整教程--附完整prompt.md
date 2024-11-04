用AI给女儿画了一本绘本，故事的主角就是她自己--完整教程--附完整prompt
========================================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/690704394)小耸应用电子高级工程师证书持证人

给AI女儿画一本绘本的想法产生很久了，之前也做过一些尝试。但是在Midjourney v6之前，画出的绘本效果一直不能让我满意。主要是角色一致性的调校很困难，比如第一幅图中的女孩和第二幅图中的女孩长得不一样。

在Midjourney v6版本引入--cref和--sref参数后，保持画面一致性便利了许多。

这个小假期终于把它付诸实践。以下记录生成这个绘本的完整过程。

1. Midjourney生成主角参考图
--------------------

基于某张照片生成主角参考图，这张图片，会在后续的绘图中不断引用，用于保持不同画面间主角的一致性。生成的图片要求：背景干净，最好是纯色（提示词中，加入"pure background"），普通站姿，不要有过份夸张的动作。

我用的prompt：

    [原始照片url] a 3-year-old cute Chinese girl in a red one-piece dress, full length portrait, pure background, children's story book illustration, picture book style, --chaos 20

2. Chatgpt生成绘本故事
----------------

这步简单，让chatgpt帮你生成故事就好，如果不满意，可以让它修改指定的部分。

chatgpt参考提示词：

    请你扮演一个儿童绘本作家，并且精通用midjourney生成图画的方法。请你写一个适合于3岁女孩的儿童绘本故事。请分画面撰写，每幅画面中，都包含"插画描述"和"旁白文本"两部分。

    请你改写第6页之后的部分，让故事更加曲折一些。

3. 请Chatgpt将绘本故事转为midjourney画图提示词
---------------------------------

我用的ChatGPT提示词：

    请把每一页的插画描述，转译为midjourney prompt，以英文撰写。

这步实测，chatgpt还没有想象中的聪明，生成的提示不能直接满足midjourney的绘图要求。需要我大量的修正。（可能是我使用方式不对，大神们可以指导一下）

这步由chatgpt生成的midjourney prompt的几个问题是：

* chatgpt把很多对绘图无关的信息纳入到提示词中。例如：Chatgpt给出的midjourney提示词之一是："A girl creatively arranging colorful flowers on the ground to form a large rainbow in celebration of the moment."。这句中，"creatively"和"in celebration of the moment"对Midjourney而言都是无效信息。对Midjourney而言，如果想要精确地控制图片的输出，只需要直接告诉它"要画什么"，而不必告诉它"画这个表达了什么"
* 没有带上画面风格相关的提示词和参数。这对Midjourney绘图很关键。

4. 使用绘本提示词绘图
------------

根据第3步给出的参考，修订，准备好midjourney提示词喂给它。

midjourney在当前版本之前，最被人诟病的就是不易保持画面的一致性（比如，第一幅图的女孩和第二幅画的女孩长得不一样）。在v6版本引入--cref和--sref参数后，保持画面一致性便利了许多。

一些保持风格一致的小技巧：

1. 所有画面，使用统一的风格相关提示词，这是我用的风格提示词："colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A heartwarming children's book illustration."。在每幅画面的提示词中，都加入这段。
2. 使用--cref参数来保持角色的一致性，所有画面的的--cref参数，都引用由第一步生成的那幅主角参考图。
3. 使用--sref参数来保持画面质感的连续性，可以将上一幅画面的输出，作为下一幅画面的--sref参数输入。
4. 多尝试。不要高估你的表达能力和MJ的理解能力。在我的这些绘本画中，画得最快的一幅，也经过了4次的提示词调整才画出满意的画面，最多的一幅，试了20组左右的提示词。

成果
---

来看看成果吧：
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic1.zhimg.com%2Fv2-14eb9d9c219ead4c2f977415e3b1ae00_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic3.zhimg.com%2Fv2-3ea04a29f2d4df17c7ba3d1f1093eb0a_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic4.zhimg.com%2Fv2-9536811fbe897ccc6d45de504ddfcc2b_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic2.zhimg.com%2Fv2-15bc26f3c39b07fd8419fc6ab0bd2815_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic2.zhimg.com%2Fv2-ee51493849fcb781570956bd49d632c9_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic3.zhimg.com%2Fv2-0e0f1cabe0e6b14cbb5642839b1cd776_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic2.zhimg.com%2Fv2-979ce7d97f78ea6a6ffb321b0905b541_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic4.zhimg.com%2Fv2-106d50f358aee4acc261d93c3a17b80f_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic2.zhimg.com%2Fv2-e04c89157445e9ea74c2d5dc72848ee5_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic3.zhimg.com%2Fv2-ef38b102e558b8948612a1684f288aca_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic1.zhimg.com%2Fv2-c8fdd918c0af27cbe627051dd2ee7624_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic1.zhimg.com%2Fv2-16e73122667f7d0af89718dca3f362e8_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic2.zhimg.com%2Fv2-5155ac932f030876bab92bec98a14f79_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic1.zhimg.com%2Fv2-84088208fed95abb12c2c2c04b5da3d0_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic4.zhimg.com%2Fv2-426a0fe78f90063d7ff13648917c95e3_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic2.zhimg.com%2Fv2-83164f79bfb25dbfed0f19823c50c609_b.jpg&valid=true)
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic1.zhimg.com%2Fv2-9b1b6582a40a3bae5403e9e9e0093ebc_b.jpg&valid=true)

Midjourney Prompt
-----------------

以下把我用到的完整prompt开放给大家参考：

主角参考图：

    [主角照片url] a 3-year-old cute Chinese girl in a red one-piece dress, full length portrait, children's story book illustration, picture book style, --chaos 20 

图1

    A joyful three-year-old girl surrounded by colorful balloons and toys in her room, with sparkling eyes full of imagination. ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A heartwarming children's book illustration. --cref [主角参考图url] --cw 50 --chaos 30

图2

    [网络上找的一张喜欢的风格的照片的url] A little girl stepping out of her house to the yard with trees and flowers, The sun is shining brightly. colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A heartwarming children's book illustration. --cref [主角参考图url] --cw 50 --chaos 50 

图3

    [图2 url] a curious girl observing dew drops closely, the dew drops shining in the sun. colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A heartwarming children's book illustration. --cref [主角参考图url] --cw 10 --chaos 20 --v 6.0

图4

    [图3 url] A curious little girl touching a dewdrop on a leaf, imagining it turning into a miniature rainbow. Rainbow is clearly painted in the picture. colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A heartwarming children's book illustration. --cref [主角参考图url] --cw 10 --chaos 40 --v 6.0

图5

    [图4 url] A girl running following a butterfly through the garden as dark clouds gather and the wind starts to pick up, signaling an approaching storm. colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A children's book illustration. --cref [主角参考图url] --cw 30 --chaos 40 --v 6.0

图6

    In heavy rain, some kittens, puppies and a littyle girl, are running at full speed, looking for shelter in the garden, dark clouds gather and the wind starts to pick up. colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A children's book illustration. --cref [主角参考图url] --cw 20 --sref [图5 url] --chaos 40 --v 6.0 --no house

图7

    a little girl, some kittens and puppies curl up to get sheltered from a tree hole, they are sad. it is rainy outside, the view from the tree hole inside out. colored ink drawing, A children's book illustration. --chaos 40 --v 6.0 --cref [主角参考图url] --cw 10 --sref [图6 url] --sw 50

图8

    a little girl and some kittens, puppies, are running out of a flooding tree hollow, determination on their faces, rainy and adventurous setting. colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A children's book illustration. --chaos 40 --v 6.0 --cref [主角参考图url] --cw 30 --sref [图7url]

图9

    a little girl and some kittens, puppies are rushing to the eaves of a cabin, in heavy rain, behind view, colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A children's book illustration. --chaos 40 --v 6.0 --cref [主角参考图url] --cw 20 --sref [图8 url]

图10

    a little girl, and some kittens and puppies are standing inside the window of a cottage, looking up at a cloudy sky, colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A heartwarming children's book illustration. --chaos 40 --v 6.0 --cref [主角参考图url]  --cw 20 --sref [图5 url]

图11

    Sun breaking through clouds, a magnificent rainbow appear in the sky after the rain. colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A heartwarming children's book illustration. --chaos 20 --v 6.0 --sref [图2 url]

图12

    a little girl, some kittens and puppies are standing at the doorway of a cottage, looking up at a rainbow with surprise and admiration, behind view. colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A heartwarming children's book illustration. --chaos 40 --v 6.0 --cref [主角参考图url] --cw 20 --sref [图11 url]

图13

    A little girl, some kittens and puppies are running on a rainbow, colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A children's book illustration. --chaos 30 --v 6.0 --cref [主角参考图 url] --cw 50 --sref [图11 url]

图14

    A little girl, some kittens and puppies are sitting on ground, they are a little sad,  colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A children's book illustration. --chaos 30 --v 6.0 --cref [主角参考图url] --cw 50 --sref [图16 url (是的，我先画的图16，后画的图14)]

图15

    One picture shows a little girl with a dialogue box painted on her head to express her thoughts, and inside the dialogue box is a small rainbow. colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A children's book illustration. --chaos 30 --v 6.0 --cref [主角参考图 url] --cw 50 --sref [图1 url]

图16

     A girl is arranging colorful stones in the shape of a rainbow on the ground. some kittens and puppies are sitting beside her. the view from above. the girl is quite small compared to the on-ground rainbow. colored ink drawing, giving the scene a magical, dreamlike, and engaging atmosphere, A children's book illustration. --chaos 30 --v 6.0 --cref [主角参考图 url] --cw 20 --sref [图11 url] --sw 50

最后以附送一张Midjourney犯傻的图：
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic1.zhimg.com%2Fv2-3aa0af774100bf227f9f6ceec4cbdda0_b.jpg&valid=true)

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7177557834882616522)
