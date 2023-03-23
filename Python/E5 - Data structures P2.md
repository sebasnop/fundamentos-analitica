# Ep 05: Python: Estructuras de datos (Parte 2)

[Ep 05: Python: Estructuras de datos (Parte 2)](https://jdvelasq.github.io/courses/modulos/python/05%20estructuras%20de%20datos%202/_index.html#prog-en-python-ep-05-estructuras-de-datos-2)

&nbsp;

---
&nbsp;

## Tabla de contenidos

- [Ep 05: Python: Estructuras de datos (Parte 2)](#ep-05-python-estructuras-de-datos-parte-2)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Tuplas](#tuplas)
  - [Conjuntos](#conjuntos)
    - [Métodos Conjuntos](#métodos-conjuntos)
    - [Operaciones Conjuntos](#operaciones-conjuntos)
      - [Diferencia](#diferencia)
      - [Unión](#unión)
      - [Intersección](#intersección)
      - [Unión menos intersección](#unión-menos-intersección)
      - [Pertenencia](#pertenencia)
  - [Diccionarios](#diccionarios)
    - [Métodos Diccionarios](#métodos-diccionarios)
    - [Operaciones Diccionarios](#operaciones-diccionarios)
  - [Iteradores](#iteradores)
    - [Concepto](#concepto)
    - [Interpretación](#interpretación)
    - [Práctica](#práctica)
  - [Enumerate](#enumerate)
  - [Zip](#zip)
    - [Uso de zip con \*](#uso-de-zip-con-)
    - [Uso más común](#uso-más-común)
    - [Unzip](#unzip)
  - [Comprehension](#comprehension)
    - [Lista usando for(), map() y comprehension](#lista-usando-for-map-y-comprehension)
    - [List Comprehension](#list-comprehension)
    - [Dict Comprehension](#dict-comprehension)
    - [Generator](#generator)
      - [Utilidad de un generador](#utilidad-de-un-generador)
      - [Cómo se construyen](#cómo-se-construyen)
      - [Lectura de datos](#lectura-de-datos)
  - [Expresiones regulares](#expresiones-regulares)

&nbsp;

---
&nbsp;

## Tuplas

Una tupla es una secuencia de elementos separados por comas.

Son muy similares a las listas, pero las tuplas son inmutables.

Los elementos de la tupla no se pueden agregar ni eliminar una vez creados.

```python
tupla_1 = tuple()
tupla_2 = ()
tupla_3 = 12345, 54321, "hello!"
tupla_4 = tuple((12345, 54321, "hello!"))
```

&nbsp;

---
&nbsp;

## Conjuntos

Estructura de datos no ordenada cuyos elementos no se repiten.

```python
set_a = {"a", "a", "b", "c", "d", "d", "d"}
set_a
```

```console
{'a', 'b', 'c', 'd'}
```

### Métodos Conjuntos

- `add`
  
  Ingresar un elemento al conjunto.
  
- `discard`
  
  Eliminar un elemento especificado del conjunto.

- `pop`
  
  Eliminar algún elemento del conjunto.
  
- `update`
  
  Agregar elementos de un conjunto a otro. Conserva el cambio.

- `difference`
  
  Elementos de un conjunto que no están en otro.
  
- `union`
  
  Como `update` pero no conserva los cambios.
  
- `intersection`

  Elementos en común entre conjuntos.  

### Operaciones Conjuntos

```python
set_a = {0, 1, 2, 3, 4, 5}
set_b = {3, 4, 5, 6, 7, 8}
```

#### Diferencia

```python
set_a - set_b
```

#### Unión

```python
set_a | set_b
```

#### Intersección

```python
set_a & set_b
```

#### Unión menos intersección

```python
set_a ^ set_b
```

```console
{0, 1, 2, 6, 7, 8}
```

#### Pertenencia

```python
"a" in set_a # False
```

&nbsp;

---
&nbsp;

## Diccionarios

Creación de diccionarios

```python
dict_1 = {}

dict_2 = {"b": 2, "a": 1}

dict_3 = dict(
    [
        ("d", 4),
        ("a", 1),
        ("b", 2),
    ]
)

dict_4 = dict(a=1, b=2, c=3)
```

Creación de un nuevo elemento (o reemplazo si ya existía)

```python
dict_1["c"] = 3
```

Obtener valor a partir de su clave

```python
dict_1["b"] # 2
```

Borrado de un elemento del diccionario

```python
del dict_1["b"]
```

Las llaves y los valores pueden ser datos complejos

```python
complex_dict = {
    (0, 0): [],
    (0, 1): [0, 1, 2],
    (1, 0): [3, 4, 5],
    (1, 1): [6, 7, 8],
}
```

Extracción de un elemento de un valor complejo

```python
complex_dict[(1, 1)][1] # 7
```

### Métodos Diccionarios

- `keys`
  
  Lista las claves.

- `items`
  
  Lista los pares

- `get`
  
  Obtiene un valor dada una clave. Permite asignar un valor por defecto en caso de que no se encuentre la clave en el diccionario.

  ```python
  dict_1.get(key, "Valor por defecto")
  ```

- `update`

  Fusiona diccionarios.

  Si hay una clave repetida en ambos diccionarios, la clave toma el valor del diccionario pasado como argumento del `update`.
  
- `pop`
  
  Elimina un par ingresando su clave.

### Operaciones Diccionarios

- Pertenencia

  ```python
  "a" in dict_1 # False
  "a" not in dict_1 # True
  ```
  
- Unión
  
  Dados los diccionarios:

  ```python
  dict_a = {
      0: "a",
      1: "b",
      2: "c",
  }

  dict_b = {
      2: "CC",
      3: "DD",
      4: "EE",
  }
  ```

  La unión de estos se ejecuta como se muestra a continuación, donde el orden de los argumentos importa:

  ```python
  # Note que se reemplaza el valor para la clave 2 en dict_a
  {**dict_a, **dict_b}
  ```

  ```console
  {0: 'a', 1: 'b', 2: 'CC', 3: 'DD', 4: 'EE'}
  ```

  ```python
  # Note que se reemplaza el valor para la clave 2 en dict_b
  {**dict_b, **dict_a}
  ```

  ```console
  {2: 'c', 3: 'DD', 4: 'EE', 0: 'a', 1: 'b'}
  ```

&nbsp;

---
&nbsp;

## Iteradores

### Concepto

Un iterador es un objeto que contiene un número contable de valores.

Es un objeto sobre el que se puede iterar, lo que significa que puede recorrer todos los valores.

En Python, un iterador es un objeto que implementa el protocolo del iterador, el cual consiste en los métodos `__iter__()` y `__next__()`.

> ---
> 💻 Iterator vs Iterable
>
> Las listas, tuplas, diccionarios y conjuntos son objetos iterables. Son contenedores iterables de los que puede obtener un iterador.
>
> ---

### Interpretación

Se interpreta que un iterador es un objeto del cuál se permite extraer sus elementos usando `next(objeto_iter)`.

Para crear este iterador a partir de otro objeto original, cuya clase debe tener un método `__iter__()` que permita crear un objeto `iter` así: `objeto_iter = iter(objeto)`

### Práctica

Dada la lista se construye un iterador

```python
# Lista
letter_list = ["a", "b", "c", "d", "e", "f"]

# Iterador para aplicar next
letter_iterator = iter(letter_list)
```

Se ejecutan los next

```python
display(
    next(letter_iterator),
    next(letter_iterator),
    next(letter_iterator),
)
```

Y el resultado es

```console
'a'
'b'
'c'
```

El operador `*` extrae todos los elementos de una vez:

```python
display(*letter_iterator)
```

El resultado es

```console
'd'
'e'
'f'
```

&nbsp;

---
&nbsp;

## Enumerate

Una enumeración permite enumerar los datos de una estructura de datos ordenada.

```python
# Construcción de una enumeración
letter_list = ["a", "b", "c", "d", "e", "f", "g"]

enum = enumerate(letter_list)

display(
    type(enum),
    list(enum),
)
```

```console
enumerate
[(0, 'a'), (1, 'b'), (2, 'c'), (3, 'd'), (4, 'e'), (5, 'f'), (6, 'g')]
```

Uso de enumerate en un ciclo for:

```python
for i_letter, letter in enumerate(letter_list):
    print(i_letter, letter)
```

```console
0 a
1 b
2 c
3 d
4 e
5 f
6 g
```

&nbsp;

---
&nbsp;

## Zip

La función `zip` permite emparejar datos.

```python
uppercase = ["A", "B", "C", "D", "E"]
lowercase = ["a", "b", "c", "d", "e"]

zipped = zip(uppercase, lowercase)

display(
    type(zipped),
    list(zipped),
)
```

```console
zip
[('A', 'a'), ('B', 'b'), ('C', 'c'), ('D', 'd'), ('E', 'e')]
```

### Uso de zip con *

```python
zipped = zip(uppercase, lowercase)
display(*zipped)
```

```console
('A', 'a')
('B', 'b')
('C', 'c')
('D', 'd')
('E', 'e')
```

### Uso más común

```python
for item1, item2 in zip(uppercase, lowercase):
    display(item1 + " " + item2)
```

```console
'A a'
'B b'
'C c'
'D d'
'E e'
```

### Unzip

```python
zipped = zip(uppercase, lowercase)
a, b = zip(*zipped)
display(a, b)
```

```console
('A', 'B', 'C', 'D', 'E')
('a', 'b', 'c', 'd', 'e')
```

&nbsp;

---
&nbsp;

## Comprehension

`Comprehension` es una sintaxis más corta que se puede usar cuando se quiere crear un objeto basado en los valores de un objeto existente.

Por ejemplo, los objetos pueden ser listas o diccionarios.

### Lista usando for(), map() y comprehension

Se requiere crear una lista con los cuadrados de los números del 0 al 9.

```python
squares = []
# for
for x in range(10):
    squares.append(x ** 2)
```

```python
# list comprehension
squares = [x ** 2 for x in range(10)]
```

```python
# map
squares = list(map(lambda x: x ** 2, range(10)))
```

### List Comprehension

Su estructura básica es la siguiente

```python
new_list = [element for item in iterable]
```

Su estructura extendida es la siguiente

```python
new_list = [element_1 if bool_fun(x,y) else element_2 for x in collection_x for y in collection_y]
```

Un ejemplo:

```python
lis = ["Even number" if i % 2 == 0 else "Odd number" for i in range(8)]
```

### Dict Comprehension

```python
new_dict = {key: value for key, value in paired_collection}
```

### Generator

Un generador es un [iterador](#iteradores) personalizado.

Son funciones que nos permitirán obtener sus resultados poco a poco. Es decir, cada vez que llamemos a la función nos darán un nuevo resultado.

Por ejemplo, una función para generar todos los números pares que cada vez que la llamemos nos devuelva el siguiente número par.

#### Utilidad de un generador

Sirve para generar datos en tiempo de ejecución. Además también podemos acelerar búsquedas y crear bucles más rápidos.

Por este motivo, utilizar `range` es más lento que usar `xrange`. `range` genera todos los valores del rango y los devuelve en un array. En cambio, `xrange` genera cada valor del rango cuando se le solicita.

[Generadores en Python](https://alvarohurtado.es/2013/08/31/generadores-en-python/)

#### Cómo se construyen

Una sintaxis de `comprehension` para hacerlo es la siguiente:

```python
new_generator = (element for item in iterable)
```

También con la orden `yield` se puede usar en funciones para que retornen solo el siguiente valor que se necesita y no todos a la vez.

```python
def pares():
    index = 1
    # En este caso definimos un bucle infinito
    while True:
        # Devolvemos un valor (reemplazando el return)
        yield index*2
        index = index + 1
```

```python
maximo = 10

for par in pares():
    print(par)
    if par >= maximo:
        break
```

#### Lectura de datos

```python
def read_large_file(file_object):
    while True:
        data = file_object.readline()

        if not data:
            break

        yield data
```

```python
with open("/directory/example.csv", "r") as file:

    gen_file = read_large_file(file)

    print(next(gen_file), end="")
    print(next(gen_file), end="")
    print(next(gen_file), end="")
```

## Expresiones regulares

Numeros del 1 al 20 que contienen un '1'.

```python
# Regular Expressions module
import re

result = [str(x) for x in range(1, 21) if re.search("1", str(x))]
```
