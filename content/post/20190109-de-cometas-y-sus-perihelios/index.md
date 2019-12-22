---
title: "De cometas y sus perihelios"
slug: "de-cometas-y-sus-perihelios"
subtitle: "Problema 41"
summary: "Problema 41: un viaje por el espacio."

date: 2019-01-09T05:59:39+02:00
lastmod: 2019-01-09T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Problemas", "Teorema chino del resto", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Lauren Pandolfi](https://unsplash.com/@laurencpandolfi), disponible en [Unsplash](https://unsplash.com/photos/zD5ry8Up83M)."
---

**Problema 41:** Los cometas *2p/Encke*, *4P/Faye* y *8p/Tuttle* tienen períodos orbitales de $3$, $8$ y $13$ años, respectivamente. Los últimos perihelios (punto más cercano de la órbita de un cuerpo celeste alrededor del Sol) de cada uno de ellos fueron en $2017$, $2014$ y $2008$, respectivamente. ¿Cuál será el siguiente año en el cual coincidan sus perihelios? (Para este problema, asume que el tiempo se mide en años completos y que cada período orbital es constante.)

***

Sea $x$ el valor entero del siguiente año en el cual coinciden los perihelios. Como el cometa *2p/Encke* tiene una órbita de la forma $2017+3t$, con $t$ un número entero, entonces $x\equiv 2017\pmod{3}$. Análogamente, dado el cometa *4p/Faye* posee una órbita de la forma $2014+8u$, con $u$ número entero, entonces $x\equiv 2014\pmod{8}$. Finalmente, debido a que el cometa *8p/Tuttle* tiene una órbita de la forma $2008+13v$, con $v$ número entero, entonces $x\equiv 2008\pmod{13}$.

Así pues, hemos de resolver el siguiente sistema de ecuaciones de congruencias lineales,

$$
\begin{aligned}
x&\equiv 2017\pmod{3}\equiv 1\pmod{3},\\\\ x&\equiv 2014\pmod{8}\equiv 6\pmod{8}\\\\ x&\equiv 2008\pmod{13}\equiv 6\pmod{13}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=3$, $m_2=8$ y $m_3=13$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=3\cdot8\cdot13 = 312$. Procedamos entonces al cálculo de las soluciones utilizando el método habitual. Así,

$$
\begin{aligned}
M_1 &= \dfrac{M}{m_1} = \dfrac{312}{3} = 8\cdot13 = 104,\\\\ M_2 &= \dfrac{M}{m_2} = \dfrac{312}{8} = 3\cdot13 = 39,\\\\ M_3 &= \dfrac{M}{m_3} = \dfrac{312}{13} = 3\cdot8 = 24,
\end{aligned}
$$

y, a continuación, resolvemos las siguientes ecuaciones de congruencia lineales:

$$
\begin{aligned}
104x\equiv 1\pmod{3}&\Leftrightarrow 2x\equiv 1\pmod{3}\\\\ &\Leftrightarrow x\equiv 2\pmod{3},\\\\ 39x\equiv 1\pmod{8}&\Leftrightarrow (-x)\equiv 1\pmod{8}\\\\ &\Leftrightarrow x\equiv (-1)\pmod{8},\\\\ 24x\equiv 1\pmod{13}&\Leftrightarrow (-2x)\equiv 1\pmod{13}\\\\ &\Leftrightarrow (-12x)\equiv 6\pmod{13}\\\\ &\Leftrightarrow x\equiv 6\pmod{13}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
x&\equiv 1\pmod{3},& 104x&\equiv 1\pmod{3},& x&\equiv 2\pmod{3},\\\\ x&\equiv 6\pmod{8},& 39x&\equiv 1\pmod{8},& x&\equiv (-1)\pmod{8},\\\\ x&\equiv 6\pmod{13},& 24x&\equiv 1\pmod{13},& x&\equiv 6\pmod{13},
\end{aligned}
$$

entonces la solución es 

$$
\begin{aligned}
x &\equiv (1\cdot104\cdot2 + 6\cdot39\cdot(-1) + 6\cdot24\cdot1)\pmod{312}\\\\ &\equiv 838\pmod{312}\equiv 214\pmod{312},
\end{aligned}
$$

esto es, en los años de la forma $214+316w$, con $w$ número entero, coinciden los tres perihelios. Para $w=5$, encontramos que el año $1794$ fue el último en el que coincidieron, mientras que si $w=6$, hallamos que $2086$ será el próximo año en el que coincidan.
