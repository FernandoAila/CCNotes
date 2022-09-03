# Raices en 1D

Obj:  Buscar ceros, o raices, de una función.

Def: $f(x)$ tiene una raiz en $x=r$ si $f(r) =0$.
Es decir cuando la función "cruza" el eje $x$.

![[Pasted image 20220831221430.png]]

>[!INFO] Tip
Podemos facilmente, buscar la raiz de cualquier función igualandola a "cero", de la forma $$g(x)=f(x)-a$$$$4x+1=2$$$$4x+1-2=0$$

Buscar raices, tiene muchas aplicaciones, por ejemplo al buscar el máximo o minimo de una función tenemos que hacer la derivada de $f(x)$ igual a 0, $f'(r)=0$.

No siempre existen raices de una funcion, ejemplo:
$$sin(x)=2$$
Como $-1 \leq sin(x) \leq 1$, entonces la función nunca llega a tener el valor 2, por lo que se dice que no tiene raiz.




## Metodo de la bisección

Recordar el siguiente teorema de bolzano:
>[!NOTE] Teorema de bolzano
>Si $f$ es continua en $[a,b]$ y $f(a)f(b) < 0$, entonces $f$ tiene una raiz entre a y b.
 ![[Pasted image 20220831225520.png]]

Podemos crear un algoritmo para encontrar la raiz de una función utilizando esta informacion, sin embargo, hay que notar que se necesita conocer tanto $a$ como $b$, osea, una *initial guess*:

### Algoritmo
 Idea basica: Tomar el punto medio (initial guess) del intervalo $[a,b]$ y evaluarlo en $f$. $f((a+b)/2)$ de tal forma de elegir un nuevo subintervalo donde se conserve la alternancia de signo. Realizar sucesivamente estas operaciones hasta que el valor del intervalo sea menor a una tolerancia TOL.
![[Pasted image 20220831232123.png]]
#### Pseudocodigo
1. Mientras el largo del intervalo $(b-a)/2$  sea mayor a una tolerancia TOL:
	1.  Tomar el punto medio entre a y b, $c=\frac{a+b}{2}$
		1. Si el $f(c)=0$, tenemos nuestra raiz.
		2. Si no, ver cuales de los intervalos $[a,c]$ y $[c,a]$ cambian de signo y elegirlo, es decir $f(a)f(c)\leq0$ o $f(b)f(c)\leq0$
	2. Hacer $a = c$ o $b=c$ .
2. Retornar el punto medio calculado.

Cada vez que avanzamos de iteracion el largo intervalo se reduce a la mitad.
Por lo tanto:
- Largo inicial: $b-a$
- Largo 1° iteracion: $\frac{b-a}{2}$
- Largo 2° iteracion: $\frac{b-a}{2}\cdot \frac{1}{2}=\frac{b-a}{4}$
- $\cdots$
- Largo n-esima iteracion: $\frac{b-a}{2^n}$

Claramente nuestra initial guess, c o  $x_c$ está en el intervalo $[a,b]$, por lo tanto la distancia entre la raiz que queremos encontrar, $r$,  y $x_c$ va a ser menor  o igual que el largo de la mitad del intervalo.
Por lo tanto satisface que:
$$|x_c^0-r|\leq\frac{b-a}{2}$$


Para la n-esima iteracion:
$$\text{Error absoluto = }|x_c^n-r|\leq\frac{b-a}{2^{n+1}}$$

Esto es especialmente útil para encontrar la cantidad de iteraciones o las evaluaciones de $f(x)$ necesarias para acotar el error, ya que estas ultimas seran $n+2$, ya que estamos contando las evaluaciones de a y b al principio.

>[!NOTE] Definicion
>Una solución es correcta  en $p$ decimales si el error absoluto es menor a $0.5\cdot10^{-p}$

Ej: Determinar cuantas evaluaciones de $f(x)=\cos x-x$ son necesarias para encontrar su raiz en el intervalo $[0,1]$ con una precision de 6 decimales.

Sol: $$\frac{1-0}{2^{n+1}}<0.5\cdot10^{-p}$$$$n>\frac{6}{log_{10}2}=19.9$$

Por lo que necesitamos $20+2=22$ evaluaciones.


## Iteracion de punto fijo

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

### Diagrama Cobweb
Iterpretacion grafica de la iteracion de punto fijo.

Para esto sea la siguiente funcion $g_1(x)= -\frac{3}{2}x+\frac{5}{2}$, con *initial guess* $x_0=1.1$ y 20 iteraciones. Una forma de ver el comportamiento es calcular las 20 iteraciones y ver los numeros se "acercan" a un valor.![[Pasted image 20220902214403.png]]

Claramente $g(x)$ diverge. Podemos utilizar un diagrama cobweb para analizar mejor los resultados obtenidos.

![[Pasted image 20220902215807.png]]
Podemos entender la iteracion de punto fijo, como la **interseccion** de dos funciones, $y=g(x)$ y $y=x$. Si el punto fijo existe, será la interseccion de las dos funciones, es decir en el punto, $(r,r)$.
Esto se conecta con la busqueda de ceros, restando las dos funciones.
Por otro lado, sea la funcion $g_2(x)=-\frac{1}{2}x+\frac{3}{2}$