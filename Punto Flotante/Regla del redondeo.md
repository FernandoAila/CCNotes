# Regla del redondeo para precision double
- Si el 53 bit (despues del ultimo de la mantissa) es 0, truncamos despues del bit 52
- Si el 53 bit es 1:
	-  Si todos los bits conocidos a la derecha del 53 bit son 0, se agrega 1 al bit 52, si y solo si el bit 52 es 1. Este caso es cuando el numero se encuentra "a la mitad" del intervalo.
	- Si es otro caso, se agrega 1.

La siguiente figura muestra los casos anteriores, por ejemplo,  si el siguiente bit despues del 52 avo bit es 0, significa que estamos en la "primera mitad" del intervalo x1-x2.
Por otro lado, si el bit 53 es 1, y existe algun bit conocido que sea 1 en los bits posteriores, estamos en el segundo caso, es decir, en la "segunda mitad" del intervalo.
Si el bit 53 es 1, y todos los bits conocidos son 0, significa que nos encontramos justo al medio del intervalo, por lo que hay que decidir.

![[Captura de Pantalla 2022-08-27 a la(s) 15.44.09.png]]