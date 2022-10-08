# Factorizacion $PA=LU$

La [[Factorizacion LU]] es bastante practica en el sentido en que el lado derecho del sistema no cambia al momento de resolverlo. Esto implica, que podemos resolver sistemas de ecuaciones donde solo cambia el lado derecho, sin necesidad de realizar operaciones demas con la matriz $A$.
Sin embargo, hasta ahora se ha supuesto que siempre existe la factorizacion $LU$ de una matriz, e incluso que esta funciona bien, lo que no siempre es el caso.
Considerar la matriz $\begin{bmatrix}  0 & 2 \\ 3 & 4 \end{bmatrix}$, esta no tiene una factorizacion $LU$ dado que tiene un 0 en el primer pivote y no existe un numero multiplicado por 0 que haga el 3 se vaya en la segunda fila.

Otra desventaja, es que $LU$ induce grandes errores en la computacion, por ejemplo, considerar $\delta = 10 ^{-20}$, es decir un numero menor a [[Machine Epsilon]].$$
\begin{bmatrix}  \delta & 1 \\ 1 & 2 \end{bmatrix}\begin{bmatrix}  x_1  \\ x_2 \end{bmatrix}=\begin{bmatrix}  1\\ 4  \end{bmatrix}
$$
 Cuya factorizacion $A=LU$, es en doble precision: $$\begin{bmatrix}  1 & 0 \\ 10^{20} & 1 \end{bmatrix}\begin{bmatrix}  10^{-20} & 1 \\ 0 & -10^{20} \end{bmatrix}$$
 Notar que como se trabaja en doble precision, $2 << -10^{20}$, por lo que perdimos significancia. Al hacer el producto queda:
 $$\begin{bmatrix} 10^{-20} & 1 \\ 1 & 0 \end{bmatrix}$$Lo cual es diferente a la matriz original. Resolviendo el sistema y considerando double precision se tiene que:
 $$\begin{bmatrix} 0 \\ 1 \end{bmatrix}$$
Lo cual es alejado de la solucion. De hecho obteniendo la factorizacion $LU$ de $A$ de forma simbolica se tiene que:$$A=\begin{bmatrix}  1 & 0 \\ \delta^{-1} & 1 \end{bmatrix}\begin{bmatrix}  \delta & 1 \\ 0 &2 -\delta^{-1} \end{bmatrix}$$
Claramente el 2 no afecta en nada al numero $10^{20}$ en doble precision por lo que solo se almacena $10^{20}$. Esto es lo que hace que el producto $LU$ no sea igual a la matriz $A$ original.
Ahora considerar que alternamos las filas de la matriz, es decir, $R1 = R2$ y $R2=R1$,  o equivalentemente, multiplicamos el sistema de ecuaciones por $P$:$$\begin{align}
\begin{bmatrix}  1 & 2\\ \delta & 1  \end{bmatrix}\begin{bmatrix}  x_1  \\ x_2 \end{bmatrix}=\begin{bmatrix}  4\\ 1 \end{bmatrix}
\end{align}$$$$\begin{align}
Ax&=b\\
PAx&=Pb
\end{align}$$
Este alternamiento de filas, es lo mismo que multiplicar $A$ por una matriz Identidad $P$ con las filas que cambiamos, es decir, una matriz de permutacion. La factorizacion simbolica $LU$ de la matriz $PA$,  es entonces:
$$A=\begin{bmatrix}  1 & 0 \\ \delta & 1 \end{bmatrix}\begin{bmatrix}  1 & 2 \\ 0 &1 -2\delta \end{bmatrix}$$
En doble precision, como $1>>>2\delta$, se tiene que:
$$A=\begin{bmatrix}  1 & 0 \\ 10^{-20} & 1 \end{bmatrix}\begin{bmatrix}  1 & 2 \\ 0 &1 \end{bmatrix}$$
Resolviendo el sistema de ecuaciones asociado se tiene la siguiente aproximacion:
$$x_a=\begin{bmatrix}  2 \\  1 \end{bmatrix}$$
Lo que corresponde a una aproximacion  mucho mejor que la obtenida.
En particular la matriz P, al multiplicarla por ambos lados lo unico que hace es un cambio de filas, que redujo significativamente el error numerico.
En particular la idea, es dejar en la diagonal de la matriz el **maximo coeficiente en valor absoluto**. Es decir, antes de realizar operaciones fila, se debe revisar que el pivote sea mayor en valor absoluto, que todos los elementos hacia abajo en la columno. Si no, realizamos la permutacion de filas.
Una vez que obtengamos las matrices $P$, $L$ y $U$ podemos resolver el sistema de ecuaciones de la siguente forma:
1. Multiplicar por $P$ a la izquierda de ambos lados:$$PAx=Pb$$ Luego reemplazamos $PA=LU$,$$LUx=Pb$$
3. Resolvemos $Ly=Pb$ con forward substitution.
4. Resolvemos $Ux=y$ con [[Backward substitution]].