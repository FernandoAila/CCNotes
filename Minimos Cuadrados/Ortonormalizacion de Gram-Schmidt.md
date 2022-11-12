Considerar la matriz $A \in \mathbb{R}^{m \times n}$ con $m$ ecuaciones y $n$ variables y $m>n$.
Podemos describir la matriz $A$ como: 
$$A=[a_1,a_2,\cdots, a_n]$$
Donde $a_i$ es el vector columna de $A$.

Reescribimos $A=\hat{Q}\hat{R}$ como:
$$[a_1, a_2,\cdots,a_n]=

\underbracket{[q_1,q_2,\cdots,q_n]}_\hat{Q}
\underbracket{\begin{bmatrix}
r_{11} & r_{12} & r_{13}& \cdots & r_{1n}\\
0 & r_{22} &r_{23} & \cdots & r_{2n}\\
0& 0 & r_{33} &\cdots & r_{3n}\\
\vdots & \vdots & \vdots & \cdots & \vdots\\
0 & 0 & 0&\cdots & r_{nn} 

\end{bmatrix}}_\hat{R}$$

Como $Q$ es ortonormal significa que sus columnas son ortogonales entre si y la norma 2 de cada una es 1.
Es decir:
$$
||q_i||_2^2=1
$$
Y
$$
q_i^Tq_j=<q_i,q_j>=0 \quad \text{para } i\neq j
$$

Multiplicando $\hat{Q}$ por $\hat{R}$ de la forma $\hat{Q}r_i$:
$$[a_1, a_2,\cdots,a_k,\cdots,a_n]=

[r_{11}\vec{q_1},r_{12}\vec{q_1}+r_{22}\vec{q_2},r_{13}\vec{q_1}+r_{23}\vec{q_2}+r_{33}\vec{q_3},\cdots,\sum_{i=1}^kq_ir_{ik},\cdots,\sum_{i=1}^n q_ir_{in}]
$$

Lo que forma el sistema: 
$$
\begin{align}
a_1&=r_{11}\vec{q_1} \quad (1)\\
a_2&=r_{12}\vec{q_1}+r_{22}\vec{q_2} \quad (2)\\
a_3&=r_{13}\vec{q_1}+r_{23}\vec{q_2}+r_{33}\vec{q_3} \quad (3)\\
&\vdots\\
a_k&=\sum_{i=1}^kq_ir_{ik} \quad (k)\\
a_n&=\sum_{i=1}^n q_ir_{in} \quad(n)
\end{align}
$$

Para la ecuacion 1 conocemos $a_1$ pero no $r_{11}$ ni $\vec{q_1}$, por lo que tenemos más incognitas que ecuaciones, por lo que usaremos el hecho de que las columnas de $Q$ son ortonormales, por lo que tenemos 2 alternativas:
- Multiplicar por la izquierda por $q_1$ aprovechando el hecho de que $q_i^Tq_i=<q_i,q_i>=1$, luego: 
   $$\begin{align}
   a_1&=r_{11}\vec{q_1}\\
   q_1^Ta_1&=r_{11}q_1^Tq_1\\
   q_1^T a_1 &= r_{11} 1\\
   q_1^T a_1 &= r_{11} 
   \end{align}$$
   Notemos que todavia no sabemos como es $q_1^T$ por lo que esta alternativa no dice mucho.


- Obtener la norma 2 a ambos lados:
      $$\begin{align}
   a_1&=r_{11}\vec{q_1}\\
  ||a_1||_2&=||r_{11}q_1||_2\\
    ||a_1||_2 &= |r_{11}| ||q_1||_2\\
   ||a_1||_2 &= |r_{11}| 1\\ 
   ||a_1||_2 &= |r_{11}|
   \end{align}$$
   Notar que $r_{11}=||a_1||_2$ o $r_{11}=-||a_1||_2$ , por lo hay que tomar una decision que en este caso es la forma positiva es decir, $r_{11}=||a_1||_2$ .


Con la segunda alternativa ya conocemos 2 terminos, por lo que por simple despeje se tiene que: 
$$
\begin{align}
    a_1&=r_{11}\vec{q_1}\\
   \frac{a_1}{||a_i||_2}&=\vec{q_1}\

   \end{align}$$

Para la segunda ecuacion  podemos repetir la misma idea donde ya $\vec{q_1}$ es conocido:
  $$\begin{align}
   a_2&=r_{12}\vec{q_1}+r_{22}\vec{q_2}\\
  ||a_1||_2&=\sqrt{r_{12}\vec{q_1}+r_{22}\vec{q_2}}\\
  ||a_1||_2&=\sqrt{ (r_{12}\vec{q_1}r_{22}\vec{q_2})^T (r_{12}\vec{q_1}r_{22}\vec{q_2})}\\
  ||a_1||_2&=\sqrt{r_{12}^2+r_{22}^2}\\
   \end{align}$$
