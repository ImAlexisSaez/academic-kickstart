---
title: "¡A la mesa! ¡Todos a la mesa!"
slug: "a-la-mesa-todos-a-la-mesa"
subtitle: "Problema 66"
summary: "Problema 66: introduciendo las permutaciones circulares."

date: 2019-04-06T05:59:39+02:00
lastmod: 2019-08-05T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Combinatoria", "Permutaciones circulares", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Erik Mclean](https://unsplash.com/@introspectivedsgn), disponible en [Unsplash](https://unsplash.com/photos/rCCF1wC-c8M)."
---

**Problema 66:** ¿De cuántas maneras pueden cinco chicos y tres chicas sentarse alrededor de una mesa si

- a) no hay restricción alguna?
- b) el chico $H_1$ y la chica $M_1$ no pueden estar juntos?
- c) ninguna chica ha de tener a otra a su lado?

***

Para el apartado a), al no imponer restricción alguna sobre la disposición de los ocho integrantes del grupo, el número de formas en las que pueden sentarse alrededor de una mesa equivale al total de permutaciones circulares de ocho elementos. Así, tienen

$$
PC_8 = (8-1)! = 7! = 5040
$$

maneras de sentarse alrededor de la mesa.

Por lo que respecta al apartado b), ya que acabamos de calcular en el párrafo anterior el total de maneras en que pueden sentarse, resulta más sencillo utilizar ahora el *Principio de complementación*, que recordemos dice *si $A$ es un subconjunto de un conjunto finito universal $U$, entonces*

$$
card(U - A) = card(U) - card(A).
$$

De esta forma, en lugar de contar el número de formas en que $H_1$ y $M_1$ pueden sentarse estando separados (es decir, con al menos un integrante del grupo entre ellos), averigüemos de cuántas maneras pueden sentarse todos alrededor de la mesa estando $H_1$ y $M_1$ juntos. Así, si consideramos la pareja como una unidad, el nuevo problema se reduce a encontrar el número de formas en que pueden disponerse siete elementos alrededor de una mesa, que sabemos equivale al total de permutaciones circulares de siete elementos, esto es,

$$
PC_7 = (7-1)! = 6! = 720.
$$

Ahora bien, como la pareja puede sentarse de maneras posibles, ($H_1M_1$ y $M_1H_1$), hemos de incorporar las permutaciones de dos elementos ($2! = 2$) al anterior resultado, aplicando la *regla del producto*. Por consiguiente, existen $720\cdot2 = 1440$ formas de sentarse los ocho integrantes del grupo asumiendo que $H_1$ y $M_1$ se colocaron uno al lado del otro. Luego, por el *Principio de complementación* hay

$$
7! - 1440 = 3600
$$

maneras de disponer a los miembros del grupo donde $H_1$ y $M_1$ no están juntos.

Finalmente, en el apartado c), comencemos sentando a los chicos en la tabla, ya que su número es más elevado que el de chicas. Por apartados anteriores, sabemos que el número de formas de sentar cinco personas alrededor de una tabla asciende al total de permutaciones circulares de cinco elementos, esto es,

$$
PC_5 = (5-1)! = 4! = 24
$$

maneras posibles. A continuación, en los huecos que quedan entre ellos, empecemos a sentar chicas. Para la primera de ella encontramos cinco opciones disponibles, pues tal es el número de huecos que quedan entre los chicos. Para la segunda chica, una vez sentada la primera, dichas opciones se reducen a cuatro. Por último, la tercera chica, una vez sentadas las otras dos, puede escoger entre las tres posiciones disponibles que restan. Luego, aplicando la *regla del producto* hay

$$
4! \cdot 5\cdot 4\cdot3 = 1440
$$

maneras de disponer a los ocho integrantes del grupo de forma que ninguna chica tenga a otra a su lado.
