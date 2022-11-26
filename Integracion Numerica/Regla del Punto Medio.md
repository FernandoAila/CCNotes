De la misma forma que la [[Suma de Riemann]] queremos encontrar el valor de $c = \int_a^b f(x)dx$. Sin embargo, ahora el intervalo $[a,b]$ se encuentra dividido en $m$ sub-intervalos osea, $[a=x_0,x_1,x_2,\cdots,x_m,b=x_{m}]$.
El algoritmo del punto medio se puede construir como el algoritmo que integra exactamente una constante $K$ es decir:
$$\int_{x_0}^{x_{1}} K (x_1-x_0) $$
Ahora si consideramos que un intervalo pequeño $[x_0,x_1]$ la funcion se comporta de manera constante, entonces:
$$
\int_{x_{0}}^{x_1} f(x)dx \approx f(x_*)(x_1-x_0)
$$
Donde el $x_{*}= \frac{x_1+x_2}{2}$ es decir el punto medio del intervalo.
El error directo del intervalo $[x_{0}, x_{1}]$ es:
$$
\int_{x_{0}}^{x_1} f(x)dx \approx f(x_*)h+\frac{h^3}{24}f^{´ ´}(c)
$$
donde $h=x_1-x_0$ y $c \in [x_{0} , x_1]$.

Si llevamos esta idea al intervalo $[a=x_{1}, b=x_{m}]$:
$$\begin{align*}
\int_{a}^{b} f(x)dx &= \sum\limits_{i=1}^{m}\int_{x_{i-1}}^{x_{i}}f(x)\\\\
&=\sum\limits_{i=1}^{m}hf(x_{*_i})+\frac{b-a}{24}h^{2}f^{´ ´}(c)
\end{align*}$$
donde $h=(b-a)/m$ , $x_{*_{i}}=\frac{x_{i}-x_{i-1}}{2}$.

Notar que si conocemos la segunda derivada de la función podemos acotarla buscando el peor caso.
Luego, lo unico que dominaria el error es el termino $h^2$ lo dice que si el $h$ disminuye a la mitad, el error disminuye cuatro veces, si $h$ disminuye 4 veces el error disminuye 16 veces
![[Pasted image 20221124021947.png]]



![[Pasted image 20221124031614.png]]