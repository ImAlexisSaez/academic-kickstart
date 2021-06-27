---
# Book
title: Ecuaciones
linktitle: Ecuaciones
summary: Problemas matemáticos de ecuaciones para la preparación de oposiciones al cuerpo de profesores de Enseñanza Secundaria, en la especialidad de matemáticas.

date: "2021-06-24T00:00:01+01:00"
lastmod: "2021-06-24T00:00:01+01:00"
draft: false # Is this a draft? true/false
toc: true # Show table of contents? true/false
type: book # Do not modify.
math: true
weight: 140
---

## Problemas resueltos

### Problema 1

Resuelve

- (a) $a_{n+3} - 3a_{n+2} - 4a_{n+1} + 12a_n = 0$.
- (b) $a_{n+3} - 4a_{n+2} + 5a_{n+1} - 2a_n = 0$.

{{< hl >}}Solución:{{< /hl >}} en el apartado (a), encontramos la ecuación en diferencias lineal homogénea de orden 3 dada por $a_{n+3} - 3a_{n+2} - 4a_{n+1} + 12a_n = 0$, cuya ecuación característica asociada es 

$$
\lambda^3-3\lambda^2-4\lambda+12=0.
$$ 

Ahora bien, como $\lambda^3 - 3\lambda^2 - 4\lambda + 12 = (\lambda - 3)(\lambda - 2)(\lambda + 2)$, estamos ante el caso de raíces reales simples, de manera que la solución queda 

$$
a_h(n) = c_1(-2)^n + c_22^n + c_33^n,
$$ 

con $c_1,c_2,c_3\in\mathbb{R}$.

Para el apartado (b), $a_{n+3} - 4a_{n+2} + 5a_{n+1} - 2a_n = 0$ es homogénea de orden 3, con ecuación característica 

$$
\lambda^3 - 4\lambda^2 + 5\lambda - 2 = 0.
$$ 

Como $\lambda^3 - 4\lambda^2 + 5\lambda - 2 = (\lambda - 2)(\lambda - 1)^2$, $\lambda=1$ es una raíz real de multiplicidad $m=2$, mientras que $\lambda=2$ es una raíz real simple, por lo que la solución queda 

$$
a_h(n) = c_11^n + c_2n1^n + c_32^n = c_1+c_2n+c_32^n,
$$ 

con $c_1,c_2,c_3\in\mathbb{R}$.

### Problema 2

Resuelve

- (a) $a_{n+3} - 3a_{n+2} + 4a_{n+1} - 12a_n = 0$.
- (b) $a_{n+4} + 2a_{n+2} + a_n = 0$.

{{< hl >}}Solución:{{< /hl >}} en el apartado (a), $a_{n+3} - 3a_{n+2} + 4a_{n+1} - 12a_n = 0$ es una ecuación en diferencias lineal homogénea de orden 3, que tiene por ecuación característica 

$$
\lambda^3 - 3\lambda^2 + 4\lambda - 12 = 0.
$$ 

Ahora bien, como $\lambda^3 - 3\lambda^2 + 4\lambda - 12 = (\lambda - 3)(\lambda - 2i)(\lambda + 2i)$, tenemos una raíz real simple y dos raíces complejas conjugadas simples, para las que $\varrho = 2$ y $\theta = \pi/2$, de manera que la solución queda 

$$
a_h(n) = c_13^n + 2^n\left(A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)}\right),
$$ 

con $c_1, A, B\in\mathbb{R}$.

A continuación, en el apartado (b), $a_{n+4} + 2a_{n+2} + a_n = 0$ es homogénea de orden 4, con ecuación característica 

$$
\lambda^4 + 2\lambda^2 + 1 = 0.
$$ 

Esta ecuación bicuadrada en $\lambda$ la podemos resolver mediante el cambio de variable $t = \lambda^2$, de forma que la ecuación queda como $t^2+2t+1=0$ y posee $t=-1$ como raíz real de multiplicidad $m=2$, es decir, 

