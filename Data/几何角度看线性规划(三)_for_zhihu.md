---
title: 几何角度看线性规划(三)
date: 2022-06-26 14:14:19
categories: 运筹学
tags: 线性规划
mathjax: true
---

## 多面体的另一种表达
前文多面体是通过约束的形式来定义的，而本节将证明一个有界的多面体可以表示为其极点的凸壳。类似的，一个无界的多面体可以用其极点和极射线进行表示。

**定理**：一个非空有界的多面体是其极点的凸壳。

<!--more-->>

**证明**：首先定义多面体 <img src="https://www.zhihu.com/equation?tex=P\subset R^n" alt="P\subset R^n" class="ee_img tr_noresize" eeimg="1"> 的维数为最小整数k，即P位于 <img src="https://www.zhihu.com/equation?tex=R^m" alt="R^m" class="ee_img tr_noresize" eeimg="1"> 的一些k维的仿射子空间。如果P是零维的，它只包括一个点，这个点即是P的一个极点，定理成立。其他情况，使用数学归纳法，首先假设对于所有维数小于k的多面体这个结论都是成立的，令 <img src="https://www.zhihu.com/equation?tex=P=\{x\in R^n\vert a_i'x\ge b_i,i=1,\dots,m\}" alt="P=\{x\in R^n\vert a_i'x\ge b_i,i=1,\dots,m\}" class="ee_img tr_noresize" eeimg="1"> 为非空k维的多面体，则P位于 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 的仿射子空间 <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> 内，其中 <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> 可以表示为:

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
S=\{x^0+\lambda_1x^1+\dots,\lambda_kx^k\vert\lambda_1,\dots,\lambda_k\in R\}
\end{equation*}
" alt="\begin{equation*}
S=\{x^0+\lambda_1x^1+\dots,\lambda_kx^k\vert\lambda_1,\dots,\lambda_k\in R\}
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
其中 <img src="https://www.zhihu.com/equation?tex=x^1,\dots,x^k" alt="x^1,\dots,x^k" class="ee_img tr_noresize" eeimg="1"> 为 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 中的一些向量，令 <img src="https://www.zhihu.com/equation?tex=f_1,\dots,f_{n-k}" alt="f_1,\dots,f_{n-k}" class="ee_img tr_noresize" eeimg="1"> 表示 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 中正交于 <img src="https://www.zhihu.com/equation?tex=x^1,\dots,x^k" alt="x^1,\dots,x^k" class="ee_img tr_noresize" eeimg="1"> 的向量。令 <img src="https://www.zhihu.com/equation?tex=g_i=f_i'x^0" alt="g_i=f_i'x^0" class="ee_img tr_noresize" eeimg="1"> ，则S的每个向量都满足 <img src="https://www.zhihu.com/equation?tex=f_i'x=g_i,i=1,\dots,n-k" alt="f_i'x=g_i,i=1,\dots,n-k" class="ee_img tr_noresize" eeimg="1"> ，由于 <img src="https://www.zhihu.com/equation?tex=P\subset S" alt="P\subset S" class="ee_img tr_noresize" eeimg="1"> ，上式对P的每个向量也都成立。

令z为P的一个向量，如果z是P的一个极点，则z一定是P极点的一个凸组合；若z不是P的一个极点，选择P的任意一个极点y，则可以建立一条射线 <img src="https://www.zhihu.com/equation?tex=z+\lambda(z-y),z\ge 0" alt="z+\lambda(z-y),z\ge 0" class="ee_img tr_noresize" eeimg="1"> 。由于P是有界的，射线会在 <img src="https://www.zhihu.com/equation?tex=\lambda=\lambda^*" alt="\lambda=\lambda^*" class="ee_img tr_noresize" eeimg="1"> 时违背某个约束 <img src="https://www.zhihu.com/equation?tex=a_{i^*}'x\ge b_{i^*}" alt="a_{i^*}'x\ge b_{i^*}" class="ee_img tr_noresize" eeimg="1"> ，设将要违背约束时的向量为u，则

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
u=z+\lambda^*(z-y)\\
a_{i^*}'u=b_{i^*}
\end{equation*}
" alt="\begin{equation*}
u=z+\lambda^*(z-y)\\
a_{i^*}'u=b_{i^*}
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
当 <img src="https://www.zhihu.com/equation?tex=\lambda\gt \lambda^*" alt="\lambda\gt \lambda^*" class="ee_img tr_noresize" eeimg="1"> 时，该约束会被违背，因此 <img src="https://www.zhihu.com/equation?tex=a_{i^*}'(z-y)\lt 0" alt="a_{i^*}'(z-y)\lt 0" class="ee_img tr_noresize" eeimg="1"> 。令多面体Q表示为：

