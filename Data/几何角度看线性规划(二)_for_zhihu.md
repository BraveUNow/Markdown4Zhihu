---
title: 几何角度看线性规划(二)
date: 2022-06-26 14:14:19
categories: 运筹学
tags: 线性规划
mathjax: true
---

## 标准型的多面体

​		一个标准型的多面体可以表示为 <img src="https://www.zhihu.com/equation?tex=P=\{x\in R^n\vert Ax=b,x\ge0\}" alt="P=\{x\in R^n\vert Ax=b,x\ge0\}" class="ee_img tr_noresize" eeimg="1"> ，其中**A**是一个 <img src="https://www.zhihu.com/equation?tex=m\times n" alt="m\times n" class="ee_img tr_noresize" eeimg="1"> 的矩阵，对应m个等式约束和n个变量，并假设m个约束是相互独立(这要求 <img src="https://www.zhihu.com/equation?tex=m\le n" alt="m\le n" class="ee_img tr_noresize" eeimg="1"> ，事实上线性相关的约束可以被舍弃而不影响解的性质)

​		上一章提到，一个基解是通过求解n个线性无关约束组成的线性方程组得到的，由于标准型的约束数量m不多于n，为了获得一个基解，需要选择m-n个变量并令它们为0，即令这m-n个变量对应的约束 <img src="https://www.zhihu.com/equation?tex=x_i\ge0" alt="x_i\ge0" class="ee_img tr_noresize" eeimg="1"> 成为有效约束。其中对于这m-n个约束的选择并不是随意的。

**定理**：对于一个标准型的多面体，向量 <img src="https://www.zhihu.com/equation?tex=x\in R^n" alt="x\in R^n" class="ee_img tr_noresize" eeimg="1"> 是一个基解当且仅当有 <img src="https://www.zhihu.com/equation?tex=Ax=b" alt="Ax=b" class="ee_img tr_noresize" eeimg="1"> ，且存在索引 <img src="https://www.zhihu.com/equation?tex=B(1),\dots,B(m)" alt="B(1),\dots,B(m)" class="ee_img tr_noresize" eeimg="1"> 令：

1. 列 <img src="https://www.zhihu.com/equation?tex=A_{B(1)},\dots, A_{B(m)}" alt="A_{B(1)},\dots, A_{B(m)}" class="ee_img tr_noresize" eeimg="1"> 相互线性独立
2. 如果 <img src="https://www.zhihu.com/equation?tex=i\neq B(1),\dots,B(m)" alt="i\neq B(1),\dots,B(m)" class="ee_img tr_noresize" eeimg="1"> ，则 <img src="https://www.zhihu.com/equation?tex=x_i=0" alt="x_i=0" class="ee_img tr_noresize" eeimg="1"> 

**证明**：假设 <img src="https://www.zhihu.com/equation?tex=x\in R^n" alt="x\in R^n" class="ee_img tr_noresize" eeimg="1"> ，且存在 <img src="https://www.zhihu.com/equation?tex=B(1),\dots,B(m)" alt="B(1),\dots,B(m)" class="ee_img tr_noresize" eeimg="1"> 满足定理的表述，则有

<img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^{m}A_{B(i)}x_{B(i)}=\sum_{i=1}^nA_ix_i=Ax=b
" alt="\sum_{i=1}^{m}A_{B(i)}x_{B(i)}=\sum_{i=1}^nA_ix_i=Ax=b
" class="ee_img tr_noresize" eeimg="1">
​		由于列 <img src="https://www.zhihu.com/equation?tex=A_{B(1)},\dots, A_{B(m)}" alt="A_{B(1)},\dots, A_{B(m)}" class="ee_img tr_noresize" eeimg="1"> 相互线性独立，因此 <img src="https://www.zhihu.com/equation?tex=x_{B(1)},\dots,x_{B(m)}" alt="x_{B(1)},\dots,x_{B(m)}" class="ee_img tr_noresize" eeimg="1"> 的值是唯一的，即由n个有效约束形成的线性方程组有唯一解(其余n-m个变量值都为0)，说明 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 是一个基解。

