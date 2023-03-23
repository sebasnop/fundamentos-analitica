# Ep 07: Errores y Excepciones

[Ep 08: Errores y Excepciones](https://jdvelasq.github.io/courses/modulos/python/08%20errores%20y%20excepciones/_index.html#prog-en-python-ep-08-errores-y-excepciones)

&nbsp;

---
&nbsp;

## Tabla de contenidos

- [Ep 07: Errores y Excepciones](#ep-07-errores-y-excepciones)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Excepciones](#excepciones)
  - [Estructura de manejo de excepciones](#estructura-de-manejo-de-excepciones)
  - [Ejemplo](#ejemplo)

&nbsp;

---
&nbsp;

## Excepciones

Las excepciones son eventos que ocurren durante la ejecución de un programa y que interrumpen el flujo normal de ejecución.

Python proporciona una forma de manejar estas excepciones y controlar el flujo del programa en caso de que se produzcan. En Python, se manejan los errores y excepciones con el uso de las sentencias `try`, `except`, `else` y `finally`.

## Estructura de manejo de excepciones

La estructura básica de un bloque de manejo de excepciones es la siguiente:

```python
try:
    # Código que puede producir una excepción
except ExceptionType:
    # Código que se ejecutará si se produce una excepción de ExceptionType
else:
    # Código que se ejecutará si no se produce ninguna excepción
finally:
    # Código que se ejecutará siempre, independientemente de si se produce una excepción o no
```

El bloque `try` contiene el código que puede producir una excepción. Si se produce una excepción, Python detiene la ejecución del bloque `try` y pasa al bloque `except`.

El bloque `except` contiene el código que se ejecutará si se produce una excepción del tipo `ExceptionType`. También es posible manejar excepciones de diferentes tipos utilizando varias sentencias `except`.

El bloque `else` es opcional y contiene el código que se ejecutará si no se produce ninguna excepción en el bloque `try`.

El bloque `finally` también es `opcional` y contiene el código que se ejecutará siempre, independientemente de si se produce una excepción o no. El bloque `finally` se utiliza comúnmente para realizar operaciones de limpieza, como cerrar archivos o conexiones de bases de datos.

## Ejemplo

Aquí hay un ejemplo de cómo manejar una excepción en Python:

```python
try:
    a = 5 / 0 # División por cero - se producirá una excepción ZeroDivisionError
except ZeroDivisionError:
    print("¡No se puede dividir por cero!")
else:
    print("El resultado es:", a)
finally:
    print("El bloque finally se ejecuta siempre")
```
