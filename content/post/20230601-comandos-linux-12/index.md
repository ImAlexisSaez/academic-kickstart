---
title: "Comandos de Linux #12"
slug: "comandos-de-linux-12"
subtitle: "Examinando el historial de la terminal"
summary: "Lección 12: Examinando el historial de la terminal"

date: 2023-06-01T00:00:01+02:00
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

## Examinando el historial de la terminal

En esta lección abordaremos cómo aprovechar de nuevo acciones llevadas a cabo en la terminal.

En primer lugar, con las teclas de los cursores (arriba y abajo en este caso particular), podemos desplazarnos por el historial de comandos ejecutados. Ello nos permite ejecutarlos de nuevo o editarlos para lanzarlos de una forma ligeramente diferente a la terminal.

En segundo lugar, a través del comando

```bash
history
```

Tenemos acceso a la totalidad de comandos ejecutados en la terminal. Cada uno de ellos posee un número de referencia al principio de la línea, de manera que podemos ejecutarlos haciendo uso de dicho número, siempre y cuando antecedamos la referencia con el símbolo de exclamación `!`

```bash
!283
```

Si queremos que un comando no figure en el historial, basta pulsar la tecla de espacio antes de empezar a escribir el comando en cuestión

```bash
 sudo apt upgrade
```

*Nota*: No obstante, este comportamiento depende de la distribución de *Linux* empleada. En *Xubuntu*, efectivamente, podemos emplear este recurso para evitar que ciertos comandos aparezcan listados en el historial.

¿Qué puede llevarnos a querer omitir comandos en el historial de *Bash*? Por ejemplo, quizá sea una práctica recomendable para aquellos que posean cierta información sensible (datos, contraseñas...).

El historial también es una herramienta útil para averiguar cómo se han resueltos incidencias en el pasado (por otras personas, si es la primera vez que administramos cierto servidor que lleva operativo un tiempo).

## Referencias

- [Linux Commands for Beginners 15 - Bash History](https://youtu.be/U7ODlrzF41s)
- [The Odin Project](https://www.theodinproject.com/)
