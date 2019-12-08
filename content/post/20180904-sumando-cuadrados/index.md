---
title: "Sumando cuadrados"
slug: "sumando-cuadrados"
subtitle: "Problema 5"
summary: "Problema 5: seguimos reforzando el Principio de inducción matemática."

date: 2018-09-04T05:59:39+02:00
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
  caption: "Fotografía de [Melanie Hughes](https://unsplash.com/@nutsycoco), disponible en [Unsplash](https://unsplash.com/photos/AY-4rm_WBB4)."
---

**Problema 5:** Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$, 

$$
\sum_{k=1}^{n}{k^2} = \dfrac{n(n+1)(2n+1)}{6}.
$$

***

Ante nosotros se plantea la tarea de demostrar una propiedad (la identidad sugerida arriba), que supuestamente se satisface para una sucesión de índices enteros que conforman un conjunto cuyo cardinal es infinito ($n\in\mathbb{N}$, con $n\geq 1$, en este caso). Entre las diferentes estrategias que tenemos a nuestra disposición para abordar esta empresa, el *principio de inducción matemática*, dado en el Teorema 1.1 (ver abajo), quizá sea el instrumento más aconsejable para una primera aproximación a la resolución del problema.

Así pues, la manera en la que ahora procederemos será ciertamente similar a la seguida en una [entrada anterior](/2018/07/12/probando-katex-con-un-problema-de-induccion-clasico/). Para empezar, a simple vista, podemos apreciar rápidamente que la igualdad se satisface de forma trivial para $n=1$, puesto que 

$$
1 = \sum_{k=1}^{1}{k^2} = \dfrac{1\cdot2\cdot3}{6} = 1.
$$

Acto seguido, asumimos verdadera la identidad para un cierto $n\in\mathbb{N}$, con $n\geq 1$, es decir, que efectivamente se verifica que 

$$
\sum_{k=1}^{n}{k^2} = \dfrac{n(n+1)(2n+1)}{6},
$$ 

y estudiamos si se satisface asimismo para $n+1$. Así pues, ahora comprobaremos si se cumple la igualdad 

$$
\sum_{k=1}^{n+1}{k^2} = \dfrac{(n+1)(n+2)(2n+3)}{6}.
$$

Para ello, apliquemos la *hipótesis de inducción* y llevemos a cabo algunas operaciones algebraicas elementales, de manera que

$$
\begin{aligned}
\sum_{k=1}^{n+1}{k^2} &= (n+1)^2 + \sum_{k=1}^{n}{k^2}\\
& = (n+1)^2 + \dfrac{n(n+1)(2n+1)}{6}\\
& = \dfrac{6(n+1)^2 + n(n+1)(2n+1)}{6}\\
& = \dfrac{(n+1)(6(n+1) + n(2n+1))}{6}\\
& = \dfrac{(n+1)(2n^2+7n+6)}{6}\\
& = \dfrac{(n+1)(n+2)(2n+3)}{6},
\end{aligned}
$$

y, por tanto, la identidad se verifica para $n+1$. El *principio de inducción matemática* nos permite concluir que es cierta para cada $n\in\mathbb{N}$.

***

**Teorema 1.1 (Principio de inducción matemática)**: Sea $S$ un conjunto de enteros positivos que tienen las dos propiedades siguientes:

- El número 1 pertenece al conjunto $S$.
- Si un entero $k$ pertenece a $S$, también $k+1$ pertenece a S.

Entonces todo entero positivo pertenece al conjunto $S$.

***
