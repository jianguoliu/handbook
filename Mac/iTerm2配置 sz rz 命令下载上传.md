上传文件到服务器是开发人员经常遇到的事情，在window下我们可以很方面的使用rz、sz命令上传、下载文件，但是mac下一般都是通过scp命令完成，虽然也很方便，但是有些场景下是不能使用的，比如目前公司登录服务器需要经过跳板机，scp命令就不再适用。所以本篇我们就介绍一下如何在mac下使用rz、sz上传下载文件。

## scp命令介绍

###上传
```
scp -r local_folder remote_username@remote_ip:remote_folder
```
或者
```
scp -r local_folder remote_ip:remote_folder
```

###下载
下载和上传对应，只需要修改后两个参数顺序即可，即调整源文件和目标文件顺序。

```
scp -r remote_username@remote_ip:remote_folder local_folder 
```

###几个可能用到的参数
* -v 和大多数 linux 命令中的 -v 意思一样 , 用来显示进度 . 可以用来查看连接 , 认证 , 或是配置错误 .
* -r 　递归处理，将指定目录下的文档和子目录一并处理
* -C 使能压缩选项 .
* -P 选择端口 . 注意 -p 已经被 rcp 使用 .
* -4 强行使用 IPV4 地址 .
* -6 强行使用 IPV6 地址 .

## Mac Iterm2如何配置使用rz sz

###安装
```
brew install lrzsz
```

### 下载iterm2-zmodem
这两个脚本文件需要放在 `/usr/local/bin` 目录下。[iterm2-zmodem](https://github.com/mmastrac/iterm2-zmodem)

```
cd /usr/local/bin
sudo wget https://raw.github.com/mmastrac/iterm2-zmodem/master/iterm2-send-zmodem.sh
sudo wget https://raw.github.com/mmastrac/iterm2-zmodem/master/iterm2-recv-zmodem.sh
sudo chmod 777 /usr/local/bin/iterm2-*
```

### 添加trigger
iTerm2的设置界面  iTerm偏好设置-> Profiles -> Default -> Advanced -> Triggers的Edit按钮

** trigger 信息**
```

Regular expression: \*\*B0100
Action: Run Silent Coprocess
Parameters: /usr/local/bin/iterm2-send-zmodem.sh
 
Regular expression: \*\*B00000000000000
Action: Run Silent Coprocess
Parameters: /usr/local/bin/iterm2-recv-zmodem.sh
```
![](http://www.xheldon.com/wp-content/uploads/2015/08/QQ20150802-9@2x-1024x598.png)