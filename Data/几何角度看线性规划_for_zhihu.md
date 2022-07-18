---
title: 几何角度看线性规划
date: 2022-06-04 13:43:36
categories: 运筹学
tags: 线性规划
mathjax: true
---

# 几何角度看线性规划

最近在阅读Dimitris Bertsimas和John N. Tsitsiklis写的Introduction to linear optimization，学习过程中发现很多基本概念及其推导在我之前学运筹学的时候都忽视了，我学习运筹学时用的教材是清华大学出版社的《运筹学》第四版，这本书虽然我觉得写得不错，但可能由于需要介绍的知识太多，很多基本概念或细节没有深入介绍，相信很多人学习这本书的感受跟我一样。因此，在学习过程中，我也希望将这些内容分享给大家。

文章的主题为从几何角度看线性规划，内容包括线性规划的一些术语（多面体、极点等）介绍和一些性质推导，阅读本章需要有一些线性代数基础（不需要很多）。由于内容有点多，可能需要分好几节来进行介绍(作者本人也在一边看一边学:joy:)，作者自己也只是一个本科生，全靠个人兴趣进行分享(可能很久才更一次:eyes:)，如果有什么地方讲得不对也希望大家能纠正。本章内容基于Introduction to linear optimization第二章，图片使用GeoGebra进行绘制。

## 多面体和凸集

### 多面体

在介绍多面体(polyhedron)之前，需要先引入超平面(hyperplane)和半空间(halfspace)的概念。假设 <img src="https://www.zhihu.com/equation?tex=a" alt="a" class="ee_img tr_noresize" eeimg="1"> 是 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 内的一个向量, <img src="https://www.zhihu.com/equation?tex=b" alt="b" class="ee_img tr_noresize" eeimg="1"> 是一个标量，则：

- **超平面**为空间中的一个集合 <img src="https://www.zhihu.com/equation?tex=\{x\in R^n\vert a'x=b\}" alt="\{x\in R^n\vert a'x=b\}" class="ee_img tr_noresize" eeimg="1"> 
- **半空间**为空间中的一个集合 <img src="https://www.zhihu.com/equation?tex=\{x\in R^n\vert a'x\ge b\}" alt="\{x\in R^n\vert a'x\ge b\}" class="ee_img tr_noresize" eeimg="1"> 

上述的意思很简单，超平面就是一条将整个空间分为两个部分的边界，在二维空间中表现为一条直线如 <img src="https://www.zhihu.com/equation?tex=x+y=1" alt="x+y=1" class="ee_img tr_noresize" eeimg="1"> ，而半空间就是对应超平面分割空间后其中一侧的空间。注意到这里的向量 <img src="https://www.zhihu.com/equation?tex=a" alt="a" class="ee_img tr_noresize" eeimg="1"> 其实就是对应超平面的法向量（即与超平面正交）。在了解超平面和半空间的概念后，多面体可以表示为有限数量的半空间的交集。如下图就是由 <img src="https://www.zhihu.com/equation?tex=a_i'x\ge b_i, i=1,2,3,4,5" alt="a_i'x\ge b_i, i=1,2,3,4,5" class="ee_img tr_noresize" eeimg="1"> ，五个半空间的交集形成的多面体。

<img src="https://raw.githubusercontent.com/BraveUNow/Markdown4Zhihu/master/Data/几何角度看线性规划/polyhedra.png" style="zoom:30%;" />

因此，多面体可以表示成集合 <img src="https://www.zhihu.com/equation?tex=\{x\in R^n\vert Ax\ge B\}" alt="\{x\in R^n\vert Ax\ge B\}" class="ee_img tr_noresize" eeimg="1"> ，其中 <img src="https://www.zhihu.com/equation?tex=A" alt="A" class="ee_img tr_noresize" eeimg="1"> 为 <img src="https://www.zhihu.com/equation?tex=m\times n" alt="m\times n" class="ee_img tr_noresize" eeimg="1"> 的矩阵， <img src="https://www.zhihu.com/equation?tex=b" alt="b" class="ee_img tr_noresize" eeimg="1"> 是一个 <img src="https://www.zhihu.com/equation?tex=m\times 1" alt="m\times 1" class="ee_img tr_noresize" eeimg="1"> 的向量。特殊地，一个线性规划问题的标准形 <img src="https://www.zhihu.com/equation?tex=\{x\in R^n\vert Ax= B\}" alt="\{x\in R^n\vert Ax= B\}" class="ee_img tr_noresize" eeimg="1"> 也是一个多面体。一个多面体不一定是有界的(bounded)，如二维空间内由 <img src="https://www.zhihu.com/equation?tex=(x_1\ge0,x_2\ge0)" alt="(x_1\ge0,x_2\ge0)" class="ee_img tr_noresize" eeimg="1"> 形成的多面体就是无界的。

