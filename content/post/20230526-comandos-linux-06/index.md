---
title: "Comandos de Linux #06"
slug: "comandos-de-linux-06"
subtitle: "Introducción a los permisos en *Linux*"
summary: "Lección 6: Introducción a los permisos en *Linux*"

date: 2023-05-26T00:00:01+02:00
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

## Introducción a los permisos en *Linux*

Para empezar, la manera en que *Linux* gestiona los permisos es un tanto diferente a la que lleva a cabo *Windows*. 

Por ejemplo, al teclear `ls -l` en la terminal, dentro de la carpeta de usuario (`cd ~` para acceder a ella si estamos ubicados en un directorio de trabajo distinto), para la carpeta `Desktop` la línea comienza con la secuencia

```bash
drwxr-xr-x
```

El primer carácter, `d`, recordemos, indica que es un directorio. (`-` para archivos). El resto de los caracteres de la secuencia nos indica lo que podemos hacer (o no) con el directorio o archivo en cuestión.

Para interpretar la secuencia de caracteres, hemos de dividirla en cuatro secciones:

- *Sección 1*: el primer carácter, que sabemos indica el tipo de elemento del que se trata (archivo, directorio o enlace).
- *Sección 2*: los siguientes tres caracteres, que hacen referencia a los permisos del usuario al que pertenece el archivo o directorio. Dicho usuario aparece en la tercera columna del listado que genera el comando `ls -l`.
- *Sección 3*: los siguientes tres caracteres, que hacen referencia a los permisos del grupo al cual pertenece el archivo o directorio. Dicho grupo aparece en la cuarta columna del listado que genera el comando `ls -l`.
- *Sección 4*: los siguientes tres caracteres, que hacen referencia a los permisos del resto de usuarios que ni son propietarios ni pertenecen al grupo en cuestión (se denomina *world* en ocasiones a los usuarios a los que afecta esta sección).

En cada una de las posiciones de las secciones 2, 3 y 4 encontramos una letra de la secuencia `rwx` o bien un guion, `-`, que indica que el correspondiente permiso no está disponible. El orden siempre es `rwx` en dichas secciones, por lo que una subsecuencia como `r-x` indica la ausencia del permiso `w` para ese elemento en concreto en la sección asociada.

Ahora bien, ¿qué significa cada una de las letras?

- `r` es para *read*, esto es, es la letra asociada al permiso de lectura.
- `w` es para *write*, esto es, es la letra asociada al permiso de escritura o edición (incluso nos permitiría eliminar el elemento en concreto).
- `x` es para *execute*, esto es, es la letra asociada al permiso de ejecución. Está reservada para aquellos elementos en los que podemos insertar comandos y ejecutarlos como si fueran programas.

Para editar permisos en un elemento, empleamos el comando `chmod`. Por ejemplo, si deseamos añadir el permiso de ejecución a un archivo denominado `test.txt`, escribiríamos

```bash
chmod +x test.txt
```

Al volver a ejecutar `ls -l` observamos que el permiso `x` está disponible para el usuario, para el grupo y para el resto. Además, la terminal cambia su color a verde, para indicar que ahora es un archivo ejecutable.

Para devolver los permisos a su estado inicial, basta teclear

```bash
chmod -x test.txt
```

Además, como cabría esperar, podemos configurar el permiso `x` de manera que afecte solo a una sección. Por ejemplo, para asignar únicamente al propietario del archivo el permiso `x` hemos de escribir

```bash
chmod u+x test.txt
```

Para habilitar todos los permisos en un elemento a cualquier usuario, hemos de teclear `chmod a+rwx`. Por ejemplo,

```bash
chmod a+rwx test.txt
```

*Nota*: no es una práctica recomendable para directorios o archivos que contengan información sensible.

Por otro lado, la letra correspondiente para el grupo es `g`, de manera que si deseo retirar todos los permisos al grupo tendría que teclear

```bash
chmod g-rwx test.txt
```

*Nota*: esta configuración tiene poco sentido, pues todo el mundo tiene los permisos `rwx`.

Finalmente, para hacer referencia al resto de usuarios que ni son propietarios, ni pertenecen al grupo, la letra es `o`. Así, para retirarlos los permisos `rwx` teclearíamos

```bash
chmod o-rwx test.txt
```

Acto seguido, devolvamos los permisos a su estado original

```bash
chmod u-x test.txt
chmod g+rw test.txt
chmod o+r test.txt
```

Cambiando de tercio, los permisos se gestionan de manera diferente si se trata de archivos o de directorios. En el caso de los directorios:

- `r` nos permite visualizar su contenido.
- `w` nos permite editar o modificar el directorio.
- `x` nos permite acceder a su interior.

## Referencias

- [Linux Commands for Beginners 09 - Understanding Permissions](https://youtu.be/T269zebUSj8)
- [The Odin Project](https://www.theodinproject.com/)
