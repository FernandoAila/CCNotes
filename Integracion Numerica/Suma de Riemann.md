Una funcion es integrable cuando las sumas izquierdas y derechas de Riemann convergen a un mismo valor c:
$$
c = \int_a^b f(x)dx$$
La suma de Riemann por la izquierda se entiende como:
$$
c = \int_a^b f(x)dx = \sum_{i=1}^{m-1}f(x_i)(x_{i+1}-x_{i})+ E_L$$
Donde los puntos $x_i$ son una particion del intervalo de integracion $[x_0,x_1, \cdots,  x_n]$ y $E_L$ el error de aproximacion numerica.
Notar que vamos generando rectangulos de largo $(x_{i+1}-x_{i})$ ($\Delta x$) y de alto  $f(x_i)$, es decir, tomamos el punto de "arriba a la izquierda".

![[Pasted image 20221120200825.png]]
De la misma forma definimos la suma de Riemann por la derecha como:

$$
c = \int_a^{b}f(x)dx = \sum_{i=1}^{m-1}f(x_{i+1})\Delta x+ E_R$$

![[Pasted image 20221122210520.png]]


Notar que al tener los sub-intervalos $\Delta x$ cada vez más pequeños el error tiende a ser más pequeño así mejorando la calidad de la aproximación. Normalmente estos sub-intervalos son **equispaciados**.