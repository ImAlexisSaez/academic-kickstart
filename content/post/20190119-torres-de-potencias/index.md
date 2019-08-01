---
title: "2019, año de las torres de potencias"
slug: "2019-anno-de-las-torres-de-potencias"
subtitle: "Problema 44"
summary: "Problema 44: uno de esos ejercicios que te tiene entretenido un rato."

date: 2019-01-19T05:59:39+02:00
lastmod: 2019-08-01T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Fórmula de Legendre", "Pequeño Teorema de Fermat", "Problemas", "Teorema chino del resto", "Teorema de Euler-Fermat", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [asoggetti](https://unsplash.com/@asoggetti), disponible en [Unsplash](https://unsplash.com/photos/T-6J6uvjDec)."
---

**Problema 44:** Encuentra los dos últimos dígitos de

$$
2017^{2018^{2019}} + 2018^{2019^{2020}} + 2019^{2020^{2021}}
$$

***

Para encontrar las dos últimas cifras de la operación indicada en el enunciado del ejercicio, un posible enfoque pasa por trabajar con el valor de las congruencias módulo $100$. Estudiemos el valor de dichas congruencias para cada uno de los tres sumandos por separado.

En primer lugar, es cierto que

$$
2017^{2018^{2019}} \equiv 17^{2018^{2019}} \pmod{100}.
$$

Ahora, como $mcd(17,100) = 1$, por el *Teorema de Euler-Fermat*, sabemos que 

$$
17^{\varphi(100)} \equiv 1\pmod{100},
$$

y como $100 = 2^2 \cdot 5^2$, 

$$
\varphi(100) = 100\cdot\left(1-\dfrac{1}{2}\right)\cdot\left(1-\dfrac{1}{5}\right) = 40,
$$

esto es, $17^{40} \equiv 1\pmod{100}$. Estudiemos pues el valor de la congruencia módulo $40$ para el exponente, $2018^{2019}$. Por el *Teorema chino del resto*, la ecuación de congruencia lineal $x\equiv 2018^{2019} \pmod{40}$ es equivalente al sistema de ecuaciones de congruencia lineales

$$
\begin{aligned}
x&\equiv 2018^{2019} \pmod{5},\\
x&\equiv 2018^{2019} \pmod{8},
\end{aligned}
$$

ya que $mcd(5,8)=1$ y $5\cdot8 = 40$. No obstante,

$$
2018^{2019} \equiv 3^{2019}\pmod{5},
$$

y como $5$ es un número primo y $mcd(3,5) = 1$, por el *Pequeño Teorema de Fermat*, $3^4 \equiv 1\pmod{5}$. Como $2019 = 4\cdot 504 + 3$, es cierto que

$$
3^{2019} = 3^3\cdot (3^4)^{504} \equiv (3^3 \cdot 1^{504}) \pmod{5} \equiv 2\pmod{5}.
$$

Por otro lado, $2018 = 2\cdot1009$, por lo que,

$$
\begin{aligned}
2018^{2019} &= (2\cdot1009)^{2019} \\
&= 2^{2019} \cdot 1009^{2019} \\
&= 2^3 \cdot 2^{2016} \cdot 1009^{2019} \\
&= 8 \cdot 2^{2016} \cdot 1009^{2019},
\end{aligned}
$$

y así, podemos concluir que $2018^{2019} \equiv 0\pmod{8}$. Por consiguiente, el sistema de ecuaciones de congruencia lineales planteado arriba es equivalente a

$$
\begin{aligned}
x&\equiv 2\pmod{5},\\
x&\equiv 0\pmod{8}.
\end{aligned}
$$

Este último podemos resolverlo, de forma mecánica, con el procedimiento habitual que nos proporciona el *Teorema chino del resto* o razonando sin más. Buscamos aquí un múltiplo de $8$ (menor que $40$) que al dividirlo entre $5$ devuelva un resto de valor $2$. Tras unos rápidos cálculos mentales, encontramos que el número $32$ satisface las restricciones impuestas y, por tanto, la solución al sistema planteado arriba es $x\equiv 32\pmod{40}$. Con todo, hemos llegado a que

$$
2017^{2018^{2019}} \equiv 17^{2018^{2019}} \pmod{100}\equiv 17^{32} \pmod{100}.
$$

Ahora bien, $17^{32} = ( 17^2 )^{16} = 189^{16} \equiv 89^{16} \pmod{100}$. Aplicando esta forma de proceder de manera recurrente, podemos reducir, en unos pocos pasos, $17^{32}$ a un número para el que el cálculo de su congruencia módulo $100$ sea razonable. Así,

$$
\begin{aligned}
17^{32} &\equiv 89^{16} \pmod{100} \\
&\equiv (-11)^{16} \pmod{100} \\
&\equiv 11^{16} \pmod{100} \\
&\equiv 21^8 \pmod{100}\\
&\equiv 41^4 \pmod{100} \\
&\equiv 81^2 \pmod{100} \\
&\equiv 61\pmod{100},
\end{aligned}
$$

esto es,

$$
2017^{2018^{2019}} \equiv 61\pmod{100}.
$$

