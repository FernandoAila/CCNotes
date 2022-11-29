Considerar la siguiente ecuacion:
$$
AX+XB=C
$$
Donde $X, A, C, B \in R^{n\times n}$, y se necesita encontrar $X$. Notar que aplicar  LU ni utilizar un algoritmo de iterativo no funciona ya no es la forma clasica $Ax=b$. 
Para esto considerar la operacion $vec(A)$ la cual:
$$
vec(\begin{bmatrix} a & b\\ c&d  \end{bmatrix})=\begin{bmatrix} a\\  b\\ c\\d  \end{bmatrix}
$$
Esto es util ya que entrega la siguiente identidad:
$$
vec(ABC)=(C^T\otimes A) vec(B)
$$
Donde $\otimes$ es el producto de Kronecker definido como:

$$
A\otimes B = 
\begin{bmatrix}a_{11}B & a_{12}B  &\cdots  &a_{1m} B\\
a_{21}B & a_{22}B  &\cdots & a_{2m} B \\
\vdots & \vdots  &\cdots & \vdots \\
a_{n1}B & a_{n2}B  &\cdots & a_{nm} B
\end{bmatrix}
$$
Usando esta identidad reescribimos la ecuacion de Sylvester como:

$$
AXI+IXB=C
$$
Reemplazando:
$$
\begin{align}
vec(AXI + XBI) = vec(C)\\
vec(AXI) + vec(XBI) = vec(C)\\
(I\otimes A)vec(x)+ (B^T\otimes I)vec(X) =vec(C)\\
 ((I\otimes A) + (B^T\otimes I))vec(X) = vec(C)\\\\
\end{align}
$$
Lo que es un sistema de ecuaciones lineales de la forma $Ax=b$ con $A=((I\otimes A) + (B^T\otimes I))$
$x=vec(x)$ y $b=vec(c)$.
Notar que:
- $A\in \mathbb{R}^{n^2 \times n^2}$
- $x\in \mathbb{R}^{n^2}$
- $b\in \mathbb{R}^{n^2}$


## Alternativa

Otra alternativa para resolver la ecuacion de Sylvester es usar una iteracion de punto fijo **matricial**, es decir:
$$
\begin{align*}
X^{0}=\text{initial guess}\\
X^{n+1}=A^{-1}(C-X^{n}B)
\end{align*}
$$

Por otro lado considerar lo siguiente si realizamos la forma matricial
de la ecuacion de sylvester:

![[Pasted image 20221128154609.png]]


![[Pasted image 20221128154630.png]]

Si sumamos los terminos a ambos lados:
![[Pasted image 20221128154712.png]]

Ahora podemos igualar  es decir, sea, $\hat{A}$ la matriz del lado derecho y $\hat{B}$ la del lado izquierdo, esto quiere decir que, $a_{11}=b_{11},a_{12}=b_{1,2},a_{21}=b{21},a_{22}=b_{22}$.
Lo que resulta en:

![[Pasted image 20221128155003.png]]

Lo que lo podemos reescribir en un sistema de ecuaciones!

![[Pasted image 20221128155024.png]]

Ahora el desafio es realizar [[GMRes]] sin construir la matriz $A$ presentada ya que es de dimensión $n\times n$, por lo que requiere mucha memoria para ser almacenada.
Por esta razon definimos la función $afun$ en el algoritmo de [[GMRes]], cuya funcion radica en recibir un vector y retornar el producto matriz-vector.

![[Pasted image 20221128161419.png]]

La interpretacion original de $afun$ es sencilla pero trae una desventaja de que tenemos que conocer la matriz $A$ original, osea, lo que estamos evitando!.

```python
def afun(v):
	# A es una matriz asociada a la forma tradicional Ax=b
	# v es el vector de entrada que será x_0 y luego qk en GMres
	out = A @ v
	return 
```


La version matrix-free se basa en la seccion del lado izquierdo de la ecuacion matricial propuesta antes de construir el sistema de ecuaciones.

```python
def afun_1(v):
	# pasamos de v de un vector n^2 a una matriz X de dimension n x n
	X = np.reshape(v,(n,n),order="F")
	# recordames la ecuacion de sylvester AX+XB=C
	out = A @ X + X @ B
	return out.flatten('F')
```
