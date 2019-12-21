---
title: "Y volvemos con los problemas de mover dígitos"
slug: "y-volvemos-con-los-problemas-de-mover-digitos"
subtitle: "Problema 36"
summary: "Problema 36: con un par de ejemplos, enseguida detectamos el patrón a seguir."

date: 2018-12-22T05:59:39+02:00
lastmod: 2018-12-22T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Problemas", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [David Wirzba](https://unsplash.com/@psalms), disponible en [Unsplash](https://unsplash.com/photos/PwF1m8jajyM)."
---

**Problema 36:** ¿Cuántas cifras tiene el menor número que cumple que, cuando la primera cifra de la izquierda se coloca en el último lugar de la derecha, el número que resulta es una vez y media el número inicial?

***

Antes de abordar la resolución del ejercicio propiamente dicho, veamos con un par de ejemplos la manera de proceder, para así intentar detectar patrones. Por ejemplo, si consideramos el número $354$, podemos aislar la primera cifra escribiéndolo como $300 + 54$, es decir, $3 \cdot 10^2 + 54$. Ahora, si colocamos la primera cifra en el último lugar de la derecha, el número pasa a ser $543$, y como deseamos aislar de nuevo el $3$, podemos escribirlo como $540 + 3$ o, equivalentemente, como $54\cdot10 + 3$. Por desgracia, no se cumple para este ejemplo la condición exigida en el enunciado del ejercicio, puesto que 

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
