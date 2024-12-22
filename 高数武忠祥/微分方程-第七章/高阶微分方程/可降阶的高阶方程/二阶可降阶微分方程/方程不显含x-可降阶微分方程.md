---
finished: true
aliases: 方程不显含x
tags: []
publish: true
created: "2024-04-17 05:53"
updated: "2024-09-22 09:33"
title: 方程不显含x
---
形如：
$$yy''+y'^{2}=0$$
用链式法则，做转化，转化为p和y的方程

1. 令 $y'=p$，两边对x导，由链式法则可以得到：$y''=\frac{dp}{dx}=\frac{dp}{dy}\cdot \frac{dy}{dx}=\frac{dp}{dy}p$ 也就是 
$$y''=p\frac{dp}{dy}$$
2. 得到[[一阶线性微分方程]] 
$y^{\prime\prime}=f(y,y^{\prime})$ 型（方程中不显含自变量$x$）
(1) 令 $y^{\prime}=p,y^{\prime\prime}=\frac{dp}{dx}=\frac{dp}{dy}\cdot\frac{dy}{dx}=\frac{dp}{dy}\cdot p$，则方程变为一阶方程 $p\frac{dp}{dy}=f(y,p)$ ;
(2) 若求得其通解为 $p=\varphi(y,C_{1})$，则由 $p=\frac{dy}{dx}$ 可得 $\frac{dy}{dx}=\varphi(y,C_{1})$. 分离变量得 $\frac{dy}{\varphi(y,C_{1})}=dx$ 
(3) 两边积分得 $\int\frac{dy}{\varphi(y,C_{1})}=x+C_{2}$，即可得原方程的通解.
3. 对这个[[可分离变量的微分方程]]两边积分，得到y与x的关系

