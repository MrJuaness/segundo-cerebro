# Unidad 1.Instalación y configuración de un sistema gestor de base de datos
## Mini-diccionario para empezar
Estas palabras aparecen todo el rato, así que mejor tenerlas claras desde ya:
- **Tabla**: donde se guardan los datos, en filas y columnas (como una hoja de Excel).
- **Campo (columna)**: cada tipo de dato que guarda una tabla (nombre, edad…).
- **Registro (fila)**: cada elemento concreto guardado (un estudiante en particular).
- **Clave primaria**: el campo que identifica a cada registro de forma única y no se repite (como el DNI de una persona).
- **Clave foránea (también "extranjera" o "externa")**: un campo que apunta a la clave primaria de otra tabla. Así se relacionan las tablas.
- **Vista**: una "ventana" que enseña solo una parte de los datos, adaptada a quien la va a mirar.
Ejemplo de tabla `Estudiantes`:

| ID_Estudiante | Nombre | Apellido | Edad |
|---|---|---|---|
| 1 | Ana | López | 20 |
| 2 | Luis | Pérez | 22 |

`ID_Estudiante` es la clave primaria, cada fila es un registro y cada columna es un campo.
## Introducción
Hoy casi todo funciona con bases de datos: pagos por internet, tiendas online, la agenda del móvil, programas para gestionar clientes, contabilidad… Todos se apoyan en **estructuras de datos**.

Por eso es crucial el **Administrador de Sistemas de Bases de Datos**: quien mantiene esos sistemas funcionando y se asegura de que la información esté disponible para quien la necesite. Sus responsabilidades:
- **Diseñar, instalar y configurar** SGBD.
- Hacer **copias de seguridad**.
- Administrar **usuarios y permisos** asociados a los datos.
- **Monitorizar y optimizar** el rendimiento del SGBD.
El manual quiere desgranar las tareas del administrador. Reconoce que es imposible detallar todas las situaciones posibles, pero busca dar las **líneas generales de actuación** para una administración eficiente. 2 consejos:
1. **Saber acudir a las fuentes oficiales** (por ejemplo, los manuales oficiales de MySQL en la web). Es crucial saber dónde está la documentación oficial.
2. Hay **2 formas de administrar** un SGBD: con **comandos** o con una **interfaz gráfica**. Se recomienda familiarizarse con los comandos por su **agilidad y efectividad**.
---
## 1. Funciones, componentes, usuarios y tipos de SGBD (págs. 7-20)
Empezamos con las dos piezas clave de toda la asignatura:
> **Base de datos (BD):** conjunto de datos relacionados entre sí, estructurados y organizados según ciertos criterios. Según esa estructura hay varios modelos. Aquí el PDF cita tres: **relacional, jerárquico y en red**. En el apartado 1.4 añade un cuarto tipo, el orientado a objetos.
>
> **Sistema Gestor de Bases de Datos (SGBD):** software que ofrece un entorno para **crear, manipular y administrar** bases de datos. Sus funciones son esenciales para garantizar **integridad, seguridad y eficiencia**.

**Imagina una biblioteca (mío).** La BD son los libros bien ordenados. El SGBD es el sistema (y el bibliotecario) que sabe dónde está todo, quién puede llevarse qué y que nada se pierda ni se estropee.
