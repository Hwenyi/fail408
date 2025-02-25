---
publish: true
tags: []
aliases: 
finished: true
title: 题d
created: "2024-12-06 04:16"
updated: "2024-12-21 10:18"
---
## 题d
### 题目

900 题数二第六章 A 类 15

15 设二次型 $f(x_1, x_2, x_3) = (x_1 + x_2)^2 + (x_1 + x_3)^2 + (x_2 + ax_3)^2$，当 $a = ()$ 时，$f$ 的秩最小.

### 分析
还是直接展开，得到[[系数矩阵]]然后算[[二次型]]的秩
### 解

答案 -1.

解：由于
$f(x_1, x_2, x_3) = 2x_1^2 + 2x_2^2 + (a^2 + 1)x_3^2 + 2x_1x_2 + 2x_1x_3 + 2ax_2x_3$，
故$f$对应的对称矩阵为$\boldsymbol{A} = \begin{pmatrix} 2 & 1 & 1 \\ 1 & 2 & a \\ 1 & a & a^2 + 1 \end{pmatrix}$。又因为$\boldsymbol{A}$有2阶非零子式$\begin{vmatrix} 2 & 1 \\ 1 & 2 \end{vmatrix} = 3$，所以$r(\boldsymbol{A}) \ge 2$。

下面考察$\boldsymbol{A}$的秩是否可以等于2.
$$
\begin{aligned}
|\boldsymbol{A}| &= \begin{vmatrix} 2 & 1 & 1 \\ 1 & 2 & a \\ 1 & a & a^2 + 1 \end{vmatrix} \\
&= 2(2(a^2+1) - a^2) - (a^2+1 - a) + (a - 2) \\
&= 2(a^2 + 2 - a^2) - a^2 - 1 + a + a - 2 \\
&= 4 - a^2 + 2a - 3 \\
&= -(a^2 - 2a + 1) \\
&= -(a-1)^2
\end{aligned}
$$
当$a = 1$时，$|\boldsymbol{A}| = 0$，$r(\boldsymbol{A}) = 2$。因此，当$a = 1$时，$r(\boldsymbol{A})$最小，即当$a = 1$时，$f$的秩最小.
