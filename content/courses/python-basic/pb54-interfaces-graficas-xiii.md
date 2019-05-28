---
title: 54. Interfaces gráficas XIII
linktitle: 54. Interfaces XIII
toc: true
type: docs
date: "2019-05-28T00:00:02+01:00"
lastmod: "2019-05-28T00:00:02+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 54

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 54
---

## Vídeo

{{< youtube TmQZBzwIMGk >}}

## Notas personales

En esta lección, construiremos la típica ventana emergente que nos permite abrir un archivo en una aplicación. Para empezar, recuperemos el código fuente generado en las últimas lecciones:

```python
from tkinter import Menu, messagebox, Tk


def info_adicional():
    messagebox.showinfo(title="Acerca de...",
                        message="Aplicación creada por Alexis Sáez.")


def aviso_licencia():
    messagebox.showwarning(title="Licencia",
                           message="Producto bajo licencia GNU.")


def salir_aplicacion():
    respuesta = messagebox.askquestion(
        title="Salir", message="¿Desear salir de la aplicación?")
    if respuesta == "yes":
        raiz.destroy()


def cerrar_documento():
    messagebox.askretrycancel(
        title="Reintentar",
        message="No es posible cerrar. Documento bloqueado.")


raiz = Tk()
raiz.title("Menús")
raiz.iconbitmap("icon.ico")

barra_menu = Menu(raiz)

raiz.config(menu=barra_menu, width=300, height=300)

archivo_menu = Menu(barra_menu, tearoff=0)
archivo_menu.add_command(label="Nuevo")
archivo_menu.add_command(label="Abrir")
archivo_menu.add_separator()
archivo_menu.add_command(label="Guardar")
archivo_menu.add_command(label="Guardar como...")
archivo_menu.add_separator()
archivo_menu.add_command(label="Cerrar", command=cerrar_documento)
archivo_menu.add_command(label="Salir", command=salir_aplicacion)

edicion_menu = Menu(barra_menu, tearoff=0)
edicion_menu.add_command(label="Copiar")
edicion_menu.add_command(label="Cortar")
edicion_menu.add_command(label="Pegar")

herramientas_menu = Menu(barra_menu, tearoff=0)

ayuda_menu = Menu(barra_menu, tearoff=0)
ayuda_menu.add_command(label="Licencia", command=aviso_licencia)
ayuda_menu.add_separator()
ayuda_menu.add_command(label="Acerca de...", command=info_adicional)

barra_menu.add_cascade(label="Archivo", menu=archivo_menu)
barra_menu.add_cascade(label="Edición", menu=edicion_menu)
barra_menu.add_cascade(label="Herramientas", menu=herramientas_menu)
barra_menu.add_cascade(label="Ayuda", menu=ayuda_menu)

raiz.mainloop()
```

A continuación, importamos el módulo `filedialog`, de la librería `tkinter`, y construimos la siguiente función:

```python
def abrir_archivo():
    fichero = filedialog.askopenfilename(title="Abrir archivo")
    print(fichero)
```

En la variable `fichero`, almacenamos la ruta al archivo que seleccionemos a través de la ventana emergente, como bien podremos comprobar en la consola de *Python* gracias a la función `print()` que hemos incorporado en el interior de `abrir_archivo()`. Después, acudimos al elemento del menú *Archivo* correspondiente y modificamos la línea como sigue:

```python
archivo_menu.add_command(label="Abrir", command=abrir_archivo)
```

A la vista del resultado, es posible que nos interese modificar la ubicación de la ruta desde la que un usuario ha de comenzar la búsqueda de un archivo. Para ello, modificamos la función `abrir_archivo()` como sigue:

```python
def abrir_archivo():
    fichero = filedialog.askopenfilename(title="Abrir archivo",
                                         initialdir="/")
    print(fichero)
```

y, de esta manera, ahora la ventana emergente nos muestra los directorios ubicados en la raíz de nuestro disco duro.

