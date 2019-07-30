---
title: "Contando soldados de una manera curiosa"
slug: "contando-soldados-de-una-manera-curiosa"
subtitle: "Problema 38"
summary: "Problema 38: estoy seguro de que por menos ha habido motines."

date: 2018-12-29T05:59:39+02:00
lastmod: 2019-07-30T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Problemas", "Teorema chino del resto", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Ishan @seefromthesky](https://unsplash.com/@seefromthesky), disponible en [Unsplash](https://unsplash.com/photos/GSZQ_eupukE)."
---

**Problema 38:** Un general cuenta el número de soldados supervivientes de una batalla alineándolos, sucesivamente, en filas de diferentes tamaños. En cada ocasión, anota el total que quedaron sin poder completar una fila. Disponía de $1200$ combatientes antes de la refriega. Tras el encuentro si los alineaba en filas de $5$, quedaban $3$ sin poder completar una fila; si lo hacía en filas de $6$, volvían a quedar $3$ sin poder completar una fila; si los repartía en filas de $7$, únicamente uno quedaba fuera de las filas y si los alineaba en filas de $11$, no quedaba soldado alguno que no estuviese en una fila ¿Cuántos soldados sobrevivieron la batalla?

***

Consideremos $x$ el número de soldados supervivientes de la batalla, cantidad que sabemos es menor o igual que $1200$ por ser este el número de los que disponía el general inicialmente, es decir, $0\leq x\leq 1200$.

Las sucesivas alineaciones de los soldados, las traducimos en el siguiente sistema de congruencias lineales,

$$
\begin{aligned}
x&\equiv 3\pmod{5},\\
x&\equiv 3\pmod{6},\\
x&\equiv 1\pmod{7},\\
x&\equiv 0\pmod{11}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=5$, $m_2=6$, $m_3=7$ y $m_4=11$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=5\cdot6\cdot7\cdot11 = 2310$. Procedamos entonces al cálculo de las soluciones utilizando el método habitual. Así,

$$
\begin{aligned}
M_1 &= \dfrac{M}{m_1} = \dfrac{2310}{5} = 6\cdot7\cdot11 = 462,\\
M_2 &= \dfrac{M}{m_2} = \dfrac{2310}{6} = 5\cdot7\cdot11 = 385,\\
M_3 &= \dfrac{M}{m_3} = \dfrac{2310}{7} = 5\cdot6\cdot11 = 330,\\
M_4 &= \dfrac{M}{m_4} = \dfrac{2310}{11} = 5\cdot6\cdot7 = 210,
\end{aligned}
$$

y, a continuación, resolvemos las siguientes ecuaciones de congruencia lineales:

$$
\begin{aligned}
462x\equiv 1\pmod{5}&\Leftrightarrow 2x\equiv 1\pmod{5}\Leftrightarrow 6x\equiv 3\pmod{5}\Leftrightarrow x\equiv 3\pmod{5},\\
385x\equiv 1\pmod{6}&\Leftrightarrow x\equiv 1\pmod{6},\\
330x\equiv 1\pmod{7}&\Leftrightarrow x\equiv 1\pmod{7},\\
210x\equiv 1\pmod{11}&\Leftrightarrow x\equiv 1\pmod{11}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
x&\equiv 3\pmod{5},& 462x&\equiv 1\pmod{5},& x&\equiv 3\pmod{5},\\
x&\equiv 3\pmod{6},& 385x&\equiv 1\pmod{6},& x&\equiv 1\pmod{6},\\
x&\equiv 1\pmod{7},& 330x&\equiv 1\pmod{7},& x&\equiv 1\pmod{7},\\
x&\equiv 0\pmod{11},& 210x&\equiv 1\pmod{11},& x&\equiv 1\pmod{11},
\end{aligned}
$$

entonces la solución es 

$$
\begin{aligned}
x &\equiv (3\cdot462\cdot3 + 3\cdot385\cdot1 + 1\cdot330\cdot1 + 0\cdot210\cdot1)\pmod{2310}\\
&\equiv 5643\pmod{2310}\equiv 1023\pmod{2310},
\end{aligned}
$$

esto es, asciende a $1023$ el número de soldados que sobrevivieron a la batalla.
