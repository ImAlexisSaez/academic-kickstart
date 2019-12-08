---
title: "Tres dados buscando sumar diez"
slug: "tres-dados-buscando-sumar-diez"
subtitle: "Problema 74"
summary: "Problema 74: reforzando el Principio de inclusión-exclusión."

date: 2019-05-04T05:59:39+02:00
lastmod: 2019-08-06T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Combinatoria", "Estrategia de barras y estrellas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Fabrice Villard](https://unsplash.com/@fabulu75), disponible en [Unsplash](https://unsplash.com/photos/UqGeqvrwBKg)."
---

**Problema 74:** En el lanzamiento simultáneo de tres dados distintos, ¿de cuántas maneras la suma de las puntuaciones puede ascender a diez?

***

Si asumimos que trabajamos con tres dados estándar y representamos por $x_i$ la puntuación obtenida en el lanzamiento del $i$-ésimo dado, con $1\leq i\leq 3$, buscamos encontrar el número de soluciones enteras de la ecuación $x_1+x_2+x_3 = 10$, donde $1\leq x_i\leq 6$, para $1\leq i\leq 3$.

Seguiremos, a continuación, el mismo esquema que figura en el [ejercicio anterior](/2019/05/01/una-vuelta-de-tuerca-para-la-estrategia-de-barras-y-estrellas/), esto es, utilizaremos el *Principio de complementación*, de forma que calcularemos el número de soluciones enteras no negativas (que satisfagan las restricciones de mayor o igual para las variables involucradas) de la ecuación propuesta y, después, haciendo uso del *Principio de inclusión-exclusión*, descontaremos aquellas que no satisfagan las restricciones impuestas.

Así pues, empecemos planteando la ecuación $x_1+x_2+x_3=10$, con $x_i\geq 1$ para todo $1\leq i\leq 3$. Pensando en términos de urnas y bolas, hemos de almacenar una bola en cada urna y pasar a encontrar entonces el número de soluciones enteras no negativas de la ecuación $x_1+x_2+x_3=7$, ahora con $x_i\geq 0$, para $1\leq i\leq 3$. Aplicando la técnica de *barras y estrellas*, como en ejercicios previos, sabemos que dicho número equivale al total de permutaciones con repetición de nueve elementos, donde uno de ellos se repite dos veces, mientras que el otro lo hace en siete ocasiones, esto es,

$$
PR_{9}^{2,7} = CR_{3,7} = \dbinom{9}{7} = \dfrac{9\cdot8}{2!} = 36.
$$


Definamos, acto seguido, los conjuntos $A_i = \\{x_i\geq 7\\}$, para $1\leq i\leq 3$, por lo que estamos interesados en hallar el valor de $card(\overline{A_1} \cap \overline{A_2} \cap \overline{A_3})$. Por el *Principio de complementación*,

$$
card(\overline{A_1} \cap \overline{A_2} \cap \overline{A_3}) = card(E) - card(A_1\cup A_2\cup A_3),
$$

donde por $E$ representamos al *conjunto total*, que en este contexto se refiere al total de soluciones enteras no negativas de la ecuación planteada y cuyo cardinal hemos obtenido en párrafos anteriores, $PR_{9}^{2,7} = 36$. Aplicando ahora el *Principio de inclusión-exclusión*,

$$
card\left( \bigcup_{i = 1}^{3}{A_{i}} \right) = \sum_{i = 1}^{3}{card(A_{i})} - \sum_{1 \leq i < j \leq 3}{card(A_{i} \cap A_{j})} + card\left( \bigcap_{i = 1}^{3}{A_{i}} \right).
$$

Estudiemos ahora el conjunto $A_1 = \\{x_1\geq 7\\}$ y averigüemos $card(A_1)$. La situación requiere calcular el número de soluciones enteras no negativas para la ecuación $x_1+x_2+x_3=10$, con $x_1\geq 7$, $x_i\geq 1$ para $2\leq i\leq 3$. Pensando en términos de urnas y bolas, hemos de almacenar siete bolas en la primera urna, una en la segunda, una en la tercera y pasar a encontrar entonces el número de soluciones enteras no negativas de la ecuación $x_1+x_2+x_3=1$, ahora con $x_i\geq 0$, para $1\leq i\leq 3$. Aplicando, de manera análoga a como lo hicimos arriba, la técnica de *barras y estrellas*, sabemos que dicho número equivale al total de permutaciones con repetición de tres elementos, donde uno de ellos se repite dos veces, mientras que el otro lo hace en una ocasión, esto es,

$$
PR_{3}^{1,2} = CR_{3,1} = \dbinom{3}{1} = 3.
$$

Por simetría, $card(A_1)=card(A_2)=card(A_3)=3$, de manera que

$$
\sum_{i=1}^{3}{card(A_i)} = 9.
$$

Por lo que respecta al resto de casos, cuando intersecamos dos o más conjuntos las restricciones imponen una suma mayor o igual que $14$, por lo que es imposible que se satisfaga en enteros no negativos la ecuación $x_1+x_2+x_3=10$, esto es, los cardinales asociados a las correspondientes intersecciones serán nulos.

Por tanto, recapitulando,

$$
card(\overline{A_1} \cap \overline{A_2} \cap \overline{A_3}) = 36-9 = 27
$$

son las maneras en las que, en el lanzamiento simultáneo de tres dados distintos, la suma de las puntuaciones asciende a diez.
