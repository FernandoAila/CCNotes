La [[Interpolación de Lagrange]] toma orden $O(n^2)$ en evaluar el polinomio interpolador.
La interpolacion **Baricentrica** tiene como caracteristica principal que es un derivado de la interpolacion de Lagrange y que mejora los tiempos de evaluacion y construccion del polinomio en ciertos casos.

Para esto, se define  $l(x)$ de la siguiente forma:
$$l(x)=\prod^n_{i=1}(x-x_i)$$
Que es distinto a los $l_i(x)$ utlizados en la interpolacion de Lagrange, ya que aqui ocupamos todos los terminos del producto.
A partir de esta definicion, podemos reescribir los $l_i(x)$ de la siguiente forma:
$$l_i(x)=\frac{l(x)}{(x-x_i)}$$
Podemos obtener los pesos asociado del denominador de $L_i(x)$ de la siguiente forma:
$$w_i=\frac{1}{l_i(x_i)}=\frac{1}{l'(x_i)}$$
Por lo que los $L_i(x)$ son,$$L_i(x)=\frac{l(x)}{(x-x_i)}w_i$$

Reescribiendo el metodo de Lagrange: 
$$\begin{align}
p(x)&=\sum_{i=1}^n y_iL_i(x)\\
&=\sum_{i=1}^n y_i\frac{l(x)}{(x-x_i)}w_i\\
&=l(x)\sum_{i=1}^n y_i\frac{w_i}{(x-x_i)}

\end{align}$$
Esto ya es una mejora, notemos que evaluar la sumatoria toma orden $O(n)$ ya que el $w_i$ es un precalulo.
Notemos si que si nos acercamos a $x=x_i$, implica que el denominador es 0, para esto considerar lo siguiente:
$$\lim_{x\rightarrow x_k}p(x)=y_k$$
Esto es por construccion, por lo que cuando nos acercamos a $x_i$ el valor del polinomio tendera a $y_i$.

Considerar ahora, que queremos interpolar la constante 1, es decir los puntos tienen la forma, $(x_1,1),(x_2,1),\cdots,(x_n,1)$, luego:
$$\begin{align}
p(x)&=l(x)\sum_{i=1}^n \frac{w_i}{(x-x_i)}=1

\end{align}$$
Despejando $l(x)$:
$$\begin{align}
l(x)=\frac{1}{\sum\limits_{i=1}^n \frac{w_i}{(x-x_i)}}

\end{align}$$
Reemplazando en la ecuacion original:
$$\begin{align}
p(x)&=l(x)\sum_{i=1}^n y_i\frac{w_i}{(x-x_i)}\\
&=\frac{1}{\sum_\limits{i=1}^n \frac{w_i}{(x-x_i)}}\sum_{i=1}^n y_i\frac{w_i}{(x-x_i)}\\
&=\frac{\sum\limits_{i=1}^n y_i\frac{w_i}{(x-x_i)}}{\sum\limits_{i=1}^n \frac{w_i}{(x-x_i)}}

\end{align}$$
Lo cual es la forma de la interpolacion barocentrica:$$p(x)=\frac{\sum\limits_{i=1}^n y_i\frac{w_i}{(x-x_i)}}{\sum\limits_{i=1}^n \frac{w_i}{(x-x_i)}}$$
Con $$w_i=\frac{1}{l_i(x_i)}=\frac{1}{l'(x_i)}$$
Notar que no se puede simplificar las sumatorias, ya que simplemente quedaria las sumatoria de los $y_i$ lo que no tiene sentido.

El costo computacional es sencillo, notemos que el denominador toma del orden $O(n)$  operaciones elementales si conocemos los $w_i$, de la misma forma de que el numerador, por lo que el algoritmo toma $O(n)$, mucho mejor que el $O(n^2)$ de Lagrange.

Aun asi, el calculo de todos los $w_i$ toma $O(n^2)$ operaciones elementales, al menos que estos sigan un patron regular como es el caso de los [[Puntos de Chebyshev]], donde los conocemos algebraicamente, es decir, un algoritmo los obtiene en $O(n)$.