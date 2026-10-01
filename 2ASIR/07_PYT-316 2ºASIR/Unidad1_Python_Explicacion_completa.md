# Unidad 1: Identificación de los elementos de un programa informático

Explicación paso a paso para principiantes.
Vamos a recorrer la unidad entera, apartado por apartado y en el mismo orden que el PDF. Si algo suena raro, no te agobies: todo viene con ejemplos. Te recomiendo copiar el código y probarlo tú mismo.
## Índice
- Objetivos de la unidad
- Introducción
- 1. Identificación de los elementos de un programa informático
- 2. Estructura y bloques fundamentales
- 3. Variables
- 4. Tipos de datos
- 5. Literales
- 6. Constantes
- 7. Operaciones y expresiones
- 8. Conversiones de tipo
- 9. Comentarios
- 10. Resumen
- 11. Glosario
- 12. Bibliografía
---
## Objetivos de la unidad
1. Reconocer elementos de un programa (su estructura y sus bloques básicos).
2. Entender qué es una variable, cómo se crea (declaración) y cómo se le da valor (asignación).
3. Distinguir los tipos de datos de Python (números, cadenas, booleanos, etc.).
4. Identificar y usar los literales.
5. Diferenciar constantes de variables, y aplicar operadores para construir expresiones (aritméticos, lógicos, relacionales...).
6. Convertir datos de un tipo a otro, sabiendo cuándo y cómo.
7. Usar comentarios para documentar el código, como buena práctica.
## Introducción
Programar: herramienta crucial para el desarrollo tecnológico y para resolver problemas. En esta unidad veremos, por orden:
- Estructura básica de un programa y sus bloques,
- variables y constantes (para guardar información),
- Tipos de datos (que determinan cómo se maneja esa información),
- los literales (valores concretos escritos en el código),
- los operadores y expresiones (para calcular y tomar decisiones),
- las conversiones de tipo,
- y los comentarios (para que el código se entienda y se pueda mantener).
---
## 1. Identificación de los elementos de un programa informático
Antes de escribir código conviene saber **de qué piezas está hecho un programa**. Conocerlas es crucial para diseñar, mantener y mejorar software. Este análisis sirve a desarrolladores y a cualquiera que quiera entender cómo funcionan las aplicaciones que usa a diario.
### Código fuente
- **Conjunto de instrucciones escritas en un lenguaje de programación** que le dicen a la computadora qué tarea ejecutar. El PDF lo llama "el alma de cualquier software": cada línea define una acción, una condición o una lógica que el sistema debe seguir. Dentro del código fuente encontramos:
	- **funciones** y **clases**,**variables**,**estructuras de control** (bucles y condicionales)y **bibliotecas externas**,
