---
title: "Comandos de Linux #03"
slug: "comandos-de-linux-03"
subtitle: "Examinando los comandos `cp`, `mv` y `rm`"
summary: "Lección 3: Moviendo y renombrando archivos."

date: 2023-05-23T00:00:01+02:00
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

## Moviendo y renombrando archivos

Para empezar, de cara a copiar un archivo usamos el comando `cp`, que posee dos argumentos: el archivo a copiar y el nombre del nuevo archivo donde será copiado. Por ejemplo

```bash
cp test2.txt newfile.txt
```

Ahora, con el comando `cat` podemos comprobar que el contenido de ambos archivos es exactamente el mismo. No obstante, existe otro comando más apropiado para llevar a cabo esta tarea de comparación: `diff`, que nos indica en qué difieren dos archivos. Así,

```bash
diff newfile.text test2.txt
```

No arroja salida alguna, es decir, no hay ninguna diferencia entre ambos archivos. Sin embargo,

```bash
diff newfile.text test3.txt
```

Sí arroja resultados, pues son ficheros cuyos contenidos difieren.

Por otra parte, de cara a borrar un archivo, el comando a usar es `rm`. Por ejemplo

```bash
rm newfile.txt
```

Este comando también elimina directorios (con el atributo `-r` que activa la recursión), por lo que hemos de ser cautos cuando lo empleamos. Esta instrucción no mueve el archivo a una suerte de *Papelera de reciclaje* como en *Windows*, sino que lo elimina por completo del sistema. Si después lo queremos recuperar tendríamos que usar herramientas específicas de recuperación de archivos en memoria.

A continuación, antes de aprender a mover archivos, creemos un nuevo directorio, con el comando `mkdir` para almacenarlos. Por ejemplo

```bash
mkdir linux-notes
```

Ahora, para mover los archivos, el comando a emplear es `mv` cuyo primer argumento será el nombre del archivo a mover y el segundo su destino.

Podemos emplear *comodines* en las instrucciones de la terminal para algunos comandos. Por ejemplo, `*.txt` se traduce en todos los archivos cuya extensión sea `.txt`. De esta manera, podemos mover en bloque todos los ficheros de prueba que hemos creado hasta el momento.

```bash
mv *.txt linux-notes
```

Recordemos que con el comando `cd` cambiamos el directorio y si tecleamos `cd ..` volvemos un paso atrás en la ruta (o a un nivel inferior). Así, siguiendo la misma lógica, si queremos mover un paso atrás en la ruta alguno de los archivos, basta escribir

```bash
cd linux-notes
mv testfile.txt ..
cd ..
ls -l
```

Además, hemos de tener en cuenta que si `..` indica un nivel inferior, `.` indica el nivel actual (el directorio de trabajo). Esto nos permite usar el comando `mv` para mover archivos hacia la actual ruta donde nos encontremos. Por ejemplo, para traer de vuelta el archivo `testfile.txt` al directorio `linux-notes`, bastaría teclear:

```bash
cd linux-notes
md ../testfile.txt .
ls -l
```

Finalmente, de cara a renombrar archivos, empleamos el mismo comando que para moverlos. Por ejemplo

```bash
mv test3.txt abc.txt
ls -l
```

Con este comando también hemos de ser cautos para no renombrar un archivo con el nombre de un fichero existente, pues podemos sobreescribirlo. En algunas distribuciones de *Linux* esto sucede directamente (*Xubuntu* es un ejemplo de esta forma de proceder) y en otras pregunta si deseamos realizar dicha acción.

```bash
mv abc.txt test4.txt
ls -l
```

## Referencias

- [Linux Commands for Beginners 06 - Moving and Renaming Files](https://youtu.be/cSBYvSA9rDM)
- [The Odin Project](https://www.theodinproject.com/)
