大家肯定在Window下SSH连接远程的liunx server，基本上在这样的环境下，我们都用的是SecureCRT这样的SSH软件，通过liunx界面数据如rs、sz命令来上传/下载文件。
但是这两个命令不是默认安装在系统里面的，需要我们手工去安装

## 准备
[下载lrzsz安装包](http://www.ohse.de/uwe/software/lrzsz.html)

## 方法与步骤
```shell
cd /tmp
wget [url]
tar zxvf [安装包]
cd [安装包]
./configure
make && make install
```
 很多时候我们执行在这里的时候大家可能已经觉得完成了，这个时候在在命令里面输入rs还是没有这个命令，我们需要继续做后续的操作
```shell
cd /usr/bin
In -s /usr/local/bin/lrz rz
In -s /use/local/bin/lsz sz
```
呵呵，基本搞定，但是还要提醒大家的一点我们可以在SecureCRT软件里面设置默认的上传和下载的目录
>  Options -> session options -> X/Y/Zmodem