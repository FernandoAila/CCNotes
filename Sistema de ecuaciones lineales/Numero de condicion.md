Se dice que una [[Matrices|matriz]] $A$ en un [[Sistemas de Ecuaciones Lineales]] esta bien condicionada si su numero de condición $\kappa$ es "cercano" a 1. En otro caso se dice que está mal condicionada. Una matriz $A$ mal condicionda nos dice que para un pequeño cambio en el vector $b$ en $Ax=b$, existe un gran cambio en la solucion del sistema de ecuaciones. De la misma forma si la matriz $A$ está bien condicionada, nos dice que el cambio en la solucion del sistema deberia ser igual de pequeño.

El numero de  condicion $\kappa$ es calculado como:
$$\kappa = ||A||_\infty ||A^{-1}||_\infty $$
Donde la norma infinito $||||_\infty$ es calculada como el maximo de la suma de las filas de $A$.

Como norma general, el logaritmo en base 10, del numero de condicion, nos entrega la cantidad de decimales perdidos de precision, es decir:
$$log(\kappa)=\# \text{ cantidad de decimales perdidos}$$.