Supongamos que queremos encontrar la raiz a la siguiente ecuación vectorial:

$$
F(\vec{x})=\vec{0}
$$
Donde $\vec{x}=[x_1,x_2,x_3,\cdots,x_n]$ es decir son las variables con las que se evalua $F$, por ejemplo:

$$
F=\begin{pmatrix}3x_1^2+x_2^2+x_3 \\ x_1+x_2 \\ x_1+x_3\end{pmatrix}
$$
Del [[Metodo de Newton en Rn]] podemos realizar lo siguiente:
$$\begin{align}
\vec{x_0}&=\text{initial guess}\\
J(\vec{x_i})\vec{w} & =-F(\vec{x_{i}})\quad \text{resolver w}\\
\vec{x_{i+1}}&=\vec{x_{i}}+w
\end{align}$$
Donde $J(\vec{x_i})$ corresponde a la matriz jacobiana de $F(\vec{x})$ evaluada en $\vec{x_i}$.
![[Pasted image 20221201021146.png]]

Lo cual son muchas derivadas!.
Para evitar todos estos calculos considerar la linearizacion (lo que signifca a obtener la expansion de Taylor) de la funcion $F(\vec{x_0}+\epsilon\vec{v})$
para $\epsilon=0$ y $x_0$ y $v$ dados:
![[Pasted image 20221201021745.png]]

donde la aproximacion mejora a medida de $\epsilon \rightarrow 0$.
Definimos la siguiente funcion $afun$:

$$afun(v)=\frac{F(X_0+\epsilon v)-F(x_0)}{\epsilon}$$
Luego podemos llamar a [[GMRes]] para encontrar una solucion numerica:

$$\begin{align*}
x_0&=\text{initial guess}\\
w&= GMRES(afun,b=-F(x),threshold=10^{-10}) \quad \text{resolver w}\\
x_{i+1}&= x_i+w
\end{align*}$$

