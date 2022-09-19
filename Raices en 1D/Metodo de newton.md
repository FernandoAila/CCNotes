# Metodo de newton


El [[Teorema de Taylor]], nos indica la siguiente expresion al considerar 3 terminos de la expansion para $f(x)$:$$f(x)=f(x_0)+f'(x_0)(x-x_0)+\frac{f''(c)(x-x_0)^2}{2!}$$
Si estamos interesados en encontrar una raiz,  es decir, queremos encontrar un $r$ tal que $f(r)=0$, reemplazamos por $x$ por $r$:
$$f(r)=f(x_0)+f'(x_0)(r-x_0)+\frac{f''(c)(r-x_0)^2}{2!}$$$$0=f(x_0)+f'(x_0)(r-x_0)+\frac{f''(c)(r-x_0)^2}{2!}$$Despejando $r$ de $f'(x_0)(r-x_0)$:$$\begin{align}
-f'(x_0)(r-x_0)&=f(x_0)+\frac{f''(c)(r-x_0)^2}{2!}\\
(r-x_0)&=(f(x_0)+\frac{f''(c)(r-x_0)^2}{2!})\frac{1}{-f'(x_0)}\\
r&=x_0-\frac{f(x_0)}{f'(x_0)}-\frac{f''(c)(r-x_0)^2}{2f'(x_0)}\\
\end{align}$$
Este despeje requiere conocer el valor de $c$ y $r$. Sin embargo podemos obtener una aproximacion dejando fuera el tercer termino de la expansion, el termino cuadratico, es decir:
$$x_1=x_0-\frac{f(x_0)}{f'(x_0)}$$
Lo cual da origen al **metodo de newton**, o sea una [[Iteracion de punto fijo]]:$$x_{i+1}=x_i-\frac{f(x_i)}{f'(x_i)}$$


En general, este metodo converge mucho más rapido que el metodo de la bisección o alguna IPF con convergencia lineal. En particular, se dice que el metodo de newton converge **cuadraticamente**.
Sin embargo, notar que necesitamos saber la derivada de la funcion.
Al igual que una IPF, el algoritmo del metodo de newton es el siguiente:
![[Pasted image 20220918152152.png]]
Ejemplo: $f(x)=x^3+x-1$ donde $f'(x)=3x^2+1$: $$\begin{align}
x_{i+1}&=x_i-\frac{x_i^3+x_i-1}{3x_i^2+1}\\
x_{i+1}&=\frac{2x_i^3+1}{3x_i^2+1}
\end{align}$$
Cuyos resultados son:
![[Pasted image 20220918161753.png]]


Notar que en la tabla, el error ($e_i$) no obedece un comportamiento lineal, por lo que el $S= \frac{e_{i+1}}{e_i}$ no se hace constante, sin embargo el cuociente $\frac{e_{i}}{e_{i-1}^2}$ si que lo es, lo que indica un comportamiento cuadratico, y por lo tanto un algoritmo mucho más rapido.


 >[!NOTE] Convergencia Cuadratica
>Sea $e_i=|x_i-r|$ el error absoluto del paso i de un metodo iterativo, con $x_i$ como el valor computado y $r$ la raiz real de la funcion.
>Si se cumple que:
>$$\lim_{i\rightarrow\infty} \frac{e_{i+1}}{e_i^2}=M<\infty$$
>Entonces el metodo converge cuadraticamente.


 >[!NOTE] Definicion
>Sea $f(x)$ una funcion 2 veces diferenciable y $f(r)=0$. Si **$f'(r)\neq0$** entonces el metodo de Newton es local y converge cuadraticamente a $r$. El error en el paso $i$ satisface que: $$\frac{e_{i+1}}{e_i^2}=M$$  donde $$M= \frac{|f''(r)|}{2|f'(r)|}$$

Notese el supuesto donde $f'(r)\neq 0$, esto ocurre por ejemplo, cuando en la raiz hay un maximo, minimo, punto de inflexion, etc. ¿Entonces, que ocurre cuando efectivamente $f'(r)=0$?

Se dice que una raiz $r$ de $f$ tiene una multiplicidad $m$ si $0=f(r)=f'(r)=f''(r)=\cdots=f^{(m-1)}(r)$ pero $f^{m}(r)\neq0$.

Por ejemplo, sea $f(x)=x^2$, con raiz $r=0$ y $f'(x)=2x$, $f'(r)=0$, la iteraracion de newton es: $$\begin{align}
x_{i+1}&=x_{i}-\frac{x^2}{2x}\\
&= \frac{x_i}{2}
\end{align}$$
Como $r=0$ sumamos $r$ ambos lados y aplicamos valor absoluto:
$$\begin{align}
|x_{i+1}-r|&=\frac{|x_i-r|}{2}\\
e_{i+1}&=\frac{e_i}{2}\\
\frac{e_{i+1}}{e_i}&=\frac{1}{2}

\end{align}$$
Por lo que $S=1/2$ y por lo tanto, la tasa de convergencia es lineal y no cuadratica, tal como en las siguientes iteraciones luego de aplicar el metodo de newton.
![[Pasted image 20220918181254.png]]

>[!INFO] Esto tambien ocurre con una funcion de la forma $f(x)=x^m$, donde $f'(x)=(m)x^{m-1}$, ya que el metodo de newton queda $x_{i+1}=\frac{m-1}{m}x_i$ 


 >[!NOTE] Convergencia Lineal del metodo de newton
>Sea $e_i=|x_i-r|$ el error absoluto del paso i de un metodo iterativo, con $x_i$ como el valor computado y $r$ la raiz real de la funcion.
>Si $f$ es una funcion $m+1$ veces continua y diferenciable en $[a,b]$ y tiene una multiplicidad $m$ en la raiz $r$. Entonces el metodo de newton converge a $r$ linealmente con tasa S
>
>$$\lim_{i\rightarrow\infty} \frac{e_{i+1}}{e_i}=\frac{m-1}{m}=S \neq 0$$


Podemos corregir esta situacion, conociendo la multiplicidad de la raiz de la siguiente forma:

 >[!NOTE] Metodo de Newton modificado
>Si $f$ es una funcion $m+1$ veces continua y diferenciable en $[a,b]$, donde la raiz $r$ tiene una multiplicidad $m$, entonces el metodo de Newton modificado:
>$$x_{i+1}=x_i-m\frac{f(x_i)}{f'(x_i)}$$ Converge local y cuadraticamente a $r$.


