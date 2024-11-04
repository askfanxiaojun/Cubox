AIGC(3)：无限次数！轻松训练stable-diffusion生成精美图片
=======================================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/613483110)刘白做一个践行者，去接近那个狂妄自大的美梦

目录

收起

前言：

1. 安装Python

版本号最好是：3.10.6，否则更容易报错

2. 安装git

3. git clone stable-diffusion-webui

4. 下载模型

768-v-ema.yaml

结果：

5. 修改bat 脚本：

6. 修改GPU超时设置

8. stable-diffusion-webui

9. 参考资料

上一篇：

[刘白：让ChatGPT更聪明：使用Prompts进行语言模型优化24 赞同 · 5 评论文章![](https://image.cubox.pro/article/2023040610331289306/22313.jpg?imageMogr2/quality/90/ignore-error/1)](https://zhuanlan.zhihu.com/p/612587257)

![](https://image.cubox.pro/article/2023040610331282042/58073.jpg?imageMogr2/quality/90/ignore-error/1)
金发红眼的长裙美女走在夜晚的沙滩上

前言：
---

以下是在本地安装stable-diffusion的教程，根据不同模型可以轻松生成不同类型的精美图片，上图是使用擅长动漫任务的Anything3.0生成的（*PS，在写教程的过程中发现，该系列模型出4.5了，模型大小比3小了一半，效果依然赞！*）

COS、游戏人物和图标、甚至漫画都可以专门训练模型来做特定的任务！

游戏领域可以使用20%的人力投入+AI 产出跟以前一样的内容！  
漫画领域有人使用呆伯特漫画作为数据，训练出来的模型甚至可以让2个人物做不同的具体的动作，当然目前可以直接用图生图，让结果的姿势符合需求，这就是stable-diffusion ControlNet 插件 的作用！

1. 安装Python
-----------

**版本号最好是：3.10.6，否则更容易报错**
-------------------------

Python 官网：[Python Release Python 3.10.6 \| Python.org](https://link.zhihu.com/?target=https%3A//www.python.org/downloads/release/python-3106/)

记得把Python加入环境变量
![](https://image.cubox.pro/article/2023040610331293159/21223.jpg?imageMogr2/quality/90/ignore-error/1)

2. 安装git
--------

[Git - Downloading Package](https://link.zhihu.com/?target=https%3A//git-scm.com/download/win)

下载之后，全部默认选项安装即可，没有需要特别注意的地方

安装完成之后到命令行确认git 安装成功，如图
![](https://image.cubox.pro/article/2023040610331218263/98000.jpg?imageMogr2/quality/90/ignore-error/1)
Git

弹出一大堆说明问答，就安装成功了，继续下面的步骤即可

3. git clone stable-diffusion-webui
-----------------------------------

安装到可以有20G以上的硬盘分区上，因为后续要放模型和加载一堆东西，会很占用空间  

打开cmd 命令终端

切换到有充足空间的硬盘，然后输入3个命令：

1. cd d:
2. d:
3. git clone [https://github.com/AUTOMATIC1111/stable-diffusion-webui.git](https://link.zhihu.com/?target=https%3A//github.com/AUTOMATIC1111/stable-diffusion-webui.git)

    Microsoft Windows [版本 10.0.22621.1344]
    (c) Microsoft Corporation。保留所有权利。

    C:\Users\ax65>cd d:
    D:\

    C:\Users\ax65>d:

    D:\>

之后，等待下载即可，

完成后会在对应的盘种新增一个 *stable-diffusion-webui*文件夹

*4. 下载模型*
---------

打开网址，下载 后缀为.safetensors或者ckpt 的模型都可以，优先选择前者，因为它的安全问题比ckpt少，目前有往 safetensors 迁移的迹象。

**Stable diffusion-2.0**

[stabilityai/stable-diffusion-2 at main](https://link.zhihu.com/?target=https%3A//huggingface.co/stabilityai/stable-diffusion-2/tree/main)

**Anything-3.0**

[Linaqruf/anything-v3.0 at main](https://link.zhihu.com/?target=https%3A//huggingface.co/Linaqruf/anything-v3.0/tree/main)

**Anything-4.5**

[https://huggingface.co/andite/anything-v4.0/resolve/main/anything-v4.5-pruned.safetensors](https://link.zhihu.com/?target=https%3A//huggingface.co/andite/anything-v4.0/resolve/main/anything-v4.5-pruned.safetensors)

**等待下载，现在可以去完成后续的步骤**

**更多模型可参考：** [Models - Hugging Face](https://link.zhihu.com/?target=https%3A//huggingface.co/models)

<br />

下载完成后，将模型放入以下文件夹（对应自己的存放位置）

    D:\stable-diffusion-webui\models\Stable-diffusion

同时

把以下文本新建文本文件  
复制代码  
修改名字和后缀：768-v-ema.yaml  
放到同一个文件夹中：

768-v-ema.yaml
--------------

    model:
      base_learning_rate: 1.0e-4
      target: ldm.models.diffusion.ddpm.LatentDiffusion
      params:
        parameterization: "v"
        linear_start: 0.00085
        linear_end: 0.0120
        num_timesteps_cond: 1
        log_every_t: 200
        timesteps: 1000
        first_stage_key: "jpg"
        cond_stage_key: "txt"
        image_size: 64
        channels: 4
        cond_stage_trainable: false
        conditioning_key: crossattn
        monitor: val/loss_simple_ema
        scale_factor: 0.18215
        use_ema: False # we set this to false because this is an inference only config

        unet_config:
          target: ldm.modules.diffusionmodules.openaimodel.UNetModel
          params:
            use_checkpoint: True
            use_fp16: True
            image_size: 32 # unused
            in_channels: 4
            out_channels: 4
            model_channels: 320
            attention_resolutions: [ 4, 2, 1 ]
            num_res_blocks: 2
            channel_mult: [ 1, 2, 4, 4 ]
            num_head_channels: 64 # need to fix for flash-attn
            use_spatial_transformer: True
            use_linear_in_transformer: True
            transformer_depth: 1
            context_dim: 1024
            legacy: False

        first_stage_config:
          target: ldm.models.autoencoder.AutoencoderKL
          params:
            embed_dim: 4
            monitor: val/rec_loss
            ddconfig:
              #attn_type: "vanilla-xformers"
              double_z: true
              z_channels: 4
              resolution: 256
              in_channels: 3
              out_ch: 3
              ch: 128
              ch_mult:
              - 1
              - 2
              - 4
              - 4
              num_res_blocks: 2
              attn_resolutions: []
              dropout: 0.0
            lossconfig:
              target: torch.nn.Identity

        cond_stage_config:
          target: ldm.modules.encoders.modules.FrozenOpenCLIPEmbedder
          params:
            freeze: True
            layer: "penultimate"

结果：
---

![](https://image.cubox.pro/article/2023040610331292028/61179.jpg?imageMogr2/quality/90/ignore-error/1)

5. 修改bat 脚本：
------------

**如果你的独立GPU的内存跟我一样只有4G或者不足8G的话，** 请加修改以下参数  
**注意！！！**如果独立GPU有8G及以上的内存的话那么就可以忽略当前的步骤，因为下面的操作是牺牲速度来换结果的

图中GPU1就是英伟达的独立显卡，专用内存4G
![](https://image.cubox.pro/article/2023040610331226958/98294.jpg?imageMogr2/quality/90/ignore-error/1)
显存截图

**专用显存和共享内存是无法一起使用的，所以需要修改运行模型，否则图片将跑不动。**

以记事本等编辑器打开webui-user.bat

修改以下这行：

    set COMMANDLINE_ARGS=

改为：

    set COMMANDLINE_ARGS=--xformers --medvram
    --xformers 的意思是
    --medvram 是 medium vram 的缩写，的意思是中等显存模式 
    --lowvram 是 low  vram 的缩写，意思是低显存模式，

vram 是 Video Random Access Memory，后者Random Access Memory 就是我们常说的内存空间，台湾翻译成记忆体，非常的直白。

修改结果如下：
![](https://image.cubox.pro/article/2023040610331289277/68936.jpg?imageMogr2/quality/90/ignore-error/1)

6. 修改GPU超时设置
------------

*同样，这个步骤是因为显存不足造成的，所以如果**显存大于等于8G** ，可以**直接跳过当前步骤**。*

因为在最开始的时候，我设置了【中等显存模式】 甚至【低显存模式】，依然无法1次性顺利跑完4张图，总是会报错： CUDA error: the launch timed out and was terminated

    RuntimeError: CUDA error: the launch timed out and was terminated
    CUDA kernel errors might be asynchronously reported at some other API call,so the stacktrace below might be incorrect.
    For debugging consider passing CUDA_LAUNCH_BLOCKING=1.

<br />

需要管理员权限打开 Nsight Monitor

此时直接修改，其中的WDDM TDR Enable 改为 False

这样就算显存卡了超过2秒也不会自动关闭，导致作法中断。  
![](https://image.cubox.pro/article/2023040610331213224/77706.jpg?imageMogr2/quality/90/ignore-error/1)

8. stable-diffusion-webui
-------------------------

打开 stable-diffusion-webui 目录下的 ***webui-user.bat***文件，等待加载，第一次加载速度会比较慢， 需要加载一大堆东西。

以下是开始启动UI的页面：
![](https://image.cubox.pro/article/2023040610331334487/96407.jpg?imageMogr2/quality/90/ignore-error/1)
开始

启动完成，复制以下网址，在浏览器打开，进入UI界面
![](https://image.cubox.pro/article/2023040610331334974/33792.jpg?imageMogr2/quality/90/ignore-error/1)

选择模型、参数和提示词
![](https://image.cubox.pro/article/2023040610331342430/78132.jpg?imageMogr2/quality/90/ignore-error/1)

正在生成
![](https://image.cubox.pro/article/2023040610331262309/36035.jpg?imageMogr2/quality/90/ignore-error/1)

**生成结果：**
![](https://image.cubox.pro/article/2023040610331284060/40918.jpg?imageMogr2/quality/90/ignore-error/1)

* Prompt为：masterpiece, best quality,Beautiful blonde with red eyes ,dress ,walking ,on the beach,night
* 反向Prompt为：lowres, bad anatomy, bad hands,error, missing fingers, extra digit, fewer digits, cropped, worst quality, low quality, normal quality, jpeg artifacts, blurry, exposed
* 模型为：Anything-V3.0

完整参数如下：
> masterpiece, best quality,Beautiful blonde with red eyes ,dress ,walking ,on the beach,night   
> Negative prompt: lowres, bad anatomy, bad hands,error, missing fingers, extra digit, fewer digits, cropped, worst quality, low quality, normal quality, jpeg artifacts, blurry, exposed   
> Steps: 60, Sampler: Euler a, CFG scale: 15, Seed: 3719634648, Size: 384x512, Model hash: 3088848987, Model: anything-v3-fp32-pruned   
> Time taken: 10m 29.63s   
> Torch active/reserved: 2352/3188 MiB, Sys VRAM: 4096/4096 MiB (100.0%)

9. 参考资料
-------

1. [Command Line Arguments and Settings · AUTOMATIC1111/stable-diffusion-webui Wiki (github.com)](https://link.zhihu.com/?target=https%3A//github.com/AUTOMATIC1111/stable-diffusion-webui/wiki/Command-Line-Arguments-and-Settings)
2. [cuda the launch timed out and was terminated windows11解决方案 关闭TDR - 哔哩哔哩 (bilibili.com)](https://link.zhihu.com/?target=https%3A//www.bilibili.com/read/cv15591572)
3. [cuda the launch timed out and was terminated - CUDA / CUDA Programming and Performance - NVIDIA Developer Forums](https://link.zhihu.com/?target=https%3A//forums.developer.nvidia.com/t/cuda-the-launch-timed-out-and-was-terminated/20337)
4. [超簡單AI繪圖Stable diffusion本機安裝\&中文化教學 - YouTube](https://link.zhihu.com/?target=https%3A//www.youtube.com/watch%3Fv%3DWjr7-1ECQwY)
5. \[dilbert comic strip \| Stable Diffusion \| OpenArt\]([dilbert comic strip \| Stable Diffusion \| OpenArt](https://link.zhihu.com/?target=https%3A//openart.ai/discovery/sd-1008275512499634226))
6. \[Generative AI: Using ChatGPT and Stable Diffusion to Create Comic Strips - YouTube\]([https://www.youtube.com/watch?v=hCyIyw1-rFo\&t=806s](https://link.zhihu.com/?target=https%3A//www.youtube.com/watch%3Fv%3DhCyIyw1-rFo%26t%3D806s))
7. [AI绘画心得：Stable Diffusion + ControlNet - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/609563100)
8. [2023-03-10_五分钟学会2023世界顶级AI绘画神器Stable Diffusion（入门篇） - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/613122671)

下一篇：

[刘白：AIGC4：ChatGPT 为什么避免不了胡说八道？4 赞同 · 0 评论文章![](https://image.cubox.pro/article/2023040610331373735/59313.jpg?imageMogr2/quality/90/ignore-error/1)](https://zhuanlan.zhihu.com/p/614155515?)

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7043479523806938289)
