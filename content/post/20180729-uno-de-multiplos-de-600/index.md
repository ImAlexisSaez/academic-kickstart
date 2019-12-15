---
title: "Uno de múltiplos... ¡de 600!"
slug: "uno-de-multiplos-de-600"
subtitle: "Problema 3"
summary: "Problema 3: la clave está en los productos notables."

date: 2018-07-29T05:59:39+02:00
lastmod: 2018-07-29T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Inducción", "Problemas", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Amelie Ohlrogge](https://unsplash.com/@pirye), disponible en [Unsplash](https://unsplash.com/photos/uu0cOMPdM2g)."
---

En el presente artículo abordaremos en detalle un interesante problema propuesto en la convocatoria de oposiciones de Andalucía, de este mismo año 2018, para la especialidad de matemáticas.

***

**Problema 3:** Demuestra que todos los términos de la sucesión $\\{a_n\\}\_{n>2}$ son múltiplos de $600$, siendo 

$$
a_n = (n^2-1)(n^2+1)(n^4-16)n^2.
$$

***

Es más que razonable que, en una primera aproximación a la resolución de este problema, estemos tentados a probar la afirmación dada en el enunciado utilizando el *principio de inducción matemática*. Esta senda nos llevaría a definir, seguramente, $P(n)$ de forma similar a la siguiente: existe $k\in\mathbb{Z}$ tal que si $n>2$, entonces 

$$
a_n = (n^2-1)(n^2+1)(n^4-16)n^2 = 600k.
$$

El *caso base*, $P(3)$ en esta ocasión, comprobamos rápidamente que se satisface, ya que

$$
\begin{aligned}
a_3 &= (3^2-1)(3^2+1)(3^4-16)3^2\\\\ &= 2^3\cdot (2\cdot 5)\cdot (5\cdot 13)\cdot 3^2\\\\ &= 2^3\cdot 3\cdot 5^2\cdot (2\cdot 3\cdot 13)\\\\ &= 600\cdot(2\cdot 3\cdot 13),
\end{aligned}
$$

y bastaría tomar $k = 2\cdot 3\cdot 13 = 78$ para concluir que $a_3$ es un múltiplo de $600$.

Sin embargo, es posible que nuestro barco escore a la hora de abordar el *paso inductivo*. Recordemos que ahora hemos de mostrar que si $P(n)$ se cumple, para un $n>2$, entonces asimismo se satisface $P(n+1)$, cuya expresión es 

$$
a_{n+1} = ((n+1)^2-1)((n+1)^2+1)((n+1)^4-16)(n+1)^2.
$$ 

A primera vista, es ciertamente complejo utilizar la información disponible en la *hipótesis de inducción*, $P(n)$, para verificar $P(n+1)$. 

En este momento, deberíamos descartar por completo la opción de desarrollar ambas expresiones para compararlas, puesto que entre manos tenemos un producto de cuatro polinomios, donde uno de los cuales es de grado considerable. Es más, no quiero siquiera empezar a imaginar la posible cantidad de errores de cálculo en los que podemos caer desarrollando la expresión de $P(n+1)$. Estos problemas están diseñados para resolverse en un período de tiempo razonable, hecho que nos debe invitar a considerar estrategias de resolución alternativas a la propuesta en primer lugar.

Así pues, a continuación, optaremos por llevar a cabo un enfoque diferente. Si estudiamos con detalle la expresión de $a_n$, enseguida apreciaremos que en ella aparecen un par de términos de la forma $a^2 - b^2$, concretamente $n^2 - 1$ y $n^4 - 16$. Esta situación puede hacernos sospechar que la clave pase por factorizar la expresión de $a_n$, utilizando para ello la identidad notable $a^2 - b^2 = (a+b)(a-b)$. Aplicándola, podemos escribir

$$
\begin{aligned}
n^2-1&=(n+1)(n-1),\\\\ n^4-16&=(n^2+4)(n^2-4)=(n^2+4)(n+2)(n-2),
\end{aligned}
$$

