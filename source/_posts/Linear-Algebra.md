---
title: Linear Algebra
date: 2023-07-30 16:11:16
description: 线性代数の注意点
categories:
- study
tags:
- 线性代数
---

# 线性代数

高数一轮终于结束了(悲)

线代总体知识点不多 总结一些做题遇到的需要注意的细节

---

**！！写在最前面：誊抄系数的时候 看nm仔细一点 别抄错了。。。**

## 行列式

注意 **余子式**$\mathrm{M}_{ij}$和 **代数余子式**$\mathrm{A}_{ij}$的区别
$$
\pmb{M}_{ij}=(-1)^{i+j}\pmb{A}_{ij}
$$
做题的时候 问**余子式** 则需要根据所在位置添加正负号构成新行列式；问 **代数余子式**就不需要 直接填系数构成

**左右乘**，一种很好用的化简法(灵感来自 *藍二乘*&*左右盲*)

## 矩阵

**舒尔公式**

引入 **舒尔补**的概念
$$

$$

$$

$$
将这个 y 的表达式代入矩阵可以有如下解。

Ax + B(D^{-1}(d-Cx)) = c \ (A-BD^{-1}C)x=c-BD^{-1}d

若 A-BD^{-1}C 是可逆的, 我们就能获得当前系统的解。
$$
x = (A-BD^{-1}C)^{-1}(c-BD^{-1}d) \ y = D^{-1}(d-C(A-BD^{-1}C)^{-1}(c-BD^{-1}d))
$$
A-BD^{-1}C 叫做D在M中的Schur Complement.

现在解有：
$$
x = (A-BD^{-1}C)^{-1}c-(A-BD^{-1}C)^{-1}BD^{-1}d

y = -D^{-1}C(A-BD^{-1}C)^{-1}c+(D^{-1}+D^{-1}C(A-BD^{-1}C)^{-1}BD^{-1})d
$$
通过上面的结果，我们能够通过上面的式子，得到M的逆
$$
\left(\begin{matrix} x \\ y\end{matrix}\right) = \left(\begin{matrix} M^{-1}\end{matrix}\right)\left(\begin{matrix} c \\ d\end{matrix}\right)
$$
即：
$$
 M^{-1} = \left(\begin{matrix} A & B \\ C & D \end{matrix}\right)^{-1} = \left(\begin{matrix} (A-BD^{-1}C)^{-1} & -(A-BD^{-1}C)^{-1}BD^{-1} \\ -D^{-1}C(A-BD^{-1}C)^{-1} & (D^{-1}+D^{-1}C(A-BD^{-1}C)^{-1}BD^{-1}) \end{matrix}\right) \\ = \left(\begin{matrix}(A-BD^{-1}C)^{-1} & 0 \\ -D^{-1}C(A-BD^{-1}C)^{-1} & D^{-1}\end{matrix}\right)\left(\begin{matrix} I & -BD^{-1} \\ 0 & I \end{matrix}\right) \\ = \left(\begin{matrix} I & 0 \\ -D^{-1}C & I \end{matrix}\right) \left(\begin{matrix} (A-BD^{-1}C)^{-1} & 0 \\ 0 & D^{-1} \end{matrix}\right) \left(\begin{matrix} I & -BD^{-1} \\ 0 & I \end{matrix}\right)
$$
在这种状态下很容易求解原来的 M
$$
M = (ONP)^-1 = P^{-1}(ON)^{-1} = P^{-1}N^{-1}O^{-1} \\ = \left(\begin{matrix} I & BD^{-1} \\ 0 & I \end{matrix}\right)\left(\begin{matrix} A-BD^{-1}C & 0 \\ 0 & D \end{matrix}\right) \left(\begin{matrix} I & 0 \\ D^{-1}C & I \end{matrix}\right)
$$
