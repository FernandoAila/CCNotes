# Raices en 1D

Obj:  Buscar ceros, o raices, de una función.

Def: $f(x)$ tiene una raiz en $x=r$ si $f(r) =0$.
Es decir cuando la función "cruza" el eje $x$.

![[Pasted image 20220831221430.png]]

>[!INFO] Tip
Podemos facilmente, buscar la raiz de cualquier función igualandola a "cero", de la forma $$g(x)=f(x)-a$$$$4x+1=2$$$$4x+1-2=0$$

Buscar raices, tiene muchas aplicaciones, por ejemplo al buscar el máximo o minimo de una función tenemos que hacer la derivada de $f(x)$ igual a 0, $f'(r)=0$.

No siempre existen raices de una funcion, ejemplo:
$$sin(x)=2$$
Como $-1 \leq sin(x) \leq 1$, entonces la función nunca llega a tener el valor 2, por lo que se dice que no tiene raiz.




## Metodo de la bisección

Recordar el siguiente teorema de bolzano:
>[!NOTE] Teorema de bolzano
>Si $f$ es continua en $[a,b]$ y $f(a)f(b) < 0$, entonces $f$ tiene una raiz entre a y b.
 ![[Pasted image 20220831225520.png]]

Podemos crear un algoritmo para encontrar la raiz de una función utilizando esta informacion, sin embargo, hay que notar que se necesita conocer tanto $a$ como $b$, osea, una *initial guess*:

### Algoritmo
 Idea basica: Tomar el punto medio del intervalo $[a,b]$ y evaluarlo en $f$. $f((a+b)/2)$ de tal forma de elegir un nuevo subintervalo donde se conserve la alternancia de signo. Realizar sucesivamente estas operaciones hasta que el valor del intervalo sea menor a una tolerancia TOL.
![[Pasted image 20220831232123.png]]

Cada vez que avanzamos de iteracion el largo intervalo se reduce a la mitad.
Por lo tanto:
- Largo inicial: $b-a$
- Largo 1° iteracion: $\frac{b-a}{2}$
- Largo 2° iteracion: $\frac{b-a}{2}\cdot \frac{1}{2}=\frac{b-a}{4}$
- $\cdots$
- Largo n-esima iteracion: $\frac{b-a}{2^n}$