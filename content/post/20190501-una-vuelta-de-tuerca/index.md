---
title: "Una vuelta de tuerca para la estrategia de barras y estrellas"
slug: "una-vuelta-de-tuerca-para-la-estrategia-de-barras-y-estrellas"
subtitle: "Problema 73"
summary: "Problema 73: retomamos la búsqueda de soluciones enteras."

date: 2019-05-01T05:59:39+02:00
lastmod: 2019-05-01T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Combinatoria", "Estrategia de barras y estrellas", "Problemas"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Kellen Riggin](https://unsplash.com/@kalaniparker), disponible en [Unsplash](https://unsplash.com/photos/i80oczfsUL0)."
---

**Problema 73:** ¿Cuántos números naturales menores que $10000$ cumplen que la suma de sus cifras es $25$?

***

Los números $n$ que nos interesan satisfacen que $0\leq n\leq 9999$, esto es, pueden tener hasta cuatro cifras. Como la suma de estas debe ascender a $25$, planteamos la ecuación 

$$
x_1+x_2+x_3+x_4=25,
$$ 

donde $0\leq x_i\leq 9$, con $1\leq i\leq 4$ y representando cada $x_i$ una de las cifras de los números buscados.

En ejercicios anteriores analizamos cómo encontrar todas las soluciones enteras no negativas de una ecuación como la planteada, e incluso vimos cuál era la forma de proceder cuando algunas de las variables quedaban afectadas por restricciones de mayor o igual. La forma de resolver este tipo de problemas, cuando surgen restricciones de menor o igual afectando a las variables, será la siguiente: utilizaremos el *Principio de complementación*, de forma que calcularemos el número de soluciones enteras no negativas de la ecuación propuesta y, después, haciendo uso del *Principio de inclusión-exclusión*, descontaremos aquellas que no satisfagan las restricciones impuestas.

Así pues, empecemos planteando la ecuación 

$$
x_1+x_2+x_3+x_4=25,
$$ 

con $x_i\geq 0$ para todo $1\leq i\leq 4$. Consideremos ahora las cuatro variables como cuatro *urnas* indistinguibles y el valor que aparece en el miembro derecho de la ecuación, $25$, como las $25$ *bolas* idénticas que vamos a introducir en las urnas. Utilizando la estrategia de *barras y estrellas*, necesitamos tres *barras* para representar sobre la recta real las cuatro urnas y buscamos ubicar luego $25$ *estrellas* en los huecos que dicha configuración produce. Por consiguiente, el número de formas en que el valor de la suma de cuatro variables puede ascender a $25$, equivale a la cantidad de permutaciones con repetición de $28$ elementos, donde uno de ellos se repite tres veces, mientras que el otro lo hace en $25$ ocasiones. Así, hay

$$
PR_{28}^{3,25} = CR_{4,25} = \dbinom{28}{25} = \dfrac{28\cdot27\cdot26}{3!} = 3276
$$

soluciones enteras no negativas para la ecuación que acabamos de plantear. Entre ellas, será válida, por ejemplo, una solución como $x_1=25$ y $x_2=x_3=x_4=0$, que en el contexto que plantea el enunciado del presente ejercicio es absurda, pues recordemos habíamos dotado a cada una de las variables el significado de ser cifras y, por tanto, sus valores han de estar comprendidos entre cero y nueve. Veamos pues, a continuación, como descontar este tipo de soluciones incorrectas.

Definamos, acto seguido, los conjuntos $A_i=\\{x_i\geq 10\\}$, por lo que estamos interesados en hallar el valor de $card(\overline{A_1} \cap \overline{A_2} \cap \overline{A_3} \cap \overline{A_4})$. Por el *Principio de complementación*,

$$
card(\overline{A_1} \cap \overline{A_2} \cap \overline{A_3} \cap \overline{A_4}) = card(E) - card(A_1\cup A_2\cup A_3\cup A_4),
$$

donde por $E$ representamos al *conjunto total*, que en este contexto se refiere al total de soluciones enteras no negativas de la ecuación planteada y cuyo cardinal hemos obtenido en párrafos anteriores, $PR_{28}^{3,25} = 3276$. Aplicando ahora el *Principio de inclusión-exclusión*,

