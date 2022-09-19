# Estandar del punto flotante




## Numeros Binarios

Un numero binario con decimales se representa como:
![[Pasted image 20220824094727.png]]
Donde $b_i$ , aka, 1 bit, equivale a 0 o 1.

Para convertir un numero binario a decimal simplemente multiplicamos $b_i \cdot i$ y lo sumamos, es decir:
$$\sum^\infty b_i \cdot i $$
![[Pasted image 20220824095159.png]]

- Notar que los digitos despues del punto tienen exponente negativo.

Para convertir un numero decimal a binario, dividimos repetitivamente su parte entera (antes de la coma), hasta que este sea 0. El resultado en binario sera el inverso de los restos de la division.
![[Pasted image 20220824095526.png]]

Por lo tanto la parte entera se expresa como $111000$.

Para la parte decimal,  multiplicamos repetetivamente por 2 obteniendo la parte entera:
![[Pasted image 20220824095813.png]]

Por lo tanto su parte decimal corresponde a $.1011001100110 \cdots$ , lo que se repite indefinidamente, siendo un numero periodico.

## Punto Flotante
"Notacion cientifica en base 2"
![[Pasted image 20220824083019.png]]


Ejemplos:![[Pasted image 20220824083155.png]]

- Notar que el exponente es el corrimiento de la coma hasta el "primer" 1.

### El numero 1 y 2 en double precision

![[Pasted image 20220824084135.png]]

![[Pasted image 20220824084148.png]]


- Cuantos numeros hay entre 1 y 2?: $2^{52}-1$  (cantidad de 0's cambiables) (-1 por que hay que descontar el caso donde hay solo ceros y estariamos contando el 1)
- Cuantos numeros hay entre 2 y 4: $2^{52}-1$  (solo cambia el exponente)
- Cuantos numeros hay entre 4 y 8: $2^{52}-1$  (solo cambia el exponente)
- Cual es el siguiente numero representable?: $1 + 2^{-52}$  (cambiamos el ultimo cero a uno)

Este ultimo resultado es muy importante para entender las limitaciones que posee el formato descrito, a este siguiente numero representable despues del 1 lo llamamos [[Machine Epsilon]].

Hasta el momento, se ha estudiado principalmente el comportamiento de la mantissa, por lo que queda ver la forma del manejo del signo y el exponente para entender que es lo que ocurre al almacenar un "numero real x" en el computador a traves de su  [[Representación de maquina]]. Debido a que se maneja con recursos limitados, en este caso memoria finita,  es que solo tenemos ciertos bits disponibles para representar un numero x, esto requiere definir una [[Regla del redondeo]] que permita decidir como transformar un numero con más decimales que los que tenemos, por ejemplo, decimales periodicos. Esta regla, y otras caracteristicas más del estandar de punto flotante, lleva dar a lo que se llama la [[Perdida de la Importancia]].
