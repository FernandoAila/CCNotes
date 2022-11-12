Una desventaja que poseen las [[Ecuaciones Normales]] es que requiere calcular el producto $A^TA$ o $A^*A$ lo que es costoso en terminos de operaciones elementales y puede generar [[Perdida de la Importancia]].

Surge la pregunta, de como obtener el $\overline{x}$ no utilizando el algoritmo de las [[Ecuaciones Normales]], donde la factorizacion $QR$ resuelve esta tarea.

A difirencia de la [[Factorizacion LU]], la factorizacion $QR$ impone la siguiente estructura:
$$A=QR$$

Donde $Q$ es una [[Matrices Unitarias|matriz unitaria]]  y $R$ es una triangular superior. En particular $Q$ las columnas de $Q,$ $q_i$, generan el mismo subespacio que las columnas de $A$, $a_i$.
Recordar algunas propiedades de las matrices unitarias:
- $||Q\vec{x}||_2=||\vec{x}||_2$ para un vector $\vec{v}$, es decir $Q$ no afecta la norma $2$ de un vector
- $|\lambda|=1$, donde $\lambda$ es un valor propio de $Q$.
- $Q^{-1}=Q^*$, o sí $Q \in \mathbb{R}^{m\times n}$ entonces $Q^{-1}=Q^{T}$, lo que es util al resolver sistema de ecuaciones lineales $Q\vec{x}=\vec{b}$, ya que $\vec{x}=Q^{-1}\vec{b}=Q^{T}\vec{b}$   


La [[Ortonormalizacion de Gram-Schmidt]] nos entrega la factorizacion $QR$ de una matriz $A$. Donde a partir de las columnas de $A$ va construyendo columna a columna la matriz $Q$ y coeficiente a coeficiente la matriz triangular superior $R$.

Existen dos variantes de la factorizacion $QR$  para la matriz $A$:
- La factorizacion $QR$ reducida, $\hat{Q}\hat{R}$.
- La factorizacion $QR-full$ , $QR$.

Ambás describen a la matriz $A$ de la misma forma:
$$A=\hat{Q}\hat{R}=QR$$

La diferencia es que $\hat{Q}$ es de $m\times n$ y $\hat{R}$  es de $n\times n$ , mientras que en la factorizacion full $Q$  es de $m\times m$ y $R$ es de $m\times n$.

Se cumple que:
$$Q=[\hat{Q},\check{Q} ]$$
$$
R=\begin{bmatrix}
\hat{R}\\
0
\end{bmatrix}


$$
Donde $\check{Q} =[q_{n+1},\cdots, q_{m}]$ lo que quiere decir que las primeras $n$ columnas de $Q$ corresponden a $\hat{Q}$ y las siguientes $m-n$ columnas corresponden $\check{Q}$.
Por otro lado $\hat{R}$ contiene las primeras $n$ filas de $R$ mientras que la matriz nula $0$ (que contiene vectores nulos) corresponde a las restantes.


# Ventaja de la factorizacion $A=QR$

Si bien las [[Ecuaciones Normales]] nos entregan el sistema de ecuaciones lineales que minimiza el error cuadratico, este requiere resolver  $A^TA\overline{x}=A^T\boldsymbol{\vec{b}}$.
Si calculamos el numero de condicion $\kappa$ este es:
$$
\kappa_2(A)=||A||_2||A^{\dagger}||_2=\frac{\sigma_1}{\sigma_2}
$$

Al multiplicar una $A^{T}A$ tendremos una nueva matriz, es decir:
$$
\kappa_2(A)=||A^TA||_2||(A^TA)^{-1}||_2=\frac{\sigma_1^2}{\sigma_2^2}=(\frac{\sigma_1}{\sigma_2})^2
$$

Es decir duplica el numero de condicion $\kappa$!. Por lo que no es muy bueno para la computación.

# Utilizacion de la Factorizacion $A=QR$

¿Como usamos la factorizacion $A=QR$ de forma que minimize el error cuadrado?

Retornando al problema inicial de
$$Ax=b$$

Consideremos una factorizacion $QR$ full de $A$ y la reemplazamos:

$$\begin{align}
Ax&=b\\
QRx&=b
\end{align}$$

Podemos utilizar [[Ecuaciones Normales]] de la forma:
$$\begin{align}
Ax&=b\\
A^TA\overline{x}&=A^Tb\\
(QR)^T(QR)\overline{x}&=(QR)^Tb\\
R^TQ^TQR\overline{x}&=R^TQ^Tb\\
R^TR\overline{x}&=R^TQ^Tb
\end{align}$$

Como $Q$ es una [[Matrices Unitarias]] se cumple que  $QQ^T=I$.
Recordando las versiones full y reducidas de las matrces $Q$ y $R$ :

