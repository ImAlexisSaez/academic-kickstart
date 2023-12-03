---
title: "La semana en problemas (S14)"
slug: "la-semana-en-problemas-s14"
subtitle: "Problemas de matrices"
summary: "Esta semana se proponen algunos enunciados relacionados con matrices, estructuras algebraicas y espacios vectoriales."

date: 2023-12-12T00:00:00+02:00
# lastmod: 2023-04-29T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Espacios vectoriales", "Estructuras algebraicas", "Matrices"]
categories: ["Problemas"]
# projects: []

image:
  focal_point: "Smart"
  caption: "Fotografía de [Jeswin Thomas](https://unsplash.com/es/@jeswinthomas), disponible en [Unsplash](https://unsplash.com/es/fotos/hecib2an4T4)."
---

Esta semana se proponen algunos enunciados relacionados con matrices, estructuras algebraicas y espacios vectoriales.

### Ejercicio 1

Considérese el conjunto $\mathcal{A}$ de las matrices cuadradas de orden tres de la forma siguiente:
{{< math >}}
\begin{align*}
    M(x) =
    \begin{bmatrix}
        1 & 0 & x \\
        0 & 1 & 0 \\
        0 & 0 & 1
    \end{bmatrix},
    \quad\text{donde } x\in\mathbb{R}.
\end{align*}
{{< /math >}}

- a) Demuestre que el conjunto $\mathcal{A}$ tiene estructura de grupo conmutativo respecto del producto de matrices.
- b) En este ejercicio se aborda el concepto de grupo, estructura básica de la teoría de conjuntos. Relacione esta con el currículo de Secundaria y dé una aplicación didáctica de algún concepto que aparezca en dicha teoría.

### Ejercicio 2

Para cada tres números enteros $x$, $y$ y $z$ se considera la matriz
{{< math >}}
\begin{align*}
    M(x, y, z) =
    \begin{bmatrix}
        1 & x & y \\
        0 & 1 & z \\
        0 & 0 & 1
    \end{bmatrix}.
\end{align*}
{{< /math >}}

- a) Pruebe que el conjunto $\mathcal{A}$ de todas estas matrices $M(x,y,z)$ es un grupo respecto del producto de matrices.
- b) Halle el conjunto $\mathcal{B}$ de todas las matrices de $\mathcal{A}$ que conmutan con todas las matrices de este grupo.
- c) Pruebe que $\mathcal{B}$ es un subgrupo de $\mathcal{A}$ isomorfo al grupo aditivo de los enteros.

### Ejercicio 3

Sea $\mathcal{M}_{\mathbb{C}}$ el conjunto de todas las matrices $2\times 2$ de la forma
{{< math >}}
\begin{align*}
    M(a, b) =
    \begin{bmatrix}
        a & -b \\
        b & a
    \end{bmatrix},
    \quad (a,b\in\mathbb{R})
\end{align*}
{{< /math >}}    

- a) Demuestre que {{< math >}}$\mathcal{M}_{\mathbb{C}}${{< /math >}} tiene estructura algebraica de cuerpo conmutativo con las operaciones usuales de suma y producto de matrices.
- b) Demuestre que {{< math >}}$\mathcal{M}_{\mathbb{C}}${{< /math >}} es isomorfo al cuerpo $\mathbb{C}$ de los números complejos, hallando el isomorfismo $f:\mathbb{C}\rightarrow\mathcal{M}_{\mathbb{C}}$ correspondiente.
- c) Utilizando el isomorfismo definido en b), calcule
{{< math >}}
\begin{align*}
    \sqrt[4]{
        \begin{bmatrix}
            -\frac{1}{2}       & -\frac{\sqrt{3}}{2} \\
            \frac{\sqrt{3}}{2} & -\frac{1}{2}
        \end{bmatrix}
    }.
\end{align*}
{{< /math >}}

### Ejercicio 4

Sea $\mathcal{M}_2(\mathbb{R})$ el espacio vectorial real de todas las matrices cuadradas de tamaño $2\times 2$, y sea $M\in\mathcal{M}_2(\mathbb{R})$ una matriz que cumple la igualdad:
{{< math >}}
\begin{align}
    M^2 - 2M - 3I = 0.\qquad (1)
\end{align}
{{< /math >}}

Sea asimismo $V$ el subespacio vectorial de $\mathcal{M}_2(\mathbb{R})$ engendrado por $M$ e $I$.

