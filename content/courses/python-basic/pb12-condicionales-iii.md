---
title: 12. Condicionales III
linktitle: 12. Condicionales III
toc: true
type: docs
date: "2019-05-01T00:01:01+01:00"
lastmod: "2019-05-01T00:01:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 12

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 12
---

## Vídeo

{{< youtube qxgEolsC6rg >}}

## Notas personales

Aunque en *Python* no existe una instrucción de tipo `switch`, como en otros lenguajes de programación, veremos que, gracias a la concatenación de operadores de comparación, a los operadores lógicos `and` y `or`, y al operador `in`, disponemos de bastante versatilidad a la hora de trabajar con estructuras condicionales.

Antes de nada, siguiendo las instrucciones de [este post](https://stackoverflow.com/a/19977184), creamos un atajo para ejecutar de manera más ágil nuestros programas. Ahora ya no hemos de navegar por los menús cada vez que deseemos realizar una ejecución en la consola, simplemente hemos de emplear la combinación de teclas `ctrl + alt + b` (mientras que para cerrarla usamos la combinación de teclas `ctrl + w`).

Empecemos creando un programa que controle si un dato numérico introducido para la edad es válido, es decir, no es negativo ni un valor muy elevado. Para ello, utilizaremos la concatenación de operadores de comparación, teniendo en cuenta que su lectura se realiza de izquierda a derecha:

```python
def comprueba_edad(edad):
    if 0 < edad < 100:
        print("La edad es correcta.")
    else:
        print("La edad es incorrecta.")


comprueba_edad(5)  # La edad es correcta.
comprueba_edad(135)  # La edad es incorrecta.
comprueba_edad(-7)  # La edad es incorrecta.
```

Creemos ahora un programa que evaluará el salario de diferentes trabajadores de una empresa:

```python
sal_presidente = int(input("Introduce el salario del presidente: "))
print("Salario presidente: " + str(sal_presidente))

sal_director = int(input("Introduce el salario del director: "))
print("Salario director: " + str(sal_director))

sal_jefe_area = int(input("Introduce el salario del jefe de área: "))
print("Salario jefe de área: " + str(sal_jefe_area))

sal_administrativo = int(input("Introduce el salario del administrativo: "))
print("Salario administrativo: " + str(sal_administrativo))

if sal_administrativo < sal_jefe_area < sal_director < sal_presidente:
    print("Todo funciona correctamente.")
else:
    print("Algo falla en esta empresa.")
```

## Código fuente

El código fuente y los posibles ficheros externos generados correspondientes a esta lección se encuentran disponibles para su consulta en la carpeta `/lecciones/12/` del [repositorio](https://github.com/ImAlexisSaez/curso-python-desde-0).