​		相反，若 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 是一个基解。令 <img src="https://www.zhihu.com/equation?tex=x_{B(1)},\dots,x_{B(k)}" alt="x_{B(1)},\dots,x_{B(k)}" class="ee_img tr_noresize" eeimg="1"> 表示 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 中非0的索引。由于 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 是基解，因此线性方程组 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^nA_ix_i=b" alt="\sum_{i=1}^nA_ix_i=b" class="ee_img tr_noresize" eeimg="1"> 和 <img src="https://www.zhihu.com/equation?tex=x_i=0,i\neq B(1),\dots,B(k)" alt="x_i=0,i\neq B(1),\dots,B(k)" class="ee_img tr_noresize" eeimg="1"> 有唯一解，即 <img src="https://www.zhihu.com/equation?tex=x_{B(1)},\dots,x_{B(k)}" alt="x_{B(1)},\dots,x_{B(k)}" class="ee_img tr_noresize" eeimg="1"> 是线性方程组组 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^kA_ix_i=b_i" alt="\sum_{i=1}^kA_ix_i=b_i" class="ee_img tr_noresize" eeimg="1"> 的唯一解，进而得到 <img src="https://www.zhihu.com/equation?tex=A_{B(1)},\dots A_{B(k)}" alt="A_{B(1)},\dots A_{B(k)}" class="ee_img tr_noresize" eeimg="1"> 是线性独立的。因为若不是相互线性独立，则存在不全为零的标量 <img src="https://www.zhihu.com/equation?tex=\lambda_1,\dots,\lambda_k" alt="\lambda_1,\dots,\lambda_k" class="ee_img tr_noresize" eeimg="1"> 满足 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^kA_i\lambda_i=0" alt="\sum_{i=1}^kA_i\lambda_i=0" class="ee_img tr_noresize" eeimg="1"> ，进而 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^kA_i(x_i+\lambda_i)=b_i" alt="\sum_{i=1}^kA_i(x_i+\lambda_i)=b_i" class="ee_img tr_noresize" eeimg="1"> ，与前面解的唯一性相矛盾。

<!--more-->

​		由于 <img src="https://www.zhihu.com/equation?tex=A_{B(1)},\dots A_{B(k)}" alt="A_{B(1)},\dots A_{B(k)}" class="ee_img tr_noresize" eeimg="1"> 线性独立，则可以得出 <img src="https://www.zhihu.com/equation?tex=k\le m" alt="k\le m" class="ee_img tr_noresize" eeimg="1"> (矩阵最大的秩为m)。由于m有个线性独立的行，也一定能找到m个线性独立的列。因此，我们能找到m-k个额外的列 <img src="https://www.zhihu.com/equation?tex=A_{k+1},\dots,A(m)" alt="A_{k+1},\dots,A(m)" class="ee_img tr_noresize" eeimg="1"> 使得列 <img src="https://www.zhihu.com/equation?tex=A_{B(1)},\dots,A_{B(m)}" alt="A_{B(1)},\dots,A_{B(m)}" class="ee_img tr_noresize" eeimg="1"> 线性独立。则如果 <img src="https://www.zhihu.com/equation?tex=i\neq B(1),\dots,B(m)" alt="i\neq B(1),\dots,B(m)" class="ee_img tr_noresize" eeimg="1"> ，有 <img src="https://www.zhihu.com/equation?tex=i\neq B(1),\dots,B(k)" alt="i\neq B(1),\dots,B(k)" class="ee_img tr_noresize" eeimg="1"> ，得到 <img src="https://www.zhihu.com/equation?tex=x_i=0" alt="x_i=0" class="ee_img tr_noresize" eeimg="1"> 。因此，定理的两个表述都得到满足。

​		根据以上理论，任何一个基解都可以用以下的步骤确定：

1. 选择m个线性独立的列 <img src="https://www.zhihu.com/equation?tex=A_{B(1)},\dots A_{B(m)}" alt="A_{B(1)},\dots A_{B(m)}" class="ee_img tr_noresize" eeimg="1"> 
2. 对所有 <img src="https://www.zhihu.com/equation?tex=i\neq B(1),\dots,B(m)" alt="i\neq B(1),\dots,B(m)" class="ee_img tr_noresize" eeimg="1"> ,令 <img src="https://www.zhihu.com/equation?tex=x_i=0" alt="x_i=0" class="ee_img tr_noresize" eeimg="1"> 
3. 解线性方程组 <img src="https://www.zhihu.com/equation?tex=Ax=b" alt="Ax=b" class="ee_img tr_noresize" eeimg="1"> ， <img src="https://www.zhihu.com/equation?tex=[x_{B(1)},\dots,x_{B(m)}]^T" alt="[x_{B(1)},\dots,x_{B(m)}]^T" class="ee_img tr_noresize" eeimg="1"> 