- a) Determine todas las matrices $M$ que cumplen la relación (1) y que son tales que la dimensión de $V$ es $1$.
- b) Halle todas las soluciones de la ecuación (1) de la forma
{{< math >}}
\begin{align*}
    M =
    \begin{bmatrix}
        p & q \\
        q & p
    \end{bmatrix}.
\end{align*}
{{< /math >}}
- c) Se supone que $M$ cumple (1) y es distinta de las matrices obtenidas en a). Determine, en el espacio $V$ correspondiente, todas las matrices $P$ tales que $P^2 = P$.

### Ejercicio 5

En el espacio vectorial de las matrices cuadradas de orden dos, consideramos los subespacios $L$ y $M$ siguientes:
{{< math >}}
\begin{align*}
    L & =
    \left\{
        \begin{bmatrix}
            a-b+2c & b-2c\\
            0 & 2c
        \end{bmatrix}
        :
        a,b,c\in\mathbb{R}
    \right\};\\
    M &= \mathcal{L}
    \left\{
        \begin{bmatrix}
            1 & -1\\
            0 & 0
        \end{bmatrix},
        \begin{bmatrix}
            1 & 0\\
            0 & -1
        \end{bmatrix},
        \begin{bmatrix}
            0 & 1\\
            0 & -1
        \end{bmatrix}
    \right\}.
\end{align*}
{{< /math >}}

- a) Determine el subespacio $L\cap M$ y compruebe que $L = L + M$, decidiendo además si se trata de una suma directa.
- b) Sea {{< math >}}$\mathcal{B}_L = \{U,V,W\}${{< /math >}} la base de $L$ en la que
{{< math >}}
\begin{align*}
    U = 
    \begin{bmatrix}
        1 & -1\\
        0 & 0
    \end{bmatrix},\quad
    V = 
    \begin{bmatrix}
        1 & 0\\
        0 & -1
    \end{bmatrix},\quad
    W = 
    \begin{bmatrix}
        1 & 1\\
        0 & 1
    \end{bmatrix}
\end{align*}
{{< /math >}}
y sea $f:L\rightarrow L$ la aplicación lineal dada por $f(U) = V$, $f(V) = U$ y $f(W) = W$. Halle la matriz de $f$ respecto de la base $\mathcal{B}_L$ y los subespacios $ker(f)$ e $img(f)$.

### Ejercicio 6

En el espacio vectorial $\mathcal{M}_2(\mathbb{R})$ de las matrices cuadradas de orden $2$ se considera la base
{{< math >}}
\begin{align*}
    \mathcal{B} =
    \left\{
    \begin{bmatrix}
        1 & 0 \\
        0 & 2
    \end{bmatrix},
    \begin{bmatrix}
        0 & 2 \\
        0 & 0
    \end{bmatrix},
    \begin{bmatrix}
        0 & 0 \\
        2 & 1
    \end{bmatrix},
    \begin{bmatrix}
        -1 & 0 \\
        2  & 0
    \end{bmatrix}
    \right\}
\end{align*}
{{< /math >}}
y los conjuntos
{{< math >}}
\begin{align*}
    S & = \{A\in\mathcal{M}_2(\mathbb{R}: A^t = A)\} \\
    U & =
    \left\{
    A\in\mathcal{M}_2(\mathbb{R}):
    A\cdot
    \begin{bmatrix}
        1 & 2 \\
        2 & 4
    \end{bmatrix}
    =
    \begin{bmatrix}
        0 & 0 \\
        0 & 0
    \end{bmatrix}
    \right\}                                         \\
    V & = \mathcal{L}
    \left\{
    \begin{bmatrix}
        1 & 1 \\
        0 & 1
    \end{bmatrix},
    \begin{bmatrix}
        1 & 1 \\
        0 & 0
    \end{bmatrix},
    \begin{bmatrix}
        1 & 1 \\
        0 & 2
    \end{bmatrix}
    \right\}
\end{align*}
{{< /math >}}
    
- a) Demuestre que $U$ es un subespacio de $\mathcal{M}_2(\mathbb{R})$.
- b) Calcule ecuaciones paramétricas e implícitas de $S\cap V$ respecto de la base canónica de $\mathcal{M}_2(\mathbb{R})$.
- c) Dé ecuaciones paramétricas e implícitas de $U$ respecto de la base $\mathcal{B}$.
- d) Razone la veracidad o falsedad de las siguientes afirmaciones, en las que $W$ es un espacio vectorial de dimensión $2021$:
    + i) En $W$ puede existir un sistema generador con $2022$ vectores.
    + ii) $2020$ vectores distintos de $W$ siempre son linealmente indpendientes.
