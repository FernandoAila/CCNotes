# Metodos Iterativos

[[Eliminacion Gaussiana]], [[Factorizacion LU]] y [[Factorizacion PALU]] se conocen como Metodos Directos, es decir, terminan luego de una cierta cantidad de operaciones elementales. El problema es cuando el tamaña del input, es decir la dimensionalidad del problema, crece.
Por ejemplo para diferentes tamaños de la dimensionalidad n:
![[Pasted image 20221007222314.png]]
Recordemos que tanto $LU$ como $PALU$ toma del orden de ~$\frac{2}{3}n^3$ operaciones elementales.

Los metodos iterativos aparecen como una alternativa a costa de entregar una solucion aproximada a un [[Sistemas de Ecuaciones Lineales|sistema de ecuacion lineal]].  Son ejemplo [[Iteracion de punto fijo|iteraciones de punto fijo]], [[Metodo de newton|metodo de newton]], etc. Donde se espera que al tener varias iteraciones el algoritmo converja.
En particular, para resolver sistemas de ecuaciones lineales, tenemos varias, por ejemplo:
- [[Metodo de Jacobi]]
- [[Metodo de Gauss Seidel]]
Ambos provienen de la misma deduccion a partir de la factorizacion $L+D+U =A$. Donde $L$ es una matriz triangular inferior, $D$ una diagonal y $U$ una triangular superior.
Esto se puede resumir como:
![[Pasted image 20221022182408.png]]
Ambos metodos poseen la misma [[Convergencia de metodos iterativos|Convergencia]].