
La primera alternativa para encontrar aquella curva, mejor dicho, los coeficientes que minimizan el error, es utilizar una minimizacion en alta dimension.

Lo primero que se requiere es definir es la estructura de la aproximacion que queremos utilizar.
![[Pasted image 20221029222834.png]]

Por ejemplo, para el ejemplo de la imagen anterior podemos realizar un ajuste lineal de la forma:$$\hat{y}=a+bx$$
>[!INFO] Se pueden proponer diferentes estructuras como:
>$$\begin{align}
>y&=a+bx+cx^2\\
>y&=a+bx+c\sin(x)
>\end{align}$$
>Lo importante es que esta esté relacionada con el contexto del problema.

La idea entonces es minimizar el error cuadratico, que lo podemos definir como:$$\begin{align}
E(a,b)&=\sum_{i=1}^m (y_i-\hat{y_i})^2\\
&=\sum_{i=1}^m (y_i-(a+bx_i))^2 \\
&=\sum_{i=1}^m (y_i-a-bx_i)^2
\end{align}$$
>[!INFO] De la misma forma podemos utilizar otra definicion de error!

$E(a,b)$ no es más que una función en $\mathbb{R}^2$, por lo que puede ser sujeta a encontrar sus puntos de inflexion, es decir, sus puntos maximos y minimos.
Para encontrar punto critico en alta dimension se procede de igual forma que en el caso de 1 dimension, es decir, igualando la derivada, en este caso el gradiente, a 0:$$\nabla E(a,b)=0$$


Calcular el gradiente corresponde a:$$\begin{align}
\nabla E(a,b)&=0\\
(\frac{\partial E}{\partial a},\frac{\partial E}{\partial b})&=0\\
\frac{\partial E}{\partial a} &=\frac{\partial}{\partial a} \sum_{i=1}^m (y_i-a-bx_i)^2=-\sum_{i=1}^m2(y_i-a-bx_i)\\
\frac{\partial E}{\partial b} &=\frac{\partial}{\partial b} \sum_{i=1}^m (y_i-a-bx_i)^2=-\sum_{i=1}^m2(y_i-a-bx_i)x_i
\end{align}$$
Igualando a 0:$$\begin{align}

0=\frac{\partial E}{\partial a} &=-\sum_{i=1}^m2(y_i-\hat{a}-\hat{b}x_i)\\
&=\sum_{i=1}^m (y_i-\hat{a}-\hat{b}x_i)\\
&=\sum_{i=1}^m (y_i)-m\hat{a}-\hat{b}\sum_{i=1}^m (x_i)\\
m\hat{a}+\hat{b}\sum_{i=1}^m (x_i)&=\sum_{i=1}^m (y_i)
\end{align}$$
Notar el cambio de $a$ a $\hat{a}$ y de $b$ a $\hat{b}$ porque $\hat{a}$ y $\hat{b}$ ahora deben satisfacer que la ecuacion sea igual a 0 donde antes no era el caso.
Ahora con $\frac{\partial E}{\partial b}$ :
$$\begin{align}

0=\frac{\partial E}{\partial a} &=-\sum_{i=1}^m2(y_i-\hat{a}-\hat{b}x_i)x_i\\
&=\sum_{i=1}^m (y_ix_i-\hat{a}x_i-\hat{b}x_i^2)\\
&=\sum_{i=1}^m (y_ix_i)-\hat{a}\sum_{i=1}^m (x_i)-\hat{b}\sum_{i=1}^m (x_i^2)\\
\hat{a}\sum_{i=1}^m (x_i)+\hat{b}\sum_{i=1}^m (x_i^2)&=\sum_{i=1}^m (y_ix_i)
\end{align}$$



Lo que genera el sistema de ecuaciones lineales:
$$\begin{bmatrix}
m & \sum_{i=1}^m (x_i) \\
\sum_{i=1}^mx_i & \sum_{i=1}^m (x_i^2)\\
\end{bmatrix}

\begin{bmatrix}
\hat{a} \\
\hat{b}\\
\end{bmatrix}
=

\begin{bmatrix}
\sum_{i=1}^m (y_i) \\
\sum_{i=1}^m (y_ix_i)\\
\end{bmatrix}
$$
>[!Note] Nota
>Puede que la minimización que realizamos no genere un sistema de ecuaciones lineales.
>En esos casos un algoritmo muy util es el metodo del [[Gradiente Descendiente|gradiente descendiente]], que corresponde a un metodo **iterativo**

Lo cual tiene como solucion:
![[Pasted image 20221030013443.png]]

Por lo que encontramos aquellos valores $a$ y $b$ que minimizan el error cuadratico $$E(a,b)=\sum_{i=1}^m (y_i-a-bx_i)^2$$

