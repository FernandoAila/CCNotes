# Metodo de la secante


El metodo de Newton requiere conocer de antemano la derivada de la funcion $f$, o en su defecto, puede que esta sea costosa de calcular. El metodo de la bisección serviria en este caso, pero nos da una convergencia lineal de solo $S=\frac{1}{2}$. La pregunta radica entonces, en encontrar un metodo que no requiera conocer (o calcular) la derivada de la funcion, y que converja más rapido que el metodo de la bisección. Para este caso surge el **metodo de la secante**, cuya idea principal radica en aproximar la derivada de la función.

Recordar entonces la definicion de derivada:$$ f'(x)=\lim_{\Delta x \rightarrow 0}\frac{f(x_0+\Delta x)-f(x)}{\Delta x}$$