### 凸集

凸集(convex sets)的定义可以表示成：

- 对于集合 <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> , 如果对于任何 <img src="https://www.zhihu.com/equation?tex=x,y\in S" alt="x,y\in S" class="ee_img tr_noresize" eeimg="1"> 和 <img src="https://www.zhihu.com/equation?tex=\lambda\in [0,1]" alt="\lambda\in [0,1]" class="ee_img tr_noresize" eeimg="1"> ，都有 <img src="https://www.zhihu.com/equation?tex=\lambda x+(1-\lambda)y\in S" alt="\lambda x+(1-\lambda)y\in S" class="ee_img tr_noresize" eeimg="1"> ，则称集合 <img src="https://www.zhihu.com/equation?tex=S\subset R^n" alt="S\subset R^n" class="ee_img tr_noresize" eeimg="1"> 是凸的(convex)。

 <img src="https://www.zhihu.com/equation?tex=\lambda x+(1-\lambda)y" alt="\lambda x+(1-\lambda)y" class="ee_img tr_noresize" eeimg="1"> 的范围就是 <img src="https://www.zhihu.com/equation?tex=x,y" alt="x,y" class="ee_img tr_noresize" eeimg="1"> 之间的一条线段，因此上述定义可以理解为，对于集合里面的任意两点之间的线段都在集合内部，则这个集合是凸集。下面引入两个概念：

设 <img src="https://www.zhihu.com/equation?tex=x^1,x^2,\dots, x^k" alt="x^1,x^2,\dots, x^k" class="ee_img tr_noresize" eeimg="1"> 为空间 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 的向量， <img src="https://www.zhihu.com/equation?tex=\lambda_1,\lambda_2,\dots,\lambda_k" alt="\lambda_1,\lambda_2,\dots,\lambda_k" class="ee_img tr_noresize" eeimg="1"> 为非负标量且 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^k\lambda_i=1" alt="\sum_{i=1}^k\lambda_i=1" class="ee_img tr_noresize" eeimg="1"> 

- 向量 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^k" alt="\sum_{i=1}^k" class="ee_img tr_noresize" eeimg="1"> 被称为向量 <img src="https://www.zhihu.com/equation?tex=x^1,x^2,\dots, x^k" alt="x^1,x^2,\dots, x^k" class="ee_img tr_noresize" eeimg="1"> 的一个**凸组合(convex combination)**

- 向量 <img src="https://www.zhihu.com/equation?tex=x^1,x^2,\dots, x^k" alt="x^1,x^2,\dots, x^k" class="ee_img tr_noresize" eeimg="1"> 的**凸包(convex hull)**是所有这些向量的凸组合.（如下图阴影部分即是向量 <img src="https://www.zhihu.com/equation?tex=x^1,\dots,x^7" alt="x^1,\dots,x^7" class="ee_img tr_noresize" eeimg="1"> 的凸包）

<img src="https://raw.githubusercontent.com/BraveUNow/Markdown4Zhihu/master/Data/几何角度看线性规划/convex_hull.png" style="zoom:50%;" />

基于上面的定义，下面将介绍一些关于凸性的定理。

1. **凸集之间的交集也是凸的**

**证明**: 设有I个凸集 <img src="https://www.zhihu.com/equation?tex=S_i, i\in I" alt="S_i, i\in I" class="ee_img tr_noresize" eeimg="1"> ，并假设 <img src="https://www.zhihu.com/equation?tex=x,y" alt="x,y" class="ee_img tr_noresize" eeimg="1"> 属于这些凸集的交集 <img src="https://www.zhihu.com/equation?tex=\cap_{i\in I}S_i" alt="\cap_{i\in I}S_i" class="ee_img tr_noresize" eeimg="1"> . 由于每个 <img src="https://www.zhihu.com/equation?tex=S_i" alt="S_i" class="ee_img tr_noresize" eeimg="1"> 都是凸的且都包含向量 <img src="https://www.zhihu.com/equation?tex=x,y" alt="x,y" class="ee_img tr_noresize" eeimg="1"> ，则有 <img src="https://www.zhihu.com/equation?tex=\lambda x+(1-\lambda)y\in S_i" alt="\lambda x+(1-\lambda)y\in S_i" class="ee_img tr_noresize" eeimg="1"> ，即 <img src="https://www.zhihu.com/equation?tex=x,y" alt="x,y" class="ee_img tr_noresize" eeimg="1"> 的凸组合也在所有凸集 <img src="https://www.zhihu.com/equation?tex=S_i" alt="S_i" class="ee_img tr_noresize" eeimg="1"> 的交集内。因此， <img src="https://www.zhihu.com/equation?tex=\cap_{i\in I}S_i" alt="\cap_{i\in I}S_i" class="ee_img tr_noresize" eeimg="1"> 是凸的。