​		通过以上步骤，如果得到的基解都是非负的，则该基解是一个基可行解。对于一个基解，变量 <img src="https://www.zhihu.com/equation?tex=x_{B(1)},\dots,x_{B(m)}" alt="x_{B(1)},\dots,x_{B(m)}" class="ee_img tr_noresize" eeimg="1"> 被称为基变量(basic variables)，其余变量被称为非基变量(nonbasic)，而基向量对应的列 <img src="https://www.zhihu.com/equation?tex=A_{B(1)},\dots A_{B(m)}" alt="A_{B(1)},\dots A_{B(m)}" class="ee_img tr_noresize" eeimg="1"> 被称为基列向量(basic columns)，这m个向量构成了空间 <img src="https://www.zhihu.com/equation?tex=R^m" alt="R^m" class="ee_img tr_noresize" eeimg="1"> 的一个基。一般认为如果两个基有不同的索引 <img src="https://www.zhihu.com/equation?tex=\{B(1),\dots,B(m\}" alt="\{B(1),\dots,B(m\}" class="ee_img tr_noresize" eeimg="1"> ，则称这两个基是不同的(索引相同顺序不同也视为同一个基)

​		在确定一个基后，该基的值可以通过求解线性方程组 <img src="https://www.zhihu.com/equation?tex=Bx_B=b" alt="Bx_B=b" class="ee_img tr_noresize" eeimg="1"> 来确定，其中 <img src="https://www.zhihu.com/equation?tex=B" alt="B" class="ee_img tr_noresize" eeimg="1"> 是由所有基变量对应的列向量组成的 <img src="https://www.zhihu.com/equation?tex=A" alt="A" class="ee_img tr_noresize" eeimg="1"> 的一个分块矩阵，由于 <img src="https://www.zhihu.com/equation?tex=B" alt="B" class="ee_img tr_noresize" eeimg="1"> 的列向量都是线性独立的，因此 <img src="https://www.zhihu.com/equation?tex=B" alt="B" class="ee_img tr_noresize" eeimg="1"> 一定可逆， <img src="https://www.zhihu.com/equation?tex=x_B" alt="x_B" class="ee_img tr_noresize" eeimg="1"> 可以通过计算 <img src="https://www.zhihu.com/equation?tex=B^{-1}b" alt="B^{-1}b" class="ee_img tr_noresize" eeimg="1"> 唯一确定。

​		从另一个角度看， <img src="https://www.zhihu.com/equation?tex=Ax=b" alt="Ax=b" class="ee_img tr_noresize" eeimg="1"> 或 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^nA_ix_i=b" alt="\sum_{i=1}^nA_ix_i=b" class="ee_img tr_noresize" eeimg="1"> 可以看做为列向量 <img src="https://www.zhihu.com/equation?tex=A_i" alt="A_i" class="ee_img tr_noresize" eeimg="1"> 通过对应的系数 <img src="https://www.zhihu.com/equation?tex=x_i" alt="x_i" class="ee_img tr_noresize" eeimg="1"> 相加而合成向量 <img src="https://www.zhihu.com/equation?tex=b" alt="b" class="ee_img tr_noresize" eeimg="1"> 。假设考虑一个m=2, n=4的标准型，4个变量列向量分别对应下图中的 <img src="https://www.zhihu.com/equation?tex=A_1,A_2,A_3,A_4" alt="A_1,A_2,A_3,A_4" class="ee_img tr_noresize" eeimg="1"> ，当令 <img src="https://www.zhihu.com/equation?tex=A_1,A_2" alt="A_1,A_2" class="ee_img tr_noresize" eeimg="1"> 形成一个基时，得到的基解是不可行的，因为 <img src="https://www.zhihu.com/equation?tex=x_2" alt="x_2" class="ee_img tr_noresize" eeimg="1"> 一定要小于0才能将 <img src="https://www.zhihu.com/equation?tex=A_1,A_2" alt="A_1,A_2" class="ee_img tr_noresize" eeimg="1"> 合成到 <img src="https://www.zhihu.com/equation?tex=b" alt="b" class="ee_img tr_noresize" eeimg="1"> 。同理 <img src="https://www.zhihu.com/equation?tex=A_1,A_3" alt="A_1,A_3" class="ee_img tr_noresize" eeimg="1"> 为基得到的基解是可行的，而 <img src="https://www.zhihu.com/equation?tex=A_1,A_4" alt="A_1,A_4" class="ee_img tr_noresize" eeimg="1"> 无法形成一个基，因为这两个向量是线性相关的。

<img src="https://raw.githubusercontent.com/BraveUNow/Markdown4Zhihu/master/Data/几何角度看线性规划(二)/synthesizeVector.png" style="zoom:30%;" />

### 基和基解的对应关系

前文提到两个基解是相邻的当它们有相同的n-1个有效约束，在标准形式下，我们称两个基是相邻的当它们有n-1个相同的基列向量索引，因此相邻的基解可以通过相邻的基获得。

