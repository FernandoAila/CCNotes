# Machine Epsilon

El numero machine epsilon $\epsilon_{mach}$  se define la distancia entre 1 y el menor numero representable, como, $2^{-52}$ en el formato double. 

Que es lo que ocurre cuando queremos representar un numero $x$ entre 1 y $\epsilon_{mach}$? ![[Pasted image 20220824103823.png]]

Tenemos 2 opciones:
- Cambiar el formato
- Mantenerlo y aproximar el numero.

Para este ultimo caso, por ejemplo, podriamos aproximar al siguiente numero si existe un 1 a la derecha del ultimo bit de la mantissa o truncar si es un cero, pero también hay que considerar el caso en que exista un empate.
![[Pasted image 20220824104514.png]]Para esto podemos utilizar la llamada [[Regla del redondeo]].

## Importancia de $\epsilon_{mach}$

Se define el error absoluto, $e_{abs}$ ,con $x$ como el numero original y $x_c$  como la cantidad calculada como: $$e_{abs}=|x_c-x|$$
De la misma forma el error relativo, $e_{rel}$, se define como: $$e_{rel} = \frac{|x_c-x|}{|x|}$$
De estas definiciones se infiere a partir de lo anterior lo siguiente:$$e_{rel} \leq \frac{1}{2} e_{mach}$$
y$$e_{abs} \leq \frac{1}{2} e_{mach} |x|$$
La primera ecuación es facil de deducir, ya que nunca el error será mayor que la mitad del intervalo, a partir de lo visto anteriormente. Además de la segunda ecuacion se muestra que el error absoluta es proporcional al tamaño del numero real en cuestion, es decir si el numero real es más grande, el error va a ser mayor, debido a la cantidad de numeros representables entre el intervalo que se encuentra $x$ que depende de la mantissa.

Por ejemplo, si utlilizamos una representación de punto flotante, con 2 bits para la mantissa, se tiene que:
![[Pasted image 20220827165246.png]]

- Se puede apreciar que la cantidad de numeros representables entre potencias de 2 es la misma, lo que tiene sentido debido a que la mantissa no cambia (solo lo hace el exponente).
- El espaciado (gap) entre numeros representables es mayor a medida que nos movemos a la derecha de la recta  númerica, debido a lo mostrado anteriormente sobre el error. Es entonces que inevitablemente debe haber un entero que no este representado. En efecto, para grandes numeros, el gap será mayor que uno, por lo que estariamos dejando un numero entero sin representar.
Cual sería este numero?
Recordar que el exponente es el corrimiento (shift) del punto decimal.  Si tenemos una mantissa de n bits, implica que podemos representar hasta $2^{(n+1)}$  numeros enteros sin que perdamos presicion, ya que para un exponente igual a n, el corrimiento alcanza hasta todos los numeros enteros antes de la siguiente potencia (estariamos sumando $2^0+2^1+\cdots+2^n$ a el $2^n$ del exponente), además de la potencia en si misma por que nos las da el exponente, sin embargo faltaría un bit de la mantissa para representar el numero siguiente a este como se ve en la figura:

![[Pasted image 20220827185713.png]]
