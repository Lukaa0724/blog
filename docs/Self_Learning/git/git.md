# Learn git
Git is a distributed version control system.
Git is a free software distributed under the GPL.
Git has a mutable index called stage.
Git tracks changes of files.

Creating a new branch is quick and simple.
Edit something.

Let's try the 'tag' (LJDHandSome)


## My method to learning git
First, I learn the book <<Git简要教程-廖雪峰>>. And you can find it in resource.
And I find the [git-cheat-sheet](https://education.github.com/git-cheat-sheet-education.pdf) to help me to
remember some instructions.

And I summarized what I learned.

> git add 'file'

添加文件到缓冲区
> git commit -m " XXX "

提交文件 -m的意思是message
> git status

查看当前状态
> git diff

查看现在的文件和上一次commit的文件的区别

> git log

查看提交历史
> git log --pretty=oneline --abbrev-commit

每一条历史占据一行 并且缩写commit id
> git reset --hard "commit id"

版本回退 其中的commit id可以写成"HEAD ^^^"或者"HEAD~100" 表示回退到前100个版本
> git reflog 

回退后查看未来的提交

> git checkout -- file

撤销工作区的修改

如果已经把需要修改的内容提交到了暂存区 首先**git reset HEAD "file"**来清除暂存区
然后使用**git checkout -- file**来丢弃工作区的修改

> git remote add origin git@github.com:XXX

添加远程仓库“origin” 

> git push -u origin master

这里的-u是制定上游(upstream)为origin  向origin仓库提交我们的master分支

> git checkout -b dev

创建并且切换到dev分支 相当于
> git branch dev
> git checkout dev


> git merge dev

直接合并dev分支

> git branch -d dev

删除dev分支

当合并分支发生冲突的时候 去文件里查看具体冲突的细节 然后add commit

> git merge --no-ff -m "merge with no-ff" dev

不采用"Fast forward"的方式合并分支 这样合并分支后 可以知道分支合并的信息
> git log --graph --pretty=oneline --abbrev-commit

以graph的形式查看分支合并情况

> git remote

查看远程仓库信息
> git remote -v

查看远程仓库更加详细的信息
> git push origin XXX

将XXX分支推送到origin中

> git checkout -b dev origin/dev

创建本地的dev分支 并且关联origin的dev

> git branch --set-upstream branch-name  origin/branch-name

建⽴本地分⽀和远程分⽀的关联，使⽤

多⼈协作的⼯作模式通常是这样：
1. ⾸先，可以试图⽤git push origin branch-name推送⾃⼰的修改；
2. 如果推送失败，则因为远程分⽀⽐你的本地更新，需要先⽤git pull试图合并；
3. 如果合并有冲突，则解决冲突，并在本地提交；
4. 没有冲突或者解决掉冲突后，再⽤git push origin branch-name推送就能成功！

> git config --global alias.st status

git的自定义操作 st是stats的别名 git st ==== git status 更加简单

分享一下我的git配置
> git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"


> git config --global alias.st status


> git config --global alias.co checkout


> git config --global alias.br branch


> git config --global alias.cm 'commit -m'


> git config --global alias.unstage 'reset HEAD'


> git config --global alias.last 'log -1'


## 日常使用发现的一些问题

> git branch -M main

github希望我们用这样的指令 把当前的分支改名为main(master改名为main)
由于我异性修改了快捷键 只需要**git br -M main**




[显示隐藏的git目录](https://blog.csdn.net/baicha11/article/details/127700351)

本来提交了一个100MB以上的大文件打算git push 结果不能 而后删除这个大文件 结果还是不能push 原因是删除后.git文件还是很大因此需要

![](images/2024-03-02-19-59-50.png)

具体的[教程](https://juejin.cn/post/6844903448627019789) 还有一种[方法](https://www.jianshu.com/p/780161d32c8e)
[解决.git文件过大的问题](https://blog.csdn.net/HOU_Zhe/article/details/115265834)
我是菜鸡  为了解决这个问题，我使用了
> rm -rf .git

直接把git全删了 然后git init  git add .  git cm

这个故事告诉我们 有大文件的时候 不要git add . 呜呜呜