2. **每个多面体都是一个凸集**

**证明**: 令 <img src="https://www.zhihu.com/equation?tex=a" alt="a" class="ee_img tr_noresize" eeimg="1"> 为一个向量,  <img src="https://www.zhihu.com/equation?tex=b" alt="b" class="ee_img tr_noresize" eeimg="1"> 为标量，假设向量 <img src="https://www.zhihu.com/equation?tex=x,y" alt="x,y" class="ee_img tr_noresize" eeimg="1"> 属于同一个半空间，即 <img src="https://www.zhihu.com/equation?tex=a'x\ge b" alt="a'x\ge b" class="ee_img tr_noresize" eeimg="1"> 和 <img src="https://www.zhihu.com/equation?tex=a'y\ge b" alt="a'y\ge b" class="ee_img tr_noresize" eeimg="1"> 。则对任意 <img src="https://www.zhihu.com/equation?tex=\lambda\in[0,1]" alt="\lambda\in[0,1]" class="ee_img tr_noresize" eeimg="1"> ， <img src="https://www.zhihu.com/equation?tex=a'(\lambda x+(1-\lambda )y)\ge\lambda b+(1-\lambda)b=b" alt="a'(\lambda x+(1-\lambda )y)\ge\lambda b+(1-\lambda)b=b" class="ee_img tr_noresize" eeimg="1"> ，表明 <img src="https://www.zhihu.com/equation?tex=\lambda x+(1-\lambda )y" alt="\lambda x+(1-\lambda )y" class="ee_img tr_noresize" eeimg="1"> 也在半空间内，因此半空间是一个凸集。而前文提到了多面体是有限个半空间的交集，根据定理1，可以得到多面体一定也是凸集。

3. **一个凸集内部有限个元素的凸组合也属于这个凸集**

**证明**: 该定理的证明可以使用数学归纳法得到。根据凸集的定义可以知道对于凸集内部任意两个元素的凸组合也在凸集内部，假设k个元素的凸组合 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^k\lambda_ix^i" alt="\sum_{i=1}^k\lambda_ix^i" class="ee_img tr_noresize" eeimg="1"> 也在凸集 <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> 内部，如果能证明k+1个元素 <img src="https://www.zhihu.com/equation?tex=x^1,\dots,x^{k+1}" alt="x^1,\dots,x^{k+1}" class="ee_img tr_noresize" eeimg="1"> 的凸组合 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^{k+1}\lambda_ix^i" alt="\sum_{i=1}^{k+1}\lambda_ix^i" class="ee_img tr_noresize" eeimg="1"> 也在凸集 <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> 内部，则定理成立。这里假设 <img src="https://www.zhihu.com/equation?tex=\lambda_{k+1}\ne1" alt="\lambda_{k+1}\ne1" class="ee_img tr_noresize" eeimg="1"> ，如果等式成立则显然该凸组合就位于 <img src="https://www.zhihu.com/equation?tex=x^{k+1}" alt="x^{k+1}" class="ee_img tr_noresize" eeimg="1"> 处。

<img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^{k+1}\lambda_ix^i=\lambda_{k+1}x^{k+1}+(1-\lambda_{x+1})\sum_{i=1}^{k}\frac{\lambda_i}{1-\lambda_{k+1}}x^i
" alt="\sum_{i=1}^{k+1}\lambda_ix^i=\lambda_{k+1}x^{k+1}+(1-\lambda_{x+1})\sum_{i=1}^{k}\frac{\lambda_i}{1-\lambda_{k+1}}x^i
" class="ee_img tr_noresize" eeimg="1">

右侧第二项的系数 <img src="https://www.zhihu.com/equation?tex=\lambda_i/(1-\lambda_{k+1})" alt="\lambda_i/(1-\lambda_{k+1})" class="ee_img tr_noresize" eeimg="1"> 是非负的且和为1，即右侧括号后的部分为前k个元素的凸组合，根据假设位于凸集 <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> 内部，则k+1个元素的凸组合可以转化为 <img src="https://www.zhihu.com/equation?tex=x^{k+1}" alt="x^{k+1}" class="ee_img tr_noresize" eeimg="1"> 和 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^{k}\frac{\lambda_i}{1-\lambda_{k+1}}x^i" alt="\sum_{i=1}^{k}\frac{\lambda_i}{1-\lambda_{k+1}}x^i" class="ee_img tr_noresize" eeimg="1"> 两个元素的凸组合，根据凸集的定义，最后可以得到 <img src="https://www.zhihu.com/equation?tex=\sum_{i=1}^{k+1}\lambda_ix^i\in S" alt="\sum_{i=1}^{k+1}\lambda_ix^i\in S" class="ee_img tr_noresize" eeimg="1"> ，证明完毕。