$$
t^2+2t+1 = (t+1)^2.
$$

Así, si deshacemos ahora el cambio de variable, resulta que 

$$
\lambda^4 + 2\lambda^2 + 1 = (\lambda - i)^2(\lambda + i)^2,
$$

con lo cual tenemos dos raíces complejas conjugadas de multiplicidad $m=2$, para las que $\varrho=1$ y $\theta = \pi/2$, por lo que la solución queda

$$
\begin{aligned}
a_h(n) &= 1^n\left(
(An+B)cos{\left(\dfrac{\pi}{2}n\right)} + (Cn+D)\sin{\left(\dfrac{\pi}{2}n\right)}
\right)\\\\ &= (An+B)cos{\left(\dfrac{\pi}{2}n\right)} + (Cn+D)\sin{\left(\dfrac{\pi}{2}n\right)},
\end{aligned}
$$

con $A,B,C,D\in\mathbb{R}$.

### Problema 3

Resuelve

- (a) $a_{n+2}-5a_{n+1}+6a_n = 10$.
- (b) $a_{n+2}-3a_{n+1}+2a_n = 4$.

{{< hl >}}Solución:{{< /hl >}} en el apartado (a), encontramos la ecuación en diferencias lineal completa de orden 2, 

$$
a_{n+2}-5a_{n+1}+6a_n = 10.
$$

Empecemos abordando su ecuación en diferencias lineal homogénea asociada, 

$$
a_{n+2}-5a_{n+1}+6a_n = 0,
$$

cuya ecuación característica correspondiente es 

$$
\lambda^2 - 5\lambda + 6 = 0.
$$ 

Ahora, como $\lambda^2 - 5\lambda + 6=(\lambda - 3)(\lambda - 2)$, estamos en el caso de raíces reales simples, de manera que la solución para la ecuación anterior queda 

$$
a_h(n) = c_12^n + c_23^n,
$$ 

con $c_1,c_2\in\mathbb{R}$. 

A continuación, de cara a encontrar una solución particular, $a_p(n)$, como $b(n)=10$ y $\lambda=1$ no es raíz de la ecuación característica, proponemos $a_p(n) = k$, de forma que, sustituyendo esta en la ecuación inicial, 

$$
k - 5k + 6k = 10,
$$ 

es decir, $k=5$, con lo que 

$$
a_p(n)=5.
$$ 

Finalmente, la solución general para la ecuación inicial la obtenemos haciendo 

$$
a(n) = a_h(n) + a_p(n) = c_12^n + c_23^n + 5,
$$ 

con $c_1,c_2\in\mathbb{R}$.

En el apartado (b), la ecuación en diferencias lineal 

$$
a_{n+2}-3a_{n+1}+2a_n = 4
$$

es completa de orden 2. Procediendo como antes, abordamos su ecuación en diferencias lineal homogénea correspondiente 

$$
a_{n+2}-3a_{n+1}+2a_n = 0,
$$

con ecuación característica asociada 

$$
\lambda^2 - 3\lambda + 2 = 0.
$$ 

Como $\lambda^2 - 3\lambda + 2 = (\lambda - 2)(\lambda - 1)$, volvemos a estar en el caso de raíces reales simples, por lo que la solución para la ecuación anterior queda 

$$
a_h(n) = c_11^n + c_22^n=c_1 + c_22^n,
$$ 

con $c_1,c_2\in\mathbb{R}$. 

Acto seguido, para encontrar una solución particular, $a_p(n)$, como $b(n)=4$ y $\lambda=1$ es raíz simple ($m=1$) de la ecuación característica, proponemos $a_p(n) = kn^1 = kn$, de forma que, sustituyendo en la ecuación inicial, 

$$
k(n+2)-3k(n+1)+2kn = kn+2k-3kn-3k+2kn= -k = 4,
$$ 

