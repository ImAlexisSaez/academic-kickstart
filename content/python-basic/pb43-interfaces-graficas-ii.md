---
title: 43. Interfaces gráficas II
linktitle: 43. Interfaces II
toc: true
type: book
date: "2019-05-21T00:00:01+01:00"
lastmod: "2019-05-21T00:00:01+01:00"
draft: false
weight: 43
---

## Vídeo

{{< youtube M80CzDC1Crc >}}

## Notas personales

Después de introducir, en la lección anterior, la *raíz* de una interfaz gráfica, en esta abordaremos la construcción y uso de *frames*. Comencemos recuperando el código fuente de la ''aplicación'' que generamos con anterioridad:

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

A continuación, crearemos un frame y lo empaquetaremos (ubicaremos) dentro de la raíz disponible a través del método `pack()`. Además, prescindiremos de la instrucción `raiz.geometry()`, para así estar en condiciones de configurar el tamaño del *frame* (la raíz se adaptará automáticamente al tamaño de sus elementos internos):

```python
from tkinter import Tk, Frame

raiz = Tk()

raiz.title("Ventana de pruebas")
raiz.resizable(width=True, height=True)
raiz.iconbitmap("icon.ico")
raiz.config(bg="lightblue")

frame = Frame()
frame.pack()
frame.config(bg="tomato", width="450", height="300")

raiz.mainloop()
```

A primera vista, al ejecutar el aterior bloque de código, da la sensación de que hemos perdido el color de fondo declarado para la aplicación (`lightblue`). No obstante, como ahora permitimos manipular el tamaño de la ventana (mediante la instrucción `raiz.resizable(width=True, height=True)`), al agrandarla comprobamos que todo funciona correctamente.

{{< figure src="/courses/python-basic/img/pb43-img01.png" title="Los dos colores de fondo siguen disponibles." numbered="true" >}}

*Nota*: en [esta página](http://www.science.smith.edu/dftwiki/index.php/Color_Charts_for_TKinter) podemos encontrar un buen recurso para acceder a una paleta de colores declarados por nombres y disponibles para la librería `tkinter`.

Por otro lado, observamos que el *frame* tiene un tamaño fijo, por mucho que manipulemos el tamaño de la ventana, las dimensiones del *frame* no se alteran, así como su posición, que permanece centrada en la parte superior de la ventana de la aplicación. Este comportamiento es el dado por defecto, que podemos configurar de manera diferente, si así lo deseamos, a través del método `pack()`.

```python
from tkinter import Tk, Frame

raiz = Tk()

raiz.title("Ventana de pruebas")
raiz.resizable(width=True, height=True)
raiz.iconbitmap("icon.ico")
raiz.config(bg="lightblue")

frame = Frame()
frame.pack(side="left", anchor="s", fill="x", expand="True")
frame.config(bg="tomato", width="450", height="300")

raiz.mainloop()
```

{{< figure src="/courses/python-basic/img/pb43-img02.png" title="Modificando propiedades del *frame*." numbered="true" >}}

Las opciones de configuración de los *frames* son ciertamente numerosas. Por ejemplo, podemos añadirle un borde (parámetros `bd` y `relief`) o cambiar el icono del ratón cuando se adentra en el interior del *frame* (parámetro `cursor`):

```python
from tkinter import Tk, Frame

raiz = Tk()

raiz.title("Ventana de pruebas")
raiz.resizable(width=True, height=True)
raiz.iconbitmap("icon.ico")
raiz.config(bg="lightblue")

frame = Frame()
frame.pack(side="left", anchor="s")
frame.config(bg="tomato",
             width="450",
             height="300",
             bd=35,
             relief="groove",
             cursor="pirate")

raiz.mainloop()
```

{{< figure src="/courses/python-basic/img/pb43-img03.png" title="Añadiendo un marco al *frame*." numbered="true" >}}

Obviamente, todo aquello que hemos visto de cara a configurar un *frame* es aplicable a la propia *raíz* y dependerá de cómo deseemos diseñar nuestra aplicación.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/43/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
