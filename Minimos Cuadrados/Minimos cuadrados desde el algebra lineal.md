De la misma forma que en [[Minimos Cuadrados por Minimizacion]] definimos la estructura a utilizar de la forma$$y_i\approx\hat{y_i}=a+bx_i$$
Podemos escribir el problema como un sistema de ecuaciones sobre-determinado, es decir, con más ecuaciones que incognitas:$$\begin{align}
a+bx_1&=y_1\\
a+bx_2&=y_2\\
a+bx_3&=y_3\\
&\vdots\\
a+bx_m&=y_m
\end{align}$$

Usando notacion matricial:
$$\underbrace{\begin{bmatrix}
1 & x_1 \\
1 & x_2  \\
1 & x_3 \\
\vdots&\vdots\\
1& x_m 
\end{bmatrix}}_{A}
\begin{bmatrix}
a\\
b
\end{bmatrix}
=
\underbrace{\begin{bmatrix}
y_1\\
y_2\\
y_3\\
\vdots\\
y_m
\end{bmatrix}}_b
$$
Notar que:
- La matriz tiene $m$ filas y $n=2$ columnas. $m$ indica la cantidad de ecuaciones y $n$ de incognitas 
- Si $m>n$ y el rank, es decir la cantidad de filas (o columnas) l.i, es $n$, se tiene un sistema de ecuaciones sobre-determianado.
- Si $m=n$, el sistema es cuadrado y se puede resolver por metodos convencionales.
- Si $m<n$ el sistema no tiene solucion unica.
- La matriz $A$ es similar a la [[Matriz de Vandermonde]], sin embargo este caso está truncada en la cantidad de columnas.


Si reescribimos la ecuacion matricial en su forma algebraica:$$\begin{align}
A\begin{bmatrix}
a\\
b
\end{bmatrix}
&=\boldsymbol{b}\\
[v1,v2]\begin{bmatrix}
a\\
b
\end{bmatrix}&=\boldsymbol{b}\\
av_1+bv_2&=\boldsymbol{b}

\end{align}$$
>[!Warning] El $b$ del lado izquierdo es distinto al del lado derecho

Lo que es una combinacion lineal de las columnas de $A$.

En definitiva buscamos la mejor combinacion lineal de los vectores $v_1$ y $v_2$ para aproximar $b$, ya que **no** siempre podemos obtener escalares $a$ y $b$ que den exacto $\boldsymbol{b}$. Definimos la funcion de error cuadratico como:$$E(a,b)=||\boldsymbol{b}-av_1-bv_2||_2^2=||\boldsymbol{b}-A\begin{bmatrix}
a\\
b
\end{bmatrix}||_2^2$$
![[Pasted image 20221030034738.png]]

La figura anterior, muestra una interpretacion grafica de lo que significa reducir el error cuadratico en algebra lineal. En particular $v_1$ y $v_2$ forman un sub-espacio vectorial en $\mathbb{R}^m$ a partir de su combinacion lineal. Por ejemplo, 2 vectores l.i $v_1$ y $v_2$ pueden formar un plano  en $\mathbb{R}^3$, y solo un vector $v_1$ genera una recta en $\mathbb{R}^2$. El vector $\boldsymbol{b}$ **no** necesariamente está en el subespacio generado por el $span(v_1,v_2)$, ya que puede tener más dimensiones que el mismo subespacio como se observó en la figura.

La idea es minimizar la distancia (color azul) entre lo que se puede representar con la combinacion lineal de $v_1$ y $v_2$ es decir $A\overline{x}=\overline{b}$ con el vector $b$ dado. Como se observa existe un unico vector $\overline{x}$  que cumpla con la minimizacion de está en el espacio.

![[Pasted image 20221030041713.png]]

Para la imagen anterior ocurre la misma situacion, la linea recta es un sub-espacio vectorial generado por las columnas de $A$, $A\overline{x}$ es un vector llamado minimizador que pertenece al subespacio, donde $\overline{x}$ son los coeficientes que escalan a las columnas de $A$ para que la distancia entre $b$ y $A\overline{x}$ sea minima. Notar que existe una ortogonalidad entre el subespacio y el vector residuo $b-A\overline{x}$.

