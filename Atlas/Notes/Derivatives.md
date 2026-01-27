---
up:
  - "[[Single variable calculus]]"
related:
  - "[[Limits]]"
date: 2026-01-17
aliases:
  - 导数
---
## DEFINITION
**GEOMETRIC DEF**: the slope (gradient) of tangent line
**PHYSICAL DEF**: instantaneous rate of change
![[Geometric Defenition of Derivative Ex]]
看上图，Q无限接近于P时的$\frac{\Delta f}{\Delta x}$就是Tangent line的slope
所以我们可以得出下面这个公式：

> [!NOTE]
> $$
> f'(x)=\lim_{ \Delta x \to 0 } \frac{f(x_{0}+\Delta x)-f(x)}{\Delta x}
> $$

## How to solve any Derivative?
> 使用Limit的方法

> [!example] Example 1
> $$
> f(x)=\frac{1}{x}
> $$

$$
\begin{align}
f'(x)=\frac{\Delta f}{\Delta x}=\frac{\left( \frac{1}{x_{0}+\Delta x}-\frac{1}{x_{0}} \right)}{\Delta x}  \\ \\
直接把 \Delta  x 趋近于零分子和分母都是0，所以先化简(通分)\\ \\
=\frac{1}{\Delta x}\left( \frac{x_{0}-(x_{0}+\Delta x)}{(x_{0}+\Delta x)x_{0}} \right) 
=\frac{-1}{(x_{0}+\Delta x)x_{0}} \\ \\
这时候再把\Delta x无限趋近于0，得到 \\ \\
=\frac{-1}{x_{0}^2 }
\end{align}
$$ 

> [!example] example 2
> $$
> f(x)=x^n
> $$

$$
f'(x)=\frac{\Delta f}{\Delta x}=\frac{(x+\Delta x)^n-x^n}{\Delta x}
$$
用[[Binominal Theorem]]展开
$$
(x+\Delta x)^n=x^n+n(x^{x-1}\Delta x)+O((\Delta x)^2)
$$
> $O((\Delta x)^2)$代表省略剩下的比$(\Delta x)^2$更高阶的项

$$
\begin{align}
=\frac{x^n+n(x^{x-1}\Delta x)+O((\Delta x)^2)-x^n}{\Delta x}\\
=\frac{n(x^{x-1}\Delta x)+O((\Delta x)^2)}{\Delta x} \\
=nx^{n-1}+O(\Delta x) \\ \\
把\Delta x无限趋近0 \\
=nx^{n-1}
\end{align}
$$
由此，我们就推出了微分的最关键的公式
> [!note] 关键公式 
> $$nx^{n-1}$$


