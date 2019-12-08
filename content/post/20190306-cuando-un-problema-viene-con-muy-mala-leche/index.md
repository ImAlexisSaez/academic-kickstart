---
title: "Cuando un problema viene con muy mala leche"
slug: "cuando-un-problema-viene-con-muy-mala-leche"
subtitle: "Problema 57"
summary: "Problema 57: un enunciado sencillo que esconde una trampa inesperada."

date: 2019-03-06T05:59:39+02:00
lastmod: 2019-08-04T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Ecuaciones", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Will Turner](https://unsplash.com/@turner_imagery), disponible en [Unsplash](https://unsplash.com/photos/tNt7fOOOgKA)."
---

**Problema 57:** En un verde prado, la hierba crece de forma uniforme y constante. Se sabe que $70$ vacas lo consumirían en $24$ días y que $30$ vacas lo harían en $60$ días. ¿Cuántas vacas se comerían la hierba en $96$ días?

***

El comienzo del enunciado de este ejercicio, aunque en apariencia tan poético como irrelevante, nos ofrece una importante pista para llevar a buen término la resolución del problema. ''En un verde prado'' nos indica que, inicialmente, el mencionado prado posee cierta cantidad de hierba (en otro caso, las vacas ni se molestarían en realizarle una visita el primer día). Consideremos pues, por ejemplo, que dicho prado posee $1$ unidad de hierba (equivalentemente, podríamos decir que está conformado por $a$ unidades de hierba, con $a\in\mathbb{N}$; o que simplemente posee un porcentaje de hierba igual a $100\%$).

Dado que la hierba crece de forma uniforme y constante, designemos por $x$ la altura que gana a diario la hierba en nuestro verde prado. Así, ¿qué cantidad de hierba acumulará dicho prado en $24$ días? Efectivamente, $1+24x$, la unidad de hierba con la que contaba inicialmente más el crecimiento uniforme y constante de esta durante el período de tiempo considerado.

La siguiente cuestión que nos planteamos, acto seguido, es: ¿cuánto come una vaca al día? Dado que las $70$ vacas consumen toda la hierba disponible del verde prado en $24$ días, cada vaca es responsable de la desaparición diaria de la siguiente fracción de hierba:

$$
\dfrac{1 + 24x}{24\cdot 70}.
$$

Ahora bien, $30$ vacas consumen la misma cantidad de hierba en $60$ días, situación que da lugar a que cada vaca disfruta, a diario, de la siguiente fracción de hierba:

$$
\dfrac{1+60x}{60\cdot 30}.
$$

Igualando ambas expresiones, seremos capaces de encontrar cuánto crece la hierba en nuestro querido verde prado a diario, es decir, el valor de $x$. Así,

$$
\dfrac{1 + 24x}{24\cdot 70} = \dfrac{1+60x}{60\cdot 30},
$$

esto es, $1800 + 43200x = 1680 + 100800x$, es decir, 

$$
x = \dfrac{1}{480}.
$$

Sustituyendo ahora, el consumo diario de hierba de una vaca asciende a la fracción

$$
\dfrac{1 + 24\cdot\dfrac{1}{480}}{24\cdot70} = \dfrac{504}{480\cdot1680} = \dfrac{1}{1600}.
$$

Por consiguiente, si cada vaca devora tal fracción de hierba a diario y designamos por $y$ la cantidad de vacas que consumirían nuestro amado verde prado en $96$ días, tendrá que satisfacerse que

$$
\dfrac{1 + 96\cdot\dfrac{1}{480}}{96y} = \dfrac{1}{1600} \Leftrightarrow \dfrac{576}{480\cdot96y} = \dfrac{1}{1600} \Leftrightarrow \dfrac{1}{80y} = \dfrac{1}{1600},
$$

esto es, $20$ serán las vacas que consuman el verde prado en $96$ días.
