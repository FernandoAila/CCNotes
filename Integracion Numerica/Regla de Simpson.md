El algoritmo de la regla de simpson propone aproximar la integral por medio de parabolas por lo que en este caso necesitariamos  3 puntos o 2 sub-intervalos, es decir, $[x_0,x_2]$.
Por ejemplo, si integramos una parabola se tiene
$$\int_{x_0}^{x_{2}} ax^{2} + bx+ cdx = (x_1-x_0)\frac{1}{3}((ax_{o}^{2}+bx_{0}+c)+4(ax_{1}^{2}+bx_{1}+c)+(ax_{2}^{2}+bx_{2}+c)) $$

![[Pasted image 20221124142745.png]]
Lo cual induce la aproximación:
$$
\int_{x_0}^{x_{2}}f(x)dx=h\frac{1}{3}(f(x_0)+4f(x_1)+f(x_2))
$$
Notar que necesitamos una cantidad par de sub-intervalos, por lo que debe satisfacer la relación $m=2n$
Por lo que si lo expandimos al intervalo $[a=x_0,b=x_m]$:
$$\int_{a}^{b}f(x)dx=\frac{h}{3}\left(f(x_0)+4 \sum\limits_{i=1}^{n}f(x_{2i-1}+2 \sum\limits_{i=1}^{n-1}f(x_{2i})+f(x_m) \right)- (b-a)\frac{h^4}{180}f^{4}(c)$$
donde $h=(b-a)/m$.

Notar que todos los metodos planteados poseen la misma forma,  el producto punto de un vector de pesos y un vector de puntos evaluado en la funcion $f(x)$.
Por otro lado, $f^4(c)$ posee la caracteristica de que hace que el error sea 0 para una familia de funciones como una funcion constante y polinomios de grado 1,2,3 . Sin embargo requerimos que esta esté acotada

![[Pasted image 20221124145810.png]]

![[Pasted image 20221124150543.png]]