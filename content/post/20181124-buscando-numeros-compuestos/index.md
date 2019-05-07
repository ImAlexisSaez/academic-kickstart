+++
title = "Buscando números compuestos"
slug  = "buscando-numeros-compuestos"
subtitle = "Problema 28"
summary  = "Problema 28: factoriales y números primos al rescate."

date     = 2018-11-24T05:59:39+02:00
#lastmod = 2019-04-03T07:30:15+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Problemas", "Teoría de números"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Ricardo Resende](https://unsplash.com/@rresenden), disponible en [Unsplash](https://unsplash.com/photos/Vq3B58_XgjQ)."
+++

**Problema 28:** Encuentra diez números compuestos consecutivos.

***

Dado que preguntan por diez números compuestos consecutivos cualesquiera (y no, por ejemplo, por los diez primeros números que satisfacen dicha propiedad), existen dos estrategias habituales para abordar la resolución de este tipo de ejercicios.

En primer lugar, consideremos que buscamos únicamente tres números compuestos consecutivos, en lugar de los diez que solicita el enunciado, de cara a aliviar un tanto la escritura. Tomemos entonces el factorial de $4$, $4! = 1\cdot2\cdot3\cdot4$, de manera que es cierto que:

$$
\begin{aligned}
4! + 2 &= 2\cdot(1\cdot3\cdot4 + 1),\\\\ 4! + 3 &= 3\cdot(1\cdot2\cdot4 + 1),\\\\ 4! + 4 &= 4\cdot(1\cdot2\cdot3 + 1),
\end{aligned}
$$

son tres números consecutivos compuestos. En general, dado un número $n\in\mathbb{N}$, si buscamos $n$ números compuestos consecutivos, una opción es considerar el número $(n+1)!$ y, a partir de él, generar el conjunto de números compuestos consecutivos siguiente: 

$$
\\{(n+1)! + k: k\in\mathbb{N}, 2\leq k\leq n+1\\}.
$$ 

Así, para $n=10$, siguiendo esta indicación, un conjunto de diez números compuestos consecutivos es $\\{11! + k: k\in\mathbb{N}, 2\leq k\leq 11\\}$.

Alternativamente, si no queremos trabajar con números cuya magnitud es tan severa, podemos optar por construir el producto de los primeros números primos hasta encontrar aquel que supere en valor la cantidad de números compuestos consecutivos que deseamos encontrar. Por ejemplo, para $n=3$, el mencionado producto sería $2\cdot3\cdot5$, que satisface que:

$$
\begin{aligned}
2\cdot3\cdot5 + 2 &= 2(3\cdot 5 + 1),\\\\ 2\cdot3\cdot5 + 3 &= 3(2\cdot 5 + 1),\\\\ 2\cdot3\cdot5 + 4 &= 2(3\cdot 5 + 2),
\end{aligned}
$$

son tres números consecutivos compuestos. Para $n=10$, consideraríamos entonces el conjunto 

$$
\\{2\cdot3\cdot5\cdot7\cdot11 + k:k\in\mathbb{N}, 2\leq k\leq 11\\},
$$ 

que contiene diez números compuestos consecutivos.
