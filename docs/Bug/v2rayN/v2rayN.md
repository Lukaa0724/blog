# **v2rayN出现failed to listen on address: 127.0.0.1:10808**

[教程参考](https://blog.csdn.net/Running_Wang/article/details/132081228)

具体的操作：以管理员身份打开**cmd**
```shell
netsh int ipv4 set dynamicport tcp start=30000 num=1000
```
然后重启电脑即可