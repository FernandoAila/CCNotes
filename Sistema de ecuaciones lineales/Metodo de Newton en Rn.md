# Metodo de newton en $\mathbb{R}^n$

Recordemos que en el caso de una dimension, es decir, una componente, por ejemplo x, si queriamos buscar el cero, o la raiz a una funcion, podiamos utilizar diferentes tecnicas. Una de ellas es el llamado [[Metodo de newton]], que nos permitia a partir de un initial guess $x_0$ y una derivada de la funcion $f$, $f'(x)$, encontrar un cero de la funcion teniendo convergencia cuadratica y cuando la raiz está en un punto critico, lineal.
La idea ahora es extender el metodo a más dimensiones que una.

Consideremos ahora una función que depende de dos variables, $x$ e $y$, es decir, $f(x,y)$.  Por ejemplo, el circulo unitario cuya formula es $x^2+y^2=1$, o una parabola $y=x^2$.  Digamos que queremos encontrar la interseccion de estas dos funciones.$$ \begin{align}x^2+y^2&=1\\y&=x^2\end{align}$$![[Pasted image 20221006052849.png]]

A este sistema se le llama un sistema de ecuaciones no lineales.
Como podemos encontrar esta interseccion?
Podemos utilizar el metodo de la substitucion, sabiendo que $y=x^2$:
$$\begin{align}y+y^2&=1 \\ y&= \pm\frac{-1\pm\sqrt{5}}{2}  \end{align}$$
Los valores de $x$ se obtiene reemplazando en la segunda ecuacion correspondiente.

Este analisis se puede re-escribirse de la forma, teniendo la misma idea del metodo de newton:
$$F(x)=F(\begin{bmatrix}x\\y\end{bmatrix})=\begin{bmatrix}x^2+y^2-1\\y-x^2\end{bmatrix} = 0$$
$F$ es simplemente una funcion vectorial que toma un  vector y entrega un vector.

El analogo del metodo de newton para más dimensiones es:
$$x_{i+1} = x_i-J^{-1}(x_i)F(x_i)$$
Por lo requerimos encontrar la inversa de la matriz jacobiana, $J$ .
En terminos practicos, $F(x)$ puede ser escrita de la siguiente forma:
![[Pasted image 20221007201358.png]]

Podemos reescribir el metodo presentado de la forma:$$\begin{align}x_{i+1} &= x_i-J^{-1}(x_i)F(x_i)\\
x_{i+1}-x_i &= -J^{-1}(x_i)F(x_i)\\
\delta x & =-J^{-1}(x_i)F(x_i)
\end{align}$$
Multiplicando por $J$ por la izquierda:$$\begin{align}
J(x_i)\delta x & =-F(x_i)
\end{align}$$
Lo que es lo mismo que resolver un sistema de ecuaciones $Ax=b$ !. Notar que $J(x_i)=A$, $\delta x=x$ y $-F(x_i)=b$.
Además,  $$x_{i+1} - x_i = \delta x$$



Usando de nuevo el ejemplo inicial se tiene:$$F(x)=\begin{bmatrix}x^2+y^2-1\\y-x^2\end{bmatrix} =\begin{bmatrix}f_1(x,y)\\f_2(x,y)\end{bmatrix} $$
 Obteniendo la Jacobiana:
$$F(x) =\begin{bmatrix}\frac{\partial f_1(x,y)}{\partial x} & \frac{\partial f_1(x,y)}{\partial y}\\ \frac{\partial f_2(x,y)}{\partial x} 
 & \frac{\partial f_2(x,y) }{\partial y}\end{bmatrix} = \begin{bmatrix}2x & 2y \\ -2x & 1 \end{bmatrix}$$
 Con initial guess : $$x_0 = \begin{bmatrix} 2\\1 \end{bmatrix}$$
La primera iteracion es: 
$$\begin{align}
J(x_0)&= \begin{bmatrix}4 & 2 \\ -2 & 1 \end{bmatrix}\\
F(x_0)&= \begin{bmatrix}4 \\ -3 \end{bmatrix}
\end{align}$$Resolviendo por $\delta x$:$$\begin{bmatrix}4 & 2 & -4 \\ 0 & 2 & -5 \end{bmatrix}$$
$$\delta x =\begin{bmatrix}
\frac{1}{4}\\\frac{-5}{2}
\end{bmatrix}$$

Por lo tanto $x_1$ es:
$$\delta x = x_{1}- x_{0} \rightarrow \delta x +x_0= x_1$$
$$x_1=\begin{bmatrix}
\frac{1}{4}\\\frac{-5}{2}
\end{bmatrix}+\begin{bmatrix} 2\\1 \end{bmatrix}=\begin{bmatrix} \frac{9}{4}\\-\frac{3}{2} \end{bmatrix}$$
