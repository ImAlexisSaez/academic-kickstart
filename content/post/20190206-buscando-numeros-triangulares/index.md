+++
title = "Buscando números triangulares que son cuadrados perfectos"
slug  = "buscando-numeros-triangulares-que-son-cuadrados-perfectos"
subtitle = "Problema 49"
summary  = "Problema 49: un primer encuentro con la ecuación de Pell."

date     = 2019-02-06T05:59:39+02:00
#lastmod = 2019-04-08T07:47:24+02:00

authors  = ["admin"]
math     = true
draft    = false
featured = false

tags       = ["Ecuación de Pell", "Ecuaciones diofánticas", "Problemas"]
categories = ["Oposiciones"]
projects   = ["problemas"]

[image]
  focal_point = "Smart"
  caption     = "Fotografía de [Elvira Visser](https://unsplash.com/@elviravisser), disponible en [Unsplash](https://unsplash.com/photos/dZh1irvg978)."
+++

**Problema 49:** Halla los números naturales $n$ de manera que se cumpla que 

$$
1+2+\cdots+n = k^2,
$$ 

con $k$ número natural.

***

Observamos rápidamente que para $n = 1$ se verifica la propiedad, sin más que tomar asimismo $k = 1$. El enunciado propuesto en el ejercicio es equivalente a hallar los números triangulares que son cuadrados perfectos. La ecuación diofántica $1+2+\cdots+n = k^2$ podemos escribirla de manera más compacta utilizando la conocida expresión para la suma de los primeros $n$ números naturales. Así,

$$
\dfrac{n(n+1)}{2} = k^2,
$$

o, equivalentemente, $n^2+n=2k^2$, dando lugar pues a la siguiente ecuación de segundo grado en $n$, $n^2+n-2k^2=0$. Por tanto,

$$
n = \dfrac{(-1)\pm\sqrt{1+8k^2}}{2}.
$$

Como buscamos valores naturales para $n$, podemos prescindir del signo $-$ que aparece en el numerador. Además, $1+8k^2$ ha de ser un cuadrado perfecto, que también necesitaremos sea impar, para que el numerador sea par y así $n$, efectivamente, pertenezca al conjunto de los números naturales. De esta manera, como ha de ser $1+8k^2$ un cuadrado perfecto, planteamos la ecuación $1+8k^2 = p^2$, que nos lleva a la *ecuación de Pell* 

$$
p^2-8k^2=1,
$$ 

de la cual sabemos posee infinitas soluciones en los enteros, pues $8$ no es un cuadrado perfecto. Por tanteo, una solución particular es $p=3$ y $k=1$, ya que $3^2 - 8\cdot1^2=1$. Expresamos ahora la diferencia de cuadrados como producto de una suma y una diferencia, de forma que

$$
3^2 - 8\cdot1^2=1\Leftrightarrow (3+\sqrt{8})(3-\sqrt{8})=1.
$$

Análogamente, la sucesión de soluciones enteras, que denotaremos por $(p\_n,k\_n)$, debe cumplir que $(p\_n + k\_n\sqrt{8})(p\_n - k\_n\sqrt{8})=1$. Obtengamos la solución general utilizando recurrencias, de manera que,

$$
p\_{n+1} + k\_{n+1}\sqrt{8} = (p\_n+k\_n\sqrt{8})(3+\sqrt{8}) = 3p\_n + \sqrt{8}p\_n + 3\sqrt{8}k\_n + 8k\_n,
$$

luego

$$
\begin{aligned}
p\_{n+1} &= 3p\_n + 8k\_n,\\\\ k\_{n+1} &=  p\_n + 3k\_n.
\end{aligned}
$$

Utilizando notación matricial,

$$
\begin{bmatrix}
p\_{n+1}\\\\ k\_{n+1}
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\\\ 1 & 3
\end{bmatrix}
\begin{bmatrix}
p\_n\\\\ k\_n
\end{bmatrix}.
$$

Ahora, $$n = \dfrac{(-1) + p}{2},$$ por lo que la solución general del ejercicio queda como

$$
\begin{bmatrix}
p\_{n+1}\\\\ k\_{n+1}
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\\\ 1 & 3
\end{bmatrix}
\begin{bmatrix}
p\_n\\\\ k\_n
\end{bmatrix},
$$

con $(p\_1,k\_1) = (3,1)$ y $$n = \dfrac{(-1) + p\_n}{2}.$$

Así, para $p\_1 = 3$, tenemos que $n = ((-1)+3)/2 = 1$. Obtengamos algunas soluciones adicionales,

$$
\begin{bmatrix}
p\_{2}\\\\ k\_{2}
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\\\ 1 & 3
\end{bmatrix}
\begin{bmatrix}
3\\\\ 1
\end{bmatrix}
= \begin{bmatrix}
17 \\\\ 6
\end{bmatrix},
$$

y entonces, para $p\_2=17$ queda $n = ((-1) + 17)/2 = 8$, esto es, 

$$
1+2+\cdots+7+8 = 6^2.
$$ 

Ahora,

$$
\begin{bmatrix}
p\_3\\\\ k\_3
\end{bmatrix}
= \begin{bmatrix}
3 & 8\\\\ 1 & 3
\end{bmatrix}
\begin{bmatrix}
17\\\\ 6
\end{bmatrix}
= \begin{bmatrix}
99\\\\ 35
\end{bmatrix},
$$

y, por tanto, para $p=99$ queda $n = ((-1) + 99)/2 = 49$, es decir, 

$$
1+2+\cdots+48+49 = 35^2,
$$ 

bastando aplicar el procedimiento tantas veces como soluciones deseemos encontrar.
