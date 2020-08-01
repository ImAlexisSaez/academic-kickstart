---
title: 69. Expresiones regulares I
linktitle: 69. RegExp I
toc: true
type: book
date: "2019-06-10T00:00:01+01:00"
lastmod: "2019-06-10T00:00:01+01:00"
draft: false
weight: 69
---

## Vídeo

{{< youtube qpwn3gRtxCo >}}

## Notas personales

En esta lección, comenzaremos el estudio de las **expresiones regulares** en *Python*, que son una secuencia de caracteres que forman un patrón de búsqueda y sirven para el trabajo y procesamiento de texto. Por ejemplo, podemos estar interesados, entre otras tareas, en:

- Buscar un texto que se ajuste a un formato determinado (correo electrónico).
- Buscar si existe o no una cadena de caracteres dentro de un texto.
- Contar el número de coincidencias dentro de un texto.

Conviene que consultemos la [documentación oficial](https://docs.python.org/3/library/re.html) del módulo asociado a las expresiones regulares, `re`, en *Python*.

A continuación, veamos algunos ejemplos sencillos. Empecemos ilustrando el uso del método `search()`, que nos permite buscar una cadena de texto concreta y nos ofrece su localización:

```python
import re

cadena = "Vamos a aprender expresiones regulares."

print(re.search("aprender", cadena))
```

```bash
<re.Match object; span=(8, 16), match='aprender'>
```

Apreciamos que la ejecución nos devuelve un objeto, de tipo `Match`, que en el intervalo de caracteres `(8, 16)` ha encontrado la cadena de texto de interés, `aprender`.

Ahora bien, si insertamos una cadena de texto que no figure en la variable `cadena`, el resultado que arroja la ejecución del programa es `None`:

```python
import re

cadena = "Vamos a aprender expresiones regulares."

print(re.search("Python", cadena))
```

```bash
None
```

Obviamente, podemos pasar variables a la función `search()`:

```python
import re

cadena = "Vamos a aprender expresiones regulares."

texto_buscar = "aprender"

if re.search(texto_buscar, cadena) is not None:
    print("Texto encontrado.")
else:
    print("Texto no encontrado.")
```

```bash
Texto encontrado.
```

Hemos encontrado el texto, efectivamente, pero, ¿en qué carácter comienza? Utilizando el método `start()` hallamos la respuesta:

```python
import re

cadena = "Vamos a aprender expresiones regulares."

texto_buscar = "aprender"

texto_encontrado = re.search(texto_buscar, cadena)

print(texto_encontrado.start())
```

```bash
8
```

Análogamente,

```python
print(texto_encontrado.end())
```

```bash
16
```

Al hilo de las acciones anteriores, el método `span()` nos devuelve una tupla con los valores mostrados arriba:

```python
print(texto_encontrado.span())
```

```bash
(8, 16)
```

Finalmente, examinemos la utilidad del método `findall()`, para lo cual hemos de ampliar un poco la cadena de texto original suministrada:

```python
import re

cadena = '''
    Vamos a aprender expresiones regulares en Python.
    Python es un lenguaje de sintaxis sencilla.'''

texto_buscar = "Python"

print(re.findall(texto_buscar, cadena))
```

```bash
['Python', 'Python']
```

Accedemos a una lista que contiene el texto de interés, tantas veces como repeticiones figuren en él. Empleando ahora la función `len()`:

```python
import re

cadena = '''
    Vamos a aprender expresiones regulares en Python.
    Python es un lenguaje de sintaxis sencilla.'''

texto_buscar = "Python"

print(len(re.findall(texto_buscar, cadena)))
```

```bash
2
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/69/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
