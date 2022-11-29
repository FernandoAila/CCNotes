Un IVP clasico es el siguiente:
$$ \begin{align*}
y'(t)&=y(t)\\
y(0)&=1\\
t &\in [0,T]
\end{align*}  $$
Que tiene todos los componentes clasicos:
- Una ODE $y'(t)=y(t)$
- Una condicion inicial: $y(0)=1$
- Un intervalo de tiempo donde se quiere resolver la ODE: $t \in [0,T]$

Por ejemplo, digamos que una solución candidata para resolver el problema es:
$$
\hat{y}(t)=1
$$

Claramente, cumple con la condicion inicial de $y(0)=1$ y que esté definida  entre 0 y $T$ ya que es continua en ese intervalo. Sin embargo, no cumple que el requirimiento de que la derivada de está sea igual a la función ya que $\hat{y}'(t)=0 \neq \hat{y}(t)$.

La solución a esta ODE es la funcion exponencial ya que $y'(t)=y(t)=e^{x}$, $y(0)=1$ y es continua y diferenciable en $[0,T]$.

![[Pasted image 20221126220023.png]]


La forma general del problema IVP es:
$$
\begin{align*}
\dot{y} &= f(t,y(t))\\
y(0)&=y_0\\
t&\in[0,T] 
\end{align*}
$$
donde  $\dot{y}$ representa la derivada con respecto a $t$ de la función $y(t)$, si aparecen dos puntos corresponde a la segunda derivada, $f(t,y(t))$ es una función de dos variables que tiene como argumento el tiempo $t$ y una función $y(t)$  la cual es conocida, $y_0$ es la condición inicial entregada.
En el caso anterior, la ODE $\dot y = y$, la funcion solo dependía del segundo argumento.

Los IVP se clasifican en dos categorias:
- Sistemas No-autonomos: $\dot{y}=f(t,y)$, es decir la función $f$ depende explicitamente de $t$
- Sistemas autonomos: $\dot{y}=f(y)$, es decir la función $f$ depende solamente del segundo argumento $y(t)$.


Un ejemplo de un sistema no-autonomo:
$$
\begin{align*}
\dot{y} &= ty+t{^3}\\
y(0)&=1\\
t&\in[0,1] 
\end{align*}
$$
Cuya solución es $y(t)=3\exp(t^2/2)-t^{2}-2$.

Y un ejemplo de sistema autonomo:
$$
\begin{align*}
\dot{y} &= cy\cdot(1-y)\\
y(0)&=y_0\\
t&\in[0,1]
\end{align*}
$$
Lo cual tiene solucion conocida:
$$
y(t)=
     \begin{cases}
       1, \text{para}\quad y_0=1\\
1-\frac{1}{1+\frac{y_0}{1-y_0}exp(ct)  } \quad \text{e.o.c} \\
     \end{cases}
$$
Una derivación inicial de distintos algoritmos de IVP es utilizando el [[Metodo de Euler]], la segunda nace del mismo algoritmo y se llama [[Backward Euler]].
Por otro lado los metodos [[Runge-Kutta 2 (RK2)]] y [[RK4]] suelen entregar mejores resultados ya que poseen un orden de convergencia mayor.