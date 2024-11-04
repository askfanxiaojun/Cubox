不需要爬虫也能轻松获取 unsplash 上的图片
=========================

[zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/139132649)测试的能量

我经常会使用 unsplash， 这里面的图片非常清爽，我的大多数文章的图片都是在这个网上找的，虽然也有同类型网站，但是用过一段时间以后基本都放弃了，图片质量参差不齐，筛选过程太费劲。

但是 unsplash 访问速度是个大问题，我经常会因为图片无法加载而被劝退。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic3.zhimg.com%2Fv2-e8bb71662d79e7bec97b1c248a6d55ae_b.jpg&valid=true)

今天一时手痒，顺手搜了 unsplash api 这个关键字，看官方有没有提供相关的 api 服务，还真有！
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic3.zhimg.com%2Fv2-3b4073a54a0e6f2624c8bd02633dfba6_b.jpg&valid=true)

unsplash 提供了 2 个版本的 API。 一个是简单版，主要是给小型应用，流量比较少的 app 使用，可以通过 [http://source.unsplash.com](https://link.zhihu.com/?target=http%3A//source.unsplash.com) 进入；一个是进阶版的开发者中心 API, 支持更多流量的 app 使用，可以通过 [http://unsplash.com/developers](https://link.zhihu.com/?target=http%3A//unsplash.com/developers) 进入。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic4.zhimg.com%2Fv2-80e62d00c9f1f3784647fb35fa12bd03_b.jpg&valid=true)

**Source API**
--------------

source api 提供的功能比较简单。如果想获取一张随机图片，可以访问地址：

    https://source.unsplash.com/random

这个地址会重定向到一张图片的地址，可以通过响应直接获取到一张图片。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic4.zhimg.com%2Fv2-a35c9858535db171f0afed69ffee08ef_b.jpg&valid=true)

如果图片太大，加载速度也会比较慢。你可以在 url 后面添加尺寸，控制返回的图片大小：

    https://source.unsplash.com/random/800x600

如果原图片不是这种长宽比，unsplash 会对图片进行裁剪，某些部分就会丢失。如果你想保持图片的原始比例，可以把高度设成 0 ：

    https://source.unsplash.com/random/800x0

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic4.zhimg.com%2Fv2-3e021a4164cf430dbe6f6ae8e54b6683_b.jpg&valid=true)
> 小提示   
> 无论是什么 API, 你都可以在最后使用 /800x0 这样的方式控制图片的大小。   

你可以指定获取某位作者的图片。比如我特别喜欢 Raamin ka 拍摄的照片。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic4.zhimg.com%2Fv2-e45cd8f95524b33f71c89f5908c6a91f_b.jpg&valid=true)

我可以把它的用户名小写以后再去掉空格，添加到 /user 的后面：

    https://source.unsplash.com/user/raaminka

这样我就能获取到这位作者拍摄的随机妹子照片了。不要忘了，你同样是可以控制图片尺寸的。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic2.zhimg.com%2Fv2-7cdfa128b5f1ed4d5d7c0783bf93459d_b.jpg&valid=true)

获取某个用户喜欢的照片：

    https://source.unsplash.com/user/raaminka/like

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic2.zhimg.com%2Fv2-d45a2005cffa8a84e08d365b3f81a911_b.jpg&valid=true)

unsplash api 还支持搜索。通常来说，我都会根据要写的文章的主题在 unsplash 上搜索图片。比如我要写一篇关于加密的文章，那我就会去搜索 encryption 相关的图片：

    https://source.unsplash.com/800x0/?encryption

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic4.zhimg.com%2Fv2-e9ff5e644f097f43ca75b52f8f1607df_b.jpg&valid=true)

你也可以组合多个不同的关键字。如果没有图片同时包含这些关键字，则会优先匹配最后的关键字。

    https://source.unsplash.com/800x0/?encryption,girl

现在我们每次访问同一个 API, 得到图片都不一样，因为是随机生成的。但是如果我们在每个 API 的后面添加 /daily 或者 /weekly， 则可以得到固定的一张图。需要注意，这并不是说这些图片更加热门或者质量更高，只是每天/每周保持不变的随机图片而已。

    https://source.unsplash.com/800x0/daily?sports

![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic2.zhimg.com%2Fv2-2e05ff1dd7d8efe28867e476245be955_b.jpg&valid=true)

**Developer API**
-----------------

source api 的功能有限，而且如果访问频率太快总是会返回相同的图片。现在我们来看一下更加专业的开发者 API。

开发者 API 不是马上就可以使用的。你需要先注册成为开发者，得到一个 access token， 之后你可以通过这个 token 访问 API:

    https://api.unsplash.com/photos?client_id=fowflsfg

这个 API 还支持 3 个参数

**paramDescription** `page`第几页`per_page`每页的图片数量`order_by`排序 (可以是: `latest`, `oldest`, `popular`; 默认是: `latest`)

其他的 api 文档你都可以在官网上查看到，这里不复制粘贴了。developer api 相比 resource api 的好处在于他可以同时提供多张图片，同时能获取到丰富的信息，比如作者，日期，大小等等。

在 unsplash 的主页只能看到编辑推荐的图片。没有最新的和流行的可以看，所以我写了个简陋的外壳查看最新和流行的图片。

首先定义一个函数获取图片：

    def get_photos(order_by='popular', page=1, per_page=50):
        """通过developer api 获取图片。"""
        session = requests.Session()
        url = 'https://api.unsplash.com/photos'
        params = {
            "client_id": "your access token",
            "order_by": order_by,
            "page": page,
            "per_page": per_page
        }
        resp = session.get(url, params=params).json()
        return resp

这样我可以得到 50 张图的 url 地址。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic3.zhimg.com%2Fv2-813d2b68656483599097b4d06413c0de_b.jpg&valid=true)

接下来使用 flask 搭建一个简易服务：

    app = Flask(__name__)

    @app.route('/')
    def index():
        pictures = get_photos()
        return render_template('index.html', pictures=pictures)

    if __name__ == '__main__':
        app.run()

直接把图片地址返回给前端页面：

    {% for pic in pictures %}
     <a href="{{ pic.urls.regular }}">
      <img src="{{ pic.urls.small }}">
        </a>
    {% endfor %}

这样我通过访问本地的 http://localhost:5000 就可以看到很多的图片。我没有对图片展示效果进行任何的美化，这种凌乱的风格其实也挺好看的。后面如果用得多我在用 css 框架去做一下页面布局。

当我点击一张图片时，则可以进入这张图片的大图地址，并且可以直接作为链接地址应用到 markdown 当中，而在 unsplash 官方网站上不能直接获取链接地址。
![](https://cubox.pro/c/filters:no_upscale()?imageUrl=https%3A%2F%2Fpic2.zhimg.com%2Fv2-9544d83ffe0229e3f9a03b805fdc6a79_b.jpg&valid=true)

最后补充一点。这个小应用只是作为 unsplash 网站访问非常慢的时候一个备选，并不能真正代替官网。对于图片的筛选和分类搜索操作，官网提供了非常人性化的操作，我就不重复造轮子了。对于这个备选服务，我把他设成了命令行形式，只需要在命令行输入 unsplash 就可以启动网站，还算比较方便。

点击 **[阅读原文](https://link.zhihu.com/?target=https%3A//github.com/looker53/unsplash_url.git)** 获取完整代码。

[跳转到 Cubox 查看](https://cubox.pro/my/card?id=7187084608276530762)
