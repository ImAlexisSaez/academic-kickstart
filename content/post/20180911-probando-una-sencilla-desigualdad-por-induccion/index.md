---
title: "Probando una sencilla desigualdad por inducción"
slug: "probando-una-sencilla-desigualdad-por-induccion"
subtitle: "Problema 8"
summary: "Problema 8: no solo de igualdades vive el principio de inducción matemática."

date: 2018-09-11T05:59:39+02:00
lastmod: 2019-07-25T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Inducción", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Daniel von Appen](https://unsplash.com/@daniel_von_appen), disponible en [Unsplash](https://unsplash.com/photos/KqKruA8nMdE)."
---

**Problema 8:** Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$, 

$$
n<2^n.
$$

***

Hagamos uso del *principio de inducción matemática*, dado en el teorema 1.1 (ver abajo), para demostrar la desigualdad planteada en el enunciado del problema. Enseguida apreciamos que esta se cumple de forma trivial para $n=1$, ya que

$$
1 < 2^1 = 2.
$$

Ahora, asumimos cierta la desigualdad para un $n\in\mathbb{N}$ dado, con $n\geq 1$, es decir, que efectivamente se cumple que

$$
n < 2^n,
$$

y estudiamos si se verifica asimismo para $n+1$. Así pues, el objetivo pasa ahora por demostrar que se satisface la siguiente desigualdad

$$
n+1 < 2^{n+1}.
$$

Apoyándonos en que $n+1\leq n+n = 2n$, para cada $n\in\mathbb{N}$, (siendo una desigualdad estricta cuando $n>1$) y en la *hipótesis de inducción*, tenemos que

$$
\begin{aligned}
n+1 &\leq n+n\\
&= 2n\\
&< 2\cdot 2^n\\
&= 2^{n+1},
\end{aligned}
$$

es decir, la desigualdad se verifica para $n+1$. El *principio de inducción matemática* nos permite concluir que es cierta para cada $n\in\mathbb{N}$.

***

**Teorema 1.1 (Principio de inducción matemática)**: Sea $S$ un conjunto de enteros positivos que tienen las dos propiedades siguientes:

- El número 1 pertenece al conjunto $S$.
- Si un entero $k$ pertenece a $S$, también $k+1$ pertenece a S.

Entonces todo entero positivo pertenece al conjunto $S$.

***
