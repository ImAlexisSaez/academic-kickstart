---
title: 68. La función map
linktitle: 68. Map
toc: true
type: docs
date: "2019-06-09T00:00:01+01:00"
lastmod: "2019-06-09T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 68

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 68
---

## Vídeo

{{< youtube 4dkjpHI6vpA >}}

## Notas personales

En esta lección, estudiaremos la función `map()`, que, como `filter()`, también forma parte de un conjunto de funciones conocidas como ''de orden superior'' y nos permiten utilizar en *Python* el paradigma de **programación funcional**.

La filosofía de ambas funciones es ciertamente similar ya que, por ejemplo, `map()` aplica una función a cada elemento de un objeto de tipo iterable (listas, tuplas...) devolviendo a su vez un objeto de tipo iterable que contiene los resultados de dicha aplicación.

Retomemos la clase definida en la lección anterior, junto con la lista de empleados generada:

```python
class Empleado:
    def __init__(self, nombre, cargo, salario):
        self.nombre = nombre
        self.cargo = cargo
        self.salario = salario

    def __str__(self):
        return f"{self.nombre} trabaja como {self.cargo} y cobra {self.salario} €."


lista_empleados = [
    Empleado("Juan", "Director", 6700),
    Empleado("Ana", "Presidenta", 7500),
    Empleado("Antonio", "Administrativo", 1200),
    Empleado("Sara", "Secretaria", 1250),
    Empleado("Mario", "Botones", 1000)
]
```

*Nota*: hemos modificado los salarios para que sus cantidades sean mensuales, en lugar de las anuales declaradas en la lección anterior.

Imaginemos ahora que todos los empleados recibien un extra monetario en forma de comisión, que hemos de agregar a su salario mensual.

```python
def calcula_comision(empleado):
    empleado.salario *= 1.03
    return empleado


lista_empleados_comision = map(calcula_comision, lista_empleados)

[print(e) for e in lista_empleados_comision]
```

```bash
Juan trabaja como Director y cobra 6901.0 €.
Ana trabaja como Presidenta y cobra 7725.0 €.
Antonio trabaja como Administrativo y cobra 1236.0 €.
Sara trabaja como Secretaria y cobra 1287.5 €.
Mario trabaja como Botones y cobra 1030.0 €.
```

¿Y si queremos aplicar la comisión solamente a aquellos trabajadores que tengan un salario inferior a 3000 euros?

```python
def calcula_comision(empleado):
    if empleado.salario <= 3000:
        empleado.salario *= 1.03
    return empleado


lista_empleados_comision = map(calcula_comision, lista_empleados)

[print(e) for e in lista_empleados_comision]
```

```bash
Juan trabaja como Director y cobra 6700 €.
Ana trabaja como Presidenta y cobra 7500 €.
Antonio trabaja como Administrativo y cobra 1236.0 €.
Sara trabaja como Secretaria y cobra 1287.5 €.
Mario trabaja como Botones y cobra 1030.0 €.
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/68/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
