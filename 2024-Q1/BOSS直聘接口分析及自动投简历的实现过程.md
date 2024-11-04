BOSS直聘接口分析及自动投简历的实现过程
=====================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/594912897)压码路物联网/大数据/ai/爬虫/小程序/app等各类软件开发

这两年疫情，公司业务越来越差，必须得准备后路了，每天睡前都会在直聘上打一遍招呼，一直到打哈欠有睡意为止...,这样持续了一周，发现很难坚持，身为一名资深蜘蛛侠，怎么能这样下去呢？于是便萌生了对BOSS下手的念头。 boss的web端功能已经挺完整了，所以直接使用无头浏览器(puppetter/playwright)应该就能搞定了，然后再整几个简单的界面，应该就差不多了。先看前端它用了哪些技术。  
web框架：vue+jQuery 熟悉的三件套
![](https://image.cubox.pro/cardImg/2024020223472025234/99770.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

经典的$
![](https://image.cubox.pro/cardImg/2024020223472015932/30841.jpg?imageMogr2/quality/90/format/gif/ignore-error/1)
![](https://image.cubox.pro/cardImg/2024020223472180753/30433.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

聊天：基于websocket的mqtt实现 paho
![](https://image.cubox.pro/cardImg/2024020223472197773/96908.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

消息传输格式protobuf,和抖音一样，找到定义文件就能解析了
![](https://image.cubox.pro/cardImg/2024020223472188008/21180.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

接口分析 要实现自动投简历，会用到以下一些接口,安全起见完整地址就不贴了，懂得搜一下就能找到。  
职位搜索joblist.json,看字段名就能猜到什么意思

    {    
    "code": 0,
        "message": "Success",
        "zpData": {
            "resCount": 415,
            "filterString": "",
            "lid": "xxx",
            "hasMore": true,
            "jobList": [
                {
                    "securityId": "xxx",
                    "bossAvatar": "xxx",
                    "bossCert": 3,
                    "encryptBossId": "xxx",
                    "bossName": "xxx",
                    "bossTitle": "渠道经理",
                    "goldHunter": 0,
                    "bossOnline": false,
                    "encryptJobId": "xxx",
                    "expectId": 0,
                    "jobName": "需求分析工程师",
                    "lid": "xxx",
                    "salaryDesc": "10-15K·13薪",
                    "jobLabels": [
                        "1-3年",
                        "本科"
                    ],
                    "jobValidStatus": 1,
                    "iconWord": "",
                    "skills": [
                        "需求分析"
                    ],
                    "jobExperience": "1-3年",
                    "daysPerWeekDesc": "",
                    "leastMonthDesc": "",
                    "jobDegree": "本科",
                    "cityName": "上海",
                    "areaDistrict": "浦东新区",
                    "businessDistrict": "张江",
                    "jobType": 0,
                    "proxyJob": 0,
                    "proxyType": 0,
                    "anonymous": 0,
                    "outland": 0,
                    "optimal": 0,
                    "iconFlagList": [],
                    "itemId": 1,
                    "city": xxx,
                    "isShield": 0,
                    "atsDirectPost": false,
                    "encryptBrandId": "xxx",
                    "brandName": "xxx",
                    "brandLogo": "xxx",
                    "brandStageName": "已上市",
                    "brandIndustry": "计算机软件",
                    "brandScaleName": "1000-9999人",
                    "welfareList": [
                        "零食下午茶",
                        "补充医疗保险",
                        "通讯补贴",
                        "五险一金",
                        "股票期权",
                        "带薪年假",
                        "员工旅游",
                        "节日福利",
                        "定期体检",
                        "交通补助",
                        "餐补",
                        "年终奖"
                    ],
                    "industry": 100021,
                    "contact": false
                }
             ]
        }
    }

<br />

获取简历attachment/checkbox

    {
        "code": 0,
        "message": "Success",
        "zpData": {
            "supportVideoResume": false,
            "resumeList": [
                {
                    "resumeId": "xxx",
                    "showName": "全栈开发.docx",
                    "resumeSize": 10000,
                    "resumeSizeDesc": "34.9KB",
                    "suffixName": "docx",
                    "annexType": 0,
                    "uploadTime": "xxx",
                    "parserId": "xxx",
                    "syncStatus": 1,
                    "previewType": 1,
                    "restricted": false,
                    "cvId": "",
                    "securityStatus": 0,
                    "restrictedDays": -1,
                    "target": 0,
                    "nlpParserType": 1
                },
                {
                    "resumeId": "xxx",
                    "showName": "资深前端.docx",
                    "resumeSize": 12345,
                    "resumeSizeDesc": "34.9KB",
                    "suffixName": "docx",
                    "annexType": 0,
                    "uploadTime": "xxx",
                    "parserId": "xxxx",
                    "syncStatus": 1,
                    "previewType": 1,
                    "restricted": false,
                    "cvId": "",
                    "securityStatus": 0,
                    "restrictedDays": -1,
                    "target": 0,
                    "nlpParserType": 1
                }
            ],
            "videoResumeList": [],
            "supportAnnexType": false,
            "supportCommonResume": true,
            "showUploadBtnType": false,
            "complete": true,
            "maxCount": 3,
            "resumeCount": 3
        }
    }

<br />

打招呼friend/add post form

    {
        "code": 0,
        "message": "Success",
        "zpData": {
            "showGreeting": true,
            "securityId": "xxx",
            "bossSource": 0,
            "source": "",
            "encBossId": "xxx",
            "greeting": "个人觉得我和贵公司这一岗位很匹配，可以聊聊么？"
        }
    }

    作者：压码路
    链接：https://juejin.cn/post/7181445693293199420
    来源：稀土掘金
    著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。

<br />

投简历exchange/request post form  
mqtt消息分析 分析这里面的消息类型，花了不少时间找规律，通过type+body.type+biztype基本就能确定唯一的消息类型

    {
            "from": {
                "uid": xxx,
                "name": "xxx",
                "avatar": "xxx",
                "company": "xxx",
                "headImg": 8,
                "certification": 3,
                "source": 0
            },
            "to": {
                "uid": xxx,
                "name": "xxx",
                "avatar": "xxx",
                "company": "",
                "headImg": 0,
                "certification": 0,
                "source": 0
            },
            "type": 1,
            "mid": xxx,
            "time": xxx,
            "body": {
                "type": 1,
                "templateId": 1,
                "headTitle": "",
                "text": "好",
                "sound": null,
                "image": null,
                "action": null,
                "articles": [],
                "notify": null,
                "dialog": null,
                "jobDesc": null,
                "resume": null,
                "redEnvelope": null,
                "orderDetail": null,
                "hyperLink": null,
                "video": null,
                "interview": null,
                "jobShare": null,
                "resumeShare": null,
                "atInfo": null,
                "sticker": null,
                "chatShare": null,
                "interviewShare": null,
                "listCard": null,
                "starRate": null,
                "frame": null,
                "multiImage": null,
                "extend": ""
            },
            "offline": false,
            "received": false,
            "pushText": "xxx",
            "taskId": 0,
            "cmid": xxx,
            "status": 0,
            "uncount": 0,
            "pushSound": 0,
            "flag": xxx,
            "encryptedBody": null,
            "bizId": null,
            "bizType": null,
            "securityId": "xxx",
            "isPresenceMsg": false,
            "isSelf": false
        }

下面是成品的界面

**第一步：添加账号**   
点击"添加账号"按钮  
![](https://image.cubox.pro/cardImg/2024020223472235350/25350.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

用boss直聘app扫码登录账号  
![](https://image.cubox.pro/cardImg/2024020223472223765/48380.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

出现boss账号头像代表登录成功  
![](https://image.cubox.pro/cardImg/2024020223472269718/42789.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

**第二步：添加求职任务**   
点击"求职计划"，然后点击右上角的"+"按钮  
![](https://image.cubox.pro/cardImg/2024020223472299486/71728.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

设置求职条件  
![](https://image.cubox.pro/cardImg/2024020223472350264/92530.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

注意事项：  
1、 职位关键字必须填写，比如你要找项目经理，那么关键字就填写"项目经理"。  
2、 投递间隔即每隔多少秒向下一个职位的boss打招呼，具体值会在范围内随机生成。建议设为5\~10秒，如果太频繁，可能会被识别为机器人。  
3、 投递简历如果选择，那么该求职计划搜索的所有职位都将投递选择的简历，如果不选，那么会按职位与简历名称进行匹配，自动选择相似度最高的简历投递。投递为完全自动，只要boss向你发出投递简历邀请，那么本工具会自动帮你接收邀请并投递。  
4、 招呼语默认使用boss app里配置的招呼语，如果要使用这里的招呼语，需要先关闭boss app里的自动招呼语。  
点击"保存"按钮后，出现提示框，点击"开始"  
![](https://image.cubox.pro/cardImg/2024020223472369277/38391.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

接下来工具就会按顺序向符合条件的所有职位的boss打招呼和自动投简历了。  
所有打过招呼的职位都会在列表里显示  
![](https://image.cubox.pro/cardImg/2024020223472340762/39591.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

**第三步：消息自动处理**   
本工具已将部分规范消息做了自动处理，比如简历投递邀请、交换联系方式请求等，而且会将其设置为已读，也就不会再出现在app的提醒里。但是有些非标准的消息，例如："你做过XXX类项目吗"，这类消息你可以在app上手工回复，也可以在工具里为其配置自动回复规则，尽可能减少你的人工操作。可按下面的方式配置自动回复规则，点击"配置"按钮  
![](https://image.cubox.pro/cardImg/2024020223472330922/51125.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

点击"添加"按钮  
![](https://image.cubox.pro/cardImg/2024020223472497296/77468.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

填写规则  
![](https://image.cubox.pro/cardImg/2024020223472446400/92842.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

规则填写说明：  
比如我要匹配消息内容中包含"简历"两个字的，然后执行自动发简历的操作，那么如下配置即可  
![](https://image.cubox.pro/cardImg/2024020223472498821/85822.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

点击"确定"，再点击"保存"。  
多个关键字匹配有两种方式：  
1、 A和B(A\&B)：即消息内容中既要包含A也要包含B，比如我要匹配"你目前工资多少"和"你目前薪资多少"这两类消息，他们的共同点是都包含"你"和"资多少"，那么规则可配置为"你\&资多少"。  
![](https://image.cubox.pro/cardImg/2024020223472578525/39520.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

2、 A或B(A\|B)：即消息内容中要么包含A要么包含B，仍然以匹配"你目前工资多少"和"你目前薪资多少"这两类消息为例，要么包含"工资多少"，要么包含"薪资多少"，那么规则可配置为"工资多少\|薪资多少"。  
![](https://image.cubox.pro/cardImg/2024020223472562547/40933.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

下面是一些常用回复规则供参考  
![](https://image.cubox.pro/cardImg/2024020223472525645/76158.jpg?imageMogr2/quality/90/ignore-error/1)

<br />

左侧的上下箭头按钮用于调整优先级，每条消息都会按顺序从上到下匹配你设置好的规则，一旦完成匹配，就不会再匹配后面的规则。匹配不上的将会在app内提醒，你再手工回复。  
如有问题，欢迎及时反馈！微信：keyiis2017

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7152641706972678704)
