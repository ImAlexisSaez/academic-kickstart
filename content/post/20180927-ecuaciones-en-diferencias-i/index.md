---
title: "Repasando ecuaciones en diferencias lineales (I)"
slug: "repasando-ecuaciones-en-diferencias-lineales-i"
subtitle: "Problema 12"
summary: "Problema 12: ecuaciones en diferencias lineales homogéneas."

date: 2018-09-27T05:59:39+02:00
lastmod: 2019-07-27T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Ecuaciones en diferencias", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Mitchell Henderson](https://unsplash.com/@mtk402), disponible en [Unsplash](https://unsplash.com/photos/AvoUZ1bjuuU)."
---

**Problema 12:** Resuelve

- (a) $a_{n+3} - 3a_{n+2} - 4a_{n+1} + 12a_n = 0$.
- (b) $a_{n+3} - 4a_{n+2} + 5a_{n+1} - 2a_n = 0$.

***

En el apartado (a), encontramos la ecuación en diferencias lineal homogénea de orden 3 dada por $a_{n+3} - 3a_{n+2} - 4a_{n+1} + 12a_n = 0$, cuya ecuación característica asociada es 

$$
\lambda^3-3\lambda^2-4\lambda+12=0.
$$ 

Ahora bien, como $\lambda^3 - 3\lambda^2 - 4\lambda + 12 = (\lambda - 3)(\lambda - 2)(\lambda + 2)$, estamos ante el caso de raíces reales simples, de manera que la solución queda 

$$
a_h(n) = c_1(-2)^n + c_22^n + c_33^n,
$$ 

con $c_1,c_2,c_3\in\mathbb{R}$.

Para el apartado (b), $a_{n+3} - 4a_{n+2} + 5a_{n+1} - 2a_n = 0$ es homogénea de orden 3, con ecuación característica 

$$
\lambda^3 - 4\lambda^2 + 5\lambda - 2 = 0.
$$ 

Como $\lambda^3 - 4\lambda^2 + 5\lambda - 2 = (\lambda - 2)(\lambda - 1)^2$, $\lambda=1$ es una raíz real de multiplicidad $m=2$, mientras que $\lambda=2$ es una raíz real simple, por lo que la solución queda 

$$
a_h(n) = c_11^n + c_2n1^n + c_32^n = c_1+c_2n+c_32^n,
$$ 

con $c_1,c_2,c_3\in\mathbb{R}$.
