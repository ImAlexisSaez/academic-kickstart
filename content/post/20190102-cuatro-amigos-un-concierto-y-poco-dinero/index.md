---
title: "Cuatro amigos, un concierto y poco dinero"
slug: "cuatro-amigos-un-concierto-y-poco-dinero"
subtitle: "Problema 39"
summary: "Problema 39: otra aplicación del Teorema chino del resto."

date: 2019-01-02T05:59:39+02:00
lastmod: 2019-01-02T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Problemas", "Teorema chino del resto", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Denys Nevozhai](https://unsplash.com/@dnevozhai), disponible en [Unsplash](https://unsplash.com/photos/R8ROQhXfHH0)."
---

**Problema 39:** Ana, Belén, Carlos y David acuden, con bastante ilusión y mucha algarabía, a un concierto de *31Knots*; pero, en mitad de la cola, tras un rápido y certero cálculo de Ana, desgraciadamente se dan cuenta de que les faltan algunos euros para poder comprar las entradas, cuyo precio asciende a $50$ euros por tique.

Cada uno de ellos posee una cifra entera mayor o igual que cero de euros y, curiosamente, además

- si Belén le pide un euro a Ana, consigue acumular dos tercios de la cantidad que le quedaría a Ana;
- si Carlos toma prestados dos euros de Belén, llega a acumular tres quintos de la cantidad que le quedaría a Belén;
- si David le pide tres euros a Carlos, consigue acumular cinco séptimos de la cantidad que le quedaría a Carlos.

¿Cuál es la mínima cantidad de euros que necesitarían entre todos para poder así permitirse la adquisición de las cuatro entradas?

***

Por comodidad en la escritura, denotemos el dinero que posee cada uno, en euros, de los cuatro protagonistas del enunciado del ejercicio por sus iniciales en minúscula, esto es, $a$, $b$, $c$ y $d$. Sabemos, dado que no pueden comprar las cuatro entradas para disfrutar del concierto, que $a+b+c+d<4\cdot50=200$. Hallemos cuánto dinero lleva encima cada uno de ellos haciendo uso de las condiciones que aparecen, que, matemáticamente, podemos expresar como sigue:

$$
\begin{aligned}
b+1 &= \dfrac{2}{3}(a-1),\\\\ c+2 &= \dfrac{3}{5}(b-2),\\\\ d+3 &= \dfrac{5}{7}(c-3).
\end{aligned}
$$

Despejando $b$, $c$ y $d$, encontramos que

$$
\begin{aligned}
b&=\dfrac{2a-5}{3},\\\\ c&=\dfrac{3b-16}{5},\\\\ d&=\dfrac{5c-36}{7},
\end{aligned}
$$

que, expresadas todas ellas en función del valor de $a$, equivalen a

$$
\begin{aligned}
b&=\dfrac{2a-5}{3},\\\\ c&=\dfrac{3b-16}{5} = \dfrac{3\cdot\dfrac{2a-5}{3} - 16}{5}=\dfrac{2a-21}{5},\\\\ d&=\dfrac{5c-36}{7} = \dfrac{5\cdot\dfrac{2a-21}{5} - 36}{7} = \dfrac{2a-57}{7}.
\end{aligned}
$$

Recordemos ahora que $b$, $c$ y $d$ llevan encima una cantidad entera mayor o igual que cero de euros, hecho que se traduce en que

$$
\begin{aligned}
(2a-5)&\equiv 0\pmod{3},\\\\ (2a-21)&\equiv 0\pmod{5},\\\\ (2a-57)&\equiv 0\pmod{7}.
\end{aligned}
$$

Llegados a este momento, comenzamos a sospechar que el camino nos lleva, irremediablemente, a buscar el valor de $a$ vía el *Teorema chino del resto*, por lo que, previamente, vamos a adaptar la forma del sistema de ecuaciones de congruencias lineales a la que figura en el resultado teórico. Así,

$$
\begin{aligned}
(2a-5)\equiv 0\pmod{3}&\Leftrightarrow 2a\equiv 5\pmod{3}\Leftrightarrow 4a\equiv 10\pmod{3}\\\\ &\Leftrightarrow a\equiv 1\pmod{3},\\\\ (2a-21)\equiv 0\pmod{5}&\Leftrightarrow 2a\equiv 1\pmod{5}\Leftrightarrow 6a\equiv 3\pmod{5}\\\\ &\Leftrightarrow a\equiv 3\pmod{5},\\\\ (2a-57)\equiv 0\pmod{7}&\Leftrightarrow 2a\equiv 1\pmod{7}\Leftrightarrow 8a\equiv 4\pmod{7}\\\\ &\Leftrightarrow a\equiv 4\pmod{7}.
\end{aligned}
$$

Esto es, recapitulando, la cantidad total de euros que lleva encima Ana (es decir, el valor de $a$), resulta ser la solución del siguiente sistema de ecuaciones de congruencias lineales

$$
\begin{aligned}
a&\equiv 1\pmod{3},\\\\ a&\equiv 3\pmod{5},\\\\ a&\equiv 4\pmod{7}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=3, m_2=5$ y $m_3=7$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=3\cdot5\cdot7 = 105$. Procedamos entonces al cálculo de las soluciones utilizando el método habitual. Así,

