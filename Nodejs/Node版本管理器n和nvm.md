#Node版本管理器n和nvm
Nodejs发展迅猛，版本发布频繁，我们日常开发的文档版本，同时我们或许会需要体验具有harmony特性的版本，那n我们如何安装管理多版本的Node，这就需要使用下面我们介绍的两个Node版本管理工具`n和nvm`

##n
非常简单易用的Node版本管理器,`n`是Node的一个模块，作者[TJ Holowaychuk](https://github.com/visionmedia)(鼎鼎有名Experss框架作者)，就和他的名字一样，它的理念就是简单。

`"no subshells, no profile setup, no convoluted api, just simple"`

![动图](https://camo.githubusercontent.com/e3c6ac1ad2a69e2e969597b69d794658cb64df88/687474703a2f2f6e696d69742e696f2f696d616765732f6e2f6e2e676966)
###安装n
安装很简单

```
sudo npm install -g n
```
安装完成后，直接输入`n` 就能看到帮助信息
###使用n

####安装某版本的node

```
$ n 0.11.12
```

####删除某版本的node

```
$ n rm 0.10.1
```

####安装最新的版本

```
$ n latest
```

####安装稳定

```
$ n stable
```

####指定版本来执行脚本

```
$ n use 0.10.21 node.js
```

##nvm

nvm全称Node Version Manager, 它与`n`的实现方式不同，是通过shell脚本实现的

###安装nvm

`$ curl https://raw.github.com/creationix/nvm/v0.4.0/install.sh | sh`

或者

`$ wget -qO- https://raw.github.com/creationix/nvm/v0.4.0/install.sh | sh`

以上脚本会把nvm库clone到~/.nvm，然后会在~/.bash_profile, ~/.zshrc或~/.profile末尾添加source，安装完成之后，你可以用以下命令来安装node

###使用nvm

####安装某版本的node

```
$ nvm use 0.10
```

####查看当前已经安装的版本

```
$ nvm ls
.nvm
->  v0.10.24
```

####查看正在使用的版本

```
$ nvm current
v0.10.24
```

####以指定版本执行脚本

```
$ nvm run 0.10.24 myApp.js
```

####卸载nvm

```
$ rm -rf ~/.nvm
```

##总结
以上的两种Node版本管理工具，根据自己的口味选择使用吧
