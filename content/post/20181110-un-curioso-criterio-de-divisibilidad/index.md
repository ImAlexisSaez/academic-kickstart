---
title: "Un curioso criterio de divisibilidad"
slug: "un-curioso-criterio-de-divisibilidad"
subtitle: "Problema 24"
summary: "Problema 24: trabajando con múltiplos de 1000."

date: 2018-11-10T05:59:39+02:00
lastmod: 2019-07-28T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Criterios de divisibilidad", "Problemas", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Mario Gogh](https://unsplash.com/@mariogogh), disponible en [Unsplash](https://unsplash.com/photos/v3aFku0VPDI)."
---

**Problema 24:** Escribe los divisores de $1001$. Considera ahora 

$$
N = a_0 + a_1t + \cdots + a_nt^n
$$ 

y 

$$
S = a_0-a_1+a_2-\cdots+(-1)^na_n,
$$

donde $t=1000$ y $a_n\in\mathbb{Z}$ y demuestra que $N\equiv S\pmod{1001}$. Deduce de ello un criterio de divisibilidad por $7$, $11$ o $13$ y aplícalo al número $312879645$.

***

Como $1001 = 7\cdot11\cdot13$, el conjunto de divisores del número $1001$ es 

$$
\{1,7,11,13,77,91,143,1001\}.
$$

A continuación, si consideramos $t=1000$, como 

$$
t\equiv (-1)\pmod{1001},
$$ 

entonces se cumple que $t^2\equiv (-1)^2\pmod{1001}\equiv 1\pmod{1001}$ y, en general, $t^n\equiv (-1)^n\pmod{1001}$, para cada $n\in\mathbb{N}$. Este hecho nos permite concluir que

$$
\begin{aligned}
N &= a_0 + a_1t + \cdots + a_nt^n \\
&\equiv (a_0-a_1+a_2-\cdots+(-1)^na_n)\pmod{1001},
\end{aligned}
$$

es decir, $N\equiv S\pmod{1001}$, tal y como se nos pedía demostrar. 

Ahora bien, que $N$ sea congruente con $S$ módulo $1001$ implica que existe un $k\in\mathbb{Z}$ de manera que podemos escribir $N = 1001k+S$. Por tanto, dado que $1001=7\cdot11\cdot13$, el número $N$ será divisible por $7$, $11$ o $13$, siempre y cuando $S$ sea divisible por $7$, $11$ o $13$ (por aplicación directa de las propiedades de las congruencias), quedando así establecido el criterio de divisibilidad solicitado.

Finalmente, si tomamos $N=312879645$, es cierto que lo podemos expresar como 

$$
N = 645 + 879\cdot1000 + 312\cdot1000^2,
$$ 

por lo que $a_0 = 645$, $a_1=879$ y $a_2=312$. Esto provoca que 

$$
S = 645 - 879 + 312 = 78 = 13\cdot 6,
$$ 

y como $S$ es divisible por $13$ concluimos, por lo anterior, que $N$ es asimismo divisible por $13$. Alternativamente, podríamos decir que como $7\nmid S$, entonces $7\nmid N$ y, análogamente, como $11\nmid S$, entonces $11\nmid N$, quedando así únicamente concluir como arriba que como $13|S$, entonces $13|N$.

Por ejemplo, si consideramos ahora $N=178178$, su expresión en esta base $1000$ que introduce el presente ejercicio es $N = 178 + 178\cdot 1000$, quedando entonces $a_0=178$, $a_1=178$ y, por consiguiente, $S = 178-178 = 0$. Ahora bien, como $7|0$, entonces $7|N$ y, de forma similar, como $11|0$ y $13|0$, entonces $11|N$ y $13|N$. Añadiendo ahora un tres delante de $N$, es decir, $N=3178178$, tenemos $N = 178 + 178\cdot1000 + 3\cdot1000^2$, con $a_0=178$, $a_1=178$, $a_2=3$ y $S=3$. Como $7\nmid 3$, $11\nmid 3$ ni $13\nmid 3$, entonces concluimos que este último número no es divisible por $7$, $11$ ni $13$.
