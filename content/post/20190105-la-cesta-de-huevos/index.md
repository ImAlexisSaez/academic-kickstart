+++
title = "La cesta de huevos de Brahmagupta"
slug  = "la-cesta-de-huevos-de-brahmagupta"
subtitle = "Problema 40"
summary  = "Problema 40: un problema clásico de teoría de números."

date     = 2019-01-05T05:59:39+02:00
#lastmod = 2019-04-05T10:15:24+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Problemas", "Teorema chino del resto", "Teoría de números"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Ben Klea](https://unsplash.com/@benkleaphoto), disponible en [Unsplash](https://unsplash.com/photos/QF8qP_pWMvs)."
+++

**Problema 40:** Brahmagupta tiene una enorme cesta repleta de huevos camperos. Si los saca de $2$ en $2$, resulta que queda un huevo en la cesta. Si opta por extraerlos de $3$ en $3$, ahora $2$ son los huevos que restan en la cesta. Análogamente, si realiza el proceso utilizando grupos de $4$, $5$ y $6$ huevos, quedan en la cesta, respectivamente, $3$, $4$ y $5$ huevos. Sin embargo, si los saca de $7$ en $7$, la cesta se vacía por completo. ¿Cuál es la menor cantidad de huevos que puede haber en la cesta de Brahmagupta?

***

Consideremos $x$ el número de huevos que se encuentran en la cesta de Brahmagupta. Los distintos modos de extracción dan lugar al siguiente sistema de ecuaciones de congruencias lineales,

$$
\begin{aligned}
x&\equiv 1\pmod{2},\\\\ x&\equiv 2\pmod{3},\\\\ x&\equiv 3\pmod{4},\\\\ x&\equiv 4\pmod{5},\\\\ x&\equiv 5\pmod{6},\\\\ x&\equiv 0\pmod{7}.
\end{aligned}
$$

Por desgracia, no podemos aplicar directamente el *Teorema chino del resto*, pues algunos módulos no son primos entre sí. No obstante, como estamos en las condiciones de la proposición que generaliza este resultado teórico (las comprobaciones sobre los pares de congruencias se pueden llevar a cabo mentalmente de forma sencilla), sabemos que el sistema de ecuaciones de congruencias lineales posee solución. Para hallarla, desdoblando la ecuación de congruencia lineal $x\equiv 5\pmod{6}$, queda

$$
\begin{aligned}
x&\equiv 1\pmod{2},\\\\ x&\equiv 2\pmod{3},\\\\ x&\equiv 3\pmod{4},\\\\ x&\equiv 4\pmod{5},\\\\ x&\equiv 5\pmod{2}\equiv 1\pmod{2},\\\\ x&\equiv 5\pmod{3}\equiv 2\pmod{3},\\\\ x&\equiv 0\pmod{7}.
\end{aligned}
$$

Encontramos dos ecuaciones de congruencias lineales repetidas, cuya escritura podemos ahorrarnos, de manera que llegamos a que

$$
\begin{aligned}
x&\equiv 1\pmod{2},\\\\ x&\equiv 2\pmod{3},\\\\ x&\equiv 3\pmod{4},\\\\ x&\equiv 4\pmod{5},\\\\ x&\equiv 0\pmod{7}.
\end{aligned}
$$

Llegados a este punto, la primera y la tercera ecuación involucran módulos de manera que uno es un factor del otro $4=2^2$. Por tanto, tenemos entre manos una posible contradicción aquí que hemos de investigar para hallar si existe o no dicha contradicción. No obstante, para cierto número entero $t$,

$$
x\equiv 3\pmod{4}\Rightarrow x = 3+4t\Rightarrow x = 1 + 2(1+2t)\Rightarrow x\equiv 1\pmod{2},
$$

luego la primera ecuación de congruencia lineal es redundante y la podremos suprimir del sistema, quedando pues

$$
\begin{aligned}
x&\equiv 2\pmod{3},\\\\ x&\equiv 3\pmod{4},\\\\ x&\equiv 4\pmod{5},\\\\ x&\equiv 0\pmod{7}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=3, m_2=4, m_3=5$ y $m_4=7$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=3\cdot4\cdot5\cdot7 = 420$. Procedamos entonces al cálculo de las soluciones utilizando el método habitual. Así,

$$
\begin{aligned}
M_1 &= \dfrac{M}{m_1} = \dfrac{420}{3} = 4\cdot5\cdot7 = 140,\\\\ M_2 &= \dfrac{M}{m_2} = \dfrac{420}{4} = 3\cdot5\cdot7 = 105,\\\\ M_3 &= \dfrac{M}{m_3} = \dfrac{420}{5} = 3\cdot4\cdot7 = 84,\\\\ M_4 &= \dfrac{M}{m_4} = \dfrac{420}{7} = 3\cdot4\cdot5 = 60,
\end{aligned}
$$

y, a continuación, resolvemos las siguientes ecuaciones de congruencia lineales:

$$
\begin{aligned}
140x\equiv 1\pmod{3}&\Leftrightarrow 2x\equiv 1\pmod{3}\Leftrightarrow 4x\equiv 2\pmod{3}\\\\ &\Leftrightarrow x\equiv 2\pmod{3},\\\\ 105x\equiv 1\pmod{4}&\Leftrightarrow x\equiv 1\pmod{4},\\\\ 84x\equiv 1\pmod{5}&\Leftrightarrow (-x)\equiv 1\pmod{5}\Leftrightarrow x\equiv 4\pmod{5},\\\\ 60x\equiv 1\pmod{7}&\Leftrightarrow 4x\equiv 1\pmod{7}\Leftrightarrow 8x\equiv 2\pmod{7}\\\\ &\Leftrightarrow x\equiv 2\pmod{7}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
x&\equiv 2\pmod{3},& 140x&\equiv 1\pmod{3},& x&\equiv 2\pmod{3},\\\\ x&\equiv 3\pmod{4},& 105x&\equiv 1\pmod{4},& x&\equiv 1\pmod{4},\\\\ x&\equiv 4\pmod{5},& 84x&\equiv 1\pmod{5},& x&\equiv 4\pmod{5},\\\\ x&\equiv 0\pmod{7},& 60x&\equiv 1\pmod{7},& x&\equiv 2\pmod{7},
\end{aligned}
$$

entonces la solución es 

$$
\begin{aligned}
x &\equiv (2\cdot140\cdot2 + 3\cdot105\cdot1 + 4\cdot84\cdot4 + 0\cdot60\cdot1)\pmod{420}\\\\ &\equiv 2219\pmod{420}\equiv 119\pmod{420},
\end{aligned}
$$

esto es, la cesta de Brahmagupta contaba con $119$ huevos.