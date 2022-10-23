Para encontrar el polinomio interpolador para n puntos, si hacemos uso de la [[Matriz de Vandermonde]], tendriamos que resolver el sistema de ecuaciones asociado. La gran ventaja del metodo de Lagrange es que no hay que resolver ningun sistema de ecuaciones lineales, ya que nos aprovechamos de una definicion particular de la estructura del polinomio interpolador.
Esta estructura tiene la siguiente forma con $n$ puntos:$$p(x)=y_1L_1(x)+y_2L_2(x)+\cdots+ y_nL_n(x)$$
Donde $L_i(x)$ son funciones donde $L_i(x_i)=1$ y $L_i(x_j)=0$ con $i\neq j$. Esta definicion nos permite obtener $y_k$ cuando evaluamos a si manteniendo la condicion de $p(x_k) = y_k$:$$p(x_k)=y_1\underbrace{L_1(x_k)}_\text{0}+y_2\underbrace{L_2(x_k)}_\text{0}+\cdots+ y_k\underbrace{L_k(x_k)}_\text{1}+\cdots+y_n\underbrace{L_n(x_k)}_\text{0}
$$
Las funciones $L_i(x)$ se contruyen definiendo las funciones $l_i(x)$ de la forma:
![[Pasted image 20221022232326.png]]
Es decir la productoria de la expresion $(x-x_k)$ menos $(x-x_i)$.
De esta forma nos aseguramos que $l_i$ evaluado en cualquier numero sea 0 menos en $x_i$.
Sin embargo si evaluamos en $x_i$ no necesariamente es $1$, y no es $0$ por construccion.
Entonces para cumplir que $L_i(x_i)=1$, realizamos el cuociente entre $l_i(x)$ y $l_i(x_i)$, luego:
![[Pasted image 20221022233142.png]]

