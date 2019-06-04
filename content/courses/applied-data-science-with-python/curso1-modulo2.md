---
title: Módulo 2
linktitle: Módulo 2
toc: true
type: docs
date: "2019-06-01T00:00:01+01:00"
lastmod: "2019-06-01T00:00:01+01:00"
draft: false
menu:
  applied-data-science-with-python:
    parent: Curso 1
    weight: 2

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 2
---

## 1. Introducción {#section-1}

En este módulo, investigaremos cómo *Python*, dado un conjunto de datos, puede realizar manipulaciones, proceder a su limpieza y llevar a cabo consultas a través de la librería `pandas`. Para resolver dudas sobre el uso de este módulo, cuatro buenos recursos son:

- El portal [Stack Overflow](https://stackoverflow.com/).
- Los libros [Python for Data Analysis](https://www.amazon.com/Python-Data-Analysis-Wrangling-IPython/dp/1491957662/) y [Learning the Pandas Library](https://www.amazon.com/Learning-Pandas-Library-Munging-Analysis/dp/153359824X/).
- El agregador de blogs [Planet Python](https://planetpython.org/).
- El podcast [Data Skeptic](https://dataskeptic.com/).

## 2. La estructura de datos Series {#section-2}

La estructura de datos `Series`, de la librería `pandas`, es una especie de mezcla entre las listas y los diccionarios de *Python* que estudiamos en el módulo anterior. Los elementos se almacenan en orden y tenemos a nuestra disposición una serie de etiquetas (*labels*), que nos permiten un acceso a ellos por nombre.

Empecemos importando la propia librería `pandas` que, por convención, habitualmente utiliza el *alias* `pd`. Desde el *notebook* de *Jupyter* podemos acceder a la documentación para la estructura de datos `Series` si tecleamos `pd.Series?`.


```python
import pandas as pd
pd.Series?
```

En primer lugar, generemos una lista de animales y convirtámosla a un objeto de la clase `Series`:


```python
animales = ["Tigre", "Oso", "Alce"]
pd.Series(animales)
```




    0    Tigre
    1      Oso
    2     Alce
    dtype: object



Análogamente, repitamos el proceso para una lista de números enteros:


```python
numeros = [1, 2, 3]
pd.Series(numeros)
```




    0    1
    1    2
    2    3
    dtype: int64



En ambos casos, observamos una primera columna de índices numéricos, que podríamos utilizar para acceder a los elementos de esta estructura de la manera que estamos habituados en *Python*. Cabe destacar también el atributo `dtype`, diferente para ambos objetos y que se adapta automáticamente (aunque lo podemos declarar manualmente) al tipo de los elementos de la lista. Con ello, *Python* trabaja de manera más eficiente, tanto en memoria, como a la hora de llevar a cabo operaciones.

Por otro lado, la instrucción `None` nos permite indicar la ausencia de ciertos registros en nuestros conjuntos datos (los conocidos *valores perdidos*). No obstante, hemos de ser cautos, pues según el tipo del resto de elementos, `None` se almacena de manera diferente.


```python
animales = ["Tigre", "Oso", None]
pd.Series(animales)
```




    0    Tigre
    1      Oso
    2     None
    dtype: object




```python
numeros = [1, 2, None]
pd.Series(numeros)
```




    0    1.0
    1    2.0
    2    NaN
    dtype: float64



En el primer caso, vemos que se registra como un objeto, mientras que en el segundo lo hace como un número especial en coma flotante: `NaN`. En cualquier caso, es diferente a `None`, como podemos comprobar a continuación:


```python
import numpy as np
np.nan == None
```




    False



Curiosamente, también falla el test de comparación con respecto a sí mismo. La lógica tras esta decisión es que dos valores perdidos cualesquiera no tienen porqué coincidir.


```python
np.nan == np.nan
```




    False



Por tanto, para comprobar la existencia de valores perdidos, hemos de recurrir a la función `isnan()` de la librería *NumPy*:


```python
np.isnan(np.nan)
```




    True



A continuación, veamos cómo crear un objeto de tipo `Series` a partir de un diccionario. De proceder de tal modo, la columna de índices estará compuesta por las claves del propio diccionario (y no por números enteros):


```python
deportes = {"Fútbol": "España",
            "Golf": "Italia",
            "Baloncesto": "Francia",
            "Kárate": "Japón"}
d = pd.Series(deportes)
d
```




    Fútbol         España
    Golf           Italia
    Baloncesto    Francia
    Kárate          Japón
    dtype: object



Para acceder a los índices de la estructura creada, hemos de utilizar el atributo `index`:


```python
d.index
```




    Index(['Fútbol', 'Golf', 'Baloncesto', 'Kárate'], dtype='object')



De hecho, no tenemos que recurrir necesariamente al uso de un diccionario para acceder a etiquetas con nombres. En los ejemplos que vimos al principio de este apartado, basta que configuremos adecuadamente el valor del parámetro `index` para conseguir la misma funcionalidad que arriba:


```python
a = pd.Series(["Tigre", "Oso", "Alce"], index=["India", "Estados Unidos", "Canadá"])
a
```




    India             Tigre
    Estados Unidos      Oso
    Canadá             Alce
    dtype: object



Es más, mediante dicho parámetro, podemos restringir la creación del objeto `Series` a los valores que nos interesen de un determinado diccionario (y automáticamente proveerá de valores `NaN` si alguna de las claves no figura en el mencionado diccionario):


```python
deportes = {"Fútbol": "España",
            "Golf": "Italia",
            "Baloncesto": "Francia",
            "Kárate": "Japón"}
d = pd.Series(deportes, index=["Fútbol", "Golf", "Baloncesto"])
d
```




    Fútbol         España
    Golf           Italia
    Baloncesto    Francia
    dtype: object




```python
d = pd.Series(deportes, index=["Fútbol", "Balonmano", "Golf"])
d
```




    Fútbol       España
    Balonmano       NaN
    Golf         Italia
    dtype: object



## 3. Extracción de elementos en Series {#section-3}

Para empezar, retomemos uno de los últimos ejemplos de la sección anterior:


```python
deportes = {"Fútbol": "España",
            "Golf": "Italia",
            "Baloncesto": "Francia",
            "Kárate": "Japón"}
d = pd.Series(deportes)
d
```




    Fútbol         España
    Golf           Italia
    Baloncesto    Francia
    Kárate          Japón
    dtype: object



Existen cuatro maneras diferentes de acceder a los valores almacenados en `deportes`. Si nos preguntamos a qué país está asociada la etiqueta `"Golf"` y sabemos que almacenamos este registro en segundo lugar, podemos emplear el atributo `iloc`:


```python
d.iloc[1]
```




    'Italia'



No obstante, es difícil recordar el orden en el que introdujimos los datos, y más cuando cierto tiempo ha transcurrido desde entonces. Por ello, es interesante que conozcamos la existencia del atributo `loc`, que nos permite acceder al valor mediante su etiqueta explícita:


```python
d.loc["Golf"]
```




    'Italia'



*Nota técnica*: notemos que `iloc` y `loc` son atributos, por lo que no hemos de utilizar paréntesis `()` cuando los empleamos.

La manera en que están programados los accesos en `pandas` busca conseguir la máxima legibilidad posible. Por ejemplo, si directamente utilizamos el operador de índice `[]` con un valor numérico, `pandas` empleará el atributo `iloc`; mientras que si es otro tipo de valor, recurrirá al atributo `loc`.


```python
d[1]
```




    'Italia'




```python
d["Golf"]
```




    'Italia'



Esta manera de proceder puede ser fuente de complicaciones cuando los índices son, asimismo, valores numéricos. En esta situación, `pandas` no puede determinar directamente si estamos accediendo a un valor vía referencia numérica o mediante etiquetas.


```python
numeros = {90: "Noventa",
           91: "Noventa y uno",
           92: "Noventa y dos",
           93: "Noventa y tres"}
n = pd.Series(numeros)
n
```




    90           Noventa
    91     Noventa y uno
    92     Noventa y dos
    93    Noventa y tres
    dtype: object




```python
n[0]  # No accede al primer elemento, como en las listas. No hay índice etiquetado 0 aquí.
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-20-56e5e6858fee> in <module>
    ----> 1 n[0]  # No accede al primer elemento, como en las listas. No hay índice etiquetado 0 aquí.
    

    ~\Anaconda3\lib\site-packages\pandas\core\series.py in __getitem__(self, key)
        866         key = com.apply_if_callable(key, self)
        867         try:
    --> 868             result = self.index.get_value(self, key)
        869 
        870             if not is_scalar(result):
    

    ~\Anaconda3\lib\site-packages\pandas\core\indexes\base.py in get_value(self, series, key)
       4373         try:
       4374             return self._engine.get_value(s, k,
    -> 4375                                           tz=getattr(series.dtype, 'tz', None))
       4376         except KeyError as e1:
       4377             if len(self) > 0 and (self.holds_integer() or self.is_boolean()):
    

    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_value()
    

    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_value()
    

    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    pandas/_libs/hashtable_class_helper.pxi in pandas._libs.hashtable.Int64HashTable.get_item()
    

    pandas/_libs/hashtable_class_helper.pxi in pandas._libs.hashtable.Int64HashTable.get_item()
    

    KeyError: 0



```python
n.iloc[0]
```

En estos casos, como acabamos de ver arriba, conviene utilizar explícitamente los atributos `iloc` y `loc`.

A continuación, veamos cómo trabajar con los valores de un objeto de tipo `Series`. Por ejemplo, nos puede interesar calcular la suma total de los elementos de una serie numérica de valores en coma flotante, almacenada mediante esta estructura de datos.


```python
s = pd.Series([100.00, 120.00, 101.00, 3.00])
s
```




    0    100.0
    1    120.0
    2    101.0
    3      3.0
    dtype: float64



Un posible enfoque consiste en iterar sobre los elementos de `s` a través de un bucle de tipo `for`:


```python
total = 0
for item in s:
    total += item
print(total)
```

    324.0
    

No obstante, la librería `numpy` dispone de un método que realiza la misma tarea de una manera más eficiente (en consumo de memoria y tiempo):


```python
total = np.sum(s)
print(total)
```

    324.0
    

¿Cómo podemos comprobar que, efectivamente, conviene utilizar las funciones que estas librerías proporcionan, en lugar de utilizar nuestros propios bucles? Llevemos a cabo un pequeño experimento declarando una serie de 10000 números aleatorios (cada uno de ellos comprendido entre 0 y 999) y procediendo a su suma. El *magic command* `%%timeit` nos permitirá acceder al tiempo de computación del proceso, que repetiremos 100 veces para conseguir así un tiempo medio representativo.


```python
s = pd.Series(np.random.randint(0, 1000, 10000))
s.head()  # Imprime los cinco primeros elementos
```




    0    970
    1    887
    2    127
    3     75
    4    170
    dtype: int32




```python
len(s)
```




    10000




```python
%%timeit -n 100
summary = 0
for item in s:
    summary += item
```

    2.58 ms ± 182 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
    


```python
%%timeit -n 100
summary = np.sum(s)
```

    277 µs ± 73.4 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
    

La explicación técnica de este resultado reside en que `numpy` efectúa operaciones algebraicas de manera **vectorizada**, enfoque de actuación mucho más eficiente que realizarlas elemento a elemento, como cuando utilizamos un bucle como el declarado arriba.

No obstante, la diferencia, aún existente, no llega a ser sorprendente. Repliquemos esta manera de proceder analizando ahora otra operación sencilla: sumar dos unidades a cada uno de los elementos de la serie generada. 

Dicha tarea la podemos llevar a cabo directamente mediante el operador incremento correspondiente:


```python
s += 2  # Suma 2 a s, elemento a elemento
s.head()
```




    0    972
    1    889
    2    129
    3     77
    4    172
    dtype: int32



O, en cualquier caso, a través de un bucle de tipo `for`:


```python
for label, value in s.iteritems():
    s.set_value(label, value + 2)  # Produce un deprecated warning 
s.head()
```

    FutureWarning: set_value is deprecated and will be removed in a future release. Please use .at[] or .iat[] accessors instead
      
    




    0    974
    1    891
    2    131
    3     79
    4    174
    dtype: int32



El anterior bloque de código arroja un mensaje (*warning*) avisándonos que la función `set_value()` está en desuso y nos recomienda utilizar los atributos `.at[]` o `iat[]`. Modifiquemos pues el código precedente:


```python
for label, value in s.iteritems():
    s.at[label] = value + 2
s.head()
```




    0    976
    1    893
    2    133
    3     81
    4    176
    dtype: int32



Acto seguido, procedamos a realizar el mencionado experimento:


```python
%%timeit -n 100
s = pd.Series(np.random.randint(0, 1000, 10000))
for label, value in s.iteritems():
    s.at[label] = value + 2
```

    109 ms ± 10.2 ms per loop (mean ± std. dev. of 7 runs, 100 loops each)
    


```python
%%timeit -n 100
s = pd.Series(np.random.randint(0, 1000, 10000))
s += 2
```

    725 µs ± 196 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
    

En resumen, si en algún momento nos encontramos iterando sobre un objeto de tipo `Series`, hemos de deternos y cuestionarnos si estamos llevando a cabo el procedimiento de la manera más adecuada (en términos de eficiencia).

Para finalizar esta sección, veamos algunas maneras de añadir información a un objeto declarado de tipo `Series`. En primer lugar, y de manera muy parecida a como realizamos el proceso cuando trabajamos con diccionarios, utilizando la estructura `s.loc[] = value`:


```python
s = pd.Series([1, 2, 3])
s.loc["Animal"] = "Oso"
s
```




    0           1
    1           2
    2           3
    Animal    Oso
    dtype: object



*Nota*: la librería `pandas` gestiona adecuadamente los índices y valores cuando, como en este caso, son de tipos diferentes (tenemos enteros y cadenas de texto), escogiendo la representación más general para representarlos.

En segundo lugar, la función `append()` resulta de gran utilidad a la hora de ampliar este tipo de estructura de datos. Además, veamos qué sucede cuando existen diferentes valores cuyo índice, en forma de etiqueta, coincide (situación imposible de conseguir cuando trabajamos, por ejemplo, con bases de datos relacionales):


```python
deportes = pd.Series({"Fútbol": "España",
                      "Golf": "Italia",
                      "Baloncesto": "Francia",
                      "Kárate": "Japón"})
paises_balonmano = pd.Series(["Inglaterra", "Alemania", "Rusia", "Colombia"],
                            index=["Balonmano", "Balonmano", "Balonmano", "Balonmano"])
deportes_ampliado = deportes.append(paises_balonmano)
```


```python
deportes
```




    Fútbol         España
    Golf           Italia
    Baloncesto    Francia
    Kárate          Japón
    dtype: object




```python
paises_balonmano
```




    Balonmano    Inglaterra
    Balonmano      Alemania
    Balonmano         Rusia
    Balonmano      Colombia
    dtype: object




```python
deportes_ampliado
```




    Fútbol            España
    Golf              Italia
    Baloncesto       Francia
    Kárate             Japón
    Balonmano     Inglaterra
    Balonmano       Alemania
    Balonmano          Rusia
    Balonmano       Colombia
    dtype: object




```python
deportes_ampliado.loc["Balonmano"]
```




    Balonmano    Inglaterra
    Balonmano      Alemania
    Balonmano         Rusia
    Balonmano      Colombia
    dtype: object



*Notas técnicas*: 

- La función `append()`, así como sucede con otras funciones de esta librería, infiere qué tipo es el más adecuado para representar la nueva estructura generada. En el ejemplo anterior, como todo son cadenas de caracteres, no hay problema alguno. 
- Por otro lado, dicha función no modifica la estructura original, sino que devuelve una nueva, comportamiento que puede resultar un tanto extraño en *Python*, tal y como estamos acostumbrados a modificar objetos. En el ejemplo anterior, tras ejecutar la celda, observamos la variable `deportes` contiene únicamente los datos originales, aunque sobre ella hayamos utilizado el método `append()`. Como podemos observar a continuación, cuando trabajamos con listas dicha función produce un resultado diferente.


```python
lista_original = [1, 2, 3]
lista_nueva = lista_original.append(4)

lista_original
```




    [1, 2, 3, 4]



## 4. La estrutura de datos DataFrame {#section-4}

La estructura de datos `DataFrame` es, posiblemente, la gran protagonista de la librería `pandas` y con la que trabajaremos habitualmente a la hora de llevar a cabo análisis de datos. Se trata de una tabla compuesta por múltiples filas y columnas (conceptualmente estaríamos hablando de un *array* 2-dimensional), donde cada registro posee su propia etiqueta.

Podemos crear un `DataFrame` a partir de un conjunto de `Series` o de diccionarios, donde cada elemento represente una fila de la tabla que deseamos generar:


```python
import pandas as pd

compra_1 = pd.Series({'Nombre': 'Alexis',
                      'Objeto comprado': 'Portátil',
                      'Coste': 622.50})
compra_2 = pd.Series({'Nombre': 'Ana',
                      'Objeto comprado': 'Auriculares',
                      'Coste': 7.50})
compra_3 = pd.Series({'Nombre': 'Marta',
                      'Objeto comprado': 'Comida para gatos',
                      'Coste': 15.25})

df = pd.DataFrame([compra_1, compra_2, compra_3], 
                  index=['Tienda 1', 'Tienda 1', 'Tienda 2'])
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Objeto comprado</th>
      <th>Coste</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda 1</th>
      <td>Alexis</td>
      <td>Portátil</td>
      <td>622.50</td>
    </tr>
    <tr>
      <th>Tienda 1</th>
      <td>Ana</td>
      <td>Auriculares</td>
      <td>7.50</td>
    </tr>
    <tr>
      <th>Tienda 2</th>
      <td>Marta</td>
      <td>Comida para gatos</td>
      <td>15.25</td>
    </tr>
  </tbody>
</table>
</div>



*Nota*: recordemos que no es necesario que las etiquetas asociadas a los registros sean únicas.

De manera similar a como procedíamos en anteriores secciones, podemos extraer información del `DataFrame` utilizando los atributos `iloc` y `loc`. Cabe destacar que, según la cantidad de información extraída, la librería `pandas` colapsa de manera adecuada el tipo de datos resultante. 

Por ejemplo, si extraemos una columna de la tabla, el objeto resultante será de tipo `Series`:


```python
df.loc["Tienda 2"]
```




    Nombre                         Marta
    Objeto comprado    Comida para gatos
    Coste                          15.25
    Name: Tienda 2, dtype: object




```python
type(df.loc["Tienda 2"])
```




    pandas.core.series.Series



De manera similar, podemos extraer información de la tabla utilizando múltiples índices (uno para la fila y otro para la columna). Por ejemplo, podríamos estar interesados en consultar los costes asociados a los productos comprados en `Tienda 1`. Para ello, tecleamos


```python
df.loc["Tienda 1", "Coste"]
```




    Tienda 1    622.5
    Tienda 1      7.5
    Name: Coste, dtype: float64




```python
type(df.loc["Tienda 1", "Coste"])
```




    pandas.core.series.Series



Al tratarse el resultado de un *array* unidimensional, observamos que su tipo se colapsa al de un objeto de tipo `Series`. En cambio, si extraemos una ''subtabla'' de la tabla, el objeto devuelto no varía de tipo y continúa perteneciendo a la clase `DataFrame`:


```python
df.loc["Tienda 1"]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Objeto comprado</th>
      <th>Coste</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda 1</th>
      <td>Alexis</td>
      <td>Portátil</td>
      <td>622.5</td>
    </tr>
    <tr>
      <th>Tienda 1</th>
      <td>Ana</td>
      <td>Auriculares</td>
      <td>7.5</td>
    </tr>
  </tbody>
</table>
</div>




```python
type(df.loc["Tienda 1"])
```




    pandas.core.frame.DataFrame



Finalmente, si extraemos un único valor concreto de la tabla, su tipo también se ve alterado:


```python
df.loc["Tienda 2", "Coste"]
```




    15.25




```python
type(df.loc["Tienda 2", "Coste"])
```




    numpy.float64




```python
df.loc["Tienda 2", "Nombre"]
```




    'Marta'




```python
type(df.loc["Tienda 2", "Nombre"])
```




    str



A continuación, imaginemos que estamos interesados en obtener todos los registros asociados a una columna, `"Coste"` por ejemplo. Una posible estrategia consistiría en trasponer el conjunto de datos y emplear, como antes, el atributo `loc`, ya que los nombres de las columnas pasan a ser los índices de los registros.


```python
df.T
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Tienda 1</th>
      <th>Tienda 1</th>
      <th>Tienda 2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Nombre</th>
      <td>Alexis</td>
      <td>Ana</td>
      <td>Marta</td>
    </tr>
    <tr>
      <th>Objeto comprado</th>
      <td>Portátil</td>
      <td>Auriculares</td>
      <td>Comida para gatos</td>
    </tr>
    <tr>
      <th>Coste</th>
      <td>622.5</td>
      <td>7.5</td>
      <td>15.25</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.T.loc["Coste"]
```




    Tienda 1    622.5
    Tienda 1      7.5
    Tienda 2    15.25
    Name: Coste, dtype: object



Sin embargo, es un tanto tedioso proceder de tal forma. La librería `pandas` permite, directamente, utilizar también los atributos `iloc` y `loc` sobre los nombres de las columnas:


```python
df["Coste"]
```




    Tienda 1    622.50
    Tienda 1      7.50
    Tienda 2     15.25
    Name: Coste, dtype: float64



Además, podemos incluso encadenar operadores de extracción de datos como sigue:


```python
df.loc["Tienda 1"]["Coste"]
```




    Tienda 1    622.5
    Tienda 1      7.5
    Name: Coste, dtype: float64




```python
df.loc["Tienda 2"]["Coste"]
```




    15.25



No obstante, hemos de ser cautos a la hora de proceder de tal manera, pues `pandas` devuelve una copia del objeto `DataFrame`, en lugar de una simple vista, con todos los costes asociados de memoria y tiempo de cálculo que ello conlleva. 

A la hora de realizar consultas, esta peculiaridad no puede parecer muy importante, pero sí puede ser fuente de errores cuando estamos modificando datos de un conjunto de datos.

*Nota*: también podemos utilizar el operador `:` a la hora de extraer información de un conjunto de datos, tal y como estamos habituados a hacerlo cuando trabajamos con listas.


```python
df.loc[:, ["Nombre", "Coste"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Coste</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda 1</th>
      <td>Alexis</td>
      <td>622.50</td>
    </tr>
    <tr>
      <th>Tienda 1</th>
      <td>Ana</td>
      <td>7.50</td>
    </tr>
    <tr>
      <th>Tienda 2</th>
      <td>Marta</td>
      <td>15.25</td>
    </tr>
  </tbody>
</table>
</div>



Acto seguido, veamos cómo descartar datos, acción para la cual la función `drop()` es ciertamente útil:


```python
df.drop("Tienda 1")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Objeto comprado</th>
      <th>Coste</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda 2</th>
      <td>Marta</td>
      <td>Comida para gatos</td>
      <td>15.25</td>
    </tr>
  </tbody>
</table>
</div>



*Nota técnica*: la función `drop()`, como muchas de las implementadas en la librería `pandas`, no modifica el objeto original, sino que devuelve una copia del mismo sobre la cual se ha llevado a cabo la acción de interés. 


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Objeto comprado</th>
      <th>Coste</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda 1</th>
      <td>Alexis</td>
      <td>Portátil</td>
      <td>622.50</td>
    </tr>
    <tr>
      <th>Tienda 1</th>
      <td>Ana</td>
      <td>Auriculares</td>
      <td>7.50</td>
    </tr>
    <tr>
      <th>Tienda 2</th>
      <td>Marta</td>
      <td>Comida para gatos</td>
      <td>15.25</td>
    </tr>
  </tbody>
</table>
</div>



Hagamos una copia del conjunto de datos, utilizando la función `copy()`, y apliquemos después la función `drop()`:


```python
copia_df = df.copy()
copia_df = copia_df.drop("Tienda 1")
copia_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Objeto comprado</th>
      <th>Coste</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda 2</th>
      <td>Marta</td>
      <td>Comida para gatos</td>
      <td>15.25</td>
    </tr>
  </tbody>
</table>
</div>



Por otro lado, cabe comentar que la función `drop()` posee dos interesantes parámetros:

- `inplace`: permite que la actualización de datos se realice sobre el objeto original, en lugar de devolver una copia.
- `axis`: dimensión que se descarta (`0` para filas, `1` para columnas)

Para acceder a más detalles sobre la función, siempre conviene que consultemos su documentación asociada:


```python
copia_df.drop?
```

Adicionalmente, mediante la combinación del operador índice y la instrucción `del` tenemos la posibilidad de descartar datos de nuestra tabla. Dicha combinación altera el objeto inicial en lugar de devolver una copia, por lo que hemos de proceder con cautela en su uso.


```python
del copia_df["Nombre"]
copia_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Objeto comprado</th>
      <th>Coste</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda 2</th>
      <td>Comida para gatos</td>
      <td>15.25</td>
    </tr>
  </tbody>
</table>
</div>



Finalmente, para añadir columnas únicamente hemos de seguir un patrón familiar a estas alturas:


```python
df["Localización"] = None
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Objeto comprado</th>
      <th>Coste</th>
      <th>Localización</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda 1</th>
      <td>Alexis</td>
      <td>Portátil</td>
      <td>622.50</td>
      <td>None</td>
    </tr>
    <tr>
      <th>Tienda 1</th>
      <td>Ana</td>
      <td>Auriculares</td>
      <td>7.50</td>
      <td>None</td>
    </tr>
    <tr>
      <th>Tienda 2</th>
      <td>Marta</td>
      <td>Comida para gatos</td>
      <td>15.25</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
</div>



**Ejercicio**: ¿cómo podríamos aplicar un descuento de un 20% a los artículos de la primera tienda?


```python
df.loc["Tienda 1", "Coste"] *= 0.8
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Objeto comprado</th>
      <th>Coste</th>
      <th>Localización</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda 1</th>
      <td>Alexis</td>
      <td>Portátil</td>
      <td>498.00</td>
      <td>None</td>
    </tr>
    <tr>
      <th>Tienda 1</th>
      <td>Ana</td>
      <td>Auriculares</td>
      <td>6.00</td>
      <td>None</td>
    </tr>
    <tr>
      <th>Tienda 2</th>
      <td>Marta</td>
      <td>Comida para gatos</td>
      <td>15.25</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
</div>



## 5. Lectura de archivos como DataFrame {#section-5}

Habitualmente, a la hora de realizar análisis de datos, importamos el conjunto de datos en un `DataFrame` y luego seleccionamos aquellas que nos resulten de interés para trabajar con ellas.

Como hemos advertido en anteriores secciones, la librería `pandas` acostumbra a devolver ''vistas'' de los `DataFrames` en lugar de copias de los mismos (debido a cuestiones de gestión de memoria y eficiencia en la realización de ciertas operaciones). Por tanto, podemos encontrar que algunas modificaciones que llevemos a cabo pueden tener impacto en el conjunto de datos original y este comportamiento es posible que no nos interese.

Por ejemplo, almacenemos en una variable los costes de los productos pertenecientes a la tabla de la sección anterior:


```python
costes = df["Coste"]
costes
```




    Tienda 1    498.00
    Tienda 1      6.00
    Tienda 2     15.25
    Name: Coste, dtype: float64



Si ahora incrementamos en dos unidades el coste de cada producto, no solo ve alterado su valor la variable `costes`, sino también el conjunto de datos original `df`:


```python
costes += 2
costes
```




    Tienda 1    500.00
    Tienda 1      8.00
    Tienda 2     17.25
    Name: Coste, dtype: float64




```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Objeto comprado</th>
      <th>Coste</th>
      <th>Localización</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Tienda 1</th>
      <td>Alexis</td>
      <td>Portátil</td>
      <td>500.00</td>
      <td>None</td>
    </tr>
    <tr>
      <th>Tienda 1</th>
      <td>Ana</td>
      <td>Auriculares</td>
      <td>8.00</td>
      <td>None</td>
    </tr>
    <tr>
      <th>Tienda 2</th>
      <td>Marta</td>
      <td>Comida para gatos</td>
      <td>17.25</td>
      <td>None</td>
    </tr>
  </tbody>
</table>
</div>



A continuación, veamos cómo importar los contenidos de un archivo, de tipo *CSV*, en una estructura de datos de tipo `DataFrame`. El fichero `olympics.csv` (ubicado en el directorio `data`) registra el número de medallas que cada país ha conseguido en los difirentes tipos de olimpiadas:


```python
df = pd.read_csv("data/olympics.csv")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
      <th>9</th>
      <th>10</th>
      <th>11</th>
      <th>12</th>
      <th>13</th>
      <th>14</th>
      <th>15</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>NaN</td>
      <td>№ Summer</td>
      <td>01 !</td>
      <td>02 !</td>
      <td>03 !</td>
      <td>Total</td>
      <td>№ Winter</td>
      <td>01 !</td>
      <td>02 !</td>
      <td>03 !</td>
      <td>Total</td>
      <td>№ Games</td>
      <td>01 !</td>
      <td>02 !</td>
      <td>03 !</td>
      <td>Combined total</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Afghanistan (AFG)</td>
      <td>13</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria (ALG)</td>
      <td>12</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>15</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Argentina (ARG)</td>
      <td>23</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
      <td>18</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>41</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Armenia (ARM)</td>
      <td>5</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>11</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>



A la vista de la tabla anterior, parece que la primera fila únicamente numera las columnas, resiendo en la segunda los nombres de cabecera de dichas columnas. Por tanto, procederemos a saltar la lectura de la línea inicial, utilizando para ello el parámetro `skiprows`.

Por otro lado, la primera columna contiene los nombres de los distintos países, siendo estos valores perfectos candidatos para conformar los índices de cada uno de los registros. Para conseguir tal característica, simplemente indicamos que la columna de índices es la primera mediante el parámetro `index_col=0`.


```python
df = pd.read_csv("data/olympics.csv", index_col=0, skiprows=1)
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>№ Summer</th>
      <th>01 !</th>
      <th>02 !</th>
      <th>03 !</th>
      <th>Total</th>
      <th>№ Winter</th>
      <th>01 !.1</th>
      <th>02 !.1</th>
      <th>03 !.1</th>
      <th>Total.1</th>
      <th>№ Games</th>
      <th>01 !.2</th>
      <th>02 !.2</th>
      <th>03 !.2</th>
      <th>Combined total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Afghanistan (AFG)</th>
      <td>13</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Algeria (ALG)</th>
      <td>12</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>15</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
    </tr>
    <tr>
      <th>Argentina (ARG)</th>
      <td>23</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
      <td>18</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>41</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
    </tr>
    <tr>
      <th>Armenia (ARM)</th>
      <td>5</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>11</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
    </tr>
    <tr>
      <th>Australasia (ANZ) [ANZ]</th>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.columns
```




    Index(['№ Summer', '01 !', '02 !', '03 !', 'Total', '№ Winter', '01 !.1',
           '02 !.1', '03 !.1', 'Total.1', '№ Games', '01 !.2', '02 !.2', '03 !.2',
           'Combined total'],
          dtype='object')



Acto seguido, encontramos dos detalles curiosos:

- La representación para las medallas de oro, plata y bronce es, cuanto menos, extraña: `01 !`, `02 !` y `03 !`.
- Existen columnas con las mismas etiquetas (las asociadas a los tipos de medallas y a los totales), práctica en absoluto recomendable por dar lugar a confusiones de manera muy sencilla. La librería `pandas` gestiona esta situación incluyendo valores numéricos al final del nombre de las repetidas (`.1`, `.2`, `.3`...) para así poder diferenciarlas.

Podemos bien editar directamente el propio archivo *CSV*, bien modificar las etiquetas conflictivas, desde *Python* con la librería `pandas`, utilizando la función `rename()`:


```python
for col in df.columns:
    if col[:2]=='01':
        df.rename(columns={col:'Gold' + col[4:]}, inplace=True)
    if col[:2]=='02':
        df.rename(columns={col:'Silver' + col[4:]}, inplace=True)
    if col[:2]=='03':
        df.rename(columns={col:'Bronze' + col[4:]}, inplace=True)
    if col[:1]=='№':
        df.rename(columns={col:'#' + col[1:]}, inplace=True) 

df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th># Summer</th>
      <th>Gold</th>
      <th>Silver</th>
      <th>Bronze</th>
      <th>Total</th>
      <th># Winter</th>
      <th>Gold.1</th>
      <th>Silver.1</th>
      <th>Bronze.1</th>
      <th>Total.1</th>
      <th># Games</th>
      <th>Gold.2</th>
      <th>Silver.2</th>
      <th>Bronze.2</th>
      <th>Combined total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Afghanistan (AFG)</th>
      <td>13</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Algeria (ALG)</th>
      <td>12</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>15</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
    </tr>
    <tr>
      <th>Argentina (ARG)</th>
      <td>23</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
      <td>18</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>41</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
    </tr>
    <tr>
      <th>Armenia (ARM)</th>
      <td>5</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>11</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
    </tr>
    <tr>
      <th>Australasia (ANZ) [ANZ]</th>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>



Notemos el uso del parámetro `inplace`, que permite modificar el objeto original, puesto que su valor está declarado como `True`. Por otro lado, hemos de proceder con cautela a la hora de renombrar las columnas para no perder la unicidad durante el proceso, de ahí la justificación de la concatenación `+ col[4:]`.

## 6. Consultas en DataFrame {#section-6}

Antes de abordar cómo realizar consultas en `DataFrame`, hemos de introducir el concepto de *máscara booleana* (*boolean masking*), puesto que esta estrategia es la que permite consultar el conjunto de datos de una manera rápida y eficiente.

La idea es construir un *array* (unidimensional o multidimensional) de valores lógicos `True` o `False`, que luego utilizaremos para extraer la información que nos interese del conjunto de datos.

Por ejemplo, utilizando la tabla de datos que figura en la sección anterior y que recoge el número de medallas obtenidas por cada país en las olimpiadas, podemos estar interesados en consultar qué países han conseguido al menos una medalla de oro en las de verano (recordemos que esta información se almacenaba en la columna `"Gold"`). Si escribimos


```python
df["Gold"] > 0
```




    Afghanistan (AFG)                               False
    Algeria (ALG)                                    True
    Argentina (ARG)                                  True
    Armenia (ARM)                                    True
    Australasia (ANZ) [ANZ]                          True
    Australia (AUS) [AUS] [Z]                        True
    Austria (AUT)                                    True
    Azerbaijan (AZE)                                 True
    Bahamas (BAH)                                    True
    Bahrain (BRN)                                   False
    Barbados (BAR) [BAR]                            False
    Belarus (BLR)                                    True
    Belgium (BEL)                                    True
    Bermuda (BER)                                   False
    Bohemia (BOH) [BOH] [Z]                         False
    Botswana (BOT)                                  False
    Brazil (BRA)                                     True
    British West Indies (BWI) [BWI]                 False
    Bulgaria (BUL) [H]                               True
    Burundi (BDI)                                    True
    Cameroon (CMR)                                   True
    Canada (CAN)                                     True
    Chile (CHI) [I]                                  True
    China (CHN) [CHN]                                True
    Colombia (COL)                                   True
    Costa Rica (CRC)                                 True
    Ivory Coast (CIV) [CIV]                         False
    Croatia (CRO)                                    True
    Cuba (CUB) [Z]                                   True
    Cyprus (CYP)                                    False
                                                    ...  
    Sri Lanka (SRI) [SRI]                           False
    Sudan (SUD)                                     False
    Suriname (SUR) [E]                               True
    Sweden (SWE) [Z]                                 True
    Switzerland (SUI)                                True
    Syria (SYR)                                      True
    Chinese Taipei (TPE) [TPE] [TPE2]                True
    Tajikistan (TJK)                                False
    Tanzania (TAN) [TAN]                            False
    Thailand (THA)                                   True
    Togo (TOG)                                      False
    Tonga (TGA)                                     False
    Trinidad and Tobago (TRI) [TRI]                  True
    Tunisia (TUN)                                    True
    Turkey (TUR)                                     True
    Uganda (UGA)                                     True
    Ukraine (UKR)                                    True
    United Arab Emirates (UAE)                       True
    United States (USA) [P] [Q] [R] [Z]              True
    Uruguay (URU)                                    True
    Uzbekistan (UZB)                                 True
    Venezuela (VEN)                                  True
    Vietnam (VIE)                                   False
    Virgin Islands (ISV)                            False
    Yugoslavia (YUG) [YUG]                           True
    Independent Olympic Participants (IOP) [IOP]    False
    Zambia (ZAM) [ZAM]                              False
    Zimbabwe (ZIM) [ZIM]                             True
    Mixed team (ZZX) [ZZX]                           True
    Totals                                           True
    Name: Gold, Length: 147, dtype: bool



Una vez hemos construido la máscara de valores lógicos (*boolean mask*), ya solo nos resta aplicarla al conjunto de datos original mediante la función `where()`:


```python
solo_oro = df.where(df["Gold"] > 0)
solo_oro.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th># Summer</th>
      <th>Gold</th>
      <th>Silver</th>
      <th>Bronze</th>
      <th>Total</th>
      <th># Winter</th>
      <th>Gold.1</th>
      <th>Silver.1</th>
      <th>Bronze.1</th>
      <th>Total.1</th>
      <th># Games</th>
      <th>Gold.2</th>
      <th>Silver.2</th>
      <th>Bronze.2</th>
      <th>Combined total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Afghanistan (AFG)</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>Algeria (ALG)</th>
      <td>12.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>8.0</td>
      <td>15.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>15.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>8.0</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>Argentina (ARG)</th>
      <td>23.0</td>
      <td>18.0</td>
      <td>24.0</td>
      <td>28.0</td>
      <td>70.0</td>
      <td>18.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>41.0</td>
      <td>18.0</td>
      <td>24.0</td>
      <td>28.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>Armenia (ARM)</th>
      <td>5.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>9.0</td>
      <td>12.0</td>
      <td>6.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>11.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>9.0</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>Australasia (ANZ) [ANZ]</th>
      <td>2.0</td>
      <td>3.0</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>12.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>12.0</td>
    </tr>
  </tbody>
</table>
</div>



Como podemos observar, se conservan todos los registros, pero únicamente existen datos disponibles para aquellos que verifican la condición impuesta, esto es, que han conseguido al menos una medalla de oro en las olimpiadas de verano. En total son


```python
solo_oro["Gold"].count()
```




    100



es decir, 100 países de un total de


```python
df["Gold"].count()
```




    147



147 países que contiene el conjunto de datos original.

Habitualmente, los registros sin información asociada los descartaremos, haciendo uso para ello de la función `dropna()` que, por defecto, actúa sobre las filas (`axis=0`):


```python
solo_oro = solo_oro.dropna()
solo_oro.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th># Summer</th>
      <th>Gold</th>
      <th>Silver</th>
      <th>Bronze</th>
      <th>Total</th>
      <th># Winter</th>
      <th>Gold.1</th>
      <th>Silver.1</th>
      <th>Bronze.1</th>
      <th>Total.1</th>
      <th># Games</th>
      <th>Gold.2</th>
      <th>Silver.2</th>
      <th>Bronze.2</th>
      <th>Combined total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Algeria (ALG)</th>
      <td>12.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>8.0</td>
      <td>15.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>15.0</td>
      <td>5.0</td>
      <td>2.0</td>
      <td>8.0</td>
      <td>15.0</td>
    </tr>
    <tr>
      <th>Argentina (ARG)</th>
      <td>23.0</td>
      <td>18.0</td>
      <td>24.0</td>
      <td>28.0</td>
      <td>70.0</td>
      <td>18.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>41.0</td>
      <td>18.0</td>
      <td>24.0</td>
      <td>28.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>Armenia (ARM)</th>
      <td>5.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>9.0</td>
      <td>12.0</td>
      <td>6.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>11.0</td>
      <td>1.0</td>
      <td>2.0</td>
      <td>9.0</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>Australasia (ANZ) [ANZ]</th>
      <td>2.0</td>
      <td>3.0</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>12.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>2.0</td>
      <td>3.0</td>
      <td>4.0</td>
      <td>5.0</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>Australia (AUS) [AUS] [Z]</th>
      <td>25.0</td>
      <td>139.0</td>
      <td>152.0</td>
      <td>177.0</td>
      <td>468.0</td>
      <td>18.0</td>
      <td>5.0</td>
      <td>3.0</td>
      <td>4.0</td>
      <td>12.0</td>
      <td>43.0</td>
      <td>144.0</td>
      <td>155.0</td>
      <td>181.0</td>
      <td>480.0</td>
    </tr>
  </tbody>
</table>
</div>



Al ser un tipo de acción habitual a la hora de llevar a cabo análisis de datos, los desarrollares de la librería `pandas` han incluido un atajo (mediante el operador índice `[]` al que le suministramos directamente la máscara booleana) para conseguir el mismo efecto de una manera más sencilla y, sobretodo, que destaca por su legibilidad:


```python
solo_oro = df[df["Gold"] > 0]
solo_oro.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th># Summer</th>
      <th>Gold</th>
      <th>Silver</th>
      <th>Bronze</th>
      <th>Total</th>
      <th># Winter</th>
      <th>Gold.1</th>
      <th>Silver.1</th>
      <th>Bronze.1</th>
      <th>Total.1</th>
      <th># Games</th>
      <th>Gold.2</th>
      <th>Silver.2</th>
      <th>Bronze.2</th>
      <th>Combined total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Algeria (ALG)</th>
      <td>12</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>15</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
    </tr>
    <tr>
      <th>Argentina (ARG)</th>
      <td>23</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
      <td>18</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>41</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
    </tr>
    <tr>
      <th>Armenia (ARM)</th>
      <td>5</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>11</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
    </tr>
    <tr>
      <th>Australasia (ANZ) [ANZ]</th>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
    </tr>
    <tr>
      <th>Australia (AUS) [AUS] [Z]</th>
      <td>25</td>
      <td>139</td>
      <td>152</td>
      <td>177</td>
      <td>468</td>
      <td>18</td>
      <td>5</td>
      <td>3</td>
      <td>4</td>
      <td>12</td>
      <td>43</td>
      <td>144</td>
      <td>155</td>
      <td>181</td>
      <td>480</td>
    </tr>
  </tbody>
</table>
</div>



Adicionalmente, podemos encadenar condiciones lógicas para construir consultas más complejas. Por ejemplo, ¿cuántos países han ganado al menos una medalla de oro en las olimpiadas de verano o en las de invierno?


```python
len(df[(df['Gold'] > 0) | (df['Gold.1'] > 0)])
```




    101



Esto es, 101 países. Recordemos que 100 países habían conseguido al menos una medalla de oro en las olimpiadas de verano, por lo que existe un país que ha ganado al menos una medalla de oro en las olimpiadas de invierno, pero ninguna en las de verano. ¿De qué país se trata?


```python
df[(df['Gold.1'] > 0) & (df['Gold'] == 0)]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th># Summer</th>
      <th>Gold</th>
      <th>Silver</th>
      <th>Bronze</th>
      <th>Total</th>
      <th># Winter</th>
      <th>Gold.1</th>
      <th>Silver.1</th>
      <th>Bronze.1</th>
      <th>Total.1</th>
      <th># Games</th>
      <th>Gold.2</th>
      <th>Silver.2</th>
      <th>Bronze.2</th>
      <th>Combined total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Liechtenstein (LIE)</th>
      <td>16</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>18</td>
      <td>2</td>
      <td>2</td>
      <td>5</td>
      <td>9</td>
      <td>34</td>
      <td>2</td>
      <td>2</td>
      <td>5</td>
      <td>9</td>
    </tr>
  </tbody>
</table>
</div>



*Nota técnica*: debido al orden en el que se efectúan las operaciones en *Python* cada máscara booleana debe encerrarse entre paréntesis.

**Ejercicio**: escribe una consulta que devuelva los nombres de las personas que compraron productos cuyo valor es superior a tres dólares.

```python
purchase_1 = pd.Series({'Name': 'Chris',
                        'Item Purchased': 'Dog Food',
                        'Cost': 22.50})
purchase_2 = pd.Series({'Name': 'Kevyn',
                        'Item Purchased': 'Kitty Litter',
                        'Cost': 2.50})
purchase_3 = pd.Series({'Name': 'Vinod',
                        'Item Purchased': 'Bird Seed',
                        'Cost': 5.00})

df2 = pd.DataFrame([purchase_1, purchase_2, purchase_3], index=['Store 1', 'Store 1', 'Store 2'])
```


```python
purchase_1 = pd.Series({'Name': 'Chris',
                        'Item Purchased': 'Dog Food',
                        'Cost': 22.50})
purchase_2 = pd.Series({'Name': 'Kevyn',
                        'Item Purchased': 'Kitty Litter',
                        'Cost': 2.50})
purchase_3 = pd.Series({'Name': 'Vinod',
                        'Item Purchased': 'Bird Seed',
                        'Cost': 5.00})

df2 = pd.DataFrame([purchase_1, purchase_2, purchase_3], 
                  index=['Store 1', 'Store 1', 'Store 2'])

df2[df2["Cost"] > 3]["Name"]
```




    Store 1    Chris
    Store 2    Vinod
    Name: Name, dtype: object



## 7. Índices en DataFrame {#section-7}

Además de las maneras que hemos visto para generar índices en un objeto de tipo `Series` o `DataFrame`, podemos utilizar la función `set_index()`, que toma una lista de columnas y las convierte en índices para el objeto.

Hemos de actuar con cautela, porque la función no almacena el índice actual antes de sobreescribirlo por el nuevo. No obstante, siempre podemos crear una columna adicional en el conjunto de datos, que almacene el índice actual, antes de utilizar la mencionada función.


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th># Summer</th>
      <th>Gold</th>
      <th>Silver</th>
      <th>Bronze</th>
      <th>Total</th>
      <th># Winter</th>
      <th>Gold.1</th>
      <th>Silver.1</th>
      <th>Bronze.1</th>
      <th>Total.1</th>
      <th># Games</th>
      <th>Gold.2</th>
      <th>Silver.2</th>
      <th>Bronze.2</th>
      <th>Combined total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Afghanistan (AFG)</th>
      <td>13</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>Algeria (ALG)</th>
      <td>12</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>15</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
    </tr>
    <tr>
      <th>Argentina (ARG)</th>
      <td>23</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
      <td>18</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>41</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
    </tr>
    <tr>
      <th>Armenia (ARM)</th>
      <td>5</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>11</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
    </tr>
    <tr>
      <th>Australasia (ANZ) [ANZ]</th>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
    </tr>
  </tbody>
</table>
</div>



Imaginemos que deseamos indexar (almacenando previamente en una columna el índice actual por países) la anterior tabla por el número de medallas de oro conseguidas en las olimpiadas de verano:


```python
df["country"] = df.index  # guardamos el índice actual en una columna del conjunto de datos
df = df.set_index("Gold")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th># Summer</th>
      <th>Silver</th>
      <th>Bronze</th>
      <th>Total</th>
      <th># Winter</th>
      <th>Gold.1</th>
      <th>Silver.1</th>
      <th>Bronze.1</th>
      <th>Total.1</th>
      <th># Games</th>
      <th>Gold.2</th>
      <th>Silver.2</th>
      <th>Bronze.2</th>
      <th>Combined total</th>
      <th>country</th>
    </tr>
    <tr>
      <th>Gold</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>13</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>Afghanistan (AFG)</td>
    </tr>
    <tr>
      <th>5</th>
      <td>12</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>15</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
      <td>Algeria (ALG)</td>
    </tr>
    <tr>
      <th>18</th>
      <td>23</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
      <td>18</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>41</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
      <td>Argentina (ARG)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>11</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
      <td>Armenia (ARM)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
      <td>Australasia (ANZ) [ANZ]</td>
    </tr>
  </tbody>
</table>
</div>



Por otro lado, podemos deshacernos directamente del índice asignado sin más que emplear la función `reset_index()`, que almacena el actual en una columna del conjunto de datos (no en el orden que antes que estaba declarado) y genera un índice numérico nuevo:


```python
df = df.reset_index()
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Gold</th>
      <th># Summer</th>
      <th>Silver</th>
      <th>Bronze</th>
      <th>Total</th>
      <th># Winter</th>
      <th>Gold.1</th>
      <th>Silver.1</th>
      <th>Bronze.1</th>
      <th>Total.1</th>
      <th># Games</th>
      <th>Gold.2</th>
      <th>Silver.2</th>
      <th>Bronze.2</th>
      <th>Combined total</th>
      <th>country</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>13</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>2</td>
      <td>Afghanistan (AFG)</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>12</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
      <td>3</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>15</td>
      <td>5</td>
      <td>2</td>
      <td>8</td>
      <td>15</td>
      <td>Algeria (ALG)</td>
    </tr>
    <tr>
      <th>2</th>
      <td>18</td>
      <td>23</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
      <td>18</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>41</td>
      <td>18</td>
      <td>24</td>
      <td>28</td>
      <td>70</td>
      <td>Argentina (ARG)</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>5</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
      <td>6</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>11</td>
      <td>1</td>
      <td>2</td>
      <td>9</td>
      <td>12</td>
      <td>Armenia (ARM)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3</td>
      <td>2</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>12</td>
      <td>Australasia (ANZ) [ANZ]</td>
    </tr>
  </tbody>
</table>
</div>



A continuación, veamos una característica ciertamente útil de la librería `pandas`: permite la existencia de múltiples índices (pasando una lista con varios elementos a la función `set_index()`).

Para ver en acción esta funcionalidad, analicemos datos de censo, que suelen estar divididos por estado y ciudad, posibilitando así ver en acción múltiples índices:


```python
df = pd.read_csv("data/census.csv")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SUMLEV</th>
      <th>REGION</th>
      <th>DIVISION</th>
      <th>STATE</th>
      <th>COUNTY</th>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th>CENSUS2010POP</th>
      <th>ESTIMATESBASE2010</th>
      <th>POPESTIMATE2010</th>
      <th>...</th>
      <th>RDOMESTICMIG2011</th>
      <th>RDOMESTICMIG2012</th>
      <th>RDOMESTICMIG2013</th>
      <th>RDOMESTICMIG2014</th>
      <th>RDOMESTICMIG2015</th>
      <th>RNETMIG2011</th>
      <th>RNETMIG2012</th>
      <th>RNETMIG2013</th>
      <th>RNETMIG2014</th>
      <th>RNETMIG2015</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>40</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>0</td>
      <td>Alabama</td>
      <td>Alabama</td>
      <td>4779736</td>
      <td>4780127</td>
      <td>4785161</td>
      <td>...</td>
      <td>0.002295</td>
      <td>-0.193196</td>
      <td>0.381066</td>
      <td>0.582002</td>
      <td>-0.467369</td>
      <td>1.030015</td>
      <td>0.826644</td>
      <td>1.383282</td>
      <td>1.724718</td>
      <td>0.712594</td>
    </tr>
    <tr>
      <th>1</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>1</td>
      <td>Alabama</td>
      <td>Autauga County</td>
      <td>54571</td>
      <td>54571</td>
      <td>54660</td>
      <td>...</td>
      <td>7.242091</td>
      <td>-2.915927</td>
      <td>-3.012349</td>
      <td>2.265971</td>
      <td>-2.530799</td>
      <td>7.606016</td>
      <td>-2.626146</td>
      <td>-2.722002</td>
      <td>2.592270</td>
      <td>-2.187333</td>
    </tr>
    <tr>
      <th>2</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>3</td>
      <td>Alabama</td>
      <td>Baldwin County</td>
      <td>182265</td>
      <td>182265</td>
      <td>183193</td>
      <td>...</td>
      <td>14.832960</td>
      <td>17.647293</td>
      <td>21.845705</td>
      <td>19.243287</td>
      <td>17.197872</td>
      <td>15.844176</td>
      <td>18.559627</td>
      <td>22.727626</td>
      <td>20.317142</td>
      <td>18.293499</td>
    </tr>
    <tr>
      <th>3</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>5</td>
      <td>Alabama</td>
      <td>Barbour County</td>
      <td>27457</td>
      <td>27457</td>
      <td>27341</td>
      <td>...</td>
      <td>-4.728132</td>
      <td>-2.500690</td>
      <td>-7.056824</td>
      <td>-3.904217</td>
      <td>-10.543299</td>
      <td>-4.874741</td>
      <td>-2.758113</td>
      <td>-7.167664</td>
      <td>-3.978583</td>
      <td>-10.543299</td>
    </tr>
    <tr>
      <th>4</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>7</td>
      <td>Alabama</td>
      <td>Bibb County</td>
      <td>22915</td>
      <td>22919</td>
      <td>22861</td>
      <td>...</td>
      <td>-5.527043</td>
      <td>-5.068871</td>
      <td>-6.201001</td>
      <td>-0.177537</td>
      <td>0.177258</td>
      <td>-5.088389</td>
      <td>-4.363636</td>
      <td>-5.403729</td>
      <td>0.754533</td>
      <td>1.107861</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 100 columns</p>
</div>




```python
df["SUMLEV"].unique()
```




    array([40, 50], dtype=int64)



Mediante la función `unique()` tenemos acceso a un listado con los diferentes valores recogidos en una columna concreta del conjunto de datos. Por ejemplo, para `SUMLEV` encontramos únicamente dos valores distintos, `40` y `50`, según las estadísticas de resumen se hayan proporcionado a nivel de estado o de condado.

Quedemos con estas últimas aplicando una máscara booleana adecuada:


```python
df = df[df["SUMLEV"] == 50]
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SUMLEV</th>
      <th>REGION</th>
      <th>DIVISION</th>
      <th>STATE</th>
      <th>COUNTY</th>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th>CENSUS2010POP</th>
      <th>ESTIMATESBASE2010</th>
      <th>POPESTIMATE2010</th>
      <th>...</th>
      <th>RDOMESTICMIG2011</th>
      <th>RDOMESTICMIG2012</th>
      <th>RDOMESTICMIG2013</th>
      <th>RDOMESTICMIG2014</th>
      <th>RDOMESTICMIG2015</th>
      <th>RNETMIG2011</th>
      <th>RNETMIG2012</th>
      <th>RNETMIG2013</th>
      <th>RNETMIG2014</th>
      <th>RNETMIG2015</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>1</td>
      <td>Alabama</td>
      <td>Autauga County</td>
      <td>54571</td>
      <td>54571</td>
      <td>54660</td>
      <td>...</td>
      <td>7.242091</td>
      <td>-2.915927</td>
      <td>-3.012349</td>
      <td>2.265971</td>
      <td>-2.530799</td>
      <td>7.606016</td>
      <td>-2.626146</td>
      <td>-2.722002</td>
      <td>2.592270</td>
      <td>-2.187333</td>
    </tr>
    <tr>
      <th>2</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>3</td>
      <td>Alabama</td>
      <td>Baldwin County</td>
      <td>182265</td>
      <td>182265</td>
      <td>183193</td>
      <td>...</td>
      <td>14.832960</td>
      <td>17.647293</td>
      <td>21.845705</td>
      <td>19.243287</td>
      <td>17.197872</td>
      <td>15.844176</td>
      <td>18.559627</td>
      <td>22.727626</td>
      <td>20.317142</td>
      <td>18.293499</td>
    </tr>
    <tr>
      <th>3</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>5</td>
      <td>Alabama</td>
      <td>Barbour County</td>
      <td>27457</td>
      <td>27457</td>
      <td>27341</td>
      <td>...</td>
      <td>-4.728132</td>
      <td>-2.500690</td>
      <td>-7.056824</td>
      <td>-3.904217</td>
      <td>-10.543299</td>
      <td>-4.874741</td>
      <td>-2.758113</td>
      <td>-7.167664</td>
      <td>-3.978583</td>
      <td>-10.543299</td>
    </tr>
    <tr>
      <th>4</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>7</td>
      <td>Alabama</td>
      <td>Bibb County</td>
      <td>22915</td>
      <td>22919</td>
      <td>22861</td>
      <td>...</td>
      <td>-5.527043</td>
      <td>-5.068871</td>
      <td>-6.201001</td>
      <td>-0.177537</td>
      <td>0.177258</td>
      <td>-5.088389</td>
      <td>-4.363636</td>
      <td>-5.403729</td>
      <td>0.754533</td>
      <td>1.107861</td>
    </tr>
    <tr>
      <th>5</th>
      <td>50</td>
      <td>3</td>
      <td>6</td>
      <td>1</td>
      <td>9</td>
      <td>Alabama</td>
      <td>Blount County</td>
      <td>57322</td>
      <td>57322</td>
      <td>57373</td>
      <td>...</td>
      <td>1.807375</td>
      <td>-1.177622</td>
      <td>-1.748766</td>
      <td>-2.062535</td>
      <td>-1.369970</td>
      <td>1.859511</td>
      <td>-0.848580</td>
      <td>-1.402476</td>
      <td>-1.577232</td>
      <td>-0.884411</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 100 columns</p>
</div>



Acto seguido, para trabajar con una tabla algo más manejable, restrinjamos sus columnas a nacimientos y estimaciones para la población, además de conservar también el nombre del estado y la correspondiente ciudad:


```python
columns_to_keep = ['STNAME',
                   'CTYNAME',
                   'BIRTHS2010',
                   'BIRTHS2011',
                   'BIRTHS2012',
                   'BIRTHS2013',
                   'BIRTHS2014',
                   'BIRTHS2015',
                   'POPESTIMATE2010',
                   'POPESTIMATE2011',
                   'POPESTIMATE2012',
                   'POPESTIMATE2013',
                   'POPESTIMATE2014',
                   'POPESTIMATE2015']
df = df[columns_to_keep]
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th>BIRTHS2010</th>
      <th>BIRTHS2011</th>
      <th>BIRTHS2012</th>
      <th>BIRTHS2013</th>
      <th>BIRTHS2014</th>
      <th>BIRTHS2015</th>
      <th>POPESTIMATE2010</th>
      <th>POPESTIMATE2011</th>
      <th>POPESTIMATE2012</th>
      <th>POPESTIMATE2013</th>
      <th>POPESTIMATE2014</th>
      <th>POPESTIMATE2015</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Alabama</td>
      <td>Autauga County</td>
      <td>151</td>
      <td>636</td>
      <td>615</td>
      <td>574</td>
      <td>623</td>
      <td>600</td>
      <td>54660</td>
      <td>55253</td>
      <td>55175</td>
      <td>55038</td>
      <td>55290</td>
      <td>55347</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Alabama</td>
      <td>Baldwin County</td>
      <td>517</td>
      <td>2187</td>
      <td>2092</td>
      <td>2160</td>
      <td>2186</td>
      <td>2240</td>
      <td>183193</td>
      <td>186659</td>
      <td>190396</td>
      <td>195126</td>
      <td>199713</td>
      <td>203709</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Alabama</td>
      <td>Barbour County</td>
      <td>70</td>
      <td>335</td>
      <td>300</td>
      <td>283</td>
      <td>260</td>
      <td>269</td>
      <td>27341</td>
      <td>27226</td>
      <td>27159</td>
      <td>26973</td>
      <td>26815</td>
      <td>26489</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Alabama</td>
      <td>Bibb County</td>
      <td>44</td>
      <td>266</td>
      <td>245</td>
      <td>259</td>
      <td>247</td>
      <td>253</td>
      <td>22861</td>
      <td>22733</td>
      <td>22642</td>
      <td>22512</td>
      <td>22549</td>
      <td>22583</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Alabama</td>
      <td>Blount County</td>
      <td>183</td>
      <td>744</td>
      <td>710</td>
      <td>646</td>
      <td>618</td>
      <td>603</td>
      <td>57373</td>
      <td>57711</td>
      <td>57776</td>
      <td>57734</td>
      <td>57658</td>
      <td>57673</td>
    </tr>
  </tbody>
</table>
</div>



A continuación, observamos que la estructura del conjunto de datos admite, de manera ideal, dos índices: uno correspondiente al nombre del estado y otro al de la ciudad. Utilicemos adecuadamente la función `set_index()` para conseguir tal característica:


```python
df = df.set_index(["STNAME", "CTYNAME"])
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>BIRTHS2010</th>
      <th>BIRTHS2011</th>
      <th>BIRTHS2012</th>
      <th>BIRTHS2013</th>
      <th>BIRTHS2014</th>
      <th>BIRTHS2015</th>
      <th>POPESTIMATE2010</th>
      <th>POPESTIMATE2011</th>
      <th>POPESTIMATE2012</th>
      <th>POPESTIMATE2013</th>
      <th>POPESTIMATE2014</th>
      <th>POPESTIMATE2015</th>
    </tr>
    <tr>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="5" valign="top">Alabama</th>
      <th>Autauga County</th>
      <td>151</td>
      <td>636</td>
      <td>615</td>
      <td>574</td>
      <td>623</td>
      <td>600</td>
      <td>54660</td>
      <td>55253</td>
      <td>55175</td>
      <td>55038</td>
      <td>55290</td>
      <td>55347</td>
    </tr>
    <tr>
      <th>Baldwin County</th>
      <td>517</td>
      <td>2187</td>
      <td>2092</td>
      <td>2160</td>
      <td>2186</td>
      <td>2240</td>
      <td>183193</td>
      <td>186659</td>
      <td>190396</td>
      <td>195126</td>
      <td>199713</td>
      <td>203709</td>
    </tr>
    <tr>
      <th>Barbour County</th>
      <td>70</td>
      <td>335</td>
      <td>300</td>
      <td>283</td>
      <td>260</td>
      <td>269</td>
      <td>27341</td>
      <td>27226</td>
      <td>27159</td>
      <td>26973</td>
      <td>26815</td>
      <td>26489</td>
    </tr>
    <tr>
      <th>Bibb County</th>
      <td>44</td>
      <td>266</td>
      <td>245</td>
      <td>259</td>
      <td>247</td>
      <td>253</td>
      <td>22861</td>
      <td>22733</td>
      <td>22642</td>
      <td>22512</td>
      <td>22549</td>
      <td>22583</td>
    </tr>
    <tr>
      <th>Blount County</th>
      <td>183</td>
      <td>744</td>
      <td>710</td>
      <td>646</td>
      <td>618</td>
      <td>603</td>
      <td>57373</td>
      <td>57711</td>
      <td>57776</td>
      <td>57734</td>
      <td>57658</td>
      <td>57673</td>
    </tr>
  </tbody>
</table>
</div>



Ahora, para consultar, por ejemplo, los datos de *Washtenaw County*, hemos de pasar al atributo `loc` también el valor del estado donde se encuentra dicha ciudad, *Michigan*, y respetando el orden declarado arriba en el interior de la función `set_index()`(estado, ciudad).


```python
df.loc["Michigan", "Washtenaw County"]
```




    BIRTHS2010            977
    BIRTHS2011           3826
    BIRTHS2012           3780
    BIRTHS2013           3662
    BIRTHS2014           3683
    BIRTHS2015           3709
    POPESTIMATE2010    345563
    POPESTIMATE2011    349048
    POPESTIMATE2012    351213
    POPESTIMATE2013    354289
    POPESTIMATE2014    357029
    POPESTIMATE2015    358880
    Name: (Michigan, Washtenaw County), dtype: int64



De esta manera, generar tablas comparativas entre diferentes ciudades de interés es sumamente sencillo:


```python
df.loc[[("Michigan", "Washtenaw County"),
        ("Michigan", "Wayne County")]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>BIRTHS2010</th>
      <th>BIRTHS2011</th>
      <th>BIRTHS2012</th>
      <th>BIRTHS2013</th>
      <th>BIRTHS2014</th>
      <th>BIRTHS2015</th>
      <th>POPESTIMATE2010</th>
      <th>POPESTIMATE2011</th>
      <th>POPESTIMATE2012</th>
      <th>POPESTIMATE2013</th>
      <th>POPESTIMATE2014</th>
      <th>POPESTIMATE2015</th>
    </tr>
    <tr>
      <th>STNAME</th>
      <th>CTYNAME</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">Michigan</th>
      <th>Washtenaw County</th>
      <td>977</td>
      <td>3826</td>
      <td>3780</td>
      <td>3662</td>
      <td>3683</td>
      <td>3709</td>
      <td>345563</td>
      <td>349048</td>
      <td>351213</td>
      <td>354289</td>
      <td>357029</td>
      <td>358880</td>
    </tr>
    <tr>
      <th>Wayne County</th>
      <td>5918</td>
      <td>23819</td>
      <td>23270</td>
      <td>23377</td>
      <td>23607</td>
      <td>23586</td>
      <td>1815199</td>
      <td>1801273</td>
      <td>1792514</td>
      <td>1775713</td>
      <td>1766008</td>
      <td>1759335</td>
    </tr>
  </tbody>
</table>
</div>



Finalmente, el concepto de índices múltiples no se restringe únicamente a las filas, sino que también es posible obtener esta característica para las columnas. Basta trasponer el conjunto de datos (mediante el atributo `T`) y utilizar adecuadamente la función `set_index()`.

**Ejercicio**: indexa los registros de compras del siguiente `DataFrama` jerárquicamente, primero por tienda y luego por persona. Designa dichos índices como `"Location"` y `"Nombre"`. Después, añade un nuevo registro a la tabla con el siguiente valor:

`Name: 'Kevyn', Item Purchased: 'Kitty Food', Cost: 3.00 Location: 'Store 2'`

```python
purchase_1 = pd.Series({'Name': 'Chris',
                        'Item Purchased': 'Dog Food',
                        'Cost': 22.50})
purchase_2 = pd.Series({'Name': 'Kevyn',
                        'Item Purchased': 'Kitty Litter',
                        'Cost': 2.50})
purchase_3 = pd.Series({'Name': 'Vinod',
                        'Item Purchased': 'Bird Seed',
                        'Cost': 5.00})

df = pd.DataFrame([purchase_1, purchase_2, purchase_3], index=['Store 1', 'Store 1', 'Store 2'])
```


```python
purchase_1 = pd.Series({'Name': 'Chris',
                        'Item Purchased': 'Dog Food',
                        'Cost': 22.50})
purchase_2 = pd.Series({'Name': 'Kevyn',
                        'Item Purchased': 'Kitty Litter',
                        'Cost': 2.50})
purchase_3 = pd.Series({'Name': 'Vinod',
                        'Item Purchased': 'Bird Seed',
                        'Cost': 5.00})

df = pd.DataFrame([purchase_1, purchase_2, purchase_3], 
                  index=['Store 1', 'Store 1', 'Store 2'])


df = df.set_index([df.index, 'Name'])
df.index.names = ['Location', 'Name']
df = df.append(pd.Series(data={'Cost': 3.00, 
                               'Item Purchased': 'Kitty Food'}, 
                         name=('Store 2', 'Kevyn')))
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Item Purchased</th>
      <th>Cost</th>
    </tr>
    <tr>
      <th>Location</th>
      <th>Name</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">Store 1</th>
      <th>Chris</th>
      <td>Dog Food</td>
      <td>22.5</td>
    </tr>
    <tr>
      <th>Kevyn</th>
      <td>Kitty Litter</td>
      <td>2.5</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">Store 2</th>
      <th>Vinod</th>
      <td>Bird Seed</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>Kevyn</th>
      <td>Kitty Food</td>
      <td>3.0</td>
    </tr>
  </tbody>
</table>
</div>



## 8. Valores perdidos {#section-8}

Dado que es bastante frecuente encontrar valores perdidos en conjuntos de datos, veamos cómo podemos gestionarlos con la librería `pandas`.

Para empezar, importemos un conjunto de datos que registra la actividad de visualización de vídeos de algunos estudiantes en una plataforma de aprendizaje en línea.


```python
import pandas as pd

df = pd.read_csv("data/log.csv")
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>time</th>
      <th>user</th>
      <th>video</th>
      <th>playback position</th>
      <th>paused</th>
      <th>volume</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1469974424</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>5</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1469974454</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>6</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1469974544</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>9</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1469974574</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>10</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1469977514</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1469977544</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1469977574</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1469977604</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1469974604</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>11</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1469974694</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>14</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>10</th>
      <td>1469974724</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>15</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>11</th>
      <td>1469974454</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>24</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>12</th>
      <td>1469974524</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>25</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13</th>
      <td>1469974424</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>23</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>1469974554</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>26</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15</th>
      <td>1469974624</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>27</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>16</th>
      <td>1469974654</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>28</td>
      <td>NaN</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>1469974724</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>29</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>18</th>
      <td>1469974484</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>7</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>19</th>
      <td>1469974514</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>8</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>20</th>
      <td>1469974754</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>21</th>
      <td>1469974824</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>31</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>22</th>
      <td>1469974854</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>32</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>23</th>
      <td>1469974924</td>
      <td>sue</td>
      <td>advanced.html</td>
      <td>33</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>24</th>
      <td>1469977424</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>True</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>25</th>
      <td>1469977454</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>26</th>
      <td>1469977484</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>27</th>
      <td>1469977634</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>28</th>
      <td>1469977664</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>29</th>
      <td>1469974634</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>12</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>30</th>
      <td>1469974664</td>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>13</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>31</th>
      <td>1469977694</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>32</th>
      <td>1469977724</td>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



La columna `time` registra, respecto a *Epoch*, cuándo se accedió a un determinado vídeo por un usuario concreto (columnas `video` y `user`). Además, tenemos información sobre qué momento del vídeo está visualizando el estudiante (`playback position`), el volumen (`volume`) y si está pausado dicho recurso (`paused`).

Podemos observar que existe gran cantidad de valores perdidos en este conjunto de datos. Ello se explica porque el sistema, si no hay cambio significativo en el estado de la información de cierta columna, simplemente inserta `NaN` como registro.

Una útil función, para trabajar con valores perdidos, que incorpora la librería `pandas` es `fillna()`, que en su parámetro `method` nos permite, por ejemplo, asignar a un valor perdido el valor existente en el registro anterior (`method=ffil`) o en el posterior (`method=bfill`).


```python
df.fillna?
```

No obstante, para aplicar los anteriores métodos, hemos de ordenar el conjunto de datos previamente. Para ello, tecleamos:


```python
df = df.set_index("time")
df = df.sort_index()
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>user</th>
      <th>video</th>
      <th>playback position</th>
      <th>paused</th>
      <th>volume</th>
    </tr>
    <tr>
      <th>time</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1469974424</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>5</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1469974424</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>23</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1469974454</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>6</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974454</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>24</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974484</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>7</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974514</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>8</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974524</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>25</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974544</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>9</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974554</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>26</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974574</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>10</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974604</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>11</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974624</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>27</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974634</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>12</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974654</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>28</td>
      <td>NaN</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>1469974664</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>13</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974694</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>14</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974724</th>
      <td>cheryl</td>
      <td>intro.html</td>
      <td>15</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974724</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>29</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974754</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974824</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>31</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974854</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>32</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974924</th>
      <td>sue</td>
      <td>advanced.html</td>
      <td>33</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977424</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>True</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1469977454</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977484</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977514</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977544</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977574</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977604</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977634</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977664</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977694</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977724</th>
      <td>bob</td>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Ahora bien, examinando el resultado, apreciamos que, en ocasiones, dos usuarios utilizan el sistema al mismo tiempo (situación habitual en grandes plataformas de aprendizaje en línea). Por tanto, en este caso particular, utilizar múltiples índices es una buena idea.


```python
df = df.reset_index()
df = df.set_index(["time", "user"])
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>video</th>
      <th>playback position</th>
      <th>paused</th>
      <th>volume</th>
    </tr>
    <tr>
      <th>time</th>
      <th>user</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">1469974424</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>5</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>sue</th>
      <td>advanced.html</td>
      <td>23</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">1469974454</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>6</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>sue</th>
      <td>advanced.html</td>
      <td>24</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974484</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>7</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974514</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>8</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974524</th>
      <th>sue</th>
      <td>advanced.html</td>
      <td>25</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974544</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>9</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974554</th>
      <th>sue</th>
      <td>advanced.html</td>
      <td>26</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974574</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>10</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974604</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>11</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974624</th>
      <th>sue</th>
      <td>advanced.html</td>
      <td>27</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974634</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>12</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974654</th>
      <th>sue</th>
      <td>advanced.html</td>
      <td>28</td>
      <td>NaN</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>1469974664</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>13</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974694</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>14</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">1469974724</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>15</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>sue</th>
      <td>advanced.html</td>
      <td>29</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974754</th>
      <th>sue</th>
      <td>advanced.html</td>
      <td>30</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974824</th>
      <th>sue</th>
      <td>advanced.html</td>
      <td>31</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974854</th>
      <th>sue</th>
      <td>advanced.html</td>
      <td>32</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469974924</th>
      <th>sue</th>
      <td>advanced.html</td>
      <td>33</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977424</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>True</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1469977454</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977484</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977514</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977544</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977574</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977604</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977634</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977664</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977694</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1469977724</th>
      <th>bob</th>
      <td>intro.html</td>
      <td>1</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



Acto seguido, utilizamos la función `fillna()`, pasándole como argumento el valor `"ffill"` al parámetro `method`.


```python
df = df.fillna(method="ffill")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>video</th>
      <th>playback position</th>
      <th>paused</th>
      <th>volume</th>
    </tr>
    <tr>
      <th>time</th>
      <th>user</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">1469974424</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>5</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>sue</th>
      <td>advanced.html</td>
      <td>23</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">1469974454</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>6</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>sue</th>
      <td>advanced.html</td>
      <td>24</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>1469974484</th>
      <th>cheryl</th>
      <td>intro.html</td>
      <td>7</td>
      <td>False</td>
      <td>10.0</td>
    </tr>
  </tbody>
</table>
</div>



*Nota*: muchas funciones, por defecto, ignoran los valores perdidos a la hora de realizar cálculos. Hemos de proceder pues con cautela si este comportamiento no es el que nos interesa.
