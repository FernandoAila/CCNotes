## Metodos Conocidos de resolucion



### Metodo de substitucion
Para este metodo simplemente despejamos una variable, reemplazamos, por ejemplo utilizando el siguiente [[Sistemas de Ecuaciones Lineales#^sistema2x2|sistema]]:
![[Pasted image 20220921193104.png]]
Reemplazando en la segunda ecuacion:
![[Pasted image 20220921193052.png]]
Despejando $y$:
![[Pasted image 20220921193149.png]]

Luego despejando $x$ a partir de la primera ecuacion:
![[Pasted image 20220921193235.png]]

Notemos que si bien es relativamente sencillo de mostrar, es complicado implementarlo para matrices de mayores dimensiones, ya que necesitariamos una formula explicita para cada uno de las variables, lo que se vuelve pesado.

### Regla de cramer

El sistema $2 \times 2$, puede tambien ser calculado con la regla de cramer a partir del despeje hecho en el [[#Metodo de substitucion]], notemos que en el denominador de las 2 variables despejadas se encuentra el determinante de la matrix $A$, mientras que el nominador se encuentra el determinante de matriz construida reemplazando el vector columna donde se encuentran los coeficientes que acompañan a esa variable por el vector $\vec{c}$. Esto corresponde a: $$\begin{align} 
x=\frac
{\begin{vmatrix} c_1 & b_1 \\  
c_2 & b_2 \end{vmatrix}}

{\begin{vmatrix} a_1 & b_1 \\  
a_2 & b_2 \end{vmatrix}}\\\\

y=\frac
{\begin{vmatrix} a_1 & c_1 \\  
b_2 & c_2 \end{vmatrix}}

{\begin{vmatrix} a_1 & b_1 \\  
a_2 & b_2 \end{vmatrix}}

\end{align}$$

Sin embargo, aunque se vea simple a primera vista, calcular el determinante de una matrix resulta muy costoso computacionalmente hablando, ya que en el peor caso calcular el determinante de una matriz $n\times n$ toma $O(n!)$, es decir queremos evitar en el calculo de este directo.
