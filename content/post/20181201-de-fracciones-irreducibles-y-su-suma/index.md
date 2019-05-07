+++
title = "De fracciones irreducibles y su suma"
slug  = "de-fracciones-irreducibles-y-su-suma"
subtitle = "Problema 30"
summary  = "Problema 30: formalizando un resultado, en apariencia, sencillo."

date     = 2018-12-01T05:59:39+02:00
#lastmod = 2019-04-03T07:44:19+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Problemas", "Teoría de números"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Adrien Olichon](https://unsplash.com/@adrienolichon), disponible en [Unsplash](https://unsplash.com/photos/wI96vLftzkE)."
+++

**Problema 30:** Sea $n$ un número natural no nulo. Dado el conjunto de fracciones 

$$
A\_n = \left\\{\dfrac{1}{n},\dfrac{2}{n},\dfrac{3}{n},\ldots,\dfrac{n}{n}\right\\}.
$$ 

Calcula el número de fracciones irreducibles y la suma de dichas fracciones.

***

Acompañemos la resolución de este ejercicio con un caso particular para $n$, con el objetivo de que esta sea así más ilustrativa. Por ejemplo, si $n=8$, el conjunto de fracciones a estudiar es

$$
A\_8 = \left\\{\dfrac{1}{8},\dfrac{2}{8},\dfrac{3}{8},\dfrac{4}{8},\dfrac{5}{8},\dfrac{6}{8},\dfrac{7}{8},\dfrac{8}{8}\right\\},
$$

que contiene $4$ fracciones irreducibles,

$$
\left\\{\dfrac{1}{8},\dfrac{3}{8},\dfrac{5}{8},\dfrac{7}{8}\right\\}.
$$

Estas se caracterizan por ser aquellas en las que numerador y denominador son coprimos. Así pues, el problema se reduce a encontrar, dado un número natural $n$ no nulo, la cantidad de enteros positivos menores o iguales a $n$ y coprimos con $n$, esto es, $\varphi(n)$. 

En nuestro caso concreto, para $n=8=2^3$, efectivamente,

$$
\varphi(8) = 8\left(1-\dfrac{1}{2}\right) = 8\cdot\dfrac{1}{2}=4.
$$

Por tanto, recapitulando, dado $n$ un número natural no nulo, la cantidad de fracciones irreducibles que figuran en el conjunto $A_n$ es igual a $\varphi(n)$.

Para calcular su suma, si volvemos a centrar nuestra atención en el caso particular de $n=8$, tenemos que

$$
\dfrac{1}{8} + \dfrac{7}{8} = 1,\qquad \dfrac{3}{8} + \dfrac{5}{8} = 1,
$$

esto es, podemos agrupar las fracciones irreducibles de dos en dos, de manera que su suma es $1$. Efectivamente, haciendo uso del Teorema 1.9 de [1], sabemos que, dados dos números enteros $a$ y $b$, para cualquier número entero $x$ se cumple que

$$
mcd(a,b) = mcd(b,a) = mcd(a,-b) = mcd(a,b+ax).
$$

Considerando ahora un número natural $k<n$ coprimo con $n$, se tiene que $mcd(k,n)=1$, y basta tomar en el resultado anterior $a=n$, $b=(-k)$ y $x=1$ para deducir que $1 = mcd(n,k) = mcd(n,(-k))= mcd(n,n-k)$ y, así, concluimos que si la fracción $k/n$ es irreducible, asimismo lo es $(n-k)/n$. Además, trivialmente 

$$
\dfrac{k}{n} + \dfrac{n-k}{n}=1.
$$  

Por tanto, aplicando el resultado alcanzado, la suma de las fracciones irreducibles del conjunto $A\_n$ será 

$$
S = \dfrac{\varphi(n)}{2},
$$ 

quedando resuelto así el ejercicio.

### Referencias

- [1] Ivan Niven, Herbert S. Zuckerman y Hugh L. Montgomery. *An Introduction to the Theory of Numbers*. 5ª edición. New York, United States: Wiley, 1991. ISBN: 9780471625469.
