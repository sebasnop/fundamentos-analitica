# Ep 06: Entrada y Salida

## Tabla de contenidos

- [Ep 06: Entrada y Salida](#ep-06-entrada-y-salida)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Impresión con formato usando f-strings](#impresión-con-formato-usando-f-strings)
    - [Decimales](#decimales)
    - [Espaciado con f-strings](#espaciado-con-f-strings)
    - [Comillas](#comillas)
  - [Template strings](#template-strings)
    - [Uso con diccionarios](#uso-con-diccionarios)
  - [El método `format()`](#el-método-format)
    - [Asignación de variables](#asignación-de-variables)
    - [Tablas](#tablas)
    - [String en formato raw](#string-en-formato-raw)
    - [Cantidad de decimales](#cantidad-de-decimales)
    - [Alineación](#alineación)
    - [Imprimir diccionario](#imprimir-diccionario)
  - [Old school string formatting](#old-school-string-formatting)

&nbsp;

---
&nbsp;

## Impresión con formato usando f-strings

Para usar `f-strings` en los `print` se coloca una `f` antes de la cadena de texto a imprimir en el `print`.

```python
print(f"Cadena de texto")
```

### Decimales

Controlar el número de decimales a mostrar con `:.3f`

```python
import math

print(f"The value of pi is approximately {math.pi:.3f}.")
```

```console
The value of pi is approximately 3.142.
```

### Espaciado con f-strings

Controlar el espaciado

```python
table = {"Sjoerd": 4127, "Jack": 4098, "Dcab": 7678}
for name, phone in table.items():
    print(f"{name:10} ==> {phone:10d}")
```

```console
Sjoerd     ==>       4127
Jack       ==>       4098
Dcab       ==>       7678
```

### Comillas

```python
animals = "eels"
```

- `ascii()`
  
  ```python
  print(f"My hovercraft is full of {animals!a}.")
  ```

  ```console
  My hovercraft is full of 'eels'.
  ```

- `repr()`
  
  ```python
  print(f"My hovercraft is full of {animals!r}.")
  ```

  ```console
  My hovercraft is full of 'eels'.
  ```

&nbsp;

---
&nbsp;

## Template strings

`Template` es una herramienta para predefinir estilos de impresión y solo reemplazar las variables del resultado final.

```python
from string import Template
```

```python
some_template = Template("-----> $variable1 $variable2 <------")
some_template.substitute(variable1="Texto1", variable2="Texto2")
```

```console
'-----> Texto1 Texto2 <------'
```

### Uso con diccionarios

```python
some_dict={'quien': 'Juan'}

Template("$quien gano $$1000").substitute(some_dict)
```

```console
'Juan gano $1000'
```

Safe substitution

```python
Template("$quien gano $$1000, pero $otro no gano").safe_substitute(some_dict)
```

```console
'Juan gano $1000, pero $otro no gano'
```

&nbsp;

---
&nbsp;

## El método `format()`

`format()` es un método de los strings para establecer estilos y variables reemplazables para la impresión de la cadena de texto.

### Asignación de variables

- Secuencial
  
  ```python
  'Este es el argumento {} y este el "{}"'.format("-1-", "-2-")
  ```

  ```console
  'Este es el argumento -1- y este el "-2-"'
  ```
  
- Ordenada
  
  ```python
  "{1} y {0}".format("a", "b")
  ```

  ```console
  'b y a'
  ```
  
- Con nombre
  
  ```python
  "{arg0} y {arg1}.".format(arg1="-1-", arg0="-0-")
  ```

[String formatting - Python Documentation](https://docs.python.org/3/library/stdtypes.html#old-string-formatting)

### Tablas

Notar que el espaciado es igual a con f-strings.

```python
for x in range(1, 11):
    print("{0:2d} {1:3d} {2:4d}".format(x, x * x, x * x * x))
```

```console
 1   1    1
 2   4    8
 3   9   27
 4  16   64
 5  25  125
 6  36  216
 7  49  343
 8  64  512
 9  81  729
10 100 1000
```

### String en formato raw

```python
x = 1
"Este es el argumento {!r}.".format(x)
```

```console
'Este es el argumento 1.'
```

### Cantidad de decimales

Igual a con f-strings.

```python
import math

"Valor de PI con tres decimales: {0:.3f}.".format(math.pi)
```

### Alineación

```python
# String de 15 caracteres alineado a la derecha
"{0:>15s} ---- {1:8.2f}".format("hola mundo", 1.23456789)
```

```console
'     hola mundo ----     1.23'
```

### Imprimir diccionario

```python
dict_ = {"a": 100, "b": 101, "c": 102}

print("a: {a:d}; b: {b:d}; c: {c:d}".format(**dict_))
```

```console
a: 100; b: 101; c: 102
```

&nbsp;

---
&nbsp;

## Old school string formatting

Así es la manera tradicional de aplicar formateado a los strings.

```python
str_var = "hola"
int_var = 123
float_var = 4.56

"Variable entera %d, string %s, flotante %.4f" % (int_var, str_var, float_var)
```

```console
'Variable entera 123, string hola, flotante 4.5600'
```
