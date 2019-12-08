---
title: "Comenzando con la combinatoria (IV)"
slug: "comenzando-con-la-combinatoria-iv"
subtitle: "Problema 62"
summary: "Problema 62: presentando la estrategia de barras y estrellas."

date: 2019-03-23T05:59:39+02:00
lastmod: 2019-08-04T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Combinatoria", "Estrategia de barras y estrellas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Lance Anderson](https://unsplash.com/@lanceanderson), disponible en [Unsplash](https://unsplash.com/photos/2_xN1-zKyLo)."
---

**Problema 62:** Calcula el número de soluciones enteras de la ecuación 

$$
x_1+x_2+\cdots+x_8=24,
$$ 

donde $x_i\geq 2$, para $1\leq i\leq 8$.

***

A diferencia del ejercicio anterior, aquí no buscamos hallar el total de soluciones enteras no negativas de la ecuación, pues nos indican que $x_i\geq 2$, para todo $1\leq i\leq 8$. No obstante, podemos razonar de la siguiente forma: asumamos que disponemos de ocho urnas indistinguibles entre sí y almacenemos dos bolas en cada una de ellas para empezar. De esta manera, quedarán $24 - 2\cdot8 = 8$ bolas idénticas por introducir en las urnas, acción que podemos llevar a cabo de

$$
PR_{15}^{8,7} = \dfrac{15!}{8!\cdot 7!} = \dfrac{15\cdot14\cdot13\cdot12\cdot11\cdot10\cdot9}{7!} = 6435
$$

maneras posibles. A este resultado hemos arribado, recordemos, dado que son necesarias siete *barras*, para representar las ocho urnas sobre la recta real, y hemos de almacenar ocho *estrellas* en los huecos que dicha configuración produce. Así pues, son $6435$ el número de soluciones enteras para la ecuación planteada, considerando que $x_i\geq 2$, para todo $1\leq i\leq 8$.

Si nos damos cuenta, simplemente hemos ignorado aquella parte del problema que sabemos está fija. Técnicamente, esta acción es equivalente a llevar a cabo un cambio de variable del tipo 

$$
x_i = x^{\prime}_i + 2,
$$ 

para $1\leq i\leq 8$, que transforma la ecuación inicial planteada en

$$
(x^{\prime}_1 + 2) + (x^{\prime}_2 + 2) + \cdots + (x^{\prime}_8+2) = 24,
$$

que es equivalente a $x^{\prime}_1 +x^{\prime}_2 +\cdots+x^{\prime}_8 =8$, con la salvedad de que ahora $x^{\prime}_i\geq 0$, para todo $1\leq i\leq 8$ y entonces ahora basta con aplicar los métodos que utilizamos en ejercicios anteriores.
