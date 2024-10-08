---
# Book
title: Teoría de números
linktitle: Teoría de números
summary: Problemas matemáticos de teoría de números para la preparación de oposiciones al cuerpo de profesores de Enseñanza Secundaria, en la especialidad de matemáticas.

date: "2021-06-20T00:00:01+01:00"
lastmod: "2021-06-20T00:00:01+01:00"
draft: false # Is this a draft? true/false
toc: true # Show table of contents? true/false
type: book # Do not modify.
math: true
weight: 40
---

## Problemas resueltos

### Problema 1

Demuestra que todos los términos de la sucesión $\\{a_n\\}\_{n>2}$ son múltiplos de $600$, siendo 

$$
a_n = (n^2-1)(n^2+1)(n^4-16)n^2.
$$

{{< hl >}}Solución:{{< /hl >}} es más que razonable que, en una primera aproximación a la resolución de este problema, estemos tentados a probar la afirmación dada en el enunciado utilizando el *principio de inducción matemática*. Esta senda nos llevaría a definir, seguramente, $P(n)$ de forma similar a la siguiente: existe $k\in\mathbb{Z}$ tal que si $n>2$, entonces 

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

### Problema 2

Demuestra que, para cada $n\in\mathbb{N}$, con $n\geq 1$, $$4^{n+1} + 5^{2n-1}$$ es un múltiplo de 21.

{{< hl >}}Solución:{{< /hl >}} para empezar, para cada $n\in\mathbb{N}$, $4^{n+1} + 5^{2n-1}$ es un entero mayor o igual que 21 y será múltiplo de este último siempre que 

$$
4^{n+1} + 5^{2n-1}\equiv 0 \pmod{21}.
$$

Ahora bien, como $21=3\cdot 7$ y $mcd(3,7)=1$, demostrar la expresión anterior equivale a probar que las expresiones

$$
4^{n+1} + 5^{2n-1}\equiv 0 \pmod{3}
$$

y

$$
4^{n+1} + 5^{2n-1}\equiv 0 \pmod{7},
$$

se satisfacen conjuntamente, ya que sabemos, por las propiedades de las congruencias, que dados $n,m\in\mathbb{N}$ fijos y $a,b\in\mathbb{Z}$, si $a\equiv b \pmod{n}$, $a\equiv b \pmod{m}$ y $mcd(n,m)=1$, entonces $a\equiv b \pmod{nm}$.

Así pues, dado que $4\equiv 1 \pmod{3}$ y $5\equiv (-1) \pmod{3}$, entonces, para cada $n\in\mathbb{N}$,

$$
\begin{aligned}
4^{n+1}+5^{2n-1} &\equiv (1^{n+1} + (-1)^{2n-1}) \pmod{3}\\\\ &\equiv (1-1) \pmod{3}\\\\ &\equiv 0 \pmod{3},
\end{aligned}
$$

quedando así una demostrada. Para verificar la restante tengamos en cuenta que $5\equiv (-2) \pmod{7}$ y así, para cada $n\in\mathbb{N}$,

$$
\begin{aligned}
4^{n+1} + 5^{2n-1} &= 2^{2(n+1)} + 5^{2n-1}\\\\ &= 2^{2n+2} + 5^{2n-1}\\\\ &= 2^32^{2n-1} + 5^{2n-1}\\\\ &\equiv (2^32^{2n-1} + (-2)^{2n-1}) \pmod{7}\\\\ &\equiv (2^32^{2n-1} + (-1)^{2n-1}2^{2n-1}) \pmod{7}\\\\ &\equiv (2^32^{2n-1} - 2^{2n-1}) \pmod{7}\\\\ &\equiv ((2^3-1)2^{2n-1}) \pmod{7}\\\\ &\equiv 7\cdot 2^{2n-1} \pmod{7}\\\\ &\equiv 0 \pmod{7}.
\end{aligned}
$$

Por tanto, podemos concluir que, para cada $n\in\mathbb{N}$, $4^{n+1} + 5^{2n-1}$ es un múltiplo de 21.

### Problema 3

Calcula el resto de la división de 

$$
2^{1538}
$$ 

entre $5$.

{{< hl >}}Solución:{{< /hl >}} estudiemos, utilizando la teoría de congruencias, el comportamiento del valor de las primeras potencias de $2$.

$$
\begin{aligned}
2^1&\equiv 2 \pmod{5},\\\\ 2^2&\equiv 4 \pmod{5}\equiv(-1) \pmod{5},\\\\ 2^3&\equiv 3 \pmod{5},\\\\ 2^4&\equiv 1 \pmod{5}.
\end{aligned}
$$

Este resulta un buen punto en el que detener nuestro análisis, ya que ahora sabemos que las potencias de $2$ que son múltiplo de $4$ son congruentes con $1$ módulo $5$. Es decir, $2^8\equiv 1 \pmod{5}$, $2^{12}\equiv 1 \pmod{5}$, etc. Antes de continuar, cabe señalar que:

- Podíamos habernos ahorrado algunos cálculos, ya que como $p=5$ es un número primo y $mcd(2,5)=1$, entonces, por el *Pequeño Teorema de Fermat*, $2^{5-1} = 2^4\equiv 1 \pmod{5}$. 
-  Además, en el momento en el que hemos obtenido la potencia para la cual $(-1)\pmod{5}$ ya podíamos intuir cuándo llegaríamos al resultado deseado, ya que $(-1)^2=1$, lo que indica que al elevar al cuadrado la potencia asociada ($2^2$ en este caso) tendríamos que sería congruente $1$ módulo $5$. Es decir $( 2^{2} )^{2} = 2^{4} \equiv 1\pmod{5}$.

Ahora, dividiendo, sabemos que $1538 = 384\cdot 4 + 2$ y, por tanto,

$$
2^{1538} = 2^{384\cdot 4 + 2} = (2^4)^{384}\cdot 2^2\equiv (1\cdot 4)\pmod{5}\equiv 4\pmod{5},
$$

y así, el resto de la división de $2^{1538}$ entre $5$ asciende a $4$.

### Problema 4

Calcula el inverso de $3$ módulo $7$.

{{< hl >}}Solución:{{< /hl >}} el enunciado nos plantea resolver 

$$
3x\equiv 1\pmod{7}.
$$

Como $mcd(3,7)=1$, es decir, $3$ y $7$ son coprimos, estamos en condiciones de asegurar que seremos capaces de encontrar el inverso de $3$ módulo $7$, $x$. Para ello, como los números involucrados son pequeños, podemos simplemente optar por emplear la ''cuenta de la vieja'' y extraer el valor de $x$ por fuerza bruta. Así,

$$
\begin{aligned}
3\cdot 1 &= 3\equiv 3\pmod{7},\\\\ 3\cdot 2 &= 6\equiv 6\pmod{7},\\\\ 3\cdot 3 &= 9\equiv 2\pmod{7},\\\\ 3\cdot 4 &= 12\equiv 5\pmod{7},\\\\ 3\cdot 5 &= 15\equiv 1\pmod{7},
\end{aligned}
$$

luego $x=5$ es el inverso de $3$ módulo $7$. 

Alternativamente, podemos llevar a cabo operaciones elementales sobre la propia ecuación de congruencia. Como $2\cdot3=6$, que es un valor muy cercano a $7$, entonces

$$
\begin{aligned}
3x\equiv 1\pmod{7}&\Leftrightarrow 6x\equiv 2\pmod{7}\\\\ &\Leftrightarrow -x\equiv 2\pmod{7}\\\\ &\Leftrightarrow x\equiv (-2)\pmod{7}\\\\ &\Leftrightarrow x\equiv 5\pmod{7},
\end{aligned}
$$

arribando así al mismo resultado que antes.

### Problema 5

Calcula el valor de la expresión 

$$
(1^3 + 2^3 + \cdots + 100^3)\pmod{4}.
$$

{{< hl >}}Solución:{{< /hl >}} si tenemos en cuenta que

$$
\begin{aligned}
1\equiv 1\pmod{4} &\Rightarrow 1^3\equiv 1^3\pmod{4}\equiv 1\pmod{4},\\\\ 2\equiv 2\pmod{4} &\Rightarrow 2^3\equiv 2^3\pmod{4}\equiv 8\pmod{4}\equiv 0\pmod{4},\\\\ 3\equiv 3\pmod{4} &\Rightarrow 3^3\equiv 3^3\pmod{4}\equiv 27\pmod{4}\equiv 3\pmod{4},\\\\ 4\equiv 0\pmod{4} &\Rightarrow 4^3\equiv 0^3\pmod{4}\equiv 0\pmod{4},\\\\ 5\equiv 1\pmod{4} &\Rightarrow 5^3\equiv 1^3\pmod{4}\equiv 1\pmod{4},\\\\ 6\equiv 2\pmod{4} &\Rightarrow 6^3\equiv 2^3\pmod{4}\equiv 8\pmod{4}\equiv 0\pmod{4},
\end{aligned}
$$

enseguida atisbamos cómo se repetiría el mismo patrón cada cuatro sumandos. Ahora bien,

$$
\begin{aligned}
(1^3 + 2^3 + 3^3 + 4^3)\pmod{4}&\equiv (1 + 0 + 3 + 0)\pmod{4}\\\\ &\equiv 4\pmod{4}\\\\ &\equiv 0\pmod{4},
\end{aligned}
$$

y como en la suma de cubos propuesta en el enunciado del ejercicio hemos de sumar $25$ veces el resultado del patrón anterior, llegamos a que

$$
(1^3 + 2^3 + \cdots+100^3)\pmod{4} \equiv 0\pmod{4},
$$

es decir, la suma de los cubos de los cien primeros números naturales es múltiplo de $4$.

### Problema 6

Calcula las reglas de divisibilidad para $3$ y para $9$.

{{< hl >}}Solución:{{< /hl >}} consideremos el número de $n$ cifras $a\_{n-1}a\_{n-2}\cdots a_2a_1a_0$ en base $10$. Sabemos, por el *Teorema Fundamental de la Numeración*, que podemos expresarlo como

$$
a_{n-1}a_{n-2}\cdots a_1a_0 = a_0+a_110+\cdots+a_{n-2}10^{n-2}+a_{n-1}10^{n-1}.
$$

Para encontrar el criterio de divisibilidad del $3$ utilizaremos las propiedades de las congruencias sobre las potencias de $10$, buscando una condición sobre los dígitos del número $a_{n-1}a_{n-2}\cdots a_2a_1a_0$ de manera que 

$$
a_0+a_110+a_210^2+\cdots+a_{n-2}10^{n-2}+a_{n-1}10^{n-1}\equiv 0\pmod{3},
$$ 

esto es, dicho número sea múltiplo de $3$.

Así, como $10\equiv 1\pmod{3}$, fácilmente apreciamos que 

$$
10^2\equiv 1^2\pmod{3}\equiv 1\pmod{3}
$$ 

y, en general, $10^i\equiv 1\pmod{3}$, para cada $i\in\mathbb{N}$, por lo que

$$
a_0+a_110+\cdots+a_{n-1}10^{n-1}\equiv (a_0+a_1+\cdots+a_{n-1})\pmod{3},
$$

es decir, el número $a_{n-1}a_{n-2}\cdots a_2a_1a_0$ es divisible por $3$ siempre y cuando la suma de sus dígitos sea múltiplo de $3$.

Por lo que respecta al criterio de divisibilidad del $9$, el modo de proceder es muy similar al mostrado arriba. Volvemos a buscar una condición sobre los dígitos del número $a_{n-1}a_{n-2}\cdots a_2a_1a_0$ de manera que 

$$
a_0+a_110+a_210^2+\cdots+a_{n-2}10^{n-2}+a_{n-1}10^{n-1}\equiv 0\pmod{9},
$$ 

esto es, dicho número sea múltiplo de $9$. Al igual que antes, como $10\equiv 1\pmod{9}$, se sigue que $10^2\equiv 1^2\pmod{9}\equiv 1\pmod{9}$ y, en general, $10^i\equiv 1\pmod{9}$, para cada $i\in\mathbb{N}$, por lo que

$$
a_0+a_110+\cdots+a_{n-1}10^{n-1}\equiv (a_0+a_1+\cdots+a_{n-1})\pmod{9},
$$

es decir, el número $a_{n-1}a_{n-2}\cdots a_2a_1a_0$ es divisible por $9$ siempre y cuando la suma de sus dígitos sea múltiplo de $9$. Expresado de otra manera, todo número es congruente con la suma de sus cifras módulo $9$. Por ejemplo, $162\equiv 0\pmod{9}$, ya que $1+6+2=9$ y $9\equiv 0\pmod{9}$; mientras que $172\equiv 1\pmod{9}$, puesto que $1+7+2=10$ y $10\equiv 1\pmod{9}$. 

*Nota*: es más, el último criterio de divisibilidad hallado se puede generalizar como sigue: ''*dado un sistema de numeración cuya base $b$ es mayor que $2$, un número es divisible por $b-1$ siempre que la suma de sus dígitos sea congruente con $0$ módulo $b-1$*''.

### Problema 7

Calcula la regla de divisibilidad por $7$.

{{< hl >}}Solución:{{< /hl >}} veamos que, en esta ocasión, proceder como en ejercicios anteriores no dará lugar a establecer una sencilla regla para el criterio de divisibilidad del $7$. En efecto, consideremos el número de $n$ cifras $a\_{n - 1} a\_{n - 2}\cdots a_2a_1a_0$ en base $10$. Sabemos, por el *Teorema Fundamental de la Numeración*, que podemos expresarlo como

$$
a_{n-1}a_{n-2}\cdots a_1a_0 = a_0+a_110+ \cdots + a_{n-2}10^{n-2}+a_{n-1}10^{n-1}.
$$

Para encontrar el criterio de divisibilidad del $7$ utilizaremos las propiedades de las congruencias sobre las potencias de $10$, buscando una condición sobre los dígitos del número $a_{n-1}a_{n-2}\cdots a_2a_1a_0$ de manera que

$$
a_0+a_110+a_210^2 + \cdots + a_{n-2}10^{n-2}+a_{n-1}10^{n-1}\equiv 0\pmod{7},
$$

esto es, dicho número sea múltiplo de $7$.

Ahora bien,

$$
\begin{aligned}
10&\equiv 3\pmod{7},\\\\ 10^2&\equiv 3^2\pmod{7}\equiv 9\pmod{7}\equiv 2\pmod{7},\\\\ 10^3&\equiv 3^3\pmod{7}\equiv 27\pmod{7}\equiv 6\pmod{7},\\\\ 10^4&\equiv 3^4\pmod{7}\equiv 81\pmod{7}\equiv 4\pmod{7},\\\\ &\vdots
\end{aligned}
$$

y comenzamos a atisbar que el criterio que podríamos extraer es ciertamente extraño y muy complicado de recordar, puesto que

$$
a_0+a_110+\cdots + a_{n-1}10^{n-1}\equiv (a_0 + 3a_1 + 2a_2 + \cdots)\pmod{7}.
$$

Por lo que respecta a la divisibilidad de un número por $7$, conviene que tengamos a mano el siguiente resultado: ''*un número de la forma $n=10d+u$, con $d>0$ y $0\leq u\leq 9$ es múltiplo de $7$ si, y solo si, $d-2u$ es múltiplo de $7$*''.

Efectivamente, si suponemos cierto que $(10d+u)\equiv 0\pmod{7}$, es decir, que $n=10d+u$ es múltiplo de $7$, y aplicamos ahora propiedades de las congruencias sobre la forma del número $n$, llegamos a que

$$
\begin{aligned}
(10d+u)\equiv 0\pmod{7} &\Leftrightarrow (3d-6u)\equiv 0\pmod{7} \\\\ &\Leftrightarrow (3(d-2u))\equiv 0\pmod{7},
\end{aligned}
$$

