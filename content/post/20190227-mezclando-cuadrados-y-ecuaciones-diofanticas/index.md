+++
title = "Mezclando cuadrados y ecuaciones diofánticas"
slug  = "mezclando-cuadrados-y-ecuaciones-diofanticas"
subtitle = "Problema 55"
summary  = "Problema 55: aparece de nuevo la ecuación de Pell."

date     = 2019-02-27T05:59:39+02:00
#lastmod = 2019-04-08T09:37:29+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Ecuación de Pell", "Ecuaciones diofánticas", "Problemas"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Len Roth](https://unsplash.com/@lenroth), disponible en [Unsplash](https://unsplash.com/photos/4XXNWJJ4msg)."
+++

**Problema 55:** Halla un cuadrado de cinco cifras que sea igual a cinco veces otro cuadrado, más uno.

***

El enunciado del ejercicio nos lleva a plantear la ecuación $x^2 = 5y^2+1$, equivalente a $x^2-5y^2=1$, *ecuación de Pell* que sabemos posee infinitas soluciones en los enteros al no ser $5$ un cuadrado perfecto. Por tanteo, hallamos la solución particular $x=9$ e $y=4$, ya que $9^2 - 5\cdot4^2=1$. Expresamos ahora la diferencia de cuadrados como producto de una suma y una diferencia, de forma que

$$
9^2 - 5\cdot4^2=1 \Leftrightarrow (9+4\sqrt{5})(9-4\sqrt{5}) = 1.
$$

Análogamente, la sucesión de soluciones enteras, que denotaremos por $(x\_n,y\_n)$, debe cumplir que $(x\_n+y\_n\sqrt{5})(x\_n-y\_n\sqrt{5})=1$. Expresamos la solución general utilizando recurrencias, de manera que,

$$
x\_{n+1} + y\_{n+1}\sqrt{5} = (x\_n + y\_n\sqrt{5})(9+4\sqrt{5}) = 9x\_n + 4\sqrt{5}x\_n + 9\sqrt{5}y\_n + 20y\_n,
$$

luego

$$
\begin{aligned}
x\_{n+1} &= 9x\_n + 20y\_n,\\\\ y\_{n+1} &= 4x\_n + 9y\_n.
\end{aligned}
$$

Utilizando notación matricial,

$$
\begin{bmatrix}
x\_{n+1}\\\\ y\_{n+1}
\end{bmatrix}
= \begin{bmatrix}
9 & 20\\\\ 4 & 9
\end{bmatrix}
\begin{bmatrix}
x\_n\\\\ y\_n
\end{bmatrix},
$$

con $(x\_1,y\_1) = (9,4)$. La solución particular hallada no cumple los requisitos impuestos en el enunciado del ejercicio, por lo que procederemos a obtener la siguiente.

$$
\begin{bmatrix}
x\_2\\\\ y\_2
\end{bmatrix}
= \begin{bmatrix}
9 & 20\\\\ 4 & 9
\end{bmatrix}
\begin{bmatrix}
9\\\\ 4
\end{bmatrix}
= \begin{bmatrix}
161\\\\ 72
\end{bmatrix},
$$

que es la solución que estamos persiguiendo, pues $161^2 = 25921 = 5\cdot72^2+1$.