quedando entonces

$$
a_n = (n+1)(n-1)(n^2+1)(n^2+4)(n+2)(n-2)n^2.
$$

No parece que estemos avanzando en la buena dirección. Sin embargo, hay cuatro términos que habrán captado nuestra atención seguramente: $(n+1)$, $(n-1)$, $(n+2)$ y $(n-2)$. Quizá ayude reescribir $a_n$ de la siguiente manera:

$$
a_n = (n-2)(n-1)(n+1)(n+2)(n^2+1)(n^2+4)n^2.
$$

Nos faltaría una $n$ entre los términos $(n-1)$ y $(n+1)$ para tener en la primera parte de la expresión de $a_n$ cinco números naturales consecutivos, ya que, por hipótesis, $n>2$. No obstante, en realidad sí que tenemos a nuestro alcance dicha $n$, pues podemos escribir el término $n^2=n\cdot n$, y nos quedaría entonces que 

$$
a_n = (n-2)(n-1)n(n+1)(n+2)n(n^2+1)(n^2+4).
$$

Esta situación nos invita a escribir $a_n = u\cdot v$, con

$$
\begin{aligned}
u&=(n-2)(n-1)n(n+1)(n+2),\\\\ v&=n(n^2+1)(n^2+4),
\end{aligned}
$$

y estudiar cada una de sus partes por separado

Tal y como hemos indicado arriba, como $n>2$, en $u$ observamos el producto de cinco números naturales consecutivos, por lo que siempre seremos capaces de encontrar entre ellos un múltiplo de $2$, uno de $3$, uno de $4$ y uno de $5$. Es decir, sabemos que existe $k\in\mathbb{N}$ de manera que podemos escribir la factorización en números primos de $u$ como 

$$
\begin{aligned}
u &= 2\cdot3\cdot4\cdot5\cdot k \\\\ &= 2^3\cdot 3\cdot 5\cdot k\\\\ &= 120\cdot k,
\end{aligned}
$$

y, por tanto, $u$ es un múltiplo de $120$. 

Bastaría ahora que comprobásemos que 

$$
v=n(n^2+1)(n^2+4)
$$ 

es múltiplo de $5$ para que el enunciado del ejercicio propuesto se satisfaga. Llevaremos a cabo tal tarea utilizando restos potenciales módulo 5, de manera que analizaremos, acto seguido, todos y cada uno de los casos posibles que puede presentar $n$:

- Si $n\equiv 0\pmod{5}$, trivialmente $v$ es múltiplo de $5$, al ser $n$ uno de sus factores.
- Si $n\equiv 1\pmod{5}$, $(n^2+4)\equiv (1+4)\pmod{5}\equiv 0\pmod{5}$ y, por tanto, $v$ es múltiplo de 5, al ser $(n^2+4)$ uno de sus factores.
- Si $n\equiv 2\pmod{5}$, $(n^2+1)\equiv (4+1)\pmod{5}\equiv 0\pmod{5}$ y, por tanto, $v$ es múltiplo de 5, al ser $(n^2+1)$ uno de sus factores.
- Si $n\equiv 3\pmod{5}$, $(n^2+1)\equiv (9+1)\pmod{5}\equiv 0\pmod{5}$ y, por tanto, $v$ es múltiplo de 5, al ser $(n^2+1)$ uno de sus factores.
- Si $n\equiv 4\pmod{4}$, $(n^2+4)\equiv (16+4)\pmod{5}\equiv 0\pmod{5}$ y, por tanto, $v$ es múltiplo de 5, al ser $(n^2+4)$ uno de sus factores.

Así pues, como $u$ es múltiplo de $120$, $v$ es múltiplo de $5$ y $120\cdot 5=600$, podemos concluir que $a_n$, cuando $n>2$, es múltiplo de $600$.
