Como podemos construir una nueva base del sub-espacio de Krylov, de forma de que los vectores basales esten bien condicionados y linealmente independientes?
La respuesta es **Ortonormalizar** la base. Es decir, hacer un nuevo span con vectores $q_i$ ortonormales tal que:

$$
\begin{align}
\mathcal{K}_k&=span(b,Ab,A^2b,\cdots A^{k-1}b)\\
&=span(q_1,q_2,q_3,\cdots q_k)
\end{align}
$$

Naturalmente podemos aplicar la [[Ortonormalizacion de Gram-Schmidt]] para ortonormalizar esta. Donde queremos ortonormalizar la matriz: 
$$
\begin{bmatrix}
b & Ab &A^2b &\cdots &A^{k-1}b


\end{bmatrix}
$$

De acuerdo a esto podemos concluir que:
$$
\begin{align}
span(b)&=span(q_1)\\
span(b,bA)&=span(q_1,q_2)\\
&\vdots\\
span(b,Ab,A^2b,\cdots,A^{k-1}b)&=span(q_1,q_2,q_3,\cdots,q_k)\\
\end{align}$$



El span de b es una linea recta, de la forma $c_1b$, esto quiere decir que $q_1$ debe tener la misma "direccion" que $b$ pero normalizado. 
$$
\frac{b}{||b||}=q_1
$$
Realizando los pasos de la [[Ortonormalizacion de Gram-Schmidt]], podemos representar $Ab$ como la combinacion lineal de $q_1$ y $q_2$
$$
Ab=\hat{h}_{11}q_1+\hat{h}_{21}q_2
$$
De la misma forma con $A^2b$
$$
A^{2}b=\hat{h}_{12}q_1+\hat{h}_{22}q_2 + \hat{h}_{23}q_3 
$$
Generalizando para $A^{k-1}b$:
$$
A^{k-1}b = h_{1k-1}q_1+h_{2k-1}q_2+ \cdots + h_{kk-1}q_k
$$

Podemos considerar la siguiente relación que es mas conveniente:
$$
\begin{align}
\mathcal{K}_k&=span(b,Ab,A^2b,\cdots A^{k-1}b)\\
&=span(q_1,Ab,AAq_1,\cdots A^{k-1}b)\\
&=span(q_1,Aq_1,Aq_2,Aq_3,\cdots Aq_{k-1})\\
&=span(q_1,q_2,q_3,\cdots q_k)
\end{align}
$$
Lo que significa que podemos sacar el "techo" al $h$, luego:
$$
\begin{align}
Aq_1&=h_{11}q_1+h_{21}q_2\\
Aq_2&=h_{12}q_1+h_{22}q_2+ h_{32}q_3\\
\vdots\\
Aq_{k-1}&=h_{1k-1}q_1+h_{2k-1}q_2+ h_{2k-1}q_3+\cdots+ h_{kk-1}q_k\\
Aq_k&=h_{1k}q_1+h_{2k}q_2+ h_{2k}q_3+\cdots+ h_{kk}q_k+ h_{k+1k}q_{k+1}=\sum^{k+1}_{j=1}h_{jk}q_j\\
\end{align}
$$

Donde los vectores $q_j$ y los valores $h_{jk}$ son obtenidos usando [[Ortonormalizacion de Gram-Schmidt]] modificada, o llamada comunmente, la iteracion de arnoldi.
Por ejemplo para las 2 primeras ecuaciones, sabiendo que $q_1=\frac{b}{||b||}$:
$$
\begin{align}
h_{11}&=q_1^T A q_1\\
h_{21}&=||Aq_1-h_{11}q_1||\\
q2&=\frac{Aq_1-h_{11}q_1}{h_{21}}\\
h_{12}&=q_1^T A q_2\\
h_{22}&=q_2^TAq_2-q_2^Th_{12}q_1=q_2^T(Aq_2-h_{12}q_1)\\
h_{32}&=||Aq_2-h_{12}q_1-h_{22}q_2||\\
q3&=\frac{Aq_2-h_{12}q_1-h_{22}q_2}{h_{32}}\\

\end{align}
$$





Lo que puede ser escrito en forma matricial como
$$
A\begin{bmatrix}
q_1,q_2,\cdots,q_k
\end{bmatrix}=\begin{bmatrix}
h_{11}q_1+h_{21}q_2,h_{12}q_1+h_{22}q_2+ h_{23}q_3,\cdots,\sum^{k+1}_{j=1}h_{jk}q_j
\end{bmatrix}
$$
El lado derecho puede verse como el producto de 2 matrices $Q$ y $H$ de la forma
$$
A\underbrace{\begin{bmatrix}
q_1,q_2,\cdots,q_k
\end{bmatrix}}_{Q_k} =\underbrace{\begin{bmatrix}
q_1 & q_2 & \cdots & q_{k+1}
\end{bmatrix}}_{Q_{k+1}}
\begin{bmatrix}
h_{11} & h_{12}  & \cdots &h_{1k-1} &  h_{1k}\\
h_{21} & h_{22}  & \cdots & h_{2k-1}&  h_{2k}\\
0 &h_{32} &\cdots  & h_{3k-1} & h_{3k}\\
\vdots &  \vdots & \vdots & \vdots & \vdots \\
0 & 0 & \cdots & h_{kk-1} & h_{kk}\\
0 & 0& \cdots & 0 & h_{k+1k}
\end{bmatrix}
$$

La cual corresponde a la reducicion parcial de $A$ a una forma de **Hessenberg**:
$$AQ_k=Q_{k+1}\hat{H}_k$$
Donde $Q_k$ es la matriz con $k$ columnas ortonormales, $Q_{k+1}$ es la matriz con $k+1$ columnas ortonormales y $\hat{H}$ es una matriz upper Hessenberg que son parecidas a las matrices triangulares superiores pero tiene coeficientes en la primera subdiagonal.

Es decir, construimos una nueva base del espacio de Krylov $\mathcal{K}_k$!.
