El algoritmo o regla del trapecio es otra regla de [[Cuadratura]] propone aproximar la integral por medio de trapecios  en cada sub-intervalo, es decir, para $[x_0,x_1]$ se tiene:
$$\int_{x_0}^{x_{1}} f(x) \approx (x_1-x_0)\frac{1}{2}(f(x_0)+f(x_1)) $$

El error directo del intervalo $[x_{0}, x_{1}]$ es:
$$
\int_{x_0}^{x_{1}} f(x) = \frac{h}{2}(f(x_{0)}+f(x_1)) -\frac{h^3}{12}f^{´ ´}(c)
$$
donde $h=x_1-x_0$ y $c \in [x_{0} , x_1]$.

Si llevamos esta idea al intervalo $[a=x_{0}, b=x_{m}]$:
$$\begin{align*}
\int_{a}^{b} f(x)dx &= \sum\limits_{i=1}^{m}\int_{x_{i-1}}^{x_{i}}f(x)\\
&=\frac{h}{2}\left(f(a)+f(b)+2 \sum\limits_{i=1}^{m-1}f(x_i) \right)- (b-a)\frac{h^2}{12}f^{''}(c)
\end{align*}$$
donde $h=(b-a)/m$ .

Escrito el metodo como producto punto es:
$$
\int_{a}^{b}f(x)dx=<\vec{f(x)},\vec{h}>
$$
Donde $\vec{f(x)}=[\frac{f(a)}{2},f(x_{1}),f(x_{2}),f(x_{3}),f(x_{4}),\cdots, f(x_{i})\cdots ,f(x_{m-1}),\frac{f(b)}{2}]$
y $\vec{h}=[h,h,h,\cdots,h]$


![[Pasted image 20221124041132.png]]

![[Pasted image 20221124041237.png]]