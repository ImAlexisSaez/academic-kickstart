---
title: "Múltiplos de 21 en Ceuta"
slug: "multiplos-de-21-en-ceuta"
subtitle: "Problema 9"
summary: "Problema 9: combinando teoría de números e inducción."

date: 2018-09-13T05:59:39+02:00
lastmod: 2018-09-13T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Inducción", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Paula Vermeulen](https://unsplash.com/@paulavermeulen), disponible en [Unsplash](https://unsplash.com/photos/URjZkhqsuBk)."
---

En el presente artículo abordaremos con sumo detalle un problema propuesto en la convocatoria de oposiciones de Ceuta, de este mismo año 2018, para la especialidad de matemáticas.

***

**Problema 9:** Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$, $4^{n+1} + 5^{2n-1}$ es un múltiplo de 21.

***

Para empezar, decimos que un número $m$ es múltiplo de 21 cuando existe un número $k\in\mathbb{Z}$ de manera que podemos escribir $m=21k$. Así, podemos redactar de nuevo el enunciado del ejemplo como sigue: demuestra que, para cada número $n\in\mathbb{N}$, existe un número $k\in\mathbb{Z}$ tal que 

$$
4^{n+1} + 5^{2n-1}=21k.
$$

Utilicemos el *principio de inducción matemática*, dado en el teorema 1.1 (ver abajo), para comprobar la anterior identidad. Rápidamente apreciamos que se cumple de manera trivial para $n=1$, puesto que 

$$
4^{1+1}+5^{2-1} = 4^2 + 5 = 16 + 5 = 21,
$$ 

y bastaría entonces que tomásemos $k=1$ para constatar que es múltiplo de 21.

Acto seguido, suponemos cierta la igualdad para un $n\in\mathbb{N}$ dado, con $n\geq 1$, es decir, que efectivamente se cumple que existe un número $k\in\mathbb{Z}$ tal que 

$$
4^{n+1}+5^{2n-1}=21k,
$$

y estudiamos si se satisface asimismo para $n+1$. De esta manera, nuestro objetivo será demostrar que existe un $k^\prime\in\mathbb{Z}$ tal que se verifica la siguiente identidad,

$$
4^{n+2} + 5^{2n+1} = 21k^\prime.
$$

Podemos escribir el miembro izquierdo de la ecuación anterior como 

$$
4^{n+2} + 5^{2n+1} = 4\cdot4^{n+1} + 5^{2n+1},
$$

y utilizar, acto seguido, la *hipótesis de inducción*, que afirma que existe $k\in\mathbb{Z}$ tal que $4^{n+1} + 5^{2n-1}=21k$. La clave reside en despejar adecuadamente el término que nos interesa de dicha hipótesis. Así, como $4^{n+1} + 5^{2n-1}=21k$, entonces $4^{n+1}=21k - 5^{2n-1}$ y, sustituyendo arriba, tenemos que

$$
\begin{aligned}
4\cdot4^{n+1} + 5^{2n+1} &= 4(21k - 5^{2n-1}) + 5^{2n+1}\\\\ &= 4\cdot 21k - 4\cdot 5^{2n-1} + 5^{2n+1}\\\\ &= 4\cdot 21k - 4\cdot 5^{2n-1} + 5^2\cdot5^{2n-1}\\\\ &= 4\cdot 21k + 5^{2n-1}(5^2-4)\\\\ &= 4\cdot 21k + 21\cdot5^{2n-1}\\\\ &= 21(4k + 5^{2n-1})\\\\ &= 21k^\prime,
\end{aligned}
$$

con $k^\prime=4k + 5^{2n-1}\in\mathbb{Z}$ y, por tanto, la identidad se verifica para $n+1$. El *principio de inducción matemática* nos permite concluir que es cierta para cada $n\in\mathbb{N}$.

***

**Teorema 1.1 (Principio de inducción matemática)**: Sea $S$ un conjunto de enteros positivos que tienen las dos propiedades siguientes:

- El número 1 pertenece al conjunto $S$.
- Si un entero $k$ pertenece a $S$, también $k+1$ pertenece a S.

Entonces todo entero positivo pertenece al conjunto $S$.

***
