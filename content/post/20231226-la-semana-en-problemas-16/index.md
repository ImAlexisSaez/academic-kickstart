---
title: "La semana en problemas (S16)"
slug: "la-semana-en-problemas-s16"
subtitle: "Problemas de funciones"
summary: "Esta semana se proponen algunos enunciados relacionados con funciones."

date: 2023-12-26T00:00:00+02:00
# lastmod: 2023-04-29T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Funciones"]
categories: ["Problemas"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Jeswin Thomas](https://unsplash.com/es/@jeswinthomas), disponible en [Unsplash](https://unsplash.com/es/fotos/hecib2an4T4)."
---

Esta semana se proponen algunos enunciados relacionados con funciones.

### Ejercicio 1

Demuestre que cualquier aplicación lineal de $\mathbb{R}$ en $\mathbb{R}$ es una función continua.

### Ejercicio 2

Sea $f$ una función real de variable real tal que, para cada $x, y\in\mathbb{R}$,
{{< math >}}
\begin{align*}
    f(x + y) = f(x) + f(y).
\end{align*}
{{< /math >}}    
    
- a) Calcule la expresión de $f(x)$, para $x\in\mathbb{Q}$.
- b) Demuestre que si $f$ es continua, entonces $f(x) = ax$ para todo $x\in\mathbb{R}$, donde $a$ es una constante.

### Ejercicio 3

Supongamos que $f:\mathbb{R}\rightarrow\mathbb{R}$, siendo $f$ no nula y cumpliendo que:
{{< math >}}
\begin{align}
    f(x + y) = f(x)\cdot f(y),\qquad \forall x, y\in\mathbb{R}.
\end{align}
{{< /math >}}
Demuestre que si $f$ es continua, existe una constante $c\in\mathbb{R}$ tal que $f(x) = e^{cx}$.

### Ejercicio 4

Demuestre que si una función $f$ real de variable real cumple que
{{< math >}}
\begin{align*}
    f(x) - f(y) \leq (x - y)^2
\end{align*}
{{< /math >}}
para cualesquiera números reales $x$ e $y$, entonces $f$ es una función constante.

### Ejercicio 5

La aplicación $f:\mathbb{Z}\rightarrow\mathbb{Z}$ cumple, para cualesquiera $m,n\in\mathbb{Z}$, que:
{{< math >}}
\begin{align*}
    f(m^2 + f(n)) = f(m)^2 + n.
\end{align*}
{{< /math >}}
Demuestre que:

- a) $f(0) = 0$
- b) $f(1) = 1$
- c) $f(n) = n$, para todo $n\in\mathbb{Z}$.

### Ejercicio 6

Sea $f:\mathbb{R}\rightarrow\mathbb{R}$ una función que satisface la relación
{{< math >}}
\begin{align*}
    f(x + y) = f(x)\cdot f(y)
\end{align*}
{{< /math >}}
para cualesquiera $x,y\in\mathbb{R}$. Demuestre que:

- a) Si $f$ se anula en un punto, entonces se anula en $\mathbb{R}$.
- b) $f$ es continua si y solo si es continua en un punto de $\mathbb{R}$.

### Ejercicio 7

Halle la condición necesaria y suficiente que debe cumplir la base $a$ de un sistema de logritmos para que en dicho sistema exista, al menos, un número igual a su logaritmo.

### Ejercicio 8

Resuelva la siguiente ecuación en $\mathbb{R}$, conocido $\alpha\in\mathbb{R}$:
{{< math >}}
\begin{align*}
    \left(\frac{1+ix}{1-ix}\right)^4 =
    \frac{1+i\tan{\frac{\alpha}{2}}}{1-i\tan{\frac{\alpha}{2}}}.
\end{align*}
{{< /math >}}

### Ejercicio 9

Dado $n\in\mathbb{N}$, se considera la ecuación
{{< math >}}
\begin{align*}
    x^{2n} - 1 = 0.
\end{align*}
{{< /math >}}
 
- a) Calcule sus soluciones en el cuerpo $\mathbb{C}$ de los números complejos.
- b) Demuestre que, para $x\neq\pm 1$ y $n > 1$, se cumple la \emph{identidad de Cotes}:
{{< math >}}
\begin{align*}
    \frac{x^{2n}-1}{x^2-1} =
    \prod_{k=1}^{n-1}{\left(x^2 - 2x\cos{\frac{k\pi}{n}} + 1\right)}.
\end{align*}
{{< /math >}}
- c) Halle el valor del producto:
{{< math >}}
\begin{align*}
    \sin{\frac{\pi}{2n}}\sin{\frac{2\pi}{2n}}\cdots\sin{\frac{(n-1)\pi}{2n}}.
\end{align*}
{{< /math >}}
