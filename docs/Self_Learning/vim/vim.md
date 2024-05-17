# This is a reposity about learning Vim
I have made up my mind to learn Vim.

And I have installed Vim extension in my VSCode.

There are some relative data.
[【Linux】Vim 入门笔记](https://imageslr.com/2021/vim.html)

[在VSCode里面配置Vim的正确姿势（细节解析）](https://zhuanlan.zhihu.com/p/188499395) 把j and j映射到Esc

[有没有练习 Vim 的网站或者软件推荐？](https://www.v2ex.com/t/830497)  这里有一些关于Vim的讨论

感觉目前自己的基础不够扎实 不能够快速使用vim打代码 而且打数字习惯用右侧的数字键盘 而不是小键盘

[菜鸟教程](https://www.runoob.com/linux/linux-vim.html)  菜鸟教程 简单直接把vim的指令集列出来了 便于查找
但是有一说一 这上面很多的快捷键都没有说到 比如dw dd

[vim常用操作总结](https://github.com/chenxiaochun/blog/issues/60) 这个常用总结写的不错

[Vim常用命令总结](https://github.com/czla/awesome-linux-command/blob/master/Vim.md)  这个应该是最全面的版本了

Vim还是比较适合打英语 奈何自己的英文水平不太够

## Vim中的按键标识符
参考了[Vim中的按键标识符](https://blog.csdn.net/lxyoucan/article/details/114261944)

修改setting json文件
```json
    "vim.insertModeKeyBindings": [
            {
                "before": ["j", "j"],
                "after": ["<Esc>"]

            },
            {
                "before": ["j", "k"],
                "after": ["<Esc>"]
            },
            {
                "before": ["k", "k"],
                "after": ["<Esc>"]
            },
            {
                "before": ["C-q"],
                "after": ["<Esc>"]
            }

    ],

 "vim.handleKeys": {
        "<C-a>": false,
        "<C-f>": false,
        "<C-c>": false,
        "<C-v>": false,
        "<C-y>": false,
        "<C-x>": false,
        "<C-n>": false,
        "<C-w>": false,
        "<C-[>": false,
        "<C-]>": false,
    },
```
## VScode Vim插件进阶
### 如何在且换到normal时自动切换为英文输入法
[vscode+vim 切换成normal模式后自动关闭输入法](https://blog.csdn.net/Losk_0/article/details/105520634)

非常的使用 把`ctrl+q`，映射到`Esc`，这样就可以非常愉快的在VScode中搭配Vim写Tex实验报告了