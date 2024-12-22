---
publish: true
tags: 
aliases: 
finished: true
title: exp乘三角的积分
created: "2024-10-21 13:10"
updated: "2024-12-21 23:32"
---
可以用[[表格积分法]]来算，因为会出现重复的部分，也可以用雅克比行列式来算

导数写上面，原函数写下面，系数配比在分母

$$\int e^{ax}\sin bxdx=\frac{{\begin{vmatrix}\left(e^{ax}\right)^{\prime}&\left(\sin bx\right)^{\prime}\\e^{ax}&\sin bx\end{vmatrix}}}{a^{2}+b^{2}}+C=\frac{ae^{ax}\sin bx-be^{ax}\cos bx}{a^{2}+b^{2}}+C$$

$$\int\mathrm{e}^{ax}\cos bx\mathrm{d}x=\frac{{\begin{vmatrix}\left(e^{ax}\right)^{\prime}&\left(\cos bx\right)^{\prime}\\e^{ax}&\cos bx\end{vmatrix}}}{a^{2}+b^{2}}=\frac{a\mathrm{e}^{ax}\cos bx+b\mathrm{e}^{ax}\sin bx}{a^{2}+b^{2}}+C$$

再如

$$\int\mathrm{e}^{-x}\sin nx\mathrm{d}x=\frac{-\mathrm{e}^{-x}\sin nx-n\mathrm{e}^{-x}\cos nx}{(-1)^{2}+n^{2}}+C$$