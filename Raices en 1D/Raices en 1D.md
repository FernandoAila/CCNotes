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
## Metodos

Existen muchos metodos para la busqueda de ceros o raices, algunos son:
- [[Metodo de la bisección]]
- [[Iteracion de punto fijo]]
	- [[Metodo de newton]]
- [[Metodo de la secante]]

Los cuales convergen de diferentes maneras, lineal, superlineal y cuadratica:
- Lineal, se tiene que: $\frac{e_{i+1}}{e_i} = S < 1$, con orden de convergencia 1
- Superlineal: $\frac{e_{i+1}}{e_i^{\alpha}} \approx L$, con orden de convergencia $\alpha=\frac{1+\sqrt{5}}{2}\approx 1.62$
- Cuadratica: $\frac{e_{i+1}}{e_i^2}\approx M=|\frac{f''(r)}{2f'(r)}|$ con orden de convergencia 2.

## Criterios de detencion
Estos algoritmos deben tener un criterio de detencion con el objetivo de que no siga calculando indefinidamente por ejemplo:

1. Error absoluto: $|x_i-x_{i+1}| < TOL$, donde $x_{i+1}$ reemplaza a la raiz $r$.
2. Error relativo: $\frac{|x_{i}-x_{i+1}|}{|x_{i+1}|}<TOL$, donde $x_{i+1}$ reemplaza a la raiz $r$ (problema division x 0).
3. Error relativo acotado: $\frac{|x_{i}-x_{i+1}|}{\max{|x_{i+1}|,\theta}}<TOL$, donde $x_{i+1}$ reemplaza a la raiz $r$


## Sensibilidad
Considerar el polinomio de Wilkinson:
![[Pasted image 20220919205959.png]]
Que tiene como raices $[1,2,3,\cdots,20]$.
Si expandimos el polinomios queda:
![[Pasted image 20220919210104.png]]
Si buscamos una raiz en el polinomio expandido, con initial guess $x_0=16$ se tiene que:
![[Pasted image 20220919210237.png]]
Pero sabemos que el raiz equivale a $16$, y por lo tanto el error absoluto registrado es del orden de $10^{-3}$.
Dado que trabajamos con el [[Estandar del punto flotante]], la funcion ya no es la original en el sentido que se inducen errores en la aproximacion, y se comportará de la forma: $$f_1(x)=f(x)+\epsilon g(x)$$
Donde esta nueva funcion tendrá una raiz nueva que no necesariamente es  es la original. $\epsilon g(x)$ corresponde a la perturbacion aplicada.
Esto se expresa como:$$f(r+\Delta r)+\epsilon g(r+\Delta)=0$$
Si expandimos con Taylor en torno a $r$:
![[Pasted image 20220920031441.png]]
Como $g'(r)<<f'(r)$:
![[Pasted image 20220920031656.png]]

Volviendo al polinomio de Wilkinson, analizando el 15avo termino:
![[Pasted image 20220920032250.png]]
![[Pasted image 20220920032320.png]]

![[Pasted image 20220928000930.png]]
