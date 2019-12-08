---
title: "Repasando ecuaciones en diferencias lineales (IV)"
slug: "repasando-ecuaciones-en-diferencias-lineales-iv"
subtitle: "Problema 15"
summary: "Problema 15: aparecen funciones potenciales como términos independientes."

date: 2018-10-04T05:59:39+02:00
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
  caption: "Fotografía de [sanjoy saha](https://unsplash.com/@rupam118), disponible en [Unsplash](https://unsplash.com/photos/0BZlxflMHJ8)."
---

**Problema 15:** Resuelve

- (a) $a_{n+2}-3a_{n+1}-2a_n = 3^n$.
- (b) $a_{n+2}-3a_{n+1}+2a_n = 2^n$.

***

En el apartado (a), encontramos la ecuación en diferencias lineal completa de orden 2, 

$$
a_{n+2}-3a_{n+1}-2a_n = 3^n.
$$

Su ecuación en diferencias lineal homogénea asociada es 

$$
a_{n+2}-3a_{n+1}-2a_n = 0,
$$

con ecuación característica 

$$
\lambda^2 - 3\lambda - 2 = 0.
$$ 

Ahora, como $\lambda^2 - 3\lambda - 2=(\lambda - 2)(\lambda - 1)$, estamos en el caso de raíces reales simples, por lo que la solución para la ecuación anterior queda 

$$
a_h(n) = c_11^n + c_22^n = c_1+c_22^n,
$$ 

con $c_1,c_2\in\mathbb{R}$. 

A continuación, para encontrar una solución particular, $a_p(n)$, como $b(n) = 3^n$ y $\lambda = 3$ no es raíz de la ecuación característica, proponemos $a_p(n) = k3^n$, de manera que, sustituyendo en la ecuación inicial, 

$$
\begin{aligned}
k3^{n+2} - 3k3^{n+1} + 2k3^n &= 3^n,\\ 
9k - 9k + 2k &= 1,\\
2k &= 1,
\end{aligned}
$$

es decir, $k = 1 / 2$, con lo que 

$$
a_p(n) = \dfrac{1}{2}3^n.
$$ 

Finalmente, la solución general de la ecuación inicial la obtenemos haciendo 

$$
a(n) = a_h(n) + a_p(n) = c_1+c_22^n + \dfrac{1}{2}3^n,
$$ 

con $c_1,c_2\in\mathbb{R}$.

En el apartado (b), la ecuación en diferencias lineal 

$$
a_{n+2}-3a_{n+1}+2a_n = 2^n
$$

es completa de orden 2. Su ecuación en diferencial lineal homogénea asociada es

$$
a_{n+2}-3a_{n+1}+2a_n = 0,
$$

con ecuación característica correspondiente 

$$
\lambda^2 - 3\lambda + 2 = 0.
$$ 

Como $\lambda^2 - 3\lambda + 2 = (\lambda - 2)(\lambda - 1)$, estamos en el caso de raíces reales simples, por lo que la solución para la ecuación anterior queda 

$$
a_h(n) = c_11^n + c_22^n=c_1+c_22^n,
$$ 

con $c_1,c_2\in\mathbb{R}$. 

Ahora, para encontrar una solución particular, $a_p(n)$, como $b(n) = 2^n$ y $\lambda=2$ es una raíz simple ($m=1$) de la ecuación característica, proponemos $a_p(n) = kn^12^n = kn2^n$, de forma que, sustituyendo en la ecuación inicial,

$$
\begin{aligned}
k(n+2)2^{n+2} - 3k(n+1)2^{n+1}+2kn2^n &= 2^n,\\
4k(n+2) - 6k(n+1) + 2kn &= 1,\\
4kn + 8k - 6kn - 6k + 2kn &=1,\\
2k &= 1,
\end{aligned}
$$

es decir, $k=1 / 2$, con lo que 

$$
a_p(n) = \dfrac{1}{2}n2^n = n2^{n-1}.
$$ 

Finalmente, la solución general de la ecuación inicial la obtenemos haciendo 

$$
a(n) = a_h(n) + a_p(n) = c_1+c_22^n+n2^{n-1},
$$ 

con $c_1,c_2\in\mathbb{R}$.
