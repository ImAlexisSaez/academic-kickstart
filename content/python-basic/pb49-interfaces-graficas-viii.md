---
title: 49. Interfaces gráficas VIII
linktitle: 49. Interfaces VIII
toc: true
type: book
date: "2019-05-25T00:00:01+01:00"
lastmod: "2019-05-25T00:00:01+01:00"
draft: false
weight: 49
---

## Vídeo

{{< youtube LnO35TiFuQY >}}

## Notas personales

En esta lección, nuestro objetivo será conseguir que la calculadora que estamos generando sea capaz de sumar valores numéricos enteros.

Empecemos declarando una variable global, que será accesible desde todos las funciones del programa, denominada `operacion` y que almacenará la operación aritmética que desea el usuario llevar a cabo. Además, la utilizaremos para conseguir que la pantalla vuelva a su estado inicial a través del uso de bloques condicionales.

```python
operación = ""
```

Esta variable cambiará de valor a medida que pulsemos los botones de operaciones aritméticas. Por ejemplo, para la suma, definimos la función:

```python
# Función suma
def suma():
    global operacion
    operacion = "suma"
```

A continuación, modificamos el código de `boton_suma` como sigue:

```python
boton_suma = Button(frame, text="+", width=3, command=lambda: suma())
```

Acto seguido, hemos de conseguir que, cuando se pulse dicho botón, la pantalla se borre y permita el almacenamiento de un nuevo número. Modifiquemos la función `numero_pulsado()`:

```python
def numero_pulsado(num):
    global operacion
    if operacion != "":
        numero_pantalla.set(num)
        operacion = ""
    else:
        numero_pantalla.set(numero_pantalla.get() + num)
```

Si pulsamos sobre el botón de sumar, la condición `operacion != ""` sería cierta, por lo que entraríamos en esa parte de la estructura condicional. En su interior, apreciamos que no concatenamos el número con nada más y volvemos a declarar el valor de la variable `operacion` como una cadena vacía, para permitir así la correcta introducción de un nuevo número.

Ahora necesitamos una variable global, que denominaremos `resultado`, que vaya almacenando los valores introducidos:

```python
resultado = 0
```

La siguiente tarea consiste en actualizar la función `suma()`:

```python
# Función suma
def suma(num):
    global operacion, resultado
    operacion = "suma"
    resultado += int(num)
    numero_pantalla.set(resultado)
```

donde `num` representa el número que aparece en la pantalla de la calculadora al pulsar el botón de sumar. Como estamos trabajando con cuadros de texto, *Python* almacena los textos, lógicamente como su nombre indica, como cadenas de caracteres, de ahí la necesidad de utilizar la función `int()`. Una vez realizada la operación aritmética, mostramos su resultado en la pantalla con `numero_pantalla.set(resultado)`.

El nuevo parámetro de la función `suma()` nos obliga a modificar el código de `boton_suma`:

```python
boton_suma = Button(frame,
                    text="+",
                    width=3,
                    command=lambda: suma(numero_pantalla.get()))
```

A continuación, programemos el comportamiento del botón del símbolo igual.

```python
# Función el_resultado (para el botón igual)
def el_resultado():
    global resultado
    numero_pantalla.set(resultado + int(numero_pantalla.get()))
    resultado = 0
```

Es decir, al resultado acumulado hemos de sumarle el número que figure en pantalla antes de pulsar el botón del símbolo igual. Tras ello, reseteamos la variable `resultado`.

Procedamos ahora a modificar el código el mencionado botón:

```python
boton_igual = Button(frame, text="=", width=3, command=lambda: el_resultado())
```

Finalmente, como viene siendo habitual, comparto el código completo de la aplicación para que podamos tener una visión global de la calculadora:

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

# Pantalla
pantalla = Entry(frame, textvariable=numero_pantalla)
pantalla.grid(row=1, column=1, padx=10, pady=10, columnspan=4)
pantalla.config(background="black", fg="#03f943", justify="right")


# Pulsaciones teclado
def numero_pulsado(num):
    global operacion
    if operacion != "":
        numero_pantalla.set(num)
        operacion = ""
    else:
        numero_pantalla.set(numero_pantalla.get() + num)


# Función suma
def suma(num):
    global operacion, resultado
    operacion = "suma"
    resultado += int(num)
    numero_pantalla.set(resultado)


# Función el_resultado (para el botón igual)
def el_resultado():
    global resultado
    numero_pantalla.set(resultado + int(numero_pantalla.get()))
    resultado = 0


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
boton_igual = Button(frame, text="=", width=3, command=lambda: el_resultado())
boton_igual.grid(row=5, column=3)
boton_suma = Button(frame,
                    text="+",
                    width=3,
                    command=lambda: suma(numero_pantalla.get()))
boton_suma.grid(row=5, column=4)

raiz.mainloop()
```


## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/49/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
