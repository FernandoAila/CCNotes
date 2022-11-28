![[Pasted image 20221127225625.png]]

Notar que calculamos 4 pendientes
Este metodo tiene orden de convergencia $O(h^4)$, es decir de orden 4, por lo que si se reduce $h$  a la mitad, el error se reduce 16 veces!.

![[Pasted image 20221127225728.png]]

![[Pasted image 20221127225850.png]]

Notar que $k_1$ es la pendiente en el primer punto, $k_2$ la pendiente en el punto medio, $k_3$ es una mejora de la pendiente y $k_4$ es una estimacion de la pendiente en el ultimo punto.

Notar que claramente este metodo resulta mucho más costoso que el [[Metodo de Euler]], aproximadamente, 4 veces más de acuerdo al codigo.