$$
\begin{align}
[\hat{R}^T, 0^T]\begin{bmatrix}
\hat{R}\\
0
\end{bmatrix}
\overline{x}&=[\hat{R}^T, 0^T]\begin{bmatrix}
\hat{Q}^T\\
\check{Q}^T
\end{bmatrix}
b\\
\hat{R}^TR \overline{x}+ 0^T0
\overline{x}&=[\hat{R}^T, 0^T]\begin{bmatrix}
\hat{Q}^Tb\\
\check{Q}^Tb
\end{bmatrix}\\
R^TR\overline{x}&=R^T\hat{Q}^Tb+0^T\check{Q}^Tb\\
R^TR\overline{x}&=R^T\hat{Q}^Tb\\
\hat{R}\overline{x}&=\hat{Q}^Tb
\end{align}
$$

De hecho el valor minimo explicito del error  es obtenido como:
$$\begin{align}
\min_{x\in R^n}||b-Ax||_2^2&=||b-A\overline{x}||_2^2\\
&=||\check{Q}b||_2^2
\end{align}$$




# Ejemplo


Sea el siguiente sistema de ecuaciones:
$$\underbrace{\begin{bmatrix}
1 & -4 \\
2 & 3  \\
2 &2
\end{bmatrix}}_{A}
\begin{bmatrix}
x_1\\
x_2
\end{bmatrix}
=
\underbrace{\begin{bmatrix}
-3\\
15\\
9\\
\end{bmatrix}}_b
$$


Para encontrar la factorizacion $QR$ de $A$ tenemos que realizar la [[Ortonormalizacion de Gram-Schmidt]] es decir:
$$
[a_1,a_2]=[q_1,q_2]
\begin{bmatrix}
r_{11} & r_{12}\\
0 & r_{22}
\end{bmatrix}
$$
$$
\begin{align}
a_1&=r_{11}q_1\\
||a_1||_2&=r_{11}=\sqrt{(1^2+2^2+2^2)}=\sqrt{9}=3\\
q_1&=
\begin{bmatrix}
\frac{1}{3}\\
\frac{2}{3}\\
\frac{2}{3}
\end{bmatrix}
\end{align}
$$
$$
\begin{align}
a_2&= r_{12}q_1+r_{22}q_2\\
r_{12} &=q_1^T a_2 = \begin{bmatrix}
\frac{1}{3} &
\frac{2}{3} &
\frac{2}{3}
\end{bmatrix}
\begin{bmatrix}
-4\\
3\\
2
\end{bmatrix} = 

\frac{-4}{3} +
2 +
\frac{4}{3} = 2\\
r_{22}&=||a_2-r_{12}q_1||_2
= \begin{bmatrix}
-4\\
3\\
2
\end{bmatrix}-2\begin{bmatrix}
\frac{1}{3}\\
\frac{2}{3}\\
\frac{2}{3}
\end{bmatrix}=
||\begin{bmatrix}
\frac{-14}{3}\\
\frac{5}{3}\\
\frac{2}{3}
\end{bmatrix}||_2
=5\\
q_2 &= \frac{a_2-r_{12}q_1}{5} = \frac{1}{5}\begin{bmatrix}
\frac{-14}{3}\\
\frac{5}{3}\\
\frac{2}{3}
\end{bmatrix} =\begin{bmatrix}
\frac{-14}{15}\\
\frac{1}{3}\\
\frac{2}{15}
\end{bmatrix}
\end{align}
$$

Lo que resulta en la factorizacion $QR$:
$$\begin{bmatrix}
1 & -4 \\
2 & 3  \\
2 &2
\end{bmatrix} = \begin{bmatrix}
\frac{1}{3} & \frac{-14}{15}\\
\frac{2}{3} & \frac{1}{3}\\
\frac{2}{3} & \frac{2}{15}
\end{bmatrix}
\begin{bmatrix}
3 & 2\\
0 & 5\\
\end{bmatrix}
$$

Ahora necesitamos obtener $Q^Tb$

$$
\begin{bmatrix}
\frac{1}{3} & \frac{-14}{15}\\
\frac{2}{3} & \frac{1}{3}\\
\frac{2}{3} & \frac{2}{15}
\end{bmatrix}^T
\begin{bmatrix}
-3\\
15\\
9\\
\end{bmatrix}=\begin{bmatrix}
\frac{1}{3} & \frac{2}{3} & \frac{2}{3}\\
\frac{-14}{15} & \frac{1}{3} & \frac{2}{15}
\end{bmatrix}

\begin{bmatrix}
-3\\
15\\
9\\
\end{bmatrix}=\begin{bmatrix}
15\\
9\\
\end{bmatrix}
$$
Finalmente resolvemos $\hat{R}x=c$ , $c=Q^Tb$, con backward substition:

$$
\begin{bmatrix}
3 & 2\\
0 & 5\\
\end{bmatrix}
\begin{bmatrix}
x_1 \\
x_2 \\
\end{bmatrix}
=\begin{bmatrix}
15\\
9\\
\end{bmatrix}
$$

Y se obtiene como resultado $x_2=\frac{9}{5}$ y $x_1=3.8$
