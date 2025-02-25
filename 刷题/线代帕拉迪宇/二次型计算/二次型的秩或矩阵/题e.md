---
publish: true
tags: []
aliases: 
finished: true
title: 题e
created: "2024-12-06 04:16"
updated: "2024-12-21 10:23"
---
## 题e
### 题目
900 题数二第六章 B 类 1
设二次型 $f(x_1, x_2, x_3) = \sum_{i=1}^3 (x_i - \bar{x})^2$，其中 $\bar{x} = \frac{x_1 + x_2 + x_3}{3}$，记其对应的矩阵为 $\mathbf{A}$，则( )
(A) $r(\mathbf{A}) + r(\mathbf{E} - \mathbf{A}) = 4$.  
(B) $r(\mathbf{A}) + r(\mathbf{E} + \mathbf{A}) = 4$.
(C) $r(\mathbf{A}) + r(\mathbf{E} - \mathbf{A}) = 5$.  
(D) $r(\mathbf{A}) + r(\mathbf{E} + \mathbf{A}) = 5$.
### 分析

二次型的形式再复杂也要冷静，把它展开就好了。这种写法不是很常见，用求和符号，但是我们只要展开算就好了。然后算这个二次的秩，因为要算这个[[系数矩阵]]的秩。惯用的技巧是算它的非零[[余子式]]，只要找到一个非零子式就能确定它的秩至少大于等于几。

### 解

答案 D.

解：整理 $f(x_1, x_2, x_3)$.

$$f(x_1, x_2, x_3) = \sum_{i=1}^3 (x_i^2 + \bar{x}^2 - 2x_i\bar{x}) = \sum_{i=1}^3 x_i^2 + 3\bar{x}^2 - 2\bar{x}\sum_{i=1}^3 x_i$$

其中 $\bar{x} = \frac{x_1 + x_2 + x_3}{3}$. 则

$$\begin{aligned}
&= \sum_{i=1}^3 x_i^2 - 3\bar{x}^2 = \sum_{i=1}^3 x_i^2 - \frac{(x_1 + x_2 + x_3)^2}{3} \\
&= x_1^2 + x_2^2 + x_3^2 - \frac{1}{3}(x_1^2 + x_2^2 + x_3^2 + 2x_1x_2 + 2x_1x_3 + 2x_2x_3).
\end{aligned}$$

根据二次型对应矩阵的定义，$A = \begin{pmatrix} \frac{2}{3} & -\frac{1}{3} & -\frac{1}{3} \\ -\frac{1}{3} & \frac{2}{3} & -\frac{1}{3} \\ -\frac{1}{3} & -\frac{1}{3} & \frac{2}{3} \end{pmatrix}$. 由于 $A$ 的各行元素之和均为 0，故 $|A| = 0$, $r(A) \le 2$. 又因为 $A$ 有 2 阶非零子式，所以 $r(A) \ge 2$. 结合 $r(A) \le 2$ 可得 $r(A) = 2$.

$E - A$ 是元素全为 $\frac{1}{3}$ 的矩阵，故 $r(E - A) = 1$. 另一方面

$$\begin{aligned}
|E + A| &= \begin{vmatrix} \frac{5}{3} & -\frac{1}{3} & -\frac{1}{3} \\ -\frac{1}{3} & \frac{5}{3} & -\frac{1}{3} \\ -\frac{1}{3} & -\frac{1}{3} & \frac{5}{3} \end{vmatrix} = \begin{vmatrix} 1 & -\frac{1}{3} & -\frac{1}{3} \\ 1 & \frac{5}{3} & -\frac{1}{3} \\ 1 & -\frac{1}{3} & \frac{5}{3} \end{vmatrix} = \begin{vmatrix} 1 & 0 & 0 \\ 1 & 2 & 0 \\ 1 & 0 & 2 \end{vmatrix} = 4 \ne 0. \\
&\text{所以 } r(E + A) = 3
\end{aligned}$$

因此，$r(A) + r(E - A) = 3$, $r(A) + r(E + A) = 5$. 应选 D.

注：也可以从特征值的角度来计算 $r(A)$, $r(E - A)$, $r(E + A)$.
注意到 $A = E - \frac{1}{3}\begin{pmatrix} 1 \\ 1 \\ 1 \end{pmatrix}(1, 1, 1)$, 而 $\frac{1}{3}\begin{pmatrix} 1 \\ 1 \\ 1 \end{pmatrix}(1, 1, 1)$ 为秩 1 的实对称矩阵，故 0 为二重特征值，其非零特征值为它的迹，等于 1. 于是，$A$ 的特征值为 0, 2/3, 2/3. 因此，$r(A) = 2$.
根据特征值的性质，$E - A$ 的特征值为 1, 1/3, 1/3, $r(E - A) = 1$. 同理可得 $E + A$ 的特征值为 2, 4/3, 4/3, $r(E + A) = 3$.

