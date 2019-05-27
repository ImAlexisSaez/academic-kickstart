---
title: 52. Interfaces gráficas XI
linktitle: 52. Interfaces XI
toc: true
type: docs
date: "2019-05-27T00:00:01+01:00"
lastmod: "2019-05-27T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 52

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 52
---

## Vídeo

{{< youtube Dv1ALaWwScI >}}

## Notas personales

En esta lección, abordaremos el estudio del *widget* `Menu`, que nos permitirá la posibilidad de crear barras de menús.

Comencemos utilizando el siguiente esqueleto de aplicación:

```python
from tkinter import Tk

raiz = Tk()
raiz.title("Menús")
raiz.iconbitmap("icon.ico")

raiz.mainloop()
```

A continuación, generamos una variable, `barra_menu`, que será la encargada de almacenar el menú:

```python
barra_menu = Menu(raiz)
```

y configuramos el valor del parámetro `menu` de la *raíz* para que figure en nuestra aplicación:

```python
raiz.config(menu=barra_menu)
```

Acto seguido, establecemos los elementos que conformarán nuestro menú. Por ejemplo, para crear uno denominado *Archivo*, generamos la variable `archivo_menu`, indicándole que pertenece a la barra de menús `barra_menu`.

```python
archivo_menu = Menu(barra_menu)
```

No obstante, si ejecutamos el código, todavía no aparece barra de menús alguna. Añadamos el texto correspondiente a cada elemento. Así,

```python
barra_menu.add_cascade(label="Archivo", menu=archivo_menu)
```

Ahora, ya únicamente nos resta la tarea de añadir elementos de submenú. Para ello, tras la línea de declaración del elemento `archivo_menu`, tecleamos:

```python
archivo_menu.add_command(label="Nuevo")
archivo_menu.add_command(label="Abrir")
archivo_menu.add_command(label="Guardar")
archivo_menu.add_command(label="Guardar como...")
archivo_menu.add_command(label="Cerrar")
archivo_menu.add_command(label="Salir")
```

Aparece una barra separadora, que identificamos por los símbolos `- - - -`, al pulsar sobre cualquier elemento de la barra de menús. Para suprimirla, modificamos como sigue la línea de declaración de la variable `archivo_menu`:

```python
archivo_menu = Menu(barra_menu, tearoff=0)
```

No obstante, aunque la mencionada barra separada no nos interesaba, sí que podemos desear diferenciar, de alguna manera, los diversos elementos de un submenú, para que así queden agrupados por cierto criterio. Con tal objetivo, donde nos convenga, introducimos la instrucción

```python
archivo_menu.add_separator()
```

Para acabar, comparto el código completo de la aplicación, para obtener así una visión global del funcionamiento de la clase `Menu`.

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

{{< figure src="/courses/python-basic/img/pb52-img01.png" title="Primer contacto con la clase `Menu`." numbered="true" >}}

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/52/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
