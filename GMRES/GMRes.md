
**GMRes**, Generalized Minimal Residual Method,  es un algoritmo que sirve para resolver [[Sistemas de Ecuaciones Lineales]] cuadrados. En particular toma la idea de [[Minimos  Cuadrados]] donde construimos la [[Factorizacion QR]] de un sistema de ecuaciones con más filas que columnas. Sin embargo, $QR$ también puede ser utilizado para sistemas de ecuaciones lineales cuadrado.


# Motivacion

>[!NOTE] Teorema de Cayley-Hamilton
>Una matriz de dimensiones $n\times n$  es **aniquilada** por su [[Valores y vectores propios|Polinomio caracteristico]] $p(\lambda)=det(\lambda I  - A)$ el cual es **monico** de grado $n$.

 Algunas consideraciones:
 - **Monico** dice que el coeficiente que acompaña al termino más grande de un polinomio es igual a 1, es decir $\boldsymbol{1}x^n+c_{n-1}x^{n-1}+\cdots+c_2x^2+c_1x+c_0$
 - $p(0)=det(-A)=(-1)^n det(A)$
 - $p(\lambda)=det(\lambda I  - A)=\lambda^n+c_{n-1}\lambda^{n-1}\cdots c_1\lambda+(-1)^ndet(A)$
 - Que una matriz sea **Aniquilidada** siginifica que $p(A)=0$ es decir : 
$$
p(A)=A^n+c_{n-1}A^{n-1}\cdots +c_1A+(-1)^ndet(A)I=0
$$
Donde $0$ es la matriz nula de dimensiones $n\times n$.




Usando esto ultimo, conseguimos una identidad que nos entrega una expresion para la inversa de $A$, $A^{-1}$, si es que $A$ es no singular, es decir $det(A)\neq 0$: 
$$
  \begin{align}
   A^n+c_{n-1}A^{n-1}\cdots +c_1A+(-1)^ndet(A)I&=0\\
   A^n+c_{n-1}A^{n-1}\cdots +c_1A&=(-1)^{n-1} det(A)I \quad /A^{-1} \\
   A^{n-1}+c_{n-1}A^{n-2}\cdots +c_1I&=(-1)^{n-1} det(A)A^{-1} \\
   \frac{(-1)^{n-1}}{ det(A)}(A^{n-1}+c_{n-1}A^{n-2}\cdots +c_2A+c_1I)&=A^{-1}
  \end{align}
$$
Lo que significa que $A^{-1}$ puede ser obtenido a partir de una combinacion lineal de las potencias de $A$.

Supongamos entonces que queremos resolver el sistema de ecuaciones:
$$
Ax=b
$$
Es decir encontrar $x$ de la forma:
$$x=A^{-1}b$$
Si reemplazamos la ecuacion obtenidad para $A^{-1}$ se tiene:
$$
\begin{align}
 x=A^{-1}b&=\frac{(-1)^{n-1}}{ det(A)}(A^{n-1}+c_{n-1}A^{n-2}\cdots +c_2A+c_1I)\boldsymbol{b}\\
 &=\frac{(-1)^{n-1}}{ det(A)} (A^{n-1} \boldsymbol{b}+c_{n-1}A^{n-2}\boldsymbol{b}\cdots +c_2A\boldsymbol{b}+c_1\boldsymbol{b})
 \end{align}
$$
Lo que podemos expresar en terminos de una sumatoria:

$$
x=\sum_{i=1}^n \tilde{c_i}A^{i-1}b
$$
Con $\tilde{c_i}=\frac{(-1)^{n-1}}{ det(A)}c_i$ y $c_n=1$.

Entonces podemos encontrar $x$ a partir de una combinacion lineal de los vectores $b,A,A^2,\cdots A^{n-1}b$.

>[!INFO] Nota
>Si bien podemos sacar el $b$ de la sumatoria no es recomendado!.
>En terminos computacionales, el producto matriz-vector es de orden $O(n^2)$ operaciones, mientras que el productor matriz-matriz es del orden de $O(n^3)$.
>Por lo que calcular $Ab$ primero y luego el $AbA$ toma $2n^{2}$  operaciones, en comparacion de $n^3+n^2$ si realizamos $AA$ primero!.

Esta combinacion lineal de vectores genera un [[Espacios Vectoriales|sub-espacio vectorial]], cuyo $span$  de los primeros $k$ vectores es:
$$\mathcal{K}_k=span(b,Ab,A^2b,\cdots A^{k-1}b)$$
Donde $\mathcal{K}_k$ se conoce como el sub-espacio de Krylov.
Observar que no se estan utilizando los $n$ vectores, si no que solamente $k$. La idea de esto, es buscar una aproximacion de $x$, $x_k$, restringiendolo al sub-espacio de Krylov $\mathcal{K}_k$ de tal forma que minimize el error cuadratico $||\boldsymbol{b}-Ax_k||_2^2$.  Notar que si $k=n$ por el teorema de Cayley Hamilton, efectivamente daremos con la solucion exacta.



