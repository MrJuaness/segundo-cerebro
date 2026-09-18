Vale, vamos al grano. Te preparo esto en dos partes: primero las herramientas, luego el Tema 1 explicado de cero a experto sin dejarme nada, y al final los mejores recursos para no perder tiempo. Antes de recomendarte vídeos/cursos, dejame comprobar qué hay disponible ahora mismo de calidad en español.

## 🎯 Vale, empecemos por lo práctico: herramientas

Antes de tocar el Tema 1, instala esto (5 minutos):

1. **Python** → [python.org/downloads](https://www.python.org/downloads/) → al instalar, marca la casilla **"Add python.exe to PATH"** (si no, luego no funciona desde la terminal).
2. **Editor de código** → **Visual Studio Code** (gratis) + instala la extensión "Python" de Microsoft. Es el estándar que usarás en toda la ASIR y en el trabajo.
3. Para probar que funciona: abre una terminal y escribe `python --version`. Si te devuelve un número, ya puedes programar.

Con esto ya tienes montado tu "laboratorio". Nada más hace falta para el Tema 1.

Aviso rápido: tu apunte tiene una errata en todas las cabeceras, pone **"Phyton"** — se escribe **Python**. No lo copies mal en un examen 😉.

---

## 📘 Tema 1 explicado sin rodeos

### 1. ¿De qué está hecho un programa?

Idea simple: un programa = **instrucciones** (código fuente) + **datos** que gestiona + una forma de **hablar con el usuario** (interfaz) + una lógica que resuelve problemas (algoritmos). Para que dure en el tiempo, también necesita estar **documentado**, **probado** (tests) y controlado con herramientas como **Git**. Esto es solo cultura general para el examen teórico; lo importante empieza en el punto 2.

### 2. Estructura del código (esto sí es fundamental)

**La regla de oro de Python:** en vez de `{ }` como Java o C++, Python usa la **sangría** (espacios al principio de línea) para marcar qué pertenece a qué bloque. Usa siempre **4 espacios**, nunca mezcles con tabulaciones.

python

```python
temperatura = 18
if temperatura < 20:
    print("Hace fresco")      # esto pertenece al "if"
    print("Pon tu chaqueta")  # esto también
print("Programa finalizado")  # esto NO pertenece al "if", se ejecuta siempre
```

Si te falla la sangría → `IndentationError`. Es el error nº1 de todo principiante.

**Funciones** (`def`): agrupan código para no repetirlo.

python

```python
def calcular_area_rectangulo(base, altura):
    """Devuelve el área de un rectángulo."""  # esto es un docstring, explica la función
    return base * altura
```

**Clases** (`class`): para agrupar datos + comportamiento (Programación Orientada a Objetos). Lo verás más a fondo en otra unidad; de momento solo reconoce la forma:

python

```python
class Vehiculo:
    def __init__(self, marca, modelo):   # constructor
        self.marca = marca
        self.modelo = modelo
```

**Módulos**: cada archivo `.py` es un módulo; puedes importar código de otro archivo con `import`.

**Manejo de errores** (lo usarás mucho como sysadmin):

python

```python
try:
    archivo = open("datos.txt")
except FileNotFoundError:
    print("El archivo no existe")
finally:
    print("Esto se ejecuta siempre")
```

⚠️ Cosas que salen en tu apunte pero son **de nivel avanzado** (decoradores `@algo`, `type hints`, context managers `with`, ámbito LEGB): no te obsesiones con ellas ahora. Entiende que existen, pero lo que de verdad vas a necesitar dominar de este tema es lo que viene abajo.
### 3. Variables

Una variable = una "caja con nombre" donde guardas un dato.

python

```python
nombre = "Carlos"   # str
edad = 30            # int
activo = True         # bool
```

No hace falta decir de qué tipo es (Python lo detecta solo → **tipado dinámico**).

**Reglas del nombre:**

- Empieza por letra o `_`, nunca por número.
- Solo letras, números y `_` (sin espacios, sin `@#$`).
- No uses palabras reservadas (`if`, `for`, `class`...).
- Usa `snake_case`: `nombre_usuario`, no `NombreUsuario`.

**Trucos útiles:**

python

```python
x, y = 5, 10
x, y = y, x          # intercambia valores en una línea
a = b = c = 100       # asigna el mismo valor a varias variables
```

### 4. Tipos de datos (aprende esto de memoria)

|Tipo|Ejemplo|Qué es|
|---|---|---|
|`int`|`10`|número entero|
|`float`|`10.5`|número decimal|
|`str`|`"Hola"`|texto|
|`bool`|`True` / `False`|lógico|
|`None`|`None`|"sin valor"|
|`list`|`[1, 2, 3]`|lista, **mutable** (se puede cambiar)|
|`tuple`|`(1, 2, 3)`|como una lista pero **inmutable**|
|`dict`|`{"a": 1}`|pares clave-valor|
|`set`|`{1, 2, 3}`|sin duplicados, sin orden|

Comprobar el tipo:

python

```python
type("Hola")           # <class 'str'>
isinstance(10, int)    # True
```

### 5. Literales

Es simplemente **el valor escrito directamente en el código**: `10`, `"Ana"`, `True`, `[1,2,3]`. La diferencia con una variable: el literal ES el valor; la variable es el nombre que apunta a ese valor.

### 6. Constantes

Python **no tiene constantes reales** (nada impide cambiarlas). Es pura convención: si un valor no debe cambiar, se escribe en **MAYÚSCULAS**:

python

```python
PI = 3.14159
URL_API = "https://api.ejemplo.com"
```

### 7. Operadores (memorizar, aparece mucho en exámenes)

python

```python
# Aritméticos
+  -  *  /  // (división entera)  % (resto)  ** (potencia)

# Comparación → devuelven True/False
==  !=  >  <  >=  <=

# Lógicos
and  or  not

# Asignación
=  +=  -=  *=  /=

# Pertenencia (muy usado)
'pera' in ['manzana', 'pera']   # True

# Identidad (¿es el mismo objeto en memoria?)
x is y
```

### 8. Conversión de tipos (type casting)

Muy típico en exámenes y en la vida real (datos que llegan como texto de un formulario):

python

```python
int("100")      # 100
float("10.5")   # 10.5
str(25)         # "25"
```

**El error clásico:** si no conviertes, `"15" + "30"` da `"1530"` (concatena texto), no `45`.

python

```python
int('abc')   # ValueError → no todo se puede convertir
```

### 9. Comentarios

python

```python
# Comentario de una línea
print("Hola")  # también al final de una línea

"""
Esto es un docstring (comentario de bloque),
se usa sobre todo para documentar funciones.
"""
```

Regla de oro: comenta el **por qué**, no el **qué** (el código ya dice el qué).

---

## 🧪 Ejemplo que une todo el tema

python

```python
# Programa de ejemplo: calcula el total de una compra

PRECIO_IVA = 1.21  # constante

precio_texto = "25.50"          # literal str
cantidad = 3                     # literal int

precio = float(precio_texto)     # conversión de tipo
total = precio * cantidad * PRECIO_IVA   # expresión con operadores

if total > 50:                    # estructura de control (sangría)
    print("Envío gratis")
else:
    print("Envío con coste")

print(f"Total a pagar: {total:.2f} €")
```

Cópialo en VS Code, guárdalo como `compra.py`, ejecútalo con `python compra.py` en la terminal. Eso ya es "saber Python".

---

## 📺 Mejores recursos gratis en español (verificados ahora mismo)

Para no perder tiempo, en orden de recomendación:

1. **MoureDev – "Python de cero a experto"** (YouTube). Es el curso gratuito en español más completo y actualizado que hay; se le conoce como el rey de los cursos de Python en YouTube, muy popular en el mundo del desarrollo. Búscalo como "MoureDev Python" — tiene el vídeo completo y también dividido por capítulos. [genbeta](https://www.genbeta.com/a-fondo/ocho-canales-youtube-para-aprender-python-cero-nivel-experto-1/amp)
2. **freeCodeCamp en Español – curso de Python** — un curso gratuito completo que enseña los fundamentos de programación en Python con explicaciones detalladas, empezando por la instalación. Ideal si prefieres texto + práctica guiada en su web, no solo vídeo. [freecodecamp](https://www.freecodecamp.org/espanol/news/aprende-a-programar-en-python-desde-cero-curso-completo-gratis/)
3. **HolaMundo** (YouTube) — tiene un curso completo de más de cinco horas en un único vídeo; se recomienda verlo en tramos cortos para ir asimilando. [genbeta](https://www.genbeta.com/a-fondo/ocho-canales-youtube-para-aprender-python-cero-nivel-experto-1/amp)
4. **Documentación oficial** → docs.python.org/es (ya traducida) — para consultar dudas puntuales de sintaxis, es la fuente más fiable.

**Mi consejo real para ASIR:** no necesitas hacer un curso gigante de 40 horas para el Tema 1. Con MoureDev viendo solo los capítulos de "variables, tipos de datos, operadores y estructuras básicas" (1-2 horas) + practicar tú mismo los ejercicios de tu unidad, tienes de sobra. Luego, cuando lleguéis a bucles/condicionales/funciones en las siguientes unidades, vuelves al mismo canal.

Si en algún punto del tema te atascas con algo concreto (un ejercicio, un error de código, etc.), pégamelo aquí y lo resolvemos directo.



