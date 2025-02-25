---
publish: true
tags: []
aliases: 
finished: true
title: 题b
created: "2024-12-06 04:16"
updated: "2024-12-21 10:10"
---
## 题b
### 题目
900 题数二第六章A类14
14 二次型 $f(x_1, x_2, x_3) = x_1^2 + 3x_2^2 + 5x_3^2 + 4x_1x_2 + 6x_1x_3 + 8x_2x_3$ 的秩为
### 分析
直接展开算系数矩阵就是[[二次型]]的秩
### 解

答案 2.

解 由题设可知，$f(x_1,x_2,x_3)$对应的对称矩阵$A = \begin{pmatrix} 1 & 2 & 3 \\ 2 & 3 & 4 \\ 3 & 4 & 5 \end{pmatrix}$。由于二次型的秩即其对应的对称矩阵的秩，故只需求 $r(A)$ 即可。
下面用两种方法计算 $r(A)$。

解法 1 由于 $A$ 有 2 阶非零子式 $\begin{vmatrix} 1 & 2 \\ 2 & 3 \end{vmatrix} = -1$，故 $r(A) \ge 2$。另一方面，
$$ \begin{vmatrix} 1 & 2 & 3 \\ 2 & 3 & 4 \\ 3 & 4 & 5 \end{vmatrix} = 1(15-16) - 2(10-12) + 3(8-9) = -1 + 4 - 3 = 0. $$
于是 $r(A) \le 2$。因此 $r(A) = 2$，即二次型 $f$ 的秩为 2。

解法 2 利用初等行变换。
$$ A = \begin{pmatrix} 1 & 2 & 3 \\ 2 & 3 & 4 \\ 3 & 4 & 5 \end{pmatrix} \to \begin{pmatrix} 1 & 2 & 3 \\ 0 & -1 & -2 \\ 0 & -2 & -4 \end{pmatrix} \to \begin{pmatrix} 1 & 2 & 3 \\ 0 & 1 & 2 \\ 0 & 0 & 0 \end{pmatrix}. $$
由 $A$ 的行阶梯形可知 $r(A) = 2$。
