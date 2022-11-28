Sabemos que el [[Metodo de Euler]] es de orden $O(h)$ es decir, 1.
Ahora para obtener un algoritmo de orden superior, podemos volver a visitar la aproximación de la integral original:


$$
y(t_1)=y_0+\int_{0}^{t_1}f(s,y(s))ds
$$

Tanto en el [[Metodo de Euler]] como en el [[Backward Euler]] determinamos $y_{i+1}$ a partir de un $y_{i}$ conocido.
Ahora podemos usar otro algoritmo para aproximar la integral, por ejemplo, el [[Regla del Punto Medio]]. 

Si aplicamos la regla del punto medio resulta:

$$
y(t_1)=y_0+\int_{0}^{t_1}f(s,y(s))ds \approx y_{0} + f(\frac{t_1}{2},y(\frac{t_1}{2}))(t_1-0)
$$
Notar que no conocemos el valor de $y(\frac{t_1}{2})$, pero podemos estimarlo con el [[Metodo de Euler]] de la forma:
$$
y(\frac{t_1}{2})\approx k_1= y_{0}+f(0,y_0)\frac{t_1}{2}
$$
Luego:
$$
\begin{align*}
k_1&=f(t_i,y_i)\\
y_{i+1}&=y_i+hf(t_i+h/2,y_{i}+h/2k_1)
\end{align*}
$$
Donde $k_1$ no es más que la pendiente en el punto $t_i,y_i$,
Lo que tiene orden de convergencia $O(h^2)$, es decir si $h$ se reduce a la mitad, el error se reduce 4 veces, por lo que es un metodo de orden 2.

![[Pasted image 20221127225335.png]]

Existe una restricción en que el $h$ no tiene que ser muy grande por que si no entrega resultados inconsistentes.