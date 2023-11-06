---
title: "La semana en problemas (S10)"
slug: "la-semana-en-problemas-s10"
subtitle: "Problemas de polinomios"
summary: "Esta semana se proponen algunos enunciados relacionados con polinomios."

date: 2023-11-14T00:00:00+02:00
# lastmod: 2023-04-29T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Polinomios"]
categories: ["Problemas"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Jeswin Thomas](https://unsplash.com/es/@jeswinthomas), disponible en [Unsplash](https://unsplash.com/es/fotos/hecib2an4T4)."
---

Esta semana se proponen algunos enunciados relacionados con polinomios.

### Ejercicio 1

Dado $P_3$, espacio vectorial de los polinomios reales de variable real de grado menor o igual que $3$:

- a) Demuestre que {{< math >}}$\{1, x+1, (x+1)^2, x^3\}${{< /math >}} es una base.
- b) Halle las componentes de $(x+1)^3$ respecto a dicha base.
- c) Fijando como base de $P_3$ la del apartado a), determine la matriz de la aplicación lineal $f$ que a cada polinomio le hace corresponder su derivada.

### Ejercicio 2

Sea $P_n$ el espacio vectorial de los polinomios reales de variable real de grado menor o igual que $n$.

- a) Pruebe que {{< math >}}$B_1 = \{p_0, p_1, \ldots, p_n\}${{< /math >}}, donde $p_i(x) = x^i$, $i = 0,1,\ldots,n$ es una base de $P_n$.
- b) Pruebe que {{< math >}}$B_2 = \{q_0, q_1, \ldots, q_n\}${{< /math >}}, donde $q_i(x) = (1+x)^i$, $i = 0,1,\ldots,n$ también es base de $P_n$.
- c) Exprese las ecuaciones del cambio de la base $B_2$ a $B_1$.
- d) Demuestre que, para $k\leq n$, es
{{< math >}}
\begin{align*}
    \binom{k}{k} + \binom{k+1}{k} + \binom{k+2}{k} + \cdots + \binom{n}{k} = \binom{n+1}{k}.
\end{align*}
{{< /math >}}
- e) Si las coordenadas del polinomio $r(x)$ en la base $B_2$ son $(1,1,\ldots,1)$, determine sus coordenadas en la base $B_1$.

### Ejercicio 3

Halle $a$ y $b$ para que el polinomio $p(x) = ax^{n+1} + bx^n + 1$ sea divisible por $(x-1)^2$.

### Ejercicio 4

Pruebe que el polinomio $p(x) = x(x+1)(x+2)(x+3) + 1$ es un cuadrado perfecto en $\mathbb{R}[x]$.


### Ejercicio 5

Halle todos los polinomios $P(x)$ con coeficientes reales tal que
{{< math >}}
\begin{align*}
    P(x+2) - 2P(x+1) + P(x) = x,
\end{align*}
{{< /math >}}
sabiendo que $P(0) = \frac{1}{6}$ y que $P(3) = \frac{2}{3}$.
