En  algoritmos anteriores, se concluyó que la integración numerica se puede escribir como el producto punto entre un vector de pesos $w$ y unos noddos $x$ ,es decir:
$$w f(x)=\sum_{i=i}^{n} w_if(x_i)$$
La pregunta entonces es que si existe una buena forma de elegir los pesos $w_i$ y los nodos $x_i$ para obtener la cuadratura $\int_a^b f(x)dx$ con el menor error posible. 
La respuesta es que estos ya existen y ya están tabulados (entregados).

De [[Interpolacion en 1D]] sabemos que podemos tomar una funcion y aproximarla por un polinomio, por ejemplo, utilizar la [[Interpolación de Lagrange]], es decir:
$$
f(x) \approx Q(x) = \sum_{i=1}^n L_i(x)f(x_i)
$$
Por lo que si realizamos la tarea de integrar $f(x)$ en el intervalo $[-1,1]$:

$$
\begin{align}
\int_{-1}^1 f(x)dx &\approx \int_{-1}^1 Q(x)dx=\int_{-1}^1 \sum_{i=1}^n L_i(x)f(x_i)dx\\
&=\sum_{i=1}^n f(x_i) \underbrace{\int_{-1}^1 L_i(x)}_{w_i} dx
\end{align}
$$
Notar que los $L_i(x)$ dependen de $x$.
Recordar que 
$$L_i=\frac{l_i(x)}{l_i(x_i)}$$ y  
$$l_i(x)=(x-x_1)(x-x_2)(x-x_3)\cdots(x-x_{i-1}) (x-x_{i+1})\cdots(x-x_n)$$
donde $L_i(x_i)=1$ y $L_i(x_j)=0$.
Por lo que la tarea radica en encontrar puntos $x_i$ convenientes.
Estos nodos se definen como las raices del n-esimo polinomio de Legendre $p_n(x):$

$$
p_n(x)=\frac{1}{2^nn!}\frac{d^n}{dx^n}(x^2-1)^n
$$
Estos son:
$$\begin{align}
p_1(x)&=1\\
p_2(x)&=x\\
p_3(x)&=\frac{1}{2}(3x^2-1)\\
p_4(x)&=\frac{1}{2}(5x^3-3x)\\
p_5(x)&=\frac{1}{8}35x^4-30x^2+3
\end{align}$$


Notar que si queremos realizar la cuadratura gaussiana en un intervalo $[a,b]$ tenemos que realizar cambio de variable al intervalo $[-1,1]$ de la forma:
$$
\int_{a}^bf(x)dx=\int_{-1}^{1}f(\frac{b-a}{2}u+\frac{a+b}{2})\frac{dx}{du}du
$$
Con $\frac{dx}{du}=\frac{b-a}{2}$ dado que definimos la función $x(u)=\frac{b-a}{2}u+ \frac{a+b}{2}$
Es decir, el algoritmo de cuadratura gaussiana resulta como:
$$
\int_{a}^{b}f(x)dx \approx \frac{b-a}{2} \sum\limits_{i=1}^nw_if(\frac{b-a}{2}u_i+\frac{a+b}{2})
$$




![[Pasted image 20221126181540.png]]
Como ejemplo, para un solo punto, $n=1$:

![[Pasted image 20221126182430.png]]

Notar que la cuadratura será exacta si $f(x)$ es un polinomio de grado $n-1$ y se usan los nodos $x_i$ y pesos $w_i$ definidos anteriormente.

![[Pasted image 20221126183504.png]]

![[Pasted image 20221126185158.png]]




