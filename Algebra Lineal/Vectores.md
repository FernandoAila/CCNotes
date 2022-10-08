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
Es importante tener la representacion adecuada ya que si queremos, por ejemplo, para obtener el producto punto (o interno) es necesario que ambos vectores tengan la misma dimension. 
La situacion ocurre de manera similar cuando multiplicamos una matriz por un vector, ya que se requiere que exista compatibilidad en sus dimensiones. Es por esta razón que podemos considerar a un vector columna de dimension n como una [[Matrices|matriz]] de dimension $1 \times n$ y un vector fila como una matrix de [[Matrices|matriz]]  $n \times 1$.


Se dice que dos vectores $q_i$ y $q_j$ son ortonormales, si su [[Normas vectoriales|norma]] es 1 y el [[Producto Interno]], es decir $<q_i,q_j>$, es nulo, es decir, $<q_i,q_j>=0$.