esto es, hemos arribado a que el producto de dos números es múltiplo de $7$, y como sabemos que el número $3$ no lo es, concluimos que $d-2u$ es múltiplo de $7$.

Recíprocamente, si $d-2u$ es múltiplo de $7$, $(d-2u)\equiv 0\pmod{7}$ y multiplicando por $10$, $(10d-20u)\equiv 0\pmod{7}$. Ahora, como $(-20)\equiv 1\pmod{7}$, llegamos a que $(10d+u)\equiv 0\pmod{7}$, es decir, el número $n=10d+u$ es un múltiplo de $7$, quedando así la doble implicación probada.

Veamos en acción esta proposición con un par de ejemplos sencillos. Si $n=63 = 60+3$, entonces $d = 6$, $u=3$ y $d-2u = 6-2\cdot3=0$ que, efectivamente, es un múltiplo de $7$, luego $63$ asimismo lo es. Si $n = 9009$, tenemos que $d = 900$, $u=9$ y $d-2u = 900-2\cdot9=882 = 7\cdot126$, luego $d-2u$ es un múltiplo de $7$, por lo que podemos concluir que el número $9009$ también lo es.

### Problema 8

- (a) Halla la base en que $$3753_{(x} - 3586_{(x} = 189_{(x}.$$
- (b) Una vez hallado el valor de $x$, deduce el criterio de divisibilidad entre $x-1$ de dicha base.
- (c\) Después, justifica si alguno de los números dados es divisible por $x-1$ en dicha base.
- (d) Por último, pasa el primero de los números dados a base $9$. 

{{< hl >}}Solución:{{< /hl >}} para el apartado (a), por el *Teorema Fundamental de la Numeración*, sabemos que

$$
\begin{aligned}
3753_{(x} &= 3x^0 + 5x^1 + 7x^2 + 3x^3 = 3+5x+7x^2+3x^3,\\\\ 3586_{(x} &= 6x^0 + 8x^1 + 5x^2 + 3x^3 = 6+8x+5x^2+3x^3,\\\\ 189_{(x} &= 9x^0 + 8x^1 + 1x^2 = 9+8x+x^2,
\end{aligned}
$$

por lo que la igualdad planteada en el enunciado es equivalente a:

$$
3+5x+7x^2 + 3x^3 - (6+8x+5x^2 + 3x^3) = 9+8x+x^2.
$$

Operando, esta se convierte en $x^2 - 11x-12=0$, y como 

$$
x^2 - 11x-12 = (x-12)(x+1),
$$ 

concluimos que la base del sistema de numeración en la que se satisface la anterior igualdad es $x=12$ ($x=-1$ queda descartada automáticamente pues toda base ha de ser un número natural estrictamente mayor que $1$. Es más, a modo anecdótico, si las soluciones hubiesen sido $x=7$ y $x=12$, también habríamos descartado de forma automática la primera, pues en la expresión de los números implicados en la igualdad hay dígitos mayores o iguales que $7$).

Para el apartado (b), consideremos el número de $n$ cifras $a_{n-1}a_{n-2}\cdots a_2a_1a_0$ en base $12$. Utilizando el mismo resultado anterior, sabemos que podemos expresarlo como

$$
a_{n-1}a_{n-2}\cdots a_1a_0 = a_0+a_112+\cdots+a_{n-2}12^{n-1}+a_{n-1}12^{n-1}.
$$

De cara a encontrar el criterio de divisibilidad del $11$ emplearemos las propiedades de las congruencias sobre las potencias de $12$, buscando una condición sobre los dígitos del número $a_{n-1}a_{n-2}\cdots a_2a_1a_0$ de manera que

$$
a_0+a_112+a_212^2+\cdots+a_{n-1}12^{n-1}\equiv 0\pmod{11}.
$$

Ahora, como $12\equiv 1\pmod{11}$, fácilmente apreciamos que 

$$
12^2\equiv 1^2\pmod{11}\equiv 1\pmod{11}
$$ 

y, en general, $12^i\equiv 1\pmod{11}$, para cada $i\in\mathbb{N}$, por lo que

$$
a_0+a_112+\cdots+a_{n-1}12^{n-1}\equiv (a_0+a_1+\cdots+a_{n-1})\pmod{11},
$$

es decir, el número $a_{n-1}a_{n-2}\cdots a_2a_1a_0$, en base $12$, es divisible por $11$ siempre y cuando la suma de sus dígitos sea múltiplo de $11$.

En el apartado (c\), a partir de la condición obtenida arriba, podemos concluir que

- $3+7+5+3 = 18\equiv 7\pmod{11}$,
- $3+5+8+6 = 22\equiv 0\pmod{11}$,
- $1+8+9 = 18\equiv 7\pmod{11}$,

esto es, $3586_{(12}$ es el único número, de entre los tres propuestos, divisible por $11$.

Finalmente, en el apartado (d) tenemos que

$$
\begin{aligned}
3753_{(12} &= 3\cdot12^0 + 5\cdot12^1 + 7\cdot12^2 + 3\cdot12^3 \\\\ &= 5184+1008+60+3 \\\\ &= 6255_{(10},
\end{aligned}
$$

y dividiendo ahora sucesivamente por $9$,

$$
\begin{aligned}
6255 &= 9\cdot 695 + 0,\\\\ 695 &= 9\cdot 77 + 2,\\\\ 77 &= 9\cdot 8 + 5,
\end{aligned}
$$

arribamos a que $6255_{(10} = 8520_{(9}$, de manera que $3753_{(12} = 8520_{(9}$ por la unicidad que nos concede el Teorema Fundamental de la Numeración.

### Problema 9

Sea $n$ un número natural. Sea $A_n = 2^n + 2^{2n} + 2^{3n}$.

- (a) Demuestra que para todo $n$, $A_{n+3}\equiv A_n\pmod{7}$.
- (b) ¿Para qué valores de $n$, $A_n$ es múltiplo de $7$?
- (c\) Los números en base $2$, $1110$, $1010100$ y $1001001000$, ¿son divisibles por $7$?

{{< hl >}}Solución:{{< /hl >}} para el apartado (a),

$$
A_{n+3} = 2^{n+3} + 2^{2(n+3)} + 2^{3(n+3)} = 2^{n+3} + 2^{2n+6} + 2^{3n+9}.
$$

Ahora bien, aprovechando que $2^3=8\equiv 1\pmod{7}$, tenemos que

$$
A_{n+3} = 2^3\cdot2^n + (2^3)^2\cdot2^{2n} + (2^3)^3\cdot 2^{3n} \equiv (2^n + 2^{2n} + 2^{3n})\pmod{7},
$$

es decir, $A_{n+3}\equiv A_n\pmod{7}$, como queríamos demostrar.

En cuanto al apartado (b), teniendo presente el resultado alcanzado en el apartado anterior, estudiemos qué sucede para tres números consecutivos. Por comodidad de cara a los cálculos, tomaremos $1$, $2$ y $3$ como valores para $n$, y así,

$$
\begin{aligned}
A_1 &= 2^1+2^2+2^3 = 14\equiv 0\pmod{7},\\\\ A_2 &= 2^2+2^4+2^6 = 84\equiv 0\pmod{7},\\\\ A_3 &= 2^3+2^6+2^9 = 584\equiv 3\pmod{7},
\end{aligned}
$$

es decir, como $A_{1}$ es múltiplo de $7$ y se satisface la propiedad dada en a), que podemos escribir como $( A_{n + 3} - A_{n} ) \equiv 0 \pmod{7}$, concluimos que $A_{4}$ será múltiplo de $7$ también, así como $A_{7}, A_{10}, A_{13}$ y, en general, los números de la forma $n=3k+1$, con $k\in\mathbb{N}$, sin más que aplicar reiteradamente la citada propiedad. Un argumento similar se podría esgrimir para los números de la forma $n=3k+2$, con $k\in\mathbb{N}$, a la vista del resultado alcanzado para $A_2$. De igual manera, este cauce de pensamiento nos llevaría a descartar que cualquier número de la forma $n=3k$, con $k\in\mathbb{N}$, vaya a ser múltiplo de $7$, ya que $A_3$ no lo es. En conclusión, $A_n$ será múltiplo de $7$ para todos aquellos valores de $n$ que no sean múltiplo de $3$.

Finalmente, en el apartado (c), por el *Teorema Fundamental de la Numeración*, sabemos que podemos escribir

$$
\begin{aligned}
1110_{(2} &= 2^1+2^2+2^3 = A_1,\\\\ 1010100_{(2} &= 2^2+2^4+2^6 = A_2,\\\\ 
1001001000_{(2} &= 2^3+2^6+2^9 = A_3,
\end{aligned}
$$

y por lo establecido para el apartado anterior, $A_{1}$ y $A_{2}$ son divisibles por $7$, mientras que $A_{3}$ no lo es. De esta manera, los números $1110_{(2}$ y $1010100_{(2}$ son divisibles por $7$, mientras que $1001001000_{(2}$ no lo es.

### Problema 10

Escribe los divisores de $1001$. Considera ahora 

$$
N = a_0 + a_1t + \cdots + a_nt^n
$$ 

y 

$$
S = a_0-a_1+a_2-\cdots+(-1)^na_n,
$$

donde $t=1000$ y $a_n\in\mathbb{Z}$ y demuestra que $N\equiv S\pmod{1001}$. Deduce de ello un criterio de divisibilidad por $7$, $11$ o $13$ y aplícalo al número $312879645$.

{{< hl >}}Solución:{{< /hl >}} como $1001 = 7\cdot11\cdot13$, el conjunto de divisores del número $1001$ es 

$$
\{1,7,11,13,77,91,143,1001\}.
$$

A continuación, si consideramos $t=1000$, como 

$$
t\equiv (-1)\pmod{1001},
$$ 

entonces se cumple que $t^2\equiv (-1)^2\pmod{1001}\equiv 1\pmod{1001}$ y, en general, $t^n\equiv (-1)^n\pmod{1001}$, para cada $n\in\mathbb{N}$. Este hecho nos permite concluir que

$$
\begin{aligned}
N &= a_0 + a_1t + \cdots + a_nt^n \\\\ &\equiv (a_0-a_1+a_2-\cdots+(-1)^na_n)\pmod{1001},
\end{aligned}
$$

es decir, $N\equiv S\pmod{1001}$, tal y como se nos pedía demostrar. 

Ahora bien, que $N$ sea congruente con $S$ módulo $1001$ implica que existe un $k\in\mathbb{Z}$ de manera que podemos escribir $N = 1001k+S$. Por tanto, dado que $1001=7\cdot11\cdot13$, el número $N$ será divisible por $7$, $11$ o $13$, siempre y cuando $S$ sea divisible por $7$, $11$ o $13$ (por aplicación directa de las propiedades de las congruencias), quedando así establecido el criterio de divisibilidad solicitado.

Finalmente, si tomamos $N=312879645$, es cierto que lo podemos expresar como 

$$
N = 645 + 879\cdot1000 + 312\cdot1000^2,
$$ 

por lo que $a_0 = 645$, $a_1=879$ y $a_2=312$. Esto provoca que 

$$
S = 645 - 879 + 312 = 78 = 13\cdot 6,
$$ 

y como $S$ es divisible por $13$ concluimos, por lo anterior, que $N$ es asimismo divisible por $13$. Alternativamente, podríamos decir que como $7\nmid S$, entonces $7\nmid N$ y, análogamente, como $11\nmid S$, entonces $11\nmid N$, quedando así únicamente concluir como arriba que como $13|S$, entonces $13|N$.

Por ejemplo, si consideramos ahora $N=178178$, su expresión en esta base $1000$ que introduce el presente ejercicio es $N = 178 + 178\cdot 1000$, quedando entonces $a_0=178$, $a_1=178$ y, por consiguiente, $S = 178-178 = 0$. Ahora bien, como $7|0$, entonces $7|N$ y, de forma similar, como $11|0$ y $13|0$, entonces $11|N$ y $13|N$. Añadiendo ahora un tres delante de $N$, es decir, $N=3178178$, tenemos $N = 178 + 178\cdot1000 + 3\cdot1000^2$, con $a_0=178$, $a_1=178$, $a_2=3$ y $S=3$. Como $7\nmid 3$, $11\nmid 3$ ni $13\nmid 3$, entonces concluimos que este último número no es divisible por $7$, $11$ ni $13$.

### Problema 11

Para cada entero no negativo $n$, se considera el valor $P(n)$, 

$$
P(n) = \dfrac{n^7}{7} + \dfrac{n^3}{3} + \dfrac{11n}{21}.
$$

- (a) Demuestra que en $\mathbb{Z}_3$ y en $\mathbb{Z}_7$ se verifica que $3n^7 + 7n^3 + 11n = 0$.
- (b) Demuestra que $P(n)$ es un entero.

{{< hl >}}Solución:{{< /hl >}} para el apartado (a), recordemos que el conjunto finito $\mathbb{Z}_3 = \\{\overline{0}, \overline{1}, \overline{2}\\}$, que es un cuerpo al ser $3$ un número primo, viene definido como el conjunto cociente de $\mathbb{Z}$ por la relación de equivalencia dada por la congruencia módulo $3$. Así, como $3\equiv 0\pmod{3}$, para cada entero no negativo $n$, $3n^7\equiv 0\pmod{3}$. Por otro lado, al ser $3$ un número primo, sabemos, por el corolario del *Pequeño Teorema de Fermat*, que $n^3\equiv n\pmod{3}$, para cada entero no negativo $n$, por lo que $7n^3\equiv 7n\pmod{3}\equiv n\pmod{3}$. Por tanto,

$$
\begin{aligned}
(3n^7+7n^3+11n)&\equiv (0+n+11n)\pmod{3}\\\\ &\equiv 12n\pmod{3}\\\\ &\equiv 0\pmod{3},
\end{aligned}
$$

para cada entero no negativo $n$. Alternativamente, en el caso de no recordar el anterior corolario, llegaríamos a que

$$
\begin{aligned}
(3n^7+7n^3+11n)&\equiv (0+7n^3+11n)\pmod{3}\\\\ &\equiv (n^3-n)\pmod{3},
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
(3n^7+7n^3+11n)&\equiv (3n+0+11n)\pmod{7}\\\\ &\equiv 14n\pmod{7}\\\\ 
&\equiv 0\pmod{7}.
\end{aligned}
$$

En cuanto al apartado (b), operando en la expresión de $P(n)$ llegamos a que

$$
P(n) = \dfrac{n^7}{7} + \dfrac{n^3}{3} + \dfrac{11n}{21} = \dfrac{3n^7 + 7n^3 + 11n}{21},
$$

y para que $P(n)\in\mathbb{Z}$, para cada entero no negativo $n$, el numerador de la anterior expresión ha de ser múltiplo de $21$. Sin embargo, en el apartado (a) acabamos de probar que $(3n^7 + 7n^3 + 11n)\equiv 0\pmod{3}$ y $(3n^7 + 7n^3 + 11n)\equiv 0\pmod{7}$, de manera que, aplicando las propiedades de las congruencias, se verifica que $(3n^7 + 7n^3 + 11n)\equiv 0\pmod{21}$, es decir, el numerador es múltiplo de $21$ y, por tanto, $P(n)\in\mathbb{Z}$ para cada entero no negativo $n$.

### Problema 12

Demuestra que la última cifra decimal de 

$$
2^{2^n} + 1
$$ 

es $7$, para cada $n\in\mathbb{N}$, con $n>1$.

{{< hl >}}Solución:{{< /hl >}} para hallar la cifra de las unidades del número 

$$
2^{2^n} + 1,
$$ 

un posible enfoque es estudiar el valor de la congruencia de dicho número módulo $10$. Ahora bien, como $10$ no es un número primo y $mcd(2, 10)=2$, no estamos en condiciones de aplicar ninguno de los resultados teóricos asociados a *Fermat*. Analicemos, pues, el comportamiento del valor de las congruencias de las potencias de $2$ módulo $10$,

$$
\begin{aligned}
2^1&\equiv 2\pmod{10},\\\\ 2^2&\equiv 4\pmod{10},\\\\ 2^3&\equiv 8\pmod{10},\\\\ 2^4&\equiv 6\pmod{10}.
\end{aligned}
$$

A la vista de este último valor alcanzado, y teniendo en cuenta el resultado al que pretendemos arribar, bastaría comprobar que, para cada número natural, con $n>1$, $2^n$ es múltiplo de $4$. 

Por inducción, para $n=2$, $2^2=4$ que, efectivamente es múltiplo de $4$. Supongamos ahora cierta la afirmación para un número natural dado $n$, con $n\geq 2$, esto es, que existe un número entero $k$ de manera que $2^n=4k$. Sin embargo, $2^{n+1} = 2\cdot 2^n = 2\cdot(4k) = 4\cdot 2k$, es decir, la propiedad asimismo se satisface para $n+1$. El *Principio de inducción matemática* nos permite concluir que se verifica para cada número natural $n$, con $n\geq 2$.

Por tanto, al ser $2^n\equiv 0\pmod{4}$, entonces 

$$
2^{2^n}\equiv 6\pmod{10},
$$ 

hecho que se traduce en que 

$$
( 2^{2^n} + 1 )\equiv 7\pmod{10}
$$ 

o, equivalentemente, que, dadas las condiciones impuestas en el enunciado del ejercicio, la cifra de las unidades del número 

$$
2^{2^n} + 1
$$ 

es $7$.

### Problema 13

Calcula los dos últimos dígitos de $3^{1492}$.

{{< hl >}}Solución:{{< /hl >}} para encontrar los dos últimos dígitos de $3^{1492}$, un posible enfoque es hallar el valor de su congruencia módulo $100$. El número $100$ no es primo, pero sí que es cierto que $mcd(3, 100)=1$, situación que nos permite hacer uso del *Teorema de Euler-Fermat*. Este resultado afirma que 

$$
3^{\varphi(100)}\equiv 1\pmod{100}.
$$

Ahora bien, como $100 = 2^2\cdot5$, entonces 

$$
\varphi(100) = 100\left(1-\dfrac{1}{2}\right)\left(1-\dfrac{1}{5}\right) = 100\cdot\dfrac{1}{2}\cdot\dfrac{4}{5} = 40,
$$ 

y, por tanto, $3^{40}\equiv 1\pmod{100}$. De esta manera, como $1492 = 40\cdot 37 + 12$, podemos escribir

$$
\begin{aligned}
3^{1492} &= 3^{12}\cdot(3^{40})^{37}\\\\ &\equiv (3^{12}\cdot1^{37})\pmod{100}\\\\ &\equiv 3^{12}\pmod{100}\\\\ &\equiv 41\pmod{100},
\end{aligned}
$$

sin más que hacer uso de la calculadora para obtener el valor de $3^{12}$.

Alternativamente, para hallar el valor de esta última congruencia, podemos manipular la potencia, $12$, como sigue:

$$
\begin{aligned}
3^{12} &= (3^4)^3\\\\ &= 81^3\\\\ &\equiv(-19)^3\pmod{100}\\\\ &\equiv (-6859)\pmod{100}\\\\ &\equiv(-59)\pmod{100}\\\\ &\equiv 41\pmod{100},
\end{aligned}
$$

como antes, pudiéndose optar también por estrategias similares del tipo $3^{12} = 3^5\cdot 3^5\cdot 3^2$ o $3^{12} = 3^6\cdot 3^6$, entre otras. 

Así, finalmente, los dos últimos dígitos de $3^{1492}$ son $41$.

### Problema 14

Encuentra diez números compuestos consecutivos.

{{< hl >}}Solución:{{< /hl >}} dado que preguntan por diez números compuestos consecutivos cualesquiera (y no, por ejemplo, por los diez primeros números que satisfacen dicha propiedad), existen dos estrategias habituales para abordar la resolución de este tipo de ejercicios.

En primer lugar, consideremos que buscamos únicamente tres números compuestos consecutivos, en lugar de los diez que solicita el enunciado, de cara a aliviar un tanto la escritura. Tomemos entonces el factorial de $4$, $4! = 1\cdot2\cdot3\cdot4$, de manera que es cierto que:

$$
\begin{aligned}
4! + 2 &= 2\cdot(1\cdot3\cdot4 + 1),\\\\ 4! + 3 &= 3\cdot(1\cdot2\cdot4 + 1),\\\\ 4! + 4 &= 4\cdot(1\cdot2\cdot3 + 1),
\end{aligned}
$$

son tres números consecutivos compuestos. En general, dado $n\in\mathbb{N}$, si buscamos $n$ números compuestos consecutivos, una opción es considerar el número $(n+1)!$ y, a partir de él, generar el conjunto de números compuestos consecutivos siguiente: 

$$
\{(n+1)! + k: k\in\mathbb{N}, 2\leq k\leq n+1\}.
$$ 

Así, para $n=10$, siguiendo esta indicación, un conjunto de diez números compuestos consecutivos es $\\{11! + k: k\in\mathbb{N}, 2\leq k\leq 11\\}$.

Alternativamente, si no queremos trabajar con números cuya magnitud es tan severa, podemos optar por construir el producto de los primeros números primos hasta encontrar aquel que supere en valor la cantidad de números compuestos consecutivos que deseamos encontrar. Por ejemplo, para $n=3$, el mencionado producto sería $2\cdot3\cdot5$, que satisface que:

$$
\begin{aligned}
2\cdot3\cdot5 + 2 &= 2(3\cdot 5 + 1),\\\\ 2\cdot3\cdot5 + 3 &= 3(2\cdot 5 + 1),\\\\ 2\cdot3\cdot5 + 4 &= 2(3\cdot 5 + 2),
\end{aligned}
$$

son tres números consecutivos compuestos. Para $n=10$, consideraríamos entonces el conjunto 

$$
\{2\cdot3\cdot5\cdot7\cdot11 + k:k\in\mathbb{N}, 2\leq k\leq 11\},
$$ 

que contiene diez números compuestos consecutivos.

### Problema 15

Prueba que $437$ es divisor de 

- (a) $16^{99} - 1$. 
- (b) $18! + 1$.

{{< hl >}}Solución:{{< /hl >}} para ambos apartados, vamos a aprovechar que $437 = 19\cdot 23$ y, de cara a demostrar que es divisor de los números dados en los apartados (a) y (b), estudiaremos si $19$ y $23$ lo son y, en caso afirmativo, por las propiedades de las congruencias, concluiremos que $437$ los divide.

Para el apartado (a), como $19$ es un número primo y $mcd(16,19)=1$, entonces, por el *Pequeño Teorema de Fermat*, $16^{18}\equiv 1\pmod{19}$. Ahora, como $99 = 18\cdot5 + 9$, entonces

$$
\begin{aligned}
16^{99} &= 16^9\cdot(16^{18})^5\\\\ &\equiv (16^9\cdot 1^{18})\pmod{19}\\\\ &\equiv 16^9\pmod{19}\\\\ &\equiv 4^{18}\pmod{19},
\end{aligned}
$$

pero como $mcd(4,19)=1$, aplicando de nuevo el resultado anterior, $4^{18}\equiv 1\pmod{19}$, luego

$$
( 16^{99} - 1 )\equiv (1 - 1)\pmod{19}\equiv 0\pmod{19},
$$

esto es, $16^{99}-1$ es múltiplo de $19$. De manera similar, como $23$ es un número primo y $mcd(16,23)=1$, por el mismo teorema que antes sabemos que $16^{22}\equiv 1\pmod{23}$, y como $99=22\cdot4+11$, tenemos que

$$
\begin{aligned}
16^{99} &= 16^{11}\cdot(16^{22})^4\\\\ &\equiv (16^{11}\cdot 1^4)\pmod{23}\\\\ &\equiv 16^{11}\pmod{23}\\\\ &\equiv 4^{22}\pmod{23},
\end{aligned}
$$

y utilizando la estrategia previa, como $mcd(4,23)=1$, sabemos que $4^{22}\equiv 1\pmod{23}$. Así,

$$
( 16^{99} - 1 )\equiv (1 - 1)\pmod{23}\equiv 0\pmod{23},
$$

es decir, $16^{99} - 1$ es múltiplo de $23$ y, por las propiedades de las congruencias, será asimismo múltiplo de $19\cdot23=437$.

Para el apartado (b), como $19$ es un número primo, aplicando el *Teorema de Wilson*, $18!\equiv (-1)\pmod{19}$, luego 

$$
( 18! + 1 )\equiv (-1+1)\pmod{19}\equiv 0\pmod{19},
$$

esto es, $18!+1$ es múltiplo de $19$. Por otro lado, $23$ es asimismo un número primo, de manera que utilizando de nuevo el resultado anterior, $22!\equiv (-1)\pmod{23}$. Ahora bien, $22! = 22\cdot21\cdot20\cdot19\cdot18!$ y como $22\equiv (-1)\pmod{23}$, $21\equiv (-2)\pmod{23}$, $20\equiv (-3)\pmod{23}$ y $19\equiv (-4)\pmod{23}$, llegamos a que

$$
\begin{aligned}
22! &= (22\cdot21\cdot20\cdot19\cdot18!)\\\\ &\equiv ((-1)\cdot(-2)\cdot(-3)\cdot(-4)\cdot18!)\pmod{23}\\\\ &\equiv (24\cdot18!)\pmod{23}\\\\ &\equiv (1\cdot18!)\pmod{23}\\\\ &\equiv 18!\pmod{23},
\end{aligned}
$$

y juntando ambos resultados, concluimos que $18!\equiv (-1)\pmod{23}$, luego 

$$
( 18! + 1 )\equiv ( -1 + 1 )\pmod{23}\equiv 0\pmod{23},
$$

es decir, $18!+1$ es múltiplo de $23$, y como también lo era de $19$, concluimos que asimismo lo será de $19\cdot23=437$.

### Problema 16

Sea $n$ un número natural no nulo. Dado el conjunto de fracciones 

$$
A_n = \left\\{\dfrac{1}{n},\dfrac{2}{n},\dfrac{3}{n},\ldots,\dfrac{n}{n}\right\\}.
$$ 

Calcula el número de fracciones irreducibles y la suma de dichas fracciones.

{{< hl >}}Solución:{{< /hl >}} acompañemos la resolución de este ejercicio con un caso particular para $n$, con el objetivo de que esta sea así más ilustrativa. Por ejemplo, si $n=8$, el conjunto de fracciones a estudiar es

$$
A_8 = \left\\{\dfrac{1}{8},\dfrac{2}{8},\dfrac{3}{8},\dfrac{4}{8},\dfrac{5}{8},\dfrac{6}{8},\dfrac{7}{8},\dfrac{8}{8}\right\\},
$$

que contiene $4$ fracciones irreducibles,

$$
\left\\{\dfrac{1}{8},\dfrac{3}{8},\dfrac{5}{8},\dfrac{7}{8}\right\\}.
$$

Estas se caracterizan por ser aquellas en las que numerador y denominador son coprimos. Así pues, el problema se reduce a encontrar, dado un número natural $n$ no nulo, la cantidad de enteros positivos menores o iguales a $n$ y coprimos con $n$, esto es, $\varphi(n)$. 

En nuestro caso concreto, para $n=8=2^3$, efectivamente,

$$
\varphi(8) = 8\left(1 - \dfrac{1}{2}\right) = 8\cdot\dfrac{1}{2} = 4.
$$

Por tanto, recapitulando, dado $n$ un número natural no nulo, la cantidad de fracciones irreducibles que figuran en el conjunto $A_n$ es igual a $\varphi(n)$.

Para calcular su suma, si volvemos a centrar nuestra atención en el caso particular de $n=8$, tenemos que

$$
\dfrac{1}{8} + \dfrac{7}{8} = 1,\qquad \dfrac{3}{8} + \dfrac{5}{8} = 1,
$$

esto es, podemos agrupar las fracciones irreducibles de dos en dos, de manera que su suma es $1$. Efectivamente, sabemos que, dados dos números enteros $a$ y $b$, para cualquier número entero $x$ se cumple que

$$
mcd(a,b) = mcd(b,a) = mcd(a,-b) = mcd(a,b+ax).
$$

Considerando ahora un número natural $k<n$ coprimo con $n$, se tiene que $mcd(k,n)=1$, y basta tomar en el resultado anterior $a=n$, $b=(-k)$ y $x=1$ para deducir que $1 = mcd(n,k) = mcd(n,(-k))= mcd(n,n-k)$ y, así, concluimos que si la fracción $k / n$ es irreducible, asimismo lo es $(n - k) / n$. Además, trivialmente 

$$
\dfrac{k}{n} + \dfrac{n-k}{n} = 1.
$$  

Por tanto, aplicando el resultado alcanzado, la suma de las fracciones irreducibles del conjunto $A_n$ será 

$$
S = \dfrac{\varphi(n)}{2},
$$ 

quedando resuelto así el ejercicio.

### Problema 17

Demuestra que $a^{25} - a$ es divisible entre $30$ para cualquier entero $a$.

{{< hl >}}Solución:{{< /hl >}} hemos de ser capaces de probar que $(a^{25} - a)\equiv 0\pmod{30}$ para todo $a\in\mathbb{Z}$. Como $30=2\cdot3\cdot5$, veremos si la expresión es múltiplo de cada uno de los factores primos de $30$ y, en caso afirmativo, por las propiedades de las congruencias, estaremos en condiciones de concluir que asimismo será múltiplo de $30$.

Vamos a apoyarnos en el corolario del *Pequeño Teorema de Fermat*, que afirma que si $p$ es un número primo y $a\in\mathbb{Z}$, entonces $a^p\equiv a\pmod{p}$. Así, para $p=5$,

$$
\begin{aligned}
a^{25} &= (a^5)^5\\\\ &\equiv a^5\pmod{5}\\\\ &\equiv a\pmod{5},
\end{aligned}
$$

de manera que $(a^{25} - a)\equiv 0\pmod{5}$, esto es, la expresión es múltiplo de $5$. Procediendo de manera similar, para $p=3$,

$$
\begin{aligned}
a^{25} &= a\cdot (a^8)^3\\\\ &\equiv (a\cdot a^8)\pmod{3}\\\\ &\equiv (a^3)^3\pmod{3}\\\\ &\equiv a^3\pmod{3}\\\\ &\equiv a\pmod{3},
\end{aligned}
$$

y, por tanto, $(a^{25} - a)\equiv 0\pmod{3}$, es decir, la expresión es asimismo múltiplo de $3$. Finalmente, para $p=2$,

$$
\begin{aligned}
a^{25} &= a\cdot(a^{12})^2\\\\ &\equiv (a\cdot a^{12})\pmod{2}\\\\ &\equiv (a\cdot (a^6)^2)\pmod{2}\\\\ &\equiv (a\cdot a^6)\pmod{2}\\\\ &\equiv (a\cdot(a^3)^2)\pmod{2}\\\\ &\equiv (a\cdot a^3)\pmod{2}\\\\ &\equiv a^4\pmod{2}\\\\ &\equiv (a^2)^2\pmod{2}\\\\ &\equiv a^2\pmod{2}\\\\ &\equiv a\pmod{2},
\end{aligned}
$$

y, por consiguiente, $(a^{25} - a)\equiv 0\pmod{2}$, esto es, la expresión también es múltiplo de $2$. Al ser múltiplo de $2$, $3$ y $5$, por las propiedades de las congruencias podemos afirmar que $(a^{25} - a)\equiv 0\pmod{30}$, es decir, la expresión es múltiplo de $30$.

A modo de nota final, aunque nos hubiese dado la impresión de que escoger la descomposición $30=5\cdot 6$ habría acelerado la resolución de este ejercicio, hemos de ser cautos, pues $6$ no es un número primo, requisito indispensable para aplicar el resultado que nos ha permitido llevar a buen puerto este problema. En este último caso, habría sido necesario recurrir a otras herramientas para verificar la propiedad propuesta en el enunciado del ejercicio.

### Problema 18

Encuentra el número natural más pequeño con $6$ como cifra de las unidades de manera que si el $6$ se mueve al principio, el número queda multiplicado por cuatro.

{{< hl >}}Solución:{{< /hl >}} antes de abordar la resolución del ejercicio propiamente en sí, analicemos el movimiento del $6$ con un par de números en concreto para intentar detectar posibles patrones.

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
13(2x) &= 2\cdot10^m - 8,\\\\ 13x &= 10^m - 4,\\\\ x &= \dfrac{10^m - 4}{13}.
\end{aligned}
$$

Podemos ahora introducir la expresión en una calculadora científica y generar una tabla de valores para ella en función de $m$, quedándonos con el primero para el cual $x$ sea un número natural. Alternativamente, podemos actuar por tanteo, dividiendo las potencias de $10$ entre $13$ hasta dar con la primera en la que el resto de esta operación matemática sea $4$. Así,

$$
\begin{aligned}
10 &= 13\cdot 0 + 10,\\\\ 100 &= 13\cdot 7 + 9,\\\\ 1000 &= 13\cdot 76 + 12,\\\\ 10000 &= 13\cdot 769 + 3,\\\\ 100000 &= 13\cdot 7692 + 4,
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
10^m\equiv 4\pmod{13}&\Leftrightarrow 10^2\cdot10^{m-2}\equiv 4\pmod{13}\\\\ &\Leftrightarrow 10^{m - 2}\equiv (-1)\pmod{13}.
\end{aligned}
$$

Como $13$ es un número primo y $mcd(10, 13) = 1$, el *Pequeño Teorema de Fermat* afirma que $10^{12}\equiv 1\pmod{13}$. La expresión que figura en la ecuación previa no se ajusta exactamente a la anterior estructura, pero si la elevamos al cuadrado queda

$$
(10^{m-2})^2\equiv (-1)^2\pmod{13}\Leftrightarrow 10^{2m-4}\equiv 1\pmod{13},
$$

e, igualando exponentes, $2m-4 = 12$, de donde $m = 8$. Este valor, lo introduciríamos en la expresión que nos permite calcular el número $x$, hallando entonces $76927692$, cifra que sabemos no es la menor. Hemos de ser cautos aquí, puesto que el resultado asociado a *Fermat* en ningún momento afirma que el exponente dado es el menor para el que se cumple que sea congruente con uno módulo $13$. No obstante, de haber uno más pequeño, sí que será cierto que dividirá a $12$.

Por tanto, si probamos con $10^6$, encontramos que $10^6\equiv 1\pmod{13}$, e, igualando como antes exponentes, $2m-4=6$, de donde $m=5$, llegando así a la primera solución que encontramos por tanteo arriba. ¿Podría haber todavía alguna menor? Como $10^3\equiv (-1)\pmod{13}$, estamos en condiciones de descartar esa situación. Por tanto, el asociado a $m=5$ es el valor más pequeño para el que se satisface la ecuación de congruencia lineal, llevándonos a la solución $x=7692$ y permitiéndonos concluir el ejercicio tal y como hicimos por el método de tanteo.

### Problema 19

- (a) ¿En cuántos ceros acaba el número $1000!$?
- (b) Demuestra que $1000!$ no es divisible por $2^{995}$,

{{< hl >}}Solución:{{< /hl >}} para el apartado (a), nuestra labor consistiría en contar el número de dieces que podemos encontrar en la expresión de $1000! = 1\cdot2\cdot3\cdots999\cdot1000$. No estamos en condiciones de emplear directamente la *Fórmula de Legendre*, puesto que $10$ no es un número primo, pero $10=2\cdot5$, de manera que nuestra tarea se reduce a buscar el número de veces que figura $5$ en la factorización en números primos de $1000!$ (porque $2$ aparecerá con mayor frecuencia, al ser menor que $5$, por ello nos interesa solamente hallar el número de cincos). 

Así, aplicando la mencionada fórmula,

$$
\begin{aligned}
v_5(1000!) &= \left\lfloor\dfrac{1000}{5}\right\rfloor + \left\lfloor\dfrac{1000}{5^2}\right\rfloor + \left\lfloor\dfrac{1000}{5^3}\right\rfloor + \left\lfloor\dfrac{1000}{5^4}\right\rfloor\\\\ &= 200 + 40 + 8 + 1 = 249,
\end{aligned}
$$

es decir, $1000!$ acaba en $249$ ceros.

Para el apartado (b), quizá de forma un tanto rebuscada, simplemente nos preguntan por el número de veces que aparece $2$ en la factorización en números primos de $1000!$, puesto que tal valor nos permitirá verificar la propiedad enunciada. Aplicando, de nuevo, la *Fórmula de Legendre*, tenemos que

$$
\begin{aligned}
v_2(1000!) &= \left\lfloor\dfrac{1000}{2}\right\rfloor + \left\lfloor\dfrac{1000}{2^2}\right\rfloor + \cdots + \left\lfloor\dfrac{1000}{2^9}\right\rfloor\\\\ &= 500 + 250 + 125 + 62 + 31 + 15 + 7 + 3 + 1 \\\\ &= 994,
\end{aligned}
$$

luego $2^{994}|1000!$, pero $2^{995}\nmid 1000!$, como queríamos demostrar.

### Problema 20

Caracteriza aquellos números naturales cuyo número de divisores es impar.

{{< hl >}}Solución:{{< /hl >}} de partida, sabemos que los números naturales buscados no serán primos, puestos estos últimos siempre poseen una cantidad par de divisores, dos para ser más concretos: $1$ y el propio número primo. Así pues, consideremos un número natural $m$ expresado mediante su factorización en factores primos, 

$$
m=a^x b^y c^z\cdots,
$$ 

con $a,b,c,\ldots$ números primos y $x,y,z,\ldots$ números naturales. Sabemos que el número de divisores de $m$ es, en total, 

$$
(x + 1)(y + 1)(z + 1)\cdots.
$$ 

Ahora bien, nos indican que dicho producto ha de ser un número impar, hecho que traduce en que todos y cada uno de sus términos han de ser números impares (ya que bastaría con que únicamente uno fuese par para que todo el producto resultase un número par). Como $x+1, y+1, z+1,\ldots$ son números impares, inmediatamente deducimos que $x,y,z,\ldots$ serán números pares, que podrán escribirse como $x=2p, y=2q, z=2r,\ldots$ para ciertos enteros $p,q,r,\ldots$. De esta manera, 

$$
m = a^x b^y c^z\cdots = a^{2p} b^{2q} c^{2r}\cdots = (a^p b^q c^r\cdots)^2,
$$ 

esto es, los números naturales que se caracterizan por poseer una cifra impar de divisores son cuadrados perfectos. Con ello, en función de la cantidad de divisores de un número, contamos así con un criterio para decidir rápidamente si dicho número es o no un cuadrado perfecto, según su total de divisores sea o no una cifra impar.

### Problema 21

Encuentra el menor número natural $n$ tal que $n / 2$ es cuadrado perfecto, $n / 3$ es cubo perfecto y $n / 5$ es potencia quinta perfecta.

{{< hl >}}Solución:{{< /hl >}} dado que podemos dividir $n$ por $2$, $3$ y $5$ y el resultado de dichas operaciones continúa siendo un número natural (porque se trata, respectivamente de cuadrado, cubo y potencia quinta perfectos), ello implica que en su descomposición en factores primos aparecerán los términos $2^x$, $3^y$ y $5^z$, con $x, y, z\geq 1$. En ejercicios anteriores también considerábamos la posibilidad de un término entero $k$ que agrupaba potencias de números primos distintos a los tres mencionados anteriormente, pero, en esta ocasión, como nuestro objetivo es hallar el menor natural $n$ que satisface las condiciones del enunciado del ejercicio, asumiremos que $k=1$. Así, $n=2^x 3^y 5^z$.

Ahora bien, como $n / 2 = 2^{x-1} 3^y 5^z$ es un cuadrado perfecto, los exponentes de la factorización dada serán múltiplos de dos ($x-1=\dot{2}$, $y=\dot{2}$, $z=\dot{2}$). Al ser $n / 3 = 2^x 3^{y-1} 5^z$ un cubo perfecto, los exponentes anteriores serán múltiplos de $3$ ($x=\dot{3}$, $y-1=\dot{3}$, $z=\dot{3}$). Finalmente, como $n / 5 = 2^x 3^y 5^{z-1}$ es una potencia quinta perfecta, los exponentes previos serán múltiplos de $5$ ($x=\dot{5}$, $y=\dot{5}$, $z-1=\dot{5}$).

Así pues, para $x$ surge el siguiente sistema de congruencias lineales

$$
\begin{aligned}
x-1&\equiv 0\pmod{2},\\\\ x&\equiv 0\pmod{3},\\\\ x&\equiv 0\pmod{5},
\end{aligned}
$$

que podemos resolver utilizando el *Teorema chino del resto*, aunque por tanteo es sencillo en este caso hallar la solución. Al ser múltiplo de $3$ y $5$, lo será de $15$. Entre los múltiplos de este último, hemos de buscar aquel que al restarle una unidad el resultado sea múltiplo de $2$. Son candidatos $15,45,75,\ldots$, pero como estamos interesados en encontrar el menor natural $n$, escogemos como solución final $x=15$.

Análogamente, para $y$ aparece el siguiente sistema de congruencias lineales

$$
\begin{aligned}
y&\equiv 0\pmod{2},\\\\ y-1&\equiv 0\pmod{3},\\\\ y&\equiv 0\pmod{5},
\end{aligned}
$$

que podemos resolver utilizando el *Teorema chino del resto*, aunque por tanteo es sencillo en este caso hallar la solución. Al ser múltiplo de $2$ y $5$, lo será de $10$. Entre los múltiplos de este último, hemos de buscar aquel que al restarle una unidad el resultado sea múltiplo de $3$. Son candidatos $10,40,70,\ldots$, pero como estamos interesados en encontrar el menor natural $n$, escogemos como solución final $y=10$.

Finalmente, para $z$ encontramos el siguiente sistema de congruencias lineales

$$
\begin{aligned}
z&\equiv 0\pmod{2},\\\\ z&\equiv 0\pmod{3},\\\\ z-1&\equiv 0\pmod{5},
\end{aligned}
$$

que podemos resolver utilizando el *Teorema chino del resto*, aunque por tanteo es sencillo en este caso hallar la solución. Al ser múltiplo de $2$ y $3$, lo será de $6$. Entre los múltiplos de este último, hemos de buscar aquel que al restarle una unidad el resultado sea múltiplo de $5$. Son candidatos $6,36,66,\ldots$, pero como estamos interesados en encontrar el menor natural $n$, escogemos como solución final $z=6$.

Por tanto, el menor número natural $n$ tal que $n/2$ es cuadrado perfecto, $n/3$ es cubo perfecto y $n/5$ es potencia quinta perfecta es $n=2^{15} \cdot 3^{10} \cdot 5^6$.

### Problema 22

¿Cuántas cifras tiene el menor número que cumple que, cuando la primera cifra de la izquierda se coloca en el último lugar de la derecha, el número que resulta es una vez y media el número inicial?

{{< hl >}}Solución:{{< /hl >}} antes de abordar la resolución del ejercicio propiamente dicho, veamos con un par de ejemplos la manera de proceder, para así intentar detectar patrones. Por ejemplo, si consideramos el número $354$, podemos aislar la primera cifra escribiéndolo como $300 + 54$, es decir, $3 \cdot 10^2 + 54$. Ahora, si colocamos la primera cifra en el último lugar de la derecha, el número pasa a ser $543$, y como deseamos aislar de nuevo el $3$, podemos escribirlo como $540 + 3$ o, equivalentemente, como $54\cdot10 + 3$. Por desgracia, no se cumple para este ejemplo la condición exigida en el enunciado del ejercicio, puesto que 

$$
\dfrac{3}{2}\cdot 354 = 531\neq 543.
$$ 

Si ahora consideramos el número $4537 = 4\cdot10^3 + 537$, después conformaríamos el número $5374=537\cdot10 + 4$ y, desgraciadamente, 

$$
\dfrac{3}{2}\cdot4537 = 6805.5\neq 5374.
$$ 

No obstante, estos dos intentos fallidos nos permiten atisbar los protagonistas de este ejercicio: la primera cifra del número buscado, que denotaremos como $A$ y el resto del número, que señalaremos como $B$. Así, dado un número de $n$ cifras, buscamos que se satisfaga la ecuación 

$$
\dfrac{3}{2}(A\cdot10^{n-1} + B) = B\cdot10 + A.
$$ 

Operando algebraicamente, llegamos a que

$$
\begin{aligned}
3A\cdot10^{n-1} + 3B &= 20B+2A,\\\\ 17B &= 3A\cdot10^{n-1} - 2A,\\\\ 17B &= A(3\cdot10^{n-1} - 2),\\\\ B &= \dfrac{A(3\cdot10^{n-1} - 2)}{17}.
\end{aligned}
$$

Ahora bien, como $A$ es la primera cifra del número buscado, es cierto que $1\leq A\leq 9$, luego no puede ser múltiplo de $17$, hecho que nos permite concluir que $3\cdot10^{n-1} - 2$ es divisible por $17$. Para hallar el valor de $n$, podemos optar por dividir, sucesivamente, números de la forma $30, 300, 3000,\ldots$, entre $17$ hasta dar con el dividendo adecuado que arroja un resto para la división que ascienda a $2$.

Alternativamente, usando congruencias, que $3\cdot10^{n-1} - 2$ sea múltiplo de $17$ es equivalente a escribir 

$$
(3\cdot10^{n-1} - 2)\equiv 0\pmod{17},
$$ 

esto es, 

$$
3\cdot10^{n-1} \equiv 2\pmod{17}.
$$ 

Multiplicando toda la ecuación de congruencia lineal por $6$ (ya que $3\cdot6=18$, cifra que queda muy cercana a un múltiplo de $17$) queda 

$$
18\cdot10^{n-1} \equiv 12\pmod{17},
$$ 

es decir, 

$$
10^{n-1} \equiv 12\pmod{17}.
$$

Nos aproximamos a la estructura de un resultado muy conocido de *Teoría de números*, por lo que podemos investigar qué sucede al multiplicar ahora por $10$ la ecuación de congruencia lineal. Así,

$$
10^{n-1} \equiv 12\pmod{17}\Leftrightarrow 10^n\equiv 120\pmod{17}\equiv 1\pmod{17},
$$

y como $17$ es un número primo y $mcd(10,17)=1$, entonces, por el *Pequeño Teorema de Fermat*, sabemos que $10^{16} \equiv 1\pmod{17}$. 

Igualando términos con la anterior ecuación de congruencia lineal, concluimos que $n=16$. No obstante, dicho resultado no garantiza haber encontrado el menor número natural que verifica esa propiedad, por lo que hemos de proceder con cautela y seguir investigando. No obstante, como $10^8 \equiv (-1)\pmod{17}$ (a modo anecdótico, si hubiera salido $10^8 \equiv 1\pmod{17}$, hubiésemos tenido que probar con $10^4$ y así sucesivamente), en esta ocasión sí podemos concluir que el resultado teórico nos ha llevado al menor valor de $n$ para el que se satisface la propiedad. Así, el menor número que cumple que, cuando la primera cifra de la izquierda se coloca en el último lugar de la derecha, el número que resulta es una vez y media el número inicial posee $16$ cifras.

### Problema 23

Un cierto número de billetes se reparten entre siete subalternos y dos jefes, teniendo en cuenta que un jefe cobra el doble que un subalterno. Tras el reparto, sobran seis billetes; pero si hubiese faltado un jefe, el reparto habría salido exacto. Por otro lado, si hubiera faltado un subalterno, serían entonces ocho los billetes que habrían sobrado. Calcular el menor número positivo de billetes que cobraron cada uno.

{{< hl >}}Solución:{{< /hl >}} la clave para resolver este ejercicio es plantearse la cuestión: ''¿entre cuántas partes hay que repartir el total de billetes?''. Como cada jefe cobra por dos subalternos, en verdad son once las partes entre las que repartir. 

Así, si denotamos por $x$ el número de billetes, la primera ecuación de congruencia lineal es $x\equiv 6\pmod{11}$, pues se reparte entre las once partes y sobran (es decir, el resto asciende a) seis. Cuando falta un jefe, son entonces nueve las partes entre las que repartir, y al ser exacto dicho reparto se traduce entonces en la ecuación de congruencia lineal $x\equiv 0\pmod{9}$. Finalmente, cuando falta un subalterno, son diez las partes entre las que repartir, y como sobran ocho billetes, la correspondiente ecuación de congruencia lineal es $x\equiv 8\pmod{10}$. 

En resumen, hemos de resolver el sistema de congruencias lineales,

$$
\begin{aligned}
x&\equiv 6\pmod{11},\\\\ x&\equiv 0\pmod{9},\\\\ x&\equiv 8\pmod{10}.
\end{aligned}
$$

Como $mcd(9,10,11)=1$, esto es, son primos entre sí los tres números, por el *Teorema chino del resto* estamos en condiciones de asegurar que existe solución módulo $9\cdot10\cdot11 = 990$. Ahora bien,

$$
M_1=90,\qquad M_2=110,\qquad M_3=99,
$$

por lo que el siguiente paso es resolver las ecuaciones de congruencias lineales,

$$
\begin{aligned}
90x&\equiv 1\pmod{11}\Leftrightarrow 2x\equiv 1\pmod{11}\Leftrightarrow x\equiv 1\pmod{11},\\\\ 110x&\equiv 1\pmod{9}\Leftrightarrow 2x\equiv 1\pmod{9}\Leftrightarrow x\equiv 5\pmod{11},\\\\ 99x&\equiv 1\pmod{10}\Leftrightarrow (-x)\equiv 1\pmod{10}\Leftrightarrow x\equiv (-1)\pmod{11}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
x&\equiv 6\pmod{11},& 90x&\equiv 1\pmod{11},& x&\equiv 6\pmod{11},\\\\ x&\equiv 0\pmod{9},& 110x&\equiv 1\pmod{9},& x&\equiv 5 \pmod{9},\\\\ x&\equiv 8\pmod{10},& 99x&\equiv 1\pmod{10},& x&\equiv (-1)\pmod{10},
\end{aligned}
$$

la solución al sistema queda

$$
\begin{aligned}
x &\equiv (6\cdot90\cdot6 + 0\cdot110\cdot5 + 8\cdot99\cdot(-1))\pmod{990}\\\\ 
&\equiv 2448\pmod{990}\equiv 468\pmod{990}.
\end{aligned}
$$

Nótese que podíamos habernos ahorrado los cálculos asociados a la segunda ecuación del sistema, por aquel $0$ que figura en la misma. Por tanto, el menor número positivo de billetes a repartir es $468$, y como $468 = 11\cdot42 + 6$, concluimos que los subalternos cobran $42$ billetes, mientras que los jefes $84$ billetes.

### Problema 24

Un general cuenta el número de soldados supervivientes de una batalla alineándolos, sucesivamente, en filas de diferentes tamaños. En cada ocasión, anota el total que quedaron sin poder completar una fila. Disponía de $1200$ combatientes antes de la refriega. Tras el encuentro si los alineaba en filas de $5$, quedaban $3$ sin poder completar una fila; si lo hacía en filas de $6$, volvían a quedar $3$ sin poder completar una fila; si los repartía en filas de $7$, únicamente uno quedaba fuera de las filas y si los alineaba en filas de $11$, no quedaba soldado alguno que no estuviese en una fila ¿Cuántos soldados sobrevivieron la batalla?

{{< hl >}}Solución:{{< /hl >}} consideremos $x$ el número de soldados supervivientes de la batalla, cantidad que sabemos es menor o igual que $1200$ por ser este el número de los que disponía el general inicialmente, es decir, $0\leq x\leq 1200$.

Las sucesivas alineaciones de los soldados, las traducimos en el siguiente sistema de congruencias lineales,

$$
\begin{aligned}
x&\equiv 3\pmod{5},\\\\ x&\equiv 3\pmod{6},\\\\ x&\equiv 1\pmod{7},\\\\ x&\equiv 0\pmod{11}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=5$, $m_2=6$, $m_3=7$ y $m_4=11$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=5\cdot6\cdot7\cdot11 = 2310$. Procedamos entonces al cálculo de las soluciones utilizando el método habitual. Así,

$$
\begin{aligned}
M_1 &= \dfrac{M}{m_1} = \dfrac{2310}{5} = 6\cdot7\cdot11 = 462,\\\\ M_2 &= \dfrac{M}{m_2} = \dfrac{2310}{6} = 5\cdot7\cdot11 = 385,\\\\ M_3 &= \dfrac{M}{m_3} = \dfrac{2310}{7} = 5\cdot6\cdot11 = 330,\\\\ M_4 &= \dfrac{M}{m_4} = \dfrac{2310}{11} = 5\cdot6\cdot7 = 210,
\end{aligned}
$$

y, a continuación, resolvemos las siguientes ecuaciones de congruencia lineales:

$$
\begin{aligned}
462x\equiv 1\pmod{5}&\Leftrightarrow 2x\equiv 1\pmod{5}\\\\ &\Leftrightarrow 6x\equiv 3\pmod{5}\\\\ &\Leftrightarrow x\equiv 3\pmod{5},\\\\ 385x\equiv 1\pmod{6}&\Leftrightarrow x\equiv 1\pmod{6},\\\\ 330x\equiv 1\pmod{7}&\Leftrightarrow x\equiv 1\pmod{7},\\\\ 210x\equiv 1\pmod{11}&\Leftrightarrow x\equiv 1\pmod{11}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
x&\equiv 3\pmod{5},& 462x&\equiv 1\pmod{5},& x&\equiv 3\pmod{5},\\\\ x&\equiv 3\pmod{6},& 385x&\equiv 1\pmod{6},& x&\equiv 1\pmod{6},\\\\ x&\equiv 1\pmod{7},& 330x&\equiv 1\pmod{7},& x&\equiv 1\pmod{7},\\\\ x&\equiv 0\pmod{11},& 210x&\equiv 1\pmod{11},& x&\equiv 1\pmod{11},
\end{aligned}
$$

entonces la solución es 

$$
\begin{aligned}
x &\equiv (3\cdot462\cdot3 + 3\cdot385\cdot1 + 1\cdot330\cdot1 + 0\cdot210\cdot1)\pmod{2310}\\\\ &\equiv 5643\pmod{2310}\equiv 1023\pmod{2310},
\end{aligned}
$$

esto es, asciende a $1023$ el número de soldados que sobrevivieron a la batalla.

### Problema 25

Ana, Belén, Carlos y David acuden, con bastante ilusión y mucha algarabía, a un concierto de *31Knots*; pero, en mitad de la cola, tras un rápido y certero cálculo de Ana, desgraciadamente se dan cuenta de que les faltan algunos euros para poder comprar las entradas, cuyo precio asciende a $50$ euros por tique.

Cada uno de ellos posee una cifra entera mayor o igual que cero de euros y, curiosamente, además

- si Belén le pide un euro a Ana, consigue acumular dos tercios de la cantidad que le quedaría a Ana;
- si Carlos toma prestados dos euros de Belén, llega a acumular tres quintos de la cantidad que le quedaría a Belén;
- si David le pide tres euros a Carlos, consigue acumular cinco séptimos de la cantidad que le quedaría a Carlos.

¿Cuál es la mínima cantidad de euros que necesitarían entre todos para poder así permitirse la adquisición de las cuatro entradas?

{{< hl >}}Solución:{{< /hl >}} por comodidad en la escritura, denotemos el dinero que posee cada uno, en euros, de los cuatro protagonistas del enunciado del ejercicio por sus iniciales en minúscula, esto es, $a$, $b$, $c$ y $d$. Sabemos, dado que no pueden comprar las cuatro entradas para disfrutar del concierto, que $a+b+c+d<4\cdot50=200$. Hallemos cuánto dinero lleva encima cada uno de ellos haciendo uso de las condiciones que aparecen, que, matemáticamente, podemos expresar como sigue:

$$
\begin{aligned}
b+1 &= \dfrac{2}{3}(a-1),\\\\ c+2 &= \dfrac{3}{5}(b-2),\\\\ d+3 &= \dfrac{5}{7}(c-3).
\end{aligned}
$$

Despejando $b$, $c$ y $d$, encontramos que

$$
\begin{aligned}
b&=\dfrac{2a-5}{3},\\\\ c&=\dfrac{3b-16}{5},\\\\ d&=\dfrac{5c-36}{7},
\end{aligned}
$$

que, expresadas todas ellas en función del valor de $a$, equivalen a

$$
\begin{aligned}
b&=\dfrac{2a-5}{3},\\\\ c&=\dfrac{3b-16}{5} = \dfrac{3\cdot\dfrac{2a-5}{3} - 16}{5}=\dfrac{2a-21}{5},\\\\ d&=\dfrac{5c-36}{7} = \dfrac{5\cdot\dfrac{2a-21}{5} - 36}{7} = \dfrac{2a-57}{7}.
\end{aligned}
$$

Recordemos ahora que $b$, $c$ y $d$ llevan encima una cantidad entera mayor o igual que cero de euros, hecho que se traduce en que

$$
\begin{aligned}
(2a-5)&\equiv 0\pmod{3},\\\\ (2a-21)&\equiv 0\pmod{5},\\\\ (2a-57)&\equiv 0\pmod{7}.
\end{aligned}
$$

Llegados a este momento, comenzamos a sospechar que el camino nos lleva, irremediablemente, a buscar el valor de $a$ vía el *Teorema chino del resto*, por lo que, previamente, vamos a adaptar la forma del sistema de ecuaciones de congruencias lineales a la que figura en el resultado teórico. Así,

$$
\begin{aligned}
(2a-5)\equiv 0\pmod{3}&\Leftrightarrow 2a\equiv 5\pmod{3}\Leftrightarrow 4a\equiv 10\pmod{3}\\\\ &\Leftrightarrow a\equiv 1\pmod{3},\\\\ (2a-21)\equiv 0\pmod{5}&\Leftrightarrow 2a\equiv 1\pmod{5}\Leftrightarrow 6a\equiv 3\pmod{5}\\\\ &\Leftrightarrow a\equiv 3\pmod{5},\\\\ (2a-57)\equiv 0\pmod{7}&\Leftrightarrow 2a\equiv 1\pmod{7}\Leftrightarrow 8a\equiv 4\pmod{7}\\\\ &\Leftrightarrow a\equiv 4\pmod{7}.
\end{aligned}
$$

Esto es, recapitulando, la cantidad total de euros que lleva encima Ana (es decir, el valor de $a$), resulta ser la solución del siguiente sistema de ecuaciones de congruencias lineales

$$
\begin{aligned}
a&\equiv 1\pmod{3},\\\\ a&\equiv 3\pmod{5},\\\\ a&\equiv 4\pmod{7}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=3, m_2=5$ y $m_3=7$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=3\cdot5\cdot7 = 105$. Procedamos entonces al cálculo de las soluciones utilizando el método habitual. Así,

$$
\begin{aligned}
M_1 &= \dfrac{M}{m_1} = \dfrac{105}{3} = 5\cdot7 = 35,\\\\ M_2 &= \dfrac{M}{m_2} = \dfrac{105}{5} = 3\cdot7 = 21,\\\\ M_3 &= \dfrac{M}{m_3} = \dfrac{105}{7} = 3\cdot5 = 15,
\end{aligned}
$$

y, a continuación, resolvemos las siguientes ecuaciones de congruencia lineales:

$$
\begin{aligned}
35a\equiv 1\pmod{3}&\Leftrightarrow (-a)\equiv 1\pmod{3}\Leftrightarrow a\equiv 2\pmod{3},\\\\ 21a\equiv 1\pmod{5}&\Leftrightarrow a\equiv 1\pmod{5},\\\\ 15a\equiv 1\pmod{7}&\Leftrightarrow a\equiv 1\pmod{7}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
a&\equiv 1\pmod{3},& 35a&\equiv 1\pmod{3},& a&\equiv 2\pmod{3},\\\\ a&\equiv 3\pmod{5},& 21a&\equiv 1\pmod{5},& a&\equiv 1\pmod{5},\\\\ a&\equiv 4\pmod{7},& 15a&\equiv 1\pmod{7},& a&\equiv 1\pmod{7},
\end{aligned}
$$

entonces la solución es 

$$
\begin{aligned}
a &\equiv (1\cdot35\cdot2 + 3\cdot21\cdot1 + 4\cdot15\cdot1)\pmod{105}\\\\ &\equiv 193\pmod{105}\\\\ &\equiv 88\pmod{105},
\end{aligned}
$$

esto es, Ana lleva encima $88$ euros. Como $a=88$, entonces

$$
\begin{aligned}
b&=\dfrac{2\cdot88-5}{3} = 57,\\\\ c&=\dfrac{2\cdot88-21}{5} = 31,\\\\ d&=\dfrac{2\cdot88-57}{7} = 17,
\end{aligned}
$$

es decir, Belén, Carlos y David llevan encima, respectivamente, $57$, $31$ y $17$ euros. En total suman $88+57+31+17=193$ euros, por lo que les faltan $200-193=7$ euros para poder comprar las cuatro entradas y así disfrutar del concierto.

Alternativamente, volvamos al momento del ejercicio en el que declaramos que

$$
\begin{aligned}
b+1 &= \dfrac{2}{3}(a-1),\\\\ c+2 &= \dfrac{3}{5}(b-2),\\\\ d+3 &= \dfrac{5}{7}(c-3).
\end{aligned}
$$

Si operamos algebraicamente las ecuaciones

$$
\begin{aligned}
3b+3 &= 2a-2 \Rightarrow 3b-2a = -5,\\\\ 5c+10 &= 3b-6 \Rightarrow 5c-3b=-16,\\\\ 7d+21 &= 5c-15 \Rightarrow 7d-5c=-36,
\end{aligned}
$$

y sumamos ahora las tres, llegamos a la ecuación diofántica $7d-2a=-57$, que, despejando la variable $a$ por ser aquella cuyo coeficiente asociado es más reducido, se tiene que

$$
a = \dfrac{7d+57}{2}.
$$

Para $d=1$, encontramos que $a=32$, arribando así a la solución particular de dicha ecuación diofántica. Su solución general es pues

$$
\begin{aligned}
a &= 32 + 7t,\\\\ d &= 1 + 2t,
\end{aligned}
$$

con $t$ número entero. Sustituyendo estos resultados alcanzados en las ecuaciones de arriba, estamos en condiciones de encontrar las expresiones para $b$ y $c$. Así,

$$
\begin{aligned}
b &= \dfrac{-5 + 2(32+7t)}{3},\\\\ c &= \dfrac{36 + 7(1+2t)}{5}.
\end{aligned}
$$

Ahora bien, estamos interesados en el valor entero de $t$ que nos proporciona la mínima cantidad de euros que necesitarían entre todos para poder así permitirse la adquisición de las cuatro entradas (y con la restricción añadida implícita de que las soluciones han de ser enteras). Como inicialmente no disponen de la cantidad necesaria, ello implica que $a+b+c+d<200$, y, sustituyendo las anteriores expresiones alcanzadas para cada una de las cuatro variables, generamos la inecuación

$$
\begin{aligned}
32+7t+1+2t+\dfrac{-5 + 2(32+7t)}{3}+\dfrac{36 + 7(1+2t)}{5}&<200\\\\ 480+105t+15+30t-25+320+70t+108+21+42t&<3000,\\\\ 247t&<2081,
\end{aligned}
$$

esto es, $t<8.43$. Así pues, empezando por $t=8$ (y continuando con $t=7$, $t=6$, etc.), sustituiremos arriba, hasta dar con el primer valor que genere cifras enteras para $a$, $b$, $c$ y $d$. Por tanto, si $t=8$,

$$
\begin{aligned}
a &= 32+7\cdot8 = 88,\\\\ b &= \dfrac{-5 + 2(32+7\cdot8)}{3} = 57,\\\\ c &= \dfrac{36 + 7(1+2\cdot8)}{5} = 31,\\\\ d &= 1+2\cdot8 = 17,
\end{aligned}
$$

llegando, afortunadamente, en el primer intento a la solución alcanzada por el método de las congruencias.

### Problema 26

Brahmagupta tiene una enorme cesta repleta de huevos camperos. Si los saca de $2$ en $2$, resulta que queda un huevo en la cesta. Si opta por extraerlos de $3$ en $3$, ahora $2$ son los huevos que restan en la cesta. Análogamente, si realiza el proceso utilizando grupos de $4$, $5$ y $6$ huevos, quedan en la cesta, respectivamente, $3$, $4$ y $5$ huevos. Sin embargo, si los saca de $7$ en $7$, la cesta se vacía por completo. ¿Cuál es la menor cantidad de huevos que puede haber en la cesta de Brahmagupta?

{{< hl >}}Solución:{{< /hl >}} consideremos $x$ el número de huevos que se encuentran en la cesta de Brahmagupta. Los distintos modos de extracción dan lugar al siguiente sistema de ecuaciones de congruencias lineales,

$$
\begin{aligned}
x&\equiv 1\pmod{2},\\\\ x&\equiv 2\pmod{3},\\\\ x&\equiv 3\pmod{4},\\\\ x&\equiv 4\pmod{5},\\\\ x&\equiv 5\pmod{6},\\\\ x&\equiv 0\pmod{7}.
\end{aligned}
$$

Por desgracia, no podemos aplicar directamente el *Teorema chino del resto*, pues algunos módulos no son primos entre sí. No obstante, como estamos en las condiciones de la proposición que generaliza este resultado teórico (las comprobaciones sobre los pares de congruencias se pueden llevar a cabo mentalmente de forma sencilla), sabemos que el sistema de ecuaciones de congruencias lineales posee solución. Para hallarla, desdoblando la ecuación de congruencia lineal $x\equiv 5\pmod{6}$, queda

$$
\begin{aligned}
x&\equiv 1\pmod{2},\\\\ x&\equiv 2\pmod{3},\\\\ x&\equiv 3\pmod{4},\\\\ x&\equiv 4\pmod{5},\\\\ x&\equiv 5\pmod{2}\equiv 1\pmod{2},\\\\ x&\equiv 5\pmod{3}\equiv 2\pmod{3},\\\\ x&\equiv 0\pmod{7}.
\end{aligned}
$$

Encontramos dos ecuaciones de congruencias lineales repetidas, cuya escritura podemos ahorrarnos, de manera que llegamos a que

$$
\begin{aligned}
x&\equiv 1\pmod{2},\\\\ x&\equiv 2\pmod{3},\\\\ x&\equiv 3\pmod{4},\\\\ x&\equiv 4\pmod{5},\\\\ x&\equiv 0\pmod{7}.
\end{aligned}
$$

Llegados a este punto, la primera y la tercera ecuación involucran módulos de manera que uno es un factor del otro $4=2^2$. Por tanto, tenemos entre manos una posible contradicción aquí que hemos de investigar para hallar si existe o no dicha contradicción. No obstante, para cierto número entero $t$,

$$
\begin{aligned}
x\equiv 3\pmod{4}&\Rightarrow x = 3+4t\Rightarrow x = 1 + 2(1+2t)\\\\ &\Rightarrow x\equiv 1\pmod{2},
\end{aligned}
$$

luego la primera ecuación de congruencia lineal es redundante y la podremos suprimir del sistema, quedando pues

$$
\begin{aligned}
x&\equiv 2\pmod{3},\\\\ x&\equiv 3\pmod{4},\\\\ x&\equiv 4\pmod{5},\\\\ x&\equiv 0\pmod{7}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=3$, $m_2=4$, $m_3=5$ y $m_4=7$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=3\cdot4\cdot5\cdot7 = 420$. Procedamos entonces al cálculo de las soluciones utilizando el método habitual. Así,

$$
\begin{aligned}
M_1 &= \dfrac{M}{m_1} = \dfrac{420}{3} = 4\cdot5\cdot7 = 140,\\\\ M_2 &= \dfrac{M}{m_2} = \dfrac{420}{4} = 3\cdot5\cdot7 = 105,\\\\ M_3 &= \dfrac{M}{m_3} = \dfrac{420}{5} = 3\cdot4\cdot7 = 84,\\\\ M_4 &= \dfrac{M}{m_4} = \dfrac{420}{7} = 3\cdot4\cdot5 = 60,
\end{aligned}
$$

y, a continuación, resolvemos las siguientes ecuaciones de congruencia lineales:

$$
\begin{aligned}
140x\equiv 1\pmod{3}&\Leftrightarrow 2x\equiv 1\pmod{3}\Leftrightarrow 4x\equiv 2\pmod{3}\\\\ &\Leftrightarrow x\equiv 2\pmod{3},\\\\ 105x\equiv 1\pmod{4}&\Leftrightarrow x\equiv 1\pmod{4},\\\\ 84x\equiv 1\pmod{5}&\Leftrightarrow (-x)\equiv 1\pmod{5}\Leftrightarrow x\equiv 4\pmod{5},\\\\ 60x\equiv 1\pmod{7}&\Leftrightarrow 4x\equiv 1\pmod{7}\Leftrightarrow 8x\equiv 2\pmod{7}\\\\ &\Leftrightarrow x\equiv 2\pmod{7}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
x&\equiv 2\pmod{3},& 140x&\equiv 1\pmod{3},& x&\equiv 2\pmod{3},\\\\ x&\equiv 3\pmod{4},& 105x&\equiv 1\pmod{4},& x&\equiv 1\pmod{4},\\\\ x&\equiv 4\pmod{5},& 84x&\equiv 1\pmod{5},& x&\equiv 4\pmod{5},\\\\ x&\equiv 0\pmod{7},& 60x&\equiv 1\pmod{7},& x&\equiv 2\pmod{7},
\end{aligned}
$$

entonces la solución es 

$$
\begin{aligned}
x &\equiv (2\cdot140\cdot2 + 3\cdot105\cdot1 + 4\cdot84\cdot4 + 0\cdot60\cdot1)\pmod{420}\\\\ &\equiv 2219\pmod{420}\equiv 119\pmod{420},
\end{aligned}
$$

esto es, la cesta de Brahmagupta contaba con $119$ huevos.

### Problema 27

Los cometas *2p/Encke*, *4P/Faye* y *8p/Tuttle* tienen períodos orbitales de $3$, $8$ y $13$ años, respectivamente. Los últimos perihelios (punto más cercano de la órbita de un cuerpo celeste alrededor del Sol) de cada uno de ellos fueron en $2017$, $2014$ y $2008$, respectivamente. ¿Cuál será el siguiente año en el cual coincidan sus perihelios? (Para este problema, asume que el tiempo se mide en años completos y que cada período orbital es constante.)

{{< hl >}}Solución:{{< /hl >}} sea $x$ el valor entero del siguiente año en el cual coinciden los perihelios. Como el cometa *2p/Encke* tiene una órbita de la forma $2017+3t$, con $t$ un número entero, entonces $x\equiv 2017\pmod{3}$. Análogamente, dado el cometa *4p/Faye* posee una órbita de la forma $2014+8u$, con $u$ número entero, entonces $x\equiv 2014\pmod{8}$. Finalmente, debido a que el cometa *8p/Tuttle* tiene una órbita de la forma $2008+13v$, con $v$ número entero, entonces $x\equiv 2008\pmod{13}$.

Así pues, hemos de resolver el siguiente sistema de ecuaciones de congruencias lineales,

$$
\begin{aligned}
x&\equiv 2017\pmod{3}\equiv 1\pmod{3},\\\\ x&\equiv 2014\pmod{8}\equiv 6\pmod{8}\\\\ x&\equiv 2008\pmod{13}\equiv 6\pmod{13}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=3$, $m_2=8$ y $m_3=13$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=3\cdot8\cdot13 = 312$. Procedamos entonces al cálculo de las soluciones utilizando el método habitual. Así,

$$
\begin{aligned}
M_1 &= \dfrac{M}{m_1} = \dfrac{312}{3} = 8\cdot13 = 104,\\\\ M_2 &= \dfrac{M}{m_2} = \dfrac{312}{8} = 3\cdot13 = 39,\\\\ M_3 &= \dfrac{M}{m_3} = \dfrac{312}{13} = 3\cdot8 = 24,
\end{aligned}
$$

y, a continuación, resolvemos las siguientes ecuaciones de congruencia lineales:

$$
\begin{aligned}
104x\equiv 1\pmod{3}&\Leftrightarrow 2x\equiv 1\pmod{3}\\\\ &\Leftrightarrow x\equiv 2\pmod{3},\\\\ 39x\equiv 1\pmod{8}&\Leftrightarrow (-x)\equiv 1\pmod{8}\\\\ &\Leftrightarrow x\equiv (-1)\pmod{8},\\\\ 24x\equiv 1\pmod{13}&\Leftrightarrow (-2x)\equiv 1\pmod{13}\\\\ &\Leftrightarrow (-12x)\equiv 6\pmod{13}\\\\ &\Leftrightarrow x\equiv 6\pmod{13}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
x&\equiv 1\pmod{3},& 104x&\equiv 1\pmod{3},& x&\equiv 2\pmod{3},\\\\ x&\equiv 6\pmod{8},& 39x&\equiv 1\pmod{8},& x&\equiv (-1)\pmod{8},\\\\ x&\equiv 6\pmod{13},& 24x&\equiv 1\pmod{13},& x&\equiv 6\pmod{13},
\end{aligned}
$$

entonces la solución es 

$$
\begin{aligned}
x &\equiv (1\cdot104\cdot2 + 6\cdot39\cdot(-1) + 6\cdot24\cdot1)\pmod{312}\\\\ &\equiv 838\pmod{312}\equiv 214\pmod{312},
\end{aligned}
$$

esto es, en los años de la forma $214+316w$, con $w$ número entero, coinciden los tres perihelios. Para $w=5$, encontramos que el año $1794$ fue el último en el que coincidieron, mientras que si $w=6$, hallamos que $2086$ será el próximo año en el que coincidan.

### Problema 28

Encuentra los tres últimos dígitos del número 

$$
N=3\times7\times11\times15\times\cdots\times2019.
$$

{{< hl >}}Solución:{{< /hl >}} como estamos interesados en encontrar los tres últimos dígitos del producto de números dado, un posible enfoque de cara a la resolución de este ejercicio es encontrar el valor de la congruencia de dicho producto módulo $1000$, esto es, resolver $x\equiv N\pmod{1000}$. Ahora bien, como $1000 = 2^3 \cdot 5^3 = 8\cdot 125$ y $mcd(8,125)=1$ sabemos, por el *Teorema chino del resto*, que la anterior ecuación de congruencia lineal es equivalente al siguiente sistema de ecuaciones de congruencias lineales,

$$
\begin{aligned}
x&\equiv N\pmod{8},\\\\ x&\equiv N\pmod{125}.
\end{aligned}
$$

Sin embargo, dado que en el producto $N$ aparecen, por ejemplo, los números $15 = 3\cdot5$, $35 = 5\cdot7$ y $55 = 5\cdot11$, resulta que encontraríamos $5^3$ en dicho producto, provocando que $N\equiv 0\pmod{125}$, esto es, $N$ es múltiplo de $125$. Por otro lado,

$$
\begin{aligned}
3&\equiv 3\pmod{8},\\\\ 7&\equiv (-1)\pmod{8},\\\\ 11&\equiv 3\pmod{8},\\\\ 15&\equiv (-1)\pmod{8},
\end{aligned}
$$

por tanto 

$$
\begin{aligned}
(3\cdot7\cdot11\cdot15)&\equiv (3\cdot(-1)\cdot3\cdot(-1))\pmod{8}\\\\ &\equiv 9\pmod{8}\equiv 1\pmod{8}.
\end{aligned}
$$

Al ser los términos del producto $N$ de la forma $3+4t$, con $t$ número entero mayor o igual que cero, la anterior situación se reproduce cada cuatro términos del mencionado producto. Así, como $3+4t=2019$ implica que $t=504$ y empezamos la sucesión en $t=0$, $N$ está compuesto por $505$ términos, de forma que podemos conseguir $126$ grupos de $4$ elementos, quedando sin agrupar el último término, $2019$, que sabemos cumple $2019\equiv 3\pmod{8}$, por lo que

$$
N\equiv (1^{126} \cdot3)\pmod{8}\equiv 3\pmod{8}.
$$

Recapitulando, buscamos un múltiplo de $125$ que sea congruente con $3$ módulo $8$, es decir, hemos de resolver la ecuación, $125x\equiv 3\pmod{8}$. No obstante,

$$
\begin{aligned}
125x\equiv 3\pmod{8}&\Leftrightarrow 5x\equiv 3\pmod{8}\\\\ &\Leftrightarrow 15x\equiv 9\pmod{8}\\\\ &\Leftrightarrow (-x)\equiv 1\pmod{8}\\\\ &\Leftrightarrow x\equiv 7\pmod{8},
\end{aligned}
$$

esto es, $125\cdot7=875$ son las tres últimas cifras de $N$.

De manera más clásica, una vez hallado el valor de las anteriores dos congruencias, el sistema de ecuaciones de congruencias lineales propuesto es equivalente a

$$
\begin{aligned}
x&\equiv 3\pmod{8},\\\\ x&\equiv 0\pmod{125}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=8$ y $m_2=125$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=8\cdot125 = 1000$. Procedamos entonces al cálculo de las soluciones utilizando el método habitual. Así,

$$
\begin{aligned}
M_1 &= \dfrac{M}{m_1} = \dfrac{1000}{8} = 125,\\\\ M_2 &= \dfrac{M}{m_2} = \dfrac{1000}{125} = 4,
\end{aligned}
$$

y, a continuación, resolvemos las siguientes ecuaciones de congruencia lineales:

$$
\begin{aligned}
125x\equiv 1\pmod{8}&\Leftrightarrow 5x\equiv 1\pmod{8}\\\\ &\Leftrightarrow 25x\equiv 5\pmod{8}\\\\ &\Leftrightarrow x\equiv 5\pmod{8},\\\\ 4x\equiv 1\pmod{125}&\Leftrightarrow 376x\equiv 94\pmod{125}\\\\ &\Leftrightarrow x\equiv 94\pmod{125}.
\end{aligned}
$$

Agrupando ahora toda la información adecuadamente,

$$
\begin{aligned}
x&\equiv 3\pmod{8},& 125x&\equiv 1\pmod{8},& x&\equiv 5\pmod{8},\\\\ x&\equiv 0\pmod{125},& 4x&\equiv 1\pmod{125},& x&\equiv 94\pmod{125},
\end{aligned}
$$

entonces la solución es 

$$
\begin{aligned}
x &\equiv (3\cdot125\cdot5 + 0\cdot4\cdot94)\pmod{1000}\\\\ &\equiv 1875\pmod{1000}\\\\ &\equiv 875\pmod{1000},
\end{aligned}
$$

esto es, $875$ son los tres últimos dígitos de $N$.

### Problema 29

Encuentra los dos últimos dígitos no nulos de $2017!$.

{{< hl >}}Solución:{{< /hl >}} dado que hay menos potencias de $5$ que de $2$ en $n!$ para cada $n>1$, el número de ceros al final de $n!$ es

$$
\left\lfloor\dfrac{n}{5}\right\rfloor + \left\lfloor\dfrac{n}{5^2}\right\rfloor + \left\lfloor\dfrac{n}{5^3}\right\rfloor + \cdots.
$$

Para $n=2017$, tenemos que

$$
\begin{aligned}
\left\lfloor\dfrac{2017}{5}\right\rfloor + \left\lfloor\dfrac{2017}{25}\right\rfloor + \left\lfloor\dfrac{2017}{125}\right\rfloor + \left\lfloor\dfrac{2017}{625}\right\rfloor &= 403 + 80 + 16 + 3 \\\\ &= 502,
\end{aligned}
$$

esto es $2017!$ acaba en $502$ ceros, situación que nos obliga a encontrar entonces el valor de la congruencia

$$
x \equiv \dfrac{2017!}{2^{502}\cdot 5^{502}}\pmod{100}.
$$

Como $100=4\cdot25$ y $mcd(4,25)=1$, es decir, son primos entre sí, hallaremos el valor de las congruencias para estos dos módulos y, después, aplicaremos el *Teorema chino del resto*.

Para empezar,

$$
\dfrac{2017!}{2^{502} \cdot 5^{502}}\equiv 0\pmod{4},
$$

debido a que en el numerador encontramos muchas más potencias de $2$ que las $502$ que hay de $5$ (de hecho, aplicando la fórmula anterior, podríamos calcular el exponente del número primo $2$ en la factorización de $2017!$ si fuese preciso).

Por comodidad, consideremos 

$$
f(x) = \dfrac{x!}{5^k}\pmod{25},
$$ 

donde $5^k$ es la mayor potencia de $5$ que divide a $x$, valor que podemos hallar haciendo uso de la expresión que figura unos párrafos arriba.

Ahora bien, resulta que

$$
\begin{aligned}
(5k+1)(5k+2)(5k+3)(5k+4)&= 625k^4 + 1250k^3 + 875k^2 + 250k + 24\\\\ &\equiv (-1)\pmod{25},
\end{aligned}
$$

hecho que nos permite escribir

$$
\begin{aligned}
f(2017)&=\dfrac{2017!}{5^{502}}\pmod{25}\\\\ &=\dfrac{(1\cdot2\cdot3\cdot4)\cdot1\cdot(1\cdot2\cdot3\cdot4)\cdot2\cdots(1\cdot2\cdot3\cdot4)\cdot403\cdot(16\cdot17)}{5^{99}}\pmod{25}\\\\ &=(-1)^{403}\cdot22\cdot f(403)\pmod{25}.
\end{aligned}
$$

Veamos en detalle la anterior cadena de igualdades:

- Los primeros términos de $2017!$ son $1\cdot2\cdot3\cdot4\cdot5$, de manera que ese $5$ se simplifica con uno de los que aparece en el denominador, quedando $1$. Por otra parte, por lo visto anteriormente, $(1\cdot2\cdot3\cdot4)\equiv(-1)\pmod{25}$.
- A continuación, aparecería el producto $6\cdot7\cdot8\cdot9\cdot10$. Por lo que respecta al $10=2\cdot5$, queda como $2$ al simplificar el $5$ con uno de los que figura en el denominador. Por otro lado, $6\cdot7\cdot8\cdot9$ $=$ $(5\cdot1+1)$ $(5\cdot1+2)$ $(5\cdot1+3)$ $(5\cdot1+4)\equiv (-1)\pmod{25}$, tal y como vimos anteriormente. Al ser cierta esa congruencia podemos, por ejemplo, sustituir el anterior producto simplemente por $1\cdot2\cdot3\cdot4$, del que también sabemos es congruente con $(-1)$ módulo $25$.
- Como $2017 = 5\cdot403+2$, esta manera de proceder la podemos llevar a cabo en $403$ ocasiones (hecho que explica el $(-1)^{403}$ que aparece posteriormente), quedando sin ''agrupar'' los dos últimos términos (dado el orden que hemos establecido) de $2017!$, esto es, $2016$ y $2017$. Sin embargo, $2016\equiv 16\pmod{25}$ y $2017\equiv 17\pmod{25}$. Además, $16\cdot17 = 272\equiv 22\pmod{25}$, cifra que figura en la última igualdad.
- Los anteriores $403$ grupos nombrados provocan el mismo número de simplificaciones de cincos, por lo que el denominador pasa lógicamente de ser $5^{502}$ a $5^{99}$.
- Finalmente, en el numerador aparece $1\cdot2\cdots403 = 403!$, cifra que podemos comprobar fácilmente que acaba en $99$ ceros, quedando así justificada la presencia de $f(403)$.

Razonando de manera similar,

$$
\begin{aligned}
f(403)&=\dfrac{403!}{5^{99}}\pmod{25}\\\\ &=\dfrac{(1\cdot2\cdot3\cdot4)\cdot1\cdot(1\cdot2\cdot3\cdot4)\cdot2\cdots(1\cdot2\cdot3\cdot4)\cdot80\cdot(1\cdot2\cdot3)}{5^{19}}\pmod{25}\\\\ &=(-1)^{80}\cdot6\cdot f(80)\pmod{25},\\\\ f(80)&=\dfrac{80!}{5^{19}}\pmod{25}\\\\ &=\dfrac{(1\cdot2\cdot3\cdot4)\cdot1\cdot(1\cdot2\cdot3\cdot4)\cdot2\cdots(1\cdot2\cdot3\cdot4)\cdot16}{5^{3}}\pmod{25}\\\\ &=(-1)^{16}\cdot f(16)\pmod{25},\\\\ f(16)&=\dfrac{16!}{5^{3}}\pmod{25}\\\\ &=((1\cdot2\cdot3\cdot4)\cdot1\cdot(1\cdot2\cdot3\cdot4)\cdot2\cdot(1\cdot2\cdot3\cdot4)\cdot3\cdot16)\pmod{25}\\\\ &=(-1)^{3}\cdot16\cdot 3!\pmod{25},
\end{aligned}
$$

y realizando ahorra las correspondientes sustituciones,

$$
\begin{aligned}
f(2017) &= (-1)^{502}\cdot22\cdot6\cdot16\cdot6\pmod{25}\\\\ &\equiv 12672\pmod{25}\\\\ &\equiv 22\pmod{25},
\end{aligned}
$$

esto es,

$$
\dfrac{2017!}{5^{502}}\equiv 22\pmod{25}.
$$

Recordemos en este instante que, en realidad, estamos interesados en hallar el valor de la congruencia

$$
\dfrac{2017!}{2^{502}\cdot 5^{502}}\pmod{25},
$$

de forma que todavía queda un poco de trabajo que llevar a cabo. Sin embargo, por el *Teorema de Euler-Fermat*, como $mcd(2,25)=1$, es decir, son primos entre sí, entonces $2^{\varphi(25)}\equiv 1\pmod{25}$. Dado que,

$$
\varphi(25) = 25\cdot\left(1-\dfrac{1}{5}\right) = 20,
$$

y $502 = 20\cdot25+2$, entonces

$$
2^{502} = (2^{20})^{25}\cdot2^2\equiv 4\cdot1^{25}\pmod{25}\equiv 4\pmod{25}.
$$

Así, sabemos que el resto de dividir 

$$
a = \dfrac{2017!}{5^{502}}
$$ 

entre $25$ asciende a $22$. Como el número que nos interesa, en términos del resto, es $4$ veces el anterior, esto es, $4a$, para hallar el resto al dividir por $25$ planteamos la ecuación de congruencia lineal,

$$
\begin{aligned}
4a\equiv 22\pmod{25}&\Leftrightarrow 24a\equiv 132\pmod{25}\\\\ &\Leftrightarrow (-a)\equiv 7\pmod{25}\\\\ &\Leftrightarrow a\equiv 18\pmod{25},
\end{aligned}
$$

es decir, finalmente hemos llegado a que 

$$
\dfrac{2017!}{2^{502}\cdot 5^{502}}\equiv 18\pmod{25}.
$$

Combinando este último resultado alcanzado con el anterior, es cierto que la ecuación de congruencia lineal

$$
x \equiv \dfrac{2017!}{2^{502}\cdot 5^{502}}\pmod{100},
$$

es equivalente al sistema de ecuaciones de congruencias lineales

$$
\begin{aligned}
x&\equiv 0\pmod{4},\\\\ x&\equiv 18\pmod{25}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=4$ y $m_2=25$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=4\cdot25 = 100$. Podemos hallar esta vía el procedimiento habitual; sin embargo, dado que la primera ecuación indica que la solución es múltiplo de $4$ y la segunda ecuación se traduce en que al dividir dicho múltiplo por $25$ ha de dejar un resto igual a $18$, llegamos, por tanteo, a que $x\equiv 68\pmod{100}$. Es decir, $68$ son los dos últimos dígitos no nulos de $2017!$.

### Problema 30

Encuentra los dos últimos dígitos de

$$
2017^{2018^{2019}} + 2018^{2019^{2020}} + 2019^{2020^{2021}}
$$

{{< hl >}}Solución:{{< /hl >}} para encontrar las dos últimas cifras de la operación indicada en el enunciado del ejercicio, un posible enfoque pasa por trabajar con el valor de las congruencias módulo $100$. Estudiemos el valor de dichas congruencias para cada uno de los tres sumandos por separado.

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
x&\equiv 2018^{2019} \pmod{5},\\\\ x&\equiv 2018^{2019} \pmod{8},
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
2018^{2019} &= (2\cdot1009)^{2019} \\\\ &= 2^{2019} \cdot 1009^{2019} \\\\ &= 2^3 \cdot 2^{2016} \cdot 1009^{2019} \\\\ &= 8 \cdot 2^{2016} \cdot 1009^{2019},
\end{aligned}
$$

y así, podemos concluir que $2018^{2019} \equiv 0\pmod{8}$. Por consiguiente, el sistema de ecuaciones de congruencia lineales planteado arriba es equivalente a

$$
\begin{aligned}
x&\equiv 2\pmod{5},\\\\ x&\equiv 0\pmod{8}.
\end{aligned}
$$

Este último podemos resolverlo, de forma mecánica, con el procedimiento habitual que nos proporciona el *Teorema chino del resto* o razonando sin más. Buscamos aquí un múltiplo de $8$ (menor que $40$) que al dividirlo entre $5$ devuelva un resto de valor $2$. Tras unos rápidos cálculos mentales, encontramos que el número $32$ satisface las restricciones impuestas y, por tanto, la solución al sistema planteado arriba es $x\equiv 32\pmod{40}$. Con todo, hemos llegado a que

$$
2017^{2018^{2019}} \equiv 17^{2018^{2019}} \pmod{100}\equiv 17^{32} \pmod{100}.
$$

Ahora bien, $17^{32} = ( 17^2 )^{16} = 189^{16} \equiv 89^{16} \pmod{100}$. Aplicando esta forma de proceder de manera recurrente, podemos reducir, en unos pocos pasos, $17^{32}$ a un número para el que el cálculo de su congruencia módulo $100$ sea razonable. Así,

$$
\begin{aligned}
17^{32} &\equiv 89^{16} \pmod{100} \\\\ &\equiv (-11)^{16} \pmod{100} \\\\ &\equiv 11^{16} \pmod{100} \\\\ &\equiv 21^8 \pmod{100}\\\\ &\equiv 41^4 \pmod{100} \\\\ &\equiv 81^2 \pmod{100} \\\\ &\equiv 61\pmod{100},
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
x&\equiv 2018^{2019^{2020}} \pmod{4},\\\\ x&\equiv 2018^{2019^{2020}} \pmod{25},
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
2019^{2020} &\equiv (-1)^{2020} \pmod{20} \\\\ &\equiv 1^{2020}\pmod{20} \\\\ &\equiv 1\pmod{20},
\end{aligned}
$$

y entonces

$$
2018^{2019^{2020}} \equiv 18^{2019^{2020}} \pmod{25}\equiv 18\pmod{25}.
$$

Por tanto, el sistema de ecuaciones de congruencia lineales planteado queda

$$
\begin{aligned}
x&\equiv 0\pmod{4},\\\\ x&\equiv 18\pmod{25}.
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
x&\equiv 2020^{2021} \pmod{5},\\\\ x&\equiv 2020^{2021} \pmod{8},
\end{aligned}
$$

pues $mcd(5,8)=1$ y $5\cdot8=40$. Ahora bien, como $2020 = 2^2 \cdot5\cdot101$, el exponente es, directamente, múltiplo de $5$ y, por otra parte, operando adecuadamente con las propiedades de las potencias, deducimos rápidamente que asimismo será múltiplo de $8$, esto es, el sistema de ecuaciones de congruencia lineales queda

$$
\begin{aligned}
x&\equiv 0\pmod{5},\\\\ x&\equiv 0\pmod{8},
\end{aligned}
$$

y su solución, trivialmente, es $x\equiv 0\pmod{40}$. Por consiguiente,

$$
2019^{2020^{2021}} \equiv 19^{2020^{2021}} \pmod{100}\equiv 1\pmod{100}.
$$

Recapitulando,

$$
\begin{aligned}
2017^{2018^{2019}} &\equiv 61\pmod{100},\\\\ 2018^{2019^{2020}} &\equiv 68\pmod{100},\\\\ 2019^{2020^{2021}} &\equiv  1\pmod{100},
\end{aligned}
$$

luego

$$
\begin{aligned}
\left(2017^{2018^{2019}} + 2018^{2019^{2020}} + 2019^{2020^{2021}} \right)&\equiv (61+68+1)\pmod{100}\\\\ &\equiv 30\pmod{100},
\end{aligned}
$$

es decir, las dos últimas cifras de la operación indicada en el enunciado del ejercicio son $30$.

## Problemas propuestos

**Problema 31:** calcula las dos últimas cifras de $2^{390}$.

**Problema 32:** calcula las dos últimas cifras de $3^{390}$.

**Problema 33:** determina todos los números naturales $m$ tales que $1066\equiv 1776\pmod{m}$.

**Problema 34:** dado $(1! + 2! + \cdots + 100!)\pmod{45}$, encuentra el menor resto no negativo.

**Problema 35:** sea $n$ un número natural y $A_n = 2^n + 2^{2n} + 2^{3n}$.

- (a) Demuestra que $A_{n+3}\equiv A_n\pmod{2}$.
- (b) ¿Para qué valores de $n$ es $A_n$ múltiplo de $7$?
- (c) Los números, en base $2$, $1110$, $1010100$ y $1001001000$, ¿son divisibles por $7$?

**Problema 36:** determina todos los pares de números naturales $(a,b)$ tales que $mcd(a,b) = 18$ y $mcm(a,b) = 540$.

**Problema 37:** halla dos números naturales sabiendo que su máximo común divisor es $120$ y la diferencia de sus cuadrados asciende a $345600$.

**Problema 38:** demuestra que $mcd(14n+3, 21n+4)=1$, para cada número natural $n$.

**Problema 39:** determina todos los posibles valores de $mcd(3n+1, n^2+1)$, donde $n$ es un número natural.

**Problema 40:** si a un número de $3$ cifras le quitamos la cifra central, resulta la séptima parte del número inicial. ¿De qué número se trata?

**Problema 41:** ¿cuál es el número de tres cifras que es igual a doce veces la suma de sus cifras?

**Problema 42:** halla el dígito final de $9^{9 ^ 9}$.

**Problema 43:** sabiendo que $7^4 = 2401$, halla los tres últimos dígitos de $7^{9999}$.

**Problema 44:** demuestra que

- (a) un número en base $7$ es par si, y solo si, la suma de sus cifras es par.
- (b) un número es divisible por $25$ si, y solo si, acaba en $00$, $25$, $50$ o $75$.

**Problema 45:** halla el criterio de divisibilidad por $5$ en base $12$ y aplícalo al número $12x75_{(12}$ para que sea divisible por $5$.

**Problema 46:** prueba que, si $n$ es un número natural, $3^{2 ^ n}+1$ es divisible por $2$, pero no por $4$.

**Problema 47:** dado el número $123456789101112\cdots100$, donde los números escritos son los naturales sin espacios, estudia si es múltiplo de $9$.

**Problema 48:** calcula el menor múltiplo de $23$ cuyas cifras son todas nueves.

**Problema 49:** demuestra que $A_n = 2903^n - 803^n - 464^n + 261^n$ es divisible por $1897$, para cada número natural $n$.

**Problema 50:** halla el número $2^n 5^m$, con $n$ y $m$ números naturales, sabiendo que la suma de sus divisores es $961$.

**Problema 51:** halla un número natural sabiendo que es múltiplo de $30$ y que la suma de sus $16$ divisores es $1440$.

**Problema 52:** un número natural tiene dos factores primos y ocho divisores naturales, la suma de los cuales es $320$. Halla el número.

**Problema 53:** halla el menor número entero $n$ que tiene $12$ divisores y solamente tres factores primos, cuya suma es $20$.

**Problema 54:** demuestra que un número es un cuadrado perfecto si, y solo si, tiene un número impar de divisores.

**Problema 55:** demuestra que no es posible expresar $2019$ como suma de dos cuadrados perfectos.

**Problema 56:** encuentra el menor número natural $n$ tal que $n / 2$ es cuadrado perfecto, $n / 3$ es cubo perfecto y $n / 7$ es potencia séptima perfecta.

**Problema 57:** halla un número natural $n$ tal que su cuadrado tenga $202$ dígitos: los primeros $100$ (desde la izquierda) todos iguales a $1$, los siguientes $100$ todos iguales a $2$ y los dos últimos, desconocidos. Es decir, de la forma $111\cdots111222\cdots222xy$.

**Problema 58:** halla

- (a) el resto de dividir $4^{26} + 5^{28}$ entre $7$.
- (b) la última cifra de $8^{254}$.
- (c) el criterio de divisibilidad por $6$ en base $7$. ¿Es divisible $34500010_{(7}$ entre $6$?

**Problema 59:** halla el resto de dividir $2^{55}$ entre $7$.

**Problema 60:** prueba que $(27 ^ 4) ^ 9 - (25 ^ 3) ^ 6$ es múltiplo de $37$.

**Problema 61:** demuestra que $n^7 - n$ es múltiplo de $42$, para cada número natural $n$.

**Problema 62:** halla el resto de dividir $13!$ entre $17$.

**Problema 63:** halla el menor residuo positivo al dividir

- (a) $5^{500}$ entre $17$.
- (b) $12!$ entre $13$.

**Problema 64:** prueba que $437$ es divisor de

- (a) $16^{99} - 1$.
- (b) $18! + 1$.

**Problema 65:** calcula el resto cuando $90!$ se divide por $97$.

**Problema 66:** calcula las dos últimas cifras de $31^{263}$.

**Problema 67:** para cada entero no negativo $n$, se considera 

$$
P(n) = \frac{n^7}{7} + \frac{n^3}{3} + \frac{11n}{21}.
$$

- (a) Demuestra que $3n^7 + 7n^3 + 11n = 0$ en $\mathbb{Z}_3$ y en $\mathbb{Z}_7$.
- (b) Demuestra que $P(n)$ es un número entero.

**Problema 68:** dado un número primo $p\geq 7$, prueba que el número $111\cdots111$ (formado por $p-1$ unos) es divisible por $p$.

**Problema 69:** sea $n$ un número natural y el conjunto de fracciones 

$$
A_n = \left\\{\frac{1}{n},\frac{2}{n},\ldots,\frac{n}{n}\right\\}.
$$ 

Calcula el número de fracciones irreducibles y la suma de estas.

**Problema 70:** calcula el menor número natural $n$ tal que se cumpla que

$$
\begin{aligned}
n&\equiv 4\pmod{5},\\\\ n&\equiv 3\pmod{7},\\\\ n&\equiv 1\pmod{9}.
\end{aligned}
$$

**Problema 71:** ¿cuántas cifras tiene el menor número que cumple que, cuando la primera cifra de la izquierda se coloca en el último lugar de la derecha, el número que resulta es una vez y media el número inicial?

**Problema 72:** encuentra el número natural más pequeño, con $6$ como cifra de las unidades, de manera que, si el $6$ se mueve al principio, el número queda multiplicado por cuatro.

**Problema 73:** halla un número de cinco cifras diferentes de manera que es igual a la suma de todos los de tres cifras que se pueden obtener con las variaciones ordinarias de dichas cifras tomadas de tres en tres.

**Problema 74:** se consideran los números naturales escritos del modo usual en base $10$. Se pide:

- (a) Encuentra el menor número tal que, al suprimir la primera cifra de la izquierda, quede reducido a su quinta parte.
- (b) Demuestre que no existe ningún número que, al suprimirle su primera cifra de la izquierda, quede reducido a su doceava parte.

**Problema 75:** halla un número con $15$ divisores tal que la suma de todos estos divisores sea igual a $1767$.

**Problema 76:** un número natural $A$, descompuesto en producto de factores primos, es de la forma $A = a^x b^y c^z$. El número de divisores de $A$, $A^2$ y $A^3$ es, respectivamente, $60$, $315$ y $910$. El máximo común divisor de todos los posibles valores de $A$ es $900$. Hállalos.

**Problema 77:** halla un número de cuatro cifras tal que sea igual al cubo de la suma de sus cifras.

**Problema 78:** encuentra un número de cuatro cifras $abcd$ de manera que $abcd = 11(a+b+c+d)^2$.

**Problema 79:** determina los números $n$ de tres cifras, divisibles por $11$, de manera que $n / 11$ es igual a la suma de los cuadrados de los dígitos de $n$.

**Problema 80:** resuelve la ecuación en congruencias $7x\equiv 6\pmod{100}$.

**Problema 81:** ¿existe algún entero positivo $x$ tal que cuando $x$ se divide entre 3, se obtiene un residuo igual a $2$; cuando $x$ se divide entre $5$, se obtiene de resto $4$; y cuando $x$ se divide entre $7$, el resto es igual a $6$?

**Problema 82:** encuentra las soluciones del siguiente sistema de ecuaciones en congruencias lineales:

$$
\begin{aligned}
x&\equiv 3\pmod{5},\\\\ x&\equiv 4\pmod{7},\\\\ x&\equiv 6\pmod{9}.
\end{aligned}
$$

**Problema 83:** determina el entero positivo más pequeño que deja de resto $1$, $2$, $3$ y $4$ cuando se divide, respectivamente, por $2$, $3$, $5$ y $11$.

---

**Problema 84:** el matemático y poeta chino *Sun Tsu* planteó, hace alrededor de $1800$ años, el siguiente problema: ''Tengo un conjunto de objetos. Cuando los cuanto de tres en tres, me sobran dos; cuando los cuento de cinco en cinco, me sobran tres; y cuando los cuento de siete en siete, me sobran dos. ¿Cuántos objetos poseo?''.

**Problema 85:** resuelve la ecuación en congruencias $91x\equiv 419\pmod{440}$.

**Problema 86:** resuelve la ecuación en congruencias $3x\equiv 11\pmod{2275}$.

**Problema 87:** demuestra que $3\cdot 5^{2n+1} + 2^{3n+1}$ es divisible por $17$, para cada número natural $n$.

**Problema 88:** demuestra que $4^n \equiv(1+3n)\pmod{9}$, para cada número natural $n$.

**Problema 89:** divide el número $101$ en dos partes tales que una sea múltiplo de $11$ y la otra sea múltiplo de $17$.

**Problema 90:** la suma de dos números vale $371$ y el cociente entre su mínimo común múltiplo y su máximo común divisor es $430$. Halla dichos números.

**Problema 91:**

- (a) Halla el exponente de $2$ en la factorización de $10!$. ¿Cuál sería en el caso de $11!$?
- (b) Halla el exponente de $3$ en la factorización de $212!$.

**Problema 92:**

- (a) ¿En cuántos ceros acaba el número $1000!$?
- (b) Demuestra que $1000!$ no es divisible por $2^{995}$, pero sí por $2^{994}$.

**Problema 93:** convierte $100!$ a base octal. ¿En cuántos ceros termina $100!$ en base octal?

**Problema 94:** ¿en cuántos ceros acaba $438_{(15}!$?

**Problema 95:**

- (a) ¿En cuántos ceros acaba $438_{(40}!$?
- (b) ¿En cuántos ceros acaba $(55555_{(6}!)^3$?

**Problema 96:** calcula el número de ceros en que acaba $(15348_{(16}!)^5$, con la condición de que debe operarse en base $16$, sin pasar a base decimal, hasta el final.

**Problema 97:** halla el criterio de divisibilidad por $5$ y por $10$ de un número en base $9$. ¿Es múltiplo de $5$ el número $213246_{(9}$?

**Problema 98:** halla el conjunto de los divisores del número $1001$. Sean $N = a_0 + a_1t + \cdots + a_nt^n$ y $S = a_0 - a_1 + a_2 - \cdots + (-1)^na_n$, donde $t=1000$ y $a_n$ es un número entero, para cada $n\in\mathbb{N}\cup\{0\}$. Demuestra que $N\equiv S\pmod{1001}$. Deduce de ello un criterio de divisibilidad por $7$, por $11$ o por $13$, y aplícalo al número $312879645$. 

**Problema 99:** demuestra que, siendo $n$ un número entero, la expresión 

$$
\frac{n^5 - 5n^3 + 4n}{n+2}
$$ 

siempre es divisible por $24$.

**Problema 100:** demuestra que, si el número natural $p=abc_{(10}$ es divisible por $37$, los números $bca_{(10}$ y $cab_{(10}$ son divisibles por $37$.

**Problema 101:** sean $a$, $b$, $c$ y $d$ números enteros cualesquiera. Prueba que 

$$
abcd(a^2 - b^2)(a^2 - c^2)(a^2 - d^2)(b^2 - c^2)(b^2 - d^2)(c^2 - d^2)
$$ 

es divisible por $7$.

**Problema 102:** encuentra los números de cuatro cifras, de la forma $abab$, que, disminuidos en una unidad, sean cuadrados perfectos.

**Problema 103:** se tienen los números $49$, $4489$, $444889$, $\ldots$ obtenido cada uno intercalando $48$ en el centro del anterior. Demuestra que todos estos números son cuadrados perfectos y halla la raíz cuadrada del que consta de $2n$ cifras.

**Problema 104:** halla el resto de la división por $11$ de $37^{437}$.

**Problema 105:** demuestra que si $p$ es un número primo impar, se cumple que $p$ divide a $2^{p-1}-2$.

**Problema 106:** sea $p$ un número primo impar. Demuestra que

- (a) $(1^{p-1} + 2^{p-1} + \cdots + (p-1)^{p-1})\equiv (-1)\pmod {p}$.
- (b) $(1^p + 2^p + \cdots + (p-1)^p)\equiv 0\pmod{p}$.

**Problema 107:** prueba que 

$$
A_k = 2^{2^{6k+2}}+3
$$ 

es múltiplo de $19$, para todo número natural $k$.

**Problema 108:** demuestra que el número $n(n^2 + 5)$ es divisible por $6$, para cada número natural $n$.

**Problema 109:** ¿qué enteros positivos, menores que $15$, tienen inverso módulo $15$? Encuentra los correspondientes inversos.

**Problema 110:** demuestra que $n^5 - 5n^3 + 4n$ es múltiplo de $120$, para cada número natural $n$.

**Problema 111:** si $a=11\cdots 11$ es un número con $2n$ dígitos y $b=22\cdots 22$ es uno que posee $n$ dígitos, prueba que $a-b$ es un cuadrado perfecto.

**Problema 112:** demuestra que $2222^{5555} + 5555^{2222}$ es múltiplo de $7$.

**Problema 113:** halla todos los números naturales $n$ tales que $2^n + 3^n$ es un múltiplo de $7$.

**Problema 114:** encuentra todos los números naturales $n$ para los cuales se satisface que $1^n + 9^n + 10^n = 5^n + 6^n + 11^n$.

**Problema 115:** en una batalla, en la que participaron entre $10000$ y $11000$ soldados, resultaron muertos $23 / 165$ del total y heridos $35 / 143$ del total. Halla cuántos resultaron ilesos.

**Problema 116:**

- (a) Dados dos números $x$ e $y$, coprimos entre sí, prueba que $mcd(x+y, xy) = 1$.
- (b) Dados dos números enteros $a$ y $b$, prueba que $mcd(a,b) = mcd(a+b, mcm(a, b))$.
- (c) La suma de dos números naturales es $5264$ y su mínimo común múltiplo es $200340$, ¿cuáles son estos números?

**Problema 117:**

- (a) Estudia, según los valores del número natural $n$, el resto de la división de $7^n$ entre $9$.
- (b) ¿Para qué valores de $n$ se cumple que $16^{3n} + 16^n - 2$ es múltiplo de $9$?
- (c) Permutando las cifras del número $1223334444555556666667777777$, ¿podrá obtenerse un cuadrado perfecto?

**Problema 118:** halla los números enteros positivos $n$ tal que $n^4+2$ es divisible por $n+2$.

**Problema 119:** determina todos los valores de $k$ para los cuales el número $11\cdots 11$, compuesto por $k$ unos, es un cuadrado perfecto.

**Problema 120:** una mujer tiene un cesto de manzanas. Haciendo grupos de $3$ sobran $2$ y haciendo grupos de $4$ sobran $3$. Halla el número de manzanas que contiene el cesto sabiendo que están entre $100$ y $110$.

**Problema 121:** A una isla llegan $17$ piratas para repartirse un botín que consiste en un saco con más de $100$ monedas de oro. Efectuado el reparto equitativo, sobra una moneda. Con el objetivo de que no sobre ninguna, los piratas deciden matar a uno de ellos y efectuar nuevamente el reparto equitativo, pero vuelve a sobrar una moneda.

- (a) ¿Cuál es el número mínimo de monedas que contiene el saco?
- (b) Conocido dicho número mínimo, ¿cuántos piratas morirán hasta que, efectuado el reparto equitativo, no sobre ninguna moneda?

**Problema 122:** resuelve en $\mathbb{Z}$ la ecuación $x^2 + x - 2\equiv 0\pmod{13}$.

**Problema 123:** una banda de piratas se apodera de un botín de piezas de oro iguales. Deciden repartírselo a partes iguales y el resto dárselo al cocinero chino, que recibe en este caso $3$ piezas. Los piratas pelean entre sí y mueren seis de ellos, con lo que en el nuevo reparto el cocinero chino se lleva $4$ piezas de oro. De regreso, el barco se hunde y se salvan el botín, seis piratas y el cocinero chino inmortal, con lo que el nuevo reparto le da ahora $5$ piezas al cocinero chino. ¿Cuál es la fortuna esperada por el cocinero chino cuando decide matar al resto de los piratas para quedarse el botín él solo si la banda era de $17$ piratas?

**Problema 124:** en una división, se conoce el dividendo, que es $258728$ y los restos sucesivos que se obtuvieron haciendo la división son $379$, $480$ y $392$. Halla el divisor y el cociente. ¿Existe más de una solución?

**Problema 125:** ¿cuántos números naturales $n$ cumplen que la expresión 

$$
\frac{n^2 + 2011}{n+1}
$$ 

es un número natural?

**Problema 126:** demuestra que $8^n + 1$ no es un número primo, para cada número natural $n$.

