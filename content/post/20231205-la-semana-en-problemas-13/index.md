---
title: "La semana en problemas (S13)"
slug: "la-semana-en-problemas-s13"
subtitle: "Problemas de sistemas, matrices, programación lineal y determinantes"
summary: "Esta semana se proponen algunos enunciados relacionados con sistemas, matrices, programación lineal y determinantes."

date: 2023-12-05T00:00:00+02:00
# lastmod: 2023-04-29T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Determinantes", "Matrices", "Programación lineal", "Sistemas"]
categories: ["Problemas"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Jeswin Thomas](https://unsplash.com/es/@jeswinthomas), disponible en [Unsplash](https://unsplash.com/es/fotos/hecib2an4T4)."
---

Esta semana se proponen algunos enunciados relacionados con matrices, programación lineal y determinantes.

### Ejercicio 1

Discuta y resuelva el siguiente sistema según los valores de $m\in\mathbb{R}$:
{{< math >}}
\begin{align*}
    S:
    \left\{
    \begin{aligned}
        -x + (1+m)y + (2-m)z + mt & = 3 \\
        mx + y + (2-m)z + mt      & = 2 \\
        mx + my + (2-m)z + mt     & = 2 \\
        mx + my + (2-m)z - t      & = 2
    \end{aligned}
    \right.
\end{align*}
{{< /math >}}

### Ejercicio 2

Discuta, según los valores reales de $a$ y $b$, el sistema siguiente y resuélvalo cuando sea compatible determinado.
{{< math >}}
\begin{align*}
    \left\{
    \begin{aligned}
        ax + by + z & = 1 \\
        x + aby + z & = b \\
        x + by + az & = 1
    \end{aligned}
    \right.
\end{align*}
{{< /math >}}

### Ejercicio 3

Una confitería de Santander es famosa por sus dos especialidades de tartas: la tarta de chocolate y la tarta de limón. La tarta de chocolate requiere para su elaboración medio kilo de azúcar y ocho huevos y tiene un precio de venta de $8$ euros. La tarta de limón necesita un kilo de azúcar y ocho huevos y se vende a $10$ euros la unidad. En el almacén de la confitería quedaban diez kilos de azúcar y ciento veinte huevos. ¿Cuántas unidades de cada tipo de tarta han de producirse para obtener el mayor ingreso por ventas

### Ejercicio 4

Sea $n\in\mathbb{N}$. Determine todas las matrices $A\in\mathcal{M}_2(\mathbb{R})$ tales que
{{< math >}}
\begin{align*}
    A^n =
    \begin{bmatrix}
        1 & 0 \\
        1 & 1
    \end{bmatrix}.
\end{align*}
{{< /math >}}

### Ejercicio 5

Sea $n$ un número natural no nulo. Determine la matriz
{{< math >}}
\begin{align*}
    S_n = \binom{n}{1}X^2 + \binom{n}{2}X^4 + \cdots + \binom{n}{n}X^{2n}
\end{align*}
donde
\begin{align*}
    X =
    \begin{bmatrix}
        0 & -i \\
        i & 0
    \end{bmatrix}
    \in\mathcal{M}_2(\mathbb{C})
\end{align*}
{{< /math >}}
e $i$ es la unidad imaginaria.

### Ejercicio 6

Calcule la potencia enésima de la matriz
{{< math >}}
\begin{align*}
    A =
    \begin{bmatrix}
        1 & 0 & 0 \\
        1 & 1 & 0 \\
        1 & 1 & 1
    \end{bmatrix}.
\end{align*}
{{< /math >}}