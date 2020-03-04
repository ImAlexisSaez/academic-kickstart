---
title: Sucesiones
linktitle: Sucesiones
toc: true
type: docs
date: "2019-10-14T00:00:01+01:00"
lastmod: "2020-03-04T00:00:01+01:00"
math: true
draft: false
menu:
  enunciados:
    parent: Enunciados
    weight: 5

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 5
---

## I. Límites

---

**Ejercicio 1.1:** Calcula

$$
\lim_{n\rightarrow\infty}{\frac{\ln{(8n^4 + 3n^2 + 5)}}{\ln{(5n^3 + n^2 + n - 4)}}}.
$$

---

**Ejercicio 1.2:** Calcula

$$
\lim_{n\rightarrow\infty}{\frac{2^n + 5}{5^n + 5}}.
$$

---

**Ejercicio 1.3:** Calcula

$$
\lim_{n\rightarrow\infty}{\frac{(3n^4 + n^2 - 3)(\cos{\left(\frac{1}{n}\right)} - 1)}{2n^2}}.
$$

---

**Ejercicio 1.4:** Calcula

$$
\lim_{n\rightarrow\infty}{\frac{n}{3}\ln{((n+a)(n+b)(n+c))} - \ln{(n^n)}}.
$$

---

**Ejercicio 1.5:** Calcula

$$
\lim_{n\rightarrow\infty}{\frac{2n + (-1)^n(n+2)}{7n+3}}.
$$

---

**Ejercicio 1.6:** Calcula

$$
\lim_{n\rightarrow\infty}{\frac{\sqrt{1} + \sqrt{2} + \sqrt{3} + \cdots + \sqrt{n}}{n\sqrt{n}}}.
$$

---

**Ejercicio 1.7:** Calcula

$$
\lim_{n\rightarrow\infty}{\sqrt[n]{\left(1+\frac{2}{n}\right)\left(1+\frac{4}{n}\right)\left(1+\frac{6}{n}\right)\cdots\left(1+\frac{2n}{n}\right)}}.
$$

---

**Ejercicio 1.8:** Calcula

$$
\lim_{n\rightarrow\infty}{\sqrt[n]{(an+b)(an+2b)(an+3b)\cdots(an+nb)}}.
$$

---

**Ejercicio 1.9:** Demuestra que la siguiente sucesión tiene límite y calcúlalo:

$$
\sqrt{1}, \sqrt{1 + \sqrt{1}}, \sqrt{1 + \sqrt{1 + \sqrt{1}}},\ldots.
$$

---

**Ejercicio 1.10:** Demuestra que la sucesión

$$
a_1 = \sqrt{k}, a_2 = \sqrt{k + \sqrt{k}}, a_3 = \sqrt{k + \sqrt{k + \sqrt{k}}},\ldots
$$

con $k > 0$, es convergente y halla su límite.

---

**Ejercicio 1.11:** Es fácil demostrar que 

$$
3 = \sqrt{6 + \sqrt{6 + \sqrt{6 + \cdots}}}.
$$ 

¿Para cuántos valores naturales $x$, tales que $1\leq x\leq 1000$, se cumple que 

$$
\sqrt{x + \sqrt{x + \sqrt{x + \cdots}}}
$$ 

es un número natural?

---

**Ejercicio 1.12:** Sea 

$$
x = \sqrt{a + \sqrt{a + \sqrt{a + \cdots}}}.
$$

- (a) Halla $x$.
- (b) Halla una relación tal que a cada número natural le corresponde un valor $a$ tal que $x$ sea racional.
- (c) Demuestra que, para cada número natural $n$, $x = n+1$.

---

**Ejercicio 1.13:** Dada la sucesión 

$$
x_{n+1} = 1 - \sqrt{1 - x_n},
$$ 

de manera que $0 < x_1 < 1$, estudia su convergencia y calcula 

$$
\lim_{n\rightarrow\infty}{\frac{x_{n+1}}{x_n}}.
$$

---


## II. Progresiones aritméticas

---

**Ejercicio 2.1:** *(Comunidad Valenciana (2016))* Con un solo corte recto puedes dividir un pastel circular en dos partes. Un segundo corte, que atraviese al primero, producirá probablemente cuatro partes, y un tercer corte puede llegar a producir siete partes. ¿Cuál es el mayor número de trozos que puedes lograr con seis cortes rectos? ¿Y, en general, cuántos pedazos de tarta se obtienen con $n$ cortes? ([Discusión](/2019/10/14/enunciados-propuestos-x/))

---

**Ejercicio 2.2:** Halla la suma de todas las fracciones irreducibles de denominador $3$ comprendidas entre $3$ y $6$. Generaliza el resultado para la suma de todas las fracciones irreducibles de denominador $3$ comprendidas entre los enteros $m$ y $n$, con $m < n$. ([Discusión](/2019/11/18/enunciados-propuestos-xxv/))

---

**Ejercicio 2.3:** Disponemos los números naturales en la forma siguiente:

$$
\begin{aligned}
&    & &    & &    & &  1 & &    & &    & &\\\\ &    & &    & &  2 & &  3 & &  4 & &    & &\\\\ &    & &  5 & &  6 & &  7 & &  8 & &  9 & &\\\\ & 10 & & 11 & & 12 & & 13 & & 14 & & 15 & & 16
\end{aligned}
$$

- (a) Calcula la suma $S_n$ de los números situados en la $n$-ésima fila.
- (b) Halle
    $$
    \lim_{n\rightarrow\infty}{\left(\sqrt[3]{S_{n+1}} - \sqrt[3]{S_n}\right)}.
    $$

---

## III. Progresiones geométricas

---

**Ejercicio 3.1:** Sea la progresión geométrica $1,3,9,27,81,\ldots$.

- (a) ¿Cuál es el término de lugar $n$? Demuestra que las diferencias primeras también forman una progresión geométrica. Generaliza el resultado para las diferencias de cualquier orden.
- (b) Calcula las siguientes sumas. ¿Qué forma toman cuando se hace $x=1$? ¿Cuál es el verdadero valor en $x=1$?

$$
\begin{aligned}
A_n &= x + x^2 + x^3 + \cdots + x^n,\\\\ B_n &= 1 + 2x + 3x^2 + \cdots + nx^{n-1}.
\end{aligned}
$$
    
- (c\) Responde a las mismas preguntas del apartado anterior para las sumas

$$
\begin{aligned}
C_n &= 1 + 3x^2 + 5x^4 + \cdots + (2n+1)x^{2n},\\\\ D_n &= 1 + 4x + 9x^2 + \cdots + n^2x^{n-1}.
\end{aligned}
$$

---
