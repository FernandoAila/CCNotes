# Algebra Lineal


## Vectores y Matrices
Un vector $\vec{u}$  columna de dimensión finita n corresponde simplemente a un arreglo unidimensional de numeros de las siguiente forma:
$$
\vec{u} =
\begin{bmatrix}
x_1\\
x_2\\
\vdots \\
x_n
\end{bmatrix}
\quad \text{Vector Columna}
$$
Si aplicamos el operador transpuesta $T$ resulta en un vector Fila:
$$
u^T =
\begin{bmatrix}
x_1, x_2, \cdots,x_n
\end{bmatrix}
\quad \text{Vector Fila}
$$
Es importante tener la representacion adecuada ya que si queremos, por ejemplo, para obtener el producto punto (o interno) es necesario que ambos vectores tengan la misma dimension. La situacion ocurre de manera similar cuando multiplicamos una matriz por un vector, ya que se requiere que exista compatibilidad en sus dimensiones. Es por esta razón que podemos cosiderar a un vector columna de dimension n como una matriz de dimension $1 \times n$ y un vector fila como una matrix de dimension $n \times 1$


Se define una matriz de dimension finita $A\in\mathbb{R}^{m \times n}$, como un arreglo bidimensional de numeros:

$$
A=
\begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n}\\
a_{21} & a_{22} & \cdots & a_{2n}\\
\vdots & \vdots & \ddots & \vdots\\ 
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix}
$$
### Producto Matriz - Vector
Se define el producto matriz $A\in\mathbb{R^{m\times n}}$ con el vector $\vec{u}\in\mathbb{R^n}$ como:
![[Pasted image 20220822143949.png]]
##### Observaciones:
- El resultado del producto es un vector
- Para que el producto tenga sentido se tiene que la cantidad de columnas de A tiene que ser igual a la cantidad de filas de u.
- La dimension del vector resultante es la cantidad de filas de A.

Podemos entonces entender una matriz como una coleccion de vectores de la forma:
![[Pasted image 20220822145802.png]]

Por que:
$$
\begin{bmatrix}
u_1 \cdot a_{11}\\
u_1 \cdot a_{21}\\
\vdots \\
u_1 \cdot a_{m1}
\end{bmatrix}
+
\begin{bmatrix}
u_2 \cdot a_{12}\\
u_2 \cdot a_{22}\\
\vdots \\
u_2 \cdot a_{m2}
\end{bmatrix}
+
\cdots
+
\begin{bmatrix}
u_n \cdot a_{1n}\\
u_n \cdot a_{2n}\\
\vdots \\
u_n \cdot a_{mn}
\end{bmatrix}
=
\begin{bmatrix}
u_1 \cdot a_{11}+u_2 \cdot a_{12}+\cdots + u_n \cdot a_{1n}\\
u_1 \cdot a_{21}+u_2 \cdot a_{22}+\cdots + u_n \cdot a_{2n}\\
\vdots \\
u_1 \cdot a_{m1}+u_2 \cdot a_{m2}+\cdots + u_n \cdot a_{mn}\\
\end{bmatrix}

$$

Lo que corresponde simplemente como a una combinacion lineal de las columnas de $A$ ponderadas por los coeficientes de $u$, expresion bastante util para que sea algoritmizable.

La generalizacion del productor matriz-vector es el producto matriz-matriz. Considerar las matrices $A\in\mathbb{R^{m\times n}}$ y $B\in\mathbb{R^{m\times l}}$, entonces su producto es:
![[Pasted image 20220822152658.png]]

Donde C es calculada computando cada uno de sus vectores columna $c_i$ de la forma $c_i=Ab_i$, o sea el producto matrix-vector  de A y $b_i$.