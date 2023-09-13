Probably a very important fact that should be noted is the fact that $f$ has to be continuous and differentiable over any interval $[a, b]$ we approximate over.
# Approximating the square root
$$x_{n+1} = \frac{1}{2} ( \frac{a}{x_n} + x_n )$$
Start at some arbitrary $x_0$.
# Errors

## Approximation Error
$$\text{Approximation Error} = |curr_i - prev_i|$$
## Relative Approximation Error
$$\text{Relative Approximation Error} = \frac{|curr_i - prev_i|}{curr_i}$$
## True Error
$$\text{True Error} = curr_i - prev_i$$
## Relative True Error
$$\text{Relative True Error} = \frac{curr_i - prev_i}{curr_i}$$
# Newton Raphson Method
$$x_{n + 1} = x_n - \frac{f(x_n)}{f'(x_n)}$$

**TO NOTE:** You can derive the square root finding formula from this pretty easily

# Secant Method
$$x_{n + 1} = x_{n - 1} - \frac{f(x_{n - 1})}{\frac{f(x_n) - f(x_{n - 1})}{x_n - x_{n - 1}}}$$
Secant might be faster than newton raphsons in practice since we are computing only $f$ over a certain number of iterations vs computing both $f$ and $f'$ for newton raphson.

# Bisection Method

- **Step 1**: Choose $a$, $b$ s.t.
	- $a < b$ 
	- $f(a) \cdot f(b) < 0$
- **Step 2**: $x_0 = \frac{a + b}{2}$
- **Step 3**: if $f(x_0) = 0$ : $res = x_0$
- **Step 4**: if $f(a) \cdot f(x_0) < 0$ : $b = x_0$
- **Step 5**: else if $f(b) \cdot f(x_0) < 0$ : $a = x_0$
- **Step 6**: Go to **Step 2**

Usually we do this a fixed number of times, since it converges fast as the search space is halved at each iteration.
# Jacobi's Method

## Iterative Method
$$\begin{equation}
x_i^{(k+1)}=\frac{1}{a_{i i}}\left(b_i-\sum_{j \neq i} a_{i j} x_j^{(k)}\right), \quad i=1,2, \ldots, n .
\end{equation}$$
$L$ is the lower triangular matrix w/out the diagonal. 
$U$ is the upper triangular matrix w/out the diagonal.
## Matrix Method
$$\begin{equation}
\mathbf{x}^{(k+1)}=D^{-1}\left(\mathbf{b}-(L+U) \mathbf{x}^{(k)}\right)
\end{equation}$$
# Gauss Seidel Method

## Iterative Method

Literally the same as Jacobi's

$$\begin{equation}
x_i^{(k+1)}=\frac{1}{a_{i i}}\left(b_i-\sum_{j=1}^{i-1} a_{i j} x_j^{(k+1)}-\sum_{j=i+1}^n a_{i j} x_j^{(k)}\right), \quad i=1,2, \ldots, n .
\end{equation}$$
Why is it the same? because $x_i^{(k + 1)} = x_i^{(k)}$.
## Matrix Method

$$\begin{equation}
\mathbf{x}^{(k+1)}=L_*^{-1}\left(\mathbf{b}-U \mathbf{x}^{(k)}\right)
\end{equation}$$
$L_{*}$ is the lower triangular matrix with the diagonal.

# Numerical Differentiation

## Taylor Series formula

What this basically says is that we can approximate any function $f$ , assuming it is continuous and differentiable, using:

$$f(x) = \sum_{n=0}^{\infty} \frac{f^{(n)}(a)}{n!}(x - a)^n$$

This is nothing but a series of polynomials $(x - a)^i$ and some constant factors $\frac{f^{(n)}(a)}{n!}$. We obviously don't need all the terms to reasonably estimate $f$ as $(x - a)^i \rightarrow 0$ as $x \rightarrow a$, i.e. around the neighborhood of $a$ we can approximate $f$ well with a few terms.  

## Forward Difference

The difference formula is pretty simple.
$$f'_{i} = \frac{f_{i + 1} - f_i}{h}$$

### Errors

Assume a taylor series centered at $x_i$ for $f$.
Assume $f(x_{i + 1}) = f_{i + 1}$ and $\Delta x = x_{i + 1} - x_i = h$ for ease of notation. 

$$
f_{i + 1} = f_i + f'_i h + \frac{f''_i}{2!} h^2 + \frac{f'''_i}{3!} h^3 + \dots
$$

We can simplify this to get:

$$
f'_{i} = \frac{f_{i + 1} - f_i}{h} - \frac{f''_i}{2!} h - \frac{f'''_i}{3!} h^2 + \dots
$$
or, 
$$f'_{i} = \frac{f_{i + 1} - f_i}{h} - \sum_{n = 2}^{\infty} \frac{f^{(n)}_n}{n!}h^{n - 1}$$
This gives the exact value of the derivative. But the forward difference formula only has the first term. The second term and onwards can be thought of as error terms from the approximation. So for a function with $degree = 2$ the error is basically some function which is $\in \mathcal{O}(h)$. But for higher order functions say with $degree = n$ the error would be $\in \mathcal{O}(h^{n - 1})$. 

