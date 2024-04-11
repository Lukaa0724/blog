# LaTeX 快速上手以及备忘
主要参考了[一份其实很短的 LaTeX 入门文档](https://liam.page/2014/09/08/latex-introduction/)，里面讲解的很详细

## 理解
> \documentclass{artice}

用与纯英文，如果出现了汉字，需要`\documentclass{ctexart}` ChineseTexArticle，我猜是这样的，否则中文不会出现


## 一些需要熟练掌握的
### 图片的插入
```tex
\usepackage{graphicx} %插入图片的宏包
\usepackage{float} %设置图片浮动位置的宏包
\usepackage{subfigure} %插入多图时用子图显示的宏包
```
切割--------------------便于复制
```tex

\begin{figure}[H] %H为当前位置，!htb为忽略美学标准，htbp为浮动图形
\centering %图片居中
\includegraphics[width=0.7\textwidth]{} %插入图片，[]中设置图片大小，{}中是图片文件名
\caption{} %最终文档中希望显示的图片标题
\label{} %用于文内引用的标签
\end{figure}
```
比较细节一点的有关图片的插入的[图片的插入及排版方法](https://blog.csdn.net/qq_31347869/article/details/103832190)




## 实验报告模版
[浙江大学实验报告模板](https://github.com/megrxu/zjureport?tab=readme-ov-file)


[浙江大学实验报告模板](https://github.com/wqwqqe/zju-report-latex-template)

两个都是中文的，而且内容几乎一样

## Verilog代码风格
```tex
\usepackage{xcolor}
\usepackage{listings}

\definecolor{vgreen}{RGB}{104,180,104}
\definecolor{vblue}{RGB}{49,49,255}
\definecolor{vorange}{RGB}{255,143,102}

\lstset
{
    language=Verilog,
    % 设置基本样式，这里设置为小字体和等宽字体
    basicstyle=\small\ttfamily,
    % 关键字的样式，这里设置为蓝色
    keywordstyle=\color{vblue},
    % 设置标识符的样式，这里设置为黑色
    identifierstyle=\color{black},
    % 设置注释的样式，这里设置为绿色
    commentstyle=\color{vgreen},
    % 设置行号的位置在左边
    numbers=left,
    % 设置行号的样式，这里设置为微小的黑色字体
    numberstyle=\tiny\color{black},
    % 设置行号和代码之间的距离为10pt
    numbersep=10pt,
    % 设置制表符的大小为4
    tabsize=4,
    % 果一行代码过长，允许自动换行
    breaklines=true,
    % moredelim=*[s][\colorIndex]{[}{]},
    % 是一个文本替换命令，它会将所有的冒号替换为冒号，这里没有实际的效果
    literate=*{:}{:}1
}   
```

## 其他一些资源
- [ZLDF的LaTeX笔记](https://zhengliangduanfang.github.io/hmpg_mkdocs/misc/latex/)

- [刘海洋LaTeX入门](https://yun.weicheng.men/Book/LaTeX%E5%85%A5%E9%97%A8.pdf) 工具书