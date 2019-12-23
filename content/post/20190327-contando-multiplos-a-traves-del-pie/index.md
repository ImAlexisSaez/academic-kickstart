---
title: "Contando múltiplos a través del PIE"
slug: "contando-multiplos-a-traves-del-pie"
subtitle: "Problema 63"
summary: "Problema 63: un resultado útil donde los haya."

date: 2019-03-27T05:59:39+02:00
lastmod: 2019-03-27T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Combinatoria", "Principio de inclusión-exclusión", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Damon Lam](https://unsplash.com/@dayday95), disponible en [Unsplash](https://unsplash.com/photos/T3SnWggaxWw)."
---

**Problema 63:** ¿Cuántos números entre $1$ y $600$ no son divisibles por $3$, ni por $5$, ni por $7$?

***

Emplearemos el *Principio de inclusión-exclusión* para resolver el presente problema. Así, definamos los conjuntos

- $3$ como ''conjunto de números menores o iguales que $600$ que son divisibles por $3$'',
- $5$ como ''conjunto de números menores o iguales que $600$ que son divisibles por $5$'', y
- $7$ como ''conjunto de números menores o iguales que $600$ que son divisibles por $7$''.

Estamos interesados en el cardinal del conjunto de números que, precisamente, no son divisibles por $3$, ni por $5$, ni por $7$, esto es, $card(\overline{3}\cap\overline{5}\cap\overline{7})$ . Ahora bien, por las *Leyes de DeMorgan*, trabajaremos con el suceso complementario, ya que es más fácil contar múltiplos que números que no son múltiplos,

$$
card(\overline{3}\cap\overline{5}\cap\overline{7}) = card(\overline{3\cup 5\cup 7}) = card(E) - card(3\cup 5\cup 7),
$$

donde por $E$ representamos el conjunto de los números enteros positivos menores o iguales que $600$, es decir, el conjunto *total*, cuyo cardinal asciende, en esta ocasión concreta, a $600$. Por tanto,

$$
card(\overline{3}\cap\overline{5}\cap\overline{7}) = 600 - card(3\cup 5\cup 7).
$$

A continuación, por el *Principio de inclusión-exclusión*,

$$
\begin{aligned}
card(3\cup 5\cup 7) &= card(3) + card(5) + card(7)\\\\ &\quad -card(3\cap 5) - card(3\cap 7) - card(5\cap 7)\\\\ &\quad +card(3\cap 5\cap 7),
\end{aligned}
$$

donde

- $card(3)$ representa el total de múltiplos de $3$ menores o iguales que $600$, esto es, 

$$
card(3) = \left\lfloor\dfrac{600}{3}\right\rfloor=200.
$$

- $card(5)$ representa el total de múltiplos de $5$ menores o iguales que $600$, esto es, 
 
$$
card(5) = \left\lfloor\dfrac{600}{5}\right\rfloor=120.
$$

- $card(7)$ representa el total de múltiplos de $7$ menores o iguales que $600$, esto es, 
 
$$
card(7) = \left\lfloor\dfrac{600}{7}\right\rfloor=85.
$$

- $card(3\cap 5)$ representa el total de múltiplos de $3$ y de $5$ menores o iguales que $600$, esto es, 
 
$$
card(3\cap 5) = \left\lfloor\dfrac{600}{3\cdot 5}\right\rfloor=40.
$$

- $card(3\cap 7)$ representa el total de múltiplos de $3$ y de $7$ menores o iguales que $600$, esto es, 
 
$$
card(3\cap 7) = \left\lfloor\dfrac{600}{3\cdot 7}\right\rfloor=28.
$$

- $card(5\cap 7)$ representa el total de múltiplos de $5$ y de $7$ menores o iguales que $600$, esto es, 
 
$$
card(5\cap 7) = \left\lfloor\dfrac{600}{5\cdot 7}\right\rfloor=17.
$$

- $card(3\cap 5\cap 7)$ representa el total de múltiplos de $3$, de $5$ y de $7$ menores o iguales que $600$, esto es, 
 
$$
card(3\cap 5\cap 7) = \left\lfloor\dfrac{600}{3\cdot 5\cdot 7}\right\rfloor=5.
$$

Por consiguiente,

$$
card(\overline{3}\cap\overline{5}\cap\overline{7}) = 600 - (200 + 120 + 85 - 40 - 28 - 17 + 5) = 275,
$$

es decir, hay $275$ números entre $1$ y $600$, ambos inclusive, que no son divisibles por $3$, ni por $5$, ni por $7$.