4. **有限个向量的凸包也是一个凸集**

**证明**: 设S是向量 <img src="https://www.zhihu.com/equation?tex=x^1,\dots,x^k" alt="x^1,\dots,x^k" class="ee_img tr_noresize" eeimg="1"> 的凸包，令 <img src="https://www.zhihu.com/equation?tex=y=\sum_{i=1}^k\varsigma_ix^i, z=\sum_{i=1}^k\theta_ix^i,\sum_{i=1}^k\varsigma_i=1,\sum_{i=1}^k\theta_i=1" alt="y=\sum_{i=1}^k\varsigma_ix^i, z=\sum_{i=1}^k\theta_ix^i,\sum_{i=1}^k\varsigma_i=1,\sum_{i=1}^k\theta_i=1" class="ee_img tr_noresize" eeimg="1"> ，根据凸包定义,   <img src="https://www.zhihu.com/equation?tex=y,z" alt="y,z" class="ee_img tr_noresize" eeimg="1"> 都属于 <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> ，则

<img src="https://www.zhihu.com/equation?tex=\lambda y+(1-\lambda)z=\lambda\sum_{i=1}^k\varsigma_ix^i+(1-\lambda)\sum_{i=1}^k\theta_ix^i=\sum_{i=1}^k(\lambda\varsigma_i+(1-\lambda)\theta_i)x_i
" alt="\lambda y+(1-\lambda)z=\lambda\sum_{i=1}^k\varsigma_ix^i+(1-\lambda)\sum_{i=1}^k\theta_ix^i=\sum_{i=1}^k(\lambda\varsigma_i+(1-\lambda)\theta_i)x_i
" class="ee_img tr_noresize" eeimg="1">
显然 <img src="https://www.zhihu.com/equation?tex=\lambda\varsigma_i+(1-\lambda)\theta_i" alt="\lambda\varsigma_i+(1-\lambda)\theta_i" class="ee_img tr_noresize" eeimg="1"> 都是非负的且和为1，因此， <img src="https://www.zhihu.com/equation?tex=\lambda y+(1-\lambda)z" alt="\lambda y+(1-\lambda)z" class="ee_img tr_noresize" eeimg="1"> 是 <img src="https://www.zhihu.com/equation?tex=x_i" alt="x_i" class="ee_img tr_noresize" eeimg="1"> 的一个凸组合，根据凸包定义一定属于 <img src="https://www.zhihu.com/equation?tex=S" alt="S" class="ee_img tr_noresize" eeimg="1"> 。因此，可以证明凸包的凸性。

## 极点、顶点和基可行解

大家学习单纯形法的过程中应该都了解过一个线性规划的最优解一定出现在可行域的顶点处。但什么是可行域的顶点，Bertsimas的书中给出了3中不同的定义方式，本节将一一介绍。

### 极点(extreme point)

多面体的极点即为无法用多面体任何其他两个元素的凸组合表示的点。它的定义如下：

- 令 <img src="https://www.zhihu.com/equation?tex=P" alt="P" class="ee_img tr_noresize" eeimg="1"> 为一个多面体, 向量 <img src="https://www.zhihu.com/equation?tex=x\in P" alt="x\in P" class="ee_img tr_noresize" eeimg="1"> 是一个极点，如果我们找不到两个向量 <img src="https://www.zhihu.com/equation?tex=y,z\in P" alt="y,z\in P" class="ee_img tr_noresize" eeimg="1"> 和标量 <img src="https://www.zhihu.com/equation?tex=\lambda" alt="\lambda" class="ee_img tr_noresize" eeimg="1"> ，可以使 <img src="https://www.zhihu.com/equation?tex=x=\lambda y+(1-\lambda)z" alt="x=\lambda y+(1-\lambda)z" class="ee_img tr_noresize" eeimg="1"> 

用通俗的话来讲，就是如果对于多面体上的一个点不在多面体内其他任何两个点连接而成的线段上，则这个点就是多面体的一个极点。

<img src="https://raw.githubusercontent.com/BraveUNow/Markdown4Zhihu/master/Data/几何角度看线性规划/extreme_point.png" style="zoom:50%;" />

上图中的x是一个极点，因为 <img src="https://www.zhihu.com/equation?tex=y\notin P" alt="y\notin P" class="ee_img tr_noresize" eeimg="1"> ，而w不是一个极点，因为它可以表示为 <img src="https://www.zhihu.com/equation?tex=v,u" alt="v,u" class="ee_img tr_noresize" eeimg="1"> 的凸组合，且 <img src="https://www.zhihu.com/equation?tex=v\in P, u\in P" alt="v\in P, u\in P" class="ee_img tr_noresize" eeimg="1"> 

### 顶点（vertex)