- Todo organizado en una **arquitectura coherente** para que el programa fluya correctamente. Puede estar escrito en distintos lenguajes: Python, Java, C++, etc.
- Además, debe ser **limpio, legible y estar bien documentado**. Así es más fácil mantenerlo, hacerlo crecer (escalabilidad) y adaptarlo a funcionalidades futuras.
### Datos y estructuras de datos
Todo programa maneja información: desde simples enteros y cadenas de texto hasta bases de datos relacionales complejas. Los programas **gestionan, transforman y almacenan datos** constantemente.
- Para organizar esa información de forma eficiente se usan **estructuras de datos**: listas, pilas, colas, árboles y grafos. Facilitan operaciones como **búsqueda, inserción, eliminación y ordenamiento**. Elegir bien la estructura influye en el rendimiento del software.
### Interfaz de usuario
Es el **Punto de contacto entre el usuario y el sistema**. Hay 2 tipos:
- **GUI (interfaz gráfica):** botones, menús, formularios, iconos y ventanas, diseñados pensando en la **usabilidad** y la **experiencia de usuario (UX)**. Una buena interfaz mejora la satisfacción del usuario y puede influir en la eficacia del software.
- **CLI (línea de comandos):** se escriben órdenes en texto. Siguen siendo esenciales en aplicaciones técnicas y sistemas donde la eficiencia y la precisión son primordiales.
### Módulos y componentes
En programas grandes, el código se divide en **módulos o componentes independientes**, cada uno con una función específica. Esa **modularidad** ayuda a organizar, mantener y ampliar el software.
- Los módulos se pueden **reutilizar** en otras partes del programa o en otros proyectos. Los desarrolladores usan a menudo **bibliotecas externas o frameworks** ya hechos para no "reinventar la rueda": traen funciones y herramientas que amplían el lenguaje base y aceleran el desarrollo.
### Algoritmos
Un **algoritmo** es una **secuencia finita de pasos lógicos** que resuelve un problema o ejecuta una tarea. Todo lo que hace un programa (ordenar una lista, autenticar a un usuario...) se apoya en un algoritmo.
- La **eficiencia** importa: un algoritmo mal diseñado puede ralentizar el software, gastar más recursos y empeorar la experiencia del usuario. Por eso uno de los grandes retos es implementar algoritmos **óptimos y escalables**.
### Archivos y sistemas de almacenamiento
Los datos que **no deben perderse al cerrar la aplicación** (configuraciones, resultados, registros) se guardan en **archivos locales, bases de datos o servicios en la nube**.
- Qué sistema elegir depende del **volumen de datos**, la **velocidad de acceso** y la **seguridad** necesaria. Muchas veces se usan **sistemas de gestión de bases de datos (DBMS)** como MySQL, PostgreSQL o MongoDB para manejar grandes cantidades de información de forma estructurada.
### Entorno de ejecución
Es lo que le da al programa los recursos para funcionar. Puede ser un **sistema operativo**, una **máquina virtual** (como la JVM de Java) o un **entorno de contenedores** (como Docker).
### Dependencias y gestores de paquetes
Un programa puede necesitar **componentes externos**:las **dependencias**, que deben estar instalados y actualizados. Los **gestores de paquetes** (npm, pip, Maven) facilitan instalarlos y gestionarlos.
### Documentación
Son los textos que explican **cómo funciona, se usa y se instala** el programa: desde manuales de usuario hasta guías técnicas para desarrolladores. Una buena documentación mejora la accesibilidad, reduce errores de uso y facilita el trabajo en equipo. En proyectos grandes se usan herramientas como **Javadoc, Sphinx o Doxygen**, que generan documentación automáticamente a partir del código fuente.
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
En Python **no es opcional: marca los límites de cada bloque**. Según la **PEP 8** (la guía oficial de estilo), se usan **cuatro espacios por nivel**.**Nunca mezcles espacios y tabulaciones**, porque crea errores difíciles de depurar.
```python
temperatura = 18
if temperatura < 20:
    print("Hace fresco")
    print("Pon tu chaqueta")
print("Programa finalizado")
```
Las 2 líneas dentro del `if` tienen la misma sangría, así que forman **un único bloque** y solo se ejecutan si la condición se cumple (18 < 20, sí). La tercera línea está pegada al margen, "sale" del bloque y **se ejecuta siempre**.
### Funciones
Son bloques etiquetados con **`def`**. Sirven para organizar el flujo y **evitar repetir código**.
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

