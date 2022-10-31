Al analizar el [[Error de Interpolacion y Fenomeno de Runge|error de interpolacion]], encontramos que los puntos equispaciados generan el llamado fenomeno de Runge, por lo que la tarea es encontrar ciertos puntos los cuales minimizen este fenomeno y reduzcan el error de interpolacion.

En particular de acuerdo a la formula del error de interpolacion:
$$f(x)-p(x)=\frac{(x-x_1)(x-x_2)\cdots(x-x_n)}{n!}f^{(n)}(c)$$
Queremos reducir el error, y el unico elemento que tenemos control es sobre el numerador $(x-x_1)(x-x_2)\cdots(x-x_n)$. Por lo tanto el problema queda en encontrar ciertos puntos que minimizan siguiente funcion:$$w(x)=\max|(x-x_1)(x-x_2)\cdots (x-x_n)|$$
Para simplificar el analisis supongamos que los puntos $x_1,x_2,\cdots,x_n$ estan acotados entre $-1$ y $1$ y queremos buscar 2 puntos, $x_1$ y $x_2$, luego:$$w(x_1,x_2)=\max|(x-x_1)(x-x_2)|$$
Buscamos aquellos $x_1$ y $x_2$ que minimizan $w(x_1,x_2)$, entonces:
$$x1,x2=\arg \min w(x_1,x_2)$$

Estos valores para el intervalo $[-1,1]$ son calculados numericamente y equivalen a
$$\begin{align}
x_1=0,707106781186547\\
x_2=-0,707106781186547
\end{align}$$
o $$\begin{align}
x_1=-0,707106781186547\\
x_2=0,707106781186547
\end{align}$$
Estos puntos calculados algebraicamente son:
$$\begin{align}
x_1=\cos(\frac{\pi}{4})\\
x_2=\cos(\frac{3\pi}{4})
\end{align}$$
## Teorema de Chebyshev

>[!NOTE] Teorema de Chebyshev
>La eleccion de numeros naturales $-1\leq x_1,x_2,\cdots,x_n\leq 1$ que hace que el valor de $$\max|(x-x_1)(x-x_2)\cdots (x-x_n)|$$ sea lo mas pequeño posible es:$$x_i=\cos(\frac{(2i-1\pi)}{2n})$$ y el valor minimo es $\frac{1}{2^{n-1}}$ .
>De hecho el minimo es alcanzado por:$$(x-x_1)\cdots(x-x_n)=\frac{1}{2^{n-1}}T_n(x)$$
>Donde $T_n(x)=\cos (n \arccos(x))$ es el polinomio de Chebyshev de grado n

Especificamente, la ultima parte aplica solamente cuando usamos los puntos de Chebyshev $x_1,x_2,\cdots, x_n$.
Claramente $T_n \leq 1$, debido a  que es un coseno, pero aún así tiene la forma de un polinomio:
$$\begin{align}
T_0(x)&=cos(0\arccos(x))=1\\
T_1(x)&=cos(1\arccos(x))=x\\
T_2(x)&=cos(2\arccos(x))=x^2-1
\end{align}
$$
Desde una interpretacion grafica, un punto de Chebyshev se puede considerar como el coseno de un angulo $\theta$, de la forma $\theta =\frac{(2i-1\pi)}{2n}$.

La siguiente figura muestra 5 puntos Chebtshev para $n=5$:
![[Pasted image 20221029185040.png]]


Con los valores:
![[Pasted image 20221029185058.png]]


## Ejemplo:

Encontrar el peor caso del error para la diferencia entre $e^x$ , $\exp(x)$  y el polinomio de Chebyshev de grado 4 en  el intervalo $[-1,1]$.

Recordando que:
$$|f(x)-p(x)|=\frac{|(x-x_1)(x-x_2)\cdots(x-x_n)|}{n!}|f^{(n)}(c)|$$

Reemplazando $\exp(x)$ por $f(x)$ y $n=5$:
$$|\exp(x)-p(x)|=\frac{|(x-x_1)(x-x_2)\cdots(x-x_5)|}{5!}|f^{(5)}(c)|$$
A partir de esto tenemos que:
- Para el termino $|f^{(5)}(c)|$, tenemos que $f^{(5)}(c)=\exp^{(5)}(c))=\exp(c)$. Como la función $\exp$ es monótonamente creciente, se tiene que en el intervalo $[-1,1]$ su valor mayor es $\exp(1)$. Es decir $f^{(5)}(c)$ es acotado superiormente por $exp(1)$, $|f^{(5)}(c)|\leq |\exp(1)|$, lo que es el peor caso ya que hace que el error sea mayor.

- Para el termino $|(x-x_1)(x-x_2)\cdots(x-x_5)|$ recordar la definicion de puntos de Chebyshev:$$|(x-x_1)(x-x_2)\cdots(x-x_5)| = ||\frac{1}{2^{n-1}}T_n(x)|\leq\frac{1}{2^{n-1}} $$ Es decir, **usando puntos de Chevyshev**, el valor maximo que puede dar este termino es $\frac{1}{2^{n-1}}$.

Usando esta informacion reemplazamos:
$$|\exp(x)-p(x)|=\frac{1}{2^{5-1}}\frac{1}{5!}|f^{(5)}(c)|$$
$$|\exp(x)-p(x)|\leq \frac{1}{2^{5-1}}\frac{1}{5!}\exp(1)$$

Es decir en el peor caso el error es de $$\frac{1}{2^{5-1}}\frac{1}{5!}\exp(1)=0.001415771785656$$

## Cambio de variable

Podemos llevar los puntos de Chevyshev de un intervalo $[-1,1]$ a uno $[a,b]$ usando un cambio de variable.

Recordando que los puntos de Chevyshev en $[-1,1]$ son:$$x_i=\cos(\frac{(2i-1\pi)}{2n})$$
Si consideramos el cambio de variable:
$$\hat{x_i}=\frac{b-a}{2}x_i+\frac{b+a}{2}$$

Podemos mover los puntos de Chevyshev al intervalo $[a,b]$.

![[Pasted image 20221029195646.png]]


Este cambio implica que hay que hacer una modificacion al termino del error de interpolacion de los puntos, es decir:
$$|(x-x_1)(x-x_2)\cdots(x-x_5)| = ||\frac{1}{2^{n-1}}T_n(x)|\leq\frac{(\frac{b-a}{2})^n}{2^{n-1}} $$

Por lo tanto el error total de interpolacion corresponde a:
$$|f(x)-p(x)|=\frac{(\frac{b-a}{2})^n}{2^{n-1}n!}|f^{(n)}(c)|$$