多面体的的顶点可以定义为关于可行域P的一些线性规划问题的唯一最优解。它的定义如下：

- 令 <img src="https://www.zhihu.com/equation?tex=P" alt="P" class="ee_img tr_noresize" eeimg="1"> 为一个多面体，向量 <img src="https://www.zhihu.com/equation?tex=x\in P" alt="x\in P" class="ee_img tr_noresize" eeimg="1"> 是P的一个顶点如果存在一些 <img src="https://www.zhihu.com/equation?tex=c" alt="c" class="ee_img tr_noresize" eeimg="1"> 可以使 <img src="https://www.zhihu.com/equation?tex=c'x\lt c'y" alt="c'x\lt c'y" class="ee_img tr_noresize" eeimg="1"> ，其中 <img src="https://www.zhihu.com/equation?tex=y\in P, y\ne x" alt="y\in P, y\ne x" class="ee_img tr_noresize" eeimg="1"> 

上述定义通俗理解就是对于点 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> ，如果存在一条经过它的一条超平面可以令 <img src="https://www.zhihu.com/equation?tex=P" alt="P" class="ee_img tr_noresize" eeimg="1"> 中所有点都在超平面的同一侧，且只有点 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 在超平面上，则 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 就是多面体的一个顶点。

### 基可行解(basic feasible solution)

根据多面体的定义，一个多面体 <img src="https://www.zhihu.com/equation?tex=P\subset R^n" alt="P\subset R^n" class="ee_img tr_noresize" eeimg="1"> 可以用一系列线性等式和不等式约束表示：

<img src="https://www.zhihu.com/equation?tex=a_i'x\ge b_i\quad i\in M_1\\
a_i'x\le b_i\quad i\in M_2\\
a_i'x= b_i\quad i\in M_3
" alt="a_i'x\ge b_i\quad i\in M_1\\
a_i'x\le b_i\quad i\in M_2\\
a_i'x= b_i\quad i\in M_3
" class="ee_img tr_noresize" eeimg="1">
每个 <img src="https://www.zhihu.com/equation?tex=a_i" alt="a_i" class="ee_img tr_noresize" eeimg="1"> 是 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 中的一个向量,  <img src="https://www.zhihu.com/equation?tex=b_i" alt="b_i" class="ee_img tr_noresize" eeimg="1"> 是一个标量。如果对于向量 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> ，存在某些 <img src="https://www.zhihu.com/equation?tex=i\in M_1,M_2,M_3" alt="i\in M_1,M_2,M_3" class="ee_img tr_noresize" eeimg="1"> 满足 <img src="https://www.zhihu.com/equation?tex=a_i'x^*=b_i," alt="a_i'x^*=b_i," class="ee_img tr_noresize" eeimg="1"> ，则称对应的约束 <img src="https://www.zhihu.com/equation?tex=i" alt="i" class="ee_img tr_noresize" eeimg="1"> 为在 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 上的有效约束(active/binding constraints)，否则称为无效约束，显然 <img src="https://www.zhihu.com/equation?tex=M_3" alt="M_3" class="ee_img tr_noresize" eeimg="1"> 中的约束都是有效约束。根据线性代数的基础知识，如果一个线性规划问题由n个有效约束，且这n个约束是线性无关(linearly independent)的，则这个问题只有唯一解。

令 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 为 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 中的一个点， <img src="https://www.zhihu.com/equation?tex=I=\{i\vert a_i'x^*=b_i\}" alt="I=\{i\vert a_i'x^*=b_i\}" class="ee_img tr_noresize" eeimg="1"> 是在 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 上的有效约束的索引，则下面三种表达是等价的：

1. 集合 <img src="https://www.zhihu.com/equation?tex=\{a_i\vert i\in I\}" alt="\{a_i\vert i\in I\}" class="ee_img tr_noresize" eeimg="1"> 内存在n个线性无关的向量

2. 向量 <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 张成的向量空间(span)是 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> ，即 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 内任意元素都可以表示为 <img src="https://www.zhihu.com/equation?tex=a_i" alt="a_i" class="ee_img tr_noresize" eeimg="1"> 的线性组合

3. 线性方程组 <img src="https://www.zhihu.com/equation?tex=a_i'x=b_i,i\in I" alt="a_i'x=b_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 有唯一解

**证明：**

**表达1和表达2**：如果向量 <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 的span是 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> ，则由线性代数的知识可得这些向量中有n个向量构成了 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 的一个基，这n个向量一定是线性无关的。同样，如果集合 <img src="https://www.zhihu.com/equation?tex=\{a_i\vert i\in I\}" alt="\{a_i\vert i\in I\}" class="ee_img tr_noresize" eeimg="1"> 内存在n个线性无关的向量，则这n个向量作为基张成的向量空间一定等于 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> ，即 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 中的任何元素都可以表示为这n个向量的线性组合。

