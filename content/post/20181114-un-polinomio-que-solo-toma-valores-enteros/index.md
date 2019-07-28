---
title: "Un polinomio que solo toma valores enteros"
slug: "un-polinomio-que-solo-toma-valores-enteros"
subtitle: "Problema 25"
summary: "Problema 25: el retorno del Pequeño Teorema de Fermat."

date: 2018-11-14T05:59:39+02:00
lastmod: 2019-07-28T00:00:01+02:00

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
  caption: "Fotografía de [Paweł Czerwiński](https://unsplash.com/@pawel_czerwinski), disponible en [Unsplash](https://unsplash.com/photos/pGEClFRk73o)."
---

**Problema 25:** Para cada entero no negativo $n$, se considera el valor $P(n)$, 

$$
P(n) = \dfrac{n^7}{7} + \dfrac{n^3}{3} + \dfrac{11n}{21}.
$$

- (a) Demuestra que en $\mathbb{Z}_3$ y en $\mathbb{Z}_7$ se verifica que $3n^7 + 7n^3 + 11n = 0$.
- (b) Demuestra que $P(n)$ es un entero.

***

Para el apartado (a), recordemos que el conjunto finito $\mathbb{Z}_3 = \\{\overline{0}, \overline{1}, \overline{2}\\}$, que es un cuerpo al ser $3$ un número primo, viene definido como el conjunto cociente de $\mathbb{Z}$ por la relación de equivalencia dada por la congruencia módulo $3$. Así, como $3\equiv 0\pmod{3}$, para cada entero no negativo $n$, $3n^7\equiv 0\pmod{3}$. Por otro lado, al ser $3$ un número primo, sabemos, por el corolario del *Pequeño Teorema de Fermat*, que $n^3\equiv n\pmod{3}$, para cada entero no negativo $n$, por lo que $7n^3\equiv 7n\pmod{3}\equiv n\pmod{3}$. Por tanto,

$$
\begin{aligned}
(3n^7+7n^3+11n)&\equiv (0+n+11n)\pmod{3}\\
&\equiv 12n\pmod{3}\\
&\equiv 0\pmod{3},
\end{aligned}
$$

para cada entero no negativo $n$. Alternativamente, en el caso de no recordar el anterior corolario, llegaríamos a que

$$
\begin{aligned}
(3n^7+7n^3+11n)&\equiv (0+7n^3+11n)\pmod{3}\\
&\equiv (n^3-n)\pmod{3},
\end{aligned}
$$

pero 

$$
n^3-n = n(n^2 - 1) = (n - 1)n(n + 1),
$$ 

esto es, $n^3 - n$ es el resultado de multiplicar tres números consecutivos, entre los cuales siempre seremos capaces de encontrar un múltiplo de $3$, haciendo pues que se verifique que $(n^3 - n)\equiv 0\pmod{3}$.

Por lo que respecta al conjunto finito $\mathbb{Z}_7$, cuerpo también al ser $7$ un número primo, que se define siguiendo un procedimiento similar al mostrado para $\mathbb{Z}_3$, la manera de proceder es idéntica. Como $7\equiv 0\pmod{7}$, entonces, para cada entero no negativo $n$, es cierto que $7n^3\equiv 0\pmod{7}$. Además, aplicando el corolario del *Pequeño Teorema de Fermat*, como $7$ es un número primo, $n^7\equiv n\pmod{7}$, por lo que $3n^7\equiv 3n\pmod{7}$ para cada entero no negativo $n$. Luego,

$$
\begin{aligned}
(3n^7+7n^3+11n)&\equiv (3n+0+11n)\pmod{7}\\
&\equiv 14n\pmod{7}\\ 
&\equiv 0\pmod{7}.
\end{aligned}
$$

En cuanto al apartado (b), operando en la expresión de $P(n)$ llegamos a que

$$
P(n) = \dfrac{n^7}{7} + \dfrac{n^3}{3} + \dfrac{11n}{21} = \dfrac{3n^7 + 7n^3 + 11n}{21},
$$

y para que $P(n)\in\mathbb{Z}$, para cada entero no negativo $n$, el numerador de la anterior expresión ha de ser múltiplo de $21$. Sin embargo, en el apartado (a) acabamos de probar que $(3n^7 + 7n^3 + 11n)\equiv 0\pmod{3}$ y $(3n^7 + 7n^3 + 11n)\equiv 0\pmod{7}$, de manera que, aplicando las propiedades de las congruencias, se verifica que $(3n^7 + 7n^3 + 11n)\equiv 0\pmod{21}$, es decir, el numerador es múltiplo de $21$ y, por tanto, $P(n)\in\mathbb{Z}$ para cada entero no negativo $n$.
