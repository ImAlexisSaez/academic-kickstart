---
title: 46. Interfaces gráficas V
linktitle: 46. Interfaces V
toc: true
type: docs
date: "2019-05-23T00:00:01+01:00"
lastmod: "2019-05-23T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 46

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 46
---

## Vídeo

{{< youtube nZF9SwhmPRo >}}

## Notas personales

En esta lección, presentaremos dos *widgets* nuevos: `Text` y `Button`. El primero de ellos nos permite introducir un texto de extensión considerable en un cuadro, mientras que el segundo simplemente se trata de la clase asociada a los botones que habitualmente pulsamos en cualquier aplicación.

Retomemos el último ejemplo de la lección anterior:

```python
from tkinter import Tk, Frame, Entry, Label

root = Tk()

root.title("Probando el widget Entry")
root.resizable(width=True, height=True)
root.iconbitmap("icon.ico")
root.config(bg="lightblue")

frame = Frame(root, width=450, height=300)
frame.pack()

nombre_label = Label(frame, text="Nombre:")
nombre_label.grid(row=0, column=0, sticky="e", padx=2, pady=2)

cuadro_nombre = Entry(frame)
cuadro_nombre.grid(row=0, column=1, padx=2, pady=2)

apellido_label = Label(frame, text="Apellido:")
apellido_label.grid(row=1, column=0, sticky="e", padx=2, pady=2)

apellido_texto = Entry(frame)
apellido_texto.grid(row=1, column=1, padx=2, pady=2)

direccion_label = Label(frame, text="Dirección:")
direccion_label.grid(row=2, column=0, sticky="e", padx=2, pady=2)

direccion_texto = Entry(frame)
direccion_texto.grid(row=2, column=1, padx=2, pady=2)

tfno_label = Label(frame, text="Teléfono (fijo):")
tfno_label.grid(row=3, column=0, sticky="e", padx=2, pady=2)

tfno_texto = Entry(frame)
tfno_texto.grid(row=3, column=1, padx=2, pady=2)

movil_label = Label(frame, text="Teléfono (móvil):")
movil_label.grid(row=4, column=0, sticky="e")

movil_texto = Entry(frame)
movil_texto.grid(row=4, column=1)

pass_label = Label(frame, text="Constraseña:")
pass_label.grid(row=5, column=0, sticky="e")

pass_texto = Entry(frame)
pass_texto.grid(row=5, column=1)
pass_texto.config(show="*")

root.mainloop()
```

Añadamos, a continuación del campo declarado para la introducción de la contraseña, uno dedicado a la biografía de la persona que está rellenando el formulario. Ello nos permitirá hacer uso de la clase `Text`, que habremos de importar al inicio del código. Así, si escribimos:

```python
bio_label = Label(frame, text="Biografía:")
bio_label.grid(row=6, column=0, sticky="e", padx=2, pady=2)

bio_texto = Text(frame, width=15, height=5)
bio_texto.grid(row=6, column=1, padx=2, pady=2)

scroll_vert = Scrollbar(frame, command=bio_texto.yview)
scroll_vert.grid(row=6, column=2, sticky="nsew")
bio_texto.config(yscrollcommand=scroll_vert.set)
```

{{< figure src="/courses/python-basic/img/pb46-img01.png" title="Primer contacto con la clase `Text`." numbered="true" >}}

*Notas*:

- Conviene que declaremos unas longitudes adecuadas mediante los parámetros `width` y `height`, ya que las asignadas por defecto son ciertamente elevadas.
- El *widget* `Text` automáticamente permite la posibilidad de *scroll*, aunque si deseamos que aparezca una barra de desplazamiento lateral, hemos de indicarlo. Para ello, se requiere la construcción de un objeto de la clase `Scrollbar` (que hemos de importar de la librería `tkinter`) y asociarlo al cuadro de texto generado. La correspondiente instrucción que se ocupa de tal tarea en el bloque de código anterior es: 

```python
scroll_vert = Scrollbar(frame, command=bio_texto.yview)
```

- Acto seguido, mediante el método `grid()`, y teniendo cuidado con el valor correspondiente para el parámetro `column`, terminamos haciendo que aparezca en la ventana de la aplicación. Para que se adapte al tamaño del cuadro de texto asociado, una posible estrategia es incluir `sticky="nsew"` en la declaración del *scroll*. 
- Por otro lado, si queremos que se posicione la barra de desplazamiento al nivel del texto que estamos introduciendo, incluiremos la instrucción `bio_texto.config(yscrollcommand=scroll_vert.set)` tras la declaración de la variable `scroll_vert`.

Pasemos ahora a añadir un botón a nuestra interfaz gráfica, para lo cual haremos uso de la clase `Button`. Posicionemos uno en la raíz (`root`) de la ventana de la aplicación:

