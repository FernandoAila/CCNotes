Este método realiza una aproximacion directa de la ODE, e incluye de inmediato las condiciones de borde, generando un sistema de ecuaciones lineales o no lineales.
Recordar la definicion de derivada:
$$
y'(x)=\lim_{h\rightarrow0} \frac{y(x+h)-y(x)}{h}
$$
Esto se define como  el cociente entre la variacion de $y(x)$ en los puntos $x+h$ y $x$, y el incremento $h$.

Como trabajamos de forma discreta tenemos pares ordenados de la forma:
$$
{(x_0,y_0),(x_1,y_1),(x_2,y_2),\cdots,(x_N,y_N)}
$$
donde $y_i$ representa la aproximacion de $y(x_i)=ih$ con y $h=\frac{b-a}{N}$, es decir, estamos discretizando el dominio del BVP.

La pregunta radica entonces, en como obtenimos una aproximacion de la derivada si solo tenemos valores discretos $y_i$ y $x_i$
Podemos obtener una aproximacion si realizamos lo siguiente:
$$
y'(x_i)=\lim_{h\rightarrow 0} \frac{y(x_{i}+h)-y(x_{i})}{h}=\frac{y(x_{i+1})-y(x_{i})}{h} \approx \frac{y_{i+1}-y_i}{h}
$$
Es decir estamos aproximando de con los valores que ya tenemos!.
![[Pasted image 20221130030445.png]]

Naturalmente, a medida que el equispaciado, es decir el $h$, se hace más pequeño la aproximacion de la derivada se hace mejor.
Esta aproximacion se llama **Forward difference**. Existen otras más como:
$$
\begin{align*}
y'(x_i)= \frac{y(x_{i}+h)-y(x_{i})}{h} \approx \frac{y_{i+1}-y_i}{h}\quad \text{Forward Difference}\\
y'(x_i)= \frac{y(x_{i})-y(x_{i}-h)}{h} \approx \frac{y_{i}-y_{i-1}}{h}\quad \text{Backward Difference}\\
y'(x_i)= \frac{y(x_{i}+h)-y(x_{i}-h)}{2h} \approx \frac{y_{i+1}-y_{i-1}}{2h}\quad \text{Central Difference}
\end{align*}
$$
Por lo que tenemos 3 formas de aproximar la primera derivada!.
Para aproximar la segunda derivada:
$$
\begin{align*}
y^{"}(x_i)&=\frac{\text{Forward Difference-Backward Difference}}{h}\\
&=\frac{\frac{y_{i+1}-y_i}{h}-\frac{y(x_{i})-y(x_{i}-h)}{h}}{h}\\
&=\frac{y(x_i+h)-2y(x_i)+y(x_i-h)}{h^2}\\\\
&=\frac{y_{i+1}-2y_i+y_{i-1}}{h^2}
\end{align*}
$$

Como utilizamos estas aproximaciones para obtener  un algoritmo que entregue una aproximacion numerica para resolver un [[Problemas de valor frontera|BVP]]?

Sea el siguiente BVP de ejemplo:
$$
\begin{align*}
y^{"}(x)&=0\\
x&\in{]0,1[}\\
y(0)&=c_1\\
y(1)&=c_2\\
\end{align*}
$$
En este caso tenemos que definir la cantidad de puntos que tendrá la discretizacion, por ejemplo, 5:
$$\{(x_0,y_0),(x_1,y_1),(x_2,y_2),(x_3,y_3),(x_4,y_4)\}$$
Donde conocemos, $x_i=ih$, $h=\frac{1}{4}$, $y_0=c_1$,$y_4=c_2$
Por lo que faltan $y_1,y_2$ y $y_3$.
Para determinar estas incognitas necesitamos 3 ecuaciones, las cuales podemos obtener usando la expresion de la segunda derivada, es decir, $y^{"}=0$, por lo que:
$$
\begin{align*}
y^{"}(x_1)=\frac{y_{2}-2y_1+y_{0}}{h^2}=0\\
y^{"}(x_2)=\frac{y_{3}-2y_2+y_{1}}{h^2}=0\\
y^{"}(x_3)=\frac{y_{4}-2y_3+y_{2}}{h^2}=0
\end{align*}
$$
Podemos reemplazar en $y_0=c_1$ y $y_4=c_2$, y movemos todos los valores conocidos al lado derecho:
$$
\begin{align*}
y_2-2y_1&=-c_1\\
y_3-y_2-2y_1&=0\\
-2y_3+y_2&=-c_2
\end{align*}
$$
Lo que corresponde a un [[Sistemas de Ecuaciones Lineales]]!.
En su forma matricial:
$$
\begin{pmatrix}-2&1&0 \\ 1&-2&1 \\ 0&1&-2\end{pmatrix}\begin{pmatrix}y_1 \\ y_2 \\ y_3 \end{pmatrix}\begin{pmatrix}-c_1 \\ 0 \\ -c_2\end{pmatrix}
$$

Lo cual podemos resolver con cualquier algoritmo descrito como [[Factorizacion LU]], [[Factorizacion PALU]], [[GMRes]], etc.

Notar que no teniamos una funcion al lado derecho de $y^"(x)$ pero si puede ser así, por ejemplo si tenemos el termino $y'(x)$ podemos aproximarlo utilizando las aproximaciones mostradas anteriormente como Forward Difference, Backward Difference, etc. Además si tenemos el termino $y(x)$ basta con reemplazarlo por la aproximación!, es decir $y_i$.


# Ejemplo:

Resolver 
$$
\begin{align*}
ay^{"}(x)+b(x)y'(x)+c(x)y(x)=f(x) \\
a(y(0)-y_0)=0\\
y(1)=0
\end{align*}
$$