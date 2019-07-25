---
title: "Múltiplos de 21 en Ceuta (versión congruencias)"
slug: "multiplos-de-21-en-ceuta-version-congruencias"
subtitle: "Problema 10"
summary: "Problema 10: siempre hay varias estrategias para abordar un mismo problema."

date: 2018-09-15T05:59:39+02:00
lastmod: 2019-07-25T00:00:01+02:00

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
  caption: "Fotografía de [Raphaël LR](https://unsplash.com/@raphaelrng), disponible en [Unsplash](https://unsplash.com/photos/wRZE35mwNak)."
---

**Problema 10:** Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$, $$4^{n+1} + 5^{2n-1}$$ es un múltiplo de 21.
<!--more-->

***

Aunque ya planteamos, hace un par de días, la resolución de este enunciado empleando el *principio de inducción matemática* en el [Problema 9](/2018/09/13/multiplos-de-21-en-ceuta/), vamos a darle aquí un enfoque alternativo a dicha resolución utilizando la teoría de congruencias.

Para empezar, para cada $n\in\mathbb{N}$, $4^{n+1} + 5^{2n-1}$ es un entero mayor o igual que 21 y será múltiplo de este último siempre que 

$$
4^{n+1} + 5^{2n-1}\equiv 0 \pmod{21}.
$$

Ahora bien, como $21=3\cdot 7$ y $mcd(3,7)=1$, demostrar la expresión anterior equivale a probar que las expresiones

$$
4^{n+1} + 5^{2n-1}\equiv 0 \pmod{3}
$$

y

$$
4^{n+1} + 5^{2n-1}\equiv 0 \pmod{7},
$$

se satisfacen conjuntamente, ya que sabemos, por las propiedades de las congruencias, que dados $n,m\in\mathbb{N}$ fijos y $a,b\in\mathbb{Z}$, si $a\equiv b \pmod{n}$, $a\equiv b \pmod{m}$ y $mcd(n,m)=1$, entonces $a\equiv b \pmod{nm}$.

Así pues, dado que $4\equiv 1 \pmod{3}$ y $5\equiv (-1) \pmod{3}$, entonces, para cada $n\in\mathbb{N}$,

$$
\begin{aligned}
4^{n+1}+5^{2n-1} &\equiv (1^{n+1} + (-1)^{2n-1}) \pmod{3}\\
&\equiv (1-1) \pmod{3}\\
&\equiv 0 \pmod{3},
\end{aligned}
$$

quedando así una demostrada. Para verificar la restante tengamos en cuenta que $5\equiv (-2) \pmod{7}$ y así, para cada $n\in\mathbb{N}$,

$$
\begin{aligned}
4^{n+1} + 5^{2n-1} &= 2^{2(n+1)} + 5^{2n-1}\\
&= 2^{2n+2} + 5^{2n-1}\\
&= 2^32^{2n-1} + 5^{2n-1}\\
&\equiv (2^32^{2n-1} + (-2)^{2n-1}) \pmod{7}\\
&\equiv (2^32^{2n-1} + (-1)^{2n-1}2^{2n-1}) \pmod{7}\\
&\equiv (2^32^{2n-1} - 2^{2n-1}) \pmod{7}\\
&\equiv ((2^3-1)2^{2n-1}) \pmod{7}\\
&\equiv 7\cdot 2^{2n-1} \pmod{7}\\
&\equiv 0 \pmod{7}.
\end{aligned}
$$

Por tanto, podemos concluir que, para cada $n\in\mathbb{N}$, $4^{n+1} + 5^{2n-1}$ es un múltiplo de 21.
