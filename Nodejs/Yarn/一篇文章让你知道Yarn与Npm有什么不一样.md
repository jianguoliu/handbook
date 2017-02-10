![Yarn](https://pic3.zhimg.com/v2-3e2647b57638cb82b8679f18d47d90de_b.png)

`Yarn`是 facebook 公开更新JavaScript包管理工具，用来替代如前被广泛使用的npm(nodejs自带的包管理工具)

##Yarn有什么优点

其实`Yarn` 和 `Npm` 做的事情都是一样的,是作为 nodejs 的包管理工具.那么我们为什么推荐大家使用`Yarn`呢?

官网的介绍,`Yarn`一下几个特点,大家可以了解下,最后再决定是否去使用它.

###离线工作*

`Yarn`提供了离线模式,如果你以前安装了某个包,那你可能在一个无网络的环境下想再次安装,也能顺利的安装成功.

我现在有网络的环境下安装`Yarn`的两个安装包

![安装包](https://static.oschina.net/uploads/space/2017/0119/160520_kCX2_2903254.png)

用`yarn install`创建 `package.json`

![创建](https://static.oschina.net/uploads/space/2017/0119/160600_lSBN_2903254.png)

用`Yarn`安装 `express` 和 `jsonwebtoken`

![安装](https://static.oschina.net/uploads/space/2017/0119/160628_uK2e_2903254.png)

安装完成

然后我们删除掉`node_modules`目录, **断网**,然后运行 `yarn install`

![继续安装](https://static.oschina.net/uploads/space/2017/0119/160655_GsCo_2903254.png)

2秒钟完成安装,其实`Yarn`会缓存每次下载好的包,之后就不需要重新下载了,所以安装速度上比`Npm`快的原因就在这里

###依赖关系确定性*

每一台机器针对同一个工程安装依赖时,生成的依赖关系与版本一致

![依赖关系](https://pic1.zhimg.com/v2-e37ac1e2686bff8f9e2570c6613e331c_b.png)

以前`Npm`这方面确实做的比较的差,举例来说，我写的工程依赖 A, B, C 三个库，我在编写 package.json 的时候，给 A, B, C 都指定了版本号。但是 A 库可能又依赖 D, E, F 库，D 库又依赖 G, H 库。这么多关联依赖关系中，很可能某个库在指定依赖时，没有指定版本号。

于是,就导致一个问题出现,如果我们在另外一台机器上对同一个工程安装依赖,或者把这台机器的`node_modules`给删除掉重新安装依赖关系.**关联依赖中,没有指定版本号的库,发生版本更新,就会导致再次安装依赖,其中某些软件包的依赖版本不一致**,这个时候你就会发现,以前运行正常的的程序,突然会变成一堆 bug .

那我们

###更好的网络性能

###多注册来源处理

###网络弹性处理

###扁平模式*

##

https://www.oschina.net/translate/five-things-you-can-do-with-yarn

https://www.zhihu.com/question/51502849
