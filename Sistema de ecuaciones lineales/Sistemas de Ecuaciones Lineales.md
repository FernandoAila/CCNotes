# Sistemas de ecuaciones Lineales

En la seccion de [[Iteracion de punto fijo]] se interpretaba a una IPF como la interseccion entre una recta (en aquel caso $y=x$) y una funcion no lineal llamada $g(x)$. Ahora se estudia solamente la interseccion de 2 o más rectas. Tal como muestra la figura:
![[Pasted image 20220921002944.png]]
 Donde queremos buscar el punto donde se intersectan las 2 rectas $(x,y)$ o, como se denota usualmente $(x_s,y_s)$. 
 Este sistema lo podemos escribir como: 
 $$\begin{align}
 a_1x+b_1y=c_1\\
 a_2x+b_2y=c_2
 \end{align}$$
 Y en su forma vectorial:
$$\begin{bmatrix}  
a_1 & b_1 \\  
a_2 & b_2  
\end{bmatrix}
\begin{bmatrix}  
x \\  
y  
\end{bmatrix}
=
\begin{bmatrix}  
 c_1 \\  
c_2  
\end{bmatrix}$$

^sistema2x2


O sea $A\vec{x}=\vec{c}$. En particular una solucion sencilla,  (**pero no eficiente**), es hacer el siguiente despeje: $\vec{x}=A^{-1}\vec{c}$.
Una forma de encontrar la solucion a estos sistemas es usar ya los famosos [[Metodos Conocidos de resolucion]] como el metodo de substitucion o la regla de Cramer, sin embargo estos suelen ser dificiles de implementar o requieren calcular el determinante de la matriz, un calculo que suele ser costoso.
Existen situaciones, donde la matriz $A$ tiene un patron regular que permite resolver el sistema de ecuaciones lineales eficientemente. Por ejemplo, considerar que la matriz $A$ sea una matriz diagonal, donde la respuesta es $x_i = b_i/d_i$, donde $x_i$ es la incognita $i$, $b_i$ el coeficiente que la acompaña y $d_i$ lo que esta "despues" de la igualdad.  

Otro caso es cuando la matriz es triangular superior (o inferior), donde nos entrega una formula explicita para una incognita, y es cosa de ir reemplazando utilizando *backward substitution*, hasta despejar todas las incognitas.  Por lo tanto es bastante conveniente tener esta forma, que va a ser la base de la tecnica de [[Eliminacion Gaussiana]].