---
## 3. Variables
Una **variable** es un espacio de almacenamiento para guardar datos que usaremos en distintas partes del programa. Más exactamente (Ramos, 2025): *un nombre simbólico que se refiere a objetos o valores almacenados en la memoria del ordenador*. Puede guardar números, cadenas de texto, listas, booleanos, diccionarios, etc.
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
Determina **dónde se puede usar** una variable. Dos tipos principales:
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
Solo dos valores: **`True`** o **`False`**. Son cruciales en condicionales y bucles.
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
---
## 5. Literales
Un **literal** es un **valor fijo escrito directamente en el código**, que el intérprete reconoce tal cual, sin evaluación adicional. Son la base de la sintaxis. Los tipos de literales:
- **Numéricos:** enteros (para contar o enumerar), flotantes (decimales) y complejos (cálculo científico). Se escriben normalmente en sistema decimal, aunque Python también admite otras bases numéricas para casos específicos.
- **Cadenas de texto:** secuencias de caracteres para datos alfanuméricos. Son esenciales cuando hay interacción con usuarios, lectura de archivos o comunicaciones en red. Tienen longitud variable, se pueden manipular y admiten múltiples codificaciones (útil para idiomas y símbolos diversos).
- **Booleanos:** `True`/`False`. Permiten establecer condiciones; son cruciales para tomar decisiones, validar resultados y crear bucles que se repiten según un criterio.
- **`None`:** ausencia de valor o estado indefinido. Se usa para inicializar variables que se asignarán después, para indicar que una función no produjo resultado concreto o para señalar la falta de un objeto válido.
- **Colecciones:** listas, tuplas, diccionarios y conjuntos, cada uno con características distintas en mutabilidad, orden y forma de acceso. Se pueden **anidar y combinar** para representar datos complejos.
Los literales pueden formar parte de **expresiones compuestas**: se combinan entre sí o con variables y operadores para producir nuevos resultados.

**Buenas prácticas:**
- Evitar los **valores mágicos** (números o textos sueltos cuyo significado no se entiende).
- Definir una **constante** cuando un literal se repite mucho.
- Mantener **coherencia en los tipos** para evitar errores sutiles.

**Diferencia literal vs. variable:** el literal **es el valor en sí mismo**; la variable es una **referencia que apunta a un valor** (que puede o no ser un literal). Ejemplo: en `nombre = "Ana"`, `nombre` es la variable y `"Ana"` es el literal. Esta distinción importa para la memoria, el flujo lógico y la depuración.

---
## 6. Constantes
Las **constantes** son valores que, **por convención**, no deberían cambiar durante la ejecución. Python **no tiene sintaxis específica** para declararlas (como sí pasa en Java o C++), pero hay una convención muy arraigada:
- Se escriben en **MAYÚSCULAS con guiones bajos** (`URL_API`, `PI`). Así cualquier desarrollador ve al instante que no debe modificarse, y se evitan sobrescrituras accidentales.
- Se declaran **al principio del archivo**: das una visión clara de los valores fundamentales y, si hay que cambiar alguno, están todos agrupados en un solo sitio.
- **No hay protección técnica** que impida cambiarlas: respetar la convención es **disciplina del programador**. En proyectos colaborativos mejora la legibilidad y reduce errores.
- En aplicaciones grandes es común tener **un archivo exclusivo de constantes** que se importa donde haga falta, sin redefinirlas.
- Si agrupan varios valores (**diccionarios o listas**), también van en mayúsculas, pero ojo: si son **mutables**, su contenido **sí puede cambiar** aunque el nombre no. Para inmutabilidad real, usa **tuplas** (u otras bibliotecas que permiten objetos inmutables).
---
## 7. Operaciones y expresiones
Python ofrece una amplia gama de operadores (W3Schools, s.f.), desde los aritméticos hasta los lógicos y los bit a bit. Usarlos bien da código más limpio, eficiente y fácil de mantener.
### Operadores aritméticos

| Operador | Nombre          | Qué hace                                   | Ejemplo          |
| -------- | --------------- | ------------------------------------------ | ---------------- |
| `+`      | Suma            | Une dos valores                            | `5 + 2` → 7      |
| `-`      | Resta           | Sustrae un valor de otro                   | `5 - 2` → 3      |
| `*`      | Multiplicación  | Multiplica dos valores                     | `5 * 2` → 10     |
| `/`      | División        | Divide, **devolviendo un float**           | `10 / 4` → 2.5   |
| `//`     | División entera | Divide y devuelve **solo la parte entera** | `10 // 4` → 2    |
| `%`      | Módulo          | Devuelve el **residuo** de la división     | `10 % 4` → 2     |
| `**`     | Exponenciación  | Eleva un número a la potencia de otro      | `10 ** 3` → 1000 |

