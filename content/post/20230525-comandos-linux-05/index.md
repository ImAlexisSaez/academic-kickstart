---
title: "Comandos de Linux #05"
slug: "comandos-de-linux-05"
subtitle: "Abordando el uso de *alias*"
summary: "Lección 5: Abordando el uso de *alias*."

date: 2023-05-25T00:00:01+02:00
# lastmod: 2023-04-29T00:00:01+02:00

authors: ["admin"]
math: false
draft: false
featured: false

tags: ["Linux", "Terminal", "The Odin Project"]
categories: ["Programación"]
# projects: []

image:
   focal_point: "Smart"
   caption: "Fotografía de [Gabriel Heinzer](https://unsplash.com/es/@6heinz3r), disponible en [Unsplash](https://unsplash.com/es/fotos/4Mw7nkQDByk)."
---

## Abordando el uso de *alias*

Al final de la [lección anterior](/2023/05/24/comandos-de-linux-04/), incluimos un *alias* en el archivo de configuración de la terminal que nos permite limpiar esta tecleando únicamente `c`.

Así pues, un *alias* nos ofrece la posibilidad de crear nuevos comandos a partir de los ya existentes. En la mayoría de los casos se busca automatizar tareas cotidianas de una manera más corta o incluir ciertos atributos por defecto cuando tecleamos la versión sin atributos de un determinado comando.

Para tener acceso a un listado de los *alias* disponibles en nuestra terminal, basta teclear en ella

```bash
alias
```

En ella podemos apreciar que uno de los comandos que examinamos en lecciones anteriores, `ll`, no es más que un *alias* del comando `ls`, al que añade los atributos `-alF`. De hecho, el propio comando `ls` es un *alias* de sí mismo configurando cierta opción para colorear.

En mi caso, el anterior listado es reducido, ya que apenas cuenta con diez líneas. Sin embargo, es posible acceder a la definición concreta de un *alias* como el generado para la tecla `c` escribiendo

```bash
alias c
```

La terminal devuelve `alias c='clear'`. A medida que incorporemos más y más *alias*, puede resultar conveniente acceder a la definición concreta de uno de ellos para disponer de todos sus detalles.

Si en algún momento precisamos eliminar un *alias*, simplemente hemos de utilizar el comando `unalias` declarando como argumento el atajo correspondiente. Por ejemplo,

```bash
unalias c
```

Desactivaría la posibilidad de limpiar la pantalla de la terminar utilizando únicamente la tecla `c`. No obstante, como dicho *alias* está incluido en el archivo de configuración de la terminal, cuando iniciemos una nueva sesión de esta, volverá a estar disponible el *alias* asignado a la tecla `c`. Para eliminarlo por completo, deberíamos editar el mencionado archivo de configuración y suprimir la línea correspondiente a la definición de dicho *alias*.

Es posible que nos resulte útil los cinco procesos que más uso están haciendo de la *CPU*. El comando asociado a ello es un tanto complejo

```bash
ps auxf | sort -nr -k 3 | head -5
```

De esta forma, si este es un dato que queremos consultar con cierta frecuencia, tiene sentido definir un *alias* para el mismo

```bash
alias cp5='ps auxf | sort -nr -k 3 | head -5'
```

*Nota*: en realidad, el anterior*alias* no es un comando, sino una composición de comandos. Como podemos apreciar, usa el símbolo `|` para redirigir los resultados de un comando hacia el argumento de entrada para otro. En el ejemplo anterior, se ejecuta el comando `ps` con ciertos atributos, la salida del cual se envía al comando `sort` y esta al comando `head` para producir el resultado final que se muestra en la terminal.

Para conocer el mismo dato, pero asociado al uso de la memoria, podemos definir un *alias* que es ciertamente similar al anterior

```bash
alias mem5 = 'ps auxf | sort -nr -k 4 | head -5'
```

Finalmente, algunos *alias* recomendados son

```bash
alias h='history'
alias install='sudo apt install'
```

Aunque, como hemos visto arriba, si nos encontramos en una situación donde habitualmente escribimos largos comandos o encadenamos siempre la misma secuencia de comandos, es recomendable definir un *alias* que nos ahorre tiempo.

## Referencias

- [Linux Commands for Beginners 08 - Command Aliases](https://youtu.be/ehKAIWJWI8Y)
- [The Odin Project](https://www.theodinproject.com/)