es decir, $k = -4$, con lo que 

$$
a_p(n) = -4n.
$$ 

Finalmente, la solución general de la ecuación inicial la obtenemos haciendo 

$$
a(n) = a_h(n) + a_p(n) = c_1+c_22^n-4n,
$$ 

con $c_1,c_2\in\mathbb{R}$.

### Problema 4

Resuelve

- (a) $a_{n+2}-3a_{n+1}-2a_n = 3^n$.
- (b) $a_{n+2}-3a_{n+1}+2a_n = 2^n$.

{{< hl >}}Solución:{{< /hl >}} en el apartado (a), encontramos la ecuación en diferencias lineal completa de orden 2, 

$$
a_{n+2}-3a_{n+1}-2a_n = 3^n.
$$

Su ecuación en diferencias lineal homogénea asociada es 

$$
a_{n+2}-3a_{n+1}-2a_n = 0,
$$

con ecuación característica 

$$
\lambda^2 - 3\lambda - 2 = 0.
$$ 

Ahora, como $\lambda^2 - 3\lambda - 2=(\lambda - 2)(\lambda - 1)$, estamos en el caso de raíces reales simples, por lo que la solución para la ecuación anterior queda 

$$
a_h(n) = c_11^n + c_22^n = c_1+c_22^n,
$$ 

con $c_1,c_2\in\mathbb{R}$. 

A continuación, para encontrar una solución particular, $a_p(n)$, como $b(n) = 3^n$ y $\lambda = 3$ no es raíz de la ecuación característica, proponemos $a_p(n) = k3^n$, de manera que, sustituyendo en la ecuación inicial, 

$$
\begin{aligned}
k3^{n+2} - 3k3^{n+1} + 2k3^n &= 3^n,\\\\ 9k - 9k + 2k &= 1,\\\\ 2k &= 1,
\end{aligned}
$$

es decir, $k = 1 / 2$, con lo que 

$$
a_p(n) = \dfrac{1}{2}3^n.
$$ 

Finalmente, la solución general de la ecuación inicial la obtenemos haciendo 

$$
a(n) = a_h(n) + a_p(n) = c_1+c_22^n + \dfrac{1}{2}3^n,
$$ 

con $c_1,c_2\in\mathbb{R}$.

En el apartado (b), la ecuación en diferencias lineal 

$$
a_{n+2}-3a_{n+1}+2a_n = 2^n
$$

es completa de orden 2. Su ecuación en diferencial lineal homogénea asociada es

$$
a_{n+2}-3a_{n+1}+2a_n = 0,
$$

con ecuación característica correspondiente 

$$
\lambda^2 - 3\lambda + 2 = 0.
$$ 

Como $\lambda^2 - 3\lambda + 2 = (\lambda - 2)(\lambda - 1)$, estamos en el caso de raíces reales simples, por lo que la solución para la ecuación anterior queda 

$$
a_h(n) = c_11^n + c_22^n=c_1+c_22^n,
$$ 

con $c_1,c_2\in\mathbb{R}$. 

Ahora, para encontrar una solución particular, $a_p(n)$, como $b(n) = 2^n$ y $\lambda=2$ es una raíz simple ($m=1$) de la ecuación característica, proponemos $a_p(n) = kn^12^n = kn2^n$, de forma que, sustituyendo en la ecuación inicial,

$$
\begin{aligned}
k(n+2)2^{n+2} - 3k(n+1)2^{n+1}+2kn2^n &= 2^n,\\\\ 4k(n+2) - 6k(n+1) + 2kn &= 1,\\\\ 4kn + 8k - 6kn - 6k + 2kn &=1,\\\\ 2k &= 1,
\end{aligned}
$$

es decir, $k=1 / 2$, con lo que 

$$
a_p(n) = \dfrac{1}{2}n2^n = n2^{n-1}.
$$ 

Finalmente, la solución general de la ecuación inicial la obtenemos haciendo 