**表达2和表达3**：如果线性方程组 <img src="https://www.zhihu.com/equation?tex=a_i'x=b_i,i\in I" alt="a_i'x=b_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 有多个解，如 <img src="https://www.zhihu.com/equation?tex=x^1,x^2" alt="x^1,x^2" class="ee_img tr_noresize" eeimg="1"> ，令非零向量 <img src="https://www.zhihu.com/equation?tex=d=x^1-x^2" alt="d=x^1-x^2" class="ee_img tr_noresize" eeimg="1"> , 则 <img src="https://www.zhihu.com/equation?tex=a_i'd=a_i'(x^1-x^2)=0" alt="a_i'd=a_i'(x^1-x^2)=0" class="ee_img tr_noresize" eeimg="1"> ，即 <img src="https://www.zhihu.com/equation?tex=d" alt="d" class="ee_img tr_noresize" eeimg="1"> 与所有 <img src="https://www.zhihu.com/equation?tex=a_i" alt="a_i" class="ee_img tr_noresize" eeimg="1"> 正交，因此无法用 <img src="https://www.zhihu.com/equation?tex=a_i" alt="a_i" class="ee_img tr_noresize" eeimg="1"> 的线性组合表示，从而不在span( <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> )内，说明span( <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> )不包括整个 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> (至少不包括 <img src="https://www.zhihu.com/equation?tex=d" alt="d" class="ee_img tr_noresize" eeimg="1"> )。同样，如果span( <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> )的不等于 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> ，存在一个非零向量 <img src="https://www.zhihu.com/equation?tex=d" alt="d" class="ee_img tr_noresize" eeimg="1"> 与span( <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> )正交，如果存在 <img src="https://www.zhihu.com/equation?tex=x" alt="x" class="ee_img tr_noresize" eeimg="1"> 满足 <img src="https://www.zhihu.com/equation?tex=a_i'x=b_i,i\in I" alt="a_i'x=b_i,i\in I" class="ee_img tr_noresize" eeimg="1"> ，则 <img src="https://www.zhihu.com/equation?tex=a_i'(x+d)=b_i,i\in I" alt="a_i'(x+d)=b_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 也一定满足，因此该线性方程组有多个解。

因此，如果对于一个有n个变量的线性规划问题，如果我们能找到n个有效约束则能唯一确定一个解。因此，这里引出了基解(basic solution)和基可行解的概念(basic feasible solution)。对于一个由一系列等式约束和不等式约束定义的多面体 <img src="https://www.zhihu.com/equation?tex=P" alt="P" class="ee_img tr_noresize" eeimg="1"> , 令 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 为 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 中的一个向量。

- 所有在 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 的有效约束中有 <img src="https://www.zhihu.com/equation?tex=n" alt="n" class="ee_img tr_noresize" eeimg="1"> 个约束是线性无关的，则求解线性方程组得到的 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 是一个**基解**.
- 如果 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 是一个基解，且满足所有的约束，则是一个基可行解。

对于一个线性规划问题，假设有n个变量，m个约束，其中有k个线性无关的等式约束，我们可以中所有不等式约束中寻找(n-k)个约束令其满足等式约束，这样就可以得到n个有效约束。

<img src="https://raw.githubusercontent.com/BraveUNow/Markdown4Zhihu/master/Data/几何角度看线性规划/basic_solution.png" style="zoom:15%;" />

假设线性规划问题的约束包括 <img src="https://www.zhihu.com/equation?tex=c_1:x+y\le 2;c_2:x-y\ge-1;c_3:x\ge0;c_4:y\ge0" alt="c_1:x+y\le 2;c_2:x-y\ge-1;c_3:x\ge0;c_4:y\ge0" class="ee_img tr_noresize" eeimg="1"> ，可行域如上图阴影部分区域所示，显然图中所有点都是都是基解，因为他们至少满足了两条线性无关的有效约束，如点E存在有效约束 <img src="https://www.zhihu.com/equation?tex=c_2,c_4" alt="c_2,c_4" class="ee_img tr_noresize" eeimg="1"> 。但只有C、D、E、F是基可行解。

### extreme point, vertex, basic feasible solution

以上三种概念虽然表达方式不同，但其实是等价的，并可以互换使用。本节将进行等价性的证明。