```python
boton_envio = Button(root, text="Enviar")
boton_envio.pack()
```

{{< figure src="/courses/python-basic/img/pb46-img02.png" title="Primer contacto con la clase `Button`." numbered="true" >}}

A continuación, veamos cómo añadir cierta funcionalidad al botón generado. Para ello, incluimos en su declaración el parámetro `command=codigo_boton`, 

```python
boton_envio = Button(root, text="Enviar", command=codigo_boton)
```

donde `codigo_boton` será una función que contendrá el código con las acciones que deseemos se lleven a cabo cuando el usuario pulse sobre el botón.

Por ejemplo, aunque no sea la característica habitual de este tipo de botones, hagamos que cuando el usuario pulse sobre el mencionado botón, se escriba nuestro nombre automáticamente en el cuadro de texto correspondiente. Así, tecleamos:

```python
def codigo_boton():
    mi_nombre.set("Alexis")


root = Tk()

mi_nombre = StringVar()
```

La instrucción `mi_nombre = StringVar()` únicamente le indica a *Python* que la variable `mi_nombre` es una cadena de caracteres. Como viene siendo habitual, habremos de importar la correspondiente clase al comienzo del código (o, directamente, utilizar el esquema `from ... import *`). Ahora, modificamos la declaración del cuadro de texto asociado al nombre del usuario introduciendo el parámetro `textvariable`:

```python
cuadro_nombre = Entry(frame, textvariable=mi_nombre)
```

*Nota técnica*: no podemos utilizar `StringVar()` antes de definir la raíz (`root`) de la aplicación.

{{< figure src="/courses/python-basic/img/pb46-img03.png" title="¡El botón está vivo!¡Vivo!" numbered="true" >}}

Si la función `set()` nos permite declarar el valor de un cuadro de texto, para obtener la información que el usuario introduzca en uno, utilizaremos, en próximas lecciones, el método `get()`.

Finalmente, comparto el código completo de esta última aplicación generada, para tener acceso así a una visión global de la misma:

```python
from tkinter import Tk, Frame, Button, Entry, Label, Scrollbar, StringVar, Text


def codigo_boton():
    mi_nombre.set("Alexis")


root = Tk()

mi_nombre = StringVar()

root.title("Probando los widgets Text y Button")
root.resizable(width=True, height=True)
root.iconbitmap("icon.ico")
root.config(bg="lightblue")

frame = Frame(root, width=450, height=300)
frame.pack()

nombre_label = Label(frame, text="Nombre:")
nombre_label.grid(row=0, column=0, sticky="e", padx=2, pady=2)

cuadro_nombre = Entry(frame, textvariable=mi_nombre)
cuadro_nombre.grid(row=0, column=1, padx=2, pady=2)

apellido_label = Label(frame, text="Apellido:")
apellido_label.grid(row=1, column=0, sticky="e", padx=2, pady=2)

apellido_texto = Entry(frame)
apellido_texto.grid(row=1, column=1, padx=2, pady=2)

direccion_label = Label(frame, text="Dirección:")
direccion_label.grid(row=2, column=0, sticky="e", padx=2, pady=2)

direccion_texto = Entry(frame)
direccion_texto.grid(row=2, column=1, padx=2, pady=2)

tfno_label = Label(frame, text="Teléfono (fijo):")
tfno_label.grid(row=3, column=0, sticky="e", padx=2, pady=2)

tfno_texto = Entry(frame)
tfno_texto.grid(row=3, column=1, padx=2, pady=2)

movil_label = Label(frame, text="Teléfono (móvil):")
movil_label.grid(row=4, column=0, sticky="e", padx=2, pady=2)

movil_texto = Entry(frame)
movil_texto.grid(row=4, column=1, padx=2, pady=2)

pass_label = Label(frame, text="Constraseña:")
pass_label.grid(row=5, column=0, sticky="e", padx=2, pady=2)

pass_texto = Entry(frame)
pass_texto.grid(row=5, column=1, padx=2, pady=2)
pass_texto.config(show="*")

bio_label = Label(frame, text="Biografía:")
bio_label.grid(row=6, column=0, sticky="e", padx=2, pady=2)

bio_texto = Text(frame, width=15, height=5)
bio_texto.grid(row=6, column=1, padx=2, pady=2)

scroll_vert = Scrollbar(frame, command=bio_texto.yview)
scroll_vert.grid(row=6, column=2, sticky="nsew")
bio_texto.config(yscrollcommand=scroll_vert.set)

boton_envio = Button(root, text="Enviar", command=codigo_boton)
boton_envio.pack()

root.mainloop()
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/46/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