```python
a = 10
b = 3
resultado = a ** b   # 1000
```
### Operadores de comparación
Comparan dos valores y devuelven un **booleano**. Son esenciales en `if`, `while` y expresiones lógicas.

| Operador | Significado |
|---|---|
| `==` | Igual a |
| `!=` | Diferente de |
| `>` | Mayor que |
| `<` | Menor que |
| `>=` | Mayor o igual que |
| `<=` | Menor o igual que |

```python
edad = 18
mayor = edad >= 18   # True
```
### Operadores lógicos
Combinan varias condiciones:
- **`and`** (Y): `True` si **ambas** son verdaderas.
- **`or`** (O): `True` si **al menos una** es verdadera.
- **`not`** (negación): **invierte** el valor booleano.
```python
edad = 25
tiene_dni = True
puede_votar = edad >= 18 and tiene_dni   # True
```
### Operadores de asignación
Guardan valores en variables. Además del `=`, hay formas abreviadas que **combinan asignación con una operación**:

`=` (simple), `+=` (suma y asigna), `-=` (resta y asigna), `*=` (multiplica y asigna), `/=` (divide y asigna), `//=` (división entera y asigna), `%=` (módulo y asigna), `**=` (exponenciación y asigna).
```python
x = 5
x += 3   # equivale a x = x + 3 → x ahora es 8
```
### Operadores bit a bit
Trabajan directamente con los **bits** (los 0 y 1) de los números. Se usan menos en aplicaciones comunes, pero son fundamentales en programación de bajo nivel, criptografía y sistemas embebidos.
- `&` → AND bit a bit
- `|` → OR bit a bit
- `^` → XOR bit a bit
- `~` → NOT bit a bit
- `<<` → desplazamiento a la izquierda
- `>>` → desplazamiento a la derecha
```python
a = 60     # 0011 1100
b = 13     # 0000 1101
c = a & b  # 0000 1100 = 12
```
El AND pone un 1 solo en las posiciones donde **ambos** números tienen 1; por eso sale `0000 1100`, que en decimal es 12.
### Operadores de identidad
En Python las variables son **referencias a objetos**. `is` e `is not` te dicen si dos variables apuntan **al mismo objeto en memoria**.
```python
x = [1, 2, 3]
y = x          # y apunta al MISMO objeto que x
z = list(x)    # z es una copia: un objeto distinto
print(x is y)  # True
print(x is z)  # False
```
### Operadores de pertenencia
`in` (existe en) y `not in` (no existe en). Sirven para saber si un valor está dentro de una lista, tupla, diccionario o cualquier colección.
```python
frutas = ['manzana', 'pera', 'naranja']
print('pera' in frutas)   # True
```
### Expresiones
Una **expresión** es una combinación de **valores, variables, operadores y llamadas a funciones** que, al evaluarse, **devuelve un resultado**. Es la unidad mínima de ejecución de un programa. Pueden ser tan simples como una suma o tan complejas como condicionales anidadas con funciones.
```python
def es_adulto(edad):
    return edad >= 18

nombre = "Luis"
edad = 20
mensaje = f"{nombre} es adulto" if es_adulto(edad) else f"{nombre} es menor"
print(mensaje)
```
Paso a paso: `es_adulto(20)` devuelve `True`; como la condición es verdadera, `mensaje` toma el primer texto. (La `f` delante de las comillas permite meter variables dentro del texto con `{}`.) Se imprime: **`Luis es adulto`**.