**vertex <img src="https://www.zhihu.com/equation?tex=\rightarrow" alt="\rightarrow" class="ee_img tr_noresize" eeimg="1"> extreme point**：设 <img src="https://www.zhihu.com/equation?tex=x^*\in P" alt="x^*\in P" class="ee_img tr_noresize" eeimg="1"> 是一个顶点，则存在向量 <img src="https://www.zhihu.com/equation?tex=c" alt="c" class="ee_img tr_noresize" eeimg="1"> 满足 <img src="https://www.zhihu.com/equation?tex=c'x^*\lt c'y,y\in P,y\ne x^*" alt="c'x^*\lt c'y,y\in P,y\ne x^*" class="ee_img tr_noresize" eeimg="1"> 。设有 <img src="https://www.zhihu.com/equation?tex=y\in P,y\ne x^*,z\in P,z\ne x^*" alt="y\in P,y\ne x^*,z\in P,z\ne x^*" class="ee_img tr_noresize" eeimg="1"> ，则 <img src="https://www.zhihu.com/equation?tex=c'y\gt c'x^*,c'z\gt c'x^*" alt="c'y\gt c'x^*,c'z\gt c'x^*" class="ee_img tr_noresize" eeimg="1"> ， <img src="https://www.zhihu.com/equation?tex=c'(\lambda y+(1-\lambda)z)\gt c'x^*" alt="c'(\lambda y+(1-\lambda)z)\gt c'x^*" class="ee_img tr_noresize" eeimg="1"> ，所以 <img src="https://www.zhihu.com/equation?tex=(\lambda y+(1-\lambda)z)\ne x^*" alt="(\lambda y+(1-\lambda)z)\ne x^*" class="ee_img tr_noresize" eeimg="1"> 因此 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 无法表示为P中任意两个元素的凸组合, 是一个极点。

**extreme point <img src="https://www.zhihu.com/equation?tex=\rightarrow" alt="\rightarrow" class="ee_img tr_noresize" eeimg="1">  basic feasible solution**：只要证明如果 <img src="https://www.zhihu.com/equation?tex=x^*\in P" alt="x^*\in P" class="ee_img tr_noresize" eeimg="1"> 不是一个基可行解，那一定不是极点即可。不是基可行解有两种情况。令 <img src="https://www.zhihu.com/equation?tex=I=\{a_i\vert a_ix^*=b_i\}" alt="I=\{a_i\vert a_ix^*=b_i\}" class="ee_img tr_noresize" eeimg="1"> 表示有效约束的集合，如果不存在n个线性无关的约束，则span( <img src="https://www.zhihu.com/equation?tex=a_i,i\in I" alt="a_i,i\in I" class="ee_img tr_noresize" eeimg="1"> )是 <img src="https://www.zhihu.com/equation?tex=R^n" alt="R^n" class="ee_img tr_noresize" eeimg="1"> 的一个子集，一定存在 <img src="https://www.zhihu.com/equation?tex=d\in R^n" alt="d\in R^n" class="ee_img tr_noresize" eeimg="1"> 正交于所有约束向量令 <img src="https://www.zhihu.com/equation?tex=a_id=0,i\in I" alt="a_id=0,i\in I" class="ee_img tr_noresize" eeimg="1"> 。令 <img src="https://www.zhihu.com/equation?tex=\epsilon" alt="\epsilon" class="ee_img tr_noresize" eeimg="1"> 是 一个很小的正数，并令 <img src="https://www.zhihu.com/equation?tex=y=x^*+\epsilon d,z=x^*-\epsilon d" alt="y=x^*+\epsilon d,z=x^*-\epsilon d" class="ee_img tr_noresize" eeimg="1"> ，则对于所有有效约束 <img src="https://www.zhihu.com/equation?tex=i\in I" alt="i\in I" class="ee_img tr_noresize" eeimg="1"> 有 <img src="https://www.zhihu.com/equation?tex=a_i'y=a_i'z=0" alt="a_i'y=a_i'z=0" class="ee_img tr_noresize" eeimg="1"> ，而对于无效约束 <img src="https://www.zhihu.com/equation?tex=i\notin I" alt="i\notin I" class="ee_img tr_noresize" eeimg="1"> ，由于 <img src="https://www.zhihu.com/equation?tex=a_i'x^*\gt b_i" alt="a_i'x^*\gt b_i" class="ee_img tr_noresize" eeimg="1"> ，由于 <img src="https://www.zhihu.com/equation?tex=\epsilon" alt="\epsilon" class="ee_img tr_noresize" eeimg="1"> 很小( <img src="https://www.zhihu.com/equation?tex=\epsilon\vert a_i'd\vert\lt a_i'x^*-b_i" alt="\epsilon\vert a_i'd\vert\lt a_i'x^*-b_i" class="ee_img tr_noresize" eeimg="1"> )，则 <img src="https://www.zhihu.com/equation?tex=a_i'y\gt b_i,a_i'z\gt b_i" alt="a_i'y\gt b_i,a_i'z\gt b_i" class="ee_img tr_noresize" eeimg="1"> ，因此 <img src="https://www.zhihu.com/equation?tex=y,z" alt="y,z" class="ee_img tr_noresize" eeimg="1"> 都满足所有约束，使 <img src="https://www.zhihu.com/equation?tex=y\in P, z\in P" alt="y\in P, z\in P" class="ee_img tr_noresize" eeimg="1"> ，则 <img src="https://www.zhihu.com/equation?tex=x^*=(y+z)/2" alt="x^*=(y+z)/2" class="ee_img tr_noresize" eeimg="1"> ，可以表示为两个向量的凸组合；另一种情况是存在n个线性无关的有效约束，但 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 违背了部分无效约束，即 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 为basic solution, 不是basic feasible solution，则 <img src="https://www.zhihu.com/equation?tex=x^*\notin P" alt="x^*\notin P" class="ee_img tr_noresize" eeimg="1"> ，自然不是极点了。

