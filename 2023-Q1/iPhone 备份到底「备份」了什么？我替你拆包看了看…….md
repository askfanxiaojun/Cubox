iPhone 备份到底「备份」了什么？我替你拆包看了看......
=================================

[mp.weixin.qq.com](http://mp.weixin.qq.com/s?__biz=MzU4Mjg3MDAyMQ==&mid=2247552034&idx=2&sn=c82e82b92777637c7786f96271be6d98&chksm=fdb3f948cac4705ed6c2e3efc15ceb58d1b975ec214b5e3fea0145956ee1f96ca56e447f757a&mpshare=1&scene=1&srcid=0328vmxfRcRgIF9BJ45rdhHB&sharer_sharetime=1679979078814&sharer_shareid=c58007142b3c8dd4da3163f5c61d6b7b#rd)万千十一 少数派


2022 年初，我的 iPhone 8 在勤恳服役三年后，以一次落地坠入不可挽救的冷寂，使其继任者 iPhone 13 mini 面临数据缺失造成的起步困难，于是数日前的 iTunes 备份有了用武之地，应用列表、聊天记录等除少量损失外，基本如数恢复。不久，手持新机的喜悦占领高地，新的折腾又已开启。

既然这些数据能够被 iTunes 备份及恢复，数据内容必然就存放在备份文件中，但应用千奇百怪，iTunes 又是如何组织备份数据结构的呢？不如同我一道，打开备份瞧瞧。

![图片](https://image.cubox.pro/article/2022082618220657983/36519.jpg?imageMogr2/quality/90/ignore-error/1)

**▍****准备**

首先，我们需要准备一个备份以供后续分析。使用 USB 将 iPhone 或 iPad 连接电脑，然后根据自己的电脑系统进行备份操作。

对于 macOS，自 Catalina 起，原本的 iTunes 已不复存在，其核心的音乐媒体功能变更为 Music，移动设备备份功能则交棒给了 Finder。为表述一致，本文仍将 Mac 和 PC 两平台的 Apple 移动设备备份统称为 iTunes 备份。

出于方便分析的目的，备份时请不要勾选加密备份。

**▍****定位初窥**

完成备份后，我们可以通过文件系统定位到备份所在路径：

•macOS 为\~/Library/Application Support/MobileSync/Backup

•Windows 为%APPDATA%\\\\Apple Computer\\\\MobileSync\\\\Backup（部分电脑%APPDATA下无Apple Computer文件夹，则应替换为Apple）

插一句，由于Backup路径固定，可以通过软链接的方式将 iTunes 备份移至外部储存，以节省本机硬盘空间，参考[这篇文章]()。

![图片](https://image.cubox.pro/article/2023032813432222375/27850.jpg?imageMogr2/quality/90/ignore-error/1)

iTunes 备份在 macOS 中的位置及目录结构

可以看到，Backup路径下有一个名似 UUID 的文件夹，想必就是我们刚刚的备份文件了。如果你曾有多个设备通过 iTunes 备份至同一台电脑，那么Backup路径下将会有对应数量的文件夹。不难猜测，每个文件夹便对应一台移动设备，文件夹名实为设备标识码 UDID。

打开设备文件夹，我们将看到一大串以两个字符命名的文件夹，可能从00到ff。熟悉十六进制的朋友已有警觉，这看上去应该就是排列好的哈希头啊。

先行跳过，看看除文件夹外还剩的几个文件：Info.plistManifest.dbManifest.plistStatus.plist。其中最大的db文件，想必是保存主要数据的一个 SQLite 数据库；另外三个为plist文件，常用于在 iOS 和 macOS 应用中保存配置、状态等信息，从中应该能够获取到一些有关备份和应用的数据。

**▍****尝试深挖**

尽管都以.plist结尾，但Manifest.plist与Status.plist是二进制文件，需借助 Xcode（Mac） 或开源跨平台的ProperTree（依赖 Python 环境）、Xplist等软件打开，而Info.plist是形似 XML 的文本文件，除前述软件外，也可用直接在文本编辑器中查看。

### **Info.plist**


首先是Info.plist，Xcode 打开后可以清晰地看出，该文件保存了我们所备份设备的各种信息：

•Applications 和 Installed Applications 分别以字典和列表的方式保存了设备上已安装的应用，前者还为每个应用保存了一些元数据；  


•Device Name /Display Name、Build Version 显示了设备名、系统版本；

•Product 相关字段是设备出厂时厂商所赋予的标识；

•Last Backup Date 与 iTunes 相关内容则记录了最近一次备份日期及一些备份相关信息。

![图片](https://image.cubox.pro/article/2023032813432230110/53074.jpg?imageMogr2/quality/90/ignore-error/1)

Info.plist 文件内容示意，Applications 部分经删减

### **Status.plist**


Status.plist的内容较为简单，主要记录当前备份状态：

•IsFullBackup 指示这次备份是否为全量备份（上图为增量备份）；  


![图片](https://image.cubox.pro/article/2023032813432227518/44134.jpg?imageMogr2/quality/90/ignore-error/1)

Status.plist 文件内容示意

### **Manifest.plist**


Manifest.plist更侧重于备份文件内容的对照：

•Applications 部分为应用元数据，与 Info.plist 中的 98 项不同，此处删减之前多达 994 项，其将各应用的数据按照域、组、插件等做了更为细致的拆分。元数据字段中也有更多信息，比如根据 Google Maps 路径可知其打包后应用文件名为 maps.app ，因为放在专属的容器中，不会与其他家的地图混淆；  


•LockDown 部分保留了一些设备和备份的相关信息；

•Date 记录了该设备第一次在此电脑备份的时间；

•IsEncrypted 表示备份是否加密；

![图片](https://image.cubox.pro/article/2023032813432252730/72235.jpg?imageMogr2/quality/90/ignore-error/1)

Manifest.plist 文件内容示意，Applications 部分经删减

### **Manifest.db**


来到核心的Manifest.db，这是一个 SQLite 文件型数据库，可使用任意支持 SQLite 的数据库软件读取查询，如 TablePlus（Mac）、DBeaver（开源跨平台）。

Manifest 数据库由 Files 和 Properties 两个数据表组成，后者暂无数据，故让我们聚焦于 Files 表。其保存了近 15 万行数据，表结构并不复杂，共有 5 个字段：

![图片](https://image.cubox.pro/article/2023032813432228537/22812.jpg?imageMogr2/quality/90/ignore-error/1)

Manifest 数据库：Files 表结构

•domain 是各应用、应用组所属的域，与 Manifest.plist 中 Applications 的子项对应；

•relativePath 可读性较高，记录了文件相对路径，相对于什么父路径呢？联想到 Google Maps 的例子，父路径应该是 domain 域所对应的容器；

•flags：结合 relativePath 总结规律，1 表示文件，2 表示文件夹；

•fileID 看起来像是一串哈希值，不禁让我们想起设备文件夹下的双字符子文件夹。从 relativePath 中随便找个文件验证一下：比如 mapcfg_logo_zh_3_icon@2x.png 对应的 fileID 开头为 000199xxxxxx，进入 00文件夹查找 000199xxxxxx，将所得文件拷贝出来，更改文件名以 .png 结尾，便能顺利打开看到了一张模糊的图片；

![图片](https://image.cubox.pro/article/2023032813432232699/89580.jpg?imageMogr2/quality/90/ignore-error/1)

通过 fileID 定位 relativePath 中的一张 png 图片

•file 为二进制数据，存放了诸如文件大小、创建时间之类的信息。  


总体而言，若你关注备份状态及设备信息，可从Status.plist和Info.plist两个文件了解，通过后者还能便捷地获取设备的应用列表。

而如果你想在备份文件中找到一些有用的数据，则需依赖 Manifest 数据库内的 Files 数据表，其为 iTunes 备份的所有文件建立了路径映射关系，可通过domain锁定应用，基于relativePath查找具体文件，再由对应的fileID定位文件在磁盘上的真实路径，设法读取即可。

**▍****一览无余**

通过层层深入，我们已经挖掘到了 iTunes 备份的末梢，即每一个具体的应用文件。那么是时候起身俯瞰，纵览这套备份了。

### **应用目录树**


还记得刚刚的relativePath字段，它标明了某一应用具体文件相对应用域的路径，如果我们将备份中该应用的所有相关文件组织在一起，然后对relativePath加以整理呢？没错，我们就得到了这个应用的文件目录树。把备份中所有应用的目录树合在一起，整个 iTunes 备份的结构就非常完整清晰了。再加一点点可视化------

![图片](https://image.cubox.pro/article/2023032813432213276/31378.jpg?imageMogr2/quality/90/ignore-error/1)

iTunes 备份部分应用目录树，由 ECharts 绘制

### **Space Sniffer**


Windows 平台曾有款名为SpaceSniffer的软件，可以帮助用户直观地看到磁盘空间占用，轻巧实用，深得我心。既然我们已经得到了目录结构，不妨再补上文件大小，以类似的形式看看各应用所占空间。文件大小的获取有两种方式，一种是解析Manifest.dbFiles 表中的file字段，从中读取文件大小相关键值；另一种更为直接，通过fileID定位真实路径后查看文件大小即可，不做赘述。

完成可视化之后便是下面这个样子------

![图片](https://image.cubox.pro/article/2023032813432238591/14021.jpg?imageMogr2/quality/90/ignore-error/1)

iTunes 备份空间占用图，由 Plotly 绘制

可以看出，微信（com.tencent.xin）在我的 iPad 备份空间中几乎占据半壁江山，其次是哔哩哔哩、京东等，以及大隐隐于图的真·小而美应用们。

**▍****结语**

我们整个探索是基于未加密的 iTunes 备份，如你所见，未加密备份中的绝大部分应用数据可被设法读取，这不可避免地给隐私及安全造成一丝威胁。

若执行备份的电脑不足够可靠，请务必勾选加密备份。按照官方对加密备份的说明，密码、健康、通话记录等数据在你勾选加密后会添加至备份中，未加密备份并不会包含这些内容。尽管以这种方式被窃取数据的可能性似乎微乎其微，但还是记得给加密备份选个安全的密码吧。

原文链接：

https://sspai.com/post/79029?utm_source=wechat\&utm_medium=social  


作者：万千十一  


责编：北鸮

******/****更多热门文章** **/******

[![图片](https://image.cubox.pro/article/2023032813421957835/83566.jpg?imageMogr2/quality/90/ignore-error/1)](http://mp.weixin.qq.com/s?__biz=MzU4Mjg3MDAyMQ==&mid=2247552001&idx=1&sn=21b5236eb1e12cf9d1a09644fad3c615&chksm=fdb3f96bcac4707d1592e213c1111ce16a4ee32de5ec2aee26d292a7345d2c335fef0e6cd987&scene=21#wechat_redirect)

[![图片](https://image.cubox.pro/article/2023032712274144089/40866.jpg?imageMogr2/quality/90/ignore-error/1)](http://mp.weixin.qq.com/s?__biz=MzU4Mjg3MDAyMQ==&mid=2247551913&idx=1&sn=8683688a6ad03ce0fc4549b3cf38c217&chksm=fdb3fec3cac477d545b7f4d1f6b6da650620305d1e64f790d24bd8bb875022b31a3c38f56698&scene=21#wechat_redirect)

![图片](https://image.cubox.pro/article/2022112114133553599/80894.jpg?imageMogr2/quality/90/ignore-error/1)

![图片](https://image.cubox.pro/article/2021071720232113863/81460.jpg?imageMogr2/quality/90/ignore-error/1)

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7040257611962255387)
