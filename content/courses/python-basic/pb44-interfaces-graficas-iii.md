---
title: 44. Interfaces gráficas III
linktitle: 44. Interfaces III
toc: true
type: docs
date: "2019-05-21T00:00:02+01:00"
lastmod: "2019-05-21T00:00:02+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 44

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 44
---

## Vídeo

{{< youtube Nf4-gvf-tNg >}}

## Notas personales

En esta lección, analizaremos cómo trabajar con el *widget* `Label`, perteneciente a la librería `tkinter`, que nos permite mostrar texto o imágenes en nuestras interfaces gráficas. No es un elemento con el que podamos interactuar, es decir, no podremos borrarlo, arrastrarlo, etc.

Su sintaxis es:

```python
variable = Label(contenedor, opciones)
```

En [esta página](http://effbot.org/tkinterbook/label.htm) podemos consultar qué opciones disponibles ofrece el *widget* `Label`.

Para ver en acción este *widget*, reutilicemos como base parte del código generado en lecciones anteriores:

```python
from tkinter import Tk, Frame

root = Tk()

root.title("Probando el widget Label")
root.resizable(width=True, height=True)
root.iconbitmap("icon.ico")
root.config(bg="lightblue")

frame = Frame(root, width=500, height=400)

frame.pack()

root.mainloop()
```

Añadimos ahora, antes de la instrucción `root.mainloop()`, las líneas de código:

```python
label = Label(frame, text="Mi primera etiqueta.")
label.pack()
```

{{< figure src="/courses/python-basic/img/pb44-img01.png" title="Primer contacto con la clase `Label`." numbered="true" >}}

Quedando el resultado de la ejecución como una ventana bastante reducida porque, recordemos, la raíz se adapta al tamaño de sus elementos integrados (aunque le hayamos indicado ciertas dimensiones previamente). Ello se debe al uso del método `pack()`. Veamos el efecto que produce utilizar la función `place()` en su lugar, pasándole las coordenadas donde deseamos situar el *widget*:

```python
from tkinter import Tk, Frame, Label

root = Tk()

root.title("Probando el widget Label")
root.resizable(width=True, height=True)
root.iconbitmap("icon.ico")
root.config(bg="lightblue")

frame = Frame(root, width=500, height=400)

frame.pack()

label = Label(frame, text="Mi primera etiqueta.")
label.place(x=100, y=200)

root.mainloop()
```

{{< figure src="/courses/python-basic/img/pb44-img02.png" title="Utilizando la función `place()`." numbered="true" >}}

*Nota*: *Python* utiliza un curioso sistema de coordenadas. La coordenada `x` indica la distancia horizontal al comienzo del *widget* tal como estamos acostumbrados en matemáticas. Sin embargo, la coordenada `y` indica la distancia vertical al comienzo del *widget* tomando como referencia la parte superior de la ventana y siendo los valores positivos desplazamientos hacia abajo.

Si no vamos a utilizar en ningún momento la variable `label`, podemos aligerar un tanto el código escribiendo:

```python
from tkinter import Tk, Frame, Label

root = Tk()

root.title("Probando el widget Label")
root.resizable(width=True, height=True)
root.iconbitmap("icon.ico")
root.config(bg="lightblue")

frame = Frame(root, width=500, height=400)

frame.pack()

Label(frame, text="Mi primera etiqueta.").place(x=100, y=200)

root.mainloop()
```

A partir de aquí, ya únicamente nos queda experimentar con las diferentes opciones asociadas al *widget* `Label`:

```python
from tkinter import Tk, Frame, Label

root = Tk()

root.title("Probando el widget Label")
root.resizable(width=True, height=True)
root.iconbitmap("icon.ico")
root.config(bg="lightblue")

frame = Frame(root, width=500, height=400)

frame.pack()

Label(frame, text="Mi primera etiqueta.", fg="tomato",
      font=("Arial", 18)).place(x=100, y=200)

root.mainloop()
```

{{< figure src="/courses/python-basic/img/pb44-img03.png" title="Probando opciones adicionales para `Label`." numbered="true" >}}

Adicionalmente, el *widget* `Label` nos permite incluir (de forma nativa en la librería `tkinter`) imágenes de tipo *gif* o *png*. Por ejemplo, insertemos en nuestra aplicación [esta imagen](https://www.freepng.es/png-lwhgke/), que, en un alarde de originalidad, llamaremos `avengers.png`:

```python
from tkinter import Tk, Frame, Label, PhotoImage

root = Tk()

root.title("Probando el widget Label")
root.resizable(width=True, height=True)
root.iconbitmap("icon.ico")
root.config(bg="lightblue")

frame = Frame(root, width=500, height=400)

frame.pack()

imagen = PhotoImage(file="avengers.png")

Label(frame, image=imagen).pack()  # .place() es otra posibilidad

root.mainloop()
```

{{< figure src="/courses/python-basic/img/pb44-img04.png" title="Una imagen como `Label`." numbered="true" >}}

*Nota*: para que la ventana se adaptase automáticamente al tamaño de la imagen descargada, he utilizado el método `pack()` en lugar de la función `place()`. No obstante, con ambas opciones se puede conseguir el mismo resultado si ajustamos de manera fina sus correspondientes opciones.


## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/44/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
