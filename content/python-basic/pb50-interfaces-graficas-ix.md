---
title: 50. Interfaces gráficas IX
linktitle: 50. Interfaces IX
toc: true
type: book
date: "2019-05-25T00:00:02+01:00"
lastmod: "2019-05-25T00:00:02+01:00"
draft: false
weight: 50
---

## Vídeo

{{< youtube YfYUOUGMaXU >}}

## Notas personales

Partamos, en esta lección, del siguiente código fuente, que incluye, además de la función para sumar, las correspondientes a las operaciones resta, multiplicación y división:

```python
from tkinter import Button, Entry, Frame, StringVar, Tk

# Raíz
raiz = Tk()
raiz.title("Calculadora")
raiz.iconbitmap("icon.ico")

# Frame
frame = Frame(raiz)
frame.pack()

# Variables
numero_pantalla = StringVar()
operacion = ""
resultado = 0
reset_pantalla = False

# Pantalla
pantalla = Entry(frame, textvariable=numero_pantalla)
pantalla.grid(row=1, column=1, padx=10, pady=10, columnspan=4)
pantalla.config(background="black", fg="#03f943", justify="right")


# Pulsaciones teclado
def numero_pulsado(num):
    global operacion, reset_pantalla
    if reset_pantalla:
        numero_pantalla.set(num)
        reset_pantalla = False
    else:
        numero_pantalla.set(numero_pantalla.get() + num)


# Función suma
def suma(num):
    global operacion, reset_pantalla, resultado
    operacion = "suma"
    resultado += int(num)
    reset_pantalla = True
    numero_pantalla.set(resultado)


# Función resta
num1 = 0
contador_resta = 0


def resta(num):
    global contador_resta, num1, operacion, reset_pantalla, resultado
    if contador_resta == 0:
        num1 = int(num)
        resultado = num1
    else:
        if contador_resta == 1:
            resultado = num1 - int(num)
        else:
            resultado = int(resultado) - int(num)
        numero_pantalla.set(resultado)
        resultado = numero_pantalla.get()
    contador_resta = contador_resta + 1
    operacion = "resta"
    reset_pantalla = True


# Función multiplicación
contador_multi = 0


def multiplica(num):
    global contador_multi, num1, operacion, reset_pantalla, resultado
    if contador_multi == 0:
        num1 = int(num)
        resultado = num1
    else:
        if contador_multi == 1:
            resultado = num1 * int(num)
        else:
            resultado = int(resultado) * int(num)
        numero_pantalla.set(resultado)
        resultado = numero_pantalla.get()
    contador_multi = contador_multi + 1
    operacion = "multiplicacion"
    reset_pantalla = True


# Función división
contador_divi = 0


def divide(num):
    global contador_divi, num1, operacion, reset_pantalla, resultado
    if contador_divi == 0:
        num1 = float(num)
        resultado = num1
    else:
        if contador_resta == 1:
            resultado = num1 / float(num)
        else:
            resultado = float(resultado) / float(num)
        numero_pantalla.set(resultado)
        resultado = numero_pantalla.get()
    contador_divi = contador_divi + 1
    operacion = "division"
    reset_pantalla = True


# Función el_resultado (para el botón igual)
def el_resultado():
    global contador_divi, contador_multi, contador_resta, operacion, resultado
    if operacion == "suma":
        numero_pantalla.set(resultado + int(numero_pantalla.get()))
        resultado = 0
    elif operacion == "resta":
        numero_pantalla.set(int(resultado) - int(numero_pantalla.get()))
        resultado = 0
        contador_resta = 0
    elif operacion == "multiplicacion":
        numero_pantalla.set(int(resultado) * int(numero_pantalla.get()))
        resultado = 0
        contador_multi = 0
    elif operacion == "division":
        numero_pantalla.set(int(resultado) / int(numero_pantalla.get()))
        resultado = 0
        contador_divi = 0


# Fila 1 de botones
boton7 = Button(frame, text="7", width=3, command=lambda: numero_pulsado("7"))
boton7.grid(row=2, column=1)
boton8 = Button(frame, text="8", width=3, command=lambda: numero_pulsado("8"))
boton8.grid(row=2, column=2)
boton9 = Button(frame, text="9", width=3, command=lambda: numero_pulsado("9"))
boton9.grid(row=2, column=3)
boton_div = Button(frame,
                   text="/",
                   width=3,
                   command=lambda: divide(numero_pantalla.get()))
boton_div.grid(row=2, column=4)

# Fila 2 de botones
boton4 = Button(frame, text="4", width=3, command=lambda: numero_pulsado("4"))
boton4.grid(row=3, column=1)
boton5 = Button(frame, text="5", width=3, command=lambda: numero_pulsado("5"))
boton5.grid(row=3, column=2)
boton6 = Button(frame, text="6", width=3, command=lambda: numero_pulsado("6"))
boton6.grid(row=3, column=3)
boton_mult = Button(frame,
                    text="*",
                    width=3,
                    command=lambda: multiplica(numero_pantalla.get()))
boton_mult.grid(row=3, column=4)

# Fila 3 de botones
boton1 = Button(frame, text="1", width=3, command=lambda: numero_pulsado("1"))
boton1.grid(row=4, column=1)
boton2 = Button(frame, text="2", width=3, command=lambda: numero_pulsado("2"))
boton2.grid(row=4, column=2)
boton3 = Button(frame, text="3", width=3, command=lambda: numero_pulsado("3"))
boton3.grid(row=4, column=3)
boton_rest = Button(frame,
                    text="-",
                    width=3,
                    command=lambda: resta(numero_pantalla.get()))
boton_rest.grid(row=4, column=4)

# Fila 4 de botones
boton0 = Button(frame, text="0", width=3, command=lambda: numero_pulsado("0"))
boton0.grid(row=5, column=1)
boton_coma = Button(frame,
                    text=".",
                    width=3,
                    command=lambda: numero_pulsado("."))
boton_coma.grid(row=5, column=2)
boton_igual = Button(frame, text="=", width=3, command=lambda: el_resultado())
boton_igual.grid(row=5, column=3)
boton_suma = Button(frame,
                    text="+",
                    width=3,
                    command=lambda: suma(numero_pantalla.get()))
boton_suma.grid(row=5, column=4)

raiz.mainloop()
```

