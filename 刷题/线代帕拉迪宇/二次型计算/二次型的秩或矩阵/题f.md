---
publish: true
tags: []
aliases: 
finished: true
title: 题f
created: "2024-12-06 04:16"
updated: "2024-12-21 10:26"
---
## 题f
### 题目
25 李永乐六套数一二三第五套
16. 设矩阵$A = \begin{pmatrix} 1 & 1 & 0 & 2 \\ 0 & 2 & 2 & a \\ 1 & 3 & a & a^2 \end{pmatrix}$，若二次型$f(x_1, x_2, x_3) = x^T(AA^T)x$的秩为2，则$a =$

### 分析

根据题目给的$a^{T}a$，我们用到了[[格拉姆矩阵]]的秩来计算[[二次型]][[系数矩阵]]的秩，

### 解
[答案] 2

[分析] 由于 $AA^T$ 为对称矩阵，所以二次型 $f(x_1, x_2, x_3)$ 的矩阵为 $AA^T$，于是二次型 $f(x_1, x_2, x_3)$ 的秩为其对应的矩阵 $AA^T$ 的秩，所以 $r(AA^T) = 2$. 又 $r(AA^T) = r(A)$，故 $r(A) = 2$. 对矩阵 $A$ 作初等行变换

$$
\mathbf{A} = \begin{bmatrix} 1 & 1 & 0 & 2 \\ 0 & 2 & 2 & a \\ 1 & 3 & a & a^2 \end{bmatrix} \to \begin{bmatrix} 1 & 1 & 0 & 2 \\ 0 & 2 & 2 & a \\ 0 & 2 & a & a^2 - 2 \end{bmatrix} \to \begin{bmatrix} 1 & 1 & 0 & 2 \\ 0 & 2 & 2 & a \\ 0 & 0 & a - 2 & (a - 2)(a + 1) \end{bmatrix}.
$$

由 $r(A) = 2$，得 $a = 2$.

[评注] 对于 $m \times n$ 矩阵 $A$，恒有 $r(AA^T) = r(A^T)$，考试时可以直接使用. 在此给出证明：考虑方程组 $AA^Tx = 0$ 与 $A^Tx = 0$，这两个方程未知量的个数均为 $m$，我们只要证明这两个方程组同解，就有 $m - r(AA^T) = m - r(A^T)$，于是 $r(AA^T) = r(A^T)$.

若向量 $\alpha$ 是方程组 $A^Tx = 0$ 的解，则 $A^T\alpha = 0$，在等式两边左乘矩阵 $A$ 得 $AA^T\alpha = 0$，于是 $\alpha$ 是方程组 $AA^Tx = 0$ 的解；另一方面，若向量 $\alpha$ 是方程组 $AA^Tx = 0$ 的解，则 $AA^T\alpha = 0$，在等式两边左乘 $\alpha^T$ 得 $\alpha^TAA^T\alpha = 0$，即 $(A^T\alpha)^T(A^T\alpha) = 0$，从而 $A^T\alpha = 0$，于是 $\alpha$ 是方程组 $A^Tx = 0$ 的解.