Además, podemos restringir el tipo de archivo que deseamos un usuario examine (por ejemplo, restringir la búsqueda a imágenes o documentos) mediante el parámetro `filetypes`. Así, si modificamos la función `abrir_archivo()` como sigue:

```python
def abrir_archivo():
    fichero = filedialog.askopenfilename(title="Abrir archivo",
                                         initialdir="/",
                                         filetypes=(("Ficheros de Excel",
                                                     "*.xlsx"),
                                                    ("Ficheros de texto",
                                                     "*.txt")))
    print(fichero)
```

ahora la ventana emergente nos restringe el tipo de fichero que podemos seleccionar y, además, nos permite filtrar por dos opciones diferentes (de Excel o de texto), según sus correspondientes extensiones.

Para comodidad del usuario, conviene siempre incluir una opción para abrir cualquier tipo de archivo, independientemente de su extensión:

```python
def abrir_archivo():
    fichero = filedialog.askopenfilename(
        title="Abrir archivo",
        initialdir="/",
        filetypes=(("Ficheros de Excel", "*.xlsx"),
                   ("Ficheros de texto", "*.txt"),
                   ("Todos los archivos", "*.*")))
    print(fichero)
```

Finalmente, como ya viene siendo habitual en esta serie de lecciones dedicadas a las interfaces gráficas, comparto el código fuente completo de la aplicación generada, para tener así una visión global de la misma:

```python
from tkinter import filedialog, Menu, messagebox, Tk


def info_adicional():
    messagebox.showinfo(title="Acerca de...",
                        message="Aplicación creada por Alexis Sáez.")


def aviso_licencia():
    messagebox.showwarning(title="Licencia",
                           message="Producto bajo licencia GNU.")


def salir_aplicacion():
    respuesta = messagebox.askquestion(
        title="Salir", message="¿Desear salir de la aplicación?")
    if respuesta == "yes":
        raiz.destroy()


def cerrar_documento():
    messagebox.askretrycancel(
        title="Reintentar",
        message="No es posible cerrar. Documento bloqueado.")


def abrir_archivo():
    fichero = filedialog.askopenfilename(
        title="Abrir archivo",
        initialdir="/",
        filetypes=(("Ficheros de Excel", "*.xlsx"),
                   ("Ficheros de texto", "*.txt"),
                   ("Todos los archivos", "*.*")))
    print(fichero)


raiz = Tk()
raiz.title("Menús")
raiz.iconbitmap("icon.ico")

barra_menu = Menu(raiz)

raiz.config(menu=barra_menu, width=300, height=300)

archivo_menu = Menu(barra_menu, tearoff=0)
archivo_menu.add_command(label="Nuevo")
archivo_menu.add_command(label="Abrir", command=abrir_archivo)
archivo_menu.add_separator()
archivo_menu.add_command(label="Guardar")
archivo_menu.add_command(label="Guardar como...")
archivo_menu.add_separator()
archivo_menu.add_command(label="Cerrar", command=cerrar_documento)
archivo_menu.add_command(label="Salir", command=salir_aplicacion)

edicion_menu = Menu(barra_menu, tearoff=0)
edicion_menu.add_command(label="Copiar")
edicion_menu.add_command(label="Cortar")
edicion_menu.add_command(label="Pegar")

herramientas_menu = Menu(barra_menu, tearoff=0)

ayuda_menu = Menu(barra_menu, tearoff=0)
ayuda_menu.add_command(label="Licencia", command=aviso_licencia)
ayuda_menu.add_separator()
ayuda_menu.add_command(label="Acerca de...", command=info_adicional)

barra_menu.add_cascade(label="Archivo", menu=archivo_menu)
barra_menu.add_cascade(label="Edición", menu=edicion_menu)
barra_menu.add_cascade(label="Herramientas", menu=herramientas_menu)
barra_menu.add_cascade(label="Ayuda", menu=ayuda_menu)

raiz.mainloop()
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/54/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
