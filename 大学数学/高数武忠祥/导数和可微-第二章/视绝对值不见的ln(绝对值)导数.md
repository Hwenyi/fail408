---
publish: true
tags: []
aliases: 
finished: false
title: 视绝对值不见的ln(绝对值)导数
created: "2024-10-26 08:04"
updated: "2024-10-26 16:05"
---

u(x)>0 时，$(\ln(|u(x)|))'=(\ln(u(x)))'=\frac{u'(x)}{u(x)}$

u(x)<0 时，$(\ln(|u(x)|))'=(\ln(-u(x)))'=\frac{-u'(x)}{-u(x)}=\frac{u'(x)}{u(x)}$

综上可知 $\ln(|x|)$ 求导视绝对值而不见，即;;$(\ln(|u(x)|))'=\frac{u'(x)}{u(x)}$

例题，设$y=\sqrt[3]{\frac{(x+1)(2x-1)^2}{(4-3x)^5}}$，求$y^{\prime}$.

解：两边加绝对值，取对数，并化简，得

$$
\ln|y|=\frac{1}{3}(\ln|x+1|+2\ln|2x-1|-5\ln|4-3x|)
$$

两边对$x$求导，得
$$
\frac{1}{y}\cdot y^{\prime}=\frac{1}{3}\left(\frac{1}{x+1}+2\cdot\frac{2}{2x-1}-5\cdot\frac{-3}{4-3x}\right)
$$
于是得到
$$
y^{\prime}=\frac{1}{3}\sqrt[3]{\frac{(x+1)(2x-1)^{2}}{(4-3x)^{5}}}\Big(\frac{1}{x+1}+\frac{4}{2x-1}+\frac{15}{4-3x}\Big)
$$

