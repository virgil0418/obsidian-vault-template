---
up:
  - "[[Linear Algebra]]"
related:
date: 2026-01-21
---
## Definition

> [!NOTE] Linear Equation 线性方程
> 所有变量都是**一次方**，并且**与常量相乘**
> $$a_{1}x_{1}+a_{2}x_{2}+\dots+a_{n}x_{n}=b$$
> 

> [!NOTE] System of Linear Equation 线性方程组
> 几个包含相同变量的Linear Equation组成的式子。

## Forms

Linear Equation->Vector Form->Matrix Form->Augmented Matrix Form
$$
\begin{cases}3x_{1}+x_{2}=4\\6x_{1}+5x_{2}=2\end{cases}
\to
\begin{pmatrix}3\\6\end{pmatrix}x_{1}+
\begin{pmatrix}1\\5\end{pmatrix}x_{2}=
\begin{pmatrix}4 \\2\end{pmatrix}
\to
\begin{bmatrix}3&1\\6&5\end{bmatrix}
\begin{pmatrix}x_{1}\\x_{2}\end{pmatrix}=
\begin{pmatrix}4\\2\end{pmatrix}
\to
\left[\begin{array}{cc|c}3 & 1 & 4 \\6 & 5 & 2\end{array}\right]
$$


## Solutions
**Consistent vs inconsistent**
- consistent: has solution
	- one solution
	- infinitely many solutions
- inconsistent: no solution

**Homogeneous vs Non-homogeneous**
- Homogeneous
	- $A\overrightarrow{x}=0$
	- at least one solution, where $\overrightarrow{x}=0$ (trivial solution)
	- non trivial solution exits only if theres at least one free variable
- Non-homogeneous
	- $A\overrightarrow{x}=\overrightarrow{b}$

## Solve
[[Gaussian Elimination with row operation]]

## Echelon Form& Row Reduction
[[Echelon Form]]

> [!NOTE] Row Reduction
> 把矩阵变成Reduced Echelon Form
> 1. 从左往右，把pivot都变成1，下面都变成0
> 2. 从右往左，把pivot上方的数字都变成0
