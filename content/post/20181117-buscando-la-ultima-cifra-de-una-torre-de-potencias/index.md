---
title: "Buscando la última cifra de una torre de potencias"
slug: "buscando-la-ultima-cifra-de-una-torre-de-potencias"
subtitle: "Problema 26"
summary: "Problema 26: qué hacer cuando no podemos recurrir a la artillería que proporciona Fermat."

date: 2018-11-17T05:59:39+02:00
lastmod: 2019-07-29T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Problemas", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Angel Santos](https://unsplash.com/@afs_snapshots), disponible en [Unsplash](https://unsplash.com/photos/LcCpvQhjJSM)."
---

**Problema 26:** Demuestra que la última cifra decimal de 

$$
2^{2^n} + 1
$$ 

es $7$, para cada $n\in\mathbb{N}$, con $n>1$.

***

Para hallar la cifra de las unidades del número 

$$
2^{2^n} + 1,
$$ 

un posible enfoque es estudiar el valor de la congruencia de dicho número módulo $10$. Ahora bien, como $10$ no es un número primo y $mcd(2, 10)=2$, no estamos en condiciones de aplicar ninguno de los resultados teóricos asociados a *Fermat*. Analicemos, pues, el comportamiento del valor de las congruencias de las potencias de $2$ módulo $10$,

$$
\begin{aligned}
2^1&\equiv 2\pmod{10},\\
2^2&\equiv 4\pmod{10},\\
2^3&\equiv 8\pmod{10},\\
2^4&\equiv 6\pmod{10}.
\end{aligned}
$$

A la vista de este último valor alcanzado, y teniendo en cuenta el resultado al que pretendemos arribar, bastaría comprobar que, para cada número natural, con $n>1$, $2^n$ es múltiplo de $4$. 

Por inducción, para $n=2$, $2^2=4$ que, efectivamente es múltiplo de $4$. Supongamos ahora cierta la afirmación para un número natural dado $n$, con $n\geq 2$, esto es, que existe un número entero $k$ de manera que $2^n=4k$. Sin embargo, $2^{n+1} = 2\cdot 2^n = 2\cdot(4k) = 4\cdot 2k$, es decir, la propiedad asimismo se satisface para $n+1$. El *Principio de inducción matemática* nos permite concluir que se verifica para cada número natural $n$, con $n\geq 2$.

Por tanto, al ser $2^n\equiv 0\pmod{4}$, entonces 

$$
2^{2^n}\equiv 6\pmod{10},
$$ 

hecho que se traduce en que 

$$
( 2^{2^n} + 1 )\equiv 7\pmod{10}
$$ 

o, equivalentemente, que, dadas las condiciones impuestas en el enunciado del ejercicio, la cifra de las unidades del número 

$$
2^{2^n} + 1
$$ 

es $7$.