$$
a(n) = a_h(n) + a_p(n) = c_1+c_22^n+n2^{n-1},
$$ 

con $c_1,c_2\in\mathbb{R}$.

### Problema 5

Resuelve

- (a) $a_{n+2}+a_n = \sin{(\pi n)}$.
- (b) $a_{n+2}+a_n = \sin{\left(\dfrac{\pi}{2}n\right)}$.

{{< hl >}}Solución:{{< /hl >}} el apartado (a) nos plantea la ecuación en diferencias lineal completa de orden 2, 

$$
a_{n+2}+a_n = \sin{(\pi n)}.
$$

Esta tiene como ecuación en diferencias lineal homogénea asociada 

$$
a_{n+2}+a_n = 0,
$$

cuya ecuación característica correspondiente es 

$$
\lambda^2+1=0.
$$ 

Como $\lambda^2+1 = (\lambda - i)(\lambda + i)$, estamos en el caso de raíces complejas conjugadas simples, para las que $\varrho = 1$ y $\theta = \pi/2$, de manera que la solución para la ecuación anterior queda

$$
\begin{aligned}
a_h(n) &= 1^n\left(A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)}\right)\\\\ &= A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)},
\end{aligned}
$$

con $A,B\in\mathbb{R}$. 

Ahora, para hallar una solución particular, $a_p(n)$, como $b(n) = \sin{(\pi n)}$ y $\lambda = \cos{(\pi)} + i\sin{(\pi)} = -1$ no es raíz de la ecuación característica, proponemos $a_p(n) = a\cos{(\pi n)} + b\sin{(\pi n)}$, de manera que, sustituyendo en la ecuación inicial

$$
\begin{aligned}
a\cos{(\pi(n+2))} + b\sin{(\pi(n+2))} + a\cos{(\pi n)} + b\sin{(\pi n)} &= \sin{(\pi n)},\\\\ a\cos{(\pi n+2\pi)} + b\sin{(\pi n+2\pi)} + a\cos{(\pi n)} + b\sin{(\pi n)} &= \sin{(\pi n)},
\end{aligned}
$$

y recordando que

$$
\begin{aligned}
\cos{(k_1+k_2)} &= \cos{(k_1)}\cos{(k_2)}-\sin{(k_1)}\sin{(k_2)},\\\\ \sin{(k_1+k_2)} &= \sin{(k_1)}\cos{(k_2)}+\cos{(k_1)}\sin{(k_2)},
\end{aligned}
$$

entonces $\cos{(\pi n+2\pi)} = \cos{(\pi n)}$ y $\sin{(\pi n+2\pi)} = \sin{(\pi n)}$, con lo que la ecuación anterior queda

$$
\begin{aligned}
a\cos{(\pi n)} + b\sin{(\pi n)} + a\cos{(\pi n)} + b\sin{(\pi n)} &= \sin{(\pi n)},\\\\ 2a\cos{(\pi n)} + 2b\sin{(\pi n)} &= \sin{(\pi n)},
\end{aligned}
$$

e, igualando coeficientes, llegamos a que $2a=0$, de donde $a=0$, y $2b=1$, con lo que $b=1 / 2$, de forma que 

$$
a_p(n) = \dfrac{1}{2}\sin{(\pi n)}.
$$ 

Finalmente, la solución general de la ecuación inicial la obtenemos haciendo 

$$
a(n) = a_h(n) + a_p(n) = A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)} + \dfrac{1}{2}\sin{(\pi n)},
$$ 

con $A,B\in\mathbb{R}$.

En el apartado (b), tenemos la ecuación en diferencias lineal completa de orden 2, 

$$
a_{n+2}+a_n = \sin{\left(\dfrac{\pi}{2}n\right)},
$$

cuya correspondiente ecuación lineal homogénea es 

$$
a_{n+2}+a_n = 0,
$$

con ecuación característica asociada 

