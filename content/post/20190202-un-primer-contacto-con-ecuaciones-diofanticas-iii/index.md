---
title: "Un primer contacto con ecuaciones diofánticas (III)"
slug: "un-primer-contacto-con-ecuaciones-diofanticas-iii"
subtitle: "Problema 48"
summary: "Problema 48: un rápido vistazo a una ecuación diofántica no lineal."

date: 2019-02-02T05:59:39+02:00
lastmod: 2019-08-01T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Ecuaciones diofánticas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Alexander Slash](https://unsplash.com/@alexanderslash), disponible en [Unsplash](https://unsplash.com/photos/reYDl88Nah0)."
---

**Problema 48:** Halla las soluciones enteras de la ecuación $x^2 - y^2=36$.

***

Al ser $36$ par y múltiplo de $4$, $36 = 2^2 \cdot 3^2$, estamos en condiciones de asegurar que la ecuación diofántica planteada admite solución entera. Escribimos $x^2 - y^2=36$ como $(x+y)(x-y)=36$, y consideramos 

$$
\begin{aligned}
36 &= 36\cdot1 \\
&= 18\cdot2 \\
&= 12\cdot3 \\
&= 9\cdot4 \\
&= 6\cdot6 \\
&= 4\cdot9 \\
&= 3\cdot12 \\
&= 2\cdot18 \\
&= 1\cdot36,
\end{aligned}
$$ 

descartando automáticamente aquellos casos en los que la paridad de ambos términos no coincide. 

Así, para $36 = 18\cdot2$, tenemos el sistema de ecuaciones lineales

$$
\begin{aligned}
x+y &= 18,\\
x-y &=  2,
\end{aligned}
$$

con solución $x = 10$ e $y = 8$. Para la descomposición $36 = (-18)\cdot(-2)$ el sistema de ecuaciones lineales que conformaríamos posee como solución $x = (-10)$ e $y = (-8)$.

A continuación, si $36 = 6\cdot6$, tenemos el sistema de ecuaciones lineales

$$
\begin{aligned}
x+y &= 6,\\
x-y &= 6,
\end{aligned}
$$

con solución $x = 6$ e $y = 0$. Para la descomposición $36 = (-6)\cdot(-6)$ el sistema de ecuaciones lineales que conformaríamos posee como solución $x = (-6)$ e $y = 0$.

Acto seguido, si $36 = 2\cdot18$, tenemos el sistema de ecuaciones lineales

$$
\begin{aligned}
x+y &=  2,\\
x-y &= 18,
\end{aligned}
$$

con solución $x = 10$ e $y = (-8)$. Para la descomposición $36 = (-2)\cdot(-18)$ el sistema de ecuaciones lineales que conformaríamos posee como solución $x = (-10)$ e $y = 8$.

Queda así resuelta la ecuación diofántica planteada en el enunciado del ejercicio.
