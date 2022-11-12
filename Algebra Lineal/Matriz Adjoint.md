# Matriz Adjoint


La matriz <font style="color:red">Transpuesta Conjugada</font>, o adjoint de una [[Matrices|matriz]] $A$, es la matriz $A^*$ tal que:
$$
A=
\begin{bmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22} \\
a_{31} & a_{32} 
\end{bmatrix}\rightarrow \overline{A^T} = A^* = \begin{bmatrix}
\overline{a_{11}} & \overline{a_{21}}  &\overline{a_{31}} \\
\overline{a_{12}} & \overline{a_{22}} &\overline{a_{32}} \\

\end{bmatrix}
$$

Es decir, donde el operador conjugado cambia el signo de la parte imaginaria del numero complejo, $z = a+ib\rightarrow \overline{z} = a-ib$.
Si se trabaja con matrices reales, entonces se tiene que $A^T=A^*$.
Una propiedad importante es que $(AB)^*=B^*A^*$, de la misma forma que la transpuesta.

## Matriz Hermitiana

Se dice que $A$ es una matriz hermitiana si $A^*=A$. Esta las siguientes propiedades:

- Los valores de la diagonal principal son reales
- Sus valores propios tambien son reales.
- Sus vectores propios son ortogonales