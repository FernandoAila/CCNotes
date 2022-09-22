# Eliminacion Gaussiana

La idea es que a traves de operaciones fila, logra convertir cualquier matriz (no todas!),  a una matriz triangular superior.

Sea el siguiente [[Sistemas de Ecuaciones Lineales#^sistema2x2|sistema]] sistema de ecuaciones:
$$\begin{align}
 a_1x+b_1y=c_1\\
 a_2x+b_2y=c_2
 \end{align}$$
El cual se puede re-escribir en el siguiente tableau o matriz ampliada, donde se acoplan los coeficientes de la matriz $A$ y los del lador derecho del sistema de ecuaciones:
![[Pasted image 20220922012302.png]]

Queremos que el coeficiente $a_2$ sea 0, por lo que restamos la primera fila ponderada por $\frac{a_2}{a_1}$, es decir:$$\begin{bmatrix}  
a_1 & b_1 & \vdots & c_1 \\  
a_2 -\frac{a_2}{a_1}a_1 & b_2 - \frac{a_2}{a_1}b_1& \vdots &  c_2- \frac{a_2}{a_1} c_1
\end{bmatrix}
$$

$$\begin{bmatrix}  
a_1 & b_1&\vdots & c_1 \\  
0 & b_2 - \frac{a_2}{a_1}b_1&\vdots & c_2- \frac{a_2}{a_1} c_1
\end{bmatrix}
$$

Donde la matriz A original ya es triangular superior por lo que:

![[Pasted image 20220922013355.png]]

Donde la segunda ecuacion solo tiene una sola incognita $y$, lo que es facilmente despejable:
![[Pasted image 20220922013455.png]]

Reemplazando en la primera ecuacion: 
![[Pasted image 20220921193235.png]]

Lo que induce el siguiente algoritmo:

1. Construir tableau a partir del sistema de ecuaciones $Ax=b$
2. Aplicar operaciones fila hasta que la matriz asociada (la parte del tableau donde esta la matriz A original) sea triangular superior y un lado derecho modificado acorde: $Ux=\hat{c}$.
3. Resolver $Ux=\hat{c}$ con *backward substitution*.