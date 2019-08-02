---
title: "Volvemos a los tiempos de libras, marcos y pesetas"
slug: "volvemos-a-los-tiempos-de-libras-marcos-y-pesetas"
subtitle: "Problema 53"
summary: "Problema 53: un problema clásico fuera del contexto actual."

date: 2019-02-20T05:59:39+02:00
lastmod: 2019-08-02T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Ecuaciones diofánticas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Andre Benz](https://unsplash.com/@trapnation), disponible en [Unsplash](https://unsplash.com/photos/HwWBTd21wiA)."
---

**Problema 53:** Para abonar una factura de $1840$ pesetas se entregan libras esterlinas y dan la vuelta en marcos. Calcula las libras esterlinas entregadas y los marcos devueltos suponiendo que se ha entregado la cantidad mínima de libras necesarias para pagar y que la devolución es en marcos ($1$ marco $=$ $70$ pesetas, $1$ libra $=$ $180$ pesetas).

***

Sea $x$ la cantidad de libras esterlinas entregadas e $y$ el total de marcos recibidos en la devolución. Como la factura viene dada en pesetas y tenemos indicadas las tasas de conversión de las otras dos monedas en relación a las pesetas, trabajaremos durante el resto del ejercicio con esta unidad monetaria. 

Con ello en mente, la cantidad que desembolso en libras para cumplir con la factura más el total de marcos que recibo en concepto de devolución ha de ascender a $1840$ pesetas, esto es,

$$
180x + 70y = 1840.
$$

Ahora bien, como $70 = 2\cdot5\cdot7$ y $180 = 2^2 \cdot 3^2 \cdot5$, $mcd(70, 180) = 10$. Dado que, trivialmente, $10|1840$, la ecuación diofántica propuesta admite solución entera. Simplificando dicha ecuación por $10$, tenemos que $18x + 7y = 184$, expresión que nos invita, para empezar, a llevar a cabo el cambio de variable

$$
\begin{aligned}
x &= 184x^{\prime},\\
y &= 184y^{\prime}
\end{aligned}
$$

que la transforma en $18x^{\prime} +7y^{\prime} =1$. Ahora, despejando la variable $y^{\prime}$, por ser aquella cuyo coeficiente asociado es más reducido, hallamos que

$$
y^{\prime} = \dfrac{1-18x^{\prime}}{7},
$$

por lo que basta probar, para $x^{\prime}$, valores pertenecientes al *menor sistema completo de restos módulo* $7$. Para $x^{\prime}_0 = 2$, resulta que $y^{\prime}_0 = (-5)$, y deshaciendo el anterior cambio de variable,

$$
\begin{aligned}
x_0 &= 184x^{\prime} = 184\cdot2 = 368,\\
y_0 &= 184y^{\prime} = 184\cdot(-5) = (-920),
\end{aligned}
$$

es una solución particular para la ecuación diofántica planteada. Su solución genera queda, entonces,

$$
\begin{aligned}
x &= 368 + 7t,\\ 
y &= (-920) - 18t,
\end{aligned}
$$

con $t$ número entero.

De entre las infinitas soluciones que tenemos a nuestra disposición, busquemos aquella que se ajusta a los dictados del enunciado del ejercicio, es decir, aquella para la cual se desembolsa la mínima cantidad de libras esterlinas necesarias para abonar la factura. Esta situación se traduce en averiguar el valor de $x$ tal que, $18x \geq 184$. Sustituyendo,

$$
18(368 + 7t)\geq 184,
$$

es decir, $6624 + 126t \geq 184$. Por tanto, $126t \geq (-6498)$, luego $t\geq (-51.6)$ y como $t$ ha de ser entero, la inecuación entonces queda $t\geq (-51)$. Como buscamos el menor valor para el que satisface la inecuación, este será, evidentemente, $t=(-51)$, resultando entonces

$$
\begin{aligned}
x &= 368 + 7\cdot(-51) = 11,\\
y &= (-920) - 18\cdot(-51) = -2,
\end{aligned}
$$

esto es, abonaremos la factura con $11$ libras esterlinas y nos devolverán $2$ marcos.
