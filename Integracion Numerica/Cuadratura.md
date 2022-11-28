
La idea de la Integracion numerica es obtener computacionalmente valores para aquellas integrales definidas que no se pueden resolver algebraicamente, por ejemplo:

$$
\int_a^b \frac{\sin x}{x}dx
$$

Esto es formalmente como:

>[!NOTE] Integracion numerica
>Es la obtencion de la constante $c$ o una aproximacion de esta, de una integral definida de la forma:
>$$
c = \int_a^b f(x)dx$$
Utilizando algun metodo numerico.

Para los metodos que se estudiaran, se utliza el ejemplo de la exponencial:

$$
\int_{-1}^1 e^x=e^1-e^{-1}=2,3504023872876\cdots
$$

En particular la [[Cuadratura|integracion numerica]] puede ser considerada como un producto punto, es decir:
$$
\int_a^b f(x)dx=<(f_1,f_2,f_3,\cdots,f_m),(h,h,h,\cdots,h)>
$$
Donde $f_i$ es $f(x_{*_{i}})$, es decir, la funcion evaluada en ciertos puntos particulares y h un peso asignado.

Algunos metodos son:
- [[Suma de Riemann]]
- [[Regla del Punto Medio]]
- [[Regla del Trapecio]]
- [[Regla de Simpson]]
- [[Cuadratura Gaussiana]]






>[!NOTE] Grado de exactitud
>Una regla de cuadratura $\sum_{i=1}^n w_if(x_i)$ tiene grado de exactitud $m$ si entrega el resultado exacto cuando la funcion $f(x)$ es cualquier polinomio de grado no mayor a "$m$" y no es exacta para todos los polinomios de grado mayor.