Formally call $F_{error}(f(x)) = \sum_{n = 2}^{\infty} \frac{f^{(n)}_n}{n!}h^{n - 1}$, $F_{error}(x_i) \in \mathcal{O}(h^{n - 1})$.

## Backward Difference
$$f'_{i} = \frac{f_{i} - f_{i - 1}}{h}$$
### Errors

Similarly as before we can find the derivative to be:

$$f'_{i} = \frac{f_{i} - f_{i -1}}{h} + \frac{f''_i}{2!} h - \frac{f'''_i}{3!} h^2 + \dots$$
or, 
$$f'_{i} = \frac{f_{i + 1} - f_i}{h} + \sum_{n = 2}^{\infty} (-1)^{n}\frac{f^{(n)}_n}{n!}h^{n - 1}$$
Similarly let $B_{error}(f(x)) = \sum_{n = 2}^{\infty} (-1)^{n}\frac{f^{(n)}_n}{n!}h^{n - 1}$ and $B_{error}(f(x)) \in \mathcal{O}(h^{n - 1})$.

## Central Difference
$$f_i = \frac{f_{i + 1} - f_{i - 1}}{2h}$$
### Errors

Similarly:

$$f'_i = \frac{f_{i + 1} - f_{i - 1}}{2h} - \sum_{n = 1}^{\infty} \frac{f^{(n)}_n}{(2n + 1)!}h^{2n}$$
$C_{error}(f(x)) = \sum_{n = 1}^{\infty} \frac{f^{(n)}_n}{(2n + 1)!}h^{2n}$ and $C_{error}(f(x)) \in \mathcal{O}(h^{n - 1})$.

## Comparisons in the errors

Asymptotically all of these errors are the same. But what is noteworthy is that for a sufficiently large $h_{bound}$ for all $h \geq h_{bound}$ we can say that the backward difference will give us the best approximation i.e.:
$$B_{error}(f(x)) \leq C_{error}(f(x)) \leq F_{error}(f(x))$$
and obviously as $h \rightarrow 0$ all the errors also $\rightarrow 0$. I omit the proof of this for the reader because lord knows tanvir fahim chudbe na thikmoton likhleo. But can be proved by induction on $h$ and $h + \epsilon$, also some limiting ching chong unsure about details. Also to note $C_{error} = \frac{F_{error} + B_{error}}{2}$.
## 3 Point Forward Difference
$$\begin{equation}
f^{\prime}(x)=\frac{4 f(x+h)-f(x+2 h)-3 f(x)}{2 h}-\text{some extra ching chong}
\end{equation}$$
## 3 Point Backward Difference
$$\begin{equation}
f^{\prime}(x)=\frac{-4(x-h)+f(x-2 h)+3 f(x)}{2 h}-\text{some extra ching chong}\end{equation}$$
## 3 Point Central Difference

Same as 2 point central diff.

Same argument applies for the comparison of errors as before.

# Second Order Derivatives

## 3 point Forward Difference
$$\begin{equation}
f^{\prime \prime}(x)=\frac{f(x)-2 f(x+h)+f(x+2h)}{h^2} + \text{some extra ching chong}
\end{equation}$$
## 3 Point Backward Difference
$$\begin{equation}
f^{\prime \prime}(x)=\frac{f(x)-2 f(x-h)+f(x-2 h)}{h^2} + \text{some extra ching chong}
\end{equation}$$
## 3 Point Central Difference
$$f''(x) = \frac{f(x - h) - 2f(x) + f(x + h)}{h^2} + \text{some extra ching chong}$$

All arguments from before still hold.

# Multi variable Newton Raphsons Method
$$\begin{equation}
\mathbf{x}_k=\mathbf{x}_{k-1}-J^{-1} \mathbf{f}\left(\mathbf{x}_{k-1}\right)
\end{equation}$$
where, 
$$\begin{equation}
J = D \mathbf{f}\left(\mathbf{x}_{k-1}\right) = \begin{bmatrix}
  \dfrac{\partial \mathbf{f}}{\partial x_1} & \cdots & \dfrac{\partial \mathbf{f}}{\partial x_n}
\end{bmatrix}
= \begin{bmatrix}
  \nabla^{\mathrm T} f_1 \\  
  \vdots \\
  \nabla^{\mathrm T} f_m   
\end{bmatrix}
= \begin{bmatrix}
    \dfrac{\partial f_1}{\partial x_1} & \cdots & \dfrac{\partial f_1}{\partial x_n}\\
    \vdots                             & \ddots & \vdots\\
    \dfrac{\partial f_m}{\partial x_1} & \cdots & \dfrac{\partial f_m}{\partial x_n}
\end{bmatrix}
\end{equation}$$
Also known as the Jacobian.