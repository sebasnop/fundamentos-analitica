# Ep 04: Python: Estructuras de datos

[Python Ep 04: Python: Estructuras de datos (Parte 1)](https://jdvelasq.github.io/courses/modulos/python/04%20estructuras%20de%20datos%201/_index.html#prog-en-python-ep-04-estructuras-de-datos-1)

&nbsp;

---
&nbsp;

## Tabla de contenidos

- [Ep 04: Python: Estructuras de datos](#ep-04-python-estructuras-de-datos)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Desempaquetado de listas](#desempaquetado-de-listas)
  - [Reemplazo de elementos en listas](#reemplazo-de-elementos-en-listas)
  - [Borrado de elementos en listas usando `del`](#borrado-de-elementos-en-listas-usando-del)
  - [Principales métodos de las listas](#principales-métodos-de-las-listas)
  - [Efectos colaterales en listas y método copy()](#efectos-colaterales-en-listas-y-método-copy)
  - [Funciones `filter()`, `map()` y `reduce()`](#funciones-filter-map-y-reduce)
    - [Filter](#filter)
    - [Map](#map)
    - [Reduce](#reduce)

&nbsp;

---
&nbsp;

## Desempaquetado de listas

Hay maneras para extraer información de listas por su posición:

```python
# first = 1, rest = [2, 3]
first, *rest = [1, 2, 3]
```

```python
# first = 1, middle = [2, 3], last = 4
first, *middle, last = [1, 2, 3, 4]
```

&nbsp;

---
&nbsp;

## Reemplazo de elementos en listas

Se puede reemplazar un elemento con su índice:

```python
cubes_list = [1, 8, 27, 65, 125]

cubes_list[3] = 64
cubes_list
```

```bash
[1, 8, 27, 64, 125]
```

También por su rango de posiciones:

```python
letters_list = ["a", "b", "c", "d", "e", "f", "g"]
```

```python
# Reemplazo
letters_list[2:5] = ["C", "D", "E"]
letters_list
```

```bash
["a", "b", "C", "D", "E", "f", "g"]
```

```python
# Borrado
letters_list[2:5] = []
letters_list
```

```bash
["a", "b", "f", "g"]
```

Reemplazo cada 2 elementos:

```python
letters_list = ["a", "b", "c", "d", "e", "f", "g"]
```

```python
letters_list[0:7:2] = ["A", "C", "E", "G"]
letters_list
```

```bash
['A', 'b', 'C', 'd', 'E', 'f', 'G']
```

&nbsp;

---
&nbsp;

## Borrado de elementos en listas usando `del`

Borrar un elemento usando su índice:

```python
integers_list = [0, 1, 2, 3, 4, 5, 6, 7, 8]

del integers_list[0]
integers_list
```

```bash
[1, 2, 3, 4, 5, 6, 7, 8]
```

Borrar elementos en un rango:

```python
del integers_list[2:4]
integers_list
```

```bash
[1, 2, 5, 6, 7, 8]
```

Vaciar lista:

```python
del integers_list[:]
integers_list
```

```bash
[]
```

Borrar variable de la memoria:

```python
del integers_list
```

&nbsp;

---
&nbsp;

## Principales métodos de las listas

- `Append`: Agregar elemento.
  
  También se pueden concatenar listas "sumándolas" con `+`.

- `Clear`: Borra todos los elementos.
- `Pop`: Extrae el último elemento y lo elimina de la lista.
- `Extend`: Concatenar listas.
- `Insert`: Insertar elemento en un índice.
- `Count`: Contar cantidad de repeticiones de un elemento en la lista.

  Para contar las repeticiones de todos los elementos es más apropiado usar el objeto `Counter` del módulo `collections`:

  ```python
  from collections import Counter

  list_c = ["a", "b", "b", "c", "c", "c", "d", "d", "d", "d"]
  
  Counter(list_c)
  ```

  ```bash
  Counter({'a': 1, 'b': 2, 'c': 3, 'd': 4})
  ```

- `Index`: Obtener índice de primera aparición de un elemento.
- `Remove`: Eliminar elemento.
- `Reverse`: Lista al revés.
- `Sort`: Ordena según algún parámetro.

  ```python
  letters_list = ["a", "b", "c", "d", "e", "f", "g"]
  letters_list.sort(reverse=True)
  letters_list
  ```

  ```bash
  ['g', 'f', 'e', 'd', 'c', 'b', 'a']
  ```
  
- Módulo `ittemgetter`: Permite ordenar listas de tuplas según alguno de los items de las tuplas.

  ```python
  tuples_list = [(10, "b"), (8, "a"), (12, "d"), (9, "c")]
  ```

  Usando el método `sort`:

  ```python
  from operator import itemgetter

  tuples_list.sort(key=itemgetter(0), reverse=True)
  
  tuples_list
  ```

  ```bash
  [(12, 'd'), (10, 'b'), (9, 'c'), (8, 'a')]
  ```

  Usando la función `sorted`:

  ```python
  tuples_list = [(10, "b"), (8, "a"), (12, "d"), (9, "c")]
  sorted(tuples_list, key=itemgetter(1), reverse=False)
  ```

  ```bash
  [(8, 'a'), (10, 'b'), (9, 'c'), (12, 'd')]
  ```

&nbsp;

---
&nbsp;

## Efectos colaterales en listas y método copy()

Al copiar una lista así:

```python
list_a = [0, 1, 2, 3, 4, 5, 6]
list_b = list_a
```

Esta operación en `list_b` se ejecuta también en la `list_a`, de forma indeseada:

```python
list_b.pop()
```

Para solucionarlo se pueden usar varios métodos al copiar la lista:

```python
list_b = list_a.copy()
```

```python
list_b = list_a[:]
```

```python
list_b = list(list_a)
```

&nbsp;

---
&nbsp;

## Funciones `filter()`, `map()` y `reduce()`

### Filter

Retorna los elementos para loscuales el condicional da verdadero.

```python
list_a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
list(filter(lambda element: element > 4, list_a))
```

```bash
[5, 6, 7, 8, 9]
```

### Map

Aplica una función a cada elemento de la lista

La función devuelve un iterador por lo que se debe usar `list()` para visualizar los elementos

```python
list_a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
list(map(lambda element: element + 10, list_a))
```

```bash
[10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
```

### Reduce

Se usa para aplicar una función particular pasada como parámetro a todos los elementos de la lista mencionados en la secuencia pasada.

Su estructura es así:

```python
reduce(fun,seq)
```

```python
from functools import reduce

my_list = [1, 2, 3, 4, 5, 6]

reduce(lambda item_1, item_2: item_1 + item_2, my_list)
```

```bash
21
```