# Derivación

Recordar las dimensiones de los elementos en los que se trabajan:
- $A \in \mathbb{R}^{n\times n}$
- $x \in \mathbb{R}^{n}$
- $b \in \mathbb{R}^{n}$
- $A^{j}b \in \mathbb{R}^{n}$

El subespacio de Krylov $\mathcal{K}_k$ es un sub-espacio de $R^n$. Cada elemento de $\mathcal{K}_k \in \mathbb{R}^n$, sin embargo no podemos representar todos los elementos de $\mathbb{R}^n$ ya que solamente tenemos $k$
vectores.

>[!INFO] Nota
>Solo requerimos que $x \in  \mathcal{K}_k$. Es decir, que la solución del sistema de ecuaciones lineales esté en $\mathcal{K}_k$. Si esto ocurre, el algoritmo terminará en k iteraciones y habremos encontrado la solucion exacta!

Que significa que $x_k \in  \mathcal{K}_k$? Significa que solamente que $x_k$ debe ser representado por una combinacion lineal de vectores basales que generen al sub-espacio de Krylov, es decir:
$$
x_k = \tilde{c_1}b+\tilde{c_2}Ab+\tilde{c_3}A^2b+\cdots+\tilde{c_{k}}A^{(k-1)}b
$$

Cuya forma matricial es:
$$
x_k=
\begin{bmatrix}
b & Ab& A^2b&\cdots &A^{k-1}

\end{bmatrix}

\begin{bmatrix}
\tilde{c_1}\\
\tilde{c_2}\\
\tilde{c_3}\\
\vdots\\
\tilde{c_k}

\end{bmatrix}
$$
Es decir el producto matriz-vector $x_k=K_k \tilde{c_k}$ .
Si volvemos a nuestro problema inicial:
$$
Ax=b
$$
Si hacemos $x=x_k$:
$$AK_k \tilde{c}_k=b$$
Notar que:
- A es una matriz $n \times n$
- K es una matriz $n\times k$
- $\tilde{c}_k$  ( desconocido) es un vector de $k$ dimensiones, es decir,  $k\times 1$

Es decir el producto $AK_k$ será $n\times k$, por lo que tenemos un sistema de $n$ filas y $k$ columnas, o sea $n$ ecuaciones y $k$ incognitas. Entonces tenemos un sistema sobre-determinado!, ya que $n>k$. 
O sea volvemos a [[Minimos  Cuadrados]]!
Esto significa que podemos encontrar una solucion que minimiza el error cuadratico de la forma:
$$
\tilde{c}_k=arg\min||b-AK_k\tilde{c}_k||_2^2
$$
El cual podemos resolver con [[Ecuaciones Normales]], [[Factorizacion QR]], etc.
Sin embargo, nos encontramos con un problema numerico, debido a que el problema de minimos cuadrado definido, utiliza una base mal condicionada del sub-espacio de Krylov. Esto se debe a que cada vez que aumenta el exponente, el angulo de los vectores $j$ y $j-1$ disminuye, haciendo que los vectores se parezcan más entre sí, o sea que en aritmetica de punto flotante, pueden ser **linealmente dependientes**.

![[Pasted image 20221110014841.png]]

Como podemos construir una nueva base del sub-espacio de Krylov, de forma de que los vectores basales esten bien condicionados y linealmente independientes?
La respuesta es [[Ortonormalizacion del Subespacio de Krylev|ortonormalizar]] la base.

Sea entonces la siguiente identidad:
$$
\mathcal{K}_k\tilde{c}=Q_kc_k
$$
Donde $Q_k$ es la nueva base ortonormal calculdada y $c_k$ es un nuevo vector, que no necesariamente es igual a $\tilde{c}$.
Por lo tanto transformamos el problema cuadratico en:
$$
\tilde{c}_k=arg\min||b-AQ_kc_k||_2^2
$$
Recordar la reduccion parcial a la forma de Hessenber vista en [[Ortonormalizacion del Subespacio de Krylev]], $AQ_k=Q_{k+1}\hat{H}_k$.
Reemplazando:
$$
\tilde{c}_k=arg\min||b-Q_{k+1}\hat{H}_kc_k||_2^2
$$

Ademas reescribimos el vector $b$ de forma conveniente recordando que $q_1=\frac{b}{||b||}\rightarrow b=q_1||b||$Podemos hacer que:

