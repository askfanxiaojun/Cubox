AI绘画教程：如何用Stable Diffusion始终画同一个人？
==================================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/619730103)AIGC部落

AI绘画每次生成图片的时候，都是随机的，也就是如果我想画三幅画：一个女孩在跑、一个女孩在读书、一个女孩在吃饭，三张图片中的女孩相貌是不一样的。如果我们想画同一个人在跑、在读书、在吃饭的多张照片，该怎么办呢？

这个时候，我们就需要让AI识别出这个女孩的相貌特征，记住她，然后以后每次生成图片的时候，就可以保持是同一个人了，如下图的效果。这个过程就叫做Stable Diffusion的模型训练。
![](https://image.cubox.pro/article/2023072400591420619/37676.jpg?imageMogr2/quality/90/ignore-error/1)

要训练一个模型，我们得首选有一些图片。准备大概35张-50张左右就可以了，注意图片中要有人物的不同侧面、不同姿势，不能太单一，背景最好比较单纯，然后要有较多的大头照，这样AI才能容易识别出人像的特征。
![](https://image.cubox.pro/article/2023072400591468641/72289.jpg?imageMogr2/quality/90/ignore-error/1)

图片准备好之后，要调整成 512×512的尺寸，可以用一些图像处理软件。这里推荐一个免费网站，处理起来很方便：[https://www.birme.net/?target_width=512\&target_height=512](https://link.zhihu.com/?target=https%3A//www.birme.net/%3Ftarget_width%3D512%26target_height%3D512)
![](https://image.cubox.pro/article/2023072400591433038/26577.jpg?imageMogr2/quality/90/ignore-error/1)

点击：browse from your computer,上传图片，很快就自动处理好了，然后点击右下角的"save as zip"，就保存到本地电脑了，解压缩zip文件就OK了。

然后在谷歌硬盘中新建一个文件夹，比如littlexixi_training,然后把刚才的图片上传到这个文件夹。
![](https://image.cubox.pro/article/2023072400591478314/72266.jpg?imageMogr2/quality/90/ignore-error/1)

接下来打开Stable Diffusion的在线DreamBooth模型训练程序：[https://colab.research.google.com/github/sagiodev/stablediffusion_webui/blob/master/DreamBooth_Stable_Diffusion_SDA.ipynb](https://link.zhihu.com/?target=https%3A//colab.research.google.com/github/sagiodev/stablediffusion_webui/blob/master/DreamBooth_Stable_Diffusion_SDA.ipynb)

这个程序已经配置好了，训练起来的操作非常简单，而且是在谷歌Colab虚拟计算机中进行在线训练，完全不需要本地电脑有多高的配置。

打开这个程序后，先进行一个设置：

Instance_prompt:训练的一个特定人物，只要提示词中包括这个词语，就按照这个模型出图。比如我训练的是一个小女孩，名字叫xixi girl;

Class_prompt:训练的一个特定类别,比如女孩，girl
![](https://image.cubox.pro/article/2023072400591472974/21227.jpg?imageMogr2/quality/90/ignore-error/1)

照例会连接谷歌硬盘drive，点击同意就可以了。
![](https://image.cubox.pro/article/2023072400591472173/29542.jpg?imageMogr2/quality/90/ignore-error/1)

然后，到上传图片的环节，出现"choose files"的按钮，把刚才谷歌硬盘文件夹littlexixi_training里面的照片选中
![](https://image.cubox.pro/article/2023072400591447993/78669.jpg?imageMogr2/quality/90/ignore-error/1)

然后开始准备这些图片作为训练模型用的数据
![](https://image.cubox.pro/article/2023072400591484503/47113.jpg?imageMogr2/quality/90/ignore-error/1)

然后就开始正式进入训练模型的环节了。训练时长通常是30分钟左右，需耐心等待。不要离开这个页面，也不要离开电脑。因为谷歌colab会自动检测人是否在电脑前，万一离开可能colab程序就会中断，导致训练过程终止。
![](https://image.cubox.pro/article/2023072400591482375/23988.jpg?imageMogr2/quality/90/ignore-error/1)

当出现Dreambooth completed successfully.字样，说明训练完成，下面会出现几张训练好的图片。
![](https://image.cubox.pro/article/2023072400591499768/51445.jpg?imageMogr2/quality/90/ignore-error/1)

训练好的模型会保存在谷歌硬盘的dreambooth_model文件夹里面。
![](https://image.cubox.pro/article/2023072400591493217/86883.jpg?imageMogr2/quality/90/ignore-error/1)

接下来可以对模型进行测试，比如输入：oil painting of xixigirl in style of van gogh
![](https://image.cubox.pro/article/2023072400591415058/84806.jpg?imageMogr2/quality/90/ignore-error/1)

出现一个梵高画风格的xixi girl，说明训练成功。

在stable diffusion中怎么使用这个模型呢？

打开"Stable Diffusion WebUl Colab TW.ipynb"的colab包：
![](https://image.cubox.pro/article/2023072400591410008/81051.jpg?imageMogr2/quality/90/ignore-error/1)

在第2步骤：下载模型，下载SD模型里面，有一个"其他sd模型下载网址"，填入/content/dirve/MyDrive/Dreambooth_model/model.ckpt，就可以把刚才训练生产的模型安装到colab包里面。

接下来运行这个colab程序，成功后进入stable diffusion界面

在提示词框里面输入： a female child,xixigirl,reading book in the library
![](https://image.cubox.pro/article/2023072400591454942/79360.jpg?imageMogr2/quality/90/ignore-error/1)

可以看到效果了。

再加一些负面词

missing eyes or ears, exaggerated features, asymmetrical features, discolored skin, missing digits, mangled or misshapen fingers, scars, burns, amputated arms or legs, severed hands or feet, twisted or broken bones, oozing wounds, festering sores, gangrene, infected teeth or gums, protruding bones, sunken eyes, hollow cheeks, visible ribs, animal features, tentacles, extra limbs, grafted skin or tissue, wrinkles, age spots, sagging skin, yellowed teeth, thinning hair, cysts, warts, tumors, growths, lesions, elongated limbs, twisted spines, hunched backs, misshapen heads

效果更棒：
![](https://image.cubox.pro/article/2023072400591418816/29975.jpg?imageMogr2/quality/90/ignore-error/1)

挑选喜欢的图片，后续再进行一些精修，就可以出图了。

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7082836929808434164)
