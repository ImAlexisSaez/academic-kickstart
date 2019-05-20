---
title: 5. Funciones I
linktitle: 5. Funciones I
toc: true
type: docs
date: "2019-04-29T00:01:02+01:00"
lastmod: "2019-04-29T00:01:02+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 5

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 5
---

## Vídeo

{{< youtube VY448UWAQ_0 >}}

## Notas personales

Una **función** es un conjunto de líneas de código agrupadas, que funcionan como una unidad realizando una tarea específica. Puede devolver valores, tener parámetros o argumentos y recibe el nombre de **método** cuando está definida dentro de una clase.

En *Python* existen funciones predifinidas, como por ejemplo `print()`. Su principal utilidad es la reutilización de código y su sintaxis es:

```python
def nombre(parámetros):
    instrucciones de la función
    return(opcional)
```

Ejecutamos (o llamamos) una función tecleando `nombre_función(parámetros)`. 

A continuación, dejamos de lado el IDLE de *Sublime Text 3* y pasamos a compilar directamente ficheros desde el propio editor. Para ello, desplegamos el menú `Tools` y en el apartado `Build System` escogemos la opción `Python`. Acto seguido, creamos el fichero `funciones.py`, que contendrá la instrucción

```python
print("Estamos aprendiendo Python.")
```

y utilizamos la combinación de teclas `ctrl + b` para compilar. En la parte inferior de la ventana aparecerá el resultado de la ejecución y el tiempo invertido. 

Ampliemos el anterior fichero a

```python
print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")
```

e imaginemos que necesitamos que las anteriores tres líneas se impriman cinco veces. Podemos, simplemente, copiar y pegar el anterior bloque de código reiteradamente:

```python
print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")

print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")

print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")

print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")

print("Estamos aprendiendo Python.")
print("Estamos aprendiendo instrucciones básicas.")
print("Poco a poco iremos avanzando.")
```

Las funciones nos permiten reutilizar código para, precisamente, evitar que actuemos como arriba. Definamos una función llamada `mensaje()` y ejecutémosla tantas veces como deseemos.

```python
def mensaje():
    print("Estamos aprendiendo Python.")
    print("Estamos aprendiendo instrucciones básicas.")
    print("Poco a poco iremos avanzando.")
```

Ahora, la tarea que buscábamos realizar quedaría como:

```python
mensaje()
mensaje()
mensaje()
mensaje()
mensaje()
```

Entre distintas llamadas a una función puede haber cualquier otro tipo de instrucción:

```python
mensaje()

print("Ejecutando código fuera de función")

mensaje()
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/05/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
