+++
title = "Tres dados buscando sumar diez"
slug  = "tres-dados-buscando-sumar-diez"
subtitle = "Problema 74"
summary  = "Problema 74: reforzando el Principio de inclusión-exclusión."

date     = 2019-05-04T05:59:39+02:00
#lastmod = 2019-05-04T11:37:00+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Combinatoria", "Estrategia de barras y estrellas", "Problemas"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Fabrice Villard](https://unsplash.com/@fabulu75), disponible en [Unsplash](https://unsplash.com/photos/UqGeqvrwBKg)."
+++

**Problema 74:** En el lanzamiento simultáneo de tres dados distintos, ¿de cuántas maneras la suma de las puntuaciones puede ascender a diez?

***

Si asumimos que trabajamos con tres dados estándar y representamos por $x\_i$ la puntuación obtenida en el lanzamiento del $i$-ésimo dado, con $1\leq i\leq 3$, buscamos encontrar el número de soluciones enteras de la ecuación $x\_1+x\_2+x\_3 = 10$, donde $1\leq x\_i\leq 6$, para $1\leq i\leq 3$.

Seguiremos, a continuación, el mismo esquema que figura en el [ejercicio anterior](/2019/05/01/una-vuelta-de-tuerca-para-la-estrategia-de-barras-y-estrellas/), esto es, utilizaremos el *Principio de complementación*, de forma que calcularemos el número de soluciones enteras no negativas (que satisfagan las restricciones de mayor o igual para las variables involucradas) de la ecuación propuesta y, después, haciendo uso del *Principio de inclusión-exclusión*, descontaremos aquellas que no satisfagan las restricciones impuestas.

Así pues, empecemos planteando la ecuación $x\_1+x\_2+x\_3=10$, con $x\_i\geq 1$ para todo $1\leq i\leq 3$. Pensando en términos de urnas y bolas, hemos de almacenar una bola en cada urna y pasar a encontrar entonces el número de soluciones enteras no negativas de la ecuación $x\_1+x\_2+x\_3=7$, ahora con $x\_i\geq 0$, para $1\leq i\leq 3$. Aplicando la técnica de *barras y estrellas*, como en ejercicios previos, sabemos que dicho número equivale al total de permutaciones con repetición de nueve elementos, donde uno de ellos se repite dos veces, mientras que el otro lo hace en siete ocasiones, esto es,

$$
PR\_{9}^{2,7} = CR\_{3,7} = \dbinom{9}{7} = \dfrac{9\cdot8}{2!} = 36.
$$


Definamos, acto seguido, los conjuntos $A\_i = \\{x\_i\geq 7\\}$, para $1\leq i\leq 3$, por lo que estamos interesados en hallar el valor de $card(\overline{A\_1} \cap \overline{A\_2} \cap \overline{A\_3})$. Por el *Principio de complementación*,

$$
card(\overline{A\_1} \cap \overline{A\_2} \cap \overline{A\_3}) = card(E) - card(A\_1\cup A\_2\cup A\_3),
$$

donde por $E$ representamos al *conjunto total*, que en este contexto se refiere al total de soluciones enteras no negativas de la ecuación planteada y cuyo cardinal hemos obtenido en párrafos anteriores, $PR\_{9}^{2,7} = 36$. Aplicando ahora el *Principio de inclusión-exclusión*,

$$
card\left(\bigcup\_{i=1}^{3}{A\_i}\right) = \sum_{i=1}^{3}{card(A\_i)} - \sum\_{1\leq i<j\leq 3}{card(A\_i\cap A\_j)} + card\left(\bigcap\_{i=1}^{3}{A\_i}\right).
$$

Estudiemos ahora el conjunto $A\_1 = \\{x\_1\geq 7\\}$ y averigüemos $card(A\_1)$. La situación requiere calcular el número de soluciones enteras no negativas para la ecuación $x\_1+x\_2+x\_3=10$, con $x\_1\geq 7$, $x\_i\geq 1$ para $2\leq i\leq 3$. Pensando en términos de urnas y bolas, hemos de almacenar siete bolas en la primera urna, una en la segunda, una en la tercera y pasar a encontrar entonces el número de soluciones enteras no negativas de la ecuación $x\_1+x\_2+x\_3=1$, ahora con $x\_i\geq 0$, para $1\leq i\leq 3$. Aplicando, de manera análoga a como lo hicimos arriba, la técnica de *barras y estrellas*, sabemos que dicho número equivale al total de permutaciones con repetición de tres elementos, donde uno de ellos se repite dos veces, mientras que el otro lo hace en una ocasión, esto es,

$$
PR\_{3}^{1,2} = CR\_{3,1} = \dbinom{3}{1} = 3.
$$

Por simetría, $card(A\_1)=card(A\_2)=card(A\_3)=3$, de manera que

$$
\sum\_{i=1}^{3}{card(A\_i)} = 9.
$$

Por lo que respecta al resto de casos, cuando intersecamos dos o más conjuntos las restricciones imponen una suma mayor o igual que $14$, por lo que es imposible que se satisfaga en enteros no negativos la ecuación $x\_1+x\_2+x\_3=10$, esto es, los cardinales asociados a las correspondientes intersecciones serán nulos.

Por tanto, recapitulando,

$$
card(\overline{A\_1} \cap \overline{A\_2} \cap \overline{A\_3}) = 36-9 = 27
$$

son las maneras en las que, en el lanzamiento simultáneo de tres dados distintos, la suma de las puntuaciones asciende a diez.
