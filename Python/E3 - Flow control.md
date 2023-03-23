# Ep 03: Herramientas de control de flujo

[Python Ep 01: Manejo básico de Jupyter Lab y Colab](https://jdvelasq.github.io/courses/modulos/python/03%20herramientas%20de%20control%20de%20flujo/_index.html#prog-en-python-ep-03-herramientas-de-control-de-flujo)

## Tabla de contenidos

- [Ep 03: Herramientas de control de flujo](#ep-03-herramientas-de-control-de-flujo)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Declaraciones if / elif / else](#declaraciones-if--elif--else)
  - [Iteración usando for](#iteración-usando-for)
    - [Break y Continue](#break-y-continue)
    - [Pass](#pass)
  - [Iteración usando while](#iteración-usando-while)
  - [Funciones](#funciones)
    - [Documentación](#documentación)
    - [Ámbito y variables](#ámbito-y-variables)
      - [Global](#global)
      - [Nonlocal](#nonlocal)
    - [Side effects](#side-effects)
      - [Variables](#variables)
      - [Lists](#lists)
    - [Argumentos posicionales, valores por defecto y número variable de argumentos](#argumentos-posicionales-valores-por-defecto-y-número-variable-de-argumentos)
    - [Funciones complejas](#funciones-complejas)
  - [Funciones anónimas](#funciones-anónimas)

&nbsp;

---
&nbsp;

## Declaraciones if / elif / else

El `if` evalúa una proposición booleana. Solo si es cierta ejecuta el código indentado a continuación.

El `elif` es un `if` que solo se puede usar luego de usar un `if` y solo se evalúa si el `if` previo es falso.

El `else` es una declaración para ejecutar algo en caso de que un `if` y/o un conjunto de `elif` previos no hayan sido verdaderos.

```python
a = int(input())

if a > 0:
    print("Positive number")
elif a < 0:
    print("Negative number")
else:
    print("Number is 0")
```

&nbsp;

---
&nbsp;

## Iteración usando for

El `for` tiene la siguiente estructura:

```python
for element in iterable:
    # Execute something
    # Element can be used
```

Para controlar la ejecución de acciones dentro del `for` se pueden usar los comandos `break`, `continue` y `pass`.

### Break y Continue

```python
for n in range(1, 10):
    if n < 4:
        # Reinicia el ciclo for sin pasar
        # por el resto del cuerpo
        continue

    # Solo pasa por aca cuando n >= 4.
    
    print(n)
    
    if n > 6:
        # Interrupe el ciclo cuando n > 6.
        break
```

```console
4
5
6
7
```

### Pass

```python
for index in range(10):
    if index > 2 and index < 8:
        pass
    else:
        print(index)
```

```console
0
1
2
8
9
```

&nbsp;

---
&nbsp;

## Iteración usando while

El `while` ejecuta un código mientras su posposición booleana es verdadera. Cuando es falsa el ciclo se termina y se deja de evaluar.

Tiene la siguiente estructura:

```python
while boolean_proposition:
    # Execute something
```

&nbsp;

---
&nbsp;

## Funciones

Una función es una secuencia de instrucciones que se pueden reusar en diferentes partes del código siendo invocada.

Las funciones pueden recibir parámetros y retornar resultados. También podrían solo ejecutar acciones.

Hay funciones internas de Python como `print`, pero un usuario puede crear sus propias funciones.

```python
def suma(a, b):
    return a+b

# Parámetro posicional
c = suma(1, 2)

# Parámetro nombrado
d = suma(a=1, b=2)
```

### Documentación

En Python no es necesario definir qué tipo de dato se ingresa o se retorna, pero ayuda al programador a entender el código.

```python
def suma(a: float, b: float) -> float:
    return a+b
```

También se le puede agregar una explicación a la función para mejorar el entendimiento del programador.

```python
def suma(a: float, b: float) -> float:
    """Suma dos números reales ingresados."""
    return a+b

print(suma.__doc__)
```

```console
Suma dos números reales ingresados.
```

```python
def suma(a: float, b: float) -> float:
    """Suma dos números reales ingresados."""
    return a+b

help(suma)
```

```console
Help on function suma in module __main__:     

suma(a: float, b: float) -> float
    Suma dos números reales ingresados.
```

### Ámbito y variables

Una función puede recibir como parámetro una variable externa y la externa no cambia.

```python
# Ambito de las variables como parámetros
int_var = 5

def my_function(int_var):
    int_var = 3
    print("inside:", int_var)

my_function(int_var)
print("outside:", int_var)
```

```console
inside: 3
outside: 5
```

Una función puede modificar el valor de una variable del programa (de tipo inmutable) sólo para sí misma.

Por fuera, la variable sigue valiendo lo mismo.

```python
# Ambito de las variables en asignaciones
int_var = 5

def my_function(a):
    int_var = a
    print("inside:", int_var)

my_function(3)
print("outside:", int_var)
```

```console
inside: 3
outside: 5
```

#### Global

Sin embargo, con `global` dentro de la función sí se puede modificar el valor global de la variable.

```python
# Usando global
int_var = 5

def my_function(a):
    global int_var
    int_var = a
    print("inside:", int_var)

my_function(3)
print("outside:", int_var)
```

```console
inside: 3
outside: 3
```

#### Nonlocal

Para aplicar lo mismo de global a funciones dentro de otras funciones se usa `nonlocal`.

```python
# Sin nonlocal
def outer():
    n = 1

    def inner():
        n = 2
        print(n)

    inner()
    print(n)

outer()
```

```console
2
1
```

```python
# Con nonlocal
def outer():
    n = 1

    def inner():
        nonlocal n
        n = 2
        print(n)

    inner()
    print(n)

outer()
```

```console
2
2
```

### Side effects

Un cambio inadvertido que provoca cambios no esperados en el resultado de la función (¡indeseado!).

#### Variables

A veces se espera que la función siempre devuelva el mismo resultado.
Se requiere ser cuidadoso cambiando las variables externas si de eso depende la función.

```python
a = 1
b = 2

def a_plus_b():
    return a + b

# Resultado 1
a_plus_b()

a = 3

# Resultado 2
a_plus_b()
```

```console
3
5
```

#### Lists

Se prefiere no modificar las listas externas, sino crear unas nuevas.
Aplica algo similar para los diccionarios.

```python
my_list = [1, 2]


def my_function(a_list):
    a_list = a_list.copy()
    a_list.append("a")
    return a_list


my_new_list = my_function(my_list)
print(my_list)
print(my_new_list)
```

```python
[1, 2]
[1, 2, 'a']
```

La variable L no debería acumular la lista ya que el valor por defecto de `L` es `[]`:

```python
def f(a, L=[]):
    L.append(a)
    return L


print(f(1))
print(f(2))
print(f(3))
```

```console
[1]
[1, 2]
[1, 2, 3]
```

Corrección del side effect usando `None`:

```python
def f(a, L=None):
    if L is None:
        L = []
    L.append(a)
    return L


print(f(1))
print(f(2))
print(f(3))
```

```console
[1]
[1]
[3]
```

### Argumentos posicionales, valores por defecto y número variable de argumentos

```python
# Tipos de argumentos
def my_function(first_arg, second_arg=2, *args, **kwargs):
    print(" first_arg:", first_arg)
    print("second_arg:", second_arg)
    print("      args:", args)
    print("    kwargs:", kwargs)

# Llamada con argumentos posicionales
my_function(1, 2)

# Llamada con argumentos por nombre
my_function(second_arg=2, first_arg=1)
```

Salida igual para ambas llamadas:

```console
 first_arg: 1
second_arg: 2
      args: ()
    kwargs: {}
```

Llamada con argumentos extra sin nombre:

```python
my_function(1, 2, 3, 4)
```

```console
 first_arg: 1
second_arg: 2
      args: (3, 4)
    kwargs: {}
```

Llamada con argumentos extra con nombre:

```python
my_function(first_arg=1, second_arg=2, third_arg=3)
```

```python
 first_arg: 1
second_arg: 2
      args: ()
    kwargs: {'third_arg': 3}
```

Otro caso de `**args`:

```python
def my_function(a, b, c):
    return a + b + c

args = {
    "a": 1,
    "b": 2,
    "c": 3,
}

my_function(**args)
```

```console
6
```

### Funciones complejas

Función compuesta de varias subfunciones.

**Principio de responsabilidad simple:**
Cada función hace una tarea y solo una tarea

Se busca usar este principio para facilitar el entendimiento y mejorar la reusabilidad.

```python
def complex_function(x):
    def constant():
        return 1

    def first():
        return x

    def second():
        return x ** 2

    result = constant() + first() + second()
    return result
```

&nbsp;

---
&nbsp;

## Funciones anónimas

Las funciones previas fueron creadas con nombre:

```python
# Función creada con nombre
def incr(x):
    return x + 1

incr(1)
```

```console
2
```

Función anónima o `lambda`:

```python
# Función anónima o lambda
incr_ = lambda x: x + 1

incr_(1)
```

```console
2
```

Las funciones lambda se puede aplicar directamente:

```python
(lambda x: x + 1)(2)
```

```console
3
```

Crear una función que devuelva otra:

```python
def make_incrementor(n):
    return lambda x: x + n

f = make_incrementor(42)
f(1)
```

```console
43
```
