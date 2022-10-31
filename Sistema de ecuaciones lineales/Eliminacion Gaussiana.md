# Eliminacion Gaussiana

La idea es que a traves de operaciones fila, logra convertir cualquier matriz (no todas!),  a una matriz triangular superior.

Sea el siguiente [[Sistemas de Ecuaciones Lineales#^sistema2x2|sistema]] sistema de ecuaciones:
$$\begin{align}
 a_1x+b_1y=c_1\\
 a_2x+b_2y=c_2
 \end{align}$$
El cual se puede re-escribir en el siguiente tableau o matriz ampliada, donde se acoplan los coeficientes de la matriz $A$ y los del lador derecho del sistema de ecuaciones:
![[Pasted image 20220922012302.png]]

Queremos que el coeficiente $a_2$ sea 0, por lo que restamos la primera fila ponderada por $\frac{a_2}{a_1}$, es decir:
$$\begin{bmatrix}  
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
## Algoritmo
Lo que induce el siguiente algoritmo:

1. Construir tableau a partir del sistema de ecuaciones $Ax=b$
2. Aplicar operaciones fila hasta que la matriz asociada (la parte del tableau donde esta la matriz A original) sea triangular superior y un lado derecho modificado acorde: $Ux=\hat{c}$.
3. Resolver $Ux=\hat{c}$ con [[Backward substitution]].

En general el tableau queda de la siguiente forma:
![[Pasted image 20220922022251.png]]

Lo cual tiene el siguiente algoritmo para convertir el tableau en triangular superior, donde B es la matriz que almacena el tableau:
![[Pasted image 20220922022340.png]]

Basicamente:
	1. Por cada columna j
		1.  Por cada fila i =  j + 1 hasta n:
			1.  Calcular $mult= \frac{B_{ij}}{B_{jj}}$
			2.  Aplicar $R_i= R_i - mult\cdot R_j$

Por ejemplo, hacemos 0 primero todos los elementos de la columna 1 "abajo" del coeficiente $a_{11}$. Luego hacemos 0 todos los coeficientes debajo del  coeficiente $a_{22}$, asi sucesivamente hasta tener una matriz triangular superior.
Este mismo algoritmo en python corresponde a:
```python
def to_triangular(B,n):
	#iterate columns from the original matrix
    for j in range(n-1):
	    # iterate rows from the original matrix
        for i in range(j+1, n):
            mult = B[i,j]/B[j,j]
            #iterate all the row
            for k in range(j,n+1):
                 B[i,k]= B[i,k]- mult*B[j,k]
    return B
```

Donde iteramos hasta $n-1$ debido a que en python los indices empiezan en 0, y la notacion $[i,j+1:]$  significa tomar la fila i, y desde el indice $j+1$ hasta el fin del arreglo.

Ahora surge la pregunta de, cuantas operaciones elementales requerimos en GE?

## Cantidad de operaciones elementales

Recordar los resultados de las siguientes sumatorias:$$\begin{align}
\sum_{i=1}^n1&=n\\
\sum_{i=1}^ni&=\frac{n(n+1)}{2}\\
\sum_{i=1}^ni^2&=\frac{n(n+1)(2n+1)}{6}
\end{align}$$


Sin contar los ```for``` anidados tenemos que:
- Division (linea 3) ocurre una vez
- La resta y la multiplicacion ocurren $2(n+1-(j)$ veces. Ya que es todos los coeficientes de la fila $i$ menos aquellos que ya son 0 de iteraciones anteriores.




Con esta informacion se obtiene lo siguiente:

![[Pasted image 20220923000410.png]]
Notar que las dos sumatorias iniciales representan un loop. (1° linea)
Ademas ver el cambio de variable en la segunda sumatoria de la forma $i = j+1 \rightarrow k=i-j$. (2° linea).
La tercera linea elimina la sumatoria debido a que no existe el termino $k$ en la sumatoria.
Y el resto es simple aritmetica de sumatoria, usando las propiedades mencionadas arriba.

De esto concluimos que la ejecucion del algoritmo de eliminacion gaussiana de una matriz $n\times n$ toma del orden de $\frac{2}{3}n^3$ operaciones elementales.

Si juntamos esto con el tiempo que toma [[Backward substitution]], tenemos que resolver un sistema de ecuaciones de esta forma tiene una complejidad temporal de  $\frac{2}{3}n^3+n^2$ operaciones elementales, siendo el termino con $n^3$ el dominante, aunque no olvidar el termino $n^2$. Esto se ejemplifica con una secuencia de sistemas de ecuaciones lineales:
$$\begin{align}
A\vec{x_1}&=\vec{b_1}\\
A\vec{x_1}&=\vec{b_1}\\
&\vdots\\
A\vec{x_m}&=\vec{b_m}\\
\end{align}$$

Notar que la matriz $A$ no cambia, solo el lado derecho, por lo siguiendo esta idea, la cantidad de operaciones elementales totales seria de $m(\frac{2}{3}n^3+n^2)$ lo que son muchas operaciones elementales!.
Este problema induce a pensar un nuevo algoritmo que no necesite ejecutar eliminacion gaussiana nuevamente cuando solo cambia el lado derecho (ver tableau). A este se le llama la [[Factorizacion LU]] de $A$.