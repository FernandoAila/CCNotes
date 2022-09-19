# Metodo de la bisección

Recordar el siguiente teorema de bolzano:
>[!NOTE] Teorema de bolzano
>Si $f$ es continua en $[a,b]$ y $f(a)f(b) < 0$, entonces $f$ tiene una raiz entre a y b.
 ![[Pasted image 20220831225520.png]]

Podemos crear un algoritmo para encontrar la raiz de una función utilizando esta informacion, sin embargo, hay que notar que se necesita conocer tanto $a$ como $b$, o sea, una *initial guess*:

### Algoritmo
 Idea basica: Tomar el punto medio (initial guess) del intervalo $[a,b]$ y evaluarlo en $f$. $f((a+b)/2)$ de tal forma de elegir un nuevo subintervalo donde se conserve la alternancia de signo. Realizar sucesivamente estas operaciones hasta que el valor del intervalo sea menor a una tolerancia TOL.
![[Pasted image 20220831232123.png]]
#### Pseudocodigo
1. Mientras el largo del intervalo $(b-a)/2$  sea mayor a una tolerancia TOL:
	1.  Tomar el punto medio entre a y b, $c=\frac{a+b}{2}$
		1. Si el $f(c)=0$, tenemos nuestra raiz.
		2. Si no, ver cuales de los intervalos $[a,c]$ y $[c,a]$ cambian de signo y elegirlo, es decir $f(a)f(c)\leq0$ o $f(b)f(c)\leq0$
	2. Hacer $a = c$ o $b=c$ .
2. Retornar el punto medio calculado.

Cada vez que avanzamos de iteracion el largo intervalo se reduce a la mitad.
Por lo tanto:
- Largo inicial: $b-a$
- Largo 1° iteracion: $\frac{b-a}{2}$
- Largo 2° iteracion: $\frac{b-a}{2}\cdot \frac{1}{2}=\frac{b-a}{4}$
- $\cdots$
- Largo n-esima iteracion: $\frac{b-a}{2^n}$

Claramente nuestra initial guess, c o  $x_c$ está en el intervalo $[a,b]$, por lo tanto la distancia entre la raiz que queremos encontrar, $r$,  y $x_c$ va a ser menor  o igual que el largo de la mitad del intervalo.
Por lo tanto satisface que:
$$|x_c^0-r|\leq\frac{b-a}{2}$$


Para la n-esima iteracion:
$$\text{Error absoluto = }|x_c^n-r|\leq\frac{b-a}{2^{n+1}}$$

Esto es especialmente útil para encontrar la cantidad de iteraciones o las evaluaciones de $f(x)$ necesarias para acotar el error, ya que estas ultimas seran $n+2$, ya que estamos contando las evaluaciones de a y b al principio.

>[!NOTE] Definicion
>Una solución es correcta  en $p$ decimales si el error absoluto es menor a $0.5\cdot10^{-p}$

Ej: Determinar cuantas evaluaciones de $f(x)=\cos x-x$ son necesarias para encontrar su raiz en el intervalo $[0,1]$ con una precision de 6 decimales.

Sol: $$\frac{1-0}{2^{n+1}}<0.5\cdot10^{-p}$$$$n>\frac{6}{log_{10}2}=19.9$$

Por lo que necesitamos $20+2=22$ evaluaciones.