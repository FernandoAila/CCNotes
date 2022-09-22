# Metodo de la secante


El metodo de Newton requiere conocer de antemano la derivada de la funcion $f$, o en su defecto, puede que esta sea costosa de calcular. El metodo de la bisección serviria en este caso, pero nos da una convergencia lineal de solo $S=\frac{1}{2}$. La pregunta radica entonces, en encontrar un metodo que no requiera conocer (o calcular) la derivada de la funcion, y que converja más rapido que el metodo de la bisección. Para este caso surge el **metodo de la secante**, cuya idea principal radica en aproximar la derivada de la función.

Recordar entonces la definicion de derivada:$$ f'(x)=\lim_{\Delta x \rightarrow 0}\frac{f(x+\Delta x)-f(x)}{\Delta x}$$

![[Pasted image 20220919182556.png]]

Esta definicion, puede ser vista de otra forma, es decir, aproximamos desde la izquierda de $x$:$$ f'(x)=\lim_{\Delta x \rightarrow 0}\frac{f(x)-f(x-\Delta x)}{\Delta x}$$
La primera definicion se llama **forward difference** mientras que la segunda se llama **backward difference**.
Utilizando el [[Metodo de newton]]:$$\begin{align}x_{i+1}&=x_i-\frac{f(x_i)}{f'(x_i)}\\
&\approx x_i-\frac{f(x_i)}{\frac{f(x_i)-f(x_i-\Delta x)}{\Delta x}}
\end{align}$$
Con $x_i-\Delta x=x_{i-1}$ y $x_i=x_i$:$$\begin{align}x_{i+1}
&\approx x_i-\frac{f(x_i)}{\frac{f(x_i)-f(x_i-\Delta x)}{\Delta x}}\\
&\approx x_i-\frac{f(x_i)(x_i-x_{i-1})}{f(x_i)-f(x_{i-1})}
\end{align}$$
Lo cual es el metodo de la secante:$$x_{i+1}=x_i-\frac{f(x_i)(x_i-x_{i-1})}{f(x_i)-f(x_{i-1})}$$
Notar que necesitamos al menos $2$ *initial guesses*, $x_0$ y $x_1$, lo cual no es complicado teniendo ya 1 *initial guess*, por que sería solamente desplazar  $x_1= x_0 + \delta$, siendo $\delta$ un valor pequeño.

## Algoritmo
Por lo tanto el algorimo es:

![[Pasted image 20220919194511.png]]
```python
def secant(n,f, x_0_init, x_1_init):
	x_0 = x_0_init
	x_1 = x_1_init
	x_2 = x_1_init
	for i in range(n):
		c = f(x_1)
		x_2 = x_1 - c * (x_1-x_0) / (c - f(x_0))
		x_0, x_1 = x_1, x_2

	return x_2
```


## Convergencia
El metodo de la secante, bajo el supuesto de que converge a $r$ y que $f'(r) \neq 0$, se tiene que:$$\begin{align}
e_{i+1}&\approx |\frac{f''(r)}{2f'(r)}|e_ie_{i-1}\\
&\approx |\frac{f''(r)}{2f'(r)}|^{\alpha-1} e_i^\alpha
\end{align}$$

Con $\alpha=\frac{1+\sqrt{5}}{2}\approx 1.62$. 
Por lo tanto la convergencia de este metodo se denomina **super-lineal** y se encuentra entre la convergencia lineal y cuadratica. En particular se espera que:
$$\frac{e_{i+1}}{e_i^\alpha}\approx L$$