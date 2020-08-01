---
title: 42. Interfaces gráficas I
linktitle: 42. Interfaces I
toc: true
type: book
date: "2019-05-20T00:00:02+01:00"
lastmod: "2019-05-20T00:00:02+01:00"
draft: false
weight: 42
---

## Vídeo

{{< youtube hTUJC8HsC2I >}}

## Notas personales

En esta lección, comenzamos el estudio de las **interfaces gráficas** en *Python*, analizando para ello la librería `Tkinter`. Las interfaces gráficas, también denominadas GUI, son intermediarios entre el programa y el usuario. Están formadas por un conjunto de gráficos como ventanas, botones, menús, casillas de verificación, etc.

Además de la mencionada, existen otras librerías alternativas para trabajar con interfaces gráficas:

- `WxPython`
- `PyQT`
- `PyGTK`

`Tkinter` es un ''puente'' entre *Python* y la librería `TCL / TK`.

La estructura de una interfaz gráfica en *Python* es:

- *Raíz*: la ventana de la aplicación propiamente dicha.
- *Frame*: estructura que agrupa diversos elementos.
- *Widgets*: elementos de la aplicación. En ocasiones, al *frame* también se le considera un *widget* más.

A continuación, veamos cómo construir la raíz:

```python
from tkinter import Tk

raiz = Tk()

raiz.mainloop()
```

Al ejecutar el anterior bloque de código aparece una ventana en blanco en nuestro escritorio, con algunos botones que permiten interactuar con ella a la manera que estamos habituados.

{{< figure src="/courses/python-basic/img/pb42-img01.png" title="Primera ventana." numbered="true" >}}

Para que una ventana pueda mantenerse en ejecución, debe estar en una especie de ''bucle infinito'' (a la espera o escucha de eventos), estado que conseguimos a través de la función `mainloop()`, que, por el momento, habrá de estar siempre al final de nuestros programas.

La documentación para la librería `Tkinter` la podemos encontrar siguiendo [este enlace](https://docs.python.org/3/library/tk.html).

Modifiquemos algunas de las características que esta ventana posee por defecto:

```python
from tkinter import Tk

raiz = Tk()

raiz.title("Ventana de pruebas")
raiz.resizable(width=False, height=False)  # raiz.resizable(0, 0)
raiz.iconbitmap("icon.ico")
raiz.geometry("450x300")
raiz.config(bg="lightblue")
raiz.mainloop()
```

*Notas*:

- `title()` nos permite cambiar el título de la ventana generada.
- `resizable()` acepta dos valores booleanos para indicar si permitimos que se modifique la anchura o la altura de la ventana. Según los argumentos escogidos, incluso queda deshabilitado el botón de maximizar ventana.
- `iconbitmap()` nos da la posibilidad de cambiar el icono de la ventana generada, que, por defecto, es una especie de pluma. Para ello, hemos de almacenar en el directorio de la aplicación (o tener bien localizada su ruta) un archivo de extensión `.ico` (buscar en *Google* ''conversor .ico'' para acceder a aplicaciones online que nos generen este tipo de ficheros).
- `geometry()` configura el ancho y el alto de la ventana.
- `config()`, entre otras acciones, nos permite cambiar el color del fondo.

{{< figure src="/courses/python-basic/img/pb42-img02.png" title="Modificando propiedades de la ventana." numbered="true" >}}

Hasta el momento, las ventanas requieren de la consola de *Python* para su funcionamiento. Si queremos que este sea independiente de ella, hemos de modificar la extensión de la aplicación de `.py` a `.pyw`.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/42/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
