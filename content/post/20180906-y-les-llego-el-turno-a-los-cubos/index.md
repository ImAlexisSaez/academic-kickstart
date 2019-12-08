---
title: "¡Y les llegó el turno a los cubos!"
slug: "y-les-llego-el-turno-a-los-cubos"
subtitle: "Problema 6"
summary: "Problema 6: en matemáticas, reutilizar resultados es clave."

date: 2018-09-06T05:59:39+02:00
lastmod: 2019-07-25T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Inducción", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Akram S](https://unsplash.com/@vrtlakram), disponible en [Unsplash](https://unsplash.com/photos/Y3q1WL2lNBc)."
---

**Problema 6:** Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$, 

$$
1^3 + 2^3 + \cdots + n^3=(1+2+3+\cdots+n)^2.
$$

***

Para empezar, y de cara a aliviar ligeramente la escritura en un futuro, podemos plantear de manera más compacta la identidad dada en el enunciado del presente problema como sigue

$$
1^3 + 2^3 + \cdots + n^3 = \sum_{k=1}^{n}{k^3} = \left(\sum_{k=1}^{n}{k}\right)^2 = (1+2+3+\cdots+n)^2.
$$

En esta ocasión, si optamos por una aproximación similar a la seguida en los problemas anteriores, la demostración puede volverse un tanto tediosa debido a los cálculos implicados. Es por ello que, utilizando el resultado probado en el [problema 1](/2018/07/12/probando-katex-con-un-problema-de-induccion-clasico/), la igualdad que buscamos verificar aquí sería equivalente a

$$
\sum_{k=1}^{n}{k^3} = \left(\sum_{k=1}^{n}{k}\right)^2
= \left(\dfrac{n(n+1)}{2}\right)^2
= \dfrac{n^2(n+1)^2}{4}.
$$

Una vez alcanzada una expresión más manejable para la identidad planteada, empleamos el *principio de inducción matemática*, dado en el Teorema 1.1 (ver abajo), para probarla. Rápidamente comprobamos que se verifica de manera trivial para $n=1$, puesto que

$$
1 = 1^3 = \dfrac{1^2\cdot2^2}{4} = \dfrac{4}{4} = 1.
$$

Ahora, suponemos cierta la identidad para un número dado $n\in\mathbb{N}$, con $n\geq 1$, es decir, que efectivamente se cumple que

$$
\sum_{k=1}^{n}{k^3} = \dfrac{n^2(n+1)^2}{4},
$$

y estudiamos si se satisface asimismo para $n+1$. Así pues, acto seguido, el objetivo que tenemos entre manos es verificar si es cierta la igualdad

$$
\sum_{k=1}^{n+1}{k^3} = \dfrac{(n+1)^2(n+2)^2}{4}.
$$

Apliquemos la *hipótesis de inducción* y llevemos a cabo algunas operaciones algebraicas elementales, de manera que

$$
\begin{aligned}
\sum_{k=1}^{n+1}{k^3} &= (n+1)^3 + \sum_{k=1}^{n}{k^3}\\
&= (n+1)^3 + \dfrac{n^2(n+1)^2}{4}\\
&= \dfrac{4(n+1)^3 + n^2(n+1)^2}{4}\\
&= \dfrac{(n+1)^2(4(n+1)+n^2)}{4}\\
&= \dfrac{(n+1)^2(n^2+4n+4)}{4}\\
&= \dfrac{(n+1)^2(n+2)^2}{4}
\end{aligned}
$$

y, por tanto, la identidad se verifica para $n+1$. El *principio de inducción matemática* nos permite concluir que es cierta para cada $n\in\mathbb{N}$.

***

**Teorema 1.1 (Principio de inducción matemática)**: Sea $S$ un conjunto de enteros positivos que tienen las dos propiedades siguientes:

- El número 1 pertenece al conjunto $S$.
- Si un entero $k$ pertenece a $S$, también $k+1$ pertenece a S.

Entonces todo entero positivo pertenece al conjunto $S$.

***