**basic feasible solution <img src="https://www.zhihu.com/equation?tex=\rightarrow" alt="\rightarrow" class="ee_img tr_noresize" eeimg="1">  vertex**：如上令 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 为一个basic feasible solution， <img src="https://www.zhihu.com/equation?tex=I=\{a_i\vert a_ix^*=b_i\}" alt="I=\{a_i\vert a_ix^*=b_i\}" class="ee_img tr_noresize" eeimg="1"> 表示有效约束的集合，令 <img src="https://www.zhihu.com/equation?tex=c=\sum_{i\in I}a_i" alt="c=\sum_{i\in I}a_i" class="ee_img tr_noresize" eeimg="1"> ,则有:

<img src="https://www.zhihu.com/equation?tex=c'x^*=\sum_{i\in I}a_i'x^*=\sum_{i\in I}b^i
" alt="c'x^*=\sum_{i\in I}a_i'x^*=\sum_{i\in I}b^i
" class="ee_img tr_noresize" eeimg="1">
此外，对于任何 <img src="https://www.zhihu.com/equation?tex=x\in P" alt="x\in P" class="ee_img tr_noresize" eeimg="1"> ，都满足所有约束 <img src="https://www.zhihu.com/equation?tex=a_i'x\ge b_i" alt="a_i'x\ge b_i" class="ee_img tr_noresize" eeimg="1"> ，则

<img src="https://www.zhihu.com/equation?tex=c'x=\sum_{i\in I}a_i'x\ge \sum_{i\in I}b_i
" alt="c'x=\sum_{i\in I}a_i'x\ge \sum_{i\in I}b_i
" class="ee_img tr_noresize" eeimg="1">
将 <img src="https://www.zhihu.com/equation?tex=c'x" alt="c'x" class="ee_img tr_noresize" eeimg="1"> 当作一个目标函数，则 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 是这个问题的下界，由于 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 是一个基可行解，因此在 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 处存在n个线性无关的有效约束，根据前面的证明这是与由这n个有效约束组成的线性方程组 <img src="https://www.zhihu.com/equation?tex=a_i'x=b_i,i\in I" alt="a_i'x=b_i,i\in I" class="ee_img tr_noresize" eeimg="1"> 有唯一解是等价的，因此 <img src="https://www.zhihu.com/equation?tex=c'x" alt="c'x" class="ee_img tr_noresize" eeimg="1"> 只有在  <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 才能使等式成立，对于所有 <img src="https://www.zhihu.com/equation?tex=x\in P,x\ne x^*" alt="x\in P,x\ne x^*" class="ee_img tr_noresize" eeimg="1"> ，都有 <img src="https://www.zhihu.com/equation?tex=c'x\gt c'x^*" alt="c'x\gt c'x^*" class="ee_img tr_noresize" eeimg="1"> ，因此 <img src="https://www.zhihu.com/equation?tex=x^*" alt="x^*" class="ee_img tr_noresize" eeimg="1"> 是一个vertex。

因此，如果一个向量是多面体的extreme point, 那它一定也是多面体的vertex或线性规划问题的一个basic feasible solution.

如果给定有限数量的线性不等式约束，则只有有限个数量的basic solution或basic feasible solution，也就是说一个多面体的extreme point或vertex的数量是有限的（但这个数字可能会很大）。

**证明**：假设线性规划问题有m个不等式约束，由于任何basic solution都可以由n个线性无关的约束组成的线性方程组唯一确定，因此只需要在m个约束中找到n个线性无关的约束令等式成立就能获得一个basic solution，则basic solution的数量实际上是受限于m个不等式约束中能找到的n个线性无关约束的数量。



本章的内容先写到这里（肝了大半天写不动了:tired_face:），写着写着发现自己好像基本就是在翻译书本:sweat:（但有些部分还是加了点个人理解，虽然不一定正确，作为本科生懂得真的不多），如果大家对此感兴趣还是欢迎大家去阅读原书。由于最近有好多事要做，之后的更新就随缘了。。。
