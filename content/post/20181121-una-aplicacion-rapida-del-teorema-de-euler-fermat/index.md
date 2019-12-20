---
title: "Una aplicación rápida del Teorema de Euler-Fermat"
slug: "una-aplicacion-rapida-del-teorema-de-euler-fermat"
subtitle: "Problema 27"
summary: "Problema 27: presentando este importante resultado."

date: 2018-11-21T05:59:39+02:00
lastmod: 2018-11-21T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Problemas", "Teorema de Euler-Fermat", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [VanveenJF](https://unsplash.com/@vanveenjf), disponible en [Unsplash](https://unsplash.com/photos/dUbvR-i5Nsc)."
---

**Problema 27:** Calcula los dos últimos dígitos de $3^{1492}$.

***

Para encontrar los dos últimos dígitos de $3^{1492}$, un posible enfoque es hallar el valor de su congruencia módulo $100$. El número $100$ no es primo, pero sí que es cierto que $mcd(3, 100)=1$, situación que nos permite hacer uso del *Teorema de Euler-Fermat*. Este resultado afirma que 

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
