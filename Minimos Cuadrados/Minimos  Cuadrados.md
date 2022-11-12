 
Cuando resolviamos un [[Sistemas de Ecuaciones Lineales|sistema de ecuaciones]] siempre trabajamos con el supuesto de que teniamos la misma cantidad de ecuaciones y de incognitas. Es decir un matriz A cuadrada.
Sin embargo, es posible trabajar con matrices no cuadradas, donde tenemos más ecuaciones que incognitas por ejemplo:
$$
\begin{align}
\begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22} \\
a_{31} & a_{32}
\end{bmatrix}
\begin{bmatrix}
x\\
y
\end{bmatrix}
&=
\begin{bmatrix}
b_1\\
b_2\\
b_3\
\end{bmatrix}
\quad{(1)}
\\

\begin{bmatrix}
2 \\
2  \\
2 
\end{bmatrix}
\begin{bmatrix}
x
\end{bmatrix}
&=
\begin{bmatrix}
1\\
0\\
0
\end{bmatrix}
\quad{(2)}



\end{align}
$$
La figura siguiente muestra un uso de minimos cuadrados:
![[Pasted image 20221029222834.png]]
En [[Interpolacion en 1D]], utilizamos polinomios para interpolar datos o aproximar funciones. En ese caso, el polinomio interpolador tiene que pasar por lo puntos dados. En este caso, en minimos cuadrados, puede pasar que los datos que se reciben ($x_i,y_i$) pueden venir con errores (especificamente los  $y_i$). Por lo que no tendría sentido, construir un interpolador que pase justamente por esos datos.
Formalmente se puede decir que los datos vienen con un error aditivo en $y_i$ de la siguiente forma:
$$y_i=\hat{y}+\epsilon_i \quad i\in 1,2,3,\cdots,m$$
Donde $y_i$ es el dato que tenemos acceso, $\hat{y}$ el dato que queremos recuperar y no tenemos acceso y $e_i$ el error de la obtencion del dato el cual tampoco tenemos acceso.

Por lo tanto el objetivo, es construir una aproximacion a estos datos tal que minimize un error (el error cuadratico), lo que implica reducir, el tamaño de las lineas azules en la gráfica que van desde el dato real hasta la curva que aproxima.
Para esto tenemos 2 alternativas equivalentes entre si:
- [[Minimos Cuadrados por Minimizacion|Minimos cuadrados por minimizacion]].
- [[Ecuaciones Normales]]
O usar la [[Factorizacion QR]]

Podemos aplicar minimos cuadrados en distintos [[Tipos de modelos]], como lineal, cuadratico, exponencial, etc.