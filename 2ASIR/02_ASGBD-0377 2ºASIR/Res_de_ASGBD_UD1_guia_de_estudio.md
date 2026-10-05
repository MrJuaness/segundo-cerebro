# Unidad 1.Instalación y configuración de un sistema gestor de base de datos
## ==Mini-diccionario para empezar==
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
## ==Introducción==
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
## 1. Funciones, componentes, usuarios y tipos de SGBD
Empezamos con las 2 piezas clave de toda la asignatura:
> **Base de datos (BD):** conjunto de datos relacionados entre sí, estructurados y organizados según ciertos criterios. Según esa estructura hay varios modelos. El PDF cita tres: **relacional, jerárquico y en red**. En el apartado 1.4 añade un cuarto tipo, **el orientado a objetos**.
> **Sistema Gestor de Bases de Datos (SGBD):** software que ofrece un entorno para **crear, manipular y administrar** bases de datos. Sus funciones son cruciales para garantizar **integridad, seguridad y eficiencia**.

**Imagina una biblioteca (mío).** La BD son los libros bien ordenados. El SGBD es el sistema (y el bibliotecario) que sabe dónde está todo, quién puede llevarse qué y que nada se pierda ni se estropee.
### ==1.1 Funciones de un SGBD==
Un SGBD debe permitir manejar y administrar **los datos** guardados y **la estructura** de las bases de datos. 10 funciones:
#### Función 1. Creación de la base de datos
Es construir los "cajones" antes de guardar nada. Permite definir la estructura: tipos de datos, relaciones entre tablas, restricciones y otros elementos.
- **Crear la estructura:** diseñar las tablas, decidir qué campos tiene cada una y cómo se relacionan.
- **Tipo de dato de cada campo:** entero, cadena de texto, fecha… (la edad será un número, el nombre un texto).
- **Relaciones entre tablas:** vínculos mediante claves primarias y extranjeras, para mantener la coherencia de los datos.
#### Función 2. Manipulación de datos
Es trabajar con el contenido. Se hace con consultas **SQL** (*Structured Query Language*) u otras interfaces de programación.
- **Insertar** datos nuevos (operación `INSERT`).
- **Actualizar** datos existentes (`UPDATE`).
- **Eliminar** datos no deseados (`DELETE`).
- **Consultar** para recuperar información concreta, con lenguajes como SQL.
#### Función 3. Integridad de datos
Consiste en que los datos sean correctos y no se contradigan, aplicando restricciones.
- **Claves primarias y externas (foráneas):** garantizan la **unicidad** de los registros (no hay dos iguales) y la **coherencia referencial** entre tablas. Por ejemplo, no puedes matricular a un alumno en un curso que no existe.
- Garantía de **consistencia y exactitud** de los datos.
#### Función 4. Seguridad
Controla el acceso con **autenticación** y **autorización**, para que solo los usuarios autorizados accedan a ciertos datos o hagan ciertas operaciones.
- **Autenticación:** comprobar la identidad del usuario (¿quién eres?). Es requisito para entrar.
- **Autorización:** determinar qué privilegios y permisos tiene para acceder y modificar datos (¿qué puedes hacer?).
- *Ejemplo (mío):* en un edificio enseñas el DNI en la puerta (autenticación) y tu tarjeta solo te deja subir a ciertas plantas (autorización).
#### Función 5. Concurrencia y control de transacciones
Gestiona que **varios usuarios** trabajen a la vez sin estropear los datos. También permite **confirmar (commit)** o **revertir (rollback)** cambios.
- **Control de concurrencia:** qué hacer cuando varias transacciones intentan acceder o modificar los mismos datos a la vez, garantizando consistencia en entornos multiusuario.
- **Transacciones:** conjunto de operaciones que se ejecutan como una **unidad atómica** ("o se hace todo o no se hace nada"). Se controlan para asegurar las propiedades **ACID**:

| Letra | Propiedad | Significa |
|---|---|---|
| A | Atomicidad | La transacción se hace entera o no se hace |
| C | Consistencia | La BD pasa de un estado válido a otro válido |
| I | Aislamiento (*Isolation*) | Las transacciones simultáneas no se interfieren |
| D | Durabilidad | Lo confirmado queda guardado de forma permanente |

*Ejemplo (mío):* transferir 100 € de la cuenta A a la B son dos pasos: restar a A y sumar a B. Si el sistema falla entre los dos, se perderían 100 €. Con una transacción, o se hacen los dos pasos (`COMMIT`) o se deshace todo (`ROLLBACK`).
