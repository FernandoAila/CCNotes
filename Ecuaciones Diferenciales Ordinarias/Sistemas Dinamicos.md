
Corresponde a una extension natural de los [[Problemas de valor inicial|IVP]], en los que hay más de una variable:

$$
\begin{align*}
\dot x&=f_1(t,x,y)\\
\dot y &= f_2(t,x,y)\\
x(0)&= x_0\\
y(0)&= y_0
\end{align*}
$$
![[Pasted image 20221127233831.png]]
donde $x(t)$ y $y(t)$ son funciones que dependen del tiempo, $f_1$ y$f_2$ son funciones en 3 variables.

La pregunta es como resolvemos este problema utilizando los metodos ya vistos para [[Problemas de valor inicial|IVP]]. La respuesta está en re-escribir el problema utilizando notación vectorial de la forma:
$$
\begin{align*}
\dot y &= F(t,\vec{y})\\
y(0)&= y_0
\end{align*}
$$

Donde:
$$
\begin{align*}
\vec{y}(t)=\begin{bmatrix} x(t)\\
y(t)\\
\end{bmatrix}\\\\
F(t)=\begin{bmatrix}f_1(t,\vec{y})\\
f_2(t,\vec{y})\\
\end{bmatrix}\\
\vec{y}(0)=\begin{pmatrix}x_0\\
y_0\end{pmatrix}
\end{align*}
$$
Las versiones vectoriales de los algoritmos presentados son:
![[Pasted image 20221127235717.png]]

Observaciones:
- El [[Metodo de Euler]] ya no es una funcion escalar si no que es vectorial
- En [[Backward Euler]] no tendremos una busqueda de ceros escalar sino que vectorial, lo que resulta en un sistema de ecuaciones no lineal, por lo que se utiliza el [[Metodo de Newton en Rn]].


## El pendulo

Consideremos que tenemos un pendulo simple, con su pivote en un punto $P$ y con una barra rigida de largo $l$ con masa despreciable en relacion a la particula con masa $m$ en el extremo opuesto.
![[Pasted image 20221128003658.png]]
Usando segunda ley de newton, la siguiente ecuacion de evolución entrega el angulo $\theta$ formado entre la vertical bajo el pivote y la barra rigida.
$$
\begin{align*}
ml\ddot{\theta}=-mg \sin\theta\\
\theta(0)=\theta_0\\
\dot \theta=\omega_0
\end{align*}
$$
Donde $g$ es la constate de aceleración de gravedad, $\theta_0$ el angulo inicial y $\omega_0$ la velocidad del angulo.
Podemos reescribir la primera ecuacion, eliminando $m$ y pasando $l$ al lado derecho:
$$
\ddot{\theta}=- \frac{g}{l} \sin\theta
$$
Notemos que la forma de la ecuacion no es compatible con la mostrada anteriormente en la definicion de un sistema mecanico. Para que la ecuacion tenga esta estructura realizamos un cambio de variable conveniente de la forma:
$$
\begin{align*}
y_1(t)=\theta(t)\\
y_2(t)=\dot\theta(t)
\end{align*}
$$
Derivando:

$$
\begin{align*}
\dot y_1(t)=\dot \theta(t)\\
\dot y_2(t)=\ddot\theta(t)
\end{align*}
$$

Donde notamos que la primera ecuacion corresponde simplemente a la definicion de $y_2(t)$, mientras que la segunda ecuacion corresponde a la definicion original de $\ddot  \theta$ es decir:
$$
\begin{align*}
\dot y_1&=y_2\\
\dot y_2&=-\frac{g}{l}\sin y_1
\end{align*}
$$
El cual es un sistema dinamico!.
Donde:

$$
\begin{align*}
\vec{y}(t)=\begin{bmatrix} y_1(t)\\
y_2(t)\\
\end{bmatrix}\\\\
F(t)=\begin{bmatrix}y_2\\
-\frac{g}{l}\sin y_1\\
\end{bmatrix}\\

\end{align*}
$$

# Ejemplo

Sea la ecuacion:
$$
y^{''}(x)+2y'(x)+3y=0
$$
con:
$$
\begin{align*}
y(1)=1\\
y^{'}(1)=0
\end{align*}
$$
Para llevar la ecuacion a un IVP normal, realizamos el siguiente cambio de variable:
$$
\begin{align*}
g_1=y\\
g_2=y^{'}
\end{align*}
$$
Derivando:
$$
\begin{align*}
g_1^{'}&=y=y_2\\
g_2^{'}&=y^{''}=-2y^{'}+3y=-2y_2-3y_1
\end{align*}
$$
Por lo que:
$$
\begin{align*}
g_1(0)&=1\\\
g_2(0)&=0
\end{align*}
$$
Por lo que en su forma matricial:
$$
\begin{align*}
\vec{y}&=\begin{pmatrix}g_1 \\ g_2\end{pmatrix}\\
\vec{y}^{'}&=\begin{pmatrix}g_1^{'}\\
g_2^{'}\end{pmatrix}=F(g_1,g_2)=\begin{pmatrix}g_2\\
-2g_2-3g_1\end{pmatrix}
\end{align*}
$$
El [[Metodo de Euler]] dice que:
$$
y_{i+1}=y_i+F(y_i)h
$$
Si definimos:
$$
y_0=\begin{pmatrix} 1 \\0 \end{pmatrix}
$$
y 
$$
F(y)=\begin{pmatrix} g_2\\-2g_2-3g_1 \end{pmatrix}
$$Luego, con un step de $0.1$:
$$
\begin{align*}
y_{1}&= \begin{pmatrix} 1 \\0 \end{pmatrix}+ F(\begin{pmatrix} 0 \\1 \end{pmatrix})0.1\\
&=\begin{pmatrix} 1 \\0 \end{pmatrix} + \begin{pmatrix} 0 \\-3 \end{pmatrix}0.1\\
&=\begin{pmatrix}0.1\\
-0.3\end{pmatrix}
\end{align*}
$$
Seguir hasta llegar al fin del intervalo.