**推论**：令 <img src="https://www.zhihu.com/equation?tex=P=\{x\vert Ax=b,x\ge0\}" alt="P=\{x\vert Ax=b,x\ge0\}" class="ee_img tr_noresize" eeimg="1"> 为一个非空的多面体，其中 <img src="https://www.zhihu.com/equation?tex=A" alt="A" class="ee_img tr_noresize" eeimg="1"> 是一个 <img src="https://www.zhihu.com/equation?tex=m\times n" alt="m\times n" class="ee_img tr_noresize" eeimg="1"> 矩阵，其行索引为 <img src="https://www.zhihu.com/equation?tex=a_1',\dots,a_m'" alt="a_1',\dots,a_m'" class="ee_img tr_noresize" eeimg="1"> ，假设 <img src="https://www.zhihu.com/equation?tex=rank(A)=k\lt m" alt="rank(A)=k\lt m" class="ee_img tr_noresize" eeimg="1"> 且行 <img src="https://www.zhihu.com/equation?tex=a_{i1}',\dots,a_{ik}'" alt="a_{i1}',\dots,a_{ik}'" class="ee_img tr_noresize" eeimg="1"> 是线性独立的，则多面体 <img src="https://www.zhihu.com/equation?tex=Q=\{x\vert a'_{i1}x=b_{i1},\dots,a_{ik}'x=b_{ik},x\ge0\}" alt="Q=\{x\vert a'_{i1}x=b_{i1},\dots,a_{ik}'x=b_{ik},x\ge0\}" class="ee_img tr_noresize" eeimg="1"> ，则 <img src="https://www.zhihu.com/equation?tex=Q=P" alt="Q=P" class="ee_img tr_noresize" eeimg="1"> 

**证明**：假设矩阵A的前k行是线性独立的，即 <img src="https://www.zhihu.com/equation?tex=i_1=1,\dots,i_k=k" alt="i_1=1,\dots,i_k=k" class="ee_img tr_noresize" eeimg="1"> 。显然 <img src="https://www.zhihu.com/equation?tex=P\subset Q" alt="P\subset Q" class="ee_img tr_noresize" eeimg="1"> ,因为任何满足Q所有约束的解都满足P的所有约束。由于 <img src="https://www.zhihu.com/equation?tex=rank(A)=k" alt="rank(A)=k" class="ee_img tr_noresize" eeimg="1"> ，则行向量 <img src="https://www.zhihu.com/equation?tex=a_{i1}',\dots,a_{ik}'" alt="a_{i1}',\dots,a_{ik}'" class="ee_img tr_noresize" eeimg="1"> 构成了行空间的一个基，因此A的任意一个行向量 <img src="https://www.zhihu.com/equation?tex=a_i'" alt="a_i'" class="ee_img tr_noresize" eeimg="1"> 都能表示为 <img src="https://www.zhihu.com/equation?tex=a_i'=\sum_{j=1}^k\lambda_{ija_j'}" alt="a_i'=\sum_{j=1}^k\lambda_{ija_j'}" class="ee_img tr_noresize" eeimg="1"> .令 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 表示P的一个约束，则

<img src="https://www.zhihu.com/equation?tex=b_i=a_i'x=\sum_{j=1}^k\lambda_{ij}a_j'x=\sum_{j=1}^k\lambda_{ij}b_j
" alt="b_i=a_i'x=\sum_{j=1}^k\lambda_{ij}a_j'x=\sum_{j=1}^k\lambda_{ij}b_j
" class="ee_img tr_noresize" eeimg="1">
因此，对于Q中的任意一个元素y，都可以表示为：

<img src="https://www.zhihu.com/equation?tex=a_i'y=\sum_{j=1}^k\lambda_{ij}a_j'y=\sum_{j=1}^k\lambda_{ij}b_j=b_i
" alt="a_i'y=\sum_{j=1}^k\lambda_{ij}a_j'y=\sum_{j=1}^k\lambda_{ij}b_j=b_i
" class="ee_img tr_noresize" eeimg="1">
即 <img src="https://www.zhihu.com/equation?tex=y\in P" alt="y\in P" class="ee_img tr_noresize" eeimg="1"> ，因此得到 <img src="https://www.zhihu.com/equation?tex=Q\subset P" alt="Q\subset P" class="ee_img tr_noresize" eeimg="1"> ，进而推出 <img src="https://www.zhihu.com/equation?tex=Q=P" alt="Q=P" class="ee_img tr_noresize" eeimg="1"> 

因此，在可行域非空的情况下，一个标准型的线性规划问题总能转为一个所有等式约束都相互独立的等价的标准型问题。

### 退化解

**定义**：当在基解 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 处有超过n个有效约束，则称 <img src="https://www.zhihu.com/equation?tex=x\in R^n" alt="x\in R^n" class="ee_img tr_noresize" eeimg="1"> 是退化解。

在二维空间，一个退化解是三个及以上直线的交点，三维空间是四个以上平面的交界。考虑多面体P：

