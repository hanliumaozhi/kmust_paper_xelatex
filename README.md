kmust_paper_xelatex
=====================
2014年昆明理工大学本科毕业论文的xeLaTeX模板
# 软件依赖
使用 [xelatex](http://www.xelatex.org/) 实现了中文的tex

# 其他说明
由于tex的参考文献号没有方括号上标的，我是通过下面的方法实现的
	
	
	1. 使用宏包：cite，并选“superscript”选项：
		\usepackage[superscript]{cite}

 	2. 在引用文献的地方使用“cite”命令：
		\cite{Tom}

    	这样，参考文献号将位于上标处，但是没有方括号！
    	(如果调用宏包“cite”时，不加“superscript”：\usepackage{cite}，则参考文献号在方括号里，如：[1])

 	3. 打开文件：\texmf\tex\latex\cite\cite.sty
    修改：

	176%  Superscript cite, with no optional note.  Check for punctuation first.
	177%
	178\def\@citew#1{\begingroup \leavevmode
	179  \@if@fillglue \lastskip \relax \unskip
	180  \def\@tempa{\@tempcnta\spacefactor
	181     \/% this allows the last word to be hyphenated, and it looks better.
	182     \@citess{\citen{#1}}\spacefactor\@tempcnta
	183     \endgroup \@restore@auxhandle}%
	184  \oc@movep\relax}% check for following punctuation (depending on options)

	将182号改为：

	182     \@citess{\citeleft\citen{#1}\citeright}\spacefactor\@tempcnta
	
注：行数可能不一样