Notemos que tenemos más incognitas que ecuaciones nuevamente, por lo que resta usar la segunda alternativa de aprovechar la ortonormalidad de los vectores $q_i$, para lo cual tenemos 2 opciones:
- Multiplicar por la izquierda con $q_1$.
- Multiplicar por la izquierda con $q_2$.

Notemos que con $q_2$ ocurre el mismo caso mostrado anteriormente, donde todavia esta el termino  $q_2^T$, por lo que resta ver el caso de $q_1$ ya conocido, luego:
   $$\begin{align}
 a_2&=r_{12}\vec{q_1}+r_{22}\vec{q_2}\\
   q_1^Ta_2&=q_1^T(r_{12}\vec{q_1}+r_{22}\vec{q_2})\\
  q_1^Ta_2&= q_1^T r_{12}\vec{q_1} + q_1^T r_{22}\vec{q_2}\\
   q_1^Ta_2&= r_{12} q_1^T \vec{q_1} + r_{22} q_1^T \vec{q_2}
   \end{align}$$

Por ortonormalidad, sabemos que $q_1^T q_1=1$ y $q_1^Tq_2=0$, reemplazando:

   $$\begin{align}
q_1^Ta_2&= r_{12} q_1^T \vec{q_1} + r_{22} q_1^T \vec{q_2}\\
q_1^Ta_2&= r_{12} 1 + r_{22} 0\\
q_1^Ta_2&= r_{12}\\
   \end{align}$$
Una vez calculado, tenemos que el termino $r_{12}\vec{q_1}$ ya es completamente conocido por lo que:
$$
 a_2-r_{12}\vec{q_1}=r_{22}\vec{q_2}
$$
El lado izquierdo de la ecuacion es conocido!, por lo podemos aplicar de la misma forma que antes el metodo de aplicar norma 2 a ambos lados:
$$\begin{align}
   a_2-r_{12}\vec{q_1}&=r_{22}\vec{q_2}\\
  ||a_2-r_{12}\vec{q_1}||_2&=||r_{22}\vec{q_2}||_2\\
  || a_2-r_{12}\vec{q_1}||_2 &= |r_{22}| ||\vec{q_2}||_2\\
   || a_2-r_{12}\vec{q_1}||_2 &= |r_{22}| 1\\ 
   || a_2-r_{12}\vec{q_1}||_2 &= |r_{22}|
   \end{align}$$
  Considerando que $r_{22}>0$, por simple despeje se tiene que $q_2$:
  $$\frac{a_2-r_{12}\vec{q_1}}{r_{22}}=\vec{q_2}$$
Este algoritmo se repite multiple veces, ya con la tercera ecuacion:
![[Pasted image 20221101004224.png]]


Para el $k$-esimo paso:
![[Pasted image 20221101005527.png]]


Lo que genera el siguiente algoritmo

![[Pasted image 20221101005632.png]]

# Ortonormalizacion de Gram-Schmidt Modificada

En todos los calculos asumimos que se trabaja con aritmetica exacta, es decir, no existen errores en la computacion por punto flotante, perdida de la importancia, etc.

Consideremos la tercera ecuación del algoritmo,  donde ya caculamos $q_1$:
$$
\begin{align}
a_3 =r_{13} q_1 + r_{23}q_2+r_{33}q_3\\
q_2^T  a_3 =r_{13}q_2^T q_1 + r_{23} q_2^Tq_2+r_{33} q_2^Tq_3\\
\end{align}
$$

La teoría nos dice que $q_2^Tq_1=0$ , $q_2^Tq_2=1$ y $q_2^Tq_3=0$.

En terminos numericos, $q_2^Tq_3$ si lo podemos considerar como $0$ ya que es desconocido.  De la misma forma $q_2^Tq_2$ es 1. Sin embargo el termino $q_2^Tq_1$ en precision doble **NO** necesariamente es 0. Esto significa que el coeficiente $r_{23}$ puede ser distinto!.
Una forma de tomar en cuenta esta situacion es considerar el termino $r_{13}q_2^Tq_1$
en la computación, es decir:

$$\begin{align}
q_2^T  a_3- r_{13}q_2^T q_1 &= r_{23} q_2^Tq_2\\
q_2^T(a_3-r_{13}q_2^Tq_1)&=r_{23}
\end{align}$$

Es decir

![[Pasted image 20221108233052.png]]

![[Pasted image 20221112044429.png]]