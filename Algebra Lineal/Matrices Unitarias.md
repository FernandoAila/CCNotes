# Matrices unitarias

Sea $Q$ una [[Matrices|matriz]] cuadrada de m filas y m columnas. Entonces se dice que es unitaria si $Q^*=Q^{-1}$, tal que $QQ^*=Q^*Q=I$, donde $Q^*$ es la [[Matriz Adjoint]].

La respuesta a esta caracterisitica es debido a que:
$$Q=[q_1,q_2,\cdots,q_n]$$
donde $q_i$ son vectores unitarios, $||q_i||=1$ y son ortogonales entre sí, es decir su producto interno es 0:
$$<q_i,q_j>=q_i^*q_j=0$$
Por lo que se dice que las columnas de $Q$ son ortonormales entre si.

Luego:
![[Pasted image 20221031204540.png]]

El siguiente teorema resulta de gran importancia:
>[!Note] Teorema
>Para cualquier matriz $A \in \mathbb{C}^{m\times n}$  y $Q \in \mathbb{C}^{m\times m}$, se tiene:
>$$||QA||_2=||A||_2, ||QA||_F=||A||_F$$

Donde $||||_F$ indica la norma de Frobenius.

Además:

>[!Note] Teorema
>Para cualquier matriz unitaria  $Q \in \mathbb{C}^{m\times m}$, se tiene:
>$$| \lambda|= 1$$
>Donde $\lambda$ es un valor propio de $Q$

Demostracion:
Recordar la ecuacion de los valores propios: 
$$
A\vec{v}= \lambda\vec{v} \quad (1)
$$
Aplicando la transpuesta conjugada a ambos lados:
$$
\vec{v}^*A^*=\lambda^* \vec{v}^* \quad(2)
$$
Multiplicando (1) por (2) :
$$\begin{align}
\vec{v}^*A^* A\vec{v}&=\lambda^* \vec{v}^*  \lambda\vec{v}\\
\vec{v}I\vec{v}&=\lambda^*\lambda(\vec{v}^*\vec{v})\\
\vec{v}\vec{v}&=\lambda^*\lambda(\vec{v}^*\vec{v}) \quad ||||_2\\
||\vec{v}||_2^2&=|\lambda|^2||\vec{v}||_2^2\\
\frac{||\vec{v}||_2^2}{||\vec{v}||_2^2}&=|\lambda|^2\\
1&=|\lambda|
\end{align} $$
