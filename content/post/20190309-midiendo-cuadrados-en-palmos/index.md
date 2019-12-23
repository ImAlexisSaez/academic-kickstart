---
title: "Midiendo cuadrados en palmos"
slug: "midiendo-cuadrados-en-palmos"
subtitle: "Problema 58"
summary: "Problema 58: requiere andar con pies de plomo."

date: 2019-03-09T05:59:39+02:00
lastmod: 2019-03-09T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Ecuaciones diofánticas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Alex D'Alessio](https://unsplash.com/@alexdalessio22), disponible en [Unsplash](https://unsplash.com/photos/fsasJf8aDvg)."
---

**Problema 58:** Determina las dimensiones de un rectángulo sabiendo que sus lados miden un número entero de centímetros, pero no un número entero de palmos, y que su área expresada en palmos cuadrados es igual a su perímetro expresado en palmos lineales. Considera que un palmo equivale a $20$ centímetros.

***

Sean $x$ e $y$ las medidas de los lados del rectángulo expresadas en centímetros, mientras que denotemos por $a$ y $b$ las correspondientes medidas obtenidas en palmos. El área del rectángulo, en palmos cuadrados, es $a\cdot b$, cantidad que nos dicen ha de ser igual a su perímetro en palmos lineales, que viene dado por $2a+2b = 2(a+b)$. Por tanto, resulta que 

$$
a\cdot b = 2(a + b).
$$

Dado que un palmo equivale a $20$ centímetros, es cierto que $x = 20a$ e $y = 20b$, y despejando $a$ y $b$, hallamos que

$$
\begin{aligned}
a &= \dfrac{x}{20},\\\\ b &= \dfrac{y}{20}.
\end{aligned}
$$

Sustituyendo los resultados alcanzados, tenemos que

$$
\dfrac{x}{20}\cdot\dfrac{y}{20} = 2\left(\dfrac{x}{20} + \dfrac{y}{20}\right),
$$

esto es, $xy = 40x+40y$, ecuación diofántica no lineal que abordaremos despejando una de las variables y forzando a que la restante tome valores enteros. Así, $xy-40x = 40y$, es decir, $x(y-40) = 40y$, de donde 

$$
x = \dfrac{40y}{y-40}.
$$ 

Como $x$ ha de tomar valores enteros, estudiaremos, a continuación, las posibilidades para la fracción que acabamos de obtener. Si llevamos a cabo la división de polinomios, es cierto que

$$
\dfrac{40y}{y-40} = 40 + \dfrac{1600}{y-40},
$$

con $y\neq 40$ ($y=40$ no es una solución aceptable en este contexto, pues al ser múltiplo de $20$, uno de los lados del rectángulo poseería una longitud igual a un número entero de palmos). Hemos llegado entonces a que $y-40$ debe ser un divisor de $1600$.

Ahora bien, $1600 = 2^6 \cdot 5^2$, situación que produce un total de 

$$
(6+1)\cdot(2+1) = 21
$$ 

divisores, por lo que, acto seguido, analizaremos todos y cada uno de los casos. Para empezar, listemos el conjunto de divisores. Para llevar a cabo tal tarea de forma relativamente sencilla, recordemos que la expresión de la suma de los divisores era 

$$
(1+2+2^2 +\cdots+2^6 )\cdot(1+5+5^2 ),
$$ 

de manera que si prescindimos de la operación suma, cada uno de los productos resulta ser un divisor de $1600$. Por ejemplo, multiplicando $1$ por $1,2,2^2,\ldots, 2^6$ aparecen los divisores 

$$
\\{1,2,4,8,16,32,64\\}.
$$ 

Multiplicando ahora $5$ por $1,2,2^2,\ldots, 2^6$, obtenemos los divisores 

$$
\\{5,10,20,40,80,160,320\\}.
$$

Finalmente, multiplicando $5^2$ por $1,2,2^2 ,\ldots,2^6$, encontramos los divisores 

$$
\\{25,50,100,200,400,800,1600\\}.
$$

En definitiva, el conjunto de divisores de $1600$ es

$$
\begin{aligned}
\\{&1, 2, 4, 5, 8, 10, 16, 20, 25, 32, 40, 50,\\\\ &64, 80, 100, 160, 200, 320, 400, 800, 1600\\}.
\end{aligned}
$$

A continuación, vemos que algunos casos los podemos descartar rápidamente. ¿Es válida la solución $y-40=20$? No, ya que implicaría $y=60 = 3\cdot20$, es decir, $y$ sería entonces un múltiplo entero de palmos, longitud no permitida por las restricciones que impone el enunciado del ejercicio. El mismo razonamiento es válido para los valores $40$, $80$, $160$, $320$, $100$, $200$, $400$, $800$ y $1600$. 

Para el resto de casos, conformamos la siguiente tabla

| $y-40$ | $x$ | Nota |
| ------ | --- | ---- |
| $1$ | $40 + \dfrac{1600}{1} = 1640$ | Solución no válida: $x$ es múltiplo de $20$.|
$2$ | $40 + \dfrac{1600}{2} = 840$ | Solución no válida: $x$ es múltiplo de $20$.|
$4$ | $40 + \dfrac{1600}{4} = 440$ | Solución no válida: $x$ es múltiplo de $20$.|
$5$ | $40 + \dfrac{1600}{5} = 360$ | Solución no válida: $x$ es múltiplo de $20$.|
$8$ | $40 + \dfrac{1600}{8} = 240$ | Solución no válida: $x$ es múltiplo de $20$.|
$10$ | $40 + \dfrac{1600}{10} = 200$ | Solución no válida: $x$ es múltiplo de $20$.|
$16$ | $40 + \dfrac{1600}{16} = 140$ | Solución no válida: $x$ es múltiplo de $20$.|
$25$ | $40 + \dfrac{1600}{25} = 104$ | Solución válida.|
$32$ | $40 + \dfrac{1600}{32} = 90$ | Solución válida.|
$50$ | $40 + \dfrac{1600}{50} = 72$ | Solución válida.|
$64$ | $40 + \dfrac{1600}{64} = 65$ | Solución válida.|

Por tanto, las dimensiones del rectángulo vienen dadas por los pares $(104, 65)$, $(90, 72)$, $(72, 90)$ y $(65, 104)$.
