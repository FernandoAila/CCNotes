>[!NOTE] Error de interpolacion
>Sea $p(x)$ el polinomio interpolador de grado n-1 o menor que ajusta a $n$ puntos $(x_1,y_1),\cdots, (x_n,y_n)$.
>El error de interpolacion es:$$f(x)-p(x)=\frac{(x-x_1)(x-x_2)\cdots(x-x_n)}{n!}f^{(n)}(c)$$
>Donde $c$ es un numero entre el mayor y el menor de los numeros $x_i$

Esta definicion tiene 3 cosas clave:
- El $n!$ induce a que a medida que aumentamos los puntos, la diferencia entre $f(x)$ y $p(x)$ es decir el error de interpolacion, disminuye. Sin embargo al aumentar los puntos tambien estamos requierendo una mayor computacion y por lo tanto estamos aumentando el tiempo de ejecucion.
- El termino $f^{(n)}(c)$ depende exclusivamente de la derivada de la funcion a interpolar por lo que no tenemos control sobre esta.
- $(x-x_1)(x-x_2)\cdots(x-x_n)$ este termino indica que el error de interpolacion depende de los puntos utilizados para interpolar. Una distribucion sencilla de puntos para interpolar una funcion utlizando un polinomio son puntos equiespaciados. Sin embargo, es posible encontrar una buena distribucion de puntos, de forma que el error sea pequeño y que la cantidad de puntos sea minima?.


## Fenomeno de Runge
Para ejemplificar el problema de los puntos espaciados, considere los siguientes 9 puntos equiespaciados en  $[0,1]$.
![[Pasted image 20221023194215.png]]

 Notar como oscila la evaluacion del polinomio entre puntos de interpolacion en los extremos del intervalo. Esta oscilacion aumenta significativamente al aumentar la cantidad de puntos a interpolar. Las oscilaciones no dependen de la data interpolada sino que del uso de los puntos equispaciados en la interpolacion.
 Para reducir este fenomeno y reducir el error de interpolacion es que se utiliza los llamados [[Puntos de Chebyshev]].

