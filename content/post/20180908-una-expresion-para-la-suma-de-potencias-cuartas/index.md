---
title: "Una expresión para la suma de potencias cuartas"
slug: "una-expresion-para-la-suma-de-potencias-cuartas"
subtitle: "Problema 7"
summary: "Problema 7: a veces, no queda otra que arremangarse las mangas y calcular."

date: 2018-09-08T05:59:39+02:00
lastmod: 2019-07-25T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Inducción", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía disponible en [Unsplash](https://unsplash.com/)."
---

**Problema 7:** Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$, 

$$
1^4+2^4+\cdots+n^4=\dfrac{n(n+1)(6n^3+9n^2+n-1)}{30}.
$$

***

Vaya por delante que estamos ante uno de esos problemas que rápidamente se ganan el apelativo de tediosos, no tanto por su dificultad, sino por el elevado número de operaciones algebraicas que debemos llevar a cabo durante el proceso de su resolución. 

Cuando en una propiedad a verificar aparecen involucrados polinomios de grado considerable, la segunda parte del *principio de inducción matemática* conlleva el desarrollo de múltiples binomios de la forma $(n+1)^m$, con $m\in\mathbb{N}$. Para reducir un tanto el tedio, siempre es aconsejable que, en primer lugar, factoricemos los mencionados polinomios.

Como nota curiosa, consultados diferentes recursos didácticos, la fórmula para la suma de las potencias cuartas de los $n$ primeros números naturales suele venir dada por 

$$
1^4 + 2^4 + \cdots + n^4=\dfrac{6n^5+15n^4+10n^3-n}{30},
$$ 

hecho que nos puede llevar a sospechar que la proporcionada en el enunciado del presente problema ya está completamente factorizada.

No obstante, como por naturaleza hemos de ser recelosos, utilicemos el *Teorema de la raíz racional* para investigar si podemos escribir el polinomio $6n^3 + 9n^2 + n - 1$ de una manera que nos resulte más cómoda de cara a futuras operaciones con él. Recordemos que, dada una ecuación polinómica con coeficientes enteros 

$$
a_mn^m + a_{m-1}n^{m-1} + \cdots + a_0=0,
$$ 

si $a_0$ y $a_m$ son enteros distintos de cero, entonces las posibles soluciones que son del tipo $n = p/q$ satisfacen:

- $p$ es divisor de $a_0$.
- $q$ es divisor de $a_m$.
- $p$ y $q$ son primos entre sí.

En nuestro problema, el conjunto de candidatos para $p$ es $\\{\pm1\\}$, mientras que para $q$ es $\\{\pm1,\pm2,\pm3,\pm6\\}$ y rápidamente podemos comprobar que $n = -1 / 2$ es solución del polinomio dado. Así, 

$$
6n^3 + 9n^2 + n - 1 = (2n + 1)(3n^2 + 3n - 1),
$$ 

de manera que

$$
\begin{aligned}
\sum_{k=1}^{n}{k^4} &= 1^4+2^4+\cdots+n^4\\
&= \dfrac{n(n+1)(6n^3+9n^2+n-1)}{30}\\
&=\dfrac{n(n+1)(2n+1)(3n^2+3n-1)}{30}.
\end{aligned}
$$

Una vez hemos alcanzado una expresión irreducible para el polinomio que figura en el numerador de la identidad anterior, utilizamos el *principio de inducción matemática*, dado en el teorema 1.1 (ver abajo), para comprobar dicha igualdad. Enseguida observamos que se satisface de manera trivial para $n=1$, puesto que

$$
1 = 1^4 = \dfrac{1\cdot2\cdot3\cdot5}{30}=1.
$$

A continuación, suponemos verdadera la identidad para un cierto $n\in\mathbb{N}$, con $n\geq 1$, es decir, que efectivamente se verifica que

$$
\sum_{k=1}^{n}{k^4} = \dfrac{n(n+1)(2n+1)(3n^2+3n-1)}{30}
$$

y estudiamos si se satisface para $n+1$. Así pues, el objetivo que tenemos ahora entre manos es comprobar si

$$
\begin{aligned}
\sum_{k=1}^{n+1}{k^4} &= \dfrac{(n+1)(n+2)(2(n+1)+1)(3(n+1)^2+3(n+1)-1)}{30}\\
&= \dfrac{(n+1)(n+2)(2n+3)(3n^2+9n+5)}{30}.
\end{aligned}
$$

Apliquemos la *hipótesis de inducción* y llevemos a cabo algunas operaciones algebraicas elementales, de forma que

$$
\begin{aligned}
\sum_{k=1}^{n+1}{k^4} &= (n+1)^4 + \sum_{k=1}^{n}{k^4}\\
&= (n+1)^4 + \dfrac{n(n+1)(2n+1)(3n^2+3n-1)}{30}\\
&= \dfrac{30(n+1)^4 + n(n+1)(2n+1)(3n^2+3n-1)}{30}\\
&= \dfrac{(n+1)(30(n+1)^3+n(2n+1)(3n^2+3n-1))}{30}.
\end{aligned}
$$

Por tanto, el resultado quedaría probado siempre y cuando fuesen equivalentes las expresiones de los polinomios $(n+2)(2n+3)(3n^2+9n+5)$ y $30(n+1)^3 + n(2n+1)(3n^2+3n-1)$. Efectivamente, si desarrollamos

$$
\begin{aligned}
(n+2)(2n+3) &= 2n^2+3n+4n+6 = 2n^2+7n+6,\\
(2n^2+7n+6)(3n^2+9n+5) &= 6n^4+39n^3+91n^2+89n+30,
\end{aligned}
$$

y, por otro lado,

$$
\begin{aligned}
30(n+1)^3 &= 30n^3 + 90n^2 + 90n + 30,\\
n(2n+1)(3n^2+3n-1) &= 6n^4+9n^3+n^2-n,
\end{aligned}
$$

de manera que la suma de estas dos últimas ecuaciones asciende a $6n^4 + 39n^3 + 91n^2 + 89n + 30,$ y, por tanto, la identidad se verifica para $n+1$. El *principio de inducción matemática* nos permite concluir que es cierta para cada $n\in\mathbb{N}$.

***

**Teorema 1.1 (Principio de inducción matemática)**: Sea $S$ un conjunto de enteros positivos que tienen las dos propiedades siguientes:

- El número 1 pertenece al conjunto $S$.
- Si un entero $k$ pertenece a $S$, también $k+1$ pertenece a S.

Entonces todo entero positivo pertenece al conjunto $S$.

***
