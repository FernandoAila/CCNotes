### Teoremas 
>[!NOTE] Definicion: Metodo localmente convergente  
>Un metodo iterativo se dice localmente convergente a $r$ si este converge a $r$ para *initial guesses* suficientemente cercanos a $r$.

Es decir, que una IPF puede diverger si utilizamos una *initial guess* equivocada incluso si $|g'(r)| < 1$.

>[!NOTE] Definicion: Teorema del valor intermedio
>Sea $f$ continua en $[a,b]$ entonces $f$ recorre cada valor entre $f(a)$  y $f(b)$. Es decir. si $y$ es un numero entre $f(a),f(b)$ entonces existe un $c$ tal que $f(c) = y$

>[!NOTE] Definicion: Teorema de Rolle
>Sea $f$ continua y diferenciable en $[a,b]$ y $f(a) = f(b)$. Entonces existe un $c$  entre $[a,b]$  tal que $f'(c) = 0$.

Analogo al teorema del valor medio donde: $$f'(c) = \frac{f(b)-f(a)}{b-a}=\frac{0}{b-a}=0$$


>[!NOTE] Teorema de taylor con  residuo
>Sea $x$ y $x_0$ numeros reales y $f(x)$ $k$ veces diferenciable en $[x, x_0]$ entonces existe un numero c entre $x$ y $x_0$ tal que:
> ![[Pasted image 20220917215006.png]]

Basicamente estamos aproximando la funcion $f(x)$  en torno al vecindario del punto $x_0$ a partir de ciertos polinomios usando la llamada serie de taylor centrada en $x_0$.
![[Pasted image 20220917220255.png]]

En cada termino la aproximacion es diferente, por ejemplo, la primera aproximacion seria una constante, luego una recta, despues una parabola, etc. Por ejemplo, estariamos utilizando los primeros 3 terminos de la serie mostrada en la imagen. Y es exacta justo en el punto $x=x_0$ y el error empieza a aumentar a medida que nos alejamos de $x_0$. Lo que nos sirve justamente para conocer el comportamiento local de la f

En particular:
- Considerando 1 termino: $f(x) \approx f(x_0)$, el error es de orden $O(x-x_0)$
- Con 2 terminos : $f(x) \approx f(x_0) + f'(x_0)(x-x_0)$ el error es de orden $O((x-x_0)^2)$

Así sucesivamente.