Para el segundo sumando, utilizaremos el *Teorema chino del resto* desde el principio. Así, la ecuación de congruencia lineal

$$
x\equiv 2018^{2019^{2020}} \pmod{100}
$$

es equivalente al sistema de ecuaciones de congruencia lineales

$$
\begin{aligned}
x&\equiv 2018^{2019^{2020}} \pmod{4},\\
x&\equiv 2018^{2019^{2020}} \pmod{25},
\end{aligned}
$$

puesto que $mcd(4,25)=1$ y $4\cdot25=100$. Ahora bien, por lo que respecta a la primera de ellas,

$$
2018^{2019^{2020}} \equiv 0\pmod{4},
$$

pues $2018 = 2\cdot1009$ y, gracias a ese dos que figura en la descomposición en factores primos de $2018$, operando adecuadamente con las propiedades de los exponentes (de una forma similar a como actuamos en el caso anterior) es fácil ver que la torre de potencias es múltiplo de cuatro. Por otro lado,

$$
2018^{2019^{2020}} \equiv 18^{2019^{2020}} \pmod{25},
$$

y como $mcd(18,25)=1$ estamos en condiciones de volver a aplicar el *Teorema de Euler-Fermat*. Así,

$$
18^{\varphi(25)}\equiv 1\pmod{25},
$$

y, dado que $25=5^2$, es cierto que

$$
\varphi(25) = 25\cdot\left(1-\dfrac{1}{5}\right) = 20.
$$

Por consiguiente, únicamente nos resta explorar el valor de la congruencia módulo $20$ del exponente, $2019^{2020}$. Sin embargo,

$$
\begin{aligned}
2019^{2020} &\equiv (-1)^{2020} \pmod{20} \\
&\equiv 1^{2020}\pmod{20} \\
&\equiv 1\pmod{20},
\end{aligned}
$$

y entonces

$$
2018^{2019^{2020}} \equiv 18^{2019^{2020}} \pmod{25}\equiv 18\pmod{25}.
$$

Por tanto, el sistema de ecuaciones de congruencia lineales planteado queda

$$
\begin{aligned}
x&\equiv 0\pmod{4},\\
x&\equiv 18\pmod{25}.
\end{aligned}
$$

Este último podemos resolverlo, de forma mecánica, por el clásico procedimiento asociado al *Teorema chino del resto* o simplemente razonando sin más. En esta ocasión, buscamos un múltiplo de cuatro (menor que $100$), tal que al dividirlo por $25$ deje un resto que asciende a $18$. Tras unos rápidos cálculos mentales, deducimos que dicho valor es $68$, luego la solución al sistema de ecuaciones planteado es $x\equiv 68\pmod{100}$.

Finalmente, el modo de actuar con el tercer sumando es similar al llevado a cabo para el primero. Así,

$$
2019^{2020^{2021}} \equiv 19^{2020^{2021}} \pmod{100},
$$

y como $mcd(19,100)=1$ sabemos, por el *Teorema de Euler-Fermat*, que $19^{\varphi(100)} = 19^{40} \equiv 1\pmod{100}$, por lo que únicamente nos resta averiguar el valor de la congruencia módulo $40$ de exponente, $2020^{2021}$. Para ello utilizaremos, de nuevo, el *Teorema chino del resto*, que nos garantiza que la ecuación de congruencia lineal

$$
x\equiv 2020^{2021} \pmod{40}
$$

es equivalente al sistema de ecuaciones de congruencia lineales

$$
\begin{aligned}
x&\equiv 2020^{2021} \pmod{5},\\
x&\equiv 2020^{2021} \pmod{8},
\end{aligned}
$$

pues $mcd(5,8)=1$ y $5\cdot8=40$. Ahora bien, como $2020 = 2^2 \cdot5\cdot101$, el exponente es, directamente, múltiplo de $5$ y, por otra parte, operando adecuadamente con las propiedades de las potencias, deducimos rápidamente que asimismo será múltiplo de $8$, esto es, el sistema de ecuaciones de congruencia lineales queda

$$
\begin{aligned}
x&\equiv 0\pmod{5},\\
x&\equiv 0\pmod{8},
\end{aligned}
$$

y su solución, trivialmente, es $x\equiv 0\pmod{40}$. Por consiguiente,

$$
2019^{2020^{2021}} \equiv 19^{2020^{2021}} \pmod{100}\equiv 1\pmod{100}.
$$

Recapitulando,

$$
\begin{aligned}
2017^{2018^{2019}} &\equiv 61\pmod{100},\\
2018^{2019^{2020}} &\equiv 68\pmod{100},\\
2019^{2020^{2021}} &\equiv  1\pmod{100},
\end{aligned}
$$

luego

$$
\begin{aligned}
\left(2017^{2018^{2019}} + 2018^{2019^{2020}} + 2019^{2020^{2021}} \right)&\equiv (61+68+1)\pmod{100}\\
&\equiv 30\pmod{100},
\end{aligned}
$$

es decir, las dos últimas cifras de la operación indicada en el enunciado del ejercicio son $30$.
