---
title: "Moviendo cifras de posición en un número"
slug: "moviendo-cifras-de-posicion-en-un-numero"
subtitle: "Problema 32"
summary: "Problema 32: siempre conviene empezar con ejemplos sencillos."

date: 2018-12-08T05:59:39+02:00
lastmod: 2019-07-30T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Problemas", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Purnomo Capunk](https://unsplash.com/@capunk77), disponible en [Unsplash](https://unsplash.com/photos/KZC7BJo0Cl0)."
---

**Problema 32:** Encuentra el número natural más pequeño con $6$ como cifra de las unidades de manera que si el $6$ se mueve al principio, el número queda multiplicado por cuatro.

***

Antes de abordar la resolución del ejercicio propiamente en sí, analicemos el movimiento del $6$ con un par de números en concreto para intentar detectar posibles patrones.

Por ejemplo, un número como el $326$ es cierto que podemos escribirlo como 

$$
326 = 320 + 6 = 32\cdot10 + 6.
$$

Al mover la cifra de las unidades al principio queda entonces el número $632$, que podemos escribir como 

$$
632 = 600 + 32 = 6\cdot 10^2 + 32.$$

La idea, como vemos, es intentar aislar la cifra $6$ de alguna forma posible, que luego nos permita construir una ecuación que satisfaga las condiciones impuestas en el enunciado del ejercicio.

Consideremos ahora el número $8886$, actuando como antes, lo podemos escribir como $8886 = 8880 + 6 = 888\cdot10 + 6 = 10n + 6$, donde $n = 888$. Al mover la cifra de las unidades al principio del número queda $6888$, que podemos escribir como $6888 = 6000 + 888 = 6\cdot 10^3 + n = 6\cdot 10^m + n$, con $m + 1$ como número de dígitos del número inicial.

Así pues, el número inicial vamos a denotarlo como $10n + 6$, mientras que el resultado de llevar a cabo el movimiento de la cifra de las unidades al principio del número será $6\cdot10^m + n$. Como el enunciado marca que este último es cuatro veces más grande que el considerado en principio, planteamos así la ecuación

$$
4(10n + 6) = 6\cdot10^m + n,
$$

o, equivalentemente, $39n = 6\cdot10^m - 24$, ecuación diofántica que podemos simplificar por $3$, quedando pues 

$$
13n = 2\cdot10^m - 8.
$$ 

Ahora bien, como el miembro derecho de esta última ecuación es un número par y $13$ es un número impar, necesariamente $n$ ha de ser un número par, es decir, de la forma $n=2x$, para algún $x\in\mathbb{Z}$. Sustituyendo arriba y despejando la variable queda

$$
\begin{aligned}
13(2x) &= 2\cdot10^m - 8,\\
13x &= 10^m - 4,\\
x &= \dfrac{10^m - 4}{13}.
\end{aligned}
$$

Podemos ahora introducir la expresión en una calculadora científica y generar una tabla de valores para ella en función de $m$, quedándonos con el primero para el cual $x$ sea un número natural. Alternativamente, podemos actuar por tanteo, dividiendo las potencias de $10$ entre $13$ hasta dar con la primera en la que el resto de esta operación matemática sea $4$. Así,

$$
\begin{aligned}
10 &= 13\cdot 0 + 10,\\
100 &= 13\cdot 7 + 9,\\
1000 &= 13\cdot 76 + 12,\\
10000 &= 13\cdot 769 + 3,\\
100000 &= 13\cdot 7692 + 4,
\end{aligned}
$$

por tanto $x = 7692$, de manera que $n = 2x = 15384$, es decir, el número que buscamos es, recordando la expresión que generamos al principio de la resolución del ejercicio, $10n + 6 = 153846$ (y es el menor por ser el primero que satisface la ecuación diofántica). Como nota anecdótica, si estuviéramos interesados en hallar el siguiente valor que cumple con los dictados del enunciado, seguiríamos dividiendo potencias de $10$, encontrando que el siguiente que verifica la condición de interés es $x = 76927692$.

Alternativamente, veamos cómo resolver la ecuación $13x = 10^m - 4$ de forma técnica. Tal y como viene planteada dicha ecuación, es cierto que $10^m - 4$ es múltiplo de $13$, por lo que hemos de resolver la ecuación de congruencia $10^m - 4\equiv 0\pmod{13}$, o, equivalentemente, $10^m\equiv 4\pmod{13}$.

Ahora bien, como $10\equiv(-3)\pmod{13}$, entonces 

$$
10^2\equiv (-3)^2\pmod{13}\equiv 9\pmod{13}\equiv (-4)\pmod{13},
$$ 

y así podemos escribir

$$
\begin{aligned}
10^m\equiv 4\pmod{13}&\Leftrightarrow 10^2\cdot10^{m-2}\equiv 4\pmod{13}\\
&\Leftrightarrow 10^{m - 2}\equiv (-1)\pmod{13}.
\end{aligned}
$$

Como $13$ es un número primo y $mcd(10, 13) = 1$, el *Pequeño Teorema de Fermat* afirma que $10^{12}\equiv 1\pmod{13}$. La expresión que figura en la ecuación previa no se ajusta exactamente a la anterior estructura, pero si la elevamos al cuadrado queda

$$
(10^{m-2})^2\equiv (-1)^2\pmod{13}\Leftrightarrow 10^{2m-4}\equiv 1\pmod{13},
$$

e, igualando exponentes, $2m-4 = 12$, de donde $m = 8$. Este valor, lo introduciríamos en la expresión que nos permite calcular el número $x$, hallando entonces $76927692$, cifra que sabemos no es la menor. Hemos de ser cautos aquí, puesto que el resultado asociado a *Fermat* en ningún momento afirma que el exponente dado es el menor para el que se cumple que sea congruente con uno módulo $13$. No obstante, de haber uno más pequeño, sí que será cierto que dividirá a $12$.

Por tanto, si probamos con $10^6$, encontramos que $10^6\equiv 1\pmod{13}$, e, igualando como antes exponentes, $2m-4=6$, de donde $m=5$, llegando así a la primera solución que encontramos por tanteo arriba. ¿Podría haber todavía alguna menor? Como $10^3\equiv (-1)\pmod{13}$, estamos en condiciones de descartar esa situación. Por tanto, el asociado a $m=5$ es el valor más pequeño para el que se satisface la ecuación de congruencia lineal, llevándonos a la solución $x=7692$ y permitiéndonos concluir el ejercicio tal y como hicimos por el método de tanteo.
