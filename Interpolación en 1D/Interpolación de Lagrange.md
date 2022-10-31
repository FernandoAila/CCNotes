Para encontrar el polinomio interpolador para n puntos, si hacemos uso de la [[Matriz de Vandermonde]], tendriamos que resolver el sistema de ecuaciones asociado. La gran ventaja del metodo de Lagrange es que no hay que resolver ningun sistema de ecuaciones lineales, ya que nos aprovechamos de una definicion particular de la estructura del polinomio interpolador.
Esta estructura tiene la siguiente forma con $n$ puntos:
$$\begin{align}
&p(x)=y_1L_1(x)+y_2L_2(x)+\cdots+ y_nL_n(x)\\
&\sum_{i=1}^n y_iL_i(x)
\end{align}$$
Donde $L_i(x)$ son funciones donde $L_i(x_i)=1$ y $L_i(x_j)=0$ con $i\neq j$. Esta definicion nos permite obtener $y_k$ cuando evaluamos a si manteniendo la condicion de $p(x_k) = y_k$:
$$p(x_k)=y_1\underbrace{L_1(x_k)}_\text{0}+y_2\underbrace{L_2(x_k)}_\text{0}+\cdots+ y_k\underbrace{L_k(x_k)}_\text{1}+\cdots+y_n\underbrace{L_n(x_k)}_\text{0}
$$
Las funciones $L_i(x)$ se contruyen definiendo las funciones $l_i(x)$ de la forma:
![[Pasted image 20221022232326.png]]
Es decir la productoria de la expresion $(x-x_k)$ menos $(x-x_i)$.
De esta forma nos aseguramos que $l_i$ evaluado en cualquier numero sea 0 menos en $x_i$.
Sin embargo si evaluamos en $x_i$ no necesariamente es $1$, y no es $0$ por construccion.
Entonces para cumplir que $L_i(x_i)=1$, realizamos el cuociente entre $l_i(x)$ y $l_i(x_i)$, luego:
![[Pasted image 20221022233142.png]]

Como el denominador es solo un producto de numeros, podemos precalcularlo para cada $L_i$, sin embargo el numerador debe ser evaluado en $x$ cada vez que se evalue el polinomio interpolador.
Esto conduce a las siguientes preguntas:
- Cuantas operaciones elementales se requieren para precalcular todos los denominadores de los $L_i$ para interpolar $n$ puntos?
	R: Si tenemos $n$ puntos entonces tenemos que descontar la operacion $x-x_i$, por lo que serian $n-1$ restas y $n-2$ multiplicaciones, por lo que en total es $n-1+n-2=2n-3$ operaciones elementales, es decir, de orden $O(n)$.
- Cuantas operaciones elementales elemetales se requieren para evaluar el polinomio interpolador con $n$ puntos considerando que ya precalculamos los denominadores?
	R:  De la misma forma, el evaluar el nominador al calcular el $L_i$, este toma $2n-3$ operaciones elementales. Ahora de acuerdo, a la definicion del polinomio interpolador $p(x)=\sum_{i=1}^n y_iL_i(x)$,
	esta evaluacion se realiza $n$ veces y realiza $n$ divisiones por lo que construir el polinomio interpolador toma $2n(2n-3)=4n^2-6n$ es decir de orden, $O(n^2)$. 