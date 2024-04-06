# Anaconda的安装和使用

## 环境变量的配置

[参考](https://zhuanlan.zhihu.com/p/147602389)

① anaconda安装的目录 D:\Download\ANACONDA

② anaconda/scripts的目录 D:\Download\ANACONDA\Scripts

③ bin的目录 D:\Download\ANACONDA\Scripts\Library\bin

## 日常使用
一些[常用的指令](https://blog.csdn.net/u014628771/article/details/80066624)

> conda info --env

查看所有的环境，等同于

> conda env list

---------------------------------------------------

> conda activate 'name'

切换到'name'的环境

> conda deactivate

退出当前环境

> conda remve -n 'name' -all

删除'name'环境
## VSCode设置终端为CMD(Anaconda Prompt)
VSCode默认的终端为Powershell，导致无法运行
> conda activate breaching

[参考](https://blog.csdn.net/qq_41011242/article/details/123043470)，缺点是换成cmd后conda py等关键字不高亮，貌似一些主题美化可以实现。


## 导入environment.yml文件
> conda env create --file environment.yml

成功导入后环境名就是当前文件夹的名字