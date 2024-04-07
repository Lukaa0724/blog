# LaTeX 快速上手以及备忘
主要参考了[一份其实很短的 LaTeX 入门文档](https://liam.page/2014/09/08/latex-introduction/)，里面讲解的很详细

## 理解
> \documentclass{artice}

用与纯英文，如果出现了汉字，需要`\documentclass{ctexart}` ChineseTexArticle，我猜是这样的，否则中文不会出现


## 一些需要熟练掌握的
### 图片的插入
```tex
\documentclass{article}
\usepackage{graphicx}
\begin{document}
\includegraphics{'the path of the image'}
% 或者可以指定格式\includegraphics[width = .8\textwidth]{a.jpg}
\end{document}
```
比较细节一点的有关图片的插入的[图片的插入及排版方法](https://blog.csdn.net/qq_31347869/article/details/103832190)




## 实验报告模版
[浙江大学实验报告模板](https://github.com/megrxu/zjureport?tab=readme-ov-file)


[浙江大学实验报告模板](https://github.com/wqwqqe/zju-report-latex-template)

两个都是中文的，而且内容几乎一样

