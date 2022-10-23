# Metodo de Gauss Seidel

Corresponde a una pequeña variante del [[Metodo de Jacobi]], de la siguiente forma:$$\begin{align}
(L+D+U)(x)&=b\\
(L+D)x+Ux&=b\\
(L+D)x&=b-Ux\\
x&=(L+D)^{-1}(b- Ux)
\end{align}$$
Donde $L+D$ es una matriz triangular superior, por lo que podemos usar forward substitution para resolver el sistema de ecuaciones lineales en cada iteracion:$$\begin{align}
x_0&=\text{initial guess}\\
x_{n+1}&=(L+D)^{-1}(b- Ux_{n-1})
\end{align}$$
De igual manera que con el [[Metodo de Jacobi]], podemos reescribir el metodo en funcion de su vector residual:
![[Pasted image 20221020230327.png]]
Y además en funcion de una matriz $M$ se tiene que:
![[Pasted image 20221022182144.png]]
Que es util para revisar la [[Convergencia de metodos iterativos]].
