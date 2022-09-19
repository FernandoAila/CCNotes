# Iteracion de punto fijo

Ej: Aplicar sucesivamente la funcion cos a un numero cualquiera resulta en que convergerá a un numero especifico.
$$
\begin{align}
x_0&=0\\
x_1&=\cos(x_0)=1\\
x_2&=\cos(x_1)=\cos(cos(x_0))\\
\vdots\\
x_\infty&=0.73908513321516...
\end{align}
$$
$$cos(x_\infty)=x_{\infty}=0.73908513321516...$$
$$\cos r=r$$
>[!WARNING]  Esto es diferente a una busqueda de ceros.


>[!NOTE] Definicion
>r es un punto fijo de $g(x)$ si $g(r)=r$
Notar que r, **NO** denota raiz
### Algoritmo

![[Pasted image 20220901152811.png]]

Para el caso del coseno esta es:
$$
x_{i+1}=\cos x_i 
$$ Donde $g(x)= \cos x$.

Notar que podemos interpretar esta iteracion de punto fijo, como la busqueda de ceros cuando $f(x)=  x-\cos x$ ("restar" $\cos x_i$ a ambos lados). Ya que si $r$ es un punto fijo de $g(x)$, significa que $g(r) = r$, por lo que $f(r)=r - cos(r)$. pero sabemos que $\cos r = r$  por lo que $f(r)=r-r=0$, o sea una raiz!

No siempre una función $g(x)$ puede converger a un número determinado, pero si converge es un punto fijo.

>[!INFO] Tip
>La idea es convertir el problema de busqueda de ceros, en un problema de encontrar el punto fijo de una funcion conveniente!.

Ej: Encontrar un raiz de $f(x)=x^3+x-1$ usando una iteracion de punto fijo

Lo primero es encontrar nuestro $g(x)$ de forma de que $g(x)$ converja. Para esto, tenemos muchas opciones, por ejemplo:
$$\begin{align}
x&=1-x^3 = g_1(x) \\
x&=\sqrt[3]{1-x}=g_2(x) \\
x&=\frac{1+2x^3}{1+3x^2} = g_3(x)
\end{align}
$$
Lo importante es elejir alguno que converja, y si se puede, rapidamente.

Una buena interpretacion grafica de la iteracion de punto fijo es utilizar el llamado [[Diagrama Cobweb]].


Podemos entender la iteracion de punto fijo, como la **interseccion** de dos funciones, $y=g(x)$ y $y=x$. Si el punto fijo existe, será la interseccion de las dos funciones, es decir en el punto, $(r,r)$. 
Esto se conecta con la busqueda de ceros, restando las dos funciones, tal como es muesta en los dos graficos,



![[Pasted image 20220902223256.png]]



Como determinamos si una iteracion de punto fijo converge? Claramente la determina la funcion, pero que componente? Para este caso, sería **la pendiente** de la funcion en el punto fijo.
Especificamente, una funcion diverge si la pendiente, es decir la derivada, del valor absoluto de la funcion evaluada en el punto fijo, es mayor que 1. Por otro lado, esta converge si la derivada de la funcion en valor absoluto, en el punto fijo,  es menor que 0. 
Si tomamos el primer caso de ejemplo, donde no existia convergencia, tenemos que la pendiente, es decir la derivada de la funcion es:
$$g´_1(x)=-\frac{3}{2}$$
### Convergencia
 >[!NOTE] Definicion
>Sea $e_i=|x_i-r|$ el error absoluto del paso i de un metodo iterativo, con $x_i$ como el valor computado y $r$ la raiz real de la funcion.
>Si se cumple que:
>$$\lim_{i\rightarrow\infty} \frac{e_{i+1}}{e_i}\approx S<1$$
>Entonces el metodo obedece una convergencia lineal con tasa S

Es decir, si el S, es decir el cuociente de errores, se va haciendo constante a partir de ciertas iteraciones, y es menor que 1, de dice que posee convergencia lineal.
Notar que, a primera vista, para calcular el error necesitamos calcular la raiz. Por otro lado, el S es variable para las iteraciones de punto fijo. Naturalmente queremos que el cuociente se vaya reduciendo con el paso de las iteraciones, ya que esto nos diria, que estamos "reduciendo" el error en relacion al paso anterior, y por lo tanto se reducen la cantidad de iteraciones. Por ejemplo, el metodo de la biseccion tiene tasa de convergencia $0.5$, ya que el error se reduce a la mitad cada vez que avanzamos en iteraciones (el largo del intervalo se reduce a la mitad).
Esto quiere decir que la mejor tasa de convergencia posible, es el valor 0.

