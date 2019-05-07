+++
title = "Repasando ecuaciones en diferencias lineales (III)"
slug  = "repasando-ecuaciones-en-diferencias-lineales-iii"
subtitle = "Problema 14"
summary  = "Problema 14: ecuaciones en diferencias lineales completas sencillas."

date     = 2018-10-02T05:59:39+02:00
#lastmod = 2019-04-01T16:29:18+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Ecuaciones en diferencias", "Problemas"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [David Werbrouck](https://unsplash.com/@bigkids), disponible en [Unsplash](https://unsplash.com/photos/hxhZMwfiGdQ)."
+++

**Problema 14:** Resuelve

- (a) $a\_{n+2}-5a\_{n+1}+6a_n = 10$.
- (b) $a\_{n+2}-3a\_{n+1}+2a_n = 4$.

***

En el apartado (a), encontramos la ecuación en diferencias lineal completa de orden 2, 

$$
a\_{n+2}-5a\_{n+1}+6a_n = 10.
$$

Empecemos abordando su ecuación en diferencias lineal homogénea asociada, 

$$
a\_{n+2}-5a\_{n+1}+6a_n = 0,
$$

cuya ecuación característica correspondiente es 

$$
\lambda^2-5\lambda+6=0.
$$ 

Ahora, como $\lambda^2-5\lambda+6=(\lambda - 3)(\lambda - 2)$, estamos en el caso de raíces reales simples, de manera que la solución para la ecuación anterior queda 

$$
a_h(n) = c_12^n + c_23^n,
$$ 

con $c_1,c_2\in\mathbb{R}$. 

A continuación, de cara a encontrar una solución particular, $a_p(n)$, como $b(n)=10$ y $\lambda=1$ no es raíz de la ecuación característica, proponemos $a_p(n) = k$, de forma que, sustituyendo esta en la ecuación inicial, 

$$
k-5k+6k=10,
$$ 

es decir, $k=5$, con lo que 

$$
a_p(n)=5.
$$ 

Finalmente, la solución general para la ecuación inicial la obtenemos haciendo 

$$
a(n) = a_h(n) + a_p(n) = c_12^n + c_23^n + 5,
$$ 

con $c_1,c_2\in\mathbb{R}$.

En el apartado (b), la ecuación en diferencias lineal 

$$
a\_{n+2}-3a\_{n+1}+2a\_n = 4
$$

es completa de orden 2. Procediendo como antes, abordamos su ecuación en diferencias lineal homogénea correspondiente 

$$
a\_{n+2}-3a\_{n+1}+2a_n = 0,
$$

con ecuación característica asociada 

$$
\lambda^2 - 3\lambda + 2 = 0.
$$ 

Como $\lambda^2 - 3\lambda + 2 = (\lambda - 2)(\lambda - 1)$, volvemos a estar en el caso de raíces reales simples, por lo que la solución para la ecuación anterior queda 

$$
a_h(n) = c_11^n + c_22^n=c_1 + c_22^n,
$$ 

con $c_1,c_2\in\mathbb{R}$. 

Acto seguido, para encontrar una solución particular, $a_p(n)$, como $b(n)=4$ y $\lambda=1$ es raíz simple ($m=1$) de la ecuación característica, proponemos $a_p(n) = kn^1 = kn$, de forma que, sustituyendo en la ecuación inicial, 

$$
k(n+2)-3k(n+1)+2kn = kn+2k-3kn-3k+2kn= -k = 4,
$$ 

es decir, $k = -4$, con lo que 

$$
a_p(n) = -4n.
$$ 

Finalmente, la solución general de la ecuación inicial la obtenemos haciendo 

$$
a(n) = a_h(n) + a_p(n) = c_1+c_22^n-4n,
$$ 

con $c_1,c_2\in\mathbb{R}$.
