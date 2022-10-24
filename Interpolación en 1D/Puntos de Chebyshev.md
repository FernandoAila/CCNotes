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




