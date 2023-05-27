---
title: "Comandos de Linux #09"
slug: "comandos-de-linux-09"
subtitle: "Gestionando procesos en *Linux*"
summary: "Lección 9: Gestionando procesos en *Linux*"

date: 2023-05-29T00:00:01+02:00
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

## Gestionando procesos en *Linux*

En esta lección abordaremos cómo gestionar procesos en *Linux*. Estudiaremos el comando `systemctl`, que permite iniciar, detener y reiniciar servicios que se ejecutan en segundo plano (que habitualmente reciben el nombre de *units*).

Comencemos instalando de nuevo *Apache*, que nos servirá de base para los ejemplos de esta lección

```bash
sudo apt install apache2
```

Recordemos que si ahora abrimos el navegador y escribimos en la barra de direcciones `localhost`, accederemos a la página por defecto de *Apache*. Esto es posible debido a que *Apache* se ejecuta en segundo plano, como podemos comprobar si tecleamos en la terminal

```bash
systemctl status apache2
```

Aparece `enabled` en la fila correspondiente a `Loaded:`, esto es, cuando iniciemos el sistema, *Apache* automáticamente se iniciará. Además, es el comportamiento que viene predefinido al instalar este paquete, pues así está declarado en `vendor preset`, con un valor asimismo de `enabled`.

*Nota*: estas características son las responsables de que una vez hayamos instalado el paquete, hayamos podido acceder a la página por defecto de *Apache* en el navegador sin tener que iniciar proceso alguno para ello.

En la línea encabezada por `Active:` observamos que está activo el proceso y en funcionamiento, indicándonos desde cuándo.

Por otro lado, en la parte final deberíamos haber tenido acceso a cierta información (*logs*), pero en mi distribución no aparece por defecto. Para visualizar los *logs* hemos de anteceder el anterior comando con `sudo`

```bash
sudo systemctl status apache2
```

Podemos desactivar *Apache* sin más que teclear

```bash
sudo systemctl disable apache2
```

Si ahora ejecutamos

```bash
systemctl status apache2
```

Observaremos que el proceso sigue en funcionamiento (`active (running)`), pero en la línea encabezada con `Loaded:` ahora aparece `disabled`, lo cual indica que la próxima vez que iniciemos el sistema, *Apache* no se iniciará de manera automática.

Para detener el proceso, hemos de teclear

```bash
sudo systemctl stop apache2
```

```bash
systemctl status apache2
```

Ahora podemos observar como en la línea encabezada por `Active:` figura `inactive (dead)`. De hecho, si refrescamos la página del navegador aparece un error en la misma.

A continuación, restauremos el comportamiento por defecto de *Apache*. Para empezar, asegurémosnos que arranca automáticamente la próxima vez que iniciemos el sistema. Para ello

```bash
sudo systemctl enable apache2
```

```bash
systemctl status apache2
```

Comprobamos que vuelve a aparecer `enabled` en la línea encabezada por `Loaded:`. Ahora, iniciamos el proceso sin más que teclear

```bash
sudo systemctl start apache2
```

```bash
systemctl status apache2
```

De manera que todo vuelve a funcionar como al principio de la lección.

Finalmente, para reiniciar un proceso, hemos de escribir

```bash
sudo systemctl restart apache2
```

```bash
systemctl status apache2
```

Comprobaremos que se ha reiniciado el proceso observando desde cuándo está activo.


## Referencias

- [Linux Commands for Beginners 12 - Managing systemd Units](https://youtu.be/ZhW6mzzyqlM)
- [The Odin Project](https://www.theodinproject.com/)
