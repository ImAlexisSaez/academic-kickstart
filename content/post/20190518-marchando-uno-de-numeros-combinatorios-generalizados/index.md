---
title: "Marchando uno de números combinatorios generalizados"
slug: "marchando-uno-de-numeros-combinatorios-generalizados"
subtitle: "Problema 78"
summary: "Problema 78: números combinatorios... ¿con valores negativos?"

date: 2019-05-18T05:59:39+02:00
lastmod: 2019-05-18T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Combinatoria", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Michael Hacker](https://unsplash.com/@michael_hacker), disponible en [Unsplash](https://unsplash.com/photos/OM5Zy3_7pGU)."
---

**Problema 78:** Demuestra que, para cada número natural $n$,

$$
\dbinom{-1 / 2}{n} = \dbinom{2n}{n}\left(-\dfrac{1}{4}\right)^n.
$$

***

Utilizando la definición,

$$
\begin{aligned}
\dbinom{-1 / 2}{n} &= \dfrac{\left(-\dfrac{1}{2}\right)\left(-\dfrac{1}{2}-1\right)\left(-\dfrac{1}{2}-2\right)\cdots\left(-\dfrac{1}{2} - (n-1)\right)}{n!}\\\\ &= \dfrac{\left(-\dfrac{1}{2}\right)\left(-\dfrac{3}{2}\right)\left(-\dfrac{5}{2}\right)\cdots\left(\dfrac{1-2n}{2}\right)}{n!}.
\end{aligned}
$$

En el numerador encontramos $n$ factores, por lo que podremos extraer esa misma cantidad de signos negativos, quedando entonces $(-1)^n$ (atención a cómo quedaría el último factor tras esta acción). Además, hay $n$ doses en los denominadores de las fracciones que aparecen en el numerador, quedando su producto entonces $2^n$, valor que podemos trasladar al denominador de la expresión. Por consiguiente,

$$
\dbinom{-1 / 2}{n} = (-1)^n \cdot\dfrac{1\cdot3\cdot5\cdots (2n-1)}{2^n n!}.
$$

Ahora, multipliquemos y dividamos por el producto de números pares $2\cdot4\cdot6\cdots 2n$ (llegamos a $2n$ y no hasta $2n-2$ por la expresión a la que buscamos arribar), provocando así que en el numerador aparezca el factorial de $2n$,

$$
\begin{aligned}
\dbinom{-1 / 2}{n} &= (-1)^n\dfrac{1\cdot2\cdot3\cdot4\cdot5\cdots (2n-1)\cdot 2n}{(2\cdot4\cdot6\cdots 2n) 2^n n!}\\\\ &= (-1)^n\dfrac{(2n)!}{(2\cdot4\cdot6\cdots 2n) 2^n n!}.
\end{aligned}
$$

Además, sacando un dos de cada factor, y teniendo en cuenta que hay $n$ de ellos, es cierto que,

$$
2\cdot4\cdot6\cdots 2n = 2^n(1\cdot2\cdot3\cdots n) = 2^n n!,
$$

y sustituyendo el resultado alcanzado en la expresión anterior,

$$
\dbinom{-1 / 2}{n} = (-1)^n\dfrac{(2n)!}{(2^n n!) (2^n n!)}.
$$

Como $2^n\cdot 2^n = 2^{2n} = 4^n$, 

$$
\dbinom{-1 / 2}{n} = (-1)^n\dfrac{(2n)!}{4^n n! n!} = \dfrac{(-1)^n}{4^n}\dbinom{2n}{n} = \dbinom{2n}{n}\left(-\dfrac{1}{4}\right)^n ,
$$

tal y como queríamos demostrar.
