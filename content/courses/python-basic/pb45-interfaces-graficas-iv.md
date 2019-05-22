---
title: 45. Interfaces gráficas IV
linktitle: 45. Interfaces IV
toc: true
type: docs
date: "2019-05-22T00:00:01+01:00"
lastmod: "2019-05-22T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 45

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 45
---

## Vídeo

{{< youtube YRs8j0QGEn0 >}}

## Notas personales

En esta lección, tras haber estudiado en la anterior el *widget* `Label`, abordaremos el uso del *widget* `Entry`, cuyo funcionamento es realmente similar a nivel de sintaxis. Este último habilita, en nuestras ventanas, la posibilidad de introducir un cuadro de texto, desde el cual el usuario puede suministrar cierta información.

```python
from tkinter import Tk, Entry

root = Tk()

root.title("Probando el widget Entry")
root.resizable(width=True, height=True)
root.iconbitmap("icon.ico")
root.config(bg="lightblue")

cuadro_texto = Entry(root)
cuadro_texto.pack()

root.mainloop()
```

{{< figure src="/courses/python-basic/img/pb45-img01.png" title="Primer contacto con la clase `Entry`." numbered="true" >}}

A partir de ahora, podemos reutilizar los conceptos y propiedades aprendidas hasta el momento:

```python
from tkinter import Tk, Frame, Entry

root = Tk()

root.title("Probando el widget Entry")
root.resizable(width=True, height=True)
root.iconbitmap("icon.ico")
root.config(bg="lightblue")

frame = Frame(root, width=450, height=300)
frame.pack()

cuadro_texto = Entry(frame)
cuadro_texto.place(x=100, y=100)

root.mainloop()
```

{{< figure src="/courses/python-basic/img/pb45-img02.png" title="Insertando el *widget* en un *frame*." numbered="true" >}}

Empecemos a combinar *widgets* añadiendo al lado del cuadro de texto una etiqueta que rece ''Nombre:'', como si quisiéramos elaborar un formulario de registro de datos personales. Utilizando la función `place()` es posible, pero resulta muy complicado cuadrar adecuadamente todos los espacios de la ventana de la aplicación.

Existen dos alternativas a la hora de abordar esta situación:

- `pack()`, aunque ya sabemos que después se ajustará la ventana al tamaño de sus elementos internos, ignorando pues las dimensiones que establecimos en su declaración.
- `grid()`, construye una tabla dentro de la interfaz gráfica con tantas filas y columnas como nosotros queramos. Tras ello, podemos ubicar en la casilla que deseemos el elemento que nos interese.

Estudiemos el uso de esta última función mencionada:

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
nombre_label.grid(row=0, column=0)

cuadro_nombre = Entry(frame)
cuadro_nombre.grid(row=0, column=1)

apellido_label = Label(frame, text="Apellido:")
apellido_label.grid(row=1, column=0)

apellido_texto = Entry(frame)
apellido_texto.grid(row=1, column=1)

direccion_label = Label(frame, text="Dirección:")
direccion_label.grid(row=2, column=0)

direccion_texto = Entry(frame)
direccion_texto.grid(row=2, column=1)

root.mainloop()
```

{{< figure src="/courses/python-basic/img/pb45-img03.png" title="Probando el método `grid()`." numbered="true" >}}

Por defecto, los elementos se alinean centrados dentro de su correspondiente casilla de la rejilla. Con el parámetro `sticky` y los cuatro puntos cardinales (`n`, `e`, `s`, `w` y sus combinaciones por parejas) podemos modificar dicho comportamiento.

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
nombre_label.grid(row=0, column=0, sticky="e")

cuadro_nombre = Entry(frame)
cuadro_nombre.grid(row=0, column=1)

apellido_label = Label(frame, text="Apellido:")
apellido_label.grid(row=1, column=0, sticky="e")

apellido_texto = Entry(frame)
apellido_texto.grid(row=1, column=1)

direccion_label = Label(frame, text="Dirección:")
direccion_label.grid(row=2, column=0, sticky="e")

direccion_texto = Entry(frame)
direccion_texto.grid(row=2, column=1)

tfno_label = Label(frame, text="Teléfono (fijo):")
tfno_label.grid(row=3, column=0, sticky="e")

tfno_texto = Entry(frame)
tfno_texto.grid(row=3, column=1)

movil_label = Label(frame, text="Teléfono (móvil):")
movil_label.grid(row=4, column=0, sticky="e")

movil_texto = Entry(frame)
movil_texto.grid(row=4, column=1)

root.mainloop()
```

{{< figure src="/courses/python-basic/img/pb45-img04.png" title="El parámetro `sticky` en acción." numbered="true" >}}

Para evitar que los elementos aparezcan tan juntos, los parámetros `padx` y `pady` pueden resultarnos de utilidad, ya que nos permiten configurar la distancia del elemento al límite del contenedor donde se haya ubicado.

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

root.mainloop()
```

{{< figure src="/courses/python-basic/img/pb45-img05.png" title="Separando elementos con `padx` y `pady`." numbered="true" >}}

Ahora, ya únicamente nos resta experimentar con la configuración de los distintos *widgets* estudiados, empleando para ello principalmente la función `config()` asociada a cada *widget*.

Finalmente, veamos cómo añadir un cuadro de texto que nos permita introducir contraseñas. Buscamos que al suministrar la información, esta aparezca ''oculta'' tras asteriscos. El parámetro `show` de la función `config()` cumple dicho cometido:

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

{{< figure src="/courses/python-basic/img/pb45-img06.png" title="Una contraseña más segura con `show`." numbered="true" >}}

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/45/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