<img src="https://www.zhihu.com/equation?tex=\begin{align}
x_1+x_2+2x_3&\le8\\
x_2+6x_3&\le12\\
x_1&\le4\\
x_2&\le6\\
x_1,x_2,x_3&\ge0\\
\end{align}
" alt="\begin{align}
x_1+x_2+2x_3&\le8\\
x_2+6x_3&\le12\\
x_1&\le4\\
x_2&\le6\\
x_1,x_2,x_3&\ge0\\
\end{align}
" class="ee_img tr_noresize" eeimg="1">
​		向量 <img src="https://www.zhihu.com/equation?tex=x=(2,6,0)" alt="x=(2,6,0)" class="ee_img tr_noresize" eeimg="1"> 不是退化解，而向量 <img src="https://www.zhihu.com/equation?tex=x=(4,0,2)" alt="x=(4,0,2)" class="ee_img tr_noresize" eeimg="1"> 是退化解，因为它同时满足4个有效约束，分别为 <img src="https://www.zhihu.com/equation?tex=x_1+x_2+2x_3\le8,x_2+6x_3\le12,x_1\le4,x_2\ge_0" alt="x_1+x_2+2x_3\le8,x_2+6x_3\le12,x_1\le4,x_2\ge_0" class="ee_img tr_noresize" eeimg="1"> 

​		而对于一个标准型的多面体，其m个等式约束一定是有效的，因此拥有超过n个有效约束与拥有超过n-m个值为零的变量是等价的，即引出以下定义：

**定义**：对于标准型 <img src="https://www.zhihu.com/equation?tex=P=\{x\in R^n\vert Ax=b,x\ge0\}" alt="P=\{x\in R^n\vert Ax=b,x\ge0\}" class="ee_img tr_noresize" eeimg="1"> ,  <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 是一个基解, m是 <img src="https://www.zhihu.com/equation?tex=A" alt="A" class="ee_img tr_noresize" eeimg="1"> 的行数。当向量 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 有超过n-m个为的元素， <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 是一个退化的基解。

当基解 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 是退化的时候，我们有超过一种方式从这些值为的变量中选择n-m个变量作为非基变量，在这种情况下，会出现几个不同的基对应同一个基解的情况。

一个基可行解的退化不完全是多面体的几何性质，它依赖于一个多面体的特定描述。考虑多面体：

<img src="https://www.zhihu.com/equation?tex=P=\{(x_1.x_2,x_3)\vert x_1-x_2=0,x_1+x_2+2x_3=2,x_1,x_2,x_3\ge0\}
" alt="P=\{(x_1.x_2,x_3)\vert x_1-x_2=0,x_1+x_2+2x_3=2,x_1,x_2,x_3\ge0\}
" class="ee_img tr_noresize" eeimg="1">
<img src="https://raw.githubusercontent.com/BraveUNow/Markdown4Zhihu/master/Data/几何角度看线性规划(二)/degenerationSample.png" style="zoom:50%;" />

该多面体n=3,m=2，则n-m=1.向量(1,1,0)是非退化解，因为只有一个变量值为0.而向量(0,0,1)是退化解，因为有2个变量值为0.但对该多面体换一种方式描述 <img src="https://www.zhihu.com/equation?tex=P=\{(x_1.x_2,x_3)\vert x_1-x_2=0,x_1+x_2+2x_3=2,x_1,x_3\ge0\}" alt="P=\{(x_1.x_2,x_3)\vert x_1-x_2=0,x_1+x_2+2x_3=2,x_1,x_3\ge0\}" class="ee_img tr_noresize" eeimg="1"> ,向量(0,0,1)就不再是一个退化基可行解了。

因此，一个基可行解在一种表述下是退化解，而在另一种表述下可能就不是退化解。

## 极点(extreme point)

### 极点的存在性

本节说明极点存在的条件，首先引入下面的概念：

**定义**：多面体 <img src="https://www.zhihu.com/equation?tex=P\subset R^n" alt="P\subset R^n" class="ee_img tr_noresize" eeimg="1"> 含有一条直线，当存在向量 <img src="https://www.zhihu.com/equation?tex=x\in P" alt="x\in P" class="ee_img tr_noresize" eeimg="1"> 和非零向量 <img src="https://www.zhihu.com/equation?tex=d\in R^n" alt="d\in R^n" class="ee_img tr_noresize" eeimg="1"> 对于任意标量 <img src="https://www.zhihu.com/equation?tex=\lambda" alt="\lambda" class="ee_img tr_noresize" eeimg="1"> 满足 <img src="https://www.zhihu.com/equation?tex=x+\lambda d\in P" alt="x+\lambda d\in P" class="ee_img tr_noresize" eeimg="1"> 

