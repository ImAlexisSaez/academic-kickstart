---
title: Introducción del curso
linktitle: Introducción
summary: Primeros pasos con Python

date: "2019-04-28T00:00:01+01:00"
lastmod: "2019-04-28T00:00:01+01:00"
draft: false
toc: true
type: book
weight: 10
---

## Introducción del curso

### Vídeo

{{< youtube G2FCfQj-9ig >}}

### Notas personales

En este vídeo, se presenta el curso de *Python* y los motivos de su desarrollo. Después se revisa el **temario**, que aborda:

- Introducción. Requisitos previos. Instalación software.
- Fundamentos y sintaxis básica del lenguaje.
- POO con Python.
- Algoritmos, listas y tramos.
- BBDD.
- Trabajo con gráficos y contenidos.
- Procesos y tareas.
- Programación de red. Sockets.
- Ejercicios prácticos.

La lección termina con un breve apartado de FAQ.

## Introducción a Python

### Vídeo

{{< youtube 9ojhJsXNWCI >}}

### Notas personales

En este vídeo, se repasa la historia de *Python* y sus principales características. Entre ellas, destacan:

- Lenguaje interpretado de alto nivel, orientado a objetos, versátil y que es de código abierto.
- Gramática sencilla, clara y muy legible, con tipado dinámico y fuerte

A través de [este enlace](https://www.python.org/downloads/) descargamos la última versión de *Python* (3.7.3 a la hora de escribir estas líneas). Si queremos la versión de 64 bits para *Windows*, hemos de buscarla en [esta página](https://www.python.org/downloads/windows/).

Durante su instalación:

- Activamos la casilla que añade la ruta de *Python* al `PATH`.
- Pulsamos, al final de la instalación, sobre la opción que elimina la restricción de longitud máxima sobre las rutas del `PATH`.

Con respecto a los IDE, en el curso se utilizará [Sublime Text 3](https://www.sublimetext.com/3), aunque se ofrecen como alternativas [Eclipse](https://www.eclipse.org/ide/) y [Notepad++](https://notepad-plus-plus.org/).

## Sintaxis básica

### Vídeo

{{< youtube yppT6GPZMyo >}}

### Notas personales

En el IDLE de *Python*, tecleamos:

```python
>>> print("¡Hola mundo!") # Esto es una instrucción
¡Hola mundo!
```

Usando `;` escribimos varias instrucciones en una misma línea, aunque es desaconsejable por restar legibilidad.

```python
>>> print("¡Hola mundo!"); print("¡Bienvenidos!")
¡Hola mundo!
¡Bienvenidos!
```

Introducimos los **comentarios** con el símbolo `#` para:

- Anotar el código, facilitando futuros mantenimientos.
- Desactivar bloques de instrucciones, para localizar errores cometidos.

```python
>>> # Esto es un comentario
... 
```

Mediante el símbolo `\` dividimos una instrucción en varias líneas, aunque es desaconsejable por restar legibilidad.

```python
>>> mi_nombre = "Mi nombre es Alexis."
>>> mi_nombre
'Mi nombre es Alexis.'
>>> mi_nombre = "Mi nombre es \
... Alexis"
>>> mi_nombre
'Mi nombre es Alexis'
```

Construimos los bloques de código mediante **identación**. El IDLE se encarga automáticamente de procurarla:

```python
>>> a = 0
>>> for i in range(5):
...     a += 1
...     print(a)
... 
1
2
3
4
5
>>> 
```

Durante el curso, usaremos el IDLE de *Sublime Text 3*. Para ello, descargamos el editor a través de [este enlace](https://www.sublimetext.com/3) y lo instalamos. Al iniciarlo:

- Desplegamos el menú `Tools` y seleccionamos `Command Palette...`.
- Escribimos `Install Package Control` y clicamos sobre la opción que aparece.
- Desplegamos, de nuevo, el menú `Tools`, seleccionamos `Command Palette...` y tecleamos `install package`.
- En la siguiente ventana, escribimos `SublimeREPL`, para así tener el interprete de *Python* disponible desde el propio editor.
- Para activarlo, desde el menú `Tools`, seleccionamos ahora `SublimeREPL` y buscamos `Python`. Entre las opciones que aparecen, escogemos `Python`.