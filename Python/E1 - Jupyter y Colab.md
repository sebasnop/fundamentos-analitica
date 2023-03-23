# Ep 01: Manejo básico de Jupyter Lab y Colab

[Python Ep 01: Manejo básico de Jupyter Lab y Colab](https://jdvelasq.github.io/courses/modulos/python/01%20uso%20de%20jupyterlab%20y%20colab/_index.html#prog-en-python-ep-01-jupyterlab-y-colab)

## Tabla de contenidos

- [Ep 01: Manejo básico de Jupyter Lab y Colab](#ep-01-manejo-básico-de-jupyter-lab-y-colab)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Uso de básico de Google Colaboratory](#uso-de-básico-de-google-colaboratory)
  - [Creación y ejecución de programas de Python](#creación-y-ejecución-de-programas-de-python)
  - [Uso de `%%bash` y `%%writefile`](#uso-de-bash-y-writefile)
    - [`%%bash`](#bash)
    - [`%%writefile`](#writefile)
  - [Lenguaje Markdown](#lenguaje-markdown)
    - [Resumen](#resumen)
    - [Citas](#citas)
    - [Énfasis](#énfasis)
    - [Numeración](#numeración)
    - [Vínculos](#vínculos)
    - [Imágenes](#imágenes)
    - [Código](#código)
    - [Expresiones Matemáticas](#expresiones-matemáticas)
    - [Tablas](#tablas)
  - [HTML para notebooks](#html-para-notebooks)
    - [Anotaciones](#anotaciones)

&nbsp;

---
&nbsp;

## Uso de básico de Google Colaboratory

Para correr comandos de terminal en Google Colab se puede hacer así:

```python
!pip install matplotlib
```

```python
shell pip install matplotlib
```

Para varias líneas de comandos:

```python
%%shell
pip install matplotlib
pip install youtube_dl
```

[Run a Full TTY Terminal in Google Colab (without Colab Pro)](https://blog.infuseai.io/run-a-full-tty-terminal-in-google-colab-without-colab-pro-2759b9f8a74a)

&nbsp;

---
&nbsp;

## Creación y ejecución de programas de Python

Para **ejecutar Python** desde la **terminal** se suele usar:

```console
python3
```

```console
ipython
```

Para **ejecutar Python** desde **Git Bash** se pueden ejecutar los siguientes comandos:

```console
winpty python
```

```console
python -i
```

Para **ejecutar un archivo** en **Git Bash** desde el directorio en donde está ubicado se usa el siguiente comando:

```console
python file.py
```

&nbsp;

---
&nbsp;

## Uso de `%%bash` y `%%writefile`

Los ambientes tienen varias utilidades que extienden las capacidades de los notebooks más allá de las características del kernel que se este usando. Las `magics` permiten modiicar el comportamiento de las celdas individuales.

### `%%bash`

Ejecuta el código de la celda usando bash.

```python
%%bash
ls -1 sample_data/*
```

Es equivalente a:

```python
%%shell
ls -1 sample_data/*
```

### `%%writefile`

Permite grabar el contenido de la celda al archivo especificado.

```python
%%writefile data.csv
1, Pepe
2, Maria
3, Juliana
```

[Lista de `magics`](https://github.com/ipython/ipython/wiki/Extensions-Index).

&nbsp;

---
&nbsp;

## Lenguaje Markdown

El formato de un libro de Jupyter/Colab se realiza usando Markdown en las celdas marcadas como tipo markdown.

### Resumen

```markdown
# Títulos
## Secciones
### Subsecciones
#### Subsecciones en tercer nivel

Párrafo.
```

### Citas

```markdown
> Citas (`quotes`)
```

### Énfasis

```markdown
- Texto en itálica: _texto_ o *text*.
- Texto en negrita: **texto** o __texto__
- Texto tachado: ~~texto~~
```

### Numeración

```markdown
1. A
2. B
3. C
```

### Vínculos

```markdown
Básicos:
[GOOGLE](http://www.google.com)

Tipo referencia:

Estos son vinculos referenciados a [Anaconda][1]  y [Python][2].

[1]: https://www.continuum.io "Continuum Analytics"
[2]: https://www.python.org "Python Software Fundation"

Internos:
[Vínculo a la seccion de abajo](#Imágenes)
```

### Imágenes

```markdown
![Texto alternativo](nombre_de_archivo)
```

### Código

```markdown
    ```python
    for i in range (10):
        print(i)
    ```
```

### Expresiones Matemáticas

```markdown
$$\frac{1}{x^2} \int{\exp{x^n}} dx$$
```

$$\frac{1}{x^2} \int{\exp{x^n}} dx$$

### Tablas

```markdown
titulo 1 MUY MUY LARGO | titulo 2 | titulo 3
-----:|:--------:| -------
celda 1-1 | celda 1-2 | celda 1-3
celda 2-1 | celda 2-2 | celda 2-3
```

&nbsp;

---
&nbsp;

## HTML para notebooks

Se pueden agregar elementos de HTML a Notebooks de IPython. Esto se hace agregando el comando `%%html` al inicio de una celda de código en el Notebook.

Por ejemplo, a continuación se inserta un formulario con un slider y una caja de número para sumarlos:

```python
%%html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">0
  <input type="range" id="a" value="50">100
  +<input type="number" id="b" value="50">
  =<output name="x" for="a b"></output>
</form>
```

Se pueden aplicar todo tipo de elementos aplicables en HTML.

### Anotaciones

- El formato de un libro de Jupyter se realiza usando Markdown.

- La sintaxis explicada en este documento se aplica a los documentos creados en RStudio usando RMarkdown.

- Haga click [aquí](https://daringfireball.net/projects/markdown/basics) para acceder a una guía de markdown y [aquí](http://jupyter-notebook.readthedocs.org/en/latest/examples/Notebook/rstversions/Working%20With%20Markdown%20Cells.html) a la documentación oficial sobre markdown en Jupyter.

- IPython tiene opciones para visualizar salidas en latex y html (entre otros). Haga click [aquí](https://github.com/ipython/ipython-in-depth/blob/1905adca735c567884c5db8c1b6295b0e1d7a218/examples/IPython%20Kernel/Rich%20Output.ipynb) para acceder a un tutorial.

- Los libros de Jupyter pueden visualizarse de forma estática en la web usando [nbviewer](http://nbviewer.jupyter.org).

- Un tutorial completo sobre HTML se encuentra en [w3Schools](http://www.w3schools.com).
