---
up:
  - "[[Single variable calculus]]"
related:
  - "[[ENGG1125 Single Variable Calculus for Engineers]]"
date: 2026-01-15
---
## Limits
Limits formalize the idea of “approaching” a value. 
$$
  \lim_{x \to a} f(x)=L
$$

## Evaluating Limits
1. **Determinate form**: Direct Substitution 
2. **Indeterminate form ($\frac{0}{0}$)** (denominator=0): Needs cancellation (factoring or conjugates)

> [!NOTE] Sandwich Theorem (Squeeze Theorem) 
> If $g(x) \leq f(x) \leq h(x)$ and $\lim_{x \to c} g(x) = \lim_{x \to c} h(x) = L$, then  
> $$
> \lim_{x \to c} f(x) = L
> $$ 

### Practice of Squeeze Theorem
> [!example]
> (a)小问
> 有三角函数，就找三角函数范围，然后用squeeze theorem
> ![[image-1768751979302.webp|621x484]]
> 

## Left Hand & Right Hand Limits
Left Hand Limit
$$
\lim_{ x \to 0 ^-} f(x)
$$
Right Hand Limit
$$
\lim_{ x \to 0 ^-} f(x)
$$

## Limits and Continuity
> [!NOTE] DEF'N
> f is continuous at $x_{0}$ means 
> $$\lim_{ x \to x_{0} }f(x)=f(x_{0})$$

从上面这个定义中，我们可以证明出这个理论：
> [!NOTE] DIFF->CTS THEOREM
> if f is differentiable at $x_{0}$, then f is continuous at $x_{0}$.
$$
证明过程:
\begin{align}
如果\lim_{ x \to x_{0} }f(x)-f(x_{0})=0那么f就是continous的 \\
 咱们巧妙的给它上下同乘(x-x_{0})\\
=\lim_{ x \to x_{0} } \frac{f(x)-f(x_{0})}{x-x_{0}}(x-x_{0})  \\
=f'(x_{0})\times 0 \\ 
所以只要f'(x_{0})是存在的那这个式子就等于0 \\
也就是continuous的 \\
\end{align}
$$



> [!NOTE] Types of Discontinuity
> - **Removable Discontinuity**:
> 	- Limit from left & right are equal.
> - **Jump Discontinuity**:
> 	- Limit from left + right exists but are not equal
> 	- So it does not have an overall limit
> - **Infinite Discontinuity**: 
> 	- function grows unbounded
> - **Oscillating Discontinuity**
> 	- Oscillation
> 
> ![[image-1768714728186.webp|400x204]]

> [!yellow] Limit (Overall Limit) do not exist on
>   1. Jump discontinuity 
>   2. Infinite Discontinuity
>   3. Oscillating Discontinuity

 


## Limit Laws
  - Sum: $\lim_{x \to c} (f(x)+g(x)) = L+M$  
  - Difference: $\lim_{x \to c} (f(x)-g(x)) = L-M$  
  - Constant Multiple: $\lim_{x \to c} (k f(x)) = kL$  
  - Product: $\lim_{x \to c} (f(x)g(x)) = LM$  
  - Quotient: $\lim_{x \to c} \frac{f(x)}{g(x)} = \frac{L}{M}, \, M \neq 0$  
  - Power: $\lim_{x \to c} [f(x)]^n = L^n$  
  - Root: $\lim_{x \to c} \sqrt[n]{f(x)} = \sqrt[n]{L}$  

## The Precise Definition of a Limit
为什么要一个精确的定义？因为“极限接近”这样的模糊定义不足够用于数学证明。

> [!NOTE] Precise Definition of a Limit (Epsilon–Delta DEFN)
> 概念：不管你给个多小的y范围($\epsilon$)，我都能给出一个x范围($\delta$)，里面随便取一个x，对应的f(x)都在这个范围里面
> 
> for every $\epsilon>0$,there exists a $\delta>0$ such that
> $$
> 
> \begin{align} |f(x)-L|<\epsilon,0<|x-c|<\delta \\ \\
> \end{align}
> $$

### Practice of Epsilon-Delta DEFN
> [!example] eg1
> (b)小问
> 
> ![[image-1768751979302.webp|621x484]]
> 

> [!example] eg2
> ![[image-1768754469799.webp|603x434]]

Some more examples: [Lecture 2.pdf](file:///Users/kevin/Documents/Courses/Term%202/ENGG1125%20Single%20variable%20calculus/Lecture%202.pdf)

## REFERENCE
[MIT Limit](https://youtu.be/ryLdyDrBfvI?si=t2fK4r-TsjxImfxJ)
[3B1B](https://youtu.be/kfF40MiS7zA?si=dVwjhzMJjSUQRaNZ)
[Epsilon Delta Explained](https://youtu.be/-ejyeII0i5c?si=6HAOyW46tkFmvgs9)