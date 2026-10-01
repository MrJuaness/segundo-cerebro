# U1.Identificación de los elementos de un programa informático
## 1. Identificación de los elementos de un programa informático
Antes de escribir código, saber **de qué piezas está hecho un programa**, para diseñar, mantener y mejorar software, un análisis que sirve a desarrolladores y a cualquiera que quiera entender cómo funcionan las aplicaciones que usa a diario.
### Código fuente
- **Conjunto de instrucciones escritas en un lenguaje de programación** que le dicen a al PC qué tarea ejecutar. El PDF lo llama "el alma de cualquier software": cada línea define una acción, una condición o una lógica que el sistema debe seguir.Dentro del código fuente tenemos:
	- **funciones** y **clases**,**variables**,**estructuras de control** (bucles y condicionales)y **bibliotecas externas**.
- Todo organizado en una **arquitectura coherente** para que el programa fluya bien. Puede estar escrito en distintos lenguajes: Python, Java, C++, etc.
- Debe ser **limpio, legible y estar bien documentado**. Así es más fácil mantenerlo, hacerlo crecer (escalabilidad) y adaptarlo a funcionalidades futuras.
### Datos y estructuras de datos
Todo programa maneja información: desde simples enteros y cadenas de texto hasta bases de datos relacionales complejas. Los programas **gestionan, transforman y almacenan datos** constantemente.
- Para organizar esa información de forma eficiente se usan **estructuras de datos**: listas, pilas, colas, árboles y grafos. Facilitan operaciones como **búsqueda, inserción, eliminación y ordenamiento**. Elegir bien la estructura influye en el rendimiento del software.
### Interfaz de usuario
**Punto de contacto entre el usuario y el sistema**. Hay 2 tipos:
- **GUI (interfaz gráfica):** botones, menús, formularios, iconos y ventanas, diseñados pensando en la **usabilidad** y la **experiencia de usuario (UX)**. Una buena interfaz mejora la satisfacción del usuario y puede influir en la eficacia del software.
- **CLI (línea de comandos):** se escriben órdenes en texto. Crucial en aplicaciones técnicas y sistemas donde la eficiencia y la precisión es crucial
### Módulos y componentes
En programas grandes, el código se divide en **módulos o componentes independientes**, cada uno con una función específica. Esa **modularidad** ayuda a organizar, mantener y ampliar el software.
- Los módulos se pueden **reutilizar** en otras partes del programa o en otros proyectos. Los desarrolladores usan a menudo **bibliotecas externas o frameworks** ya hechos para no "reinventar la rueda": traen funciones y herramientas que amplían el lenguaje base y aceleran el desarrollo.
### Algoritmos
**Algoritmo.** **Secuencia finita de pasos lógicos** que resuelve un problema o ejecuta una tarea. Todo lo que hace un programa (ordenar una lista, autenticar a un usuario...)se apoya en un algoritmo.
- La **eficiencia** importa: un algoritmo mal diseñado ralentiza el software, gasta más recursos y empeora la experiencia del usuario, por eso hay que implementar algoritmos **óptimos y escalables**.
### Archivos y sistemas de almacenamiento
Los datos que **no deben perderse al cerrar la aplicación** (configuraciones, resultados, registros) se guardan en **archivos locales, bases de datos o servicios en la nube**.
- Qué sistema elegir depende del **volumen de datos**, la **velocidad de acceso** y la **seguridad** necesaria. Muchas veces se usan **sistemas de gestión de bases de datos (DBMS)** como MySQL, PostgreSQL o MongoDB para manejar grandes cantidades de información de forma estructurada.
### Entorno de ejecución
Le da al programa los recursos para funcionar. Puede ser un **sistema operativo**, una **máquina virtual** (como la JVM de Java) o un **entorno de contenedores** (como Docker).
### Dependencias y gestores de paquetes
Un programa puede necesitar **componentes externos**:las **dependencias**, que deben estar instalados y actualizados. Los **gestores de paquetes** (npm, pip, Maven) facilitan instalarlos y gestionarlos.
### Documentación
Textos que explican **cómo funciona, se usa e instala** el programa: manuales de usuario, guías técnicas para desarrolladores. Una **buena documentación** mejora la accesibilidad, reduce errores de uso y facilita el trabajo en equipo. En proyectos grandes se usan herramientas como **Javadoc, Sphinx o Doxygen**, que generan documentación automáticamente a partir del código fuente.
### Pruebas y validación
Los programas deben probarse para garantizar que funcionan. Las pruebas pueden ser **manuales o automatizadas** y evalúan usabilidad, seguridad, compatibilidad y rendimiento. Las más comunes:
- **Unitarias:** comprueban que cada función funciona de forma independiente.
- **De integración:** evalúan cómo interactúan distintos módulos entre sí.
- **De sistema:** comprueban el comportamiento del programa como un todo.
- **De aceptación:** validan que el software cumple los requisitos del usuario final.
### Control de versiones
Herramientas como **Git** permiten **registrar los cambios** del código, **colaborar en equipo** y mantener un **historial completo** del desarrollo. Es vital sobre todo cuando varios desarrolladores trabajan a la vez sobre el mismo código base.

