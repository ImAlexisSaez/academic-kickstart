---
title: "Repasando ecuaciones en diferencias lineales (II)"
slug: "repasando-ecuaciones-en-diferencias-lineales-ii"
subtitle: "Problema 13"
summary: "Problema 13: aparecen raíces complejas en el polinomio característico."

date: 2018-09-29T05:59:39+02:00
lastmod: 2019-07-27T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Ecuaciones en diferencias", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía disponible en [Unsplash](https://unsplash.com/)."
---

**Problema 13:** Resuelve

- (a) $a_{n+3} - 3a_{n+2} + 4a_{n+1} - 12a_n = 0$.
- (b) $a_{n+4} + 2a_{n+2} + a_n = 0$.

***

En el apartado (a), $a_{n+3} - 3a_{n+2} + 4a_{n+1} - 12a_n = 0$ es una ecuación en diferencias lineal homogénea de orden 3, que tiene por ecuación característica 

$$
\lambda^3 - 3\lambda^2 + 4\lambda - 12 = 0.
$$ 

Ahora bien, como $\lambda^3 - 3\lambda^2 + 4\lambda - 12 = (\lambda - 3)(\lambda - 2i)(\lambda + 2i)$, tenemos una raíz real simple y dos raíces complejas conjugadas simples, para las que $\varrho = 2$ y $\theta = \pi/2$, de manera que la solución queda 

$$
a_h(n) = c_13^n + 2^n\left(A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)}\right),
$$ 

con $c_1, A, B\in\mathbb{R}$.

A continuación, en el apartado (b), $a_{n+4} + 2a_{n+2} + a_n = 0$ es homogénea de orden 4, con ecuación característica 

$$
\lambda^4 + 2\lambda^2 + 1 = 0.
$$ 

Esta ecuación bicuadrada en $\lambda$ la podemos resolver mediante el cambio de variable $t = \lambda^2$, de forma que la ecuación queda como $t^2+2t+1=0$ y posee $t=-1$ como raíz real de multiplicidad $m=2$, es decir, 

$$
t^2+2t+1 = (t+1)^2.
$$

Así, si deshacemos ahora el cambio de variable, resulta que 

$$
\lambda^4 + 2\lambda^2 + 1 = (\lambda - i)^2(\lambda + i)^2,
$$

con lo cual tenemos dos raíces complejas conjugadas de multiplicidad $m=2$, para las que $\varrho=1$ y $\theta = \pi/2$, por lo que la solución queda

$$
\begin{aligned}
a_h(n) &= 1^n\left(
(An+B)cos{\left(\dfrac{\pi}{2}n\right)} + (Cn+D)\sin{\left(\dfrac{\pi}{2}n\right)}
\right)\\
&= (An+B)cos{\left(\dfrac{\pi}{2}n\right)} + (Cn+D)\sin{\left(\dfrac{\pi}{2}n\right)},
\end{aligned}
$$

con $A,B,C,D\in\mathbb{R}$.
