Existen diferentes modelos en donde es posible aplicar minimos cuadrados. Algunos modelos son lineales en relacion a sus coeficientes que se buscan, por lo que se puede aplicar directamente la teoría en [[Minimos Cuadrados por Minimizacion]] o en [[Ecuaciones Normales]], pero algunos son no-lineales por lo que combiene realizar un cambio de variable.

## Modelo Lineal

Este modelo es el visto originalmente, y tiene el siguiente sistema de ecuaciones lineales sobre-determinado:

$$\begin{bmatrix}
1 & t_1 \\
1 & t_2  \\
1 & t_3 \\
\vdots&\vdots\\
1& t_m 
\end{bmatrix}
\begin{bmatrix}
c_1\\
c_2
\end{bmatrix}
=
\begin{bmatrix}
y_1\\
y_2\\
y_3\\
\vdots\\
y_m
\end{bmatrix}
$$
Que es de la forma $$y=c_1+c_2t$$
Y se obtiene simplemente aplicando $A^TA\overline{x}=A^T\boldsymbol{\vec{b}}$.
![[Pasted image 20221030232138.png]]


## Modelo cuadratico

Corresponde a la extension del modelo lineal de la forma:

$$\begin{bmatrix}
1 & t_1 & t_1^2\\
1 & t_2 &t_2^2 \\
1 & t_3 & t_3^2\\
\vdots&\vdots\\
1& t_m & t_m^2
\end{bmatrix}
\begin{bmatrix}
c_1\\
c_2
\end{bmatrix}
=
\begin{bmatrix}
y_1\\
y_2\\
y_3\\
\vdots\\
y_m
\end{bmatrix}
$$
Y se obtiene de la misma forma aplicando $A^TA\overline{x}=A^T\boldsymbol{\vec{b}}$.
Si bien los datos, no se comportan de manera lineal, el sistema de ecuaciones es lineal, ya que los coeficientes $c_i$ si lo son.

![[Pasted image 20221030232617.png]]

## Modelo periódico

Corresponde a un modelo adecuado en caso de que los datos presente un comportamiento oscilatorio o periodico.
El modelo queda expresado como:
![[Pasted image 20221030233240.png]]
Y se obtiene de la misma forma aplicando $A^TA\overline{x}=A^T\boldsymbol{\vec{b}}$.

![[Pasted image 20221030233301.png]]


## Modelo exponencial

Ocurre cuando los datos crecen más rapido que un modelo lineal o cuadratico y tiene la forma:
$$y=c_1\exp(c_2t)$$
![[Pasted image 20221030234840.png]]
Notar que claramente el modelo no es lineal en relacion a los coeficientes $c_i$, por lo que no podemos aplicar directamente el metodo de minimos cuadradods. Para este caso tenemos dos opciones:
- Utilizar minimos cuadrados no lineales.
- Transformar el problema no lineal en $c_1$ y $c_2$ en uno lineal respecto a nuevas variables.

Para el segundo caso la transformacion es bastante directa al aplicar la funcion logartimo:
$$\begin{align}
y&=c_1\exp(c_2t)\\
\log(y)&=\log(c_1\exp(c_2t))\\
\log(y)&=\log(c_1)+\log(\exp(c_2t))\\
\log(y)&=\log(c_1)+c_2t\\
\end{align}$$

Si bien aún el modelo no es lineal, notemos que $\log(c_1)$ es solamente un coeficiente, por lo que lo podemos reescribir como $K=\log(c_1)$, luego:
$$
\log(y)=K+c_2t
$$
Que claramente es lineal respecto a $K$ y $c_2$. Luego de obtener $\overline{K}$, podemos recuperar $c_1$ aplicando la operacion inversa, $c_1=\exp(K)$.

Por lo que el sistema de ecuaciones lineales es:
![[Pasted image 20221030234544.png]]

Y es posible aplicar $A^TA\overline{x}=A^T\boldsymbol{\vec{b}}$.


## Modelo de potencia

Corresponde a una variante del modelo exponencial anterior donde: $$y=c_1t^{c_2}$$

![[Pasted image 20221030234951.png]]


De la misma forma que el metodo anterior, el modelo no lineal respecto a los coeficientes por lo que aplicamos logartimo y realizamos un cambio de variable:
$$\begin{align}
y&=c_1t^{c_2}\\
\log(y)&=\log(c_1t^{c_2})\\
\log(y)&=\log(c_1)+\log(t^{c_2})\\
\log(y)&=\log(c_1)+c_2\log(t)\\
\end{align}$$
Y definimos $K=\log(c_1)$.

Lo que resulta en el sistema de ecuaciones lineales:
![[Pasted image 20221030235614.png]]

Por lo que  es posible aplicar $A^TA\overline{x}=A^T\boldsymbol{\vec{b}}$ y luego obtener $c_1=\exp(K)$.
