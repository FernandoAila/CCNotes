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



### Almacenamiento de numeros en memoria
![[Pasted image 20220824083347.png]]

### El numero 1 y 2 en double precision

![[Pasted image 20220824084135.png]]

![[Pasted image 20220824084148.png]]


- Cuantos numeros hay entre 1 y 2?: $2^{52}-1$  (cantidad de 0's cambiables) (-1 por que hay que descontar el caso donde hay solo ceros y estariamos contando el 1)
- Cuantos numeros hay entre 2 y 4: $2^{52}-1$  (solo cambia el exponente)
- Cuantos numeros hay entre 4 y 8: $2^{52}-1$  (solo cambia el exponente)
- Cual es el siguiente numero representable?: $1 + 2^{-52}$  (cambiamos el ultimo cero a uno)

### Machine Epsilon

El numero machine epsilon $\epsilon_{mach}$  se define la distancia entre 1 y el menor numero representable, aka, $2^{-52}$ en el formato double. 

Que es lo que ocurre cuando queremos representar un numero $x$ entre 1 y $\epsilon_{mach}$? ![[Pasted image 20220824103823.png]]

Tenemos 2 opciones:
- Cambiar el formato
- Mantenerlo y aproximar el numero.

Para este ultimo caso, por ejemplo, podriamos aproximar al siguiente numero si existe un 1 a la derecha del ultimo bit de la mantissa o truncar si es un cero, pero también hay que considerar el caso en que exista un empate.
![[Pasted image 20220824104514.png]]

### Regla del redondeo para precision double
- Si el 53 bit (despues del ultimo de la mantissa) es 0, truncamos despues del bit 52
- Si el 53 bit es 1:
	-  Si todos los bits conocidos a la derecha del 53 bit son 0, se agrega 1 al bit 52, si y solo si el bit 52 es 1. Este caso es cuando el numero se encuentra "a la mitad" del intervalo.
	- Si es otro caso, se agrega 1.

La siguiente figura muestra los casos anteriores, por ejemplo,  si el siguiente bit despues del 52 avo bit es 0, significa que estamos en la "primera mitad" del intervalo x1-x2.
Por otro lado, si el bit 53 es 1, y existe algun bit conocido que sea 1 en los bits posteriores, estamos en el segundo caso, es decir, en la "segunda mitad" del intervalo.
Si el bit 53 es 1, y todos los bits conocidos son 0, significa que nos encontramos justo al medio del intervalo, por lo que hay que decidir.

![[Captura de Pantalla 2022-08-27 a la(s) 15.44.09.png]]


### Importancia de $\epsilon_{mach}$

Se define el error absoluto, $e_{abs}$ ,con $x$ como el numero original y $x_c$  como la cantidad calculada como: $$e_{abs}=|x_c-x|$$
De la misma forma el error relativo, $e_{rel}$, se define como: $$e_{rel} = \frac{|x_c-x|}{|x|}$$
De estas definiciones se infiere a partir de lo anterior lo siguiente:$$e_{rel} \leq \frac{1}{2} e_{mach}$$
y$$e_{abs} \leq \frac{1}{2} e_{mach} |x|$$
La primera ecuación es facil de deducir, ya que nunca el error será mayor que la mitad del intervalo, a partir de lo visto anteriormente. Además de la segunda ecuacion se muestra que el error absoluta es proporcional al tamaño del numero real en cuestion, es decir si el numero real es más grande, el error va a ser mayor, debido a la cantidad de numeros representables entre el intervalo que se encuentra $x$ que depende de la mantissa.

Por ejemplo, si utlilizamos una representación de punto flotante, con 2 bits para la mantissa, se tiene que:
![[Pasted image 20220827165246.png]]

- Se puede apreciar que la cantidad de numeros representables entre potencias de 2 es la misma, lo que tiene sentido debido a que la mantissa no cambia (solo lo hace el exponente).
- El espaciado entre numeros representables es mayor a medida que nos movemos a la derecha de la recta  númerica, debido a lo mostrado anteriormente sobre el error. Es entonces que inevitablemente debe haber un entero que no este representado.
Cual sería este numero?
Recordar que el exponente es el corrimiento (shift) del punto decimal.  Si tenemos una mantissa de n bits, implica que podemos representar hasta $2^{(n+1)}$  numeros enteros sin que perdamos presicion, ya que para un exponente igual a n, el corrimiento alcanza hasta todos los numeros enteros antes de la siguiente potencia (estariamos sumando $2^0+2^1+\cdots+2^n$ a el $2^n$ del exponente), además de la potencia en si misma por que nos las da el exponente, sin embargo faltaría un bit de la mantissa para representar el numero siguiente a este como se ve en la figura:

![[Pasted image 20220827185713.png]]

## Representacion de maquina

Para formato double, corresponde a :
![[Pasted image 20220824121921.png]]

#### Signo
- s: 0 positivo, 1 si es negativo

#### Exponente
Exponente: 11 bits -> $2^{11} = 2048$ numeros, es decir, $[0,1,2,\cdots, 2047 ]$
	Se necesitan representar numeros negativos para eso  introducimos un shift que corresponde, si tenemos k bits disponibles para el exponente es:$$2^{k-1}-1$$
Que para el caso del formato double equivale a $1023$
		
Esto permite trasladar los numeros enteros representables por el exponente de la siguiente forma: $$[1-shift, 2- shift, \cdots, 2^k-2]$$
		Dejando fuera el caso de 0 ($000\cdots000$) y $2^k-1$ ($111\cdots111$) ya que son casos especiales.
		Que para formato double es:![[Pasted image 20220827193453.png]] y es lo que muestra el siguiente esquema: ![[Pasted image 20220828001153.png]]

![[Pasted image 20220828005448.png]]
##### Caso especial 11111111111
En el caso de que todos los bits del exponente son 1, tenemos 3 situciones:
- Si el bit de signo es 0, y todos los bits de la mantissa son 0, esto equivale a $+\infty$, que se obtiene al dividir $1/0$.
- Si el bit de signo es 1, y todos los bits de la mantissa son 0, esto equivale a $-\infty$.
- Si existe un bit en la mantissa tal que es distinto de 0, se interpreta como un NaN, not a number. Se obtiene al dividir $0/0$.

![[Pasted image 20220828004046.png]]

##### Caso especial 00000000000
Caso cuando todos los bits del exponente son 0. Permite representar números aún más pequeños que los que se podia representar.
Por ejemplo, en caso del formato double, el exponente más pequeño era -1022. cuando el exponente era 00000000001.
Ahora, si todos los bits del exponente son 0, seguimos la siguiente representación.
![[Pasted image 20220828004538.png]]
- El bit de signo se mantiene igual.
- Los bits de la mantissa se mantienen igual.
- El elemento despues del signo, es 0 no 1.
- El exponente es fijo en -1022 (o el exponente más pequeño de la representación que estemos usando).

En el formato anterior el numero más pequeño que podiamos almacenar era:$$+1.000\cdots 000\cdot2^{-1022}$$
Por lo tanto el antecesor (restar $1.000\cdots000\cdot2^{-1022}$):$$+0.111\cdots1111 \cdot 2^{-1022}$$
El numero más pequeño representable, lo obtenemos restando sucesivamente como el caso anterior, llegando a que en la mantissa tengo solo 0´s excepto en el ultimo bit.
$$+0.000\cdots0001 \cdot 2^{-1022}$$ Lo que corresponde a $$2^{-52}\cdot2^{-1022}=2^{-1074}$$
## Perdida de la Importancia

![[Pasted image 20220824124409.png]]

