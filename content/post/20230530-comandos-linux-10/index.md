---
title: "Comandos de Linux #10"
slug: "comandos-de-linux-10"
subtitle: "Revisando *logs*"
summary: "Lección 10: Revisando *logs*"

date: 2023-05-30T00:00:01+02:00
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

## Revisando *logs*

En esta lección examinaremos la gestión de *logs*, a los que recurriremos habitualmente para examinar la información que recopilen nuestras aplicaciones (errores, acciones...).

*Nota*: a la hora de trabajar con *logs* es posible que necesitemos privilegios de administrador (*root*) para revisar algunos de ellos, por lo que quizá nos veamos forzados a emplear el comando `sudo`.

Empecemos revisando `syslog`, que contiene una enorme cantidad de información que el sistema va almacenando en dicho archivo. Para ello, emplearemos el comando `cat`

```bash
sudo cat /var/log/syslog
```

¿Qué más *logs* tenemos a nuestra disposición?

```bash
cd /var/log/
ls -l
```

*Nota*: a modo de curiosidad, el sistema gestiona *logs* como `syslog` de manera inteligente, rotándolos y comprimiéndolos para que ocupen el menor espacio posible.

En el interior del directorio de *logs* observamos que existen asimismo carpetas. Por ejemplo, hay una asociada al paquete *Apache* que instalamos en lecciones anteriores

```bash
sudo su
cd apache2/
ls -l
cat error.log
exit
```

*Nota*: mi usuario no tiene permiso para acceder a la carpeta de *logs* de *Apache*. Buscando en *Google* [este post](https://stackoverflow.com/questions/8221820/cd-into-directory-without-having-permission) de *stackoverflow* ha resultado de ayuda. Activamos un modo de "súper usuario" con `sudo su`, ejecutamos los comandos deseados y salimos de dicho modo con `exit`.

En el *log* `dmesg` encontramos información principalmente referente al *hardware* del sistema

```bash
sudo cat dmesg
```

A modo de curiosidad, *Linux* posee un comando específico para acceder a este tipo de información sin necesidad de revisar el correspondiente *log*. Por ejemplo, podemos volver a nuestra carpeta de usuario y teclear `sudo dmesg`

```bash
cd ~
sudo dmesg
```

Así, tenemos acceso a una cantidad de información apabullante de bajo nivel sobre el sistema.

Por otra parte, como estamos trabajando con archivos de extensión considerable, quizá sea conveniente utilizar de manera adicional los comandos `head` o `tail` para centrar el foco de atención, respectivamente, en el principio o el final del archivo (10 líneas por defecto).

```bash
sudo head /var/log/syslog
sudo tail /var/log/syslog
```

Con el atributo `-n` declaramos el número de líneas que deseamos consultar

```bash
sudo head -n 15 /var/log/syslog
sudo tail -n 5 /var/log/syslog
```

Un atributo muy útil para `tail` es `-f` (*follow*), que deja la terminal en suspenso y nos permite ver cambios en tiempo real en el correspondiente *log*.

```bash
sudo tail -n 5 -f /var/log/syslog
```

Así, podemos controlar cualquier cambio en el sistema (por ejemplo, el reinicio de un proceso) que añada información a `syslog`. Para terminar el seguimiento del archivo, usamos la combinación de teclas `Ctrl + c`.

*Nota*: una aplicación práctica la encontramos a la hora de reproducir errores que los usuarios reportan en tiempo real para cierto servidor.

Finalmente, otro comando de utilidad para revisar *logs* es `journalctl`

```bash
sudo journalctl -u apache2
```

*Nota*: este comando también permite realizar seguimiento con el atributo `-f`.

Podemos conseguir resultados similares concatenando `cat` y `grep` (este último comando nos permite realizar búsqueda de texto sobre un archivo o salida de otro comando)

```bash
sudo cat /var/log/syslog | grep apache2
```

## Referencias

- [Linux Commands for Beginners 13 - Viewing Logs](https://youtu.be/Ei276TjyxCA)
- [The Odin Project](https://www.theodinproject.com/)
