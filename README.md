最近在写毕业论文，看到网上的推荐学习使用了latex。在写作的过程中也逐渐感受到了latex相比于word的优势。现将写作过程中使用latex遇到的一些问题记录如下：



# 入门

可以参考知乎问题[如何从零开始，入门latex](https://www.zhihu.com/question/62943097)。

我找到的比较好的入门资料有：[一份其实很短的 LaTeX 入门文档](https://liam.page/2014/09/08/latex-introduction/)，[最新版lshort](https://www.latexstudio.net/archives/6058.html)。



# 环境配置

windows下推荐安装tex live，如果想要在线编辑，也可以使用overleaf。

安装tex live时可以选择安装texworks（是一款自带的编辑器），texworks功能比较简洁，可以根据自己的喜好来选择其他编辑器，例如Texstudio，vscode。

我最终选择使用vscode，也是看中了它的正反向搜索功能。vscode的环境配置可以参考[这篇文章](https://zhuanlan.zhihu.com/p/38178015)。



# 常见的问题

## 编译

按照xelatex bibtex xelatex xelatex的顺序进行编译

编译时经常会出现“Undefined control sequence”错误，这时可以删除同一个文件夹中的.aux文件，再重新编译，可以参考[文章](https://blog.csdn.net/qq_37325494/article/details/89849948)。

编译之前需要关掉pdf阅读器中的pdf文件。

## 图片

需要注意，\label命令要放在\caption命令之后。

两图并排放置并且分别有单独的图名：

```latex
\begin{figure}[htbp]
\begin{minipage}[t]{0.5\textwidth}
\centering
\includegraphics[height=0.5\textwidth]{11}
\caption{图1}
\label{11}
\end{minipage}
\hfill
\begin{minipage}[t]{0.5\textwidth}
\centering
\includegraphics[height=0.5\textwidth]{22}
\caption{图2}
\label{22}
\end{minipage}
\end{figure} 
```



两子图并排放置分别标记为图(a)(b)：

```latex
\begin{figure}[htbp]
    \centering
    \subfloat[]{ %[]对齐方式，t为top，b为bottom，留空即可
\label{Fig:R1} % 子图1标签名
    	\includegraphics[height=0.27\textwidth]{11}} %插入图片命令，格式为[配置]{图片路径}
    \quad %空格
    \subfloat[]{
	\label{Fig:R2} % 子图2标签名
    	\includegraphics[height=0.27\textwidth]{22}}
    \caption{图1：\protect\subref{Fig:R1}子图a，\protect\subref{Fig:R2}子图b} %注意须使用\protect\subref{}进行标号引用
    \label{Fig1} % 整个组图的标签名
\end{figure}
```



## 公式

行内公式用$...$

行间公式有标号用\begin{eqution}...\end{equation}

行间公式无标号用\\[...]\



## 参考文献

bibtex最好在谷歌学术上找，百度学术上错误较多。





