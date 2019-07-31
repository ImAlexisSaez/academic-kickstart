---
title: "Tiempo de generalizar problemas al año 2019"
slug: "tiempo-de-generalizar-problemas-al-anno-2019"
subtitle: "Problema 42"
summary: "Problema 42: extendiendo un problema clásico para que coincida con el año de las oposiciones."

date: 2019-01-12T05:59:39+02:00
lastmod: 2019-07-31T00:00:01+02:00

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
  caption: "Fotografía de [Andre Benz](https://unsplash.com/@trapnation), disponible en [Unsplash](https://unsplash.com/photos/e4xOmzd8vzg)."
---

**Problema 42:** Encuentra los tres últimos dígitos del número 

$$
N=3\times7\times11\times15\times\cdots\times2019.
$$

***

Como estamos interesados en encontrar los tres últimos dígitos del producto de números dado, un posible enfoque de cara a la resolución de este ejercicio es encontrar el valor de la congruencia de dicho producto módulo $1000$, esto es, resolver $x\equiv N\pmod{1000}$. Ahora bien, como $1000 = 2^3 \cdot 5^3 = 8\cdot 125$ y $mcd(8,125)=1$ sabemos, por el *Teorema chino del resto*, que la anterior ecuación de congruencia lineal es equivalente al siguiente sistema de ecuaciones de congruencias lineales,

$$
\begin{aligned}
x&\equiv N\pmod{8},\\
x&\equiv N\pmod{125}.
\end{aligned}
$$

Sin embargo, dado que en el producto $N$ aparecen, por ejemplo, los números $15 = 3\cdot5$, $35 = 5\cdot7$ y $55 = 5\cdot11$, resulta que encontraríamos $5^3$ en dicho producto, provocando que $N\equiv 0\pmod{125}$, esto es, $N$ es múltiplo de $125$. Por otro lado,

$$
\begin{aligned}
3&\equiv 3\pmod{8},\\
7&\equiv (-1)\pmod{8},\\
11&\equiv 3\pmod{8},\\
15&\equiv (-1)\pmod{8},
\end{aligned}
$$

por tanto 

$$
\begin{aligned}
(3\cdot7\cdot11\cdot15)&\equiv (3\cdot(-1)\cdot3\cdot(-1))\pmod{8}\\
&\equiv 9\pmod{8}\equiv 1\pmod{8}.
\end{aligned}
$$

Al ser los términos del producto $N$ de la forma $3+4t$, con $t$ número entero mayor o igual que cero, la anterior situación se reproduce cada cuatro términos del mencionado producto. Así, como $3+4t=2019$ implica que $t=504$ y empezamos la sucesión en $t=0$, $N$ está compuesto por $505$ términos, de forma que podemos conseguir $126$ grupos de $4$ elementos, quedando sin agrupar el último término, $2019$, que sabemos cumple $2019\equiv 3\pmod{8}$, por lo que

$$
N\equiv (1^{126} \cdot3)\pmod{8}\equiv 3\pmod{8}.
$$

Recapitulando, buscamos un múltiplo de $125$ que sea congruente con $3$ módulo $8$, es decir, hemos de resolver la ecuación, $125x\equiv 3\pmod{8}$. No obstante,

$$
\begin{aligned}
125x\equiv 3\pmod{8}&\Leftrightarrow 5x\equiv 3\pmod{8}\\
&\Leftrightarrow 15x\equiv 9\pmod{8}\\
&\Leftrightarrow (-x)\equiv 1\pmod{8}\\
&\Leftrightarrow x\equiv 7\pmod{8},
\end{aligned}
$$

esto es, $125\cdot7=875$ son las tres últimas cifras de $N$.

De manera más clásica, una vez hallado el valor de las anteriores dos congruencias, el sistema de ecuaciones de congruencias lineales propuesto es equivalente a

$$
\begin{aligned}
x&\equiv 3\pmod{8},\\
x&\equiv 0\pmod{125}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=8$ y $m_2=125$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=8\cdot125 = 1000$. Procedamos entonces al cálculo de las soluciones utilizando el método habitual. Así,

$$
\begin{aligned}
M_1 &= \dfrac{M}{m_1} = \dfrac{1000}{8} = 125,\\
M_2 &= \dfrac{M}{m_2} = \dfrac{1000}{125} = 4,
\end{aligned}
$$

y, a continuación, resolvemos las siguientes ecuaciones de congruencia lineales:

$$
\begin{aligned}
125x\equiv 1\pmod{8}&\Leftrightarrow 5x\equiv 1\pmod{8}\\
&\Leftrightarrow 25x\equiv 5\pmod{8}\\
&\Leftrightarrow x\equiv 5\pmod{8},\\
4x\equiv 1\pmod{125}&\Leftrightarrow 376x\equiv 94\pmod{125}\\
&\Leftrightarrow x\equiv 94\pmod{125}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
x&\equiv 3\pmod{8},& 125x&\equiv 1\pmod{8},& x&\equiv 5\pmod{8},\\
x&\equiv 0\pmod{125},& 4x&\equiv 1\pmod{125},& x&\equiv 94\pmod{125},
\end{aligned}
$$

entonces la solución es 

$$
\begin{aligned}
x &\equiv (3\cdot125\cdot5 + 0\cdot4\cdot94)\pmod{1000}\\
&\equiv 1875\pmod{1000}\\
&\equiv 875\pmod{1000},
\end{aligned}
$$

esto es, $875$ son los tres últimos dígitos de $N$.
