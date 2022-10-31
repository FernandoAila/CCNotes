Recordar las representaciones de los [[Metodos Iterativos]] expuestos:
![[Pasted image 20221022182408.png]]
Considerar la tercera representación de cualquier metodo en base a una matriz $M$ y un vector $\hat{b}$.
Con dos iteraciones se tiene que:
![[Pasted image 20221022182842.png]]

Restando la ecuacion $2$ con la ecuacion $1$:
![[Pasted image 20221022182911.png]]
Si aplicamos cualquier norma vectorial, por ejemplo, la norma 2, obtenemos:
![[Pasted image 20221022183041.png]]
El lado izquierdo corresponde al error $e_{n+1}$  en la n+1 iteracion, por lo que:
$$\begin{align}e_{n+1}&=||x_{n+2}-x_{n+1}|| \\ 

&\leq ||M|| x_n
\end{align}$$
Claramente si $M\leq1$, entonces el metodo reducirá el error.

# Matriz diagonal Dominante

>[!NOTE] Definicion
>La matriz $A$ cuadrada $n\times n$ es estrictamente diagonal dominante, si en todas sus filas, el valor en  la diagonal principal en valor absoluto, es mayor que la suma de los otros valores de la fila en valor absoluto

>[!NOTE] Definicion
>Si $A$ es diagonal dominante se cumple que:
>- $A$ es una matriz no singular
>- Los metodos de [[Metodo de Gauss Seidel||Gauss Seidel]] y [[Metodo de Jacobi|Jacobi]] convergen a una solucion unica de $Ax=b$.