$$
\begin{aligned}
M_1 &= \dfrac{M}{m_1} = \dfrac{105}{3} = 5\cdot7 = 35,\\\\ M_2 &= \dfrac{M}{m_2} = \dfrac{105}{5} = 3\cdot7 = 21,\\\\ M_3 &= \dfrac{M}{m_3} = \dfrac{105}{7} = 3\cdot5 = 15,
\end{aligned}
$$

y, a continuación, resolvemos las siguientes ecuaciones de congruencia lineales:

$$
\begin{aligned}
35a\equiv 1\pmod{3}&\Leftrightarrow (-a)\equiv 1\pmod{3}\Leftrightarrow a\equiv 2\pmod{3},\\\\ 21a\equiv 1\pmod{5}&\Leftrightarrow a\equiv 1\pmod{5},\\\\ 15a\equiv 1\pmod{7}&\Leftrightarrow a\equiv 1\pmod{7}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
a&\equiv 1\pmod{3},& 35a&\equiv 1\pmod{3},& a&\equiv 2\pmod{3},\\\\ a&\equiv 3\pmod{5},& 21a&\equiv 1\pmod{5},& a&\equiv 1\pmod{5},\\\\ a&\equiv 4\pmod{7},& 15a&\equiv 1\pmod{7},& a&\equiv 1\pmod{7},
\end{aligned}
$$

entonces la solución es 

$$
\begin{aligned}
a &\equiv (1\cdot35\cdot2 + 3\cdot21\cdot1 + 4\cdot15\cdot1)\pmod{105}\\\\ &\equiv 193\pmod{105}\\\\ &\equiv 88\pmod{105},
\end{aligned}
$$

esto es, Ana lleva encima $88$ euros. Como $a=88$, entonces

$$
\begin{aligned}
b&=\dfrac{2\cdot88-5}{3} = 57,\\\\ c&=\dfrac{2\cdot88-21}{5} = 31,\\\\ d&=\dfrac{2\cdot88-57}{7} = 17,
\end{aligned}
$$

es decir, Belén, Carlos y David llevan encima, respectivamente, $57$, $31$ y $17$ euros. En total suman $88+57+31+17=193$ euros, por lo que les faltan $200-193=7$ euros para poder comprar las cuatro entradas y así disfrutar del concierto.

Alternativamente, volvamos al momento del ejercicio en el que declaramos que

$$
\begin{aligned}
b+1 &= \dfrac{2}{3}(a-1),\\\\ c+2 &= \dfrac{3}{5}(b-2),\\\\ d+3 &= \dfrac{5}{7}(c-3).
\end{aligned}
$$

Si operamos algebraicamente las ecuaciones

$$
\begin{aligned}
3b+3 &= 2a-2 \Rightarrow 3b-2a = -5,\\\\ 5c+10 &= 3b-6 \Rightarrow 5c-3b=-16,\\\\ 7d+21 &= 5c-15 \Rightarrow 7d-5c=-36,
\end{aligned}
$$

y sumamos ahora las tres, llegamos a la ecuación diofántica $7d-2a=-57$, que, despejando la variable $a$ por ser aquella cuyo coeficiente asociado es más reducido, se tiene que

$$
a = \dfrac{7d+57}{2}.
$$

Para $d=1$, encontramos que $a=32$, arribando así a la solución particular de dicha ecuación diofántica. Su solución general es pues

$$
\begin{aligned}
a &= 32 + 7t,\\\\ d &= 1 + 2t,
\end{aligned}
$$

con $t$ número entero. Sustituyendo estos resultados alcanzados en las ecuaciones de arriba, estamos en condiciones de encontrar las expresiones para $b$ y $c$. Así,

$$
\begin{aligned}
b &= \dfrac{-5 + 2(32+7t)}{3},\\\\ c &= \dfrac{36 + 7(1+2t)}{5}.
\end{aligned}
$$

Ahora bien, estamos interesados en el valor entero de $t$ que nos proporciona la mínima cantidad de euros que necesitarían entre todos para poder así permitirse la adquisición de las cuatro entradas (y con la restricción añadida implícita de que las soluciones han de ser enteras). Como inicialmente no disponen de la cantidad necesaria, ello implica que $a+b+c+d<200$, y, sustituyendo las anteriores expresiones alcanzadas para cada una de las cuatro variables, generamos la inecuación

$$
\begin{aligned}
32+7t+1+2t+\dfrac{-5 + 2(32+7t)}{3}+\dfrac{36 + 7(1+2t)}{5}&<200\\\\ 480+105t+15+30t-25+320+70t+108+21+42t&<3000,\\\\ 247t&<2081,
\end{aligned}
$$

esto es, $t<8.43$. Así pues, empezando por $t=8$ (y continuando con $t=7$, $t=6$, etc.), sustituiremos arriba, hasta dar con el primer valor que genere cifras enteras para $a$, $b$, $c$ y $d$. Por tanto, si $t=8$,

$$
\begin{aligned}
a &= 32+7\cdot8 = 88,\\\\ b &= \dfrac{-5 + 2(32+7\cdot8)}{3} = 57,\\\\ c &= \dfrac{36 + 7(1+2\cdot8)}{5} = 31,\\\\ d &= 1+2\cdot8 = 17,
\end{aligned}
$$

llegando, afortunadamente, en el primer intento a la solución alcanzada por el método de las congruencias.
