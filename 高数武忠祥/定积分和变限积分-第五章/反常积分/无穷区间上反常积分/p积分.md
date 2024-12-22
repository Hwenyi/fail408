---
publish: true
finished: true
aliases: p积分
tags: []
created: 2024-03-10 04:38
updated: 2024-09-22 09:33
title: p积分
TARGET DECK: 大学数学::高数武忠祥::定积分和变限积分-第五章::反常积分::无穷区间上反常积分::p积分
---

Q:p积分和无穷递缩等比数列求和是一致的
A:如果等比数列是递缩的，也就是公比小于1，也就是每一项都是<1的数，显然是收敛的
如果$\frac{1}{x}$这里的x是分数，那么倒一下就是一个变大的等比数列，也就发散了
$$\text{常用结论}:\int_a^{+\infty}\frac1{x^P}dx\begin{cases}P>1&\text{收敛}\\P\leq1&\text{发散}\end{cases}(a>0)$$
$$\int_{1}^{+\infty}\frac{\ln x}{x^{p}}\:\mathrm{d}x\:\begin{cases}\text{收敛，}p>1,\\\text{发散，}p\leqslant1.\end{cases}$$
基本上，很多时候，反常积分的敛散性都是和这个已知的p积分的敛散性作比较 
从$[a,\infty]$这个区间上的p积分，这和**那个$x-a$的那个公式的敛散性是相反的！**
**在[0,1]上的p积分**和$x-a$那个[[p积分-瑕积分]]是一致的
$$\int_0^1\frac1{x^p}\:\mathrm{d}x\begin{cases}\text{收敛，}0<p<1,\\\text{发散，}p\geqslant1;\end{cases}$$
$$\int_0^1\frac{\ln x}{x^p}\:\mathrm{d}x\begin{cases}\text{收敛，}0<p<1,\\\text{发散，}p\geqslant1.\end{cases}$$
[更多结论看这里](obsidian://bookmaster?type=open-book&bid=aLcWXQEPprFPkUSX&aid=7ab597f2-5fdc-c7c3-1047-dc9dd7593603&page=214):[[25张宇-高数强化18讲.pdf#page=214]]
[敛散性的判别法](obsidian://bookmaster?type=open-book&bid=GdmjFWSvPKSCJmGt&aid=8237d916-4218-618d-dad3-9e5c22467374&page=155):[[2025张宇30讲-高等数学.pdf#page=155]]
<!--ID: 1728212210525-->