<img src="https://www.zhihu.com/equation?tex=\begin{align*}
Q&=\{x\in P\vert a_{i^*}'x=b_{i^*}\}\\
&=\{x\in R^n\vert a_i'x\ge b_i, i=1,\dots,m, a_{i^*}'x=b_{i^*}\}
\end{align*}
" alt="\begin{align*}
Q&=\{x\in P\vert a_{i^*}'x=b_{i^*}\}\\
&=\{x\in R^n\vert a_i'x\ge b_i, i=1,\dots,m, a_{i^*}'x=b_{i^*}\}
\end{align*}
" class="ee_img tr_noresize" eeimg="1">
由于 <img src="https://www.zhihu.com/equation?tex=z\in P,y\in P" alt="z\in P,y\in P" class="ee_img tr_noresize" eeimg="1"> ，则有 <img src="https://www.zhihu.com/equation?tex=f_i'z=f_iy=b_i" alt="f_i'z=f_iy=b_i" class="ee_img tr_noresize" eeimg="1"> ，这表示 <img src="https://www.zhihu.com/equation?tex=y-z" alt="y-z" class="ee_img tr_noresize" eeimg="1"> 与所有 <img src="https://www.zhihu.com/equation?tex=f_i" alt="f_i" class="ee_img tr_noresize" eeimg="1"> 正交，又因为 <img src="https://www.zhihu.com/equation?tex=a_{i^*}'(z-y)\lt 0" alt="a_{i^*}'(z-y)\lt 0" class="ee_img tr_noresize" eeimg="1"> ，这说明 <img src="https://www.zhihu.com/equation?tex=a_{i^*}'" alt="a_{i^*}'" class="ee_img tr_noresize" eeimg="1"> 不是 <img src="https://www.zhihu.com/equation?tex=f_i" alt="f_i" class="ee_img tr_noresize" eeimg="1"> 的凸组合，且

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
Q\subset \{x\in R^n\vert a_{i^*}'x=b_i,f_i'x=g_i,i=1,\dots,n-k\}
\end{equation*}
" alt="\begin{equation*}
Q\subset \{x\in R^n\vert a_{i^*}'x=b_i,f_i'x=g_i,i=1,\dots,n-k\}
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
上述右侧共有n-k+1条线性无关的等式约束，因此形成了k-1维的仿射空间，又由于Q是右侧的一个子空间，其最大维数是k-1维。前面已经假设了对于所有维数小于k的多面体都是其极点的凸桥，因此u可以表示为凸组合：

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
u=\sum_i \lambda_iv^i
\end{equation*}
" alt="\begin{equation*}
u=\sum_i \lambda_iv^i
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
其中 <img src="https://www.zhihu.com/equation?tex=v^i" alt="v^i" class="ee_img tr_noresize" eeimg="1"> 为多面体Q的极点， <img src="https://www.zhihu.com/equation?tex=\lambda_i" alt="\lambda_i" class="ee_img tr_noresize" eeimg="1"> 为非负标量且和为1.由于v是Q的极点，一定n个线性无关的向量 <img src="https://www.zhihu.com/equation?tex=a_i" alt="a_i" class="ee_img tr_noresize" eeimg="1"> 满足 <img src="https://www.zhihu.com/equation?tex=a_i'v=b_i" alt="a_i'v=b_i" class="ee_img tr_noresize" eeimg="1"> ，因此v也是P的极点，对前面 <img src="https://www.zhihu.com/equation?tex=u=z+\lambda^*(z-y)" alt="u=z+\lambda^*(z-y)" class="ee_img tr_noresize" eeimg="1"> 移项，则有：

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
z=\frac{u+\lambda^*y}{1+\lambda^*}=\frac{\lambda^*y}{1+\lambda^*}+\sum_i\frac{\lambda_i}{1+\lambda^*}v^i
\end{equation*}
" alt="\begin{equation*}
z=\frac{u+\lambda^*y}{1+\lambda^*}=\frac{\lambda^*y}{1+\lambda^*}+\sum_i\frac{\lambda_i}{1+\lambda^*}v^i
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
因此，z是P极点的一个凸组合。

## 多面体的映射：Fourier-Motzkin消元法

本节将给出一种过去解决线性规划问题的方法，该方法实用性较弱，但可以得到一些有趣的推论。

方法的关键是利用了投影的概念，即： <img src="https://www.zhihu.com/equation?tex=x=(x_1,\dots,x_n)" alt="x=(x_1,\dots,x_n)" class="ee_img tr_noresize" eeimg="1"> 是 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 的一个向量，映射 <img src="https://www.zhihu.com/equation?tex=\pi_k:R^n\to R^k" alt="\pi_k:R^n\to R^k" class="ee_img tr_noresize" eeimg="1"> 将x投影到其前k个坐标

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
\pi_k(x)=\pi_k(x_1,\dots,x_n)=(x_1,\dots,x_k)\quad k\le n
\end{equation*}
" alt="\begin{equation*}
\pi_k(x)=\pi_k(x_1,\dots,x_n)=(x_1,\dots,x_k)\quad k\le n
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
同理，集合 <img src="https://www.zhihu.com/equation?tex=S\subset R^n" alt="S\subset R^n" class="ee_img tr_noresize" eeimg="1"> 的投影为：

<img src="https://www.zhihu.com/equation?tex=\begin{align*}
\Pi_k(S)&=\{\pi_k(x)\vert x\in S\}\\
&=\{(x_1,\dots,x_k)\vert 存在x_{k+1},\dots,x_n,s.t. (x_1,\dots,x_n)\in S\}
\end{align*}
" alt="\begin{align*}
\Pi_k(S)&=\{\pi_k(x)\vert x\in S\}\\
&=\{(x_1,\dots,x_k)\vert 存在x_{k+1},\dots,x_n,s.t. (x_1,\dots,x_n)\in S\}
\end{align*}
" class="ee_img tr_noresize" eeimg="1">
显然，S非空当且仅当 <img src="https://www.zhihu.com/equation?tex=\Pi_k(S)" alt="\Pi_k(S)" class="ee_img tr_noresize" eeimg="1"> 非空，因此对于多面体P，通过消去变量 <img src="https://www.zhihu.com/equation?tex=x_n" alt="x_n" class="ee_img tr_noresize" eeimg="1"> 来构建集合 <img src="https://www.zhihu.com/equation?tex=\Pi_{n-1}(P)" alt="\Pi_{n-1}(P)" class="ee_img tr_noresize" eeimg="1"> ，判断 <img src="https://www.zhihu.com/equation?tex=\Pi_{n-1}(P)" alt="\Pi_{n-1}(P)" class="ee_img tr_noresize" eeimg="1"> 是否非空以此来确定P是否非空。通过不断消去变量直到 <img src="https://www.zhihu.com/equation?tex=\Pi_1(P)" alt="\Pi_1(P)" class="ee_img tr_noresize" eeimg="1"> ，则是否非空就很好确定了。这个方法的缺点在于每消去一个变量就会增加很多新的约束。下面将介绍消元方法，给定多面体P的形式：

<img src="https://www.zhihu.com/equation?tex=\sum_{j=1}^na_{ij}x_j\ge b_i\quad i=1,\dots,m.
" alt="\sum_{j=1}^na_{ij}x_j\ge b_i\quad i=1,\dots,m.
" class="ee_img tr_noresize" eeimg="1">
我们希望消去 <img src="https://www.zhihu.com/equation?tex=x_n" alt="x_n" class="ee_img tr_noresize" eeimg="1"> ，来构造映射 <img src="https://www.zhihu.com/equation?tex=\Pi_{n-1}(P)" alt="\Pi_{n-1}(P)" class="ee_img tr_noresize" eeimg="1"> 

1. 首先对约束移向，构造以下形式：

<img src="https://www.zhihu.com/equation?tex=a_{ij}x_n\ge-\sum_{j=1}^{n-1}a_{ij}x_j+b_i\quad i=1,\dots,m
    " alt="a_{ij}x_n\ge-\sum_{j=1}^{n-1}a_{ij}x_j+b_i\quad i=1,\dots,m
    " class="ee_img tr_noresize" eeimg="1">
    当 <img src="https://www.zhihu.com/equation?tex=a_{in}\ne 0" alt="a_{in}\ne 0" class="ee_img tr_noresize" eeimg="1"> 时，上式两边同时除以 <img src="https://www.zhihu.com/equation?tex=a_{in}" alt="a_{in}" class="ee_img tr_noresize" eeimg="1"> ，令 <img src="https://www.zhihu.com/equation?tex=\bar{x}=(x_1,\dots,x_{n-1})" alt="\bar{x}=(x_1,\dots,x_{n-1})" class="ee_img tr_noresize" eeimg="1"> ，则多面体P也可以表示为：

<img src="https://www.zhihu.com/equation?tex=\begin{align}
    x_n\ge d_i+f_i'\bar{x}\quad\text{if }a_{in}>0\\
    d_j+f_j'\bar{x}\ge x_n\quad\text{if }a_{jn}<0\\
    0\ge d_k+f_k'\bar{x}\quad\text{if }a_{kn}=0\\
    \end{align}
    " alt="\begin{align}
    x_n\ge d_i+f_i'\bar{x}\quad\text{if }a_{in}>0\\
    d_j+f_j'\bar{x}\ge x_n\quad\text{if }a_{jn}<0\\
    0\ge d_k+f_k'\bar{x}\quad\text{if }a_{kn}=0\\
    \end{align}
    " class="ee_img tr_noresize" eeimg="1">
    其中， <img src="https://www.zhihu.com/equation?tex=d_i,d_j,d_k" alt="d_i,d_j,d_k" class="ee_img tr_noresize" eeimg="1"> 为标量， <img src="https://www.zhihu.com/equation?tex=f_i,f_j,f_k" alt="f_i,f_j,f_k" class="ee_img tr_noresize" eeimg="1"> 为n-1维的向量
    
2. 令Q表示由以下约束定义的 <img src="https://www.zhihu.com/equation?tex=R^{n-1}" alt="R^{n-1}" class="ee_img tr_noresize" eeimg="1"> 中的多面体：

<img src="https://www.zhihu.com/equation?tex=\begin{align}
   d_j+f_j'\bar{x}\ge d_i+f_i'\bar{x}\quad&\text{if }a_{in}>0\text{ and }a_{jn}<0\\
   0\ge d_k+f_k'\bar{x}\quad&\text{if }a_{kn}=0\\
   \end{align}
   " alt="\begin{align}
   d_j+f_j'\bar{x}\ge d_i+f_i'\bar{x}\quad&\text{if }a_{in}>0\text{ and }a_{jn}<0\\
   0\ge d_k+f_k'\bar{x}\quad&\text{if }a_{kn}=0\\
   \end{align}
   " class="ee_img tr_noresize" eeimg="1">
   

由上述消元法得到的多面体 <img src="https://www.zhihu.com/equation?tex=Q" alt="Q" class="ee_img tr_noresize" eeimg="1"> 是与 <img src="https://www.zhihu.com/equation?tex=\Pi_{n-1}(P)" alt="\Pi_{n-1}(P)" class="ee_img tr_noresize" eeimg="1"> 的投影等价的

**证明**：通过证明 <img src="https://www.zhihu.com/equation?tex=\Pi_{n-1}(P)\subset Q,Q\subset \Pi_{n-1}(P)" alt="\Pi_{n-1}(P)\subset Q,Q\subset \Pi_{n-1}(P)" class="ee_img tr_noresize" eeimg="1"> , 首先证明 <img src="https://www.zhihu.com/equation?tex=\Pi_{n-1}(P)\subset Q" alt="\Pi_{n-1}(P)\subset Q" class="ee_img tr_noresize" eeimg="1"> .令 <img src="https://www.zhihu.com/equation?tex=\bar{x}\in \Pi_{n-1}(P)" alt="\bar{x}\in \Pi_{n-1}(P)" class="ee_img tr_noresize" eeimg="1"> , 根据定义存在一些 <img src="https://www.zhihu.com/equation?tex=x_n" alt="x_n" class="ee_img tr_noresize" eeimg="1"> 使得 <img src="https://www.zhihu.com/equation?tex=(\bar{x},x_n)\in P" alt="(\bar{x},x_n)\in P" class="ee_img tr_noresize" eeimg="1"> ，则 <img src="https://www.zhihu.com/equation?tex=x=(\bar{x},x_n)" alt="x=(\bar{x},x_n)" class="ee_img tr_noresize" eeimg="1"> 满足约束(3)-(5)，自然也能推出满足约束(6)和(7)，因此 <img src="https://www.zhihu.com/equation?tex=\Pi_{n-1}(P)\subset Q" alt="\Pi_{n-1}(P)\subset Q" class="ee_img tr_noresize" eeimg="1"> .下面将证明 <img src="https://www.zhihu.com/equation?tex=Q\subset \Pi_{n-1}(P)" alt="Q\subset \Pi_{n-1}(P)" class="ee_img tr_noresize" eeimg="1"> .

约束(6)可以推出：

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
\underset{j\vert a_{jn<0}}{min}(d_j+f_j'\bar{x})\ge \underset{i\vert a_{in>0}}{max}(d_i+f_i'\bar{x})
\end{equation*}
" alt="\begin{equation*}
\underset{j\vert a_{jn<0}}{min}(d_j+f_j'\bar{x})\ge \underset{i\vert a_{in>0}}{max}(d_i+f_i'\bar{x})
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
其中 <img src="https://www.zhihu.com/equation?tex=\bar{x}\in Q" alt="\bar{x}\in Q" class="ee_img tr_noresize" eeimg="1"> ,取 <img src="https://www.zhihu.com/equation?tex=x_n" alt="x_n" class="ee_img tr_noresize" eeimg="1"> 为上式两端之间的一个任意值,则 <img src="https://www.zhihu.com/equation?tex=(\bar{x},x_n)" alt="(\bar{x},x_n)" class="ee_img tr_noresize" eeimg="1"> 一定满足约束(3)-(5)，即 <img src="https://www.zhihu.com/equation?tex=\bar{x}\in P" alt="\bar{x}\in P" class="ee_img tr_noresize" eeimg="1"> , 因此,  <img src="https://www.zhihu.com/equation?tex=Q\subset \Pi_{n-1}(P)" alt="Q\subset \Pi_{n-1}(P)" class="ee_img tr_noresize" eeimg="1"> .

同样有

<img src="https://www.zhihu.com/equation?tex=\begin{align*}
\pi_{n-2}(\pi_{n-1}(x))&=\pi_{n-2}(x)\\
&或\\
\Pi_{n-2}(\Pi_{n-1}(P))&=\Pi_{n-2}(P)\\
\end{align*}
" alt="\begin{align*}
\pi_{n-2}(\pi_{n-1}(x))&=\pi_{n-2}(x)\\
&或\\
\Pi_{n-2}(\Pi_{n-1}(P))&=\Pi_{n-2}(P)\\
\end{align*}
" class="ee_img tr_noresize" eeimg="1">
**例子：**考虑多面体：

<img src="https://www.zhihu.com/equation?tex=\begin{align*}
x_1+x_2&\ge1\\
x_1+x_2+2x_3&\ge2\\
2x_1+3x_3&\ge3\\
x_1-4x_3&\ge4\\
-2x_1+x_2-x_3&\ge5\\
\end{align*}
" alt="\begin{align*}
x_1+x_2&\ge1\\
x_1+x_2+2x_3&\ge2\\
2x_1+3x_3&\ge3\\
x_1-4x_3&\ge4\\
-2x_1+x_2-x_3&\ge5\\
\end{align*}
" class="ee_img tr_noresize" eeimg="1">
将约束转成以下形式：

<img src="https://www.zhihu.com/equation?tex=\begin{align*}
0&\ge1-x_1-x_2\\
x_3&\ge1-x_1/2-x_2/2\\
x_3&\ge1-2x_1/3\\
-1+x_1/4&\ge x_3\\
-5-2x_1+x_2&\ge x_3\\
\end{align*}
" alt="\begin{align*}
0&\ge1-x_1-x_2\\
x_3&\ge1-x_1/2-x_2/2\\
x_3&\ge1-2x_1/3\\
-1+x_1/4&\ge x_3\\
-5-2x_1+x_2&\ge x_3\\
\end{align*}
" class="ee_img tr_noresize" eeimg="1">
则多面体Q可以由以下约束定义：

<img src="https://www.zhihu.com/equation?tex=\begin{align*}
0&\ge1-x_1-x_2\\
-1+x_1/4&\ge1-x_1/2-x_2/2\\
-1+x_1/4&\ge1-2x_1/3\\
-5-2x_1+x_2&\ge1-x_1/2-x_2/2\\
-5-2x_1+x_2&\ge1-2x_1/3\\
\end{align*}
" alt="\begin{align*}
0&\ge1-x_1-x_2\\
-1+x_1/4&\ge1-x_1/2-x_2/2\\
-1+x_1/4&\ge1-2x_1/3\\
-5-2x_1+x_2&\ge1-x_1/2-x_2/2\\
-5-2x_1+x_2&\ge1-2x_1/3\\
\end{align*}
" class="ee_img tr_noresize" eeimg="1">
显然每消去一个变量都会产生 <img src="https://www.zhihu.com/equation?tex=I\times J+K" alt="I\times J+K" class="ee_img tr_noresize" eeimg="1"> 个约束， <img src="https://www.zhihu.com/equation?tex=I,J,K" alt="I,J,K" class="ee_img tr_noresize" eeimg="1"> 分别为消去变量系数大于0，小于0，等于0的约束的数量。即使 <img src="https://www.zhihu.com/equation?tex=P_1(P)" alt="P_1(P)" class="ee_img tr_noresize" eeimg="1"> 只有一维，消到这一步很多约束是多余的，但在消元过程中无法确保哪些约束是多余的，必须一一列举。

该消元法可以推导出很多性质：

**推论**： <img src="https://www.zhihu.com/equation?tex=P\subset R^{n+k}" alt="P\subset R^{n+k}" class="ee_img tr_noresize" eeimg="1"> 是一个多面体，则它的投影

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
\{x\in R^n\vert\text{存在}y\in R^k\text{使得}(x,y)\in P\}
\end{equation*}
" alt="\begin{equation*}
\{x\in R^n\vert\text{存在}y\in R^k\text{使得}(x,y)\in P\}
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
也是一个多面体。上述消元法得到Q也是由一些等式、不等式的线性约束定义的，因此是多面体。

**推论**：令 <img src="https://www.zhihu.com/equation?tex=P\subset R^n" alt="P\subset R^n" class="ee_img tr_noresize" eeimg="1"> 是一个多面体,  <img src="https://www.zhihu.com/equation?tex=A" alt="A" class="ee_img tr_noresize" eeimg="1"> 是一个 <img src="https://www.zhihu.com/equation?tex=m\times n" alt="m\times n" class="ee_img tr_noresize" eeimg="1"> 的矩阵，则集合 <img src="https://www.zhihu.com/equation?tex=Q=\{AX\vert x\in P\}" alt="Q=\{AX\vert x\in P\}" class="ee_img tr_noresize" eeimg="1"> 也是一个多面体

**证明**： <img src="https://www.zhihu.com/equation?tex=Q" alt="Q" class="ee_img tr_noresize" eeimg="1"> 可以理解为多面体 <img src="https://www.zhihu.com/equation?tex=\{(x,y)\in R^{n+m}\vert Ax=y,x\in P\}" alt="\{(x,y)\in R^{n+m}\vert Ax=y,x\in P\}" class="ee_img tr_noresize" eeimg="1"> 在y坐标上的投影，即 <img src="https://www.zhihu.com/equation?tex=\{y\in R^m\vert\text{存在}x\in R^m\text{使}Ax=y,x\in P\}" alt="\{y\in R^m\vert\text{存在}x\in R^m\text{使}Ax=y,x\in P\}" class="ee_img tr_noresize" eeimg="1"> 

**推论**：有限个向量的凸壳是多面体。

**证明**：凸壳

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
\{\sum_{i=1}^{k}\lambda_ix^i\vert \sum_{i=1}^k\lambda_i=1,\lambda_i\ge0\}
\end{equation*}
" alt="\begin{equation*}
\{\sum_{i=1}^{k}\lambda_ix^i\vert \sum_{i=1}^k\lambda_i=1,\lambda_i\ge0\}
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
是多面体

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
\{(\lambda_1,\dots\lambda_k)\vert \sum_{i=1}^k\lambda_i=1,\lambda_i\ge0\}
\end{equation*}
" alt="\begin{equation*}
\{(\lambda_1,\dots\lambda_k)\vert \sum_{i=1}^k\lambda_i=1,\lambda_i\ge0\}
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
的一个线性映射，因此也是一个多面体。

最后将说明消元法是怎么解决线性规划问题的。考虑一个线性规划问题具有可行域P并以最小化 <img src="https://www.zhihu.com/equation?tex=c'x" alt="c'x" class="ee_img tr_noresize" eeimg="1"> 为目标，通过引入一个约束 <img src="https://www.zhihu.com/equation?tex=x_0=c'x" alt="x_0=c'x" class="ee_img tr_noresize" eeimg="1"> ，并使用n次消元法将变量 <img src="https://www.zhihu.com/equation?tex=x_1,\dots,x_n" alt="x_1,\dots,x_n" class="ee_img tr_noresize" eeimg="1"> 消去，最后得到

<img src="https://www.zhihu.com/equation?tex=\begin{equation*}
Q=\{x_0\vert\text{存在}x\in P使得x_0=c'x \}
\end{equation*}
" alt="\begin{equation*}
Q=\{x_0\vert\text{存在}x\in P使得x_0=c'x \}
\end{equation*}
" class="ee_img tr_noresize" eeimg="1">
最优的解即是Q的最小元素。
