---
title: "Buscando números triangulares que son cuadrados perfectos"
slug: "buscando-numeros-triangulares-que-son-cuadrados-perfectos"
subtitle: "Problema 49"
summary: "Problema 49: un primer encuentro con la ecuación de Pell."

date: 2019-02-06T05:59:39+02:00
lastmod: 2019-08-01T00:00:01+02:00

authors: ["admin"]
math: true
markup: mmark
draft: false
featured: false

tags: ["Ecuación de Pell", "Ecuaciones diofánticas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Elvira Visser](https://unsplash.com/@elviravisser), disponible en [Unsplash](https://unsplash.com/photos/dZh1irvg978)."
---

**Problema 49:** Halla los números naturales $n$ de manera que se cumpla que 

$$
1+2+ \cdots +n = k^2,
$$ 

con $k$ número natural.

***

Observamos rápidamente que para $n = 1$ se verifica la propiedad, sin más que tomar asimismo $k = 1$. El enunciado propuesto en el ejercicio es equivalente a hallar los números triangulares que son cuadrados perfectos. La ecuación diofántica $1+2+ \cdots +n = k^2$ podemos escribirla de manera más compacta utilizando la conocida expresión para la suma de los primeros $n$ números naturales. Así,

$$
\dfrac{n(n+1)}{2} = k^2,
$$

o, equivalentemente, $n^2 +n=2k^2$, dando lugar pues a la siguiente ecuación de segundo grado en $n$, $n^2 +n-2k^2 =0$. Por tanto,

$$
n = \dfrac{(-1)\pm\sqrt{1+8k^2}}{2}.
$$

Como buscamos valores naturales para $n$, podemos prescindir del signo $-$ que aparece en el numerador. Además, $1+8k^2$ ha de ser un cuadrado perfecto, que también necesitaremos sea impar, para que el numerador sea par y así $n$, efectivamente, pertenezca al conjunto de los números naturales. De esta manera, como ha de ser $1+8k^2$ un cuadrado perfecto, planteamos la ecuación $1+8k^2 = p^2$, que nos lleva a la *ecuación de Pell* 

$$
p^2 -8k^2 =1,
$$ 

de la cual sabemos posee infinitas soluciones en los enteros, pues $8$ no es un cuadrado perfecto. Por tanteo, una solución particular es $p=3$ y $k=1$, ya que $3^2 - 8\cdot1^2=1$. Expresamos ahora la diferencia de cuadrados como producto de una suma y una diferencia, de forma que

$$
3^2 - 8\cdot 1^2 =1\Leftrightarrow (3+\sqrt{8})(3-\sqrt{8})=1.
$$

De igual manera, la sucesión de soluciones enteras, que denotaremos por $(p_n,k_n)$, debe cumplir que $(p_n + k_n\sqrt{8})(p_n - k_n\sqrt{8})=1$. Obtengamos la solución general utilizando recurrencias, de manera que,

$$
p_{n+1} + k_{n+1}\sqrt{8} = (p_n+k_n\sqrt{8})(3+\sqrt{8}) = 3p_n + \sqrt{8}p_n + 3\sqrt{8}k_n + 8k_n,
$$

luego

$$
\begin{aligned}
p_{n+1} &= 3p_n + 8k_n,\\
k_{n+1} &=  p_n + 3k_n.
\end{aligned}
$$

Utilizando notación matricial,

$$
\begin{bmatrix}
p_{n+1}\\
k_{n+1}
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\
1 & 3
\end{bmatrix}
\begin{bmatrix}
p_n\\
k_n
\end{bmatrix}.
$$

Ahora, $$n = \dfrac{(-1) + p}{2},$$ por lo que la solución general del ejercicio queda como

$$
\begin{bmatrix}
p_{n+1}\\
k_{n+1}
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\
1 & 3
\end{bmatrix}
\begin{bmatrix}
p_n\\
k_n
\end{bmatrix},
$$

con $(p_1,k_1) = (3,1)$ y $$n = \dfrac{(-1) + p_n}{2}.$$

Así, para $p_1 = 3$, tenemos que $n = ((-1)+3) / 2 = 1$. Obtengamos algunas soluciones adicionales,

$$
\begin{bmatrix}
p_{2}\\
k_{2}
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\
1 & 3
\end{bmatrix}
\begin{bmatrix}
3\\
1
\end{bmatrix}
= \begin{bmatrix}
17 \\
6
\end{bmatrix},
$$

y entonces, para $p_2=17$ queda $n = ((-1) + 17) / 2 = 8$, esto es, 

$$
1+2+ \cdots +7+8 = 6^2.
$$ 

Ahora,

$$
\begin{bmatrix}
p_3\\
k_3
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\
1 & 3
\end{bmatrix}
\begin{bmatrix}
17\\
6
\end{bmatrix}
= \begin{bmatrix}
99\\
35
\end{bmatrix},
$$

y, por tanto, para $p=99$ queda $n = ((-1) + 99)/2 = 49$, es decir, 

$$
1+2+ \cdots +48+49 = 35^2,
$$ 

bastando aplicar el procedimiento tantas veces como soluciones deseemos encontrar.