A partir de esto, tenemos que:
$$\begin{align}
\frac{e_{i+1}}{e_i}&\approx S\\
e_{i+1}&\approx S\cdot{e_i}\\
e_{i+1}&\approx S\cdot (S\cdot{e_{i-1}})\\
e_{i+1}&\approx S^2\cdot{e_{i-1}}\\
\vdots\\
e_{i+1}&\approx S^i\cdot{e_{0}}\\
\end{align} 
$$

Independiente del error inicial, si S<1 y lo elevamos a un entero positivo, se reduce rapidamente.

 >[!NOTE] Definicion
>Si $g(x)$ es continua y diferenciable, y que tiene un punto fijo $g(r)=r$, y $S=|g´(r)|< 1$. Entonces la iteracion de punto fijo converge linealmente con tasa $S$ a $r$ para un  *intial guess* lo suficientemente cerca de $r$. (por ejemplo en el intervalo donde la derivada en abs sea menor que 1)



![[Pasted image 20220903221135.png]]

En el grafico se muestra la funcion $g(x)$ de una iteracion de punto fijo, la recta $y=x$ con el punto fijo $r$ que corresponde a la interseccion de las 2 rectas y en magenta $g'(x)$. Claramente vemos que $g(x)$ no converge a su punto fijo, debido a que la derivada de la funcion evaluada en el punto $r$ (la interseccion de $y=x$ y $g(x)$ ), es menor o mayor que 1.

Notar que necesitamos saber la raiz, para eso podemos utilizar una aproximacion para el S o una cota.
#### Demostracion
Para demostrar esta situacion utilizaremos el llamado **teorema del valor medio**:

>[!NOTE] Definicion: Teorema del valor medio
>Sea $f$ una funcion continua y diferenciable en $[a,b]$. Entonces existe un numero $c$ entre $a$ y $b$ tal que $f'(c) = \frac{f(b)-f(a)}{b-a}$ 
>![[Pasted image 20220917190833.png]]

Es decir que existe un numero c entre $[a,b]$ tal que la pendiente de la recta secante de $[a,b]$ es igual a $f'(c)$.

Entonces si $x_i$ es el i-esimo termino de la iteracion de punto fijo $x_i = g(x_{i-1})$ con *initial guess* $x_0$. Por el teorema del valor medio se tiene que:$$g'(c_i)=\frac{g(x_i)-g(r)}{x_i-r}$$
![[Pasted image 20220917192817.png]]

Como $g(r) = r$ y $g(x_i) = x_{i+1}$ por definicion de punto fijo se tiene: $$g'(c_i)=\frac{x_{i+1}-r}{x_i-r}$$

Moviendo el denominador al lado derecho:
$$g'(c_i) (x_i -r) = x_{i+1}-r $$
De acuerdo a la definicion de error $e_i = |x_i-r|$ :

$$g'(c_i) e_i = e_{i+1} $$
$$e_{i+1} = |g'(c_i)| e_i  $$

Si $S=|g'(r)| < 1$, entonces existe un pequeño vencindario alrededor de $r$, como $|r- \epsilon, r+ \epsilon|$.  tal que para todo $x$ en el vecindario $|g'(x) \leq \frac{S+1}{2}|$ donde claramente el promedio entre $1$ y $S$ es menor a $1$ pero mayor que $S$.

Por lo que para un $x_i$ suficientemente cerca de $r$ significa que $c_i$ está en el vecindario.

$$e_{i+1} = |g'(c_i)| e_i  \leq \frac{S+1}{2}e_i $$
Notemos que claramente $e_{i+1}$ va a ser menor a $e_i$, ya que $\frac{S+1}{2}$ es menor a 1. 

Lo que significa que el error decrece al menos con el factor $\frac{S+1}{2}$.
Obteniendo el cociente entre los errores y obteniendo el caso limite: $$\lim_{i\rightarrow\infty}\frac{e_{i+1}}{e_i}=\lim_{i\rightarrow\infty}|g'(c_i)|=|g'(r)|=S$$
Sin embargo, surge una pregunta, ¿como sabemos que la IPF convergera si no sabemos $r$?, ya que claramente es lo que se quiere buscar. Una idea es conocer la estimacion de S al ejecutar un para de iteraciones de punto fijo. Como $S \approx \frac{e_{i+1}}{e_i}$ y $e_i= |x_i-r|$ , aun necesitariamos saber $r$.
Otra cosa seria estimar el error $e_i$ como $|x_i-x_{i+1}|$ donde $x_{i+1}$ seria la aproximacion a $r$ y entonces  $S =\frac{e_{i+1}}{e_i}\approx \frac{|x_{i+1}- x_{i+2} |}{x_i-x_{i+1}}$.