不是所有多面体都有极点的，如一个半空间就不存在顶点，下面将给出极点存在性的等价表示：

**定理**：设多面体 <img src="https://www.zhihu.com/equation?tex=P=\{x\in R^n\vert a_i'x\ge b_i,i=1,\dots,m\}" alt="P=\{x\in R^n\vert a_i'x\ge b_i,i=1,\dots,m\}" class="ee_img tr_noresize" eeimg="1"> 非空，则一下表述是等价的：

1. 多面体P至少存在一个极点
2. 多面体P不含有一条直线
3. 在向量组 <img src="https://www.zhihu.com/equation?tex=a_1,\dots,a_m" alt="a_1,\dots,a_m" class="ee_img tr_noresize" eeimg="1"> 中有n个相互线性独立的向量

**证明**：

(2)→(1)：首先证明如果P不含有一条直线，则一定存在一个极点。令 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 为P中的一个元素，且 <img src="https://www.zhihu.com/equation?tex=I=\{i\vert a_i'x=b_i\}" alt="I=\{i\vert a_i'x=b_i\}" class="ee_img tr_noresize" eeimg="1"> 。如果I中存在n个线性无关的向量，即有n个线性无关的独立约束，则 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 显然是一个基可行解，根据之前的证明，基可行解和极点是等价的。若I中不存在n个线性无关的向量，则所有 <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 构成了 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 的一个子空间，则存在非零向量 <img src="https://www.zhihu.com/equation?tex=d\in R^n" alt="d\in R^n" class="ee_img tr_noresize" eeimg="1"> 与所有 <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 正交使 <img src="https://www.zhihu.com/equation?tex=a_i'd=0,i\in I" alt="a_i'd=0,i\in I" class="ee_img tr_noresize" eeimg="1"> 。考虑向量 <img src="https://www.zhihu.com/equation?tex=y=x+\lambda d" alt="y=x+\lambda d" class="ee_img tr_noresize" eeimg="1"> ，当 <img src="https://www.zhihu.com/equation?tex=i\in I" alt="i\in I" class="ee_img tr_noresize" eeimg="1"> 时， <img src="https://www.zhihu.com/equation?tex=a_i'y=a_i'x+\lambda a_id=a_i'x=b_i" alt="a_i'y=a_i'x+\lambda a_id=a_i'x=b_i" class="ee_img tr_noresize" eeimg="1"> ，即对于I中的约束仍为有效约束。但由于多面体不含有直线，因此当 <img src="https://www.zhihu.com/equation?tex=\lambda" alt="\lambda" class="ee_img tr_noresize" eeimg="1"> 大到某一个值 <img src="https://www.zhihu.com/equation?tex=\lambda^*" alt="\lambda^*" class="ee_img tr_noresize" eeimg="1"> 时一定会有一些约束 <img src="https://www.zhihu.com/equation?tex=j\notin I" alt="j\notin I" class="ee_img tr_noresize" eeimg="1"> 将要被违背，这时候的向量y相比向量x多了一个有效约束，通过这样的方式不断添加有效约束，最终可以得到一个极点。

(1)→(3)：如果P是一个极点，则P也是一个基可行解，因此在 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 处存在n个有效约束，其对于的向量 <img src="https://www.zhihu.com/equation?tex=a_i" alt="a_i" class="ee_img tr_noresize" eeimg="1"> 也是相互线性独立的

(3)→(2)：不失一般性假设 <img src="https://www.zhihu.com/equation?tex=a_1,\dots,a_n" alt="a_1,\dots,a_n" class="ee_img tr_noresize" eeimg="1"> 是相互线性独立的。若 <img src="https://www.zhihu.com/equation?tex=P" alt="P" class="ee_img tr_noresize" eeimg="1"> 存在一条直线 <img src="https://www.zhihu.com/equation?tex=x+\lambda d" alt="x+\lambda d" class="ee_img tr_noresize" eeimg="1"> ， <img src="https://www.zhihu.com/equation?tex=d\in R^n,d>0" alt="d\in R^n,d>0" class="ee_img tr_noresize" eeimg="1"> 则对所有的 <img src="https://www.zhihu.com/equation?tex=i,\lambda" alt="i,\lambda" class="ee_img tr_noresize" eeimg="1"> 有 <img src="https://www.zhihu.com/equation?tex=a_i'(x+\lambda d)\ge b_i" alt="a_i'(x+\lambda d)\ge b_i" class="ee_img tr_noresize" eeimg="1"> ，因此 <img src="https://www.zhihu.com/equation?tex=a_i'd=0" alt="a_i'd=0" class="ee_img tr_noresize" eeimg="1"> ，但由于 <img src="https://www.zhihu.com/equation?tex=a_i,\dots,a_n" alt="a_i,\dots,a_n" class="ee_img tr_noresize" eeimg="1"> 是相互线性独立的能够构成 <img src="https://www.zhihu.com/equation?tex=R_n" alt="R_n" class="ee_img tr_noresize" eeimg="1"> 的一个基，则d=0，与前面假设矛盾，因此多面体不存在一条直线。

