# Ep 8: Librería Estándar

[Ep 10: Librería Estandar 1](https://jdvelasq.github.io/courses/modulos/python/10%20libreria%20estandar%201/_index.html#prog-en-python-ep-10-libraria-estandar-parte-1)

&nbsp;

---
&nbsp;

## Tabla de contenidos

- [Ep 8: Librería Estándar](#ep-8-librería-estándar)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Data pretty printer `pprint`](#data-pretty-printer-pprint)
  - [Datetime](#datetime)
  - [Expresiones regulares `re`](#expresiones-regulares-re)
  - [Collections](#collections)
  - [Glob](#glob)
    - [Ejemplo uso de glob](#ejemplo-uso-de-glob)
  - [Fileinput](#fileinput)
    - [Leer líneas en varias archivos](#leer-líneas-en-varias-archivos)
    - [Reemplazar contenido](#reemplazar-contenido)

&nbsp;

---
&nbsp;

## Data pretty printer `pprint`

Herramienta para imprimir mejor los datos.

Tiene funciones como la indentación, definir el ancho, la profundidad a mostrar de elementos anidados y la impresión fácil de archivos tipo `json`.

```python
import pprint
```

&nbsp;

---
&nbsp;

## Datetime

Permite la manipulación de fechas, horas y duraciones.

```python
from datetime import datetime, date, timedelta
import time
```

&nbsp;

---
&nbsp;

## Expresiones regulares `re`

Permite aplicar búsquedas o diferentes funciones en texto usando las expresiones regulares.

```python
import re
```

&nbsp;

---
&nbsp;

## Collections

Permite acceder a estructuras de datos útiles como:

- `Counter`

  Se utiliza para contar la frecuencia de elementos en una lista u otro iterable.
  
  ```python
  from collections import Counter
  ```
  
- `deque`

  Se utiliza para crear objetos de lista doblemente enlazados y es muy útil para implementar colas y pilas.

  ```python
  from collections import deque
  ```
  
- `defaultdict`

  Se utiliza para crear diccionarios que tienen un valor predeterminado para una clave que no existe en el diccionario.

  Con `defaultdict`, podemos especificar un valor predeterminado para todas las claves que no están en el diccionario, lo que significa que no se genera una excepción si intentamos acceder a una clave que no está en el diccionario.

  ```python
  from collections import defaultdict
  ```
  
- `namedtuple`

  Permite crear tuplas que tienen campos con nombres.

  Es similar a una tupla normal, pero en lugar de acceder a los elementos por su índice numérico, podemos acceder a ellos por su nombre.

  ```python
  from collections import namedtuple
  ```

  `namedtuple` es útil cuando queremos crear una estructura de datos simple que tenga campos con nombres, pero no queremos definir una clase completa solo para eso.
  
  ```python
  Person = namedtuple('Person', ['name', 'age', 'sex'])

  person1 = Person('Alice', 25, 'F')
  person2 = Person('Bob', 30, 'M')
  ```

&nbsp;

---
&nbsp;

## Glob

(Expansión de nombres de paths estilo Unix)

Es una biblioteca que proporciona una manera fácil de buscar archivos que coincidan con un patrón especificado en un directorio dado.

```python
import glob
```

La biblioteca `glob` proporciona una función `glob()` que toma un patrón de búsqueda como argumento y devuelve una lista de rutas de archivo que coinciden con ese patrón. El patrón de búsqueda puede incluir comodines como `*` y `?` que representan cualquier cadena y cualquier carácter individual, respectivamente.

### Ejemplo uso de glob

Encontrar todos los archivos con una extensión .txt en un directorio:

```python
txt_files = glob.glob('/path/to/dir/*.txt')
print(txt_files)
```

&nbsp;

---
&nbsp;

## Fileinput

La biblioteca `fileinput` proporciona una manera fácil de iterar sobre múltiples archivos de entrada como si fueran uno solo. Esta biblioteca es útil cuando necesitamos procesar múltiples archivos de entrada en un solo script o programa.

```python
import fileinput
```

### Leer líneas en varias archivos

```python
for line in fileinput.input(['/path/to/file1', '/path/to/file2']):
    if 'search_string' in line:
        print(line)
```

### Reemplazar contenido

```python
for line in fileinput.input('/path/to/file', inplace=True):
    line = line.replace('old_string', 'new_string')
    print(line, end='')
```
