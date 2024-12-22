---
finished: true
aliases: 
tags: []
publish: true
url: https://www.cnblogs.com/onsummer/p/7596109.html
title: 根号下x方+a方的积分∫√(x²+a²)dx
created: "2024-03-03 01:30"
updated: "2024-10-24 03:05"
TARGET DECK: 大学数学::高数武忠祥::一元积分学-第四章::根号下x方+a方的积分∫√(x²+a²)dx
---
快速算的核心是给根式做有理化

$$\int\sqrt{x^2+2}dx$$

这个可以直接用基本积分公式的。

但是就其结果的推导过程，一般是用三角换元法。

以

$$\int\sqrt{x^2+a^2}dx$$

为例，计算一下在三角换元方法下的不定积分：

令 $x=a \tan t$，则 $dx=ad(\tan t)=a \sec^2 t dt$。
$$\begin{aligned}
\int\sqrt{x^{2}+a^{2}}dx&=\int\sqrt{a^{2}\tan^{2}t+a^{2}}a\sec^{2}tdt\\
&=\int a^{2}\sec^{3}tdt
\end{aligned}$$

$$\begin{aligned}&=\int a\cdot\sec\cdot ad(tant)=a^{2}\int sec^{3}t\cdot dt=a^{2}A\\&=a^{2}\left[\text{tant}\cdot\sec-\int tant\cdot d(sect)\right]\\&=a^{2}\left[\tan t\cdot\sec t-\int(sec^{2}t\cdot sect\cdot dt\right]\\&=a^{2}\left[\tan t\cdot\sec t-\int sec^{3}t\cdot dt+\int sect\cdot dt\right]\\&=a^{2}\left[\tan t\cdot\sec t-\int sec^{3}t\cdot dt+\int sect\cdot dt\right]\\&=a^{2}\left[\tan t\cdot\sec t-A+\ln(sect+tant)\right]\\&\text{解得 原式}=a^{2}A=\frac{a^{2}}{2}tant\cdot\frac{a^{2}}{2}ln(sect+tant)+C\end{aligned}$$

$$\begin{aligned}\text{由三角关系得tant}&=\frac{x}{a}，sect=\sqrt{x^{2}+a^{2}}\text{,代入有}\\&\text{原式}=\frac{a^{2}}{2}\cdot\frac{x}{a}\cdot\sqrt{x^{2}+a^{2}}+\frac{a^{2}}{2}\ln\left(\frac{x}{a}+\sqrt{x^{2}+a^{2}}\right)+C\\&=\frac{x}{2}\sqrt{x^{2}+a^{2}}+\frac{a^{2}}{2}ln\left(x+\sqrt{x^{2}+a^{2}}\right)+D\end{aligned}$$

很繁琐对不对？还要回代，现给出群里交流时的一种简便的做法：

$$\begin{gathered}
\int \sqrt{ x^{2}+a^{2} } \, dx =\int\frac{x^{2}+a^{2}}{\sqrt{x^{2}+a^{2}}}dx=\int\frac{x^{2}}{\sqrt{x^{2}+a^{2}}}dx+\int\frac{a^{2}}{\sqrt{x^{2}+a^{2}}}dx \\
=\int\frac{x}{2\sqrt{x^{2}+a^{2}}}d(x^{2}+a^{2})+a^{2}\mathrm{ln}\:(x+\sqrt{x^{2}+a^{2}}) \\
=\int xd\left(\sqrt{x^{2}+a^{2}}\right)+a^{2}\ln\left(x+\sqrt{x^{2}+a^{2}}\right) \\
=x\sqrt{x^{2}+a^{2}}-\int\sqrt{x^{2}+a^{2}}dx+a^{2}\ln\left(x+\sqrt{x^{2}+a^{2}}\right) 
\end{gathered}$$

移项合并，系数化1得

$$\int\sqrt{x^{2}+a^{2}}dx=\frac{x}{2}\sqrt{x^{2}+a^{2}}+\frac{a^{2}}{2}\ln\left(x+\sqrt{x^{2}+a^{2}}\right)+C$$

是不是比较简单呢？

类似的，给出长得类似的三个根式积分的结果，各位可以自行推导：

Q: $\int\sqrt{x^{2}+a^{2}}dx$
A:后一半和$\int \sqrt{ x^{2}-a^{2} } \, dx$是一样的，因为都是做有理化同乘出来的，前一半和被积函数形式一致
$$\int\sqrt{x^{2}+a^{2}}dx=\frac{x}{2}\sqrt{x^{2}+a^{2}}+\frac{a^{2}}{2}\ln\left(x+\sqrt{x^{2}+a^{2}}\right)+C$$
<!--ID: 1729596379845-->


Q: $\int\sqrt{x^2-a^2}dx$
A:后一半和$\int \sqrt{ x^{2}+a^{2} } \, dx$是一样的，因为都是做有理化同乘出来的，前一半和被积函数形式一致
$$\int\sqrt{x^2-a^2}dx=\frac x2\sqrt{x^2-a^2}+\frac{a^2}2\ln\left|x+\sqrt{x^2+a^2}\right|+C$$
<!--ID: 1729596379922-->


Q: $\int\sqrt{a^2-x^2}dx$
A:前一半和被积函数保持一致，因为这是做有理化，凑微分得到的，后一半是凑出来的$\frac{1}{\sqrt{ a^{2}-x^{2} }}$
无论是$a^{2}-x^{2}$还是$x^{2}-a^{2}$，**后面部分**都带着$\frac{a^{2}}{2}$
$$\int\sqrt{a^2-x^2}dx=\frac x2\sqrt{a^2-x^2}+\frac{a^2}2arcsin\frac xa+C$$
<!--ID: 1729596379991-->



