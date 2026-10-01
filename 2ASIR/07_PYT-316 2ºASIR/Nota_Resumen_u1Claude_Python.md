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