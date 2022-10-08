# Matrices

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
Se define el producto matriz $A\in\mathbb{R^{m\times n}}$ con el [[Vectores|vector]] $\vec{u}\in\mathbb{R^n}$ como:
![[Pasted image 20220822143949.png]]
##### Observaciones:
- El resultado del producto es un [[Vectores|vector]]
- Para que el producto tenga sentido se tiene que la cantidad de columnas de A tiene que ser igual a la cantidad de filas de u.
- La dimension del [[Vectores|vector]] resultante es la cantidad de filas de A.

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

Lo que corresponde simplemente como a una [[combinacion lineal]] de las columnas de $A$ ponderadas por los coeficientes de $u$, expresion bastante util para que sea algoritmizable.

La generalizacion del productor matriz-vector es el producto matriz-matriz. Considerar las matrices $A\in\mathbb{R^{m\times n}}$ y $B\in\mathbb{R^{m\times l}}$, entonces su producto es:
![[Pasted image 20220822152658.png]]

Donde C es calculada computando cada uno de sus vectores columna $c_i$ de la forma $c_i=Ab_i$, o sea el producto matrix-vector  de A y $b_i$.

## Propiedades
### Rango
El rango de una matriz $A$, o, column space corresponde al [[Espacios Vectoriales| espacio vectorial]] (conjunto de todos los vectores) generado por las columnas de $A$. Es decir, si todos los vectores columnas de $A$ son [[Combinacion lineal|linealmente independientes]] entre si, significa que la dimension de $A$ es la cantidad de vectores columna, es decir n, lo que corresponde al **column rank**.

El row space de $A$ corresponde al espacio generado por los vectores filas de $A$, es decir, Range($A^T$). Por lo tanto, el row rank sera la dimension del row space, es decir, el numeor de filas linealmente independientes.

Notar que el column rank y el row rank son siempre iguales, por lo que se llaman "rank".

Una matriz se dira full rank, si tiene el maximo rank posible, y sera el minimo entre sus dimensiones n y m.


### Nullspace
Se define el Nullspace de una matriz $A$ como el conjunto de vectores $x_i \in \mathbb{R}^n$, tales que:$$Ax=0$$
### Transpuesta
Se define el operador transpuesta de una matriz $A$ al alternar el orden de las filas y de las columnas de la forma:

![[Pasted image 20221001002112.png]]



### Inversa
Una matriz tiene inversa $A^{-1}$, si  y solo si, esta es cuadrada y es full rank. Y por lo tanto, $AA^{-1}=A^{-1}A=I$

### Determinante
El determinante de una matriz se obtiene recursivamente de la siguiente forma:
![[Pasted image 20221001003217.png]]

![[Pasted image 20221001003224.png]]

### Valores y vectores propios
Sea $A$ una matriz cuadrada y $v$ en $\mathbb{R}^n$ con $v\neq 0$. Si $A$, $V$ y $\lambda$  satisfacen:
$$Av=\lambda v$$
Entonces se dice que $\lambda$ es un valor propio de $A$ y $v$ es un vector propio de $A$.
Se le llama el polinomio caracteristico de $A$, al determinante $||A-\lambda I||$ y la ecuacion caracteristica $||A-\lambda I||= 0$.

Si la matriz $A$ es invertible y tiene valores propios $\lambda_i$ entonces los valores propios de $A^{-1}$ son $\frac{1}{\lambda_i}$, y los vectores son los mismos. 