---
## 8. Conversiones de tipo
Aunque Python es dinámicamente tipado, muchas veces hay que **convertir un tipo en otro** para que el programa funcione bien o para evitar errores. Se llama **conversión de tipo** o **type casting**. Pueden ser:
- **Explícitas:** tú indicas el cambio usando funciones como `int()`, `float()`, `str()`...
- **Implícitas:** Python las hace solo, normalmente cuando puede hacerlo **sin perder datos** (Programar, s.f.).
### Funciones de conversión
- **`int()`**: convierte un número o una cadena numérica en entero.
  ```python
  int('10')     # 10
  int(10.99)    # 10  (se queda con la parte entera; no redondea)
  ```
- **`float()`**: convierte a decimal.
  ```python
  float(5)         # 5.0
  float('3.1416')  # 3.1416
  ```
- **`str()`**: convierte **cualquier** dato a texto.
  ```python
  str(100)    # '100'
  str(True)   # 'True'
  ```
- **`bool()`**: los valores **vacíos, el cero y `None`** dan `False`; el resto, `True`.
  ```python
  bool(0)       # False
  bool('Hola')  # True
  ```
- **`list()`**: convierte cualquier iterable en lista.
  ```python
  list('python')   # ['p', 'y', 't', 'h', 'o', 'n']
  ```
- **`tuple()`**: convierte un iterable en tupla.
  ```python
  tuple([1, 2, 3])   # (1, 2, 3)
  ```
- **`set()`**: convierte un iterable en conjunto, **eliminando duplicados**.
  ```python
  set([1, 2, 2, 3])   # {1, 2, 3}
  ```
### Conversión implícita
```python
a = 5
b = 2.0
resultado = a + b   # 7.0 (float)
```
Python convierte `a` a `float` antes de sumar, para **preservar la precisión**.
### El error típico: `ValueError`
Si intentas convertir algo que no se puede, hay error:
```python
int('abc')     # Error: ValueError
float('uno')   # Error: ValueError
```
Por eso conviene **validar o limpiar los datos antes** de convertirlos.
### Conversiones entre estructuras
```python
# De lista a cadena
lista = ['a', 'b', 'c']
cadena = ''.join(lista)    # 'abc'

# De cadena a lista
cadena = '1234'
lista = list(cadena)       # ['1', '2', '3', '4']

# De diccionario a lista de claves
dic = {'a': 1, 'b': 2}
claves = list(dic)         # el PDF indica ['a']
```

> **Nota del profe:** el comentario del PDF en la última línea tiene una errata. Como `list(dic)` recoge **todas** las claves, el resultado real es `['a', 'b']`.
### Verificar el tipo antes de convertir
```python
valor = '25'
if type(valor) == str:
    valor_entero = int(valor)
```
Evita errores inesperados, sobre todo con entradas de usuarios o datos externos.
### Ejemplo práctico: números de un formulario web
```python
num1 = '15'
num2 = '30'

suma = int(num1) + int(num2)   # 45
```
**Sin** la conversión, `'15' + '30'` daría `'1530'`: una **concatenación de textos**, no una suma matemática.

---
## 9. Comentarios
Los **comentarios** son texto que el **intérprete ignora**. No cambian el comportamiento del código: explican **qué hace, por qué lo hace así o cómo usarlo**. Son cruciales cuando varios desarrolladores trabajan en el mismo proyecto o cuando revisas código después de semanas o meses. Hay dos tipos: **de una sola línea** y **multilínea o de bloque**.

> **Sabías que:** el símbolo `#` viene heredado de lenguajes mucho más antiguos, como el shell script de Unix. Guido van Rossum, creador de Python, lo mantuvo por su simplicidad y familiaridad. Algunos desarrolladores han dejado mensajes graciosos, advertencias misteriosas o hasta poemas en comentarios, "como pequeñas cápsulas del tiempo".

