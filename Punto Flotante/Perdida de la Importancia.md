# Perdida de la Importancia
Existen casos donde al realizar operaciones númericas, como sumar, restar, multiplicar, etc. al trabajar con una cierta cantidad de bits para la representacion de punto flotante, es posible perder algunos bits de informacion debido a la [[Regla del redondeo]] antes vista.


Por ejemplo, si queremos sumar $n_1+n_2$, primero tenemos que alinear el exponente a un valor igual, por ejemplo, corriendo la coma 2 veces  hacia la izquierda de $n_1$.
![[Pasted image 20220824124409.png]]
Si realizamos la suma, tenemos que:
![[Pasted image 20220828152749.png]] 
La regla del redondeo dice que tenemos que sumar 1 al bit 52, por lo tanto:
![[Pasted image 20220828153522.png]]

Claramente del resultado vemos que lo obtenido no es lo mismo que lo teoríco, dado que se tuvo que aplicar la regla del redondeo.

Estos casos de perdida de significancia pueden ocurrir por diferentes motivos:
#### Números con ordenes de magnitud muy diferentes
Por ejemplo, supongamos que queremos sumar los numeros $m_1 = 1$,$m_2=2^{-55}$ y $m_3=-1$ ![[Pasted image 20220828160801.png]]

Tenemos varias formas de sumar esos numeros, por ejemplo:
1. $(m_1+m_2)+m_3$
2. $(m_1+m_3)+m_2$
Claramente a simple vista el resultado es $2^{55}$
Para saber cual algoritmo es el mejor realizamos los dos algoritmos:
Para el primer algoritmo:
![[Pasted image 20220828161501.png]]

Donde el resultado es 0.

>[!INFO] El cero en punto flotante
> El numero $0$ puede tener 2 representaciones en punto flotante, la representación normal y la subnormal.
>- Notación normal: $\pm0.000\cdots000\cdot2^0$>-
>- Subnormal: $\pm0.000\cdots000\cdot2^{-1022}$

Para el algoritmo 2 se tiene que:

![[Pasted image 20220828163842.png]]

![[Pasted image 20220828163901.png]]

Cuyo resultado es $2^{55}$ y claramente el correcto.

Como resumen, para evitar este caso, es recomendable sumar primero aquellos números cercanos en orden de magnitud entre sí.


#### Cancelación Catastrofica
Esta situacion ocurre cuando substraimos dos valores muy cercanos entre sí,  por ejemplo,  en el caso de la solución a la ecuacion cuadratica $ax^2+bx+c=0$:$$\frac{-b\pm\sqrt{b^2-4ac}}{2a}$$
Donde si $b>>> -4ac$ entonces el denominador queda en 0 y por lo tanto el resultado es 0.
Otro caso comun es del logaritmo