# Metodo de Jacobi

Una matriz $A$ puede ser descompuesta de muchas formas, una de esta es:
$$A=L+D+U$$
Donde: 
-$L$ es una matriz que contiene todos los elementos bajo la diagonal de A
-$D$ contiene los elementos de la diagonal de A
-$U$ contiene los elementos sobre la diagonal de $U$.

>[!WARNING] $L$ y $U$ son distintos a aquellos de la factorizacion $A= LU$!

![[Pasted image 20221007223801.png]]

Sea el siguiente sistema de ecuaciones lineales:
$$\begin{align}
Ax=b
\end{align}$$
Tomando la factorizacion anterior:$$\begin{align}
(L+D+U)(x)&=b\\
Lx+Dx+Ux&=b\\
Dx&=b-Lx-Ux\\
Dx&=b-(L+U)x \quad /D^{-1} \\
x&=D^{-1}(b-(L+ U)x)

\end{align}$$
Por lo que tendriamos ya una expresion para el x !. 
Notemos que $D^{-1}$ es facil de calcular ya que la inversa de $D$ es simplemente la inversa de los elementos de la diagonal principal, $D^{-1}=\frac{1}{D}$.
La expresion obtenida no es más que una [[Iteracion de punto fijo]], donde el lado derecho no es más que $G(\vec{x})$.
$$\begin{align}
x_0&=\text{initial guess}\\
x_{n+1}&=D^{-1}(b-(L+ U)x_n)
\end{align}$$
Esta expresion puede ser escrita de diferentes maneras:
![[Pasted image 20221007232322.png]]

