---
title: "Buscando dígitos no nulos en números factoriales"
slug: "buscando-digitos-no-nulos-en-numeros-factoriales"
subtitle: "Problema 43"
summary: "Problema 43: sencillo de enunciar, muy entretenido de resolver."

date: 2019-01-16T05:59:39+02:00
lastmod: 2019-07-31T00:00:01+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Fórmula de Legendre", "Problemas", "Teorema chino del resto", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Wolfgang Hasselmann](https://unsplash.com/@wolfgang_hasselmann), disponible en [Unsplash](https://unsplash.com/photos/vIxqtVFOfgw)."
---

**Problema 43:** Encuentra los dos últimos dígitos no nulos de $2017!$.

***

Dado que hay menos potencias de $5$ que de $2$ en $n!$ para cada $n>1$, el número de ceros al final de $n!$ es

$$
\left\lfloor\dfrac{n}{5}\right\rfloor + \left\lfloor\dfrac{n}{5^2}\right\rfloor + \left\lfloor\dfrac{n}{5^3}\right\rfloor + \cdots.
$$

Para $n=2017$, tenemos que

$$
\begin{aligned}
\left\lfloor\dfrac{2017}{5}\right\rfloor + \left\lfloor\dfrac{2017}{25}\right\rfloor + \left\lfloor\dfrac{2017}{125}\right\rfloor + \left\lfloor\dfrac{2017}{625}\right\rfloor &= 403 + 80 + 16 + 3 \\
&= 502,
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
(5k+1)(5k+2)(5k+3)(5k+4)&= 625k^4 + 1250k^3 + 875k^2 + 250k + 24\\
&\equiv (-1)\pmod{25},
\end{aligned}
$$

hecho que nos permite escribir

$$
\begin{aligned}
f(2017)&=\dfrac{2017!}{5^{502}}\pmod{25}\\
&=\dfrac{(1\cdot2\cdot3\cdot4)\cdot1\cdot(1\cdot2\cdot3\cdot4)\cdot2\cdots(1\cdot2\cdot3\cdot4)\cdot403\cdot(16\cdot17)}{5^{99}}\pmod{25}\\
&=(-1)^{403}\cdot22\cdot f(403)\pmod{25}.
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
f(403)&=\dfrac{403!}{5^{99}}\pmod{25}\\
&=\dfrac{(1\cdot2\cdot3\cdot4)\cdot1\cdot(1\cdot2\cdot3\cdot4)\cdot2\cdots(1\cdot2\cdot3\cdot4)\cdot80\cdot(1\cdot2\cdot3)}{5^{19}}\pmod{25}\\
&=(-1)^{80}\cdot6\cdot f(80)\pmod{25},\\
f(80)&=\dfrac{80!}{5^{19}}\pmod{25}\\
&=\dfrac{(1\cdot2\cdot3\cdot4)\cdot1\cdot(1\cdot2\cdot3\cdot4)\cdot2\cdots(1\cdot2\cdot3\cdot4)\cdot16}{5^{3}}\pmod{25}\\
&=(-1)^{16}\cdot f(16)\pmod{25},\\
f(16)&=\dfrac{16!}{5^{3}}\pmod{25}\\
&=((1\cdot2\cdot3\cdot4)\cdot1\cdot(1\cdot2\cdot3\cdot4)\cdot2\cdot(1\cdot2\cdot3\cdot4)\cdot3\cdot16)\pmod{25}\\
&=(-1)^{3}\cdot16\cdot 3!\pmod{25},
\end{aligned}
$$

y realizando ahorra las correspondientes sustituciones,

$$
\begin{aligned}
f(2017) &= (-1)^{502}\cdot22\cdot6\cdot16\cdot6\pmod{25}\\
&\equiv 12672\pmod{25}\\
&\equiv 22\pmod{25},
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
4a\equiv 22\pmod{25}&\Leftrightarrow 24a\equiv 132\pmod{25}\\
&\Leftrightarrow (-a)\equiv 7\pmod{25}\\
&\Leftrightarrow a\equiv 18\pmod{25},
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
x&\equiv 0\pmod{4},\\
x&\equiv 18\pmod{25}.
\end{aligned}
$$

Por la estructura que presenta el anterior sistema y dado que $m_1=4$ y $m_2=25$ son primos entre sí, sabemos, por el *Teorema chino del resto*, que dicho sistema admite solución módulo $M=4\cdot25 = 100$. Podemos hallar esta vía el procedimiento habitual; sin embargo, dado que la primera ecuación indica que la solución es múltiplo de $4$ y la segunda ecuación se traduce en que al dividir dicho múltiplo por $25$ ha de dejar un resto igual a $18$, llegamos, por tanteo, a que $x\equiv 68\pmod{100}$. Es decir, $68$ son los dos últimos dígitos no nulos de $2017!$.
