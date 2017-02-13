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

其实`Yarn`采用的方式是引用了`yarn.lock`文件来应对这个问题,lock机制在很多包管理中都用到过.例如:ruby的rubygems就会生成一个`Gemfile.lock`的文件.

`yarn.lock`会记录你安装的软件包的具体版本.只要你不删除`yarn.lock`文件,在运行`yarn install`就会根据记录的版本包获取所需要的依赖包.所以大家可以吧`yarn.lock`提交到版本管理库.这样同事或者协同开发者运行的时候保证大家依赖都是完全一致的.

特使适合大型项目协作开发和部署.

其实写到这里大家可能会说`npm`有一个`shrinkwrap(拆封)` [[查看1](https://docs.npmjs.com/cli/shrinkwrap),[查看2](http://tech.meituan.com/npm-shrinkwrap.html)],但是它的问题是,每个开发者都必须手动运行`npm shrinkwrap` 生成一个 `npm-shrikwrap.json`文件.开发者也是人啦,容易忘记(如果你说你牛逼你不忘记,我也没有办法)

###更好的网络性能

下载软件包的时候,会更好的排序,避免**请求瀑布流**,最大限度提交网络利用率.

###多注册来源处理

我们知道我们的项目可以安装多个资料库的包:`npm` `bower` `Git`库甚至是本地文件系统.

而`Yarn`可以从多个资料库安装 JavaScript 包.

默认情况下,它会在`npm`资料库扫描你所需要的包

```
yarn add <pkg-name>
```

你下面这样可以从远程安装一个 gzip 压缩包：

```
yarn add <https://thatproject.code/package.tgz>
```

下面会从本地文件系统安装包：

```
yarn add file:/path/to/local/folder
```

从本地文件系统安装包对持续发行 JavaScript 包的开发者特别有帮助。你可以在把包发行到资料库之前通过这个功能测试你的包。

从远程 Git 库安装包：

```
yarn add <git remote-url>
```

![add git](https://static.oschina.net/uploads/space/2017/0119/160751_EM2J_2903254.png)

`Yarn` 从 Github 安装包

![add github](https://static.oschina.net/uploads/space/2017/0119/160831_RQqi_2903254.png)

`Yarn` 还会自动检查 Git 库是否是作为 Bower 资料库使用,如果是则把它当作 Bower 资料库使用.



###网络弹性处理

安装依赖的过程中，不会因为某个单次网络请求的失败导致整个安装挂掉（这里又要黑一下 npm）。当请求失败时会进行自动重试。

##小结

Yarn 一开始就为 JavaScript 获取包的方式带来了重大改进，允许从公共资料库获取包，也允许从本地环境获取，更重要的是为它还充分考虑了速度和安全性
