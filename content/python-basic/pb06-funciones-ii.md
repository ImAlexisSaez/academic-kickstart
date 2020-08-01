---
title: 6. Funciones II
linktitle: 6. Funciones II
toc: true
type: book
date: "2019-04-29T00:01:03+01:00"
lastmod: "2019-04-29T00:01:03+01:00"
draft: false
weight: 6
---

## Vídeo

{{< youtube vawEHhV_HFA >}}

## Notas personales

Comencemos definiendo una función que suma dos números dados (5 y 7), mediante el mecanismo aprendido en la lección anterior:

```python
def suma():
    num1 = 5
    num2 = 7
    print(num1 + num2)


suma()
```

Podemos reutilizar tantas veces como queramos la función `suma()`. No obstante, su utilidad así declarada es bastante limitada. Nos gustaría que no siempre sumara los dos mismos valores, sino aquellos que nos interesen en cada llamada. Para ello emplearemos los **parámetros** o **argumentos**.

*Nota*: aunque el autor del curso se refiere a los términos ''parámetros'' y ''argumentos'' casi como si fueran sinónimos, en realidad hay un sutil matiz que los diferencia: los **parámetros** son las variables que aparecen en la definición de una función o método; cuando se produce la llamada a dicha función, los **argumentos** son los datos que pasamos a los parámetros de la mencionada función.

Definamos de nuevo la función `suma()`, ahora con dos parámetros, con el objetivo de que realice la suma de dos números que pasaremos como argumentos:

```python
def suma(num1, num2):
    print(num1 + num2)


suma(5, 7)  # 12
suma(2, 3)  # 5
suma(35, 358)  # 393
```

Tal y como está declarada la nueva función de suma, **obligatoriamente** hemos de pasarle dos argumentos o sino aparecerán errores.

```python
suma(7)
# TypeError: suma() missing 1 required positional argument: 'num2'
```

```python
suma(1, 2, 3)
# TypeError: suma() takes 2 positional arguments but 3 were given
```

Puede resultar conveniente, por legibilidad, pasar los argumentos a una función utilizando el esquema `parámetro=valor`.

```python
suma(num1=5, num2=7)  # 12
```

Además, las funciones

- pueden poseer parámetros de diferentes tipos y
- devuelven valores siempre y cuando empleemos la instrucción `return`.

```python
def suma(num1, num2):
    resultado = num1 + num2
    return resultado


suma(5, 7)
```

La ejecución del anterior bloque de código no muestra resultado alguno en la consola. La función devuelve el resultado, pero no lo hemos imprimido. Así,

```python
print(suma(5, 7))  # 12
```

Una ventaja de utilizar la instrucción `return` reside en que podemos almacenar los valores que devuelve una función en variables y trabajar posteriormente con ellas.

```python
almacena_resultado = suma(5, 8)
print(almacena_resultado)  # 13

actualiza_resultado = suma(almacena_resultado, 8)
print(actualiza_resultado)  # 13 + 8 = 21
```

*Nota técnica*: *Python* pasa siempre los valores por referencia, no por valor.

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/06/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