$$
\lambda^2 + 1=0.
$$ 

Como $\lambda^2+1 = (\lambda - i)(\lambda + i)$, estamos en el caso de raíces complejas conjugadas simples, para las que $\varrho = 1$ y $\theta = \pi/2$, de manera que la solución para la ecuación anterior queda 

$$
\begin{aligned}
a_h(n) &= 1^n\left(
A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)}
\right)\\\\ &= A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)},
\end{aligned}
$$ 

con $A,B\in\mathbb{R}$. 

Ahora, para hallar una solución particular, $a_p(n)$, como 

$$
b(n) = \sin{\left(\dfrac{\pi}{2}n\right)}
$$ 

y 

$$
\lambda = \cos{\left(\dfrac{\pi}{2}\right)} + i\sin{\left(\dfrac{\pi}{2}\right)} = i
$$

es raíz simple ($m=1$) de la ecuación característica, proponemos

$$
\begin{aligned}
a_p(n) &= n^1\left(a\cos{\left(\dfrac{\pi}{2}n\right)} + b\sin{\left(\dfrac{\pi}{2}n\right)}\right)\\\\ &= n\left(a\cos{\left(\dfrac{\pi}{2}n\right)} + b\sin{\left(\dfrac{\pi}{2}n\right)}\right),
\end{aligned} 
$$

de manera que, sustituyendo en la ecuación inicial,

$$
\begin{aligned}
(n+2)&\left(a\cos{\left(\dfrac{\pi}{2}(n+2)\right)} + b\sin{\left(\dfrac{\pi}{2}(n+2)\right)}\right)\\\\ &+n\left(a\cos{\left(\dfrac{\pi}{2}n\right)} + b\sin{\left(\dfrac{\pi}{2}n\right)}\right) = \sin{\left(\dfrac{\pi}{2}n\right)}
\end{aligned}
$$

y recordando que

$$
\begin{aligned}
\cos{(k_1+k_2)} &= \cos{(k_1)}\cos{(k_2)}-\sin{(k_1)}\sin{(k_2)},\\\\ \sin{(k_1+k_2)} &= \sin{(k_1)}\cos{(k_2)}+\cos{(k_1)}\sin{(k_2)},
\end{aligned}
$$

entonces 

$$
\begin{aligned}
\cos{\left(\dfrac{\pi}{2}(n+2)\right)} &= \cos{\left(\dfrac{\pi}{2}n+\pi\right)} = -\cos{\left(\dfrac{\pi}{2}n\right)},\\\\ \sin{\left(\dfrac{\pi}{2}(n+2)\right)} &= \sin{\left(\dfrac{\pi}{2}n+\pi\right)} = -\sin{\left(\dfrac{\pi}{2}n\right)},
\end{aligned}
$$

con lo que la ecuación anterior queda

$$
\begin{aligned}
(n+2)&\left(-a\cos{\left(\dfrac{\pi}{2}n\right)} - b\sin{\left(\dfrac{\pi}{2}n\right)}\right)\\\\ &+ n\left(a\cos{\left(\dfrac{\pi}{2}n\right)} + b\sin{\left(\dfrac{\pi}{2}n\right)}\right) = \sin{\left(\dfrac{\pi}{2}n\right)}
\end{aligned}
$$

e, igualando coeficientes, llegamos a que $-2a=0$, de donde $a=0$, y $-2b=1$, por lo que $b = -1 / 2$, de forma que 

$$
a_p(n) = -\dfrac{1}{2}\sin{\left(\dfrac{\pi}{2}n\right)}.
$$ 

Finalmente, la solución general de la ecuación inicial la obtenemos haciendo 

$$
\begin{aligned}
a(n) = a_h(n) + a_p(n) &= A\cos{\left(\dfrac{\pi}{2}n\right)} + B\sin{\left(\dfrac{\pi}{2}n\right)} -\dfrac{1}{2}\sin{\left(\dfrac{\pi}{2}n\right)}\\\\ &=A\cos{\left(\dfrac{\pi}{2}n\right)} + \left(B-\dfrac{1}2{}\right)\sin{\left(\dfrac{\pi}{2}n\right)},
\end{aligned}
$$