A continuación, veremos cómo trabajar con botones de radio, es decir, con la clase `Radiobutton`.

```python
from tkinter import Radiobutton, Tk

raiz = Tk()
raiz.title("Botones de radio")
raiz.iconbitmap("icon.ico")

Radiobutton(raiz, text="Femenino").pack()
Radiobutton(raiz, text="Masculino").pack()

raiz.mainloop()
```

{{< figure src="/courses/python-basic/img/pb50-img01.png" title="Primer contacto con la clase `Radiobutton`." numbered="true" >}}

A primera vista, observamos dos inconvenientes:

- aparecen ambas opciones seleccionadas al abrir la aplicación y
- por mucho que pulse sobre ellas, la selección no se modifica.

Para abordar esta situación, comenzamos creando una variable global, `opcion`, perteneciente a la clase `IntVar` y se la asignamos a ambos botones a través del parámetro `variable`; junto con un valor para cada uno de ellos, utilizando el parámetro `value`.

```python
from tkinter import IntVar, Radiobutton, Tk

raiz = Tk()
raiz.title("Botones de radio")
raiz.iconbitmap("icon.ico")

opcion = IntVar()

Radiobutton(raiz, text="Femenino", variable=opcion, value=1).pack()
Radiobutton(raiz, text="Masculino", variable=opcion, value=2).pack()

raiz.mainloop()
```

{{< figure src="/courses/python-basic/img/pb50-img02.png" title="Permitiendo la posibilidad de seleccionar una de las opciones." numbered="true" >}}

*Nota técnica*: si asignamos `value=0` a alguno de los botones, aparecerá seleccionado por defecto cuando abramos la aplicación. Esta característica puede resultar de cierta utilidad en algunos contextos.

Ahora bien, ¿cómo rescatamos el valor que ha seleccionado el usuario? Al igual que sucedía en el caso de la calculadora, recurriremos al uso de funciones en esta ocasión.

Así, generemos una, denominada `imprimir`, que imprima en la consola de *Python* el valor del botón seleccionado:

```python
from tkinter import IntVar, Label, Radiobutton, Tk

raiz = Tk()
raiz.title("Botones de radio")
raiz.iconbitmap("icon.ico")

opcion = IntVar()


def imprimir():
    print(opcion.get())


Label(raiz, text="Género:").pack()
Radiobutton(raiz, text="Femenino", variable=opcion, value=1,
            command=imprimir).pack()
Radiobutton(raiz, text="Masculino", variable=opcion, value=2,
            command=imprimir).pack()

raiz.mainloop()
```

Modifiquemos el código para ver dichos valores en la propia interfaz:

```python
from tkinter import IntVar, Label, Radiobutton, Tk

raiz = Tk()
raiz.title("Botones de radio")
raiz.iconbitmap("icon.ico")

opcion = IntVar()


def imprimir():
    if opcion.get() == 1:
        etiqueta.config(text="Has elegido género femenino.")
    else:
        etiqueta.config(text="Has elegido género masculino.")


Label(raiz, text="Género:").pack()
Radiobutton(raiz, text="Femenino", variable=opcion, value=1,
            command=imprimir).pack()
Radiobutton(raiz, text="Masculino", variable=opcion, value=2,
            command=imprimir).pack()

etiqueta = Label(raiz)
etiqueta.pack()

raiz.mainloop()
```

{{< figure src="/courses/python-basic/img/pb50-img03.png" title="Mostrando la opción seleccionada en la ventana de la aplicación." numbered="true" >}}

Incorporar un botón adicional que contemple otros géneros es sencillo:

```python
from tkinter import IntVar, Label, Radiobutton, Tk

raiz = Tk()
raiz.title("Botones de radio")
raiz.iconbitmap("icon.ico")

opcion = IntVar()


def imprimir():
    if opcion.get() == 1:
        etiqueta.config(text="Has elegido género femenino.")
    elif opcion.get() == 2:
        etiqueta.config(text="Has elegido género masculino.")
    else:
        etiqueta.config(text="Has elegido otras opciones para género.")


Label(raiz, text="Género:").pack()
Radiobutton(raiz, text="Femenino", variable=opcion, value=1,
            command=imprimir).pack()
Radiobutton(raiz, text="Masculino", variable=opcion, value=2,
            command=imprimir).pack()
Radiobutton(raiz, text="Otras opciones", variable=opcion, value=3,
            command=imprimir).pack()

etiqueta = Label(raiz)
etiqueta.pack()

raiz.mainloop()
```

{{< figure src="/courses/python-basic/img/pb50-img04.png" title="Añadiendo una nueva opción a las disponibles." numbered="true" >}}

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/50/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