### Una línea
Empieza con `#`; todo lo que sigue se ignora. Puede ir solo en una línea o al final de una línea de código. Deben ser **claros, concisos y relacionados directamente con el código**.
```python
# Este es un comentario de una sola línea
print("Hola Mundo")  # También se puede comentar al final de una línea de código
```
### Multilínea
Python no tiene sintaxis especial (como `/* */` en C), así que se pone `#` al inicio de **cada línea**:
```python
# Este es un comentario
# que se extiende por
# varias líneas
```
Otra alternativa: **cadenas de varias líneas entre comillas triples** que no se asignan a ninguna variable. Técnicamente **no son comentarios**, y **no es la forma recomendada** de comentar:
```python
"""
Este texto no se almacena en ninguna variable.
Es común usar este tipo de cadenas como comentarios multilínea.
Sin embargo, no es la forma recomendada para comentar código.
"""
```
### Buenas prácticas
- **Evitar comentar lo obvio.**
- **Actualizar los comentarios** si cambias el código: uno desactualizado puede ser peor que ninguno.
- Comentar **el "porqué"** más que el "qué": el código ya muestra lo que hace; el comentario explica la razón de una decisión.
- Ser **concisos y específicos**.
- Mantener un **estilo consistente**.
### En funciones y clases: docstrings + comentarios internos
Lo ideal es usar **docstrings**, complementados con comentarios internos:
```python
def calcular_area(base, altura):
    """
    Calcula el área de un triángulo.

    Parámetros:
        base (float): La base del triángulo.
        altura (float): La altura del triángulo.
    Retorna:
        float: El área calculada.
    """
    return (base * altura) / 2  # Fórmula del área de un triángulo
```
El docstring da la **visión general**; el comentario en línea detalla la **lógica matemática**.
### Cuidado con el exceso
Demasiados comentarios saturan el código y lo hacen difícil de leer. Idealmente el código es tan claro que solo hace falta comentar para: **justificar una solución compleja**, **advertir de un comportamiento inesperado** o **dar contexto adicional**.
### Deshabilitar líneas temporalmente
Durante el desarrollo puedes "comentar" una línea para desactivarla y probar variantes sin borrarla:
```python
# print("Esta línea está deshabilitada temporalmente")
```
Antes de la versión final, esas líneas deben **eliminarse o documentarse bien**.
### Trabajo en equipo
Los comentarios son vitales para **compartir decisiones de diseño**, **advertir sobre dependencias** y **explicar fragmentos que interactúan con otros módulos**:
```python
# Esta función se conecta al servicio externo de pagos.
# No modificar sin consultar con el equipo de backend.
```
### Normas de la PEP 8 para comentarios (van Rossum, 2001)
- Empezar con **mayúscula**.
- Evitar errores gramaticales u ortográficos.
- **Un espacio después del `#`**.
- Usar **oraciones completas** cuando sea necesario.

