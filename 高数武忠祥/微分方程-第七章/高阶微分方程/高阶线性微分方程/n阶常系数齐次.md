---
finished: true
aliases: n阶常系数齐次
tags: []
publish: true
created: "2024-04-19 16:39"
updated: "2024-09-22 09:33"
title: n阶常系数齐次
---
[[24张宇高数带书签.pdf#page=203]]
[n阶常系数齐次线性微分方程的解](obsidian://bookmaster?type=open-book&bid=YtkKDToqywQHISXn&aid=7a1d6871-f8da-d318-ecc6-0a1202e9fbde&page=203)

方程
$$y^{(n)}+p_1y^{(n-1)}+\cdots+p_{n-1}y^{\prime}+p_{n}y=0$$
称为$n$阶常系数齐次线性微分方程，其中$p_1,p_2,\cdots,p_n$为常数，其对应的特征方程为
$$r^n+p_1r^{n-1}+\cdots+p_{n-1}r+p_n=0$$
求出其特征根。
有如下情况需要大家牢记（其中大写的英文字母均为任意常数）。
（1）特征根为单实根$r$时，微分方程通解中对应一项$Ce^{rx}$，
（2）特征根为$k$重实根$r$时，微分方程通解中对应$k$项
$$(C_1+C_2x+\cdots+C_kx^{k-1})e^{rx}$$
（3）特征根为单复根$a\pm\beta i(\beta>0)$时，微分方程通解中对应两项
$$e^{ax}(C_1\cos\beta x+C_2\sin\beta x)$$
（4）特征根为$k$重复根$a\pm\beta i(\beta>0)$时，微分方程通解中对应$2k$项
$$e^{ax}[(C_{1}+C_{2}x+\cdots+C_{k}x^{k-1})\cos\beta x+(D_{1}+D_{2}x+\cdots+D_{k}x^{k-1})\sin\beta x].$$