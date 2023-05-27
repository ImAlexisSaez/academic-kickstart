---
title: "Comandos de Linux #08"
slug: "comandos-de-linux-08"
subtitle: "Gestionando los paquetes"
summary: "Lección 8: Gestionando los paquetes"

date: 2023-05-28T00:00:01+02:00
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

## Gestionando los paquetes

En esta lección abordaremos la instalación, eliminación y actualización de paquetes en nuestro sistema.

*Nota*: los métodos que se describen a continuación están diseñados para distribuciones basadas en *Debian* o *Ubuntu*.

El primer paso a llevar a cabo es la actualización de nuestro índice local de paquetes disponibles en el repositorio, es decir, en el servidor online desde el cual los descargaremos. Para ello, tecleamos

```bash
sudo apt update
```

En mi caso concreto, la mayoría de servidores con los que conecta son de *Ubuntu*, pero también observamos que aparece alguno de *Google* o de *Microsoft*.

A continuación, una vez actualizado el índice de paquetes, podemos buscar paquetes concretos en él desde la propia línea de comandos

```bash
apt search firefox
```

*Nota*: en esta ocasión no necesitamos anteceder el comando con `sudo`, pues no vamos a realizar cambios en el sistema. Cuando queramos instalar un paquete, por ejemplo, sí será necesario incluir ese comando en la sentencia.

El listado es bastante extenso en este ejemplo concreto, pues muestra todos los paquetes relacionados con *Firefox* (desde idiomas a extensiones, pasando por el propio navegador en sí).

Para instalar un paquete concreto, la instrucción es `sudo apt install` seguida el nombre del paquete a instalar. Por ejemplo, para instalar el editor de texto plano *Vim* escribimos

```bash
sudo apt install vim-nox
```

Como ejemplo más práctico, instalemos a continuación [Apache](https://ubuntu.com/server/docs/web-servers-apache), que es un servidor web que utilizamos a diario

```bash
apt search apache
```

```bash
sudo apt install apache2
```

A la hora de instalar este paquete, el comando `apt` se encarga de gestionar sus dependencias, de manera que nos indica qué paquetes adicionales son necesarios para realizar la instalación del que nos interesa. Como esta operación implica llevar a cabo más cambios de los que indicamos desde la línea de comandos, la instalación se detiene y espera a que el usuario confirme si realmente desea instalar tanto el paquete indicado como sus correspondientes dependencias.

*Nota*: además de las dependencias, `apt` recomienda la instalación de paquetes adicionales por su utilidad, aunque no fuerza a su instalación y deberíamos llevar a cabo el proceso después de manera manual.

Una vez instalado *Apache*, si escribimos en la barra de direcciones de *Chrome* (o cualquier navegador), `localhost` nos aparecerá la página por defecto de *Apache*.

Por otro lado, para eliminar un paquete del sistema, la instrucción es `sudo apt remove` seguida el nombre del paquete a eliminar. Por ejemplo

```bash
sudo apt remove apache2
```

Por defecto, no elimina las dependencias asociadas a *Apache*. Para solventar la situación tecleamos

```bash
sudo apt autoremove
```

Acto seguido, actualicemos los paquetes que tenemos instalados en nuestro sistema. En mi caso, desde que iniciamos la lección, la terminal me ha indicado cada vez que poseo 21 paquetes que no están actualizados. Para ello tecleamos

```bash
sudo apt update
```

```bash
sudo apt upgrade
```

```bash
sudo apt dist-upgrade
```

*Nota*: la última instrucción conviene ejecutarla cuando hayan quedado paquetes a eliminar o haya algunos que deban instalarse por primera vez, pues `sudo apt upgrade` no realiza estas labores por defecto.

*Nota*: por cuestiones de seguridad, conviene actualizar los paquetes con frecuencia.

Finalmente, en el caso que se hayan realizado actualizaciones del *kernel*, conviene reiniciar el sistema, para lo cual escribimos

```bash
sudo reboot
```

## Referencias

- [Linux Commands for Beginners 11 - Intro to Package Management on Debian-based Distributions](https://youtu.be/yxc2ntmH9xY)
- [The Odin Project](https://www.theodinproject.com/)