一个有界的多面体不存在一条直线，比如一个正象限 <img src="https://www.zhihu.com/equation?tex=\{x\vert x\ge 0\}" alt="\{x\vert x\ge 0\}" class="ee_img tr_noresize" eeimg="1"> 不存在一条直线。由于一个标准型的多面体被正象限所包括，它一定也不存在一条直线，因此一个非空有界的多面体或一个标准型的多面体至少有一个基可行解。

### 极点的最优性

在建立极点的存在性条件后，本节将证明如果一个线性规划问题有最优解且可行域存在至少一个极点，则最优解出现在极点上。

**定理**：可行域为多面体P的线性规划问题以最小化成本 <img src="https://www.zhihu.com/equation?tex=c'x" alt="c'x" class="ee_img tr_noresize" eeimg="1"> 为目标函数，设P有至少一个极点且问题有最优解，则存在一个最优解是P的一个极点。

**证明**：令Q表示最优解的集合，v表示成本 <img src="https://www.zhihu.com/equation?tex=c'x" alt="c'x" class="ee_img tr_noresize" eeimg="1"> 的最小值，则Q可以表示为 <img src="https://www.zhihu.com/equation?tex=Q=\{x\in R^n\vert Ax\ge b,c'x=v\}" alt="Q=\{x\in R^n\vert Ax\ge b,c'x=v\}" class="ee_img tr_noresize" eeimg="1"> ，也是一个多面体。由于P存在极点，即P不存在一条直线，而 <img src="https://www.zhihu.com/equation?tex=Q\subset P" alt="Q\subset P" class="ee_img tr_noresize" eeimg="1"> ，也不存在一条直线，有至少一个极点。设 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 为Q的一个极点，若 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 不是P的极点，存在 <img src="https://www.zhihu.com/equation?tex=y\in P,z\in P" alt="y\in P,z\in P" class="ee_img tr_noresize" eeimg="1"> 使得 <img src="https://www.zhihu.com/equation?tex=x=\lambda y+(1-\lambda)z,z\in[0,1]" alt="x=\lambda y+(1-\lambda)z,z\in[0,1]" class="ee_img tr_noresize" eeimg="1"> , 则 <img src="https://www.zhihu.com/equation?tex=v=c'x=c'\lambda y+c'(1-\lambda)z" alt="v=c'x=c'\lambda y+c'(1-\lambda)z" class="ee_img tr_noresize" eeimg="1"> ，由于v是原问题的最优解， <img src="https://www.zhihu.com/equation?tex=c'y\ge v,c'z\ge z" alt="c'y\ge v,c'z\ge z" class="ee_img tr_noresize" eeimg="1"> ，只有 <img src="https://www.zhihu.com/equation?tex=c'y=c'z=v" alt="c'y=c'z=v" class="ee_img tr_noresize" eeimg="1"> 时等式成立，这表示 <img src="https://www.zhihu.com/equation?tex=y\in Q,z\in Q" alt="y\in Q,z\in Q" class="ee_img tr_noresize" eeimg="1"> ，与 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 是Q的一个极点相矛盾，因此 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 是P的一个极点。

上述证明适用于标准型或有界的多面体，因为它们不包含直线。下面的证明将表示如果最优解不是无穷的，则一定存在最优解出现在极点上。

**定理**：可行域为多面体P的线性规划问题以最小化成本 <img src="https://www.zhihu.com/equation?tex=c'x" alt="c'x" class="ee_img tr_noresize" eeimg="1"> 为目标函数，设P至少有一个极点，则要么最优解的值为 <img src="https://www.zhihu.com/equation?tex=-\infty" alt="-\infty" class="ee_img tr_noresize" eeimg="1"> ，或存在一个极点为最优解。

