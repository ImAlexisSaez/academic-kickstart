---
title: 19. Generadores I
linktitle: 19. Generadores I
toc: true
type: docs
date: "2019-05-05T00:02:01+01:00"
lastmod: "2019-05-05T00:02:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 19

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 19
---

## Vídeo

{{< youtube TLVnoqXGWpY >}}

## Notas personales

Un **generador** es una estructura que extrae valores de una función y los almacena, de uno en uno, en objetos iterables (que se pueden recorrer). Cada vez que un generador almacena un valor, permanece en un estado pausado hasta que se solicita el siguiente, característica que se conoce como **suspensión de estado**.

La utilidad de los generadores reside en que:

- son más eficientes que las funciones tradicionales (sobretodo en consumo de recursos y tiempo, al no tener que construir ''estructuras completas de datos'');
- resultan muy útiles con listas de valores infinitos; y
- bajo determinados escenarios, será recomendable que un generador devuelva los valores de uno en uno.

Su sintaxis es:

```python
def nombre():
    yield
```

Creemos un programa que nos genere una lista de números pares, primero a través de una función y luego utilizando generadores:

```python
def genera_pares(limite):
    num = 1
    lista_pares = []
    while num < limite:
        lista_pares.append(num * 2)
        num += 1
    return lista_pares


print(genera_pares(10))  # [2, 4, 6, 8, 10, 12, 14, 16, 18]
```

```python
def genera_pares(limite):
    num = 1
    while num < limite:
        yield num * 2
        num += 1


# Creo el objeto iterable que genera la función
devuelve_pares = genera_pares(10)

# Recorro el objeto iterable con, por ejemplo, un bucle for
for i in devuelve_pares:
    print(i)

# 2
# 4
# 6
# 8
# 10
# 12
# 14
# 16
# 18
```

Imaginemos ahora que nuestro objetivo es imprimir en la consola únicamente los tres primeros números pares. Con el método `next()` podemos solicitar valores de uno en uno al objeto iterable fruto del generador:

```python
def genera_pares(limite):
    num = 1
    while num < limite:
        yield num * 2
        num += 1


# Creo el objeto iterable que genera la función
devuelve_pares = genera_pares(10)

print(next(devuelve_pares))  # 2

print("Aquí podría ir más código.")

print(next(devuelve_pares))  # 4

print("Aquí podría ir más código.")

print(next(devuelve_pares))  # 6
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/19/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
