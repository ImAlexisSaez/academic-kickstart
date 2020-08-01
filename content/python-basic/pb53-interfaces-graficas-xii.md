---
title: 53. Interfaces gráficas XII
linktitle: 53. Interfaces XII
toc: true
type: book
date: "2019-05-28T00:00:01+01:00"
lastmod: "2019-05-28T00:00:01+01:00"
draft: false
weight: 53
---

## Vídeo

{{< youtube xUGUglpaTJc >}}

## Notas personales

En esta lección, estudiaremos cómo construir ventanas emergentes, que son ventanas modales para informar, avisar o permitir realizar ciertas tareas al usuario.

Para comenzar, recuperemos el código fuente generado en la lección anterior:

```python
from tkinter import Menu, Tk

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
archivo_menu.add_command(label="Cerrar")
archivo_menu.add_command(label="Salir")

edicion_menu = Menu(barra_menu, tearoff=0)
edicion_menu.add_command(label="Copiar")
edicion_menu.add_command(label="Cortar")
edicion_menu.add_command(label="Pegar")

herramientas_menu = Menu(barra_menu, tearoff=0)

ayuda_menu = Menu(barra_menu, tearoff=0)
ayuda_menu.add_command(label="Licencia")
ayuda_menu.add_separator()
ayuda_menu.add_command(label="Acerca de...")

barra_menu.add_cascade(label="Archivo", menu=archivo_menu)
barra_menu.add_cascade(label="Edición", menu=edicion_menu)
barra_menu.add_cascade(label="Herramientas", menu=herramientas_menu)
barra_menu.add_cascade(label="Ayuda", menu=ayuda_menu)

raiz.mainloop()
```

A continuación, nuestro objetivo será construir una ventana emergente que aparezca cuando el usuario pulse sobre la opción *Acerca de...*, ubicada en el menú *Ayuda*. Para ello, empecemos creando una función que será la responsable de generar la mencionada ventana emergente:

```python
def info_adicional():
    messagebox.showinfo(title="Acerca de...",
                        message="Aplicación creada por Alexis Sáez.")
```

*Notas*:

- Hemos de importar el módulo `messagebox` al principio de nuestro código.
- El parámetro `title` gestiona el texto que aparecerá en la barra que figura en la parte superior de la ventana emergente.
- El parámetro `text` declara el texto que se ubicará en el cuerpo de la ventana emergente.

Acto seguido, modificamos la declaración del submenú *Acerca de...* como sigue:

```python
ayuda_menu.add_command(label="Acerca de...", command=info_adicional)
```

{{< figure src="/courses/python-basic/img/pb53-img01.png" title="Primera ventana emergente." numbered="true" >}}

Estas ventanas emergentes admiten enormes posibilidades de configuración y podemos adaptarlas según nuestra intención sea informar al usuario de algún detalle concreto (como el ejemplo que se muestra en la imagen que figura arriba), avisarle de algún error, etc. Los símbolos y la disposición de los diferentes botones asociados variarían en función de nuestro objetivo.

Por ejemplo, generemos una ventana emergente que nos avise del estado de la licencia de nuestra aplicación. Para ello, creamos la siguiente función:

```python
def aviso_licencia():
    messagebox.showwarning(title="Licencia",
                           message="Producto bajo licencia GNU.")
```

y modificamos la correspondiente opción del menú *Ayuda*:

```python
ayuda_menu.add_command(label="Licencia", command=aviso_licencia)
```

{{< figure src="/courses/python-basic/img/pb53-img02.png" title="Ventana emergente de aviso." numbered="true" >}}

Acto seguido, veamos un nuevo tipo de ventana emergente, que asociaremos al submenú *Salir* y que nos pedirá confirmación antes de proceder a cerrar la aplicación. Con tal objetivo en mente, empecemos construyendo la función:

```python
def salir_aplicacion():
    messagebox.askquestion(title="Salir",
                           message="¿Desear salir de la aplicación?")
```

para luego modificar la opción del menú *Archivo* asociada:

```python
archivo_menu.add_command(label="Salir", command=salir_aplicacion)
```

{{< figure src="/courses/python-basic/img/pb53-img03.png" title="Ventana emergente con pregunta." numbered="true" >}}

Ahora, si pulsamos sobre el botón *No*, volvemos a la aplicación, como cabría esperar. No obstante, al pulsar sobre el botón *Sí* debería salir de la aplicación y no sucede tal acción, puesto que hemos de programar todavía dicho comportamiento.

La función `askquestion()` devuelve una cadena de texto en función del botón pulsado, `"yes"` o `"no"`, por lo que basta modificar la función `salir_aplicacion()` como sigue:

```python
def salir_aplicacion():
    respuesta = messagebox.askquestion(
        title="Salir", message="¿Desear salir de la aplicación?")
    if respuesta == "yes":
        raiz.destroy()
```

La función `destroy()` posee un nombre lo suficientemente explicativo para que intuyamos cómo afecta a la *raíz* de la aplicación.

*Nota*: con la función `askokcancel()` tenemos una variante de la anterior ventana emergente, cuyos botones son del tipo *Aceptar* y *Cancelar*.

A continuación, veamos una ventana emergente de tipo ''reintentar'', asociada a la opción *Cerrar* del menú *Archivo*. Para ello, construimos la siguiente función:

```python
def cerrar_documento():
    messagebox.askretrycancel(
        title="Reintentar",
        message="No es posible cerrar. Documento bloqueado.")
```

y modificamos el correspondiente elemento del menú *Archivo*:

```python
archivo_menu.add_command(label="Cerrar", command=cerrar_documento)
```

{{< figure src="/courses/python-basic/img/pb53-img04.png" title="Ventana emergente para reintentar una acción." numbered="true" >}}

Finalmente, como viene siendo habitual en este subapartado del curso dedicado a las interfaces gráficas, comparto el código completo de la aplicación generada para así ofrecer una visión global de la misma.

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

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/53/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
