---
title: 51. Interfaces gráficas X
linktitle: 51. Interfaces X
toc: true
type: docs
date: "2019-05-26T00:00:01+01:00"
lastmod: "2019-05-26T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 51

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 51
---

## Vídeo

{{< youtube TzeU61X-dnI >}}

## Notas personales

En esta lección, introduciremos el funcionamiento de la clase `Checkbutton`, que se encarga de gestionar los clásicos *botones de selección* (también denominados *casillas de verificación*). Estos nos permiten la posibilidad de realizar una selección múltiple sobre distintas opciones ofrecidas.

Acto seguido, veamos un sencillo ejemplo de aplicación de la mencionada clase, donde el usuario ha de escoger qué tipo de destinos prefiere para sus vacaciones.

```python
from tkinter import Checkbutton, Frame, IntVar, Label, PhotoImage, Tk

raiz = Tk()
raiz.title("Casillas de verificación")
raiz.iconbitmap("icon.ico")

playa = IntVar()
montana = IntVar()
turismo_rural = IntVar()


def opciones_viaje():
    opcion_escogida = ""
    if playa.get() == 1:
        opcion_escogida += " playa"
    if montana.get() == 1:
        opcion_escogida += " montaña"
    if turismo_rural.get() == 1:
        opcion_escogida += " turismo rural"
    texto_final.config(text=opcion_escogida)


foto = PhotoImage(file="helicoptero.png")
Label(raiz, image=foto).pack()

frame = Frame(raiz)
frame.pack()

Label(frame, text="Escoge destinos:", width=50).pack()

Checkbutton(frame,
            text="Playa",
            variable=playa,
            onvalue=1,
            offvalue=0,
            command=opciones_viaje).pack()
Checkbutton(frame,
            text="Montaña",
            variable=montana,
            onvalue=1,
            offvalue=0,
            command=opciones_viaje).pack()
Checkbutton(frame,
            text="Turismo rural",
            variable=turismo_rural,
            onvalue=1,
            offvalue=0,
            command=opciones_viaje).pack()

texto_final = Label(frame)
texto_final.pack()

raiz.mainloop()
```

Para empezar, el siguiente bloque de código

```python
foto = PhotoImage(file="helicoptero.png")
Label(raiz, image=foto).pack()
```

nos permite introducir, como cabecera de nuestra aplicación, la imagen de un helicóptero (disponible en [este enlace](https://www.freepng.es/png-ct7rpy/download.html)). 

A continuación, las líneas de código asociadas a la primera casilla de verificación son

```python
Checkbutton(frame,
            text="Playa",
            variable=playa,
            onvalue=1,
            offvalue=0,
            command=opciones_viaje).pack()
```

Observamos que dicha casilla está ubicada en el *frame* `frame` y muestra como texto, en la ventana de la aplicación, la palabra `Playa`. Para posibilitar la interacción con ella, almacenamos su valor en la variable `playa`, siendo este `1` cuando esté seleccionada y `0` en otro caso. Finalmente, su comportamiento se gestiona a través de la función `opciones_viaje()`, tal y como figura en el valor del parámetro `command`.

Por lo que respecta a la variable `playa`, así como al resto, las declaramos utilizando la clase `IntVar`, puesto que nuestra intención es almacenar en ellas valores enteros:

```python
playa = IntVar()
montana = IntVar()
turismo_rural = IntVar()
```

Por otro lado, mostraremos las opciones seleccionadas por el usuario empleando una etiqueta para ello, de ahí que figure el siguiente bloque de código al final del programa:

```python
texto_final = Label(frame)
texto_final.pack()
```

Finalmente, la función que gestiona el comportamiento de las casillas de verificación simplemente se ocupa de establecer el texto de la variable `texto_final` según una serie de bloques condicionales:

```python
def opciones_viaje():
    opcion_escogida = ""
    if playa.get() == 1:
        opcion_escogida += " playa"
    if montana.get() == 1:
        opcion_escogida += " montaña"
    if turismo_rural.get() == 1:
        opcion_escogida += " turismo rural"
    texto_final.config(text=opcion_escogida)
```

{{< figure src="/courses/python-basic/img/pb51-img01.png" title="Primer contacto con la clase `Checkbutton`." numbered="true" >}}

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/51/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
