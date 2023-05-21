---
title: "Comandos de Linux #02"
slug: "comandos-de-linux-02"
subtitle: "Examinando los comandos `cat` y `touch` y los programas *nano* y *Vim*"
summary: "Lección 2: Editando archivos."

date: 2023-05-22T00:00:01+02:00
# lastmod: 2023-04-29T00:00:01+02:00

authors: ["admin"]
math: false
draft: false
featured: false

tags: ["Linux", "Terminal", "The Odin Project", "Vim"]
categories: ["Programación"]
# projects: []

image:
   focal_point: "Smart"
   caption: "Fotografía de [Gabriel Heinzer](https://unsplash.com/es/@6heinz3r), disponible en [Unsplash](https://unsplash.com/es/fotos/4Mw7nkQDByk)."
---

## Edición básica de archivos

Para empezar, creamos un archivo mediante el comando `touch`, al que pasamos como argumento el nombre deseado para el mencionado archivo. Por ejemplo, para generar un fichero denominado `testfile.txt` tecleamos

```bash
touch testfile.txt
```

Acto seguido, si escribimos

```bash
ls -l
```

observamos que un nuevo archivo aparece en el listado, cuyo tamaño es `0`.

Ahora, para acceder al contenido de un archivo, empleamos el comando `cat`. Por ejemplo, en el caso del fichero que acabamos de generar, teclearíamos:

```bash
cat testfile.txt
```

aunque, al estar vacío, la terminal no arroja información alguna cuando ejecutamos el anterior comando. Por otro lado, si tecleamos de nuevo 

```bash
touch testfile.txt
```

como resultado se actualizará la fecha de creación del fichero.

Por otro lado, podemos editar archivos empleando el comando 

```bash
nano
```

que nos da acceso a un editor de texto plano. Si lo iniciamos de esta manera, no estaremos modificando ningún archivo (basta observar que en la parte superior aparece `New Buffer`). 

En la parte inferior de la aplicación figura el menú con todas sus opciones. El símbolo `^`, que aparece en todas ellas, ha de ser interpretado como el uso de la tecla `Ctrl`. Así, el atajo `^X`, para salir del programa, ha de ser ejecutado mediante la combinación `Ctrl + X`. Asimismo, para guardar (o salvar) un archivo tras escribir cierto texto, el atajo es `^O`, que equivale a la combinación `Ctrl + O`.

Si cerramos el editor de texto y ejecutamos `ls -l`, observaremos que aparece el nuevo archivo y este, a diferencia del anterior, posee cierto tamaño y podemos revisar sus contenidos mediante el comando `cat`.

Al comando `nano` le podemos añadir un atributo con el nombre del fichero que queremos editar. Por ejemplo

```bash
nano test3.txt
```

Este archivo no existía en el directorio actual, de manera que cuando salvemos lo creará con los contenidos que hayamos escrito. Siguiendo esta lógica, podríamos editar el archivo `testfile.txt` que generamos al principio de la sección

```bash
nano testfile.txt
```

*Nota*: la terminal posee autocompletado a través de la tecla `Tab`. Así, escribiendo el principio del nombre de un archivo o directorio y pulsando dicha tecla, se autocompleta la línea.

*Nota*: con el comando `which` podemos saber si una instrucción está disponible para su uso en la terminar. Por ejemplo, `which nano` nos devuelve la ruta hacia el ejecutable, mientras que `which prueba` no muestra salida, es decir, no existe ningún comando o aplicación en mi sistema con el nombre `prueba`.

## Una breve mirada a *Vim*

Un editor de texto plano muy completo es *Vim* y, por tanto, es recomendable aprender su uso. Quizá no a corto plazo, dada su elevada curva de aprendizaje; pero por sus muchos beneficios merece la pena invertir un tiempo a medio plazo para dominar esta aplicación si continuamos por la senda de la programación.

En mi caso particular, al teclear en la terminal `which vim`, esta no arroja respuesta alguna. Es decir, la mencionada aplicación no está instalada en mi sistema. Para solventar esta situación, basta teclear

```bash
sudo apt install vim-nox
```

*Vim*, como ya hemos mencionado, es un editor de texto plano más avanzado que `nano`, por lo que su uso es más complejo. Para empezar, salir de la propia aplicación no es nada intuitivo y lo haremos tecleando `:q` en el modo *command*.

Así pues, ya apreciamos que existen diversos modos o estados en *Vim*. Por ejemplo, pulsando la tecla `i` activamos el modo *insert* (mediante el cual podemos editar un archivo de la manera habitual) y con la tecla `Esc` retrocederíamos de nuevo al modo *command*. En este último modo, no podemos escribir como habitualmente estamos acostumbrados, sino que es el modo que empleamos en *Vim* para introducir instrucciones o comandos al programa.

De esta forma, para salvar el archivo que hemos escrito a través del modo *insert*, volvemos al modo *command* y escribimos `:w` (si pulsamos intro a continuación, recibiremos un error por no asignar un nombre al archivo). Así, tecleamos `:w test4.txt`. Al igual que sucedía con `nano`, podemos lanzar *Vim* con el nombre de un archivo como atributo, de manera que abrirá dicho fichero al iniciarse.

*Nota*: el atajo `shift + I` es muy útil, pues activa el modo *insert* y coloca el cursor al final del archivo. 

Si usamos 

```bash
vim test4.txt
```

y añadimos texto, bastará en el modo *command* teclear para `:w` para guardar el archivo (pues ya posee nombre asignado).

*Nota*: para borrar una línea por completo, podemos emplear el atajo que consiste en pulsar `d` dos veces en el modo *command*.

## Referencias

- [Linux Commands for Beginners 05 - Basic File Editing](https://youtu.be/T20jXu7rDCA)
- [The Odin Project](https://www.theodinproject.com/)
