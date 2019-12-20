---
title: "Presentando el Teorema de Wilson"
slug: "presentando-el-teorema-de-wilson"
subtitle: "Problema 29"
summary: "Problema 29: un resultado que da mucho juego en teoría de números."

date: 2018-11-28T05:59:39+02:00
lastmod: 2018-11-28T05:59:39+02:00

authors: ["admin"]
math: true
draft: false
featured: false

tags: ["Problemas", "Teorema de Wilson", "Teoría de números"]
categories: ["Oposiciones"]
projects: ["problemas"]

image:
  focal_point: "Smart"
  caption: "Fotografía de [Francesco Ungaro](https://unsplash.com/@francesco_ungaro), disponible en [Unsplash](https://unsplash.com/photos/p3NOK6MhvKQ)."
---

**Problema 29:** Prueba que $437$ es divisor de 

- (a) $16^{99} - 1$. 
- (b) $18! + 1$.

***

Para ambos apartados, vamos a aprovechar que $437 = 19\cdot 23$ y, de cara a demostrar que es divisor de los números dados en los apartados (a) y (b), estudiaremos si $19$ y $23$ lo son y, en caso afirmativo, por las propiedades de las congruencias, concluiremos que $437$ los divide.

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