---
## 2. Estructura y bloques fundamentales
Aquí empieza lo propio de Python. Muchos lenguajes usan llaves `{}` o palabras como `BEGIN/END` para marcar dónde empieza y termina un bloque de código. **Python usa la sangría** (espacios al principio de la línea). Entender esto y cómo se conectan las piezas (módulos, funciones, clases y paquetes) nos permite escribir código más legible, mantenible y robusto.
### El script
Un **script** es un archivo con extensión **`.py`** cuyas instrucciones **se ejecutan de arriba abajo**. Dentro puedes encontrar:
- **Importaciones (`import`):** traen funcionalidades de la biblioteca estándar o de paquetes externos.
- **Constantes y variables globales:** valores accesibles desde cualquier punto del archivo.
- **Definiciones de funciones (`def`) y clases (`class`):** guardan lógica reutilizable.
- **Código ejecutable:** instrucciones que se lanzan al ejecutar el script directamente.
### Patrón profesional: el bloque de protección
```python
def main():
    # Punto de entrada real
    ...

if __name__ == "__main__":
    main()
```
Metes tu código principal dentro de una función `main()`, y solo se llama si el archivo se ejecuta directamente. Así **evitas que el código se ejecute al importar** ese archivo como módulo desde otro proyecto. (Los `...` significan "aquí iría tu código".)
### La sangría (indentación)
En Python **no es opcional: marca los límites de cada bloque**. Según la **PEP 8** (la guía oficial de estilo), se usan **4 espacios por nivel**.**Nunca mezcles espacios y tabulaciones**, porque crea errores difíciles de depurar.
```python
temperatura = 18
if temperatura < 20:
    print("Hace fresco")
    print("Pon tu chaqueta")
print("Programa finalizado")
```
Las 2 líneas dentro del `if` tienen la misma sangría, así que forman **un único bloque** y solo se ejecutan si la condición se cumple (18 < 20, sí). La tercera línea está pegada al margen, "sale" del bloque y **se ejecuta siempre**.
### Funciones
Bloques etiquetados con **`def`**, son para organizar el flujo y **evitar repetir código**.
```python
def calcular_area_rectangulo(base, altura):
    """Devuelve el área de un rectángulo."""
    return base * altura
```
Buenas prácticas:
- **Nombre descriptivo**, en minúsculas y con guiones bajos.
- **Parámetros claros** (`base`, `altura`: los datos que recibe).
- **Docstring** entre triples comillas que explica para qué sirve y cómo se usa.
- `return` devuelve el resultado.
Las funciones favorecen el principio **DRY (Don't Repeat Yourself, "no te repitas")** y permiten delegar tareas y probarlas de forma aislada.
### Clases y POO
En proyectos que crecen rápido, la **POO (Programación Orientada a Objetos)** añade estructura:
```python
class Vehiculo:
    def __init__(self, marca, modelo):
        self.marca = marca
        self.modelo = modelo

    def describir(self):
        return f"{self.marca} {self.modelo}"
```
- `__init__` es el **constructor**: recibe parámetros y los guarda como **atributos**.
- Los **métodos** (como `describir`) usan **`self`** para acceder a los datos de ese objeto concreto (la "instancia").
- Las clases **encapsulan estado y comportamiento** en entidades coherentes que se pueden combinar, **heredar** y ampliar.
### Módulos y paquetes
Cuando un archivo no basta, dividimos el proyecto en **módulos** (archivos `.py`) y **paquetes** (carpetas con un `__init__.py`). Esto ayuda a agrupar funcionalidades relacionadas, reducir dependencias cruzadas y acelerar tiempos de compilación e importación.
```
mi_aplicacion/
│
├── __init__.py
├── utilidades.py
├── modelos/
│   ├── __init__.py
│   └── usuario.py
└── servicios/
    ├── __init__.py
    └── autenticacion.py
```
Para usar la clase `Usuario` desde otro sitio:
```python
from mi_aplicacion.modelos.usuario import Usuario
```
Este esquema refleja la arquitectura y permite a cualquiera localizar rápido cada pieza.
### Alcance de variables: LEGB
Python maneja **4 niveles de alcance**, de dentro hacia fuera:
- **L**ocal: dentro de la función actual.
- **E**nclosing: funciones que contienen a otra función (niveles intermedios).
- **G**lobal: el nivel del archivo.
- **B**uilt-in: lo que Python trae incorporado.
Conocerlos evita errores de "sombra de variables" (que un nombre tape a otro) y el uso indebido de globales.
```python
PI = 3.14159  # Global

def calcular_circunferencia(radio):
    # Local (dentro de la función)
    return 2 * PI * radio
```
La función puede **leer** `PI` (global). Si necesitas **escribir** en una global desde dentro de una función, usas **`global`**; para niveles intermedios, **`nonlocal`**. Aun así, conviene **limitar las globales** para que el código sea predecible y testeable.
### Manejo de errores: try / except / else / finally
```python
try:
    archivo = open("datos.txt")
    procesar(archivo)
except FileNotFoundError as exc:
    logger.error("Archivo no encontrado: %s", exc)
else:
    print("Procesamiento exitoso")
finally:
    archivo.close()
```
- **`try`**: delimita el bloque "de riesgo", donde algo puede fallar.
- **`except`**: captura errores **específicos** (aquí, que el archivo no exista).
- **`else`**: se ejecuta **solo si no hubo excepciones**.
- **`finally`**: se ejecuta **siempre**; ideal para liberar recursos (cerrar archivos, etc.).
(`logger` es una herramienta para registrar mensajes; el PDF la usa sin entrar en detalle.) Usar excepciones en lugar de "códigos de error" mantiene el flujo limpio y declara de forma explícita qué puede fallar.

> **Sabías que:** `else` es poco conocido pero útil: separa la lógica normal del manejo de errores. Y `finally` se ejecuta pase lo que pase, **incluso si hay un `return` antes**, por eso es el lugar ideal para cerrar archivos o conexiones.

> **Nota del profe:** en este ejemplo concreto, si el archivo no existe, la variable `archivo` nunca llega a crearse y el `finally` daría otro error. Justo por eso el PDF presenta a continuación `with`, que lo resuelve mejor.

### El protocolo de contexto: `with`
Garantiza el **cierre automático** de recursos (archivos, conexiones, locks):
```python
with open("datos.txt") as archivo:
    datos = archivo.read()
# Aquí el archivo ya está cerrado
```
Por detrás, Python llama a los métodos **`__enter__`** (al entrar) y **`__exit__`** (al salir), y libera el recurso incluso si hay excepciones. Tú también puedes crear tus propios *context managers* con `@contextmanager` o implementando esos dos métodos "mágicos".
### Decoradores
Un **decorador** recibe una función y devuelve otra **con comportamiento ampliado**:
```python
def loggeable(funcion):
    def wrapper(*args, **kwargs):
        logger.info("Ejecutando %s", funcion.__name__)
        return funcion(*args, **kwargs)
    return wrapper

@loggeable
def saludar(nombre):
    print(f"Hola, {nombre}")
```
`wrapper` registra un mensaje ("Ejecutando saludar") y luego llama a la función original con los mismos argumentos. `@loggeable` es **azúcar sintáctica** (un atajo) de `saludar = loggeable(saludar)`. Permite añadir capas transversales (logging, caché, validación) **sin tocar la lógica central**.
### Type hints
Con los *type hints* (PEP 484) se **anotan** los tipos de parámetros y retornos:
```python
def area_circulo(radio: float) -> float:
    return PI * radio ** 2
```
Significa: `radio` debe ser `float` y la función devuelve un `float`. Herramientas como **mypy** o **Pyright** analizan estos "contratos" y detectan incompatibilidades **antes de ejecutar**, aumentando la seguridad y la claridad.

### Pruebas unitarias
Viven en carpetas como `tests/` y usan **unittest** o **pytest**. Cada caso de prueba verifica un comportamiento:
```python
def test_area_rectangulo():
    assert calcular_area_rectangulo(3, 4) == 12
```
`assert` comprueba que algo es cierto (3 × 4 = 12). Con **CI/CD**, las pruebas se ejecutan automáticamente **tras cada `push`** (cada vez que subes cambios), garantizando que ninguna función nueva rompa las existentes.
## 3. Variables
**Variable.** Espacio de almacenamiento para guardar datos que usaremos en distintas partes del programa. Más exactamente (Ramos, 2025): *un nombre simbólico que se refiere a objetos o valores almacenados en la memoria del PC*. Puede guardar números, cadenas de texto, listas, booleanos, diccionarios, etc.
### Tipado dinámico
En Python **no hay que declarar el tipo** antes de usar la variable. El tipo se determina **automáticamente al asignar un valor**.
```python
nombre = "Carlos"   # cadena (str)
edad = 30           # entero (int)
activo = True       # booleano (bool)
```
### Reglas para los nombres
- Debe empezar por **letra o guion bajo (`_`)**, nunca por número.
- Solo puede contener **letras, números y guiones bajos**.
- **Sin espacios** ni caracteres especiales como `@`, `#`, `$`.
- **No usar palabras reservadas** (`for`, `if`, `def`, `class`...).
- Se recomiendan **nombres descriptivos**.
```python
nombre_usuario = "Ana"     # Correcto
1nombre = "Ana"            # Incorrecto: da error (empieza por número)
```
### Asignación
Se usa el signo **`=`**: lo de la derecha se guarda en el nombre de la izquierda.

**Intercambio de valores** (muy cómodo en Python):
```python
x = 5
y = 10
x, y = y, x   # Ahora x vale 10 e y vale 5
```

**Mismo valor a varias variables a la vez:**
```python
a = b = c = 100
```
### Tipos principales que puede guardar una variable
`int` (enteros), `float` (decimales), `str` (texto), `bool` (booleanos), `list` (listas), `tuple` (tuplas), `dict` (diccionarios) y `set` (conjuntos).
```python
entero = 20
decimal = 20.5
texto = "Hola mundo"
booleano = False
lista = [1, 2, 3]
tupla = (1, 2, 3)
diccionario = {"nombre": "Carlos", "edad": 30}
conjunto = {1, 2, 3}
```
### Ámbito (scope)
Determina **dónde se puede usar** una variable. 2 tipos principales:
- **Locales:** definidas dentro de una función; solo existen ahí.
- **Globales:** definidas fuera de cualquier función; accesibles en todo el archivo.
```python
def saludar():
    mensaje = "Hola"
    print(mensaje)

saludar()
# print(mensaje)  # Daría error: 'mensaje' es local
```

```python
mensaje = "Hola mundo"   # global

def saludar():
    print(mensaje)       # puede leerla

saludar()
```
Para **modificar** una global dentro de una función hay que usar la palabra clave **`global`**:
```python
contador = 0

def incrementar():
    global contador
    contador += 1
```
### Buenas prácticas con variables
- Nombres **descriptivos**, evitando abreviaciones innecesarias.
- **Evitar sobrescribir** variables, sobre todo si ya se usan en otro ámbito.
- Estilo **consistente** (por ejemplo `snake_case`: palabras en minúscula unidas por `_`).
- **Inicializar** las variables antes de usarlas.
- **Comentar** cuando el significado no sea evidente.
```python
precio_producto = 150.75
cantidad_comprada = 3
total_pagar = precio_producto * cantidad_comprada
```
### Type hints en variables
Aunque no es obligatorio, puedes anotar el tipo para mejorar la legibilidad y ayudar a las herramientas de análisis estático. Son útiles sobre todo en proyectos grandes:
```python
nombre: str = "Lucía"
edad: int = 28
activo: bool = True
```
### Constantes (adelanto)
Python **no tiene constantes reales**, pero existe una convención: escribir el nombre **en mayúsculas** para indicar que no debe cambiar. Aunque técnicamente se pueden modificar, por convención no deberían.
```python
PI = 3.14159
URL_API = "https://api.ejemplo.com"
```
---
## 4. Tipos de datos
Cada valor en Python tiene un **tipo**, que determina cómo se maneja y qué se puede hacer con él. Python, al ser de alto nivel y dinámico, trae muchos tipos integrados: números, texto, listas, colecciones complejas...
> **Sabías que:** puedes escribir `x = 5` y luego `x = "ahora soy un texto"` y Python lo acepta sin quejarse. Esa flexibilidad hace a Python accesible para principiantes, pero puede llevar a **errores difíciles de detectar** si no prestas atención al tipo con el que trabajas.
### Tipos numéricos
- **`int`**: enteros, positivos o negativos, **sin parte decimal**. Sirven para contar, iterar en bucles, hacer divisiones enteras... Admiten números **tan grandes como permita la memoria** de la máquina.
  ```python
  numero = 10
  ```
- **`float`**: números reales **con parte decimal**; ideal cuando necesitas precisión decimal.
  ```python
  precio = 19.99
  ```
- **`complex`**: números complejos con formato `a + bj` (`a` parte real, `b` parte imaginaria). Poco comunes, pero muy útiles en aplicaciones científicas y de ingeniería.
  ```python
  numero_complejo = 2 + 3j
  ```
### Cadenas de texto (`str`)
Son **secuencias inmutables de caracteres** ("inmutable" = una vez creada, no se puede cambiar por dentro). Se escriben entre comillas **simples, dobles o triples** (las triples sirven para texto de varias líneas).
```python
nombre = "Python es poderoso"
```
Permiten muchas operaciones: concatenación (unir), búsqueda, reemplazo, formateo...
### Booleanos (`bool`)
Solo 2 valores: **`True`** o **`False`**. Son cruciales en condicionales y bucles.
```python
es_mayor = True
```
Dato curioso: el booleano es una **subclase del entero**, así que **`True` equivale a 1 y `False` a 0**.

### `None`
Indica la **ausencia de valor**. Se usa como valor de retorno por defecto o para inicializar variables que aún no tienen contenido.
```python
resultado = None
```
### Secuencias (colecciones ordenadas)
- **Listas (`list`)**: ordenadas y **mutables** (se pueden modificar después de crearlas). Puedes agregar, eliminar, modificar o acceder a elementos con **índices**.
  ```python
  frutas = ["manzana", "banana", "naranja"]
  ```

- **Tuplas (`tuple`)**: como las listas pero **inmutables**. Se usan para proteger datos de modificaciones accidentales.
  ```python
  coordenadas = (10.0, 20.5)
  ```

- **Rangos (`range`)**: secuencias de números enteros, muy usadas en bucles `for`.
  ```python
  for i in range(5):
      print(i)    # imprime 0, 1, 2, 3, 4
  ```
### Conjuntos
- **`set`**: colecciones **sin orden y sin duplicados**, mutables. Ideales para eliminar duplicados y para operaciones de teoría de conjuntos (**unión, intersección, diferencia**).
  ```python
  colores = {"rojo", "verde", "azul"}
  ```

- **`frozenset`**: versión **inmutable** del conjunto; útil cuando necesitas usar conjuntos como claves de un diccionario.
  ```python
  dias = frozenset(["lunes", "martes", "miércoles"])
  ```
### Diccionarios (`dict`)
Colecciones de **pares clave-valor**: mutables, desordenados, y permiten acceder rápido al dato mediante su clave. Son de los tipos más usados por su flexibilidad y eficiencia.
```python
persona = {
    "nombre": "Juan",
    "edad": 30,
    "ciudad": "Madrid"
}
```
### Convertir, comprobar tipos
- Conversión: `int()`, `float()`, `str()`, `list()`, `set()`... (lo vemos a fondo en el apartado 8).
  ```python
  numero = int("100")
  decimal = float("10.5")
  texto = str(25)
  ```
  Útil cuando los datos vienen de formularios, archivos o bases de datos.

- **`type()`** te dice el tipo:
  ```python
  print(type("Hola"))   # <class 'str'>
  ```

- **`isinstance()`** comprueba si un valor es de un tipo concreto:
  ```python
  isinstance(10, int)   # True
  ```