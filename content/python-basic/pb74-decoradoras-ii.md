---
title: 74. Decoradoras II
linktitle: 74. Decoradoras II
toc: true
type: book
date: "2019-06-14T00:00:01+01:00"
lastmod: "2019-06-14T00:00:01+01:00"
draft: false
weight: 74
---

## Vídeo

{{< youtube _IwlE3Z7U04 >}}

{{< youtube KOw0tpcspH4 >}}

## Notas personales

En esta lección, continuamos el estudio de las funciones generadoras, analizando cómo utilizar parámetros con ellas. Para ello, retomemos el código del ejemplo de la lección anterior:

```python
def funcion_decoradora(funcion_parametro):
    def funcion_interior():
        # Acciones adicionales que decoran
        print("Vamos a realizar un cálculo: ")
        funcion_parametro()
        # Acciones adicionales que decoran
        print("Hemos terminado el cálculo.")
    return funcion_interior


@funcion_decoradora
def suma():
    print(15 + 20)


@funcion_decoradora
def resta():
    print(30 - 10)


suma()
resta()
```

Modifiquemos las funciones `suma()` y `resta()` para que admitan la posibilidad de recibir parámetros:

```python
@funcion_decoradora
def suma(n1, n2):
    print(n1 + n2)


@funcion_decoradora
def resta(n1, n2):
    print(n1 - n2)
```

A continuación, en la `funcion_interior()` y en `funcion_parametros()`, que figuran dentro de la `funcion_decoradora()`, gestionamos esos parámetros utilizando `*args`, que posibilita que una función reciba un número indeterminado de parámetros. Así,

```python
def funcion_decoradora(funcion_parametro):
    def funcion_interior(*args):
        # Acciones adicionales que decoran
        print("Vamos a realizar un cálculo: ")
        funcion_parametro(*args)
        # Acciones adicionales que decoran
        print("Hemos terminado el cálculo.")
    return funcion_interior
```

De esta manera, si ejecutamos ahora el código para las siguientes llamadas de las funciones `suma()` y `resta()`:

```python
suma(10, 5)
resta(25, 20)
```

```bash
Vamos a realizar un cálculo: 
15
Hemos terminado el cálculo.
Vamos a realizar un cálculo: 
5
Hemos terminado el cálculo.
```

Por otro lado, incluso podemos ampliar la funcionalidad de nuestra decoradora, permitiendo la posibilidad de admitir parámetros que sigan el patrón *key = value*. Para ello, utilizamos en la definición de `funcion_interior()` y `funcion_parametro()` la convención `**kwargs` como sigue:

```python
def funcion_decoradora(funcion_parametro):
    def funcion_interior(*args, **kwargs):
        # Acciones adicionales que decoran
        print("Vamos a realizar un cálculo: ")
        funcion_parametro(*args, **kwargs)
        # Acciones adicionales que decoran
        print("Hemos terminado el cálculo.")
    return funcion_interior
```

A continuación, construimos una función que realice la potenciación de un número y procedemos a su llamada, utilizando ahora el esquema *key = value*:

```python
@funcion_decoradora
def potencia(base, exponente):
    print(pow(base, exponente))


potencia(base=5, exponente=2)
```

```bash
Vamos a realizar un cálculo: 
25
Hemos terminado el cálculo.
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/74/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
