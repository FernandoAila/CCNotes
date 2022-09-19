# Representacion de maquina
#### Almacenamiento de numeros en memoria
![[Pasted image 20220824083347.png]]

Para formato double, corresponde a :
![[Pasted image 20220824121921.png]]

#### Signo
- s: 0 positivo, 1 si es negativo

#### Exponente
Exponente: 11 bits -> $2^{11} = 2048$ numeros, es decir, $[0,1,2,\cdots, 2047 ]$
	Se necesitan representar numeros negativos para eso  introducimos un shift que corresponde, si tenemos k bits disponibles para el exponente es:$$2^{k-1}-1$$
Que para el caso del formato double equivale a $1023$
		
Esto permite trasladar los numeros enteros representables por el exponente de la siguiente forma: $$[1-shift, 2- shift, \cdots, 2^k-2-shift]$$
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