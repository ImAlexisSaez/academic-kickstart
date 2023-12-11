---
title: "La semana en problemas (S15)"
slug: "la-semana-en-problemas-s15"
subtitle: "Problemas de matrices y determinantes"
summary: "Esta semana se proponen algunos enunciados relacionados con matrices y determinantes."

date: 2023-12-19T00:00:00+02:00
# lastmod: 2023-04-29T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Determinantes", "Matrices"]
categories: ["Problemas"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Jeswin Thomas](https://unsplash.com/es/@jeswinthomas), disponible en [Unsplash](https://unsplash.com/es/fotos/hecib2an4T4)."
---

Esta semana se proponen algunos enunciados relacionados con matrices y determinantes



### Ejercicio 1

Demuestre que la siguiente matriz $A$ es diagonalizable sobre el cuerpo $\mathbb{R}$ de los números reales y encuentre una matriz regular $P$ de números reales tal que $P^{-1}AP$ sea una matriz diagonal.
{{< math >}}
\begin{align*}
    A =
    \begin{bmatrix}
        2 & 0  & -1 & 0  \\
        4 & -3 & 1  & -3 \\
        6 & -6 & 3  & -6 \\
        2 & -2 & 1  & -2
    \end{bmatrix}
\end{align*}
{{< /math >}}

### Ejercicio 2

Se considera la aplicación $f:\mathbb{R}^3\rightarrow\mathbb{R}^3$ definida por
{{< math >}}
\begin{align*}
    f(x, y, z) = (x - 4y, -y, 2y + z).
\end{align*}
{{< /math >}}
    
- a) Demuestre que $f$ es endomorfismo del espacio vectorial $\mathbb{R}^3$.
- b) Determine la expresión matricial de $f$ respecto de la base canónica de $\mathbb{R}^3$.
- c) Calcule el núcleo y la imagen de $f$.
- d) Calcule los valores propios de $f$ y los subespacios de vectores propios asociados.
- e) Determine si la matriz $A$ asociada a la aplicación lineal $f$ en la base canónica es diagonalizable y, en caso afirmativo, calcule una matriz diagonal semejante a $A$ y una matriz de paso correspondientes.
- f) Calcule la matriz $A^9$.

### Ejercicio 3

Dado el determinante de orden $n$:
{{< math >}}
\begin{align*}
    D =
    \begin{vmatrix}
        8      & 3      & 3      & \ldots & 3      & 3      \\
        3      & 8      & 3      & \ldots & 3      & 3      \\
        3      & 3      & 8      & \ldots & 3      & 3      \\
        \vdots & \vdots & \vdots & \ddots & \vdots & \vdots \\
        3      & 3      & 3      & \ldots & 8      & 3      \\
        3      & 3      & 3      & \ldots & 3      & 8
    \end{vmatrix}
\end{align*}
{{< /math >}}
    
- a) Calcule su valor.
- b) Determine para qué enteros positivos $n$ dicho valor es múltiplo de $10$.

### Ejercicio 4

Calcule el valor del determinante:
{{< math >}}
\begin{align*}
    D =
    \begin{vmatrix}
        x - 1   & x^2 - 1  & x^3 - 1  & x^4 - x^3 + x - 1    \\
        2x - 4  & x^2 - 4  & x^3 - 8  & x^4 - 2x^3 + 2x - 4  \\
        3x - 9  & x^2 - 9  & x^3 - 27 & x^4 - 2x^3 + 3x - 9  \\
        4x - 16 & x^2 - 16 & x^3 - 64 & x^4 - 4x^3 + 4x - 16
    \end{vmatrix}
\end{align*}
{{< /math >}}

### Ejercicio 5

Calcule el valor del siguiente determinante de orden $n\in\mathbb{N}$:
{{< math >}}
\begin{align*}
    A_n =
    \begin{vmatrix}
        1 + x  & 1      & 1      & \ldots & 1      \\
        1      & 1 + x  & 1      & \ldots & 1      \\
        1      & 1      & 1 + x  & \ldots & 1      \\
        \vdots & \vdots & \vdots & \ddots & \vdots \\
        1      & 1      & 1      & \ldots & 1 + x
    \end{vmatrix}
\end{align*}
{{< /math >}}

### Ejercicio 6

Calcule el valor del siguiente determinante de orden $n$:
{{< math >}}
\begin{align*}
    D_n =
    \begin{vmatrix}
        1 + x^4 & x^2     & 0       & 0       & \ldots & 0       & 0       \\
        x^2     & 1 + x^4 & x^2     & 0       & \ldots & 0       & 0       \\
        0       & x^2     & 1 + x^4 & x^2     & \ldots & 0       & 0       \\
        0       & 0       & x^2     & 1 + x^4 & \ldots & 0       & 0       \\
        \vdots  & \vdots  & \vdots  & \vdots  & \ddots & \vdots  & \vdots  \\
        0       & 0       & 0       & 0       & \ldots & 1 + x^4 & x^2     \\
        0       & 0       & 0       & 0       & \ldots & x^2     & 1 + x^4
    \end{vmatrix}
\end{align*}
{{< /math >}}

### Ejercicio 7

Sea $x\in\mathbb{R}$ y sea $D_n$ el siguiente determinante de orden $n$:
{{< math >}}
\begin{align*}
    D_n =
    \begin{vmatrix}
        1 + x^2 & x       & 0       & 0       & \ldots & 0       & 0       \\
        x       & 1 + x^2 & x       & 0       & \ldots & 0       & 0       \\
        0       & x       & 1 + x^2 & x       & \ldots & 0       & 0       \\
        0       & 0       & x       & 1 + x^2 & \ldots & 0       & 0       \\
        \vdots  & \vdots  & \vdots  & \vdots  & \ddots & \vdots  & \vdots  \\
        0       & 0       & 0       & 0       & \ldots & 1 + x^2 & x       \\
        0       & 0       & 0       & 0       & \ldots & x       & 1 + x^2
    \end{vmatrix}
\end{align*}
{{< /math >}}
    
- a) Calcule el polinomio ordenado en $x$ que resulta al desarrollar $D_n$.
- b) En este ejercicio se abordan conceptos como polinomios ordenados, determinantes y matrices. Relaciónelos con el currículum del bachillerato y dé alguna aplicación didáctica de los mismos.