$$
card\left(\bigcup_{i=1}^{4}{A_i}\right) = \sum_{i=1}^{4}{card(A_i)} - \sum_{1\leq i < j\leq 4}{card( A_i\cap A_j )} + \cdots + (-1)^{n+1} card\left(\bigcap_{i=1}^{4}{A_i}\right).
$$

Estudiemos ahora el conjunto $A_1 = \\{x_1\geq 10\\}$ y averigüemos $card(A_1)$. La situación requiere calcular el número de soluciones enteras no negativas para la ecuación $x_1+x_2+x_3+x_4=25$, con $x_1\geq 10$, $x_i\geq 0$ para $2\leq i\leq 4$. Pensando en términos de urnas y bolas, hemos de almacenar diez bolas en la primera urna y pasar a encontrar entonces el número de soluciones enteras no negativas de la ecuación $x_1+x_2+x_3+x_4=15$, ahora con $x_i\geq 0$, para $1\leq i\leq 4$. Aplicando, de manera análoga a como lo hicimos arriba, la técnica de *barras y estrellas*, sabemos que dicho número equivale al total de permutaciones con repetición de $18$ elementos, donde uno de ellos se repite tres veces, mientras que el otro lo hace en $15$ ocasiones, esto es,

$$
PR_{18}^{3,15} = CR_{4,15} = \dbinom{18}{15} = \dfrac{18\cdot17\cdot16}{3!} = 816.
$$

Por simetría, $card(A_1)=card(A_2)=card(A_3)=card(A_4)=816$, de manera que

$$
\sum_{i=1}^{4}{card(A_i)} = 4\cdot816 = 3264.
$$

Ahora, hallemos $card(A_1\cap A_2)$, donde $A_1\cap A_2 = \\{x_1\geq 10, x_2\geq 10\\}$. La situación requiere calcular el número de soluciones enteras no negativas para la ecuación $x_1+x_2+x_3+x_4=25$, con $x_1\geq 10$, $x_2\geq 10$ y $x_i\geq 0$ para $3\leq i\leq 4$. Razonando en términos de urnas y bolas, hemos de almacenar diez bolas en la primera urna, otras tantas en la segunda urna y pasar a buscar entonces el número de soluciones enteras no negativas de la ecuación $x_1+x_2+x_3+x_4=5$, ahora con $x_i\geq 0$, para $1\leq i\leq 4$. Utilizando, como antes, la técnica de *barras y estrellas*, sabemos que el mencionado número equivale al total de permutaciones con repetición de ocho elementos, donde uno de ellos se repite tres veces, mientras que el otro lo hace en cinco ocasiones, es decir,

$$
PR_{8}^{3,5} = CR_{4,5} = \dbinom{8}{5} = \dfrac{8\cdot7\cdot6}{3!} = 56.
$$

Por simetría, el resto de cardinales de los conjuntos $A_{i} \cap A_{j}$, con $1\leq i < j \leq 4$ ascenderán al mismo valor. Como el orden en el que seleccionemos los conjuntos implicados no tiene relevancia y no existe posibilidad de repetir elemento alguno, en total su número será igual a la cantidad de combinaciones de cuatro elementos tomados de dos en dos, $C_{4,2}$, luego

$$
\sum_{1 \leq i < j \leq 4}{card(A_{i} \cap A_{j})} = C_{4,2} \cdot PR_{8}^{3,5} = \dbinom{4}{2}\cdot 56 = 336.
$$

Acto seguido, el cardinal de los conjuntos $A_i\cap A_j\cap A_k$, con $1\leq i<j<k\leq 4$ y el del conjunto $A_1\cap A_2\cap A_3\cap A_4$ será cero, pues si tres o más variables poseen un valor mayor o igual que diez, es imposible satisfacer la ecuación $x_1+x_2+x_3+x_4=25$ en los enteros no negativos. Por tanto, recapitulando,

$$
card(\overline{A_1} \cap \overline{A_2} \cap \overline{A_3} \cap \overline{A_4}) = 3276 - (3264 - 336) = 346
$$

son los números naturales menores que $10000$ que cumplen que la suma de sus cifras es $25$.
