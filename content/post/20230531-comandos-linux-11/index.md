---
title: "Comandos de Linux #11"
slug: "comandos-de-linux-11"
subtitle: "Gestionando usuarios"
summary: "Lección 11: Gestionando usuarios"

date: 2023-05-31T00:00:01+02:00
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

## Gestionando usuarios

En esta lección abordaremos la gestión de usuarios, en concreto la creación y eliminación de usuarios, así como la creación y eliminación de grupos. Antes de empezar, es importante conocer la existencia del siguiente archivo

```bash
cat /etc/passwd
```

En él encontramos un listado de todos los usuarios existentes en nuestro sistema. En la mayoría de los casos, la línea finaliza con `/nologin`, es decir, son usuarios necesarios para llevar a cabo ciertas tareas de determinadas aplicaciones y no para acceder al sistema en sí.

En la línea correspondiente a mi usuario, `alexis`,

```bash
alexis:x:1000:1000:alexis,,,:/home/alexis:/bin/bash
```

Los números `1000` que aparecen son, respectivamente, las referencias para el usuario (*uid*) y el grupo al que pertenece (también denominado `alexis` en este caso particular). A continuación, figura nuestro directorio de usuario (`/home/alexis`) y nuestra terminal por defecto (`/bin/bash`). Tras mi nombre de usuario aparece una `x`, que es la posición que ocuparía nuestra contraseña (oculta ahora mismo bajo ese carácter `x`). La contraseña, de hecho, se almacena en otro archivo diferente, ya que dista de ser idóneo que las contraseñas de los usuarios estén en un archivo de texto de libre acceso.

En general, si el *uid* es mayor o igual que `1000` se tratará de un usuario real, mientras que aquellos que posean referencias inferiores seguramente sean usuarios de sistema (y no aparecerán por defecto en las ventanas de *login* de usuario).

A continuación, si tecleamos

```bash
sudo cat /etc/shadow
```

*Nota*: un atajo útil de teclado es `!!` que ejecuta el anterior comando escrito en la terminal. Cuando escribimos una instrucción y no se lleva a cabo por falta de permisos, simplemente hemos de teclear `sudo !!` para intentar ejecutarla con permisos de *super user*.

El archivo muestra información sensible, pero no de forma abierta. En lugar de aparecer nuestra contraseña, aparece su *hash* (para los usuarios de sistema sí que aparece directamente su contraseña).

Otro archivo importante para conocer es

```bash
cat /etc/group
```

Nos muestra un listado de los grupos definidos en nuestro sistema, con sus respectivas referencias (así como sus contraseñas ocultas por el carácter `x`).

Si estamos interesados en conocer a qué grupos pertenecemos, no es necesario revisar el anterior fichero, ya que basta con teclear

```bash
groups
```

¿Cómo creamos un usuario? Mediante `adduser` seguido del nombre del nuevo usuario

```bash
adduser batman
```

Sin embargo, encontramos un problema al ejecutar el anterior comando, ya que la terminal nos indica que solo el usuario `root` puede añadir un usuario o un grupo al sistema. Como en anteriores ocasiones, solventamos la situación escribiendo

```bash
sudo adduser batman
```

Esta acción añade el usuario `batman`, así como el grupo `batman`, además de generar un directorio de usuario para él y proporcionarle ciertos archivos de configuración por defecto del sistema desde `/etc/skel`. Después, nos pide una contraseña para dicho usuario. A continuación, podemos indicar (o dejar en blanco) algunos datos del usuario, como su nombre completo, número de habitación, número de teléfono...

Si ahora escribimos

```bash
ls -l /home/
```

Aparece un nuevo directorio asociado al usuario `batman`.

Para cambiar a este usuario, hemos de escribir

```bash
su - batman
```

e introducir su correspondiente contraseña (la que hemos definido al crear el usuario). Si ahora tecleamos `logout` (o usamos la combinación de teclas `Ctrl + d`), volvemos a nuestro usuario principal. Por otro lado, si escribimos `sudo su - batman` cambiamos de usuario sin necesidad de introducir la contraseña (al trabajar con `sudo` es como si adoptáramos el papel del todopoderoso usuario `root`).

*Nota*: con el comando `passwd` podemos cambiar la contraseña de un usuario.

*Nota*: para cambiar de usuario a `root`, hemos de teclear `sudo su -`.

Ahora, para eliminar un usuario el comando es `userdel -r` seguido del nombre del usuario a suprimir

```bash
sudo userdel -r batman
```

El atributo `-r` se emplea para eliminar asimismo el directorio del usuario, por lo que hemos de actuar con cautela cuando llevamos a cabo este proceso.

Acto seguido, para añadir un grupo, el comando es `groupadd` seguido del nombre del grupo

```bash
sudo groupadd heroes
cat /etc/group
```

Para introducir nuestro usuario en este nuevo grupo, el comando a emplear es

```bash
sudo usermod -aG heroes alexis
groups
```

No obstante, aunque hemos ejecutado el comando, no aparece el grupo `heroes` asociado a nuestro usuario. Para ello, hemos de hacer *logout* y *login* en el sistema. Sin embargo, en este momento, basta teclear

```bash
groups alexis
```

Para comprobar que, efectivamente, mi usuario pertenece al grupo `heroes`.

Eliminar un usuario de un grupo es también sencillo, ya que basta teclear

```bash
sudo gpasswd -d alexis heroes
groups alexis
```

Finalmente, para eliminar un grupo, escribimos

```bash
sudo groupdel heroes
```

Y podemos comprobar que, efectivamente, no pertenece al listado de grupos tecleando, por ejemplo, `tail /etc/group` y observando que no aparece al final ninguna línea asociada a `heroes`.

## Referencias

- [Linux Commands for Beginners 14 - Managing Users](https://youtu.be/DmdyxEJdt3k)
- [The Odin Project](https://www.theodinproject.com/)