Formalizando, el vector residuo lo definimos como:
$$\vec{r}=\boldsymbol{\vec{b}}-A\overline{x}$$
El "tamaño" de este vector lo podemos sacar como una norma, $||\vec{r}||$, naturalmente queremos que este vector sea el minimo posible es decir, minimizar la funcion error antes mencionada:
$$E(a,b)=||\vec{r}||_2^2$$
Este vector $\vec{r}$ es **ortogonal** al vector definido como $A\overline{x}$,  (tambien al sub-espacio generado por $Ax$) llamado minimizador. Esto quiere decir que el [[Producto Interno]] de $\vec{r}$ y de $A\overline{x}$ da 0 es decir:
$$\begin{align}
(Ax)^T(\boldsymbol{\vec{b}}-A\overline{x})&=0\\
x^T A^T(\boldsymbol{\vec{b}}-A\overline{x})&=0\\
\end{align}
$$

Notar que  $x$ es un  vector del espacio desconocido, $\overline{x}$ un vector de los coeficientes ( en este caso $<a,b>$) que queremos encontrar.
Si $\vec{x}\neq 0$ significa que el termino $A^T(\boldsymbol{\vec{b}}-A\overline{x})$ tiene que ser 0, lo que significa que:
$$
\begin{align}
A^T(\boldsymbol{\vec{b}}-A\overline{x})=0\\
A^T\boldsymbol{\vec{b}}-A^TA\overline{x}=0\\
A^TA\overline{x}=A^T\boldsymbol{\vec{b}}
\end{align}
$$

Lo que se conoce como **ecuaciones normales**, lo que no es más que un [[Sistemas de Ecuaciones Lineales|sistema de ecuacion lineal]]. Estas nos dan una formula explicita para el $\overline{x}$:
$$
\overline{x}=(A^TA)^{-1}A^T\boldsymbol{\vec{b}}
$$
El termino que acompaña al $\boldsymbol{\vec{b}}$, es decir, $(A^TA)^{-1}A^T$ es la llamada **pseudo-inversa de Moore-Penrose** y se denota como $A^{\dagger}=(A^TA)^{-1}A^T$.


>[!INFO] Nota
>Notar que no es necesario calcular la inversa $(A^TA)^{-1}$ directamente ya que podemos realizar un sistema de ecuaciones lineal para  encontrar $\overline{x}$!.


Finalmente podemos analizar nuevamente el problema de minimos cuadrados de la forma:
$$\underbrace{\begin{bmatrix}
1 & x_1 \\
1 & x_2  \\
1 & x_3 \\
\vdots&\vdots\\
1& x_m 
\end{bmatrix}}_{A}
\begin{bmatrix}
a\\
b
\end{bmatrix}
=
\underbrace{\begin{bmatrix}
y_1\\
y_2\\
y_3\\
\vdots\\
y_m
\end{bmatrix}}_b
$$
Lo primero consiste en construir las ecuaciones normales, $A^TA\overline{x}=A^T\boldsymbol{\vec{b}}$:
$$
\begin{bmatrix}
1 &  1    & 1  & \cdots & 1\\ 
x_1 & x_2  & x_3 &\cdots & x_m
\end{bmatrix}
\begin{bmatrix}
1 & x_1 \\
1 & x_2  \\
1 & x_3 \\
\vdots&\vdots\\
1& x_m 
\end{bmatrix}
\begin{bmatrix}
\overline{a} \\ 
\overline{b} 
\end{bmatrix}
=

\begin{bmatrix}
1 &  1    & 1  & \cdots & 1\\ 
x_1 & x_2  & x_3 &\cdots & x_m
\end{bmatrix}

\begin{bmatrix}
y_1 \\ 
y_2 \\
y_3 \\
\vdots\\
y_m
\end{bmatrix}
$$

Si multiplicamos las matrices obtenemos:

$$\begin{bmatrix}
m & \sum_{i=1}^m (x_i) \\
\sum_{i=1}^mx_i & \sum_{i=1}^m (x_i^2)\\
\end{bmatrix}

\begin{bmatrix}
\overline{a} \\ 
\overline{b} 
\end{bmatrix}
=

\begin{bmatrix}
\sum_{i=1}^m (y_i) \\
\sum_{i=1}^m (y_ix_i)\\
\end{bmatrix}
$$

Que es exactamente lo mismo que lo visto en [[Minimos Cuadrados por Minimizacion]]!, solamente aquí no se calculó ninguna derivada e igualmente se encontró una solucion que minimiza el error cuadratico.

## Ejemplo




