En la derivacion del [[Metodo de Euler]] se mostraron todas las tecnicas de integración numerica discutidas, donde se concluyó que solamente se podía utilizar la suma de Riemman por la izquierda donde la aproximación era:
$$
y(t_1)=y_0+\int_{0}^{t_1}f(s,y(s))ds\approx y_0+f(0,y_0)t_1
$$
Sin embargo, si realizamos la suma de Riemman por la derecha resulta:
$$
y(t_1)=y_0+\int_{0}^{t_1}f(s,y(s))ds\approx y_0+f(t_1,y(t_1))t_1
$$
Por lo que de la misma forma:
$$
y_1=y_0+f(t_1,y_1)t_1
$$
Podemos mover todos los terminos al lado izquierdo:
$$
y_{1}-f(t_1,y_1)t_1-y_0=0
$$
Conocemos $t_{1}$,$f(t,y)$ y  $t_1$ , por lo que podemos dejar el lado izquierdo como una función que depende de $y_1$ es decir:

$$
\hat{f}(y_1)=y_{1}-f(t_1,y_1)t_1-y_0=0
$$
Lo que es claramente un problema de [[Raices en 1D|busqueda de ceros]]!. Ya que el problema radica en encontrar un $x^{*}$, en este caso, $y_1$, tal que $f(x^*)=0$. 

Por lo que de modo general debemos resolver un problema de busqueda de ceros por cada **time-step** de tiempo:
$$
\hat{f}(y_{i+1})=y_{i+1}-f(t_{i+1},y_{i+1})(t_{i+1}-t_{i})-y_i=0
$$


![[Pasted image 20221127153341.png]]

Claramente resulta más costoso computacionalmente que el [[Metodo de Euler]] tradicional