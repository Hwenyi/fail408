---
finished: true
aliases: 方程不显含y
tags: []
publish: true
created: "2024-04-17 04:59"
updated: "2024-09-22 09:33"
title: 方程不显含y
---
形如：
$$xy''+y'=4x$$
不出现一次的y，也就是 $y''=f(x,y')$ ，y''等于x和y'组成的多项式
把二阶当一阶，把一阶不当阶
$(1)$ 令 $y^{\prime}=p(x),y^{\prime\prime}=p^{\prime}$，则原方程变为一阶方程 $\frac{dp}{dx}=f(x,p)$
把原式转化为[[一阶线性微分方程]]，然后求出通解为
$(2)$ 若求得其通解为 $p=\varphi(x，C_1)$，即 $y^{\prime}=\varphi(x，C_1)$，则原方程的通解为 
再代换回y转化为[[可分离变量的微分方程]]，两边积分得到：
$(2)$ 若求得其通解为 $p=\varphi(y,C_1)$，则由 $p=\frac{dy}{dx}$ 可得 $\frac{dy}{dx}=\varphi(y，C_1)$，分离变量得 $\frac{dy}{\varphi(y，C_1)}=dx$；
$(3)$ 两边积分得 $\int\frac{dy}{\varphi(y，C_{1})}=x+C_{1}$。即可求得原方程的通解。

