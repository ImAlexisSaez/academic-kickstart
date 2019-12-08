---
title: "Cuando bailar se convierte en un problema matemático"
slug: "cuando-bailar-se-convierte-en-un-problema-matematico"
subtitle: "Problema 72"
summary: "Problema 72: arreglando parejas descontentas."

date: 2019-04-27T05:59:39+02:00
lastmod: 2019-08-05T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Combinatoria", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [S.](https://unsplash.com/@projct33), disponible en [Unsplash](https://unsplash.com/photos/jLCJF_nmd70)."
---

**Problema 72:** En una fiesta, a la que acuden seis chicos y seis chicas, comienza a sonar la primera canción,

- (a) ¿de cuantas formas pueden organizarse para bailar todos ellos por parejas? (Asume que una pareja está conformada por un chico y una chica).
- (b) Como ninguna chica ha quedado contenta con el desempeño en el baile de su pareja, de cara a la segunda canción, ¿de cuántas maneras pueden organizarse para bailar por parejas de forma que no repitan con la anterior?

***

Para el apartado (a), consideremos, sin pérdida de generalidad, que las chicas escogen su pareja. La primera de ellas dispone, para su elección, de seis opciones, tantas como chicos han acudido a la fiesta. La segunda chica, una vez haya escogido la primera, puede seleccionar su pareja de entre los cinco chicos restantes, y así sucesivamente. Por tanto, utilizando la *regla del producto*, se pueden organizar de

$$
6\cdot5\cdot4\cdot3\cdot2\cdot1 = 6! = 720
$$

formas posibles para bailar por parejas la primera canción.

Alternativamente, y pensando ya más bien en el próximo apartado, imaginemos que la situación a la hora de emparejarse se produce como sigue: situemos en una fila a los chicos y, en frente de ellos, en otra fila parelela a las chicas. Ellas poseen en sus manos un papel con un número del $1$ al $6$, al igual que ellos. Supongamos que los números de los chicos están ordenados de menor a mayor, situación que, abreviadamente, denotaremos por $123456$. Después, dejamos que las chicas intercambien sus posiciones entre ellas como deseen y saquen a bailar al chico que al final tengan en frente. Así, las chicas podrían ordenarse, en función de los números que llevan entre manos, como $654321$ y se formarían las parejas de baile $(1,6)$, $(2,5)$, $(3,4)$, $(4,3)$, $(5,2)$ y $(6,1)$, que podemos denotar de forma más abreviada como $123456\rightarrow 654321$. La pregunta que surge ahora es, ¿de cuántas maneras pueden ordenarse las seis chicas? Efectivamente, como el orden es importante y no es posible repetir elemento alguno (una chica no puede bailar a la vez con dos chicos), el total de formas coincide con la cantidad de permutaciones de seis elementos, esto es, $P_6 = 6! = 720$ maneras posibles.

En cuanto al apartado (b), comencemos reduciendo un poco la magnitud del problema, para así visualizar cómo abordarlo. Consideremos únicamente tres chicos y tres chicas, y supongamos, por ejemplo, que para la primera canción las parejas se conformaron fueron $123\rightarrow 123$. Como en la segunda canción ninguna de ellas quiere repetir con la pareja anterior, las dos únicas opciones disponibles serían $123\rightarrow 231$ y $123\rightarrow 312$, esto es, los dos desarreglos.

Por el [ejercicio anterior](/2019/04/24/presentando-desarreglos/), y ya volviendo al problema que contempla seis chicos y seis chicas, sabemos que

$$
D_6 = 6!\left(\dfrac{1}{2} - \dfrac{1}{6} + \dfrac{1}{24} - \dfrac{1}{120} + \dfrac{1}{720}\right) = 265
$$

son las maneras en que pueden organizarse, para bailar por parejas los seis chicos y las seis chicas, de forma que no repitan con la anterior.
