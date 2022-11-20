---
title: 多重网格方法中光滑器的并行：多项式迭代方法和Gauss-Seidel 迭代方法的比较
author: 马鹏飞
category: translation
paper: Parallel multigrid smoothing: polynomial versus Gauss–Seidel
layout: post
mathjax: yes
status: waiting
tags: 多重网格光滑器, 论文笔记
date: 2022-10-17 16:35
doi: 10.1016/S0021-9991(03)00194-3
---

作者：马鹏飞
2022年6月3日



#### [[多项式光滑器(Polynomial smoothers)]]
迭代格式为
$$
x^{(m+1)}=x^{(m)}+p(A)\left(b-A x^{(m)}\right)
$$

其中，$p(A)$为[[矩阵多项式]]，可以表示成
$$
p(A)=\sum_{0 \leqslant j \leqslant n} \alpha_j A^j
$$
[[误差传递]]公式为
$$
e^{(m+1)}=q(A) e^{(m)}
$$
其中
$$
q(A)=I-p(A) A, \quad e^{(m)}=x^{(m)}-x^*
$$

[[Chebyshev多项式|Chebyshev多项式(Chebyshev polynomials)]]

考虑A的特征值和特征向量
$$
\left(\lambda_1, x_1\right),\left(\lambda_2, x_2\right), \ldots,\left(\lambda_n, x_n\right)
$$
其中
$$
\lambda_1 \leqslant \lambda_2 \leqslant \cdots \leqslant \lambda_n .
$$
选取一个中间值$\lambda^*$，$\lambda_1<\lambda^*<\lambda_n$，特征值被分为两组，大特征值对应高频能量，小特征值对应低频能量。假设粗网格校正$C_\text{mg}(A)$能够完全消除低频误差，但是不影响高频误差，那么有
$$
C_{m g}(A) x_k= \begin{cases}0 & \text { if } \lambda_k<\lambda^* \\ x_k & \text { if } \lambda_k \geqslant \lambda^*\end{cases}
$$
理想的多重网格光滑器要求多项式$q(z)$在$\lambda^* \leqslant z \leqslant \lambda_n$上的值比较小，且满足$q(0)=1$。

如果我们希望多项式$q(z)$在这个区间内的最大振幅尽可能小，那么Chebyshev多项式是最优选择，只要知道$\lambda^*$和$\lambda_n$的值就能确定$q(z)$。

最后得到的[[Chebyshev迭代方法]]有点像[[Chebyshev半迭代方法]]加速的[[Jacobi迭代方法]]。Chebyshev迭代方法用来消除高频误差，高频误差消除为原来的$\mu_k$，其中
$$
\begin{aligned}
\mu_0 &=1 \\
\mu_1 &=\frac{\lambda_n-\lambda^*}{\lambda_n+\lambda^*} \\
\mu_k &=\frac{\mu_1 \mu_{k-1} \mu_{k-2}}{2 \mu_{k-2}-\mu_{k-1} \mu_1} \quad k \geqslant 2 .
\end{aligned}
$$
如果理想的粗网格校正非常接近真实的粗网格校正，那么$\mu_k$接近真实的多重网格收敛速率。

## 特征值估计
[Chebyshev迭代方法](Chebyshev迭代方法)的主要缺点是需要知道矩阵$A$的最大最小特征值。如果我们使用[Chebyshev半迭代方法](Chebyshev半迭代方法)作为一个单独的求解器使用，那么需要最小特征值，最小特征值通常很难得到。如果[Chebyshev半迭代方法](Chebyshev半迭代方法)作为一个[多重网格光滑器](../有限元方法/多重网格光滑器.md)使用，那么我们只需知道最大特征值。最大特征值除以一个常数（比如30），作为最小特征值的估计。这个常数和多重网格方法中网格粗化速度相关。据我们观察，多重网格方法的收敛速率对这个常数不是非常敏感，后文中进行了讨论。

最大特征值的估计相对容易计算，例如A是[M矩阵](M%E7%9F%A9%E9%98%B5.md)，那么A的最大特征值可以通过[[盖尔圆盘定理|盖尔圆盘定理(Gershgorin theorem)]]估计，而且估计相对准确。如果A不是M矩阵，那么它的最大特征值可以通过几次[[Lanczos迭代方法]]或[[共轭梯度迭代方法]]求解得到，通常有现成的程序。本文中的最大特征值是通过Smoothed aggregation获得的。[Chebyshev迭代方法](Chebyshev迭代方法)对特征值低估很敏感，但是对于高估不是很敏感。而大部分算法（例如[Lanczos迭代方法](Lanczos迭代方法.md)）估计出来的特征值比真实的最大特征值小，因此建议给估计出来的最大特征值乘上一个小系数。
>[!problem] Smoothed aggregation 是什么意思？

>[!problem] Lanczos迭代方法为什么能够估计特征值？





