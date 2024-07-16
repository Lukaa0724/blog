[Mkdocs-Wcowin中文主题](https://wcowin.work/Mkdocs-Wcowin/blog/Mkdocs/mkdocs1/)，很好的参考，有很多高级用法
## Code Block 代码块
制定代码块的Title，在*\`\`\`*后添加 `title="xxx.cpp"`

## Admonitions 警告 / 标注
使用时，在开头添加**!!!**，而后可以使用""来添加标题，如果里面为空则没有标题

如果开头使用**???**，那么就是Collapsible(可折叠)的Admonitions，默认是收启的，如果想让他默认展开，则通过
`???+ note`就可以实现

支持的常用的类型`note`,`abstract`,`info`,`tip`,`success`,`question`,`warning`,`failure`,`danger`,`bug`,`example`,`quote`

平时使用最多的应该是**note,abstract,info,tip,example,warning**
[Here](https://squidfunk.github.io/mkdocs-material/reference/admonitions/#+type:note)可以查看这些常用的`admonitions`的样子

## 评论系统的搭建
[官方教程](https://squidfunk.github.io/mkdocs-material/setup/adding-a-comment-system/))

[基于 giscus 为网站添加评论系统](https://fengchao.pro/blog/comment-system-with-giscus/)

!!! failure
    无法实现为多个界面搭建评论 必须在markdown前添加
    ```
    ---
    comments: true
    ---
    ```

## 任务列表
[Here](https://squidfunk.github.io/mkdocs-material/setup/extensions/python-markdown-extensions/#tasklist)是官方教程

!!! example
    ```
    - [x] Lorem ipsum dolor sit amet, consectetur adipiscing elit
    - [ ] Vestibulum convallis sit amet nisi a tincidunt
        * [x] In hac habitasse platea dictumst
        * [x] In scelerisque nibh non dolor mollis congue sed et metus
        * [ ] Praesent sed risus massa
    - [ ] Aenean pretium efficitur erat, donec pharetra, ligula non scelerisque
    ```

    - [x] Lorem ipsum dolor sit amet, consectetur adipiscing elit
    - [ ] Vestibulum convallis sit amet nisi a tincidunt
        * [x] In hac habitasse platea dictumst
        * [x] In scelerisque nibh non dolor mollis congue sed et metus
        * [ ] Praesent sed risus massa
    - [ ] Aenean pretium efficitur erat, donec pharetra, ligula non scelerisque