**证明**：在证明前使用以下术语：向量 <img src="https://www.zhihu.com/equation?tex=x\in P" alt="x\in P" class="ee_img tr_noresize" eeimg="1"> 的秩为k，当在 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 处可以找到最多k个线性无关的有效约束。设最优解是有界的，考虑一些 <img src="https://www.zhihu.com/equation?tex=x\in P,rank(x)=k<n" alt="x\in P,rank(x)=k<n" class="ee_img tr_noresize" eeimg="1"> ，令 <img src="https://www.zhihu.com/equation?tex=I=\{i\vert a_i'x=b_i\}" alt="I=\{i\vert a_i'x=b_i\}" class="ee_img tr_noresize" eeimg="1"> ，由于k<n，因此 <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 张成了 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 的一个子空间，存在向量 <img src="https://www.zhihu.com/equation?tex=d\ne 0" alt="d\ne 0" class="ee_img tr_noresize" eeimg="1"> 与所有 <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 正交使 <img src="https://www.zhihu.com/equation?tex=a_id=0" alt="a_id=0" class="ee_img tr_noresize" eeimg="1"> ，通过选择 <img src="https://www.zhihu.com/equation?tex=d" alt="d" class="ee_img tr_noresize" eeimg="1"> 的值的正负性可以令 <img src="https://www.zhihu.com/equation?tex=c'd<0" alt="c'd<0" class="ee_img tr_noresize" eeimg="1"> 。考虑射线 <img src="https://www.zhihu.com/equation?tex=y=x+\lambda d" alt="y=x+\lambda d" class="ee_img tr_noresize" eeimg="1"> ，由于d与x的有效约束向量正交，因此有 <img src="https://www.zhihu.com/equation?tex=a_iy=b_i,i\in I" alt="a_iy=b_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 。当整条射线都在P内部时， <img src="https://www.zhihu.com/equation?tex=\vert d\vert" alt="\vert d\vert" class="ee_img tr_noresize" eeimg="1"> 可以取无限大，则最小成本就为 <img src="https://www.zhihu.com/equation?tex=-\infty" alt="-\infty" class="ee_img tr_noresize" eeimg="1"> 。若只有部分在P内部，则在边界上有 <img src="https://www.zhihu.com/equation?tex=\lambda^*>0,j\notin I" alt="\lambda^*>0,j\notin I" class="ee_img tr_noresize" eeimg="1"> 使得 <img src="https://www.zhihu.com/equation?tex=a_j'(x+\lambda^*d)=a_j'y=b_j" alt="a_j'(x+\lambda^*d)=a_j'y=b_j" class="ee_img tr_noresize" eeimg="1"> ，由于 <img src="https://www.zhihu.com/equation?tex=c'd<0" alt="c'd<0" class="ee_img tr_noresize" eeimg="1"> ，因此 <img src="https://www.zhihu.com/equation?tex=c'y<c'x" alt="c'y<c'x" class="ee_img tr_noresize" eeimg="1"> ，且此时y的秩为k+1. 如果c与d也是正交的，则最后得到 <img src="https://www.zhihu.com/equation?tex=c'y=c'x" alt="c'y=c'x" class="ee_img tr_noresize" eeimg="1"> ，

​		通过这种方式总可以找到一个新的向量 <img src="https://www.zhihu.com/equation?tex=y\in P,c'y\le c'x,rank(y)>rank(x)" alt="y\in P,c'y\le c'x,rank(y)>rank(x)" class="ee_img tr_noresize" eeimg="1"> ，通过重复这种方式最终可以找到一个向量 <img src="https://www.zhihu.com/equation?tex=w" alt="w" class="ee_img tr_noresize" eeimg="1"> 令 <img src="https://www.zhihu.com/equation?tex=c'w\le c'x" alt="c'w\le c'x" class="ee_img tr_noresize" eeimg="1"> ，且 <img src="https://www.zhihu.com/equation?tex=w" alt="w" class="ee_img tr_noresize" eeimg="1"> 的秩为n。因此 <img src="https://www.zhihu.com/equation?tex=w" alt="w" class="ee_img tr_noresize" eeimg="1"> 是一个基可行解，也是一个极点。令 <img src="https://www.zhihu.com/equation?tex=w^1,\dots,w^r" alt="w^1,\dots,w^r" class="ee_img tr_noresize" eeimg="1"> 表示P中基可行解的集合，且 <img src="https://www.zhihu.com/equation?tex=w^*" alt="w^*" class="ee_img tr_noresize" eeimg="1"> 是最优的基可行解 <img src="https://www.zhihu.com/equation?tex=c'w^*\le c'w^i" alt="c'w^*\le c'w^i" class="ee_img tr_noresize" eeimg="1"> 。前面已经证明了对于每一个 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 都能找到一些 <img src="https://www.zhihu.com/equation?tex=i" alt="i" class="ee_img tr_noresize" eeimg="1"> 令 <img src="https://www.zhihu.com/equation?tex=c'w^i\le c'x" alt="c'w^i\le c'x" class="ee_img tr_noresize" eeimg="1"> ，因此可以得到 <img src="https://www.zhihu.com/equation?tex=c'w^*\le c'x" alt="c'w^*\le c'x" class="ee_img tr_noresize" eeimg="1"> ， <img src="https://www.zhihu.com/equation?tex=w^*" alt="w^*" class="ee_img tr_noresize" eeimg="1"> 是最优的。

