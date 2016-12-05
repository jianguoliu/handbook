>Nginx("engine x")是一款是由俄罗斯的程序设计师Igor Sysoev所开发高性能的 Web和 反向代理 服务器，也是一个 IMAP/POP3/SMTP 代理服务器。
在高连接并发的情况下，Nginx是Apache服务器不错的替代品

## Nginx 安装
>系统平台: CentOS release 7.5

### 一、安装编译工具及所需要的库文件
```shell
yum -y install make zlib zlib-devel gcc-c++ libtool  openssl openssl-devel
```
### 二、安装PCRE
> PCRE主要的作用是让Nginx 支持Rewrite功能。

```shell
wget [url]
tar zxvf [package]
cd [package]
./configure
make && make install
```
