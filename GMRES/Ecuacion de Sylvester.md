Considerar la siguiente ecuacion:
$$
AX+XB=C
$$
Donde $X, A, C, B \in R^{n\times n}$, y se necesita encontrar $X$. Notar que aplicar  LU ni utilizar un algoritmo iteratio no funciona ya no es la forma clasica $Ax=b$. 
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
Por lo que utilizar PALU es muy costoso, nos quedariamos sin memoria.

Es por esta razon que es recomendable utilizar [[GMRes]] .