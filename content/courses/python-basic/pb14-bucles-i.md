---
title: 14. Bucles I
linktitle: 14. Bucles I
toc: false
type: docs
date: "2019-05-01T00:02:01+01:00"
lastmod: "2019-05-01T00:02:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 14

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 14
---

## Vídeo

{{< youtube GQGhU1526Oo >}}

## Notas personales

Abordaremos ahora otro tipo de estructura de control de flujo (las estructuras condicionales asimismo lo eran): los **bucles**.

La utilidad de un **bucle** es repetir una o varias líneas de código tantas veces como sea preciso (siendo esta cantidad conocida de antemano o no). En *Python* tenemos dos tipos de bucles:

- *determinados*: sabemos a priori cuántas veces se repetirá el bloque de código, e
- *indeterminados*: desconocemos a priori el número de repeticiones del bloque de código.

Empecemos viendo el primer tipo, al que pertenece la instrucción `for`, cuya sintaxis es:

```python
for variable in elemento_a_recorrer:
    instrucciones
```

donde el `elemento_a_recorrer` puede ser una lista, una tupla, una cadena de texto...

Por ejemplo, para imprimir tres veces una palabra, una posible estrategia sería:

```python
for i in [1, 2, 3]:
    print("Hola")
```

Aunque hemos utilizado una lista de números, no es imprescindible. El siguiente ejemplo consigue el mismo resultado:

```python
for i in ["enero", "febrero", "marzo"]:
    print("Hola")
```

En ambos casos, el elemento a recorrer es una lista de tres elementos y es por ello que el mensaje `"Hola"` se repite en tres ocasiones, tantas como el mencionado número de elementos de la correspondiente lista.

Si en lugar de un texto predeterminado optamos por imprimir la propia variable en ambos casos, el resultado es:

```python
for i in [1, 2, 3]:
    print(i)

# 1
# 2
# 3
```

```python
for i in ["enero", "febrero", "marzo"]:
    print(i)

# enero
# febrero
# marzo
```

La variable no tiene que denominarse necesariamente `i`:

```python
for meses in ["enero", "febrero", "marzo"]:
    print(meses)

# enero
# febrero
# marzo
```
