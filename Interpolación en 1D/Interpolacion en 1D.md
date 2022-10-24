>[!NOTE] Definicion
>Una función $y=p(x)$ interpola los datos $(x_1,y_1)\cdots (x_n,y_n)$ si para cada dato $i$ (punto) este pertenece a la curva. Es decir $p(x_i) = y_i$

En general la funcion $p(x)$ que interpola serán polinomios como se ve en la figura:
![[Pasted image 20221022185808.png]]

Una problema simple es interpolar 2 puntos, $(x_1,y_1), (x_2,y_2)$. En la práctica existen infinitos polinomios que interpolan esos puntos, sin embargo existe un unico polinomio que tiene grado minimo. En este caso, se puede observar que la opción sería una recta, pero el desafio radica en encontrar un polinomio con grado minimo que interpole una cantidad arbitraria de puntos.

![[Pasted image 20221022190718.png]]

Por ejemplo para interpolar con un polinomio de grado 2 los puntos anteriores se tiene que:
$$\begin{align}
p(x_1)=x_1^2+bx_1+c=y_1\\
p(x_2)=x_2^2+bx_2+c=y_2\\
\end{align}$$
Por lo que podemos realizar un [[Sistemas de Ecuaciones Lineales]]:
$$\begin{bmatrix}  
x_1 & 1 \\  
x_2 & 1  
\end{bmatrix}
\begin{bmatrix}  
b \\  
c 
\end{bmatrix}
=
\begin{bmatrix}  
 y_1-x^2 \\  
y_2-x^2 
\end{bmatrix}$$
El resolverlo nos dará los coeficientes que entregan el polinomio interpolador de grado 2.

El siguiente teorema muestra la unicidad de la interpolacion polinomial:
>[!NOTE] Unicidad de la interpolacion polinomial
>Sea $(x_1,y_1)\cdots (x_n,y_n)$ n puntos en el plano $\mathbb{R}^2$ con **distintos** $x_i$, entonces existe **sólo un** polinomio $p(x)$ de grado $n-1$ **o menor** que satisface $p(x_i) = y_i$.

Notar que si tenemos un  $x_i$ repetido, ya no estamos buscando una funcion, por lo que la teoria de interpolacion polinomial no aplica.
Utilizando lo anterior, una forma natural de encontrar el polinomio es utilizando la [[Matriz de Vandermonde]], pero no es recomendable su uso para una cantidad de puntos alta. Para estos casos podemos utilizar:
- [[Interpolación de Lagrange]]
- [[Interpolación Baricentrica]]