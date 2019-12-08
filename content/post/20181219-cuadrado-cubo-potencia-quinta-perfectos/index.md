---
title: "Cuadrado perfecto, cubo perfecto, potencia quinta perfecta..."
slug: "cuadrado-perfecto-cubo-perfecto-potencia-quinta-perfecta"
subtitle: "Problema 35"
summary: "Problema 35: jugando con las factorizaciones."

date: 2018-12-19T05:59:39+02:00
lastmod: 2019-07-30T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Problemas", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [John Westrock](https://unsplash.com/@johnwestrock), disponible en [Unsplash](https://unsplash.com/photos/FLdNfW3fshc)."
---

**Problema 35:** Encuentra el menor número natural $n$ tal que $n / 2$ es cuadrado perfecto, $n / 3$ es cubo perfecto y $n / 5$ es potencia quinta perfecta.

***

Dado que podemos dividir $n$ por $2$, $3$ y $5$ y el resultado de dichas operaciones continúa siendo un número natural (porque se trata, respectivamente de cuadrado, cubo y potencia quinta perfectos), ello implica que en su descomposición en factores primos aparecerán los términos $2^x$, $3^y$ y $5^z$, con $x, y, z\geq 1$. En ejercicios anteriores también considerábamos la posibilidad de un término entero $k$ que agrupaba potencias de números primos distintos a los tres mencionados anteriormente, pero, en esta ocasión, como nuestro objetivo es hallar el menor natural $n$ que satisface las condiciones del enunciado del ejercicio, asumiremos que $k=1$. Así, $n=2^x 3^y 5^z$.

Ahora bien, como $n / 2 = 2^{x-1} 3^y 5^z$ es un cuadrado perfecto, los exponentes de la factorización dada serán múltiplos de dos ($x-1=\dot{2}$, $y=\dot{2}$, $z=\dot{2}$). Al ser $n / 3 = 2^x 3^{y-1} 5^z$ un cubo perfecto, los exponentes anteriores serán múltiplos de $3$ ($x=\dot{3}$, $y-1=\dot{3}$, $z=\dot{3}$). Finalmente, como $n / 5 = 2^x 3^y 5^{z-1}$ es una potencia quinta perfecta, los exponentes previos serán múltiplos de $5$ ($x=\dot{5}$, $y=\dot{5}$, $z-1=\dot{5}$).

Así pues, para $x$ surge el siguiente sistema de congruencias lineales

$$
\begin{aligned}
x-1&\equiv 0\pmod{2},\\
x&\equiv 0\pmod{3},\\
x&\equiv 0\pmod{5},
\end{aligned}
$$

que podemos resolver utilizando el *Teorema chino del resto*, aunque por tanteo es sencillo en este caso hallar la solución. Al ser múltiplo de $3$ y $5$, lo será de $15$. Entre los múltiplos de este último, hemos de buscar aquel que al restarle una unidad el resultado sea múltiplo de $2$. Son candidatos $15,45,75,\ldots$, pero como estamos interesados en encontrar el menor natural $n$, escogemos como solución final $x=15$.

Análogamente, para $y$ aparece el siguiente sistema de congruencias lineales

$$
\begin{aligned}
y&\equiv 0\pmod{2},\\
y-1&\equiv 0\pmod{3},\\
y&\equiv 0\pmod{5},
\end{aligned}
$$

que podemos resolver utilizando el *Teorema chino del resto*, aunque por tanteo es sencillo en este caso hallar la solución. Al ser múltiplo de $2$ y $5$, lo será de $10$. Entre los múltiplos de este último, hemos de buscar aquel que al restarle una unidad el resultado sea múltiplo de $3$. Son candidatos $10,40,70,\ldots$, pero como estamos interesados en encontrar el menor natural $n$, escogemos como solución final $y=10$.

Finalmente, para $z$ encontramos el siguiente sistema de congruencias lineales

$$
\begin{aligned}
z&\equiv 0\pmod{2},\\
z&\equiv 0\pmod{3},\\
z-1&\equiv 0\pmod{5},
\end{aligned}
$$

que podemos resolver utilizando el *Teorema chino del resto*, aunque por tanteo es sencillo en este caso hallar la solución. Al ser múltiplo de $2$ y $3$, lo será de $6$. Entre los múltiplos de este último, hemos de buscar aquel que al restarle una unidad el resultado sea múltiplo de $5$. Son candidatos $6,36,66,\ldots$, pero como estamos interesados en encontrar el menor natural $n$, escogemos como solución final $z=6$.

Por tanto, el menor número natural $n$ tal que $n/2$ es cuadrado perfecto, $n/3$ es cubo perfecto y $n/5$ es potencia quinta perfecta es $n=2^{15} \cdot 3^{10} \cdot 5^6$.
