---
publish: true
tags: 
aliases: 
finished: true
title: 广义p积分
created: "2024-10-13 04:52"
updated: "2024-10-13 04:52"
---
[广义p积分](https://www.bilibili.com/video/BV19FWDeEEkQ?t=62.0&p=4),用来给[[反常积分]]的题目举特例，要么举[[p积分]]的特例，要么就是广义p积分的特例

$$\int_{1}^{2}\frac{1}{x\ln^{p}x}\:\mathrm{d}x\begin{cases}\text{收敛，}&0<p<1,\\\text{发散，}&p\geqslant1.\end{cases}$$
$$[\text{注]令}\ln x=t\:，\:I=\int_{0}^{\ln2}\frac{\mathrm{d}t}{t^{p}}\:\begin{cases}\text{收敛，}&0<p<1,\\\text{发散，}&p\geqslant1.\end{cases}$$

$\int_{2}^{+\infty}\frac{1}{x\ln^{p}x}$d$x$ 与(仅数学一、数学三$)\sum_n=2^{\infty}\frac1{n\ln^{\rho}n}$同敛散$\begin{cases}\text{收敛，}&p>1，\\\text{发散，}&p\leqslant1.\end{cases}$

$$[\text{ 注 }]\text{ 令}\ln x=t\:，\quad I=\int_{\ln2}^{+\infty}\frac{\mathrm{d}t}{t^p}\left\{\begin{array}{ll}\text{收敛，}&p>1,\\\text{发散，}&p\leqslant1.\end{array}\right.$$

$$\int_{1}^{+\infty}\frac{1}{x\ln^{p}x}\mathrm{d}x\:\text{必发散}$$

$$\text{【注】}\int_{1}^{+\infty}\frac{1}{x\ln^{p}x}\:\mathrm{d}x=\int_{1}^{2}\frac{1}{x\ln^{p}x}\:\mathrm{d}x+\int_{2}^{+\infty}\frac{1}{x\ln^{p}x}\:\mathrm{d}x\:，\:\text{结合}{1}\:，\:{2}\:,\:\text{收敛域为空集，故必发散}\:.$$