$$
\begin{align}
b &= ||b||q_1\\
&=||b||Q_{k+1}e_1
\end{align}
$$
Donde $e_1$ es el vector canonico que tiene un 1 en su primera componente y 0 en las demas.
Reemplamos nuevamente:
$$
\begin{align}
\tilde{c}_k&=arg\min||b-Q_{k+1}\hat{H}_kc_k||_2^2\\
 &=arg\min|| \lVert b \rVert Q_{k+1}e_1-Q_{k+1}\hat{H}_kc_k||_2^2\\
  &=arg\min||  Q_{k+1}(\lVert b \rVert e_1-\hat{H}_kc_k)||_2^2
\end{align}
$$
Recordar ahora que la norma 2 de un vector  puede ser definido como  el [[Producto Interno]] de el mismo vector con su transpuesta, es decir:
$$
\begin{align}
||Q_{k+1}(\lVert b \rVert e_1-\hat{H}_kc_k)||_2^2 &= (Q_{k+1}(\lVert b \rVert e_1-\hat{H}_kc_k))^T Q_{k+1}(\lVert b \rVert e_1-\hat{H}_kc_k)\\
&=(\lVert b \rVert e_1-\hat{H}_kc_k)^T Q^T_{k+1}Q_{k+1}(\lVert b \rVert e_1-\hat{H}_kc_k)\\
&=(\lVert b \rVert e_1-\hat{H}_kc_k)^T(\lVert b \rVert e_1-\hat{H}_kc_k)\\
&=||\lVert b \rVert e_1-\hat{H}_kc_k|||_2^2
\end{align}
$$

Por lo que finalmente tenemos la identidad 
$$
\tilde{c}_k=arg\min||\lVert b \rVert e_1-\hat{H}_kc_k|||_2^2
$$
Notar que $||b||e_1$ es el analogo al $b$ original, $\hat{H}$ es el analogo a la matriz $A$ y $c_k$ el anologo al vector de incognitas $c_k$.

Ver que $||b||e_i$ es de dimension $k$ (ya no $n$ !), $\hat{H}_k$ es dimension $k+1$ y $c_k$ de dimension $k$, por lo que es mucho más conveniente calcularlo.

Lo que es el siguiente sistema de ecuaciones lineales:
![[Pasted image 20221111043854.png]]

# Algoritmo

![[Pasted image 20221111113913.png]]

Partimos de un *initial guess* $x_0$, donde uno ya conoce algo de la solucion, entonces se puede reescribir el sistema  de ecuaciones lineales de la siguiente forma:

$$
\begin{align}
Ax&=b\\
A(x_0+y)&=b\\
Ay&=b-Ax_0\\
Ay&=\tilde{b}
\end{align}
$$
Es decir solo modifica el lado derecho convenientemente.

Es por esta razon que utilizamos $r_0=b-Ax_0$ ya que si usamos el vector nulo en $x_0$, recuperamos la formulación inicial de $q_1=\frac{b}{||b||}$.

Necesitamos almacenar $Q_{k+1}$  y $\hat{H}_k$ las cuales aumentan en funcion del numero de iteraciones $k$.

La matriz $A$ solo aparece en las lineas $2$ y $5$, esto siginifica que no se requiere acceder a los coeficientes de la matriz, solo necesitamos saber el producto por un vector, por lo que podemos reemplazar ese producto por una funcion por ejemplo, $afun(v)=Av$, es decir una funcion a la que se entregue un vector $v$ y retorne el producto de ese vector por la matriz $A$. Esta nos da una ventaja por ejemplo para resolver la [[Ecuacion de Sylvester]].

La linea 12 se encarga de resolver el problema de minimos quadrados una y otra vez, lo que implica obtener la [[Factorizacion QR]] reducida de $\hat{H}$ en cada iteracion. 

>[!WARNING] IMPORTANTE
>Los vectores ortonormales de la $QR$ reducida no son los mismo que los obtenidos con la iteracion de arnoldi de GMRES


Puede ser el caso de que el coeficiente $h_{k+1k}$ sea $0$, a este caso se le denomina GMRES **Breakdown**, esto significa que al tener este coeficiente igual a 0, el problema de minimizacion se puede resolver exactamente ya que se convierte en un sistema de dimension $(k+1)\times k$ a un sistema de ecuaciones lineales cuadrado, $k\times k$, es decir, resolvimos exactamente el problema original. En terminos formales significa que el residuo es $\tilde{c}_k=arg\min||\lVert b \rVert e_1-\hat{H}_kc_k|||_2^2=0$.

![[Pasted image 20221112044453.png]]