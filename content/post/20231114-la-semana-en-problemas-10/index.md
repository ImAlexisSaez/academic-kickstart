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

### Ejercicio 6

Sea $\mathbb{R}^3[x]$ el espacio vectorial de los polinomios de grado menor o igual que $3$ con coeficientes reales y sea {{< math >}}$B_1 = \{1, x, x^2, x^3\}${{< /math >}} la base canónica de $\mathbb{R}^3[x]$. Se consideran los subespacios vectoriales
{{< math >}}
\begin{align*}
    U_1 & := L\{x^2+2x, -x^2+x, x^2+x\},                                                                      \\
    U_2 & := \{a+bx+cx^2+dx^3\in\mathbb{R}^3[x]:b+c=0, 2b-c=0\},\text{ y}                                     \\
    U_3 & := \{a+bx+cx^2+dx^3\in\mathbb{R}^3[x]:a=0, b=-\beta,c=0,d=\alpha+\beta,\alpha,\beta\in\mathbb{R}\}.
\end{align*}
{{< /math >}}
    
- a) Calcule $U_1\cap U_2$ y $U_1+U_2$. ¿Son $U_1$ y $U_2$ suplementarios?
- b) Calcule unas ecuaciones cartesianas respecto de la base $B_1$ de $U_1$ y $U_2$.
- c) Encuentre una aplicación lineal {{< math >}}$h:\mathbb{R}^3[x]\mapsto \mathbb{R}^4${{< /math >}} cuyo núcleo sea $U_1$.
- d) Halle la matriz de la aplicación lineal anterior respecto de las bases $B_1$ y
{{< math >}}
\begin{align*}
    B_2 := \{u_1:&=(1,0,0,0),\\
     u_2:&=(1,1,0,0),\\
     u_3:&=(1,1,1,0),\\
     u_4:&=(1,1,1,1)\}.
\end{align*}
{{< /math >}}
- e) ¿Es la matriz hallada en el apartado anterior equivalente a la matriz
{{< math >}}
\begin{align*}
    A =
    \begin{bmatrix}
        3 & 4 & 2 & 1 \\
        1 & 0 & 0 & 0 \\
        3 & 1 & 1 & 1 \\
        0 & 0 & 0 & 1
    \end{bmatrix}?
\end{align*}
{{< /math >}}
