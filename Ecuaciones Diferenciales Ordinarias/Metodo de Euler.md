Sea una estructura general de un [[Problemas de valor inicial|IVP]] de la forma:
$$
\dot{y}=f(t,y(t))
$$
Podemos integrar a ambos lados con respecto a una variable $s$, entre $t=0$  y $t=1$es decir:
$$
\int_{0}^{t_{1}}\dot y(s)ds=\int_{0}^{t_1}f(s,y(s))ds
$$
Notar que si bien $f$ tiene dos argumentos, al final de cuentas el segundo argumento también depende de la misma variable $s$.

Usando el teorema fundamental del calculo y reemplazando la condición inicial $y(0)=y_0$,  y haciendo $g(s)=f(s,y(s))$:
$$
y(t_1)=y_0+\int_{0}^{t_1}g(s)ds
$$
Conocemos el valor $y_0$ y la forma de la función $g(s)=f(s,y(s))$, sin embargo, no conocemos el valor de $y(s)$.
Una forma de encontrar el valor de la integral es utilizando [[Cuadratura|Integración numerica]], sin embargo necesitamos elegir un método.
Por ejemplo, si queremos utilizar 2 puntos de [[Cuadratura Gaussiana]] se traduce en lo siguiente:
$$
\int_{0}^{t_1}g(s)ds = \frac{t_1}{2} \left(w_1g\left(\frac{t_1}{2}\left(x_{1}+1\right)\right)+ w_2g\left(\frac{t_1}{2}\left(x_{2}+1\right)\right)\right)
$$
Con $g\left(\frac{t_1}{2}\left(x_{1}+1\right)\right)=f\left(\frac{t_1}{2}\left(x_{1}+1\right), g\left(\frac{t_1}{2}\left(x_{1}+1\right) \right)  \right)$ y $g\left(\frac{t_1}{2}\left(x_{2}+1\right)\right)=f\left(\frac{t_1}{2}\left(x_{2}+1\right), g\left(\frac{t_1}{2}\left(x_{2}+1\right) \right)  \right)$

En particular para $n$ puntos:
$$
\int_{0}^{t_1}g(s)=\sum\limits_{i=1}^{n}\widehat{w_i}g(\widehat{x_i})=\sum\limits_{i=1}^{n}\widehat{w_i}f(\widehat{x_i},y(\widehat{x_i}))
$$
Notar que los pesos y los nodos no están considerados en el intervalo comun de $[-1,1]$.
Pero no conocemos la forma de $y$ !. ya que es justo lo que estamos buscando. 
Por lo que no funciona Cuadratura Gaussiana para este caso.
En particular para otros metodos:
![[Pasted image 20221127013057.png]]

Donde notamos que el unico metodo que no depende de tener la función $y$ es la 
[[Suma de Riemann]] por la izquierda!.
En resumen, hemos construido un algoritmo capaz de encontrar una aproximación a $y(t_1)$ es decir:
$$
y(t_1)=y_0+\int_{0}^{t_1}f(s,y(s))ds\approx y_0+f(0,y_0)t_1
$$
De la cual obtenemos nuestra aproximacion de $y(t_1)$,  la cual llamaremos $y_1$:
$$
y_1=y_0+f(0,y_0)t_1
$$
y de modo general:
$$
y_{i+1}=y_i+f(t_i,y_i)(t_{i+1}-t_i)
$$
con $i \in [0,1,2,3,\cdots]$. En general el termino $t_{i+1}-t_i$ es llamado $\Delta T$ o $h$ y suele ser equispaciados.

Este algoritmo es conocido como el **metodo de euler** el cual es:

![[Pasted image 20221127025955.png]]

Donde:
- $t_0$ es el tiempo de la condicion inicial $y(t_0)=y_0$
- $T$ es el intervalo a obtener la aproximacion numerica, $t=[t_0,T]$
- $N$ numero de puntos de la discretizacion temporal
- $y_0$ condicion inicial , $y(t_0)=y_0$
- $f$ Función $f(t,y)$ que recibe 2 parametros, $t$ y $y$. Es la funcion que define el IVP: $\dot y=f(t,y)$.
- $t$ e $y$ son los vectores que representan la data $(t_i,y_i)$.


## Error inducido del método de Euler

Considerar que se aplica el metodo de Euler para $\dot y=f(t,y(t))$ y $y(0)=y_0$ en el tiempo $t=t_i$ y $y(t_i)=y_i$ con paso $h$, lo que se traduce en un paso cualquiera del metodo:
$$
y_{i+1}= y_i+hf(t_i,y_i)
$$

Por otro lado, el valor exacto en el tiempo siguiente no es más que $y(t_{i+1})=y(t_i+h)$, por lo que si expandimos con taylor considerando que $h$ es pequeño:
$$
y(t_{i+1})=y(t_i+h)=y(t_{i})+\dot{y}(t_{i})h+ y''(c)\frac{h^2}{2} 
$$

Recordando la definicion de la ODE, $\dot y=f(t,y(t))$, podemos evaluar en $t=t_i$ y obtenemos $\dot y(t_i)=f(t_i,y(t_i))$:

$$
y(t_{i+1})=y(t_i+h)=y(t_{i})+f(t_i,y(t_i)h+ y''(c)\frac{h^2}{2} 
$$

Comparamos ahora el valor exacto $y(t_{i+1})$ con su aproximación $y_{i+1}$ calculando su error, es decir:
![[Pasted image 20221127164926.png]]
![[Pasted image 20221127170522.png]]

>[!NOTE] Lipschitz continua
>Una función $f(t,y)$ es Lipschitz continua en la variable $y$ en el rectangulo $S=[a,b]\times[\alpha,\beta]$  si existe una constante $L$ que satisface:
>$$
>|f(t,y_1)-f(t,y_{2}) |\leq L|y_{1}-y_{2}|$$ 
>Para cada $t,y_1$ y $t,y_2$ en $S$

Está definición nos dice que si tenemos una función de 2 variables, si la funcion es de tipo Lipschitz continua significa que la diferencia entre $|f(t,y_1)-f(t,y_{2}) |$ está acotada por una constante $L$ por la diferencia de los segundos argumentos de las funciones.

Una vez teniendo este resultado, tenemos que:
![[Pasted image 20221127171242.png]]

Por lo que podemos decir que el error del metodo de Euler es $|y(t_{i})-y_{i}|=O(h)$ .
Esto significa que el metodo de Euler es de orden 1 lo que implica que si el $h$, es decir el largo entre los equispaciados, disminuye a la mitad el error también disminuye en en la mitad.
![[Pasted image 20221127173046.png]]
