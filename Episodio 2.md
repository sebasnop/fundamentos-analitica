# Python Ep 02: Una introducción informal a Python

## Tabla de contenidos

- [Python Ep 02: Una introducción informal a Python](#python-ep-02-una-introducción-informal-a-python)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Uso de Python como una calculadora](#uso-de-python-como-una-calculadora)
    - [Comentarios](#comentarios)
    - [Números](#números)
    - [Operaciones](#operaciones)

## Uso de Python como una calculadora

### Comentarios

Los comentarios permiten documentar el código. Se recomienda centrarse en explicar el **por qué** se hace algo en el código y no el **cómo**.

```python
# Comentario de una línea
```

```python
print("hola mundo cruel!") # Comentario después del código
```

```python
"""
Comentario entre comillas dobles.

Se usa para documentar modulos y funciones, o para comentar
bloques de código.

"""
```

Los `codetags` son palabras clave usadas en los comentarios que etiquetan aspectos del código.

Algunos `codetags` comunes son:

```python
"""
TODO:    Código pendiente por completar
FIXME:   Áreas problemáticas o código que necesita ser reesrito.
BUG:     Defecto reportado
RFE:     Request For Enhancement
???:     Pregunta
!!!:     Alerta
TODOC:   Necesita documentación
"""
```

### Números

Los tipos de números en Python son:

- Entero (`int`)
- Flotante (`float`)
- Imaginario (`complex`)

Los métodos `display` y `print` en Python son similares, pero tienen funcionalidades distintas.

Por ejemplo, en el siguiente código se busca ver el tipo de dato de un número imaginario:

```python
display(
    1 + 1j,
    type(1 + 1j),
)

print(type(1 + 1j))
```

La salida es la siguiente

```python
(1+1j)
complex
<class 'complex'>
```

### Operaciones


