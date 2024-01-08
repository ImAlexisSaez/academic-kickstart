---
title: "La semana en problemas (S17)"
slug: "la-semana-en-problemas-s17"
subtitle: "Problemas de límites"
summary: "Esta semana se proponen algunos enunciados relacionados con límites."

date: 2024-01-23T00:00:00+02:00
# lastmod: 2023-04-29T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Límites"]
categories: ["Problemas"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Jeswin Thomas](https://unsplash.com/es/@jeswinthomas), disponible en [Unsplash](https://unsplash.com/es/fotos/hecib2an4T4)."
---

Esta semana se proponen algunos enunciados relacionados con límites.

### Ejercicio 1

Calcula:
{{< math >}}
\begin{align*}
    \lim_{n\rightarrow\infty}{\frac{\sum_{i=1}^{n}{i^2}}{n^3}}.
\end{align*}
{{< /math >}}


### Ejercicio 2

Calcula:
{{< math >}}
\begin{align*}
    \lim_{n\rightarrow\infty}{\left(\frac{3}{1}\right)^{\frac{1}{n}}\cdot\left(\frac{4}{2}\right)^{\frac{2}{n}}\cdot\ldots\cdot\left(\frac{n+2}{n}\right)^{\frac{n}{n}}}.
\end{align*}
{{< /math >}}

### Ejercicio 3

Calcula:
{{< math >}}
\begin{align*}
    \lim_{n\rightarrow\infty}{\sqrt[n]{n^2+1}}.
\end{align*}
{{< /math >}}

### Ejercicio 4

Calcula:
{{< math >}}
\begin{align*}
    \lim_{n\rightarrow\infty}{\frac{\ln{n!}}{n}}.
\end{align*}
{{< /math >}}

### Ejercicio 5

Calcule:
{{< math >}}
\begin{align*}
    \lim_{x\rightarrow\infty}{\frac{x + \sin{x}}{x - \sin{x}}}
\end{align*}
{{< /math >}}

### Ejercicio 6

Calcule:
{{< math >}}
\begin{align*}
    E = \lim_{n\rightarrow\infty}{
        \left[
            \frac{1}{1\cdot 2} + \frac{1}{2\cdot 3} + \ldots + \frac{1}{(n-1)n} + \frac{1}{n(n+1)}
            \right]
    }.
\end{align*}
{{< /math >}}

### Ejercicio 7

Calcule:
{{< math >}}
\begin{align*}
    \lim_{n\rightarrow\infty}{
        \frac{1}{n^2}
        \left[
            \frac{2}{1} + \frac{3^2}{2} + \frac{4^3}{3^2} + \ldots + \frac{(n+1)^n}{n^{n-1}}
            \right]
    }.
\end{align*}
{{< /math >}}

### Ejercicio 8

Calcule:
{{< math >}}
\begin{align*}
    \lim_{n\rightarrow\infty}{
        \sqrt[n]{\binom{n}{0}\binom{n}{1}\cdots\binom{n}{n}}
    }.
\end{align*}
{{< /math >}}

### Ejercicio 9

Calcule:
{{< math >}}
\begin{align*}
    \lim_{n\rightarrow\infty}{
        \sqrt[n^2]{\binom{n}{0}\binom{n}{1}\cdots\binom{n}{n}}
    }.
\end{align*}
{{< /math >}}

### Ejercicio 10

Estudie la continuidad de la función $f:[0, 1]\rightarrow\mathbb{R}$ dada por
{{< math >}}
\begin{align*}
    f(x) :=
    \left\{
    \begin{aligned}
        0,           & \quad\text{ si }x = 0\text{ o }x\notin\mathbb{Q}                     \\
        \frac{1}{q}, & \quad\text{ si }x = \frac{p}{q},\ p,q\in\mathbb{N}^+,\ mcd(p,q)=1
    \end{aligned}
    \right.
\end{align*}
{{< /math >}}

### Ejercicio 11

Sea $f:[0, 1] \rightarrow [0, 1]$ una función real tal que
{{< math >}}
\begin{align*}
    f(x) =
    \left\{
    \begin{aligned}
        x,     & \quad\text{ si }x\text{\ es racional}    \\
        1 - x, & \quad\text{ si }x\text{\ no es racional}
    \end{aligned}
    \right.
\end{align*}
{{< /math >}}
    
- (a) Estudie la continuidad en los puntos $x_0 = \frac{1}{2}$ y $x_1 = \frac{1}{4}$.
- (b) Estudie la derivabilidad en dichos puntos.

### Ejercicio 12

Una semicircunferencia de radio $r$ se divide en $n + 1$ partes iguales y se uno un punto cualquiera de la división con los extremos, formándose un triángulo rectángulo de área $A(k)$. Se pide el límite, cuando $n\rightarrow\infty$, de la media aritmética de las áreas de esos triángulos.

### Ejercicio 13

Sea $f\in\mathcal{C}^2(\mathbb{R})$ una función tal que:
{{< math >}}
\begin{align*}
    \lim_{x\rightarrow 0}{\left(
        1 + x + \frac{f(x)}{x}
        \right)^{1/x}} = e^3.
\end{align*}
{{< /math >}}
Calcule razonadamente $f(0)$, $f'(0)$ y $f''(0)$.
