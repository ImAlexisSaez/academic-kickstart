---
title: "¿Será múltiplo de treinta o no?"
slug: "sera-multiplo-de-treinta-o-no"
subtitle: "Problema 31"
summary: "Problema 31: el Pequeño Teorema de Fermat siempre tan útil."

date: 2018-12-05T05:59:39+02:00
lastmod: 2019-07-30T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Pequeño Teorema de Fermat", "Problemas", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Nathan Duck](https://unsplash.com/@nvte), disponible en [Unsplash](https://unsplash.com/photos/KnLj3o9A66E)."
---

**Problema 31:** Demuestra que $a^{25} - a$ es divisible entre $30$ para cualquier entero $a$.

***

Hemos de ser capaces de probar que $(a^{25} - a)\equiv 0\pmod{30}$ para todo $a\in\mathbb{Z}$. Como $30=2\cdot3\cdot5$, veremos si la expresión es múltiplo de cada uno de los factores primos de $30$ y, en caso afirmativo, por las propiedades de las congruencias, estaremos en condiciones de concluir que asimismo será múltiplo de $30$.

Vamos a apoyarnos en el corolario del *Pequeño Teorema de Fermat*, que afirma que si $p$ es un número primo y $a\in\mathbb{Z}$, entonces $a^p\equiv a\pmod{p}$. Así, para $p=5$,

$$
\begin{aligned}
a^{25} &= (a^5)^5\\
&\equiv a^5\pmod{5}\\
&\equiv a\pmod{5},
\end{aligned}
$$

de manera que $(a^{25} - a)\equiv 0\pmod{5}$, esto es, la expresión es múltiplo de $5$. Procediendo de manera similar, para $p=3$,

$$
\begin{aligned}
a^{25} &= a\cdot (a^8)^3\\
&\equiv (a\cdot a^8)\pmod{3}\\
&\equiv (a^3)^3\pmod{3}\\
&\equiv a^3\pmod{3}\\
&\equiv a\pmod{3},
\end{aligned}
$$

y, por tanto, $(a^{25} - a)\equiv 0\pmod{3}$, es decir, la expresión es asimismo múltiplo de $3$. Finalmente, para $p=2$,

$$
\begin{aligned}
a^{25} &= a\cdot(a^{12})^2\\
&\equiv (a\cdot a^{12})\pmod{2}\\
&\equiv (a\cdot (a^6)^2)\pmod{2}\\
&\equiv (a\cdot a^6)\pmod{2}\\
&\equiv (a\cdot(a^3)^2)\pmod{2}\\
&\equiv (a\cdot a^3)\pmod{2}\\
&\equiv a^4\pmod{2}\\
&\equiv (a^2)^2\pmod{2}\\
&\equiv a^2\pmod{2}\\
&\equiv a\pmod{2},
\end{aligned}
$$

y, por consiguiente, $(a^{25} - a)\equiv 0\pmod{2}$, esto es, la expresión también es múltiplo de $2$. Al ser múltiplo de $2$, $3$ y $5$, por las propiedades de las congruencias podemos afirmar que $(a^{25} - a)\equiv 0\pmod{30}$, es decir, la expresión es múltiplo de $30$.

A modo de nota final, aunque nos hubiese dado la impresión de que escoger la descomposición $30=5\cdot 6$ habría acelerado la resolución de este ejercicio, hemos de ser cautos, pues $6$ no es un número primo, requisito indispensable para aplicar el resultado que nos ha permitido llevar a buen puerto este problema. En este último caso, habría sido necesario recurrir a otras herramientas para verificar la propiedad propuesta en el enunciado del ejercicio.
