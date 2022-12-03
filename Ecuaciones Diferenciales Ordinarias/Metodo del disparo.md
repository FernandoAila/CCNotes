La base del metodo del disparo es considerar un BVP como un IVP.
Recordemos que los IVP tienen una condicion inicial, mientras que los BVP tienen 2 condiciones de borde. Es decir, la unica diferencia es la condicion de borde adicional.

Por ejemplo, el siguiente BVP, $y^{"}(x)=0$ para $x\in]0,1[$, $y(0)=c_1$ y $y(1)=c_2$, consideraremos que $x\rightarrow t$ de forma de que obtendriamos un IVP de la forma:
$$
\begin{align*}
y^{"}(x)=0\\
y(c)=c_1\\
y'(c)=\alpha
\end{align*}
$$
Queda entonces preguntarse que sucede con $y(1)=c$ y con $\alpha$, ya que este ultimo es un valor desconocido.
Este problema se convierte en un [[Sistemas Dinamicos]] similar al pendulo. Si continuamos con la transformacion de la ODE:

$$
\begin{align*}
y_1(t)=y(t)\\
y_2(t)=y'(t)
\end{align*}
$$
Obtenemos que:
$$
\begin{align*}
\dot y &= y_2\\
\dot y_{2} &= 0\\
y_{1}(0)&= c_1\\
y_{2}(0)&= \alpha\\

\end{align*}
$$

Siendo $\alpha$ un valor elegido arbitrariamente

A medida que vamos iterando por ejemplo, con el [[Metodo de Euler]], vamos a llegar al valor de $t_n$ (en nuestro caso sería $1$) que implica que llegamos al fin del intervalo. De esta forma generamos "puntos" discretos que aproximan a la función $y_1(t)$.
Es ahí donde verificamos si el valor calculado usando el $\alpha$, en este caso $y_1(1)$ satisface el valor entregado en la condición de frontera.
Normalmente este valor es poco probable  que se cumpla de inmediato. Que podemos hacer en este caso?

La respuesta es que podemos resolver nuevamente el IVP usando otro valor de $\alpha$, por ejemplo, $\alpha_1$ el cual entregaría otra aproximacion de $y_1(t)$.
Nuevamente podemos aplicar el mismo analisis, si $y_{1numerico}(t_n)$ es cercano al valor original $y_1(1)=c_2$ 
En principio podemos iterar infinitas veces, pero podemos reconocer que estamos resolviendo un probema de busqueda de ceros!
En particular, estamos buscando una solución a la ecuación:
$$
g(x)=y_{numerico}(t_n)-c_2=0
$$
Por lo cual, podemos realizar, cualquier metodo de [[Raices en 1D]] visto.