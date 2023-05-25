---
title: "Comandos de Linux #07"
slug: "comandos-de-linux-07"
subtitle: "Examinando el uso de recursos del sistema"
summary: "Lección 7: Examinando el uso de recursos del sistema"

date: 2023-05-27T00:00:01+02:00
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

## Examinando el uso de recursos del sistema

En esta lección abordaremos la gestión de recursos del sistema como, por ejemplo, uso de memoria, uso de espacio en disco, etc. El primer comando que analizaremos es

```bash
free
```

Este nos ofrece información relevante sobre el uso de memoria del sistema. No obstante, por defecto, la ofrece en *bytes*, comportamiento que podemos modificar haciendo uso del atributo `-m`:

```bash
free -m
```

En mi caso, al estar la distribución de *Xubuntu* virtualizada, los datos corresponden a los declarados en la configuración de la máquina virtual y no a los correspondientes al ordenador en sí.

Por otro lado, ¿cuál es la diferencia entre las columnas *free* y *available*? El dato que aparece en la columna *free* está verdaderamente libre de uso, mientras que *available* tiene en cuenta que algunas aplicaciones reservan parte de la memoria para su uso y puede que actualmente no estén haciendo uso de dicha reserva. Por ello este dato es más elevado, aunque, según las necesidades de las aplicaciones, es bastante variable.

A continuación, para analizar el espacio en disco usado, empleamos el comando `df` (abreviatura de *disk free*)

```bash
df
```

Para una lectura más cómoda de los números que aparecen en su salida, conviene agregar el atributo `-h`, que transforma las cantidades a *megabytes* o *gigabytes* según convenga.

```bash
df -h
```

A modo anecdótico, el espacio en disco puede agotarse:

- Cuando almacenamos demasiados elementos cuyo tamaño es considerable (películas, videojuegos...).
- Cuando almacenamos demasiados elementos, aunque su tamaño sea reducido. Cada distribución tiene un límite a este respecto y viene dado por el concepto de *Inodes*. Para acceder al listado de *Inodes* disponibles, basta teclear `df -i`.

Acto seguido, otro comando de gran utilidad es `htop`, que, en mi caso, no viene instalado por defecto en *Xubuntu*. Así pues, para solventar esta situación

```bash
sudo apt install htop
```

```bash
htop
```

A primera vista, nos recuerda al administrador de tareas de *Windows* y nos ofrece una cantidad enorme de información acerca de los recursos del sistema. Aún siendo una herramienta que se ofrece en la línea de comandos, podemos emplear el ratón para movernos por los diferentes menús disponibles.

Desde esta herramienta podemos cerrar procesos haciendo uso de la combinación `F9 + 15 SIGTERM` o, de haber quedado la aplicación totalmente congelada, con `F9 + 9 SIGKILL`. Para cerrar, hacemos clic sobre la opción correspondiente o simplemente pulsamos `F10`.

Finalmente, otro comando útil es

```bash
uptime
```

Este indica cuánto tiempo lleva en marcha la sesión actual y la carga media. Estos tres últimos valores no han de ser interpretados como porcentajes, pues los ordenadores de hoy en día poseen varios núcleos (un `0.12` no equivale pues a un 12% de carga, a no ser que nuestra máquina tenga un único núcleo). Además,

- El primer valor hace referencia a la carga media durante el último minuto.
- El segundo valor es con respecto a los últimos cinco minutos.
- El tercer valor es con respecto a los últimos quince minutos.

Los valores hemos de interpretarlos como tareas a la espera de ser ejecutadas por el sistema. Por ejemplo, `0,12` indica que, de media, menos de una tarea está en espera de ser ejecutada; es decir, el sistema está trabajando de manera bastante desahogada.

En otras palabras, y utilizando como analogía un supermercado, el número de núcleos del ordenador haría las veces de cajeros, mientras que las tareas serían los clientes a la espera de pagar sus compras. Si tenemos 2 núcleos y hay un cliente, el sistema funcionará bien e incluso habrá un cajero que se estará aburriendo en ese momento determinado. Con dos clientes todavía no encontramos problema, pues cada cajero está atendiendo su tarea asociada. El problema es cuando el número de clientes asciende, por ejemplo, a 20, pues los dos cajeros no dan abasto y las colas serán largas. En este último caso, algunas de las tareas del sistema tardarán en poder llevarse a cabo.

## Referencias

- [Linux Commands for Beginners 10 - Checking Resource Usage](https://youtu.be/kyt1xAlXITE)
- [The Odin Project](https://www.theodinproject.com/)
