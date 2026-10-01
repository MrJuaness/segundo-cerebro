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
En Python **no es opcional: marca los límites de cada bloque**. Según la **PEP 8** (la guía oficial de estilo), se usan **cuatro espacios por nivel**. Y **nunca mezcles espacios y tabulaciones**, porque genera errores difíciles de depurar.

```python
temperatura = 18
if temperatura < 20:
    print("Hace fresco")
    print("Pon tu chaqueta")
print("Programa finalizado")
```

Las dos líneas dentro del `if` tienen la misma sangría, así que forman **un único bloque** y solo se ejecutan si la condición se cumple (18 < 20, sí). La tercera línea está pegada al margen, "sale" del bloque y **se ejecuta siempre**.

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

Python maneja **cuatro niveles de alcance**, de dentro hacia fuera:

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