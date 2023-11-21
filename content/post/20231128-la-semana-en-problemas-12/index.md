---
title: "La semana en problemas (S12)"
slug: "la-semana-en-problemas-s12"
subtitle: "Problemas de ecuaciones diofánticas"
summary: "Esta semana se proponen algunos enunciados relacionados con ecuaciones."

date: 2023-11-28T00:00:00+02:00
# lastmod: 2023-04-29T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Ecuaciones", "Ecuaciones diofánticas", "Métodos numéricos"]
categories: ["Problemas"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Jeswin Thomas](https://unsplash.com/es/@jeswinthomas), disponible en [Unsplash](https://unsplash.com/es/fotos/hecib2an4T4)."
---

Esta semana se proponen algunos enunciados relacionados con ecuaciones (haciendo hincapié en su resolución numérica) y con ecuaciones diofánticas.

### Ejercicio 1

Responda a las siguientes cuestiones:

- a) Demuestre que todo polinomio de grado impar con coeficientes reales tiene, por lo menos, una raíz real.
- b) Razone entonces que el polinomio $x^8 + 3x^3 - 1$ tiene al menos dos raíces reales y distintas.
- c) Demuestre que el polinomio $x^3 - 3x + a$ no puede tener más de una raíz en el intervalo $[-1, 1]$.
- d) ¿Para qué valores de $a$ el polinomio $x^3 - 3x + a$ no tiene raíz alguna en el intervalo $[-1, 1]$?
- e) Demuestre que todo número real positivo tiene raíz cuadrada positiva.
- f) Halle una solución de la ecuación $x^3 + x^2 -7x + 1 = 0$, con un error menor que $0.07$.
- g) Estudie la continuidad de la función $g:\mathbb{R}\rightarrow\mathbb{R}$ dada por
{{< math >}}
\begin{align*}
    g(x) =
    \left\{
    \begin{aligned}
        x,  &\quad \text{si } x\in\mathbb{Q}   \\
        2x, &\quad \text{si} x\notin\mathbb{Q}
    \end{aligned}
    \right..
\end{align*}
{{< /math >}}
- h) Sea $f:\mathbb{R}\rightarrow\mathbb{R}$ una función continua tal que $f(x)\in\mathbb{Q}$ para todo $x\in\mathbb{R}$. Demuestre que $f$ es necesariamente una función constante.

### Ejercicio 2

La ecuación $x - e^{-x} = 0$ tiene una solución en el intervalo $[0.5, 0.6]$. Para aproximar dicha solución se consideran los métodos de Lagrange, de Newton y de las aproximaciones sucesivas basado en la función $g$ definida por $g(x) = -\ln{x}$. Justifique la existencia de dicha solución y analice la conveniencia de utilizar un método u otro para aproximarla.

### Ejercicio 3

Un hombre acude a un banco para cobrar un cheque por valor de $E$ euros y $C$ céntimos. El cajero, por error, le entrega un sobre con $C$ euros y $E$ céntimos. El cliente no se da cuenta del error hasta que gasta $23$ céntimos y, además, observa que en ese momento tiene $2E$ euros y $2C$ céntimos. ¿Cuál es el valor del cheque?

### Ejercicio 4

Responda razonadamente a las siguientes cuestiones:

- a) Halle un conjunto infinito de ternas $(a, b, c)$ formadas por números naturales distintos que sean solución de la ecuación
{{< math >}}
\begin{align*}
    a^2 + b^2 + c^2 = 2c(a + b).
\end{align*}
{{< /math >}}
- b) Demuestre que la ecuación
{{< math >}}
\begin{align*}
    a^3 + b^3 - c^3 = 3b(a - c)(a + c - b)
\end{align*}
{{< /math >}}
no tiene soluciones $(a, b, c)\in\mathbb{N}^3$ tales que $a < b < c$.