con $A,B\in\mathbb{R}$.

### Problema 6

En un verde prado, la hierba crece de forma uniforme y constante. Se sabe que $70$ vacas lo consumirían en $24$ días y que $30$ vacas lo harían en $60$ días. ¿Cuántas vacas se comerían la hierba en $96$ días?

{{< hl >}}Solución:{{< /hl >}} el comienzo del enunciado de este ejercicio, aunque en apariencia tan poético como irrelevante, nos ofrece una importante pista para llevar a buen término la resolución del problema. ''En un verde prado'' nos indica que, inicialmente, el mencionado prado posee cierta cantidad de hierba (en otro caso, las vacas ni se molestarían en realizarle una visita el primer día). Consideremos pues, por ejemplo, que dicho prado posee $1$ unidad de hierba (equivalentemente, podríamos decir que está conformado por $a$ unidades de hierba, con $a\in\mathbb{N}$; o que simplemente posee un porcentaje de hierba igual a $100\%$).

Dado que la hierba crece de forma uniforme y constante, designemos por $x$ la altura que gana a diario la hierba en nuestro verde prado. Así, ¿qué cantidad de hierba acumulará dicho prado en $24$ días? Efectivamente, $1+24x$, la unidad de hierba con la que contaba inicialmente más el crecimiento uniforme y constante de esta durante el período de tiempo considerado.

La siguiente cuestión que nos planteamos, acto seguido, es: ¿cuánto come una vaca al día? Dado que las $70$ vacas consumen toda la hierba disponible del verde prado en $24$ días, cada vaca es responsable de la desaparición diaria de la siguiente fracción de hierba:

$$
\dfrac{1 + 24x}{24\cdot 70}.
$$

Ahora bien, $30$ vacas consumen la misma cantidad de hierba en $60$ días, situación que da lugar a que cada vaca disfruta, a diario, de la siguiente fracción de hierba:

$$
\dfrac{1+60x}{60\cdot 30}.
$$

Igualando ambas expresiones, seremos capaces de encontrar cuánto crece la hierba en nuestro querido verde prado a diario, es decir, el valor de $x$. Así,

$$
\dfrac{1 + 24x}{24\cdot 70} = \dfrac{1+60x}{60\cdot 30},
$$

esto es, $1800 + 43200x = 1680 + 100800x$, es decir, 

$$
x = \dfrac{1}{480}.
$$

Sustituyendo ahora, el consumo diario de hierba de una vaca asciende a la fracción

$$
\dfrac{1 + 24\cdot\dfrac{1}{480}}{24\cdot70} = \dfrac{504}{480\cdot1680} = \dfrac{1}{1600}.
$$

Por consiguiente, si cada vaca devora tal fracción de hierba a diario y designamos por $y$ la cantidad de vacas que consumirían nuestro amado verde prado en $96$ días, tendrá que satisfacerse que

$$
\dfrac{1 + 96\cdot\dfrac{1}{480}}{96y} = \dfrac{1}{1600} \Leftrightarrow \dfrac{576}{480\cdot96y} = \dfrac{1}{1600} \Leftrightarrow \dfrac{1}{80y} = \dfrac{1}{1600},
$$

esto es, $20$ serán las vacas que consuman el verde prado en $96$ días.


## Problemas propuestos

**Problema 7:** demuestra que $\sqrt[3]{45 + 29\sqrt{2}} + \sqrt[3]{45 - 29\sqrt{2}}$ es un número entero.

**Problema 8:** sean $a$ y $b$ dos números enteros. Demuestra que la ecuación $(x - a)(x - b)(x - 3) = (-1)$ tiene, a lo sumo, una solución entera.