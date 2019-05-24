---
title: 48. Interfaces gráficas VII
linktitle: 48. Interfaces VII
toc: true
type: docs
date: "2019-05-24T00:00:01+01:00"
lastmod: "2019-05-24T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 48

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 48
---

## Vídeo

{{< youtube oIzt6ESA7nU >}}

## Notas personales

Una vez elaborada la interfaz gráfica de la calculadora, en esta lección abordaremos cómo programar parte de la funcionalidad de la misma. Para empezar, nuestro objetivo será conseguir que al pulsar los diferentes botones numéricos aparezcan sus valores asociados en la pantalla.

Empecemos creando una variable para almacenar una cadena de texto y asociémosla a la pantalla:

```python
numero_pantalla = StringVar()

pantalla = Entry(frame, textvariable=numero_pantalla)
```

A continuación, creemos una función que, por ejemplo, escriba el número `4` en pantalla:

```python
# Pulsaciones teclado
def numero_pulsado():
    numero_pantalla.set("4")
```

Ahora, asociémosla al botón correspondiente:

```python
boton4 = Button(frame, text="4", width=3, command=numero_pulsado)
```

Ahora, al pulsar en el botón del número cuatro, aparece un `4` en la pantalla. Vemos que si pulsamos en varias ocasiones, no se añaden más cuatros, que sería el comportamiento deseable. Modifiquemos la función `numero_pulsado()` para conseguir tal efecto. Para ello, obtendremos la información actual de la pantalla y le agregaremos el número `4` después:

```python
# Pulsaciones teclado
def numero_pulsado():
    numero_pantalla.set(numero_pantalla.get() + "4")
```

Para generalizar, necesitaremos el uso de funciones *lambda* o *anónimas* en la declaración de los botones. De no utilizarlas, tal y como transcurre el flujo del programa, al llegar a la línea de la declaración de `boton4`, se produciría directamente la llamada de la función `numero_pulsado("4")`, mostrando (sin que el usuario pulse sobre nada) un `4` en la pantalla al abrir la calculadura y, además, deshabilitando la funcionalidad del botón, puesto que al seguir pulsando sobre él no añade más cuatros.

```python
def numero_pulsado(num):
    numero_pantalla.set(numero_pantalla.get() + num)

boton4 = Button(frame, text="4", width=3, command=lambda: numero_pulsado("4"))
```

Para finalizar, incluyo el código completo de la aplicación elaborada hasta este instante, para obtener así una visión global de la calculadora:

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

# Pantalla
pantalla = Entry(frame, textvariable=numero_pantalla)
pantalla.grid(row=1, column=1, padx=10, pady=10, columnspan=4)
pantalla.config(background="black", fg="#03f943", justify="right")


# Pulsaciones teclado
def numero_pulsado(num):
    numero_pantalla.set(numero_pantalla.get() + num)


# Fila 1 de botones
boton7 = Button(frame, text="7", width=3, command=lambda: numero_pulsado("7"))
boton7.grid(row=2, column=1)
boton8 = Button(frame, text="8", width=3, command=lambda: numero_pulsado("8"))
boton8.grid(row=2, column=2)
boton9 = Button(frame, text="9", width=3, command=lambda: numero_pulsado("9"))
boton9.grid(row=2, column=3)
boton_div = Button(frame, text="/", width=3)
boton_div.grid(row=2, column=4)

# Fila 2 de botones
boton4 = Button(frame, text="4", width=3, command=lambda: numero_pulsado("4"))
boton4.grid(row=3, column=1)
boton5 = Button(frame, text="5", width=3, command=lambda: numero_pulsado("5"))
boton5.grid(row=3, column=2)
boton6 = Button(frame, text="6", width=3, command=lambda: numero_pulsado("6"))
boton6.grid(row=3, column=3)
boton_mult = Button(frame, text="*", width=3)
boton_mult.grid(row=3, column=4)

# Fila 3 de botones
boton1 = Button(frame, text="1", width=3, command=lambda: numero_pulsado("1"))
boton1.grid(row=4, column=1)
boton2 = Button(frame, text="2", width=3, command=lambda: numero_pulsado("2"))
boton2.grid(row=4, column=2)
boton3 = Button(frame, text="3", width=3, command=lambda: numero_pulsado("3"))
boton3.grid(row=4, column=3)
boton_rest = Button(frame, text="-", width=3)
boton_rest.grid(row=4, column=4)

# Fila 4 de botones
boton0 = Button(frame, text="0", width=3, command=lambda: numero_pulsado("0"))
boton0.grid(row=5, column=1)
boton_coma = Button(frame,
                    text=".",
                    width=3,
                    command=lambda: numero_pulsado("."))
boton_coma.grid(row=5, column=2)
boton_igual = Button(frame, text="=", width=3)
boton_igual.grid(row=5, column=3)
boton_suma = Button(frame, text="+", width=3)
boton_suma.grid(row=5, column=4)

raiz.mainloop()
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/48/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
