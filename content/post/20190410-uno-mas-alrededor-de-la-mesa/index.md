+++
title = "Uno más alrededor de la mesa"
slug  = "uno-mas-alrededor-de-la-mesa"
subtitle = "Problema 67"
summary  = "Problema 67: ¡otra ronda de permutaciones circulares!"

date     = 2019-04-10T05:59:39+02:00
#lastmod = 2019-04-10T10:04:05+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Combinatoria", "Permutaciones circulares", "Problemas"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Marita Kavelashvili](https://unsplash.com/@maritafox), disponible en [Unsplash](https://unsplash.com/photos/ugnrXk1129g)."
+++

**Problema 67:** Encuentra el número de maneras en que pueden sentarse $n$ matrimonios alrededor de una mesa si

- (a) hombres y mujeres se alternan.
- (b) cada mujer está sentada al lado de su marido.

***

Para el apartado (a) empecemos sentando, por ejemplo, a los hombres (podríamos haber iniciado la resolución colocando a las mujeres asimismo, pues el número de personas coincide). Sabemos, por ejercicios anteriores, que el total de formas de sentar a $n$ personas alrededor de una mesa asciende al total de permutaciones circulares de $n$ elementos, esto es, hay 

$$
PC\_n = (n-1)!
$$ 

maneras. A continuación, comencemos a sentar mujeres. La primera de ellas puede hacerlo en cualesquiera de los $n$ huecos que la configuración de los hombres produce. Para la segunda, una vez sentada la primera, son $n-1$ las opciones que tiene a su disposición para ubicarse. En cuanto a la tercera, una vez sentadas las dos anteriores, tiene a su disposición $n-2$ asientos para escoger su sitio, y así sucesivamente. Aplicando la *regla del producto*, hay

$$
(n-1)!\cdot n\cdot(n-1)\cdot(n-2)\cdot\ldots\cdot2\cdot1 = (n-1)!n!
$$

maneras en que pueden sentarse $n$ matrimonios alrededor de una mesa si hombres y mujeres han de alternar sus sitios.

Para el apartado (b), consideremos cada matrimonio como una unidad indivisible. Sabemos, por ejercicios anteriores, que el número de formas de disponer $n$ elementos alrededor de una mesa equivale al total de permutaciones circulares de $n$ elementos, es decir, $PC\_n = (n-1)!$. Ahora bien, el primer matrimonio puede sentarse de dos maneras posibles (hombre - mujer o mujer - hombre), hecho que hemos de tener en cuenta. Lo mismo sucede para el segundo matrimonio, para el tercero, y así sucesivamente. Por consiguiente, aplicando la *regla del producto*, existen

$$
(n-1)!\cdot2\cdot2\cdot\ldots\cdot2 = (n-1)!\cdot2^n
$$

maneras en que pueden sentarse $n$ matrimonios alrededor de una mesa si cada mujer ha de estar sentada al lado de su marido. Alternativamente, podemos abordar este apartado sentando primero a los hombres, acción que sabemos podemos llevar a cabo de $PC\_n=(n-1)!$ formas posibles y luego considerar que cada mujer tiene sus opciones bastante limitadas a la hora de sentarse, pues únicamente puede hacerlo de dos manera posibles (a la izquierda o a la derecha de su marido). Como hemos de colocar $n$ mujeres asumiendo la restricción anterior, son $2^n$ las formas posibles y aplicando la *regla del producto* se llega al resultado alcanzado arriba.