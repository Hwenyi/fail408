---
publish: true
tags: []
aliases: 
finished: true
title: 题c
created: "2024-12-06 04:16"
updated: "2024-12-21 10:11"
---
## 题c
### 题目
900 题数二第六章 A 类 1
设$\alpha, \beta$均为3维列向量，二次型$f = x^T \alpha \beta^T x$，则下列关于$f$的秩的说法中，正确的个数为( )
① 可能为 0. 
② 可能为 1. 
③ 可能为 2. 
④ 可能为 3.
(A) 1. (B) 2. (C) 3. (D) 4.
### 分析
直接通过系数矩阵算[[二次型]]的秩，我们首先保证这是[[大学数学/线代张宇/第五讲特征值与特征向量/实对称矩阵|实对称矩阵]]的，通过加[[转置矩阵]]然后除以二得到
### 解

答案 C.

解 令矩阵$A = \frac{1}{2}(\alpha\beta^T + \beta\alpha^T)$，则

$$A^T = \frac{1}{2}(\alpha\beta^T + \beta\alpha^T)^T = \frac{1}{2}(\alpha\beta^T + \beta\alpha^T) = A.$$

于是，$A$为[[对称矩阵]]，并且可以验证$x^TAx = x^T\alpha\beta^Tx$，因此$A$为二次型$f$对应的对称矩阵，$f$的秩即$r(A)$.

取$\alpha = 0$，则$A = O, r(A) = 0$. ①正确.

取$\alpha = \beta = (1, 0, 0)^T$，则$A = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}, r(A) = 1$. ②正确

取$\alpha = (1, 0, 0)^T, \beta = (0, 1, 0)^T$，则$A = \begin{pmatrix} 0 & \frac{1}{2} & 0 \\ \frac{1}{2} & 0 & 0 \\ 0 & 0 & 0 \end{pmatrix}, r(A) = 2$. ③正确

由于

$$r(A) = r(\alpha\beta^T + \beta\alpha^T) \le r(\alpha\beta^T) + r(\beta\alpha^T) \le 1 + 1 = 2,$$

故$r(A)$不可能为 3. ④不正确

综上所述，应选 C.

注

若非零列向量$\alpha, \beta$线性相关，即存在非零常数$k$，使得$\beta = k\alpha$，则$A = k\alpha\alpha^T, r(A) \le r(\alpha) = 1$. 结合$A \ne O$可知，$r(A) = 1$.
若$\alpha, \beta$线性无关，则可证明$A = \frac{1}{2}(\alpha\beta^T + \beta\alpha^T)$存在 2 阶非零子式，从而$r(A) \ge 2$. 结合$r(A) \le 2$可得 $r(A) = 2$.
