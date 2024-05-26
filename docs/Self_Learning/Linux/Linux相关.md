## Ubuntu 22.04的安装以及基础设置
使用VMWare配置Ubuntu的[教程](https://blog.csdn.net/yang4123/article/details/131661855)，以及需要使用的[ZJU Mirror](https://mirrors.zju.edu.cn/)

## Linux中gbd调试
主要的[基础操作](https://blog.csdn.net/qq_52242864/article/details/131029041)





## Ping指令的使用
![](images/Pasted%20image%2020240517084147.png)
测试能不能访问某个网站，如果是上面的就是无法访问，下面的就是可以访问

## 关于Ubuntu任何源都无法访问
问题描述：**sudo apt-get update Cannot initiate the connection to archive.ubuntu.com:80**

尝试了很多方法，[更换软件源](https://blog.csdn.net/hemmmm/article/details/136133844)，将Https改为Http，设置nameserve，等等，无论什么方法都无法解决。

将[wsl降级](https://blog.csdn.net/zhihao_li/article/details/131248100)降级为wsl1就可以正常update了，不知道这是什么奇怪的bug。

## Ubuntu换源
[清华大学镜像站](https://mirror.tuna.tsinghua.edu.cn/help/ubuntu/)，使用其源代码，修改 `/etc/apt/sources.list`文件
```bash
sudo vi /etc/apt/sources.list
```
**Ubuntu 22.04**
```
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-backports main restricted universe multiverse

# 以下安全更新软件源包含了官方源与镜像站配置，如有需要可自行修改注释切换
deb http://security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse

# 预发布软件源，不建议启用
# deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-proposed main restricted universe multiverse
# # deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-proposed main restricted universe multiverse
```
完成修改配置文件后
```bash
sudo apt-get update
sudo apt-get upgrade
```
更新软件源头，更新软件