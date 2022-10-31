# Factorizacion LU
En [[Eliminacion Gaussiana]] pasamos de un sistema $A\vec{x}=\vec{b}$, a uno $U\vec{x}=\hat{b}$, donde $U$ es una matriz triangular superior (o inferior) y $\hat{b}$ corresponde al lado derecho modificado. O sea modificamos la matriz original $A$ y el lado derecho $\vec{b}$ a partir de operaciones fila. Esto quiere decir si queremos solucionar otro sistema de ecuaciones donde solo cambia el lado derecho, tendriamos que ejecutar nuevamente eliminacion gaussiana, la cual tiene complejidad temporal $m(\frac{2}{3}n^3)$ para $m$ sistemas de ecuaciones distintos.
La idea de la factorizacion LU, es "desacoplar" el lado derecho de la ecuacion con la matriz $A$.
Cuando realizamos la operaciones filas en eliminacion gaussiana, basicamente estamos "multiplicando" por la inversa de una matriz $L$, es decir:
$$L^{-1}A\vec{x}=L^{-1}\vec{b}$$

Donde:$$\begin{align}
L^{-1}A&=U\\
L^{-1}\vec{b}&=\hat{b}
\end{align}$$
De la primera ecuacion se desprende que:
$$
A=LU
$$
Ya sabemos que $U$ es una matriz triangular superior, por lo que resta saber que forma tiene $L$. Para obtener $L$ sean las siguientes aseveraciones:

Se dice que una matriz $L$ es triangular inferior si sus coeficientes  satisfacen $l_{ij}=0$ , para $i>j$.
Se dice que una matriz $U$ es triangular superior si sus coeficientes satisfacen $u_{ij}=0$ para $i<j$.

1. Sea $L_{ij}(-c)$ una matriz triangular inferior con puros 1s en la diagonal y en la posicion $(i,j)$ se esta el valor $-c$. Entonces $L_{ij}(-c) A$  representa la operacion fila restar la fila $j$ multiplicada por $c$  a la fila $i$. $R_i-cR_j$. 
$$\begin{align}A &=\begin{bmatrix}  
a_{11} & a_{12} \\  
a_{21} & a_{22} 
\end{bmatrix}\\\\ 
L_{21}(-c)A&=
\begin{bmatrix}  
1 & 0 \\  
-c & 1 
\end{bmatrix}
\begin{bmatrix}  
a_{11} & a_{12} \\  
a_{21} & a_{22} 
\end{bmatrix}=\begin{bmatrix}  
a_{11} & a_{12} \\  
a_{21} -ca_{11} & a_{22} 
\end{bmatrix}\end{align}$$

Lo que implica que podemos representar operaciones fila como el producto de una matriz, es decir una [[Transformacion Lineal]]
2. La inversa de $L_{ij}(-c)$ es $L_{ij}(c)$:$$\begin{bmatrix}  
1 & 0 \\  
-c & 1 
\end{bmatrix} \begin{bmatrix}  
1 & 0 \\  
c & 1 
\end{bmatrix}=\begin{bmatrix}  
1 & 0 \\  
-c+c & 1 
\end{bmatrix}=\begin{bmatrix}  
1 & 0 \\  
0 & 1 
\end{bmatrix}=I$$
3. La siguiente ecuacion es cierta: 
$$\begin{bmatrix}  
1 & 0 & 0\\  
c_1 & 1  & 0\\
0 & 0  & 1
\end{bmatrix}
\begin{bmatrix}  
1 & 0 & 0\\  
0 & 1  & 0\\
c_2 & 0  & 1
\end{bmatrix}
\begin{bmatrix}  
1 & 0 & 0\\  
0 & 1  & 0\\
0& c_3  & 1
\end{bmatrix}
=
\begin{bmatrix}  
1 & 0 & 0\\  
c_1 & 1  & 0\\
c_2& c_3  & 1
\end{bmatrix}
$$
Como ejemplo sea ahora la siguiente matriz $A$:
$$A=\begin{bmatrix}  
1 & 2 & -1\\  
2 & 1  & -2\\
-3 & 1  & 1
\end{bmatrix}$$
Para hacerla triangular superior, se necesitan 3 operaciones fila (hacer 0 los dos numeros de abajo del 1 de la primera columna, y hacer 0 el numero abajo del 1 en la segunda). De acuerdo a la primera aseveracion se tiene que:
 $$\begin{bmatrix}  
1 & 0 & 0\\  
0 & 1  & 0\\
0 & \frac{7}{3}  & 1
\end{bmatrix}
\begin{bmatrix}  
1 & 0 & 0\\  
0 & 1  & 0\\
3 & 0  & 1
\end{bmatrix}
\begin{bmatrix}  
1 & 0 & 0\\  
-2 & 1  & 0\\
0& 0  & 1
\end{bmatrix}

