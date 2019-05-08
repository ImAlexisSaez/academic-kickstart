---
title: 24. Programación orientada a objetos I
linktitle: 24. POO I
toc: true
type: docs
date: "2019-05-08T00:00:01+01:00"
lastmod: "2019-05-08T00:00:01+01:00"
draft: false
menu:
  python-basic:
    parent: Lecciones
    weight: 24

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 24
---

## Vídeo

{{< youtube 5Ohme4A2Weg >}}

## Notas personales

*Python* es un lenguaje de programación orientado a objetos (POO). Existen, principalemente, dos paradigmas de programación:

1. Programación orientada a procedimientos.
2. Programación orientada a objetos.

### Programación orientada a procedimientos

Algunos ejemplos de lenguajes de programación que siguen este paradigma son: Fortan, Cobol, Basic...

Entre sus principales desventajas encontramos:

- Las unidades de código son muy grandes en aplicaciones complejas (resultando en un número de líneas significativamente elevado).
- En aplicaciones complejas, el código resulta difícil de descifrar.
- Las aplicaciones generadas suelen ser poco reutilizables.
- Si existen fallos en alguna línea del código, es muy probable que el programa caiga en su totalidad.
- Aparición frecuente de **código espaguetti** (saltos en el flujo de ejecución del programa).
- Es difícil de depurar el código por otros programadores en caso de necesidad o error.

### Programación orientada a objetos

La programación orientada a objetos consiste en trasladar el comportamiento que tienen los objetos en la vida real al código de programación. Los objetos tienen un estado, un comportamiento (¿qué puede hacer?) y unas propiedades.

Por ejemplo, pensemos en el objeto ''coche'':

- ¿Cuál es el estado de un coche? Puede estar parado, circulando, aparcado...
- ¿Qué propiedades tiene un coche? Tiene un color, un peso, un tamaño...
- ¿Qué comportamiento tiene un coche? Puede arrancar, frenar, acelerar, girar...

| Objeto | Coche |
| ------ | ----- |
| Propiedades (atributos) | Color, peso, alto, largo... |
| Comportamiento | Arrancar, frenar, girar, acelerar... |

Algunos ejemplos de lenguajes de programación que emplean este paradigma son: C++, Java, VisualNet...

Entre las principales ventajas encontramos:

- Los programas están divididos en ''trozos'', ''partes'', ''módulos'' o ''clases'', es decir, existe **modularización**.
- El código es muy reutilizable. Aparece en el concepto de **herencia**.
- Si existen fallos en alguna línea del código, el programa es posible que continue con su funcionamiento, debido al **control de excepciones**.
- Surge el concepto de **encapsulamiento**.

El vocabulario más frecuente de este paradigma de programación incluye palabras o expresiones como:

- Clase.
- Objeto.
- Ejemplar de clase. Instancia de clase. Ejemplarizar una clase. Instanciar una clase.
- Modularización.
- Encapsulamiento / encapsulación.
- Herencia.
- Polimorfismo.