---
## 10. Resumen (repaso rápido)
- Un programa en Python se organiza en **bloques** marcados por la **indentación** (no por llaves).
- Las **variables** guardan datos; no se declara el tipo (**tipado dinámico**); se crean con `=`.
- Tipos básicos: **numéricos** (`int`, `float`, `complex`), **booleanos** (`True`, `False`), **texto** (`str`) y **colecciones** (`list`, `tuple`, `set`, `dict`).
- Los **literales** son valores fijos escritos en el código; sirven para inicializar variables o definir condiciones.
- Las **constantes** se simulan por convención (mayúsculas), lo que mejora legibilidad y mantenimiento.
- Los **operadores** se dividen en aritméticos (`+ - * / // % **`), de comparación (`== != < > <= >=`), lógicos (`and or not`), de asignación (`= += -=`...) y de pertenencia (`in`, `not in`).
- Las **expresiones** combinan operadores y operandos para obtener un resultado.
- Las **conversiones** (`int()`, `float()`, `str()`, `list()`...) adaptan los datos; por ejemplo `int("23")`.
- Los **comentarios** (`#`) explican código sin afectar a la ejecución: documentan, aclaran intenciones o desactivan líneas temporalmente, y mejoran el trabajo en equipo.
---
## 11. Glosario explicado en fácil
- **Programa informático:** serie de instrucciones escritas para que la computadora haga tareas concretas, desde cálculos simples hasta aplicaciones complejas.
- **Estructura del programa:** cómo se organizan sus líneas de código. Un programa típico mezcla instrucciones secuenciales, bloques (como funciones) y estructuras de control (bucles y condiciones).
- **Bloque de código:** grupo de líneas que se ejecutan juntas. En Python se identifican por la **indentación**; todo lo que está dentro de una función o bucle pertenece al mismo bloque.
- **Variable:** espacio con nombre donde se guarda información que puedes usar o cambiar luego. `edad = 30` crea la variable `edad` con el número 30.
- **Tipo de dato:** indica qué clase de valor puede contener una variable. Principales: entero, flotante (con decimales), texto (*string*) y booleano (verdadero/falso).
- **Literal:** valor fijo escrito directamente en el código. En `nombre = "Ana"`, `"Ana"` es un literal de texto.
- **Constante:** como una variable, pero su valor no debe cambiar. Python no tiene constantes "oficiales"; por convención se escriben en mayúsculas (`PI = 3.14`).
- **Operador:** símbolo que realiza una acción sobre uno o más valores (el `+` suma dos números). Los hay matemáticos, lógicos y de comparación.
- **Expresión:** combinación de variables, operadores y valores literales que produce un nuevo valor, como `a + b * 2`.
- **Conversión de tipo (casting):** cambiar el tipo de un valor. Con el texto `"5"`, `int("5")` lo convierte en número para poder operar con él.
- **Comentario:** nota en el código que el programa ignora. Explica lo que hace el código para que otros (o tú mismo, más adelante) lo entiendan. Se escribe con `#`.
- **Entrada de datos:** forma en que el programa recibe información del usuario. En Python se usa **`input()`**, que pide al usuario que escriba algo por teclado.
- **Salida de datos:** forma en que el programa muestra información. Se usa **`print()`** para mostrar texto o resultados en pantalla.
- **Función:** conjunto de instrucciones agrupadas que realizan una tarea específica y se pueden usar varias veces sin repetir código. `print()` es una función.
- **Indentación:** no es solo estética; define qué instrucciones pertenecen a qué bloque. Se usan cuatro espacios (el glosario dice "o una tabulación", pero recuerda lo de la sección 2: **nunca mezclar** espacios y tabulaciones).
- **Palabra reservada:** palabra que Python usa para su propia sintaxis y que **no puedes usar como nombre de variable**: `if`, `while`, `def`, `return`...
- **Condición:** afirmación que puede ser verdadera o falsa y sirve para tomar decisiones. En `if edad > 18:` el bloque solo se ejecuta si la condición es verdadera.
- **Bucle (loop):** permite repetir una acción varias veces. Hay dos principales: **`for`** y **`while`**. Por ejemplo, un bucle puede imprimir los números del 1 al 10.
- **Error de sintaxis:** error que ocurre cuando el código no está bien escrito; por ejemplo, olvidar los dos puntos `:` al final de un `if`.
- **Depuración:** proceso de revisar el código para encontrar y corregir errores. Python ayuda mostrando mensajes de error que indican dónde está el problema.
---
## 12. Bibliografía
4 fuentes:
- **Programar, C. P. (s.f.)**: *Conversión entre tipos de datos en Python* (apartado 8).
- **Ramos, L. P. (2025)**: *Variables in Python: Usage and Best Practices*, Real Python (apartado 3).
- **van Rossum, G. W. (2001)**: *Guía de estilo para el código Python, PEP 8* (apartado 9).
- **W3Schools (s.f.)**: *Python Tutorial, Python Operators* (apartado 7).
---
