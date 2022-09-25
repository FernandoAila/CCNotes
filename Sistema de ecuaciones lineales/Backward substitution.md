## Backward substitution

Cuando se tiene ya una matriz diagonal superior $U$, y el lado derecho modificado $\hat{b}$, es decir $Ux=\hat{b}$ podemos aplicar el algoritmo de backward substitution, es decir:
![[Pasted image 20220923012131.png]]

De la ultima ecuacion extraemos que:
$$
u_{nn}x_{n}=b_n \rightarrow x_n = \frac{b_n}{u_{nn}}
$$

Ya que conocemos el valor de $x_n$ podemos despejar la penultima ecuacion:
$$\begin{align}
u_{n-1,n-1}x_{n-1}+u_{n-1,n}{x_n}&=b_{n-1}\\
x_{n-1}&=\frac{b_{n-1}-u_{n-1,n}{x_n}}{u_{n-1,n-1}}
\end{align}
$$

De hecho para no es necesario reemplazar la expresion explicita  para  el $x_n$ por que este ya está calculado.

Siguiendo el mismo procedimiento podemos escribir la i-esima ecuacion:
$$
\begin{align}
u_{ii}x_i + \sum_{j=i+1}^{n}u_{ij}x_j=b_i\\
x_i=\frac{b_i-\sum_{j=i+1}^{n}u_{ij}x_j}{u_{ii}}
\end{align}
$$
Esto se repite hasta que el i sea igual a 1.

Lo que induce el siguiente algoritmo:
![[Pasted image 20220923020029.png]]

El indice $i$ reprensenta la i-esima ecuacion, mientras que $j$ representa el indice la sumatoria.

A partir de esto podemos contar la cantidad de operaciones elementales: $$\begin{align}
\#&=\sum_{i=1}^n(\sum_{j=i+1}^n2+1)\\
&=\sum_{i=1}^n(\sum_{k=1}^{n-i}2+1)\\
&=\sum_{i=1}^n 2(n-i)+1\\
&=\sum_{i=1}^n 2n-2i+1\\
&=2n\sum_{i=1}^n 1-2\sum_{i=1}^ni+\sum_{i=1}^n1\\
&=2n^2 -2\frac{n(n+1)}{2}+n\\
&=2n^2 -n^2-n+n\\
&=n^2

\end{align}$$
Por lo que backward substitution toma $n^2$ operaciones elementales.