eSIM 转 SIM 实体卡
==============

[iecho.cc](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/)nonPointer

This post is also available in English and alternative languages.

长文警告：本文包含大量外链，建议自行展开阅读您认为需要的链接。

0. 术语表
------

阅读本文之前，您需要了解以下术语，否则可能会对您的阅读造成困扰。

### 简称

* **SIM**: Subscriber Identity Module
* **pSIM**：Physical SIM，物理 SIM 卡。
* **eSIM**：Embedded SIM，嵌入式 SIM 卡。在不同的语境下可以指代 eSIM 卡片或 eSIM 配置文件。
* **iSIM**：Integrated SIM，集成在 SoC 中的 SIM 卡。
* **USIM**: UMTS SIM
* **CSIM**: CDMA SIM
* **eSE**: embedded Secure Element
* **TPM**: Trusted Platform Module
* **UIM**: User Identity Module Card

### 专有名词

以下内容可在 [GSMA SGP.21 标准的 "Definitions and Terms" 章节](https://web.archive.org/web/20240416170633if_/https://www.gsma.com/esim/wp-content/uploads/2021/07/SGP.21-2.3.pdf#page=6.51)找到。

* **UICC**：Universal Integrated Circuit Card，通用集成电路卡。是 SIM 卡的标准名称。
* **eUICC**：本意指 Embedded UICC，嵌入式通用集成电路卡。后来指代支持本地配置文件管理的 UICC。需由第三方厂商制造，如东信和平（ECP）、泰尔（Thales）、Gemalto（已被 Thales 收购）等。
* **LPA** ：Local Profile Assistant，本地配置文件助手，是用于管理 eUICC 卡片的软件。Android、iOS 和 Windows 都有自己的 LPA 实现。[Infineon](https://github.com/CursedHardware/infineon-lpa-mirror/) 和 [lpac](https://github.com/estkme-group/lpac) 是第三方的开源 LPA。
* **RSP**：Remote SIM Provisioning，远程 SIM 配置。是下载、安装、启用、禁用、删除 eSIM Profile 的过程。
* SM-DP+：Subscription Manager Data Preparation，订阅管理数据准备。是用于管理、下发 eSIM Profile 的平台，是实现 RSP 的一部分。
* **GSMA**：Global System for Mobile Communications Association，全球移动通信系统协会。是全球移动通信行业的标准制定组织。
* **GSMA CI**：GSMA Certificate Issuer，是 GSMA 认证的证书颁发机构。
* **EUM**：eUICC Manufacturer，eUICC 卡片的制造商。
* **EUM 证书**：GSMA CI 给 eUICC 制造商签发的证书，用于验证 eUICC 卡片的合法性。
* **eUICC 证书**：EUM 使用 EUM 证书签发的 eUICC 证书，用于验证 eUICC 卡片的合法性。
* **EID**：eUICC ID，eUICC 的唯一标识符，本质上是 eUICC 卡片内 eUICC 证书的序列号。
* **ICCID**：用于区分 eSIM 配置文件的标识符，不唯一，可以由运营商自行定义。
* **SAS-UP**: SAS for UICC Production，通用集成电路卡生产。

### 关系图

以下图片来自 [GSMA SGP.21 标准](https://web.archive.org/web/20240416170633if_/https://www.gsma.com/esim/wp-content/uploads/2021/07/SGP.21-2.3.pdf)

* [RSP 架构](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/rsp-arch.png)
* [eUICC 图解](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/euicc-pre.png)
* [eUICC 交互架构](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/euicc-arch.png)

1. 背景
-----

[eSIM](https://source.android.com/docs/core/connect/esim-overview) (embedded-SIM, eUICC) 是一种嵌入式可编程的 SIM 卡，集成在设备主板或模块上，可以通过 LPA (Local Profile Assistants) 进行管理。eSIM 与 SoftSIM 不是同一个东西，但都是虚拟 SIM 卡的实现，两者都可以通过 OTA (Over-The-Air) 进行更新。

几天前 Apple 发布了国行 iPad（第 10 代）无线局域网 + 蜂窝网络机型（A3162），支持 eSIM，但是[反向锁区](https://support.apple.com/zh-cn/HT213954)，只能在境内激活中国大陆运营商（中国联通）的 eSIM Profile，在境外需要开启定位才能激活境外运营商的 eSIM Profile。借此机会也了解到一个新东西：eSIM 转物理 USIM。

早期这项技术被用于以下场景：

1. 提取智能手表、廉价 4G Wi-Fi dongle 的内置物联网卡的 eUICC 芯片，将其改变为 USIM 的形态，安装到 CPE 或者手机里。一般用于"双不限"流量卡。
   * [反向操作 0 成本将 eSIM 卡魔改成物理 SIM 卡](https://www.bilibili.com/video/BV1oA411r7NL/)
   * [魔改内置 eSIM 为普通卡槽 打造不到 20 元的 4G 随身 Wi-Fi 狗 兼廉价热点机](https://www.bilibili.com/video/BV15R4y1E7ME/)
2. 拆除 eSIM 手表的 eUICC 芯片，在原位置焊接上转接板，然后将自己的 eUICC 白卡放入转接板。利用"一号双终端"业务，将自己的手机号码写入到 eUICC 白卡，再将其安装至手机，从而实现两台手机同时在网，共享号码、通话、短信和数据业务。参考链接 [1](https://web.archive.org/web/20240101163722if_/https://tieba.baidu.com/p/7449598338?pn=1)、[2](https://web.archive.org/web/20240101163807if_/https://tieba.baidu.com/p/7449598338?pn=2)。

除此之外，我们可以使用 eUICC 测试白卡写入境外运营商的 eSIM Profile，畅游 Internet 或接收短信验证码（接码）。

2. 购买 eSIM 实体卡
--------------

由于缺失 China CI 和 GSMA Test CI，所有品牌（5ber.eSIM、eSIM.me 和速易卡科技等）发行的 eUICC 卡片均不能写入中国大陆运营商的 eSIM Profile。具体原因参见下文 Certificate Issuer (CI) 证书颁发者。此外，部分中国运营商采取了 IMEI 和 EID 绑定制度。

### 速易卡科技

淘宝店"[速易卡科技](https://shop104192953.m.taobao.com/)"目前提供两种规格的 eUICC 成品卡片

* 420 KB
  * 售价：¥55
  * 购买暗号：安卓esim
  * [取决于 Profile 大小](https://sim.obdo.cc/esim-size)，能写入 10-20 张 eSIM
* [1 MB](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/syc-1m.jpg)
  * 价格：¥68
  * 购买暗号：安卓esim 1m
  * [取决于 Profile 大小](https://sim.obdo.cc/esim-size)，能写入 30-50 张 eSIM

无法直邮海外，港澳台及海外用户需要自行联系转运仓。

除此外，店内还提供 [USB-C 接口的 eUICC 读卡器](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/syc-e001.png)、Nano SIM (4FF) to Mini SIM (2FF) 转接板、eSIM (MFF2) to Nano SIM (4FF) 转接板、植锡、ST33 芯片等。

注意：由于 iOS 限制，[速易卡科技](https://shop104192953.m.taobao.com/)销售的 eUICC 白卡不能在国行 iPhone 中使用。iPhone 用户可以购买 [5ber.eSIM](https://esim.5ber.com/) 标准版搭配[速易卡科技](https://shop104192953.m.taobao.com/)的[读卡器](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/(./syc-e001.png))写卡，或者购买 [eSTK.me](https://t.me/estkme) 一步到位。

### eSTK.me

更多关于 eSTK.me 的信息请阅读 [eSTK.me: 下一代可插拔消费者 eSIM 卡](https://iecho.cc/2024/03/16/estk-me-next-generation-removable-consumer-esim/)。

无法直邮海外，港澳台及海外用户需要自行联系转运仓。

[eSTKme-ECO](https://www.estk.me/product/estkme-eco/?aid=171) 10% OFF 优惠码：`4JEMHFAS`。

[eSTK.me](https://estk.me/?aid=171) 调用 USIM 卡的 Applet 实现在 iOS 内自助切换 Profile。写卡仍然需要借助硬件读卡器或者兼容 eSIM 的 Android 手机。支持国行 iPhone。

eSTK.me（固件 v2.x 及以后的版本）基于 ETSI 的 Bearer Independent Protocol (BIP) 协议，使得 eUICC 通过基带与远程服务器建立 TCP 连接，手动实现了 eSIM Profile 的远程配置（类似于 M2M 的形式）。本质上是让 STK 直接联网读写 APDU，而不是通过手机的 LPA 进行管理。因此，eSTK.me 是目前市面上唯一可以在 iOS 上实现自主写卡和 eSIM Profile 管理的解决方案。

eSTK.me 还支持以下特色功能

* 设置虚拟 EID：自定义 Android App 所识别到的 eUICC EID。
* 自定义 ARA-M SHA-1：仅作用于 Android 平台。eUICC 宣告 5ber 和 eSIM.me 的 ARA-M SHA-1，容许第三方 App 提权获得 Carrier Privileges，从而与 UICC 卡片进行通信
* 设置 ISD-R 模式
* 设置 ATR 模式：卡片功能宣告。[ATR 字段定义](https://blog.apdu.fr/posts/2016/01/atr-list-study/)和[在线解析](https://smartcard-atr.apdu.fr/)。
* 设置 ECASD 管理域
* 设置 MOTD：设置 SIM 卡启动时显示的信息。

### Lenovo

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2Flenovo-thales.png&valid=true "Lenovo Thales eSIM")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/lenovo-thales.png)

仅在联想海外官网提供购买，发 UPS Worldwide Express Saver。

* ThinkPad Thales eSIM card
  * FRU: 4XC1L91362
* Lenovo Wireless Gemalto eSIM card
  * FRU: 5W11H85415

群友 @Lockestek 订购了一盒 FRU 为 4XC1L91362 的 [Thales eSIM](https://euicc-manual.osmocom.org/docs/pki/eum/files/89033023-1c1b5a.txt) 卡：

* 容量 516 KiB
* [SAS](https://www.gsma.com/security/security-accreditation-scheme/) TS-CA-UP-0823
* [SGP.22 v2.2](https://www.gsma.com/esim/resources/sgp-22-v2-2-2/)
* 产地 墨西哥

EUICCinfo2 信息如下

|------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ``` 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 ``` | ``` { "profile_version": "2.1.0", "sgp22_version_supported": "2.2.0", "euicc_firmware_version": "66.81.1", "free_nvram": 528532, "uicc_capability": [ "USIM Support", "ISIM Support", "CSIM Support", "DeviceInfo Extensibility Support", "AkaMilenage", "AkaCave", "AkaTuak128", "RFU2", "GBA Authentication USIM", "EAP Client", "MultOS", "Multiple USIM Support", "Multiple ISIM Support" ], "ts102241_version": "9.2.0", "gp_version": "2.3.0", "rsp_capability": [ "additionalProfile", "crlSupport", "testProfileSupport" ], "issuer_for_verification": [ "81370f5125d0b1d408d4c3b232e6d25e795bebfb" ], "issuer_for_signing": [ "81370f5125d0b1d408d4c3b232e6d25e795bebfb" ], "category": "Medium eUICC", "sas_accreditation_number": "TS-CA-UP-0823" } ``` |

### 5ber.eSIM 和 eSIM.me

[5ber.eSIM](https://esim.5ber.com/)（¥180）和 [eSIM.me](https://esim.me/)（€70）都提供 eSIM 实体卡片，用户可以使用它们的 Android App 将 eSIM Profile 下载至实体卡中（无需读卡器），然后插入手机、CPE 等设备使用。但这两家均软件限制了 Profile 的写入次数，并以此收费。

**扩展阅读**

* <https://www.zyh8.com/archives/1064/kill-5ber-esim/>
* <https://www.v2ex.com/t/1001516#r_14131644>
* <https://www.nodeseek.com/post-67964-1#4>
* [https://sim.obdo.cc/esim-size#:\~:text=7-,%E6%B3%A8](https://sim.obdo.cc/esim-size#:~:text=7-,%E6%B3%A8)
* <https://forums.redflagdeals.com/5ber-esim-physical-card-us12-us25-per-card-2649427/12/#p39137480>

以上内容均为网友分享，仅供参考。

### SakuraSIM - 已停售

由名为 Sakura 的 Telegram 用户发行的、从 ECP 直接采购的 eUICC 卡片。由于各种原因，SakuraSIM 已经停售。

* Sakura v1：不含 ARA-M，只可以使用读卡器或者 LPA 写卡，与 Lenovo Thales eSIM 卡片类似。
* Sakura v2：含有 EasyEUICC 和两个社区公共（[1](https://github.com/zdzym/sakurasim_key), [2](https://github.com/ShiinaSekiu/CommunityKey)）的 ARA-M。

### 9eSIM（9ber）

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2Fmeme-9ber.webp&valid=true "9ber 表情")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/meme-9ber.webp)

9eSIM（9ber）是简单的 eUICC 白卡，未设置 ARA-M，只能使用读卡器写卡。据悉是 G+D 的产品。

* 1MB 版本（v1）：售价 78 人民币，对标 5ber Standard。
* 1.6MB 版本（v2）：售价 138 人民币，含有 EasyEUICC 的 ARA-M，对标 5ber Premium。

据悉，9ber 将于 2024 年 11 月推出 STK 切卡功能。

### PlanB

[Plan B Technology](https://shop126378180.taobao.com/) 的淘宝商家推出了 [planB 卡](https://item.taobao.com/item.htm?id=820906718446)，[使用闭源 LPA 管理](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/planb-demo.mp4)，支持不限次数写入。

* Android 版：定价为 136 人民币，对标 5ber Premium
* iOS 版：定价 219 元，对标 5ber Ultra

### TLDR

针对使用场景，可以分为以下几种选择：

* 偶尔写卡或在 Windows、Linux 平台使用 ------ 购买不含 ARA-M 的白卡，显然速易卡科技（国内用户）和 Lenovo Thales（海外用户）更具竞争力。
* 频繁切卡且 Android 平台 ------ 内置 ARA-M，仅在 Android 平台使用的白卡，SakuraSIM（已停售）、9ber 和 eSTK-ECO Lite 是不错的选择。
* iOS 用户 ------ 内置 ARA-M 且支持 STK 管理（切卡、下卡等），只有 eSTK-ECO 能满足需求。

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2Fmeme-only-estk-can-do.webp&valid=true "eSTK.me 表情")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/meme-only-estk-can-do.webp)

3. 获取支持 eSIM 的 WWAN 模块或 PC/SC 读卡器
---------------------------------

### 支持 eSIM 的 WWAN 模块

移动宽带（Mobile Broadband）是自 Windows XP 时代就存在的功能。Windows 通过独立的 WWAN 模块（Wireless Wide Area Network）来实现移动宽带功能。Windows 10/11 内置了 [MB eSIM Operations](https://learn.microsoft.com/en-us/windows-hardware/drivers/network/mb-esim-operations)，用户可以通过系统内置的 LPA 管理 eSIM 配置。

模块参数和购买事项请阅读：[使用 NGFF M.2 B Key 转 USB 转接卡连接 4G/5G WWAN 模块](https://iecho.cc/2024/04/02/using-ngff-m2-to-usb-adapter-for-4g-5g-wwan-module-connection/)。

### PC/SC 读卡器

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2Fsyc-e001.png&valid=true "SYC-E001 读卡器")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/syc-e001.png) [![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2Festk-card-reader.png&valid=true "eSTK.me ACR38U 读卡器")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/estk-card-reader.png)

* 淘宝店"[速易卡科技](https://shop104192953.m.taobao.com/)"提供 [USB-C 接口的 PC/SC 读卡器和 nano SIM 转接板](https://item.taobao.com/item.htm?id=782783572391)（售价 78 元），搭配 [SYC-LPA App](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/syc-lpa-v1.0.3.apk) 可以在 Android 设备上读写。
* [eSTK.me](https://www.estk.me/product/acr38u-smartcard-reader/) 随产品附赠的 [ACR38U 读卡器](https://www.estk.me/product/acr38u-smartcard-reader/)和 nano SIM 转接板。目前只可以在电脑上使用 EasyLPAC 等软件读写。

4. 获取 eSIM Profile
------------------

### 购买 eSIM 套餐

* 免费试用 eSIM（无流量无通话，仅用于测试设备是否能安装 eSIM Profile）
  * [BetterRoaming](https://www.betterroaming.com/)
    * [`LPA:1$rsp.truphone.com$QR-G-5C-KR-1PCDWP9`](https://qr.esim.cyou/1$rsp.truphone.com$QR-G-5C-KR-1PCDWP9)（[来源](https://www.linkedin.com/posts/hakan-koc_i-am-happy-to-announce-my-newest-company-activity-7079382859777486848-MK7I/)）
    * [`LPA:1$rsp.truphone.com$QRF-BETTERROAMING-PMRDGIR2EARDEIT5`](https://qr.esim.cyou/1$rsp.truphone.com$QRF-BETTERROAMING-PMRDGIR2EARDEIT5)（[来源](https://www.betterroaming.com/esim-installation/)）
* [红茶移动 RedteaGo](https://esim.redteago.com/zh-CN/esim-china/)：使用优惠码 `NONP0002`，领取 $3 余额。
  * 100 MB 365 天，$2.65：适合用于 eSTK.me Cloud Enhance 写卡。
  * 300 MB 高速流量 1 天，$0.54：用完 300MB 后降速为 256 kbps，仍可满足基本的上网需求，甚至 Zoom 会议。
* [Eskimo](https://eskimo.travel/X78676)：使用优惠码 `MONSTERDEALZ`，领取 1GB 两年有效的全球漫游流量。
* [对比全球 eSIM 套餐资费](https://esimdb.com/)
* [支持 eSIM 的运营商列表](https://support.apple.com/zh-cn/HT209096)
* [支持 eSIM 的手机列表](https://www.getnomad.app/shop/support_device)
* [中国大陆区域的便宜 eSIM](https://esims.io/countries/china)
* [eSIM Profile 占用大小统计](https://sim.obdo.cc/esim-size)
* [港澳预付费手机卡大比拼！一篇长文章让你透彻了解各个港澳手机卡保号、上网与日用的资费](https://telegra.ph/%E6%B8%AF%E6%BE%B3%E9%A2%84%E4%BB%98%E8%B4%B9%E6%89%8B%E6%9C%BA%E5%8D%A1%E5%A4%A7%E6%AF%94%E6%8B%BC%E8%AE%A9%E4%BD%A0%E6%B8%85%E6%A5%9A%E7%9A%84%E7%9F%A5%E9%81%93%E5%93%AA%E5%BC%A0%E5%8D%A1%E6%89%8D%E6%98%AF%E6%9C%80%E9%80%82%E5%90%88%E4%BD%A0%E6%97%A5%E7%94%A8%E4%BF%9D%E5%8F%B7%E6%88%96%E4%B8%8A%E7%BD%91-02-04)

注意：除了下列运营商，其他区域运营商（如香港）通常需要 KYC（客户身份审查）认证，需要提供护照等实名身份信息。

常见的用于接收验证码的境外 Pay As You Go (PAYG) 现收现付 eSIM：

* Giffgaff：激活时需充值 £10（约合人民币 90 元），号码有效期为 6 个月。漫游时接收短信免费。每隔 6 个月发短信（£0.3，约合人民币 3 元）保号。开局成本为 90 元，之后每年维护成本为 6 元。
* Lyca Mobile：激活时需充值 £5（约合人民币 45 元），号码有效期为 3 个月。漫游时接收短信免费。每隔3 个月发短信（£0.23，约合人民币 2 元）保号。开局成本为 45 元，之后每年维护成本为 8 元。
* [Three UK](http://aklam.io/jdiW3e)：激活时无需充值，号码有效期为 6 个月。漫游时接收短信免费。每隔 6 个月发短信（£0.4 [中国大陆位于 Band 2](https://web.archive.org/web/0if_/https://www.three.co.uk/content/dam/threedigital/terms-and-conditions/price-guides/latest-price-guides/paygplans-priceguide-12052023.pdf)，约合人民币 3.6 元）保号。开局成本为 0 元，之后每年维护成本为 7.2 元。

注意：苹果用户激活 iMessage 和 FaceTime 时需要发送短信，会产生费用。

~~部分运营商例如英国 Giffgaff 不直接提供 QR Code 和 eSIM Activation Code，只能使用运营商自有的 App 写入到手机中，不能加载至外部 eUICC。但是根据[这个帖子](https://shuzijumin.com/forum.php?mod=viewthread&tid=689&page=1#pid11408)，Giffgaff 用户可以在手机上进行 MITM 抓包，查看 URL 为 `https://publicapi.giffgaff.com/gateway/graphql` 的请求 body，其中的 `lpaString` 字段即 Giffgaff 的 eSIM Activation Code。Telegram 用户 [@kkkwatt](https://t.me/kkkwatt) 提供了一份 Frida 的[脚本](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/giffgaff_frida_hook.js.txt)：点 Giffgaff App 的"安装 eSIM 按钮"时 Frida 会在终端输出激活码。~~

Giffgaff 现在可以使用中国大陆 IP 直接订购 eSIM，无需实体卡板转换、无需通过中介办理。

注意：

* 几乎所有美国运营商使用了 EID 白名单，无法直接写入 eSIM Profile 至外部 eUICC。你需要联系客服，提供自己的 IMEI 和 EID，让他们绑定。
* [日本运营商也存在 EID 白名单](https://www.google.com/search?q=89033023+site:jp#ip=1)
* [慎重购买日本 Android 合约机](https://cheerio-the-bear.hatenablog.com/entry/2022/06/26/035217)：日本运营商使用 RAT ([Rules Authorisation Table](https://www.gsma.com/esim/wp-content/uploads/2020/06/SGP.22-v2.2.2.pdf#page=205)) [限制可安装的 eSIM profile 的归属运营商](https://www.gsma.com/esim/wp-content/uploads/2020/06/SGP.22-v2.2.2.pdf#page=44)，且技术上无法解除该限制。换言之，不用合约机就得满足 EID 的限制，买了合约机就只能安装他们自己家的 eSIM。
  * 相关讨论可以参考[俄语区的帖子](https://4pda.to/forum/index.php?showtopic=1066140&view=findpost&p=126536592)。

### eSIM Profile Activation Code 格式定义

详细的式定义可以参考 [GSMA SGP.22](https://web.archive.org/web/20240210210355if_/https://www.gsma.com/esim/wp-content/uploads/2020/06/SGP.22-v2.2.2.pdf#page=111)。MOC 字段意思为 Mandatory, Optional or Conditional。

常见格式如下：

|-----------|----------------------------------------------|
| ``` 1 ``` | ``` LPA:1${SM-DP+_ADDRESS}${MATCHING_ID} ``` |

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2FeSIM-format.png&valid=true "eSIM Activation Code 格式")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/eSIM-format.png)

`SM-DP+_ADDRESS` 即 Subscription Manager Data Preparation Address，是运营商侧的 eSIM 配置服务器地址。`MATCHING_ID` 则用于匹配对应的 eSIM Profile，可以理解为传递至 SM-DP+ 的 Bearer Token。为了方便用户，运营商一般会将 eSIM Activation Code 转换为 QR Code。终端扫描 QR Code 后，会自动将字符串写入到 eUICC 中。

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2Frsp-architecture.png&valid=true "eSIM Profile 下载过程")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/rsp-architecture.png)

如图是 Remote eSIM Provisioning (RSP) 的过程图，来源自 [Android 文档](https://source.android.com/docs/core/connect/esim-overview)。

`MATCHING_ID` 字段是可选的。例如 T-Mobile 绑定 eSIM 卡的 EID，所以在下载时无需提供 `MATCHING_ID`。

`SM-DP+ OID` 字段一般不会出现。

5. 写入 eSIM Profile 至 eUICC 卡片
-----------------------------

### Android

Android 设备可以使用以下方式管理 eUICC 卡片：

* [PeterCxy/OpenEUICC](https://gitea.angry.im/PeterCxy/OpenEUICC)：{Open,Easy}EUICC
  * ARA-M: `2A2FA878BC7C3354C2CF82935A5945A3EDAE4AFA`（目前仅 eSTK.me 发行的 eUICC 卡片支持自定义 ARA-M）
  * OpenEUICC 使用 Android Telephony Manager API (TMAPI)，是提供给第三方 ROM 开发者使用的、用于封装为 system app 的 eUICC 管理器。
  * EasyEUICC 使用 Android Open Mobile API (OMAPI)，是以 user app 形式安装的 LPA，可以直接使用，也可以搭配 OMAPI Bypass 来管理 5ber 和 esim.me 的卡。
* 使用 OTG 外置读卡器：[CursedHardware/infineon-lpa-mirror: Infineon Android LPA](https://github.com/CursedHardware/infineon-lpa-mirror)
  * 原版 Infineon LPA 不包含读卡器驱动，请下载 [Queally Modified (2024-02-27)](https://github.com/CursedHardware/infineon-lpa-mirror/releases/tag/queally-2024-02-27) 版本
* 使用内置 LPA：[AndroPlus-org/magisk-module-openeuicc](https://github.com/AndroPlus-org/magisk-module-openeuicc)

国行 Android 手机不一定双卡都支持 OMAPI，可以使用 [eUICC Probe](https://github.com/CursedHardware/euicc-probe) 检测各卡槽是否支持 OMAPI。

已经 root 的用户可以使用 [OMAPI-Bypass](https://github.com/QueallyTech/OMAPI-Bypass) 或 [XposedOMAPIOverrideSEAccessRules](https://github.com/johnzweng/XposedOMAPIOverrideSEAccessRules)（适用于 Android 6-8）绕过 OMAPI 限制，不验证 ARA 和 ArF。更多关于 OMAPI 的信息可以参考 [Open Mobile API - eUICC Manual](https://euicc-manual.osmocom.org/docs/android/open-mobile-api/)。

### Windows、macOS 和 Linux 平台

PC/SC 读卡器需要搭配以下 LPA 使用：

* [estkme-group/lpac](https://github.com/estkme-group/lpac)：跨平台的 C-based eUICC LPA，在 macOS、Windows 和 Linux 下均可使用。
* （推荐）[creamlike1024/EasyLPAC](https://github.com/creamlike1024/EasyLPAC)：Material Design 风格的 lpac 客户端，包含了 [estkme-group/lpac](https://github.com/estkme-group/lpac) 的二进制文件。
* （推荐）[EsimMoe/MiniLPA](https://github.com/EsimMoe/MiniLPA)：Kotlin 编写的跨平台 LPA，支持 macOS、Windows 和 Linux。也是基于 [estkme-group/lpac](https://github.com/estkme-group/lpac) 的 UI。
* [Truphone/LPAdesktop](https://github.com/Truphone/LPAdesktop) 或 [sparkcyf/LPAdesktop](https://github.com/sparkcyf/LPAdesktop)（支持 Apple Silicon）：需要 Java 环境，使用方式参考这篇文章：[通过 PC/SC 智能卡读卡器配置 esim.me 的 SIM 卡 - Sparktour's](https://sparktour.me/2022/11/20/configure-esim-me-card-with-pc-sc-reader/)。

[速易卡科技](https://shop104192953.m.taobao.com/)销售的读卡器（Alcor Micro USB Smart Card Reader）可以在 macOS Sonoma 和 Windows 10 下免驱使用。如果出现 `APDU library init error` 或 `SCardTransmit() failed: 8010002f`，请手动安装 [Alcor Micro USB Smart Card Reader 驱动](https://www.catalog.update.microsoft.com/Search.aspx?q=Alcor%20Micro%20USB%20Smart%20Card%20Reader)。

执行如下命令运行 LPAdesktop：

|-----------|---------------------------------------------------------|
| ``` 1 ``` | ``` java -jar LPA-1.0.0.0-jar-with-dependencies.jar ``` |

如果你的 macOS Sonoma 无法识别第三方读卡器，可以尝试安装 [ACSCCID](https://acsccid.sourceforge.io/#:~:text=Official%20openSUSE%20Packages-,Mac%20OS%20X%20Installer,-acsccid_installer%2D1.1.10.dmg) 驱动。

出厂预置了 SIM 插槽且已经安装了对应 WWAN 网卡（例如 L850-GL, L860-GL 等）的 ThinkPad/HP/Dell 笔记本用户，可以使用 Windows 10/11 系统自带的 LPA 管理 eSIM：[Use an eSIM to get a cellular data connection on your Windows PC](https://support.microsoft.com/en-us/windows/0e255714-f8be-b9ef-9e84-f75b05ed98a3)

淘宝上有网店销售 M.2 (NGFF) 转 USB 的 WWAN 转接卡，集成了 SIM 卡插槽。可以搭配 eUICC 卡和支持 eSIM 的 Fibocom（广和通）或 Quectel（移远）的 4G/5G WWAN 模块使用。部分转接卡[存在兼容性问题](https://cheerio-the-bear.hatenablog.com/entry/2022/09/05/003328)。

6. eSIM 实体卡行业动态
---------------

* 2023 年底 [eSIM.me 在 Reddit 上点名表扬了 5ber.eSIM](https://web.archive.org/web/20240225170917/https://www.reddit.com/r/eSIMs/comments/17nuhze/alternative_to_esimme_now_available_make_almost/)，双方就对方产品进行了坦诚、务实、建设性的讨论。截止 2024 年 4 月，[此事以社群管理员将 eSIM.me 单方面删帖告终。](https://www.reddit.com/user/esim_me/)
* 2024 年 2 月，[eSTK.me](https://estk.me/?aid=171) 发布了第二代 eUICC 工程样品（ES 版），基于 BIP 联网的 rLPA 远程管理功能初步实现。
* 2024 年 2 月，[GSMA 为 Wuhan Tianyu Information Industry CO.LTD 签发了 EUM 证书](https://euicc-manual.osmocom.org/docs/pki/eum/files/89086029/e0a4f4.txt)。这意味着该公司可以生产符合 GSMA 标准的 eUICC 卡片。
* 2024 年 3 月，据 [eSTK.me](https://estk.me/?aid=171) 透露，eSIM.me 的实验室版本已经实现了 iOS 切卡和下卡功能。
* 2024 年 4 月，据 [eSTK.me](https://estk.me/?aid=171) 透露，eSIM.me 准备就监管不力的问题起诉 GSMA。但根据 [GSMA CI 的 CRL (Certificate Revocation List)](https://www.gsma.com/esim/gsma-root-ci/)，EUM 证书吊销并没有先例。
* 2024 年 4 月，拼多多平台上多家店铺的 5ber.eSIM 产品开始促销，Premium 版本售价仅不到 140 元。相较于其 180 元的原价，价格下降了 22%。有商家甚至打出"今日下单送 VPS 一台"的促销内容。
* 2024 年 4 月 10 日，据悉 [eSTK.me](https://estk.me/?aid=171) 预售订单将于 5 月 6 日发货。随后的 5 月 20 日将开放现货销售。本次发售的 eSTK-400KB 将搭载最新版 2.3.4.1 固件，rLPA 功能更名为 Cloud Enhance。此外，种子用户群（eSTK.me Group）将于 6 月后解散，eSTK.me 将正式进入基于邮件和 WhatsApp 的客服模式。
* 2024 年 4 月 11 日，名为 lsf 的用户发布了 [eSTK.me 早期 PCB 文件](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/eSTK_IC_Reference_Gerber.zip)。
* 2024 年 4 月 14 日，闲鱼上的 5ber Standard 售价已降至 60 元，Premium 版售价则降至 120 元。相较于其 180 元的原价，价格下降了 33%。
* 2024 年 4 月 14 日，[速易卡科技](https://shop104192953.m.taobao.com/) 420 KB 容量的 eSIM 实体卡降价至 55 元，并推出了[新版 USB-C 接口的读卡器 SYC-E001](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/syc-e001.png)，售价为 78 元。
* 2024 年 4 月 14 日，据悉 [eSTK.me](https://estk.me/?aid=171) 正在开发 USB-C + BLE 的二合一读卡器（[正面](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/estk-reader-pcb-front.jpg)，[反面](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/estk-reader-pcb-rear.jpg)）。
* 2024 年 4 月 14 日，名为"昊子"的 QQ 用户[透露了自己正在仿制 eSTK.me 的消息](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/haozi-1.jpg)，并晒出了[成品截图](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/haozi-2.jpg)以表明自己不是口嗨。根据该用户的发言可以得知，其具备一定的嵌入式设计能力，但对 GSMA 标准和 eSIM 卡技术实现的理解有待提高。
* 2024 年 4 月 15 日，[速易卡科技](https://shop104192953.m.taobao.com/)推出了 [1MB 容量的实体 eSIM](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/syc-1m.jpg)，售价仅为 68 元，容量为 5ber.eSIM (500KB) 的两倍。购买暗号"安卓esim 1m"。这是目前市面上仅有的 1MB 容量的 eUICC 卡片。
* 2024 年 4 月 16 日，根据闲鱼上 5ber.eSIM 代理商所[发布的照片](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/5ber-stock.jpg)，其手头囤积的 5ber-500KB 产品至少有 <math xmlns="http://www.w3.org/1998/Math/MathML"> 80 × 25 = 2000 </math> 张。假设平均出厂价为 100，其积压了近 20 万人民币的库存。当前 5ber.eSIM 官网库存高达 18 万件。
* 2024 年 4 月 18 日，有 Twitter (X) 用户声称，[5ber.eSIM 没有为使用引荐链接下单的客户提供被承诺的优惠折扣。](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/5ber-issue-2.jpeg)
* 2024 年 4 月 19 日，有多位 Telegram 用户声称，其在闲鱼上 5ber.eSIM 代理商处购买的 60 元的 Standard 实体卡，实际发货为 Premium。
* 2024 年 4 月 19 日，[有 Twitter (X) 用户声称](https://x.com/spatacus1986/status/1781149221644914848)，[其 5ber.eSIM 客户经理透露公司内部现在存在问题，不要继续发布 5ber.eSIM 的商业推广。](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/5ber-issue-1.jpeg)
* 2024 年 4 月 25 日，[5ber.eSIM 官方账号称](https://x.com/5beresim/status/1783018471267488124)：["这位同事离职而已😅。5ber 一直都在呢，社媒的内容也会持续更新。"](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/5ber-issue-3.jpeg)
* 2024 年 4 月 27 日，[eSTK.me](https://estk.me/?aid=171) 早鸟用户的预售订单已经提前发货。4 月 29 日将再次开放预售。
* 2024 年 4 月 28 日，[速易卡科技](https://shop104192953.m.taobao.com/)发布了[尿袋版（外置）eSIM 卡贴](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/syc-sim-sticker.pdf)，售价为 36 人民币。预置了多款 LPA 的 ARA-M 值，支持 EasyUICC、英飞凌和 syclpa 等 App 的切卡，是 5ber Standard 的绝佳搭配。对于华为手机，卡内预先下载一个号码，处于激活状态，不然不认卡。
* 2024 年 4 月，[5ber.eSIM](https://esim.5ber.com/) 发布了[团队公告](https://web.archive.org/web/20240426155057/https://esim.5ber.com/bulletin?language=zh-CN)，宣称"拥有自主知识产权，不受任何外部因素影响"。
* 2024 年 4 月 30 日，[eSTK.me](https://estk.me/?aid=171) 的早鸟用户逐步收到了 eSTK-400K，并[晒出了照片](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/estk-shaidan.jpg)。后续预购和现货用户将收到彩印纸质包装的产品。
* 2024 年 5 月 9 日，有网友[晒单了速易卡科技的新品](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/syc-new-package.png)，包含收纳盒、读卡器、SYC-1MB eUICC 和 nano SIM 转接板。
* 2024 年 5 月 13 日，闲鱼上的 5ber.eSIM Premium 已经降至 115 元。
* 2024 年 5 月 19 日半夜，名为 Sakura 卖家以"30 包邮 4 个，1 个起 10 块，10 个起 8 块，100 个 5块"的极低价格倾销来自 ECP 的消费者 eSIM。这些卡片的容量为 503KB，与 5ber.eSIM 位于同一个 EID 号段。内置 CI 为 GSM Association - RSP2 Root CI1 (`81370f5125d0b1d408d4c3b232e6d25e795bebfb`)。唯一的区别在于不含有 5ber.eSIM 的 ARA-M 值，因此无法使用 5ber.eSIM 的 LPA 进行管理。据悉第一批次（白卡）的卡片数量有 3000 张，第二批（内置 EasyUICC ARA-M）的卡片最快将于本周内提供。
* 2024 年 5 月 20 日，eSTK-400KB 开放现货销售。社区用户创建了两个 Android App 证书（[1](https://github.com/zdzym/sakurasim_key), [2](https://github.com/ShiinaSekiu/CommunityKey)）给 SakuraSIM，以便用户可以自签 App 实现 SakuraSIM 管理（如果后续加入了这两个证书的 ARA-M）。
* 2024 年 5 月 21 日，SakuraSIM 公布了含 EasyEUICC ARA-M 的卡片的定价："第一批每人每个地址限购 10 张，15 一张，5 张包邮"。
* 2024 年 5 月 22 日，有用户发现最初版本的 SakuraSIM 可以直接使用 5ber.eSIM 的 app 进行管理，甚至升级固件。此外，卡片还装有 5ber.eSIM 卡特有的 CI 证书（`0b1359633d2ab469761ca9d82b2229350db722d7`），这意味着 SakuraSIM 就是没有涂装的 5ber.eSIM 产品。同时，eSTK.me 发布了 [ESTKme-ECO](https://www.estk.me/product/estkme-eco/) 产品，价格比 eSTK-400KB 便宜 40 HKD，具备相同容量。
* 2024 年 5 月 27 日，SakuraSIM 通过微信发售。ESTKme-400K 已经绝版，只剩下量产版的 ESTKme-ECO 产品。
* 2024 年 5 月 30 日，SakuraSIM 开放了[微信群](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/sakura-wechat-group.jpg)和[快团团购买](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/sakura-ktt.jpg)。此次销售的为不含 ARA-M 的白卡，价格为 15 元/张，50 元 4 张。几小时后，因为被喷耍猴，SakuraSIM 关闭了微信群，并锁定了 Telegram 群。声称此后不会公开销售了，仅小范围提供。
* 2024 年 5 月 31 日，[5ber.eSIM 在小红书 repost 了中文公告](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/5ber-xhs-notice.webp)，但 [eSIM.me 仍然主张他们是业界唯一合法的可插拔 eSIM 品牌](https://esim.me/blog-about-esim#:~:text=counterfeit%20and%20illegal%20copies%20of%20esim.me%20cards)。
* 2024 年 6 月 1 日，SakuraSIM (ver 2) 以 [eSIM.re](https://esim.re/) 的品牌[重新上线了](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/esim-re.webp)，支持支付宝红包和 USDT 购买。[针对海外用户](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/esim-re-2.webp)定价为 USD 5.5 一张，国内用户定价为 USD 4.5 一张（折合约人民币 33 元），相当于 5ber.eSIM 普通版的半价。内含 [EasyEUICC](https://gitea.angry.im/PeterCxy/OpenEUICC) 和另外两个社区公开的 ARA-M [\[1\]](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/CommunityKey-main-1.zip) [\[2\]](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/CommunityKey-main-2.zip)。这意味着用户不仅可以使用 EasyEUICC（开源但签名的 key 不公开），还可以自行签名其他的 app 来操作卡片。根据 Whois 信息，其域名注册于 1 月 9 日。
* 2024 年 6 月 5 日，[eUICC Manual](https://euicc-manual.osmocom.org/) [正式捐赠](https://x.com/laf0rge/status/1798062755704160299?s=46)给 [Osmocom (Open Source Mobile Communications)](https://osmocom.org/) 项目。
* 2024 年 6 月 10 日，SakuraSIM 宣布无限期停止销售。eSIM.re 是由 SakuraSIM 发起人 @sakura_ryl 的好友 @cvv050 创建的，SakuraSIM 本人不参与运营，但交付的产品是一致的。目前 eSIM.re 处于无法访问的状态。
* 2024 年 6 月 22 日，[@Mjollnir](https://t.me/mjollnirs) 发布了 [iLPA](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/iLPA.webp) 的 [Testflight 内测](https://testflight.apple.com/join/M9UiN10c)。iLPA 是 iOS 平台的 eSIM 卡管理工具，通过 USB CCID 读卡器管理外部 eUICC 卡片。你也可以下载 [IPA 文件](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/iLPA_1.0.3_decrypted.ipa) 手动签名安装。
* 2024 年 6 月 26 日，eSTK.me 发布[彩色包装版本的 eSTK-400K](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/estk-400k-color.jpg)。
* 2024 年 6 月 27 日，[iLPA 正式上架 App Store](https://apps.apple.com/app/id6504213575)。eSTK.me 剧透了 [eSTKme-RED BLE/USB-C 读卡器](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/estkme-red-spoiler.jpg)。之后可能会搭配 iLPA 授权一起销售。
* 2024 年 6 月，一家名为 [SIMLINK LTD.](https://find-and-update.company-information.service.gov.uk/company/15751259) 的英国公司发布了 [9eSIM](https://www.9esim.com/) 产品，并[在淘宝上预售](https://item.taobao.com/item.htm?id=807878935283)（没有现货）。产品本体为一张 eUICC 白卡 (1MB) 和一个 BLE 读卡器。[微信小程序](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/9esim-ug.pdf)通过蓝牙连接，实现 eSIM 卡管理。社区给出的评价为：[灵车](https://t.me/Hearse_Drifting/3761)。[有网友"开源"了 9eSIM 的微信小程序源码](https://t.me/estkstock/380)。网友提供的[9eSIM 产品照片](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/9esim.pdf)。
* 2024 年 7 月 24 日，[网传 9esim 的 1MB 白卡为缺陷产品](https://www.nodeseek.com/post-137403-1#4)。
* 2024 年 7 月 25 日，[eSTKme-ECO](https://www.estk.me/product/estkme-eco/?aid=171) 现货销售。九折优惠码：`4JEMHFAS`。
* 2024 年 7 月 26 日，据悉是因为同行举报，ECP 要求停售 SakuraSIM 一代产品。
* 2024 年 8 月 5 日，名为 [Plan B Technology](https://shop126378180.taobao.com/) 的淘宝商家推出了 [planB 卡](https://item.taobao.com/item.htm?id=820906718446)，[使用闭源 LPA 管理](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/planb-demo.mp4)。定价为 136（Android 版，对标 5ber Premium）和 219 元（iOS 版，对标 5ber Ultra）。
* 2024 年 8 月 6 日，据悉 5ber.eSIM 推出 Ultra 版本，支持基于 STK 菜单的 Profile 切换，最多储存 15 个 eSIM Profile，其他部分等同于 5ber Premium。

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2Fmeme-5ber-ultra.webp&valid=true "5ber Ultra 表情")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/meme-5ber-ultra.webp)

* 2024 年 8 月 9 日，有用户发布了 [5ber.eSIM Ultra 的开箱视频](https://www.bilibili.com/video/BV1pSYeeVEgN/)，不过只展示了外包装，没啥看头。
* 2024 年 8 月 10 日，据 5ber.eSIM 小红书动态，5ber Ultra 版本将于 8 月 12 日正式发布。[据 eSTK.me 的消息](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/5ber-ultra-spoiler.webp)，"5ber ultra 还是 89086，容量没变但多了功能实际容量小了。封锁了所有读卡器，必须用 5ber app 管理。iOS 只支持切换，不支持删除，备注，下载。不仅封锁了读卡器，还特意封锁了 Open、EasyEUICC/小米解锁原生管理模块/OMAPI Bypass 模块。定价比 5ber premium 预计贵 60-70 元人民币"。考虑到 5ber 具备 OTA 能力，这个限制可能可以通过 OTA 下发给现存的 Standard 和 Premium 卡片，建议用户慎重更新。

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2Fmeme-5ber-ecp.webp&valid=true "5ber 新固件表情")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/meme-5ber-ecp.webp)

* 2024 年 8 月 12 日，[5ber Ultra 正式发布](https://esim.5ber.com/ultraorder)，定价 USD 28，折合人民币 200 元。相比 [eSTKme-ECO](https://www.estk.me/product/estkme-eco/?aid=171) 170 港币（折合人民币 156）的定价而言，没有什么竞争力。
* 2024 年 8 月 16 日，eSTK.me 为 eSTK-400K 的早鸟用户推出了 [eSTK-ECO 三折优惠码](https://www.estk.me/standalone/400k_coupons/)，折后为 HKD 56.7（人民币 52 元）。此外，据悉 [9eSIM（坊间称为"9ber"）预计于 11 月推出 STK 切卡，对标 5ber Ultra](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/9esim-iOS.webp)。[9ber 的销售称](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/9esim-personas.webp)，"我后面看了一下后台，我们的人群画像里面 62% 的人是本科。以前做电商用户素质群里是没有你们那么高的。有时候和你们打交道都感觉好轻松。比较讲道理，有素质。"据悉，9ber 的 2MB 新产品的固件占用约 400KB，因此标注可用空间 1.6MB。

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2Fmeme-ecp.webp&valid=true "ECP 表情")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/meme-ecp.webp)

* 2024 年 8 月 17 日，[9ber 流出了](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/9ber-ecp-lpa.webp) PlanB 所使用的 [LPA 安装包](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/LPAd-Android-OMA_2.0.1.apk) 以及[对应的逆向工程项目](https://github.com/CursedHardware/ecp-lpa-sdk-decompiled/)。根据源码和签名证书所示，所谓"从头到尾都是我们自己做的"的 LPA 其实是 ECP 开发的项目，其商品评论区的晒带图片也与早前 SakuraSIM 的 ECP 白卡完全一致。

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2Fplanb-genuine.webp&valid=true "东西从头到尾都是我们自己做的")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/planb-genuine.webp)

* 2024 年 8 月 18 日，SakuraSIM 限量发售了 500 张二代卡，价格为 15 元每张。
* 2024 年 8 月 19 日，据悉 eSTK 代理商流洋[注册了 5ber、estk.esim、evesim 和 kesim 等多个商标](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/liuyang-icon.webp)。[eSTKme-RED](https://www.estk.me/product/estkme-red/) 蓝牙、USB-C 读卡器工程版开放了预售。
* 2024 年 8 月 22 日，PlanB eSIM 上线了[官方网站](https://planbesim.com/)，产品定价分为 9、19 和 29 美元，对标 5ber Standard、Premium 和 Ultra。此外官网还揭示了[OEM 贴牌 (white label) 服务](https://planbesim.com/white-label/)。不过事实上，PlanB 的产品本身就是 ECP 的白卡。
* 2024 年 8 月 23 日，[9eSIM 的 Android LPA 程序被发现是 EasyEUICC 套壳](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/9esim-apk.webp)。
* 2024 年 8 月 30 日，[PlanB 宣布跳票](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/planb-bounced.webp)。9eSIM 正在与 Kigen 开发新产品。
* 2024 年 9 月 1 日，[LuckySIM](https://emaster.luckysim.com.hk/) 基于 ECP 的 OEM 方案推出了 eMaster eSIM 卡，可以写入最多 10 张 LuckySIM 或 Lucky2 的 eSIM profile。本质上，它是一张仅能写入 ICCID 为 LuckySIM (89852000008) 和 Lucky2 (89852000163) 的可插拔 eSIM 白卡。鉴定为不如 5ber。

7. 常见问题
-------

### M2M eUICC

M2M eUICC 与 Consumer eUICC（消费者 eSIM）都属于标准的 GSMA eSIM 实现，但 M2M eUICC 不能写入 Consumer eSIM Profile，只能通过原厂的 OTA 平台进行云管理，仅用于集中管理 IoT 场景（例如共享单车）。若读者想进一步了解 M2M 和 Consumer eSIM 区别，可以参考下文部分的参考文献。

### 国行 Android 能否支持 eSIM？

* 华为和荣耀可以识别并使用 eSIM，但由于 ROM 阉割了 eUICCManager，无法使用内置 LPA 管理 eSIM 配置。
* 如果你的 ROM 没有阉割掉 `eUICCManager`，可能可以使用 Android 原生的 LPA 管理 eSIM。已知国行小米 13 刷入 MIUI 国际版，可以使用系统内置 LPA 管理 5ber.eSIM 的 eUICC（ST33 白卡同理）。
* 如果你 root 了，可以尝试上文提到的 OpenEUICC 项目。[高通基带的手机可能无法使用 OpenEUICC](https://www.v2ex.com/t/1013989)。

### eSIM.me 和 5ber.eSIM 如何实现在没有 eUICCManager 的 Android 设备上管理 eSIM？

根据[这篇博客](https://cheerio-the-bear.hatenablog.com/entry/2022/03/04/172109)和[这篇博客](https://www.esper.io/blog/android-dessert-bites-24-esim-me-1248143)，eSIM.me 的 App（即 LPA）使用 [Open Mobile API (OMAPI)](https://source.android.com/docs/security/features/open-mobile-api) 与 UICC 进行通信，而非标准的 [eUICC API](https://source.android.com/docs/core/connect/esim-euicc-api)。5ber.eSIM 也是如此。这也正是它们产品的使用场景：在不支持原生 eSIM 管理（LPA）的设备上使用 eSIM。

eUICC 使用 ARA-M 字段储存 Android 开发者证书的 SHA-1 或者 SHA-256 值，从而告知 Android 系统来自哪个开发者的应用可以访问自身，容许第三方 App 提权获得 Carrier Privileges。因此，用户只能使用特定的 App 通过 OMAPI 管理 eUICC。eSTK.me 可以宣告五个 ARA-M SHA-1 值，因此同时支持 5ber.eSIM、eSIM.me 和 [EasyUICC](https://gitea.angry.im/PeterCxy/OpenEUICC) 等 App。

OMAPI 是 Android 为外置安全组件（Secure Element，SE）提供的标准接口。eUICC 是智能卡（Smart Card）的一种，因此用 OMAPI 与 eUICC 通信是 by design 的，算不上 hack。至于 eSIM.me 想因此起诉 5ber.eSIM，是没有依据的。版权应该只保护代码实现，而不是接口。

查看 5ber.eSIM 的 min SDK 版本，可知 5ber 最低兼容 Android 5.0：

|-------------|---------------------------------------------------------|
| ``` 1 2 ``` | ``` $ apkanalyzer manifest min-sdk 5ber.eSIM.apk 21 ``` |

* 在 Android 5-8 上，使用第三方的 [Smartcard API](https://github.com/seek-for-android/pool/wiki/UsingSmartCardAPI) 访问 eUICC。
* 在 Android 9 之后，使用 Android 集成的 OMAPI 访问 eUICC。

关于 OMAPI 的更多细节请参考 [eUICC Manual](https://euicc-manual.osmocom.org/docs/android/open-mobile-api/)。

### 什么是 EID？

[eUICC Identifier](https://www.gsma.com/services/esim-eis/)（简称：EID）是 eUICC (embedded UICC) 的全球唯一物理标识（类似于网卡的 MAC 地址），存储在 eUICC 的 ECASD (eUICC Controlling Authority Security Domain) 中，主要用于 eUICC 卡管理和远程配置。EID 可以被读取但不能被更改，在远程配置中和 ICCID 一起共同关联某个 Profile 信息。

下图是 [GSMA SGP.29 规范](https://web.archive.org/web/20240304134706if_/https://www.gsma.com/esim/wp-content/uploads/2020/07/SGP.29-1.0.pdf)对于 EID 的格式定义。

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2FEID.jpg&valid=true "EID format")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/EID.jpg)

### 为什么 Virtual EID 只能骗 app 不能骗 RSP？

EID 是 EUM 使用对应的 EUM 证书签发的 eUICC 证书的序列号。执行 Profile 下载过程时，eUICC 与 SM-DP+ 交换证书信息，并用上游的证书来验证其合法性。

当 LPA 使用 OMAPI 与 eUICC 通信时，使用 [ES10c#GetEID](https://www.gsma.com/esim/wp-content/uploads/2020/06/SGP.22-v2.2.2.pdf#page=204) 方法获取 Hex 形式的 EID。因此，eSTK.me 的 vEID 只能欺骗依赖此行为获取 EID 的 App，而无法欺骗 SM-DP+ 和使用 eUICC 证书验证的 App。

下图为 [eSIM、LPA、网络与 SM-DP+ 之间的通讯过程](https://web.archive.org/web/20240401133154if_/https://www.docomo.ne.jp/english/binary/pdf/corporate/technology/rd/technical_journal/bn/vol19_2/vol19_2_002en.pdf)：

[![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fiecho.cc%2F2023%2F10%2F20%2FConvert-eSIM-to-physical-SIM%2FeSIM-LPA-RSP.jpg&valid=true "eSIM、LPA、网络与 SM-DP+ 之间的通讯过程")](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/eSIM-LPA-RSP.jpg)

### 无法读取 eSIM 卡片（通用）

1. 购买的读卡器并非 PC/SC 标准兼容，无法被系统识别。
2. 未安装正确的读卡器驱动。
3. 卡片没插好。
4. 卡片损坏------ ST33 芯片非常脆弱，施加外力会导致芯片损坏。

### macOS 无法读取 eSIM 卡片

在 macOS Sonoma 上使用 LPA 操作 eUICC 时可能会遇到以下错误：

* 使用 [lpac](https://github.com/estkme-group/lpac)：`SCardTransmit() failed: 80100016`
* 使用 [Truphone/LPAdesktop](https://github.com/Truphone/LPAdesktop) 或 [sparkcyf/LPAdesktop](https://github.com/sparkcyf/LPAdesktop)：`SCARD_E_NOT_TRANSACTED`

这是 Apple 自行开发的 USB CCID 智能卡读卡器驱动在 macOS Sonoma 上的 bug：

* [Apple's own CCID driver in Sonoma](https://blog.apdu.fr/posts/2023/11/apple-own-ccid-driver-in-sonoma/)
* [macOS Sonoma bug: SCardControl() returns SCARD_E_NOT_TRANSACTED](https://blog.apdu.fr/posts/2023/09/macos-sonoma-bug-scardcontrol-returns-scard_e_not_transacted/)

建议更新至最新的 macOS Sonoma 14.4 Beta，或遵照上文替换读卡器驱动。

### 如何批量获取 Consumer eSIM

如果您是 eSIM 从业者，可以通过以下渠道采购符合 SGP.26 标准的 Consumer eSIM 测试卡：

* [Sysmocom](https://sysmocom.de/)
* [Comprion](https://www.comprion.com/)

如果您是普通用户，可以通过[速易卡科技](https://shop104192953.m.taobao.com/)购买 MFF2 或 nano SIM 形式的 eUICC。

### eUICC Manufacturer (EUM)

eUICC Manufacturer (EUM) 是 eUICC 卡片的制造商，通过 EID 的 8 位前缀进行区分。

你可以在 [eUICC Manual](https://euicc-manual.osmocom.org/docs/pki/eum/) 查询已知的 EUM 信息。

### 使用 RSP Dump 提取 eUICC 的 CI、EUM 等信息

[RSP Dump](https://rsp.septs.app/) 是基于 AWS Lambda 的中间件。它拦截（intercepts）LPA 与 SM-DP+ 之间的通信，提取 eUICC 卡片的 CI、EUM、EUM 证书、eUICC 证书、EID、剩余空间等信息，并发送至用户指定的邮箱。

只需将 `rsp.septs.app` 作为 SM-DP+ 地址，将邮箱地址作为 Matching ID（也就是 eSIM Activation Code），执行下载 Profile 操作，即可收到邮件。

对应的命令行操作：`lpac.exe profile download -s rsp.septs.app -m 邮箱`

邮件附件为 EUICCInfo2 和提取到的 EUM、eUICC 证书。

邮件正文格式大致如下：

|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ``` 1 2 3 4 5 6 7 8 9 10 11 12 13 ``` | ``` EID: 8903302300121136000000000XXXXXXX Issuer: 665a1433d67c1a2c5db8b52c967f10a057ba5cb2 Free NVRAM: 359.73 KiB SGP.22 Version: 2.2.0 SAS Accreditation Number: ?????????? If you need to download other CIs, please run: ./lpac profile download -s "cdf6d1.rsp.septs.app" -m "邮箱" ./lpac profile download -s "7c0e54.rsp.septs.app" -m "邮箱" ./lpac profile download -s "4eb94e.rsp.septs.app" -m "邮箱" ./lpac profile download -s "062a9a.rsp.septs.app" -m "邮箱" ``` |

### Certificate Issuer (CI)

阅读本章节之前，建议先阅读 [GSMA: eSIM 白皮书（中文翻译）](https://zhuanlan.zhihu.com/p/106904288)。

你可以在 [eUICC Manual](https://euicc-manual.osmocom.org/docs/pki/ci/) 查询到已知的 CI 信息。

根据 [GSMA 信息](https://www.gsma.com/esim/gsma-root-ci/)，目前消费者 eSIM 的证书颁发者有 DigiCert 和 WISeKey。

根据 [PKI 数字证书在 eSIM 安全上的应用研究 \| 中国联通研究院](https://web.archive.org/web/0if_/https://mp.weixin.qq.com/s/dcpsUlplik62kGZSSFZkEA)：GSMA 特别准许国内运营商自己选择 CI，CA 证书签发者必须是工业与信息化部公布的具有电子认证服务行政许可的认证机构，目前，三家运营商各自有 CA，国内的电信终端产业协会 (TAF) 也是具备为 eSIM 平台及 EUM 颁发证书的 CA。

根据 eSTK.me 和速易卡科技的信息，目前市面上存在同时支持 GSMA 和国内 CI 的 eUICC 卡片（内置了 CI 的根证书），可以同时写入国内运营商和国外运营商的 eSIM Profile。比如说，前文提到的 iPad 10 (A3162) 国行版。

根据 SGP.22 标准中关于 `ES9+.InitiateAuthentication` 函数的定义：SM-DP+ 会返回 `serverCertificate` 给 LPA。

你可以使用 [Infineon LPA](https://github.com/CursedHardware/infineon-lpa-mirror)、[LPAc](https://github.com/estkme-group/lpac) 或 [EasyEUICC](https://gitea.angry.im/PeterCxy/OpenEUICC) 读取 eSIM 中的 `euiccCiPKIdListForVerification` 和 `euiccCiPKIdListForSigning`信息，对比 RSP 所支持的 CI，从而判断此 eSIM 卡片是否支持该 RSP（以及使用该 RSP 的运营商）。

以下是中国区 RSP 及其支持的 CI：

* 中国信通院：`www.esimtest.chinattl.cn`

  * Taier eSIM Root CA: `148030fc246c02ff222106125a8d6bda990afbe9`
  * China Unicom eSIM Root CA: `16b5d16048e3ea02bd4b606e5f77a4bf20808d83`
  * Symantec Corporation RSP Test Root CA: `665a1433d67c1a2c5db8b52c967f10a057ba5cb2`
  * Test CI: `f54172bdf98a95d65cbeb88a38a1c11d800a85c3`
* 中国移动：`esim.yhdzd.chinamobile.com:8001`

  * Taier eSIM Root CA: `148030fc246c02ff222106125a8d6bda990afbe9`
  * China Unicom eSIM Root CA: `16b5d16048e3ea02bd4b606e5f77a4bf20808d83`
  * CMCA eSIM Root CA_NIST: `cdf6d1c0a7b07f98a861b6e378b82f648d99663e`
  * CCS NETCA eSIM ECC RootCA: `d3ef83fc503f9c6ec4b7f6ae055b7f1373d4ab1e`
* 中国电信：`esimapple.crm.189.cn`

  * Taier eSIM Root CA: `148030fc246c02ff222106125a8d6bda990afbe9`
  * China Unicom eSIM CA: `3bd3f57b34f44436e08f028b5101c0e0a9b0986e`
  * China Unicom eSIM Root CA: `16b5d16048e3ea02bd4b606e5f77a4bf20808d83`
  * NETCA: `4eb94ea05b451a729cc5272ddf66f481701a05c9`
  * CMCA eSIM Root CA_NIST: `cdf6d1c0a7b07f98a861b6e378b82f648d99663e`
  * CCS NETCA eSIM ECC RootCA: `d3ef83fc503f9c6ec4b7f6ae055b7f1373d4ab1e`
* 中国联通：`esim.wo.com.cn`

  * Taier eSIM Root CA: `148030fc246c02ff222106125a8d6bda990afbe9`
  * China Unicom eSIM CA: `3bd3f57b34f44436e08f028b5101c0e0a9b0986e`
  * China Unicom eSIM Root CA: `16b5d16048e3ea02bd4b606e5f77a4bf20808d83`
  * CMCA eSIM Root CA_NIST: `cdf6d1c0a7b07f98a861b6e378b82f648d99663e`
  * CCS NETCA eSIM ECC RootCA: `d3ef83fc503f9c6ec4b7f6ae055b7f1373d4ab1e`

根据以上列表可以发现，三大运营商（中国移动、中国联通、中国电信）和中国信通院的 RSP 都交叉信任了对方的 CI，因此，若 eUICC 拥有任意国内运营商的 CI，即可写入所有国内运营商的 eSIM Profile。

* 一部分中国区 RSP 的证书可以从[这里](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/china-rsp-certs.7z)下载
* 几乎完整的 RSP 证书列表可以从[这里](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/complete-rsp-certs.7z)下载

申请 eUICC 证书请联系[证书签发主管单位](https://www.taf.org.cn/BusinessPublish.aspx)。

### 购买 eSIM 兼容的手机

* [GSMA eSIM 手机列表](https://www.gsmarena.com/search.php3?sAvailabilities=1,2&sSIMTypes=4)
* [GSMA eSIM 手机列表的 150 USD（约折合 1100 CNY）以内的低端带 eSIM 手机筛选](https://www.gsmarena.com/results.php3?nPriceMax=150&sSIMTypes=4&sOSes=2)

8. 扩展阅读
-------

### 技术演进

* [eUICC Development History - eUICC](https://euicc-manual.osmocom.org/docs/history/)
* （推荐阅读）[浅谈 SIM 卡虚拟化及云服务的发展趋势 - 龚智辉](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/%E6%B5%85%E8%B0%88%20SIM%20%E5%8D%A1%E8%99%9A%E6%8B%9F%E5%8C%96%E5%8F%8A%E4%BA%91%E6%9C%8D%E5%8A%A1%E7%9A%84%E5%8F%91%E5%B1%95%E8%B6%8B%E5%8A%BF.pdf)：eSIM 和 Soft SIM 的技术演进和行业应用。
* （推荐阅读）[The ingenious product that brings eSIM to any Android phone](https://www.esper.io/blog/android-dessert-bites-24-esim-me-1248143)：eSIM.me 如何使用 OMAPI 与 UICC 进行通信。
* [SIM card technology from A-Z](https://media.ccc.de/v/36c3-10737-sim_card_technology_from_a-z) ([备份链接](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/SIM%20card%20technology%20from%20A-Z.pdf))：a look at SIM card technology during the past almost 30 years.
* [为物联网 OEM 带来更大的自由度 - truphone](https://web.truphone.com/globalassets/assets/reports/truphone-iot-beecham-esim-analysis-report-v1.1-2021-cn.pdf) ([备份链接](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/truphone-iot-beecham-esim-analysis-report-v1.1-2021-cn.pdf))：M2M/IoT eSIM 市场分析。
* （推荐阅读）[GSMA: eSIM 白皮书（中文翻译）](https://zhuanlan.zhihu.com/p/106904288)
* [eSIM Whitepaper: The what and how of Remote SIM Provisioning - GSMA](https://www.gsma.com/esim/wp-content/uploads/2018/12/esim-whitepaper.pdf) ([备份链接](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/esim-whitepaper-gsma.pdf))
* [eSIM Introduction - GSMA](https://forums.quectel.com/uploads/short-url/aCFNp1v9fRZtWU9mucGbJy3N0rq.pdf)
* [About eSIM Cards - osmocom](https://discourse.osmocom.org/t/about-esim-cards/80) ([备份链接](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/about-esim-cards.pdf))
* [Open Mobile API: Accessing the UICC on Android Devices](https://arxiv.org/abs/1601.03027) ([备份链接](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/1601.03027.pdf))
* [ravens/awesome-telco: A curated list of telco resources and projects](https://github.com/ravens/awesome-telco)
* [eSIM for Consumer Devices toward Expanded eSIM Usage̶](https://web.archive.org/web/20240401133154if_/https://www.docomo.ne.jp/english/binary/pdf/corporate/technology/rd/technical_journal/bn/vol19_2/vol19_2_002en.pdf)

### 标准与规范

* [EID 管理实施规定 - 电信终端产业协会](https://www.taf.org.cn/Guide_Eid.aspx)：中国大陆已分配发行方 ID 列表和 EID 编码格式。
* [GSMA Certificate Issuer (CI)](https://www.gsma.com/esim/gsma-root-ci/)
* [GSMA SGP.29](https://web.archive.org/web/20240304134706if_/https://www.gsma.com/esim/wp-content/uploads/2020/07/SGP.29-1.0.pdf): EID Definition and Assignment Process
* [GSMA eSIM M2M Compliance](https://www.gsma.com/esim/what-is-m2m-compliance/)
* [GSMA eSIM Consumer Compliance](https://www.gsma.com/esim/compliance/)
* [GSMA SGP.01](https://www.gsma.com/esim/resources/sgp-01-v4-3/): a common architecture framework to enable the remote Provisioning and management of the Embedded UICC (eUICC) in Devices which are not easily reachable, and additionally a way to locally switch to specific Profiles for testing/certification or emergency cases.
* [GSMA SGP.21](https://www.gsma.com/esim/resources/sgp-21-v2-5/): the architecture and technical requirements for Remote SIM Provisioning of all device types across all consumer markets.

### eUICC

* （推荐阅读）[eUICC 开发者手册](https://euicc-manual.osmocom.org/)
* [eSTK.me 文档](https://docs.estk.me/)
* [eSTK.me 固件归档](https://t.me/estkmefirmwarebackup)
* [eSIM.me SIM Card with Windows - Zero Log](https://log.zero.root.me/thoughts/esimme-sim-card-with-windows)
* [eUICC 通用物理电气特性及传输协议检验标准 V1.0](https://www.taf.org.cn/upload/notice/2022-0125-140433-2084440682.pdf)

9. 其他参考
-------

* [eSIM.me を Windows 11 の LPA で使用する - クマは森で用を足しますか？](https://cheerio-the-bear.hatenablog.com/entry/2022/09/05/003328)
* [eSIM 版 iPhone 4s](https://www.bilibili.com/video/BV1vN4y1o7Xw)
* [使用 eSTK.me 的 Fake EID 欺骗 eSIM.me 和 5ber 的 App](https://www.bilibili.com/video/BV1Y8411r7kE)
* [通过 PC/SC 智能卡读卡器配置 esim.me 的 SIM 卡 - Sparktour's](https://sparktour.me/2022/11/20/configure-esim-me-card-with-pc-sc-reader/)
* [A tricky way to use eSIM on CN/IN variant - XDAForums](https://xdaforums.com/t/a-tricky-way-to-use-esim-on-cn-in-variant.4609543/)
* [让普通手机支持 esim 的方法（基于速易卡科技对 esim.me 进行平替）- Frienkie](https://frienkie.eu.org/posts/2816769116/)
* [Demystifying eSIM Technology - Hacker News](https://news.ycombinator.com/item?id=37200284)
* [较低价格的 eSIM.me 平替 - V2EX](https://www.v2ex.com/t/954177)
* [简单评测下无 eSIM 手机的 eSIM 方案，5ber - 美卡论坛](https://www.uscardforum.com/t/topic/190872/54)
* [软 SIM 卡 - 基于高通/联发科技/紫光展锐等平台的 Soft SIM](https://softs.im/)

10. 截图素材
--------

* [eSIM 安装失败截屏汇总](https://imgur.com/a/v1YR9gw)
  * [Screenshot of Cannot connect to network failure (1)](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/demo-cannot-connect-to-network-1.png)
  * [Screenshot of Cannot connect to network failure (2)](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/demo-cannot-connect-to-network-2.png)
  * [Screenshot of incorrect QR code failure](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/demo-Incorrect-qr-code.png)
  * [Screenshot of SIM already downloaded failure](https://iecho.cc/2023/10/20/Convert-eSIM-to-physical-SIM/demo-sim-already-downloaded.png)

11. 致谢
------

感谢 [eSTK.me](https://estk.me/?aid=171)、[速易卡科技](https://shop104192953.m.taobao.com/)和不愿意透露 ID 的匿名网友对文本的校对和补充。

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7231538872109238989)
