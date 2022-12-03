Los problemas de valor frontera o BVP se caracterizan por que no dependen del tiempo $t$ sino que de una variable espacial $x$. Por ejemplo, $y^"(x)=0$ para $x\in ]0,1[$ , $y(0)=c_1$ y $y(1)=c_2$. 
La pregunta es la misma, cual es la funcion en una variable tal que su segunda derivada es igual a 0 en $]0,1[$ y al evaluarla en $x=0$ y en $x=1$ da uno respectivamente.


Por lo que tenemos 3 compoenntes:

- Una ODE: Ej: $y^"(x)=0$
- Condiciones de borde: $y(0)=c_1$ y $y(1)=c_2$
- Y un intervalo donde queremos obtener la solucion $x\in[0,1]$

En este caso, se verifica que la solucion es $y(x)=c_1+(c_2-c_1)x$

De manera general un BVP se define como:
$$
\begin{align*}
y^{"}(x)&=f(x,y,y^{'})\\
y(x_0)&=c_1\\
y(x_1)&=c_2
\end{align*}
$$
En el intervalo $]x_0,x_1[$


Para resolver BVP tenemos dos alternativas:
- [[Metodo del disparo]]
- [[Metodo de diferencias finitas]]