\begin{bmatrix}  
1 & 2 & -1\\  
2 & 1  & -2\\
-3 & 1  & 1
\end{bmatrix}=
\begin{bmatrix}  
1 & 2 & -1\\  
0 & -3  & 0\\
0 & 0  & -2
\end{bmatrix}
$$
Lo que corresponde aplicar las siguientes operaciones filas a $A$:
$$
\begin{align}
R2&=R2-2R1\\
R3&=R3+3R1\\
R3&=R3+\frac{7}{3}R2
\end{align}
$$
Y se representa algebraicamente como:
$$
L_{32}(\frac{7}{3})L_{31}(3)L_{21}(-2)A=U
$$

Despejando $A$:
$$
\begin{align}
L_{32}(\frac{7}{3})L_{31}(3)L_{21}(-2)A&=U\\
L_{32}^{-1}(\frac{7}{3})L_{32}(\frac{7}{3})L_{31}(3)L_{21}(-2)A&=L_{32}^{-1}(\frac{7}{3})U\\
L_{21}(-2)A&=L_{31}^{-1}(3)L_{32}^{-1}(\frac{7}{3})U\\
A&=L_{21}^{-1}(-2)L_{31}^{-1}(3)L_{32}^{-1}(\frac{7}{3})U\\
\end{align}
$$

De acuerdo a la aseveracion 2:
$$
\begin{align}
A&=L_{21}(2)L_{31}(-3)L_{32}(-\frac{7}{3})U\\
\end{align}
$$
Y por lo tanto:
 $$A=
\begin{bmatrix}  
1 & 0 & 0\\  
2 & 1  & 0\\
0& 0  & 1
\end{bmatrix} 
\begin{bmatrix}  
1 & 0 & 0\\  
0 & 1  & 0\\
-3 & 0  & 1
\end{bmatrix}
\begin{bmatrix}  
1 & 0 & 0\\  
0 & 1  & 0\\
0 & -\frac{7}{3} &1
\end{bmatrix}
\begin{bmatrix}  
1 & 2 & -1\\  
0 & -3  & 0\\
0 & 0  & -2
\end{bmatrix}
$$
$$
A= \begin{bmatrix}  
1 & 0 & 0\\  
2 & 1  & 0\\
-3 & -\frac{7}{3} &1
\end{bmatrix}
\begin{bmatrix}  
1 & 2 & -1\\  
0 & -3  & 0\\
0 & 0  & -2
\end{bmatrix}
$$
Es decir $A=LU$, donde $L$ es una matriz triangular **inferior** y $U$ una matriz triangular superior. 
>[!tip] Basicamente la matriz $L$ almacena los coeficientes que utilizamos al momento de realizar las operaciones filas para hacer $U$ triangular superior!

Es decir, lo unico que requerimos para hacer la  factorizacion $LU$ es almacenar convenientemente los coeficientes utilizados en las operaciones filas de la eliminacion gaussiana, es decir el coeficiente $c$ de la forma $R_i= R_i - cR_j$.


## Resolver sistemas con $A=LU$

Como el sistema original era $Ax=b$ ahora podemos reemplazar de la forma
$LU\vec{x}=\vec{b}$. Notese que podemos hacer un cambio de variable donde $\vec{c}=U\vec{x}$, y entonces: $$L\vec{c}=\vec{b}$$
Lo que sigue siendo un sistema de ecuaciones!. En este caso, ahora $\vec{c}$ es nuestra incognita y solo basta resolver:
![[Pasted image 20220927223445.png]]

Esto se resuelve usando **forward substitution**, que es el analogo a [[Backward substitution]], pero empezando desde "arriba hacia abajo", es decir, su algoritmo es:
```python
def forward_substitution(B,n,b):
	#iterate rows from the original matriz, rows and columns are considered starting from index 1
    for i in range(1,n):
	    # iterate rows from the original matrix
        for j in range(1, i):
	        ui += B[i,j]*b[i]
        
        ci = b[i] - u_i
    return B
```

Lo que toma $n^2$ operaciones igualmente.

Una vez resuelto el sistema podemos, tenemos el vector $\vec{c}$, por lo que recordar que $\vec{c}=U\vec{x}$, como tenemos una incognita este puede ser resuelto!, y este es no mas que una [[Backward substitution]], de la siguiente forma:
![[Pasted image 20220927231453.png]]

Como el lado derecho, es conocido, basta con resolver el sistema para encontrar el $\vec{x}$ , que es lo queriamos encontrar todo este tiempo.

## Algoritmo
Finalmente todo este procedimiento se puede explicar como:
![[Pasted image 20220927231629.png]]

