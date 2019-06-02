---
title: 60. Práctica guiada II
linktitle: 60. Práctica II
toc: true
type: docs
date: "2019-06-02T00:00:01+01:00"
lastmod: "2019-06-02T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 60

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 60
---

## Vídeo

{{< youtube o8E869dmK3U >}}

## Notas personales

En esta lección, comenzaremos a esbozar la interfaz gráfica de nuestra aplicación *CRUD*. Para ello, empezamos tecleando:

```python
from tkinter import Tk

# Raíz de la aplicación
root = Tk()
root.title("Aplicación CRUD")
root.iconbitmap("icon.ico")

# Ejecución de la aplicación
root.mainloop()
```

A continuación, generamos la barra de menú superior:

```python
# Menú superior de la aplicación
barra_menu = Menu(root)
root.config(menu=barra_menu)

bbdd_menu = Menu(barra_menu, tearoff=0)
bbdd_menu.add_command(label="Conectar")
bbdd_menu.add_separator()
bbdd_menu.add_command(label="Salir")

borrar_menu = Menu(barra_menu, tearoff=0)
borrar_menu.add_command(label="Borrar campos")

crud_menu = Menu(barra_menu, tearoff=0)
crud_menu.add_command(label="Crear")
crud_menu.add_command(label="Leer")
crud_menu.add_command(label="Actualizar")
crud_menu.add_command(label="Borrar")

help_menu = Menu(barra_menu, tearoff=0)
help_menu.add_command(label="Licencia")
help_menu.add_separator()
help_menu.add_command(label="Acerca de...")

barra_menu.add_cascade(label="BBDD", menu=bbdd_menu)
barra_menu.add_cascade(label="Borrar", menu=borrar_menu)
barra_menu.add_cascade(label="CRUD", menu=crud_menu)
barra_menu.add_cascade(label="Ayuda", menu=help_menu)
```

Por lo que respecta al cuerpo de la aplicación, lo dividiremos en dos *frames*: uno superior para organizar los campos de introducción de datos y otro inferior para distribuir los cuatro botones que nos permitirán llevar a cabo acciones de tipo *CRUD*.

Así pues, si, por ejemplo, optamos por construir los diferentes campos de entrada que poseerá la aplicación, el bloque de código a escribir será:

```python
# Frame superior
campos_frame = Frame(root)
campos_frame.pack()

id_entry = Entry(campos_frame)
id_entry.grid(row=0, column=1, padx=2, pady=2)

name_entry = Entry(campos_frame)
name_entry.grid(row=1, column=1, padx=2, pady=2)

lastname_entry = Entry(campos_frame)
lastname_entry.grid(row=2, column=1, padx=2, pady=2)

address_entry = Entry(campos_frame)
address_entry.grid(row=3, column=1, padx=2, pady=2)

password_entry = Entry(campos_frame)
password_entry.grid(row=4, column=1, padx=2, pady=2)
password_entry.config(show="*")

comment_text = Text(campos_frame, width=15, height=5)
comment_text.grid(row=5, column=1, padx=2, pady=2)
comment_text_scrollvert = Scrollbar(campos_frame, command=comment_text.yview)
comment_text_scrollvert.grid(row=5, column=2, sticky="nsew")
comment_text.config(yscrollcommand=comment_text_scrollvert)
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/60/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
