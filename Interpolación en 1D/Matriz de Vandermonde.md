Sabemos que para interpolar $2$ puntos podemos utilzar el siguiente polinomio:
$$p(x)=a_0+a_1x$$
Podemos encontrar los coeficientes $a_0$ y $a_1$ resolviendo el siguiente sistema de ecuaciones:
$$\begin{align}
p(x_1)&=a_0+a_1x_1\\
p(x_2)&=a_0+a_1x_2
\end{align}$$
Donde $a_0$ y $a_1$ son las incognitas, esto en su forma matricial es:$$\begin{bmatrix}  
1 & x_1 \\  
1 & x_2  
\end{bmatrix}
\begin{bmatrix}  
a_0 \\  
a_1  
\end{bmatrix}
=
\begin{bmatrix}  
 y_1 \\  
y_2  
\end{bmatrix}$$
Para interpolar tres puntos, de la misma forma, ahora incrementamos el grado del polinomio a 3:
$$\begin{bmatrix}  
1 & x_1 & x_1^2 \\  
1 & x_2 &x_2^2 \\
1 & x_3 & x_3^2
\end{bmatrix}
\begin{bmatrix}  
a_0 \\  
a_1  \\
a_2
\end{bmatrix}
=
\begin{bmatrix}  
 y_1 \\  
y_2 \\
y_3
\end{bmatrix}$$

En particular a medidad que avanzamos en las columnas aumenta el exponente.
Si extendemos este resultado a n puntos:
$$\begin{bmatrix}  
1 & x_1 & x_1^2 & \cdots & x_1^{n-1}  \\  
1 & x_2 &x_2^2 & \cdots & x_2^{n-1} \\
1 & x_3 & x_3^2 & \cdots & x_2^{n-1}\\
\vdots & \vdots & \vdots & \cdots & \vdots\\
1 & x_n & x_n^2 & \cdots & x_n^{n-1}\\
\end{bmatrix}
\begin{bmatrix}  
a_0 \\  
a_1  \\
a_2  \\
\vdots \\
a_{n-1}
\end{bmatrix}
=
\begin{bmatrix}  
 y_1 \\  
y_2 \\
y_3 \\
\vdots \\
y_n

\end{bmatrix}$$

![[Pasted image 20221022224615.png]]
La matriz $A$ es llamada la **Matriz de Vandermonde** denotada con la letra $V$.
El determinante de esta matriz es conocido y equivale a:
![[Pasted image 20221022225020.png]]

Notar que si tenemos un $x_i$ repetido, entonces $x_i=x_j$, la productoria es 0 por lo que el determinante es 0 y la matriz singular, por lo que existen infinitas soluciones o ninguna solucion.

Una de las desventajas de la matriz de Vandermonde es que está muy mal condicionada, es decir, su [[Numero de condicion]], $\kappa >> 1$. Por lo que no es recomendable usarla cuando el numero de puntos es alto.