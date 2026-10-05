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
Casi todo funciona con bases de datos: pagos por internet, tiendas online, la agenda del móvil, programas para gestionar clientes, contabilidad… Todos se apoyan en **estructuras de datos**.
Por eso es crucial el **Administrador de Sistemas de Bases de Datos**: quien mantiene esos sistemas funcionando y se asegura de que la información esté disponible para quien la necesite. Sus responsabilidades:
- **Diseñar, instalar y configurar** SGBD.
- Hacer **copias de seguridad**.
- Administrar **usuarios y permisos** asociados a los datos.
- **Monitorizar y optimizar** el rendimiento del SGBD.
El manual quiere desgranar las tareas del administrador.Es imposible detallar todas las situaciones posibles, pero daremos las **líneas generales de actuación** para una administración eficiente. 2 consejos:
1. **Saber acudir a fuente oficiales** (por ejemplo; manuales oficiales de MySQL en la web).Es crucial saber dónde está la documentación oficial.
2. Hay **2 formas de administrar** un SGBD: con **comandos** o con una **interfaz gráfica**. Se recomienda con comandos por su **agilidad y efectividad**.
---
## 1. Funciones, componentes, usuarios y tipos de SGBD
> **Base de datos (BD):** conjunto de datos relacionados entre sí, estructurados y organizados según ciertos criterios. Según esa estructura hay varios modelos: **relacional, jerárquico y en red**. En el apartado 1.4 tenemos un cuarto tipo, **el orientado a objetos**.
> **Sistema Gestor de Bases de Datos (SGBD):** software que ofrece un entorno para **crear, manipular y administrar** bases de datos. Sus funciones son cruciales para garantizar **integridad, seguridad y eficiencia**.

**Imagina una biblioteca (mío).** La BD son los libros bien ordenados. El SGBD es el sistema (y el bibliotecario) que sabe dónde está todo, quién puede llevarse qué y que nada se pierda ni se estropee.
### ==1.1 Funciones de un SGBD==
Un SGBD debe permitir manejar y administrar **los datos** guardados y **la estructura** de las bases de datos. 10 funciones:
#### ==Función 1. Creación de la base de datos==
Es construir los "cajones" antes de guardar nada. Permite definir la estructura: tipos de datos, relaciones entre tablas, restricciones y otros elementos.
- **Crear la estructura:** diseñar las tablas, decidir qué campos tiene cada una y cómo se relacionan.
- **Tipo de dato de cada campo:** entero, cadena de texto, fecha… (la edad será un número, el nombre un texto).
- **Relaciones entre tablas:** vínculos mediante claves primarias y extranjeras, para mantener la coherencia de los datos.
#### ==Función 2. Manipulación de datos==
Es trabajar con el contenido realizando consultas **SQL** (*Structured Query Language*) u otras interfaces de programación.
- **Insertar** datos nuevos (operación `INSERT`).
- **Actualizar** datos existentes (`UPDATE`).
- **Eliminar** datos no deseados (`DELETE`).
- **Consultar** para recuperar información concreta, con lenguajes como SQL.
#### ==Función 3. Integridad de datos==
Consiste en que los datos sean correctos y no se contradigan, aplicando restricciones.
- **Claves primarias y externas (foráneas):** garantizan la **unicidad** de los registros (no hay 2 iguales) y la **coherencia referencial** entre tablas. Por ejemplo, no puedes matricular a un alumno en un curso que no existe.
- Garantía de **consistencia y exactitud** de los datos.
#### ==Función 4. Seguridad==
Controla el acceso con **autenticación** y **autorización**, para que solo los usuarios autorizados accedan a ciertos datos o hagan ciertas operaciones.
- **Autenticación:** comprobar la identidad del usuario (¿quién eres?). Es requisito para entrar.
- **Autorización:** determinar qué privilegios y permisos tiene para acceder y modificar datos (¿qué puedes hacer?).
- *Ejemplo (mío):* en un edificio enseñas el DNI en la puerta (autenticación) y tu tarjeta solo te deja subir a ciertas plantas (autorización).
#### ==Función 5. Concurrencia y control de transacciones==
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
#### ==Función 6. Respaldo y recuperación==
Ofrece copias de seguridad periódicas y la capacidad de volver a un estado anterior si hay fallos o pérdida de datos.
- **Copia de seguridad (backup):** guarda una copia de la BD en un estado concreto.
- **Recuperación:** restaura la BD a un estado previamente respaldado.
#### ==Función 7. Optimización del rendimiento==
Son técnicas para que las consultas, los índices y otras operaciones recuperen los datos de forma eficiente.
- **Índices:** aceleran la velocidad de búsqueda y la recuperación de datos. Funcionan como el índice alfabético de un libro: no lees todas las páginas para encontrar algo.
- **Optimización de consultas:** ajustar las consultas para recuperar datos con más eficiencia.
- *Ojo:* los índices aceleran las lecturas, pero pueden **ralentizar** las inserciones, actualizaciones y borrados, porque hay que mantenerlos al día.
#### ==Función 8. Diccionario de datos==
Es un registro exhaustivo que detalla la organización y estructura de la BD: tablas, interrelaciones, campos y normas de validación e integridad.
- **Metadatos:** información sobre la BD (estructura de las tablas, restricciones, relaciones). Son "datos sobre los datos". Se amplía en el apartado 10.
#### ==Función 9. Interfaz de usuario y herramientas de desarrollo==
Ofrece interfaces gráficas o de línea de comandos para interactuar con la BD, y herramientas para su diseño, desarrollo y mantenimiento.
- **GUI** (interfaz gráfica de usuario): una interfaz visual.
- **Herramientas de desarrollo:** facilitan crear y modificar esquemas de BD, consultas y otros elementos.
#### ==Función 10. Escalabilidad y tolerancia a fallos==
El SGBD debe poder manejar que la BD crezca y tener estrategias de **redundancia de datos** (tener copias o duplicados) para garantizar su disponibilidad continua.
- **Escalabilidad:** capacidad de manejar más tamaño de BD y más carga de usuarios.
- **Tolerancia a fallos:** recuperarse de fallos sin pérdida significativa de datos ni interrupciones del servicio.
**Las 10 de un vistazo:** crear · manipular · integridad · seguridad · concurrencia/transacciones · respaldo/recuperación · rendimiento · diccionario · interfaz · escalabilidad/tolerancia a fallos.
---
### ==1.2 Componentes de un SGBD==
Las *funciones* son **lo que hace** el SGBD. Los *componentes* son **las piezas de las que está hecho**. Son 8:
1. **Motor de base de datos:** el **núcleo** (el "cerebro"). Interpreta consultas y comandos, los transforma a un formato que pueda entender y procesar, y gestiona los recursos del sistema para ejecutarlos de forma eficiente.
2. **Diccionario de datos:** una BD que contiene **metadatos**: nombre de la BD, nombres de las tablas, nombre y tipo de los campos, restricciones e índices.
3. **Lenguaje de Manipulación de Datos (DML):** operaciones para manipular los datos almacenados: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
4. **Lenguaje de Definición de Datos (DDL):** operaciones para definir la estructura de la BD: `CREATE`, `ALTER`, `DROP`.
5. **Gestor de transacciones:** hace que las transacciones se ejecuten de forma segura y eficiente, **aisladas entre sí**, y que sus cambios se **confirmen de forma permanente**.
6. **Gestor de recuperación:** recupera la BD ante fallos o errores. La devuelve a un **estado consistente** tras un fallo del sistema o recupera datos perdidos o dañados.
7. **Gestor de concurrencia:** gestiona el **acceso simultáneo** para garantizar la consistencia, previniendo conflictos de acceso y asegurando que las transacciones se ejecuten aisladas. (El PDF lo escribe "Concurrency" por error.)
8. **Interfaz de usuario:** el medio de interacción entre el usuario y el SGBD, para hacer consultas y recibir resultados. Puede ser **GUI** (gráfica, con ventanas y botones) o **CLI** (línea de comandos, escribiendo órdenes).
---
### ==1.3 Usuarios==
Son los distintos perfiles de personas que usan una BD:
1. **DBA (Administrador de la BD):** tiene el **nivel más alto de acceso** y es responsable del mantenimiento y la seguridad. Puede crear y eliminar BD, tablas y otros objetos, y **otorgar y revocar permisos**. También optimiza el rendimiento, planifica la capacidad e implementa políticas de seguridad.
2. **Usuarios RESOURCE:** pueden **crear sus propios objetos** (tablas, vistas…), pero **no dar permisos** a otros, y solo acceden a lo que tienen permitido. Suelen ser **desarrolladores de aplicaciones**.
3. **Usuarios CONNECT:** solo pueden **acceder** a objetos si se les ha concedido permiso. No crean objetos ni dan permisos. Suelen ser **usuarios finales** que consultan datos para su trabajo.
4. **Usuarios especializados:** son capaces de **escribir aplicaciones** para interactuar con la BD, que usan ellos u otros. Pueden conocer a fondo su estructura y diseño.
5. **Usuarios casuales:** interactúan mediante un **procesador de consultas**, con consultas creadas por ellos o por otras personas. Pueden no conocer a fondo la estructura de la BD.
6. **Usuarios esporádicos:** hacen **consultas especializadas y más complejas**, que requieren más conocimiento de la estructura. El PDF dice que pueden ser analistas o científicos de datos con análisis complejos.
**Truco (mío):** los tres primeros son una escalera de poder. DBA (puede todo) → RESOURCE (crea lo suyo) → CONNECT (solo usa lo que le dan).
---
### ==1.4 Tipos de SGBD==
Se clasifican según **cómo organizan los datos**. Hay 4 tipos. En el (Resumen) se añaden otras formas de clasificarlos, que explico allí.
#### Tipo 1. SGBD Relacionales
Son **los más utilizados** y se basan en el modelo relacional. Los datos se guardan en **tablas**, y la relación entre ellos se establece con **claves primarias y foráneas**. Se manejan con consultas y manipulaciones de alto nivel usando **SQL**. Ejemplos: MySQL, Oracle y SQL Server.
Características:
- **Integridad:** datos precisos y consistentes mediante reglas de integridad.
- **Seguridad:** control de acceso y **encriptación** (cifrado).
- **Eficiencia:** usan **indexación** (índices) y **particionamiento** (dividir tablas enormes en trozos más manejables) para acelerar las consultas.
Ejemplo del PDF (con datos inventados por mí): una tabla `Estudiantes` (ID_Estudiante, Nombre, Apellido, Edad), una tabla `Cursos` (ID_Curso, Nombre_Curso, Profesor) y una tabla `Registro` (ID_Estudiante, ID_Curso) que las relaciona.
```
Estudiantes: (1, Ana, López, 20) · (2, Luis, Pérez, 22)
Cursos:      (10, Bases de Datos, Marta) · (11, Redes, Pedro)
Registro:    (1, 10) · (1, 11) · (2, 10)
```
Ana (1) está en Bases de Datos (10) y en Redes (11). Luis (2) solo en Bases de Datos. En `Registro`, los dos campos son claves foráneas que apuntan a las otras tablas.
> **Sabías que:** Edgar Frank "Ted" Codd, informático inglés (1923-2003), fue el creador del actual modelo relacional.
#### Tipo 2. SGBD de Red
Los datos se organizan en una **red** donde cada registro se conecta con otros mediante **enlaces**. Permiten representar relaciones muy flexibles, pero son más complejos de diseñar y gestionar.
- **Flexibilidad:** permiten relaciones complejas entre datos.
- **Eficiencia:** buenos para consultas que reflejan la estructura de red.
- **Complejidad:** más difíciles de diseñar y gestionar.
- *Ejemplo:* **IDS (Integrated Data Store)** de IBM. Un registro `Empleado` está enlazado con `Departamento` y `Proyecto`. Un empleado puede relacionarse con **varios** departamentos o proyectos, y un departamento o proyecto con **varios** empleados.
#### Tipo 3. SGBD Jerárquicos
Los datos se organizan como un **árbol**: cada **nodo** es un registro y cada **arista** es una relación entre registros. Son eficientes para operaciones que reflejan la jerarquía, pero poco flexibles para relaciones que no son jerárquicas.
- **Eficiencia:** buenos para consultas que siguen la jerarquía.
- **Simplicidad:** más simples de entender y gestionar.
- **Limitaciones:** menos flexibles con relaciones no jerárquicas.
- *Ejemplo:* **IMS (Information Management System)** de IBM. Un departamento puede tener varios empleados, pero **cada empleado pertenece a un solo departamento**. Compáralo con el tipo de red, donde un empleado podía estar en varios.
#### Tipo 4. SGBD Orientados a Objetos
Se basan en el **modelo de objetos**. Los datos se representan como **objetos** (instancias de clases) y se aplican conceptos de la programación orientada a objetos, como la **herencia** y el **polimorfismo**. Son útiles cuando hay que representar datos muy complejos y hacer operaciones de alto nivel.

==**palabras para entender esto (explicación mía)**==: una **clase** es un molde (p. ej. "Estudiante"), un **objeto** es una pieza concreta hecha con ese molde (p. ej. "Ana"), la **herencia** permite que una clase reutilice lo de otra, y el **polimorfismo** permite que un mismo método se comporte distinto según el objeto.
- **Flexibilidad:** datos complejos y relaciones entre ellos.
- **Reutilización y extensibilidad:** gracias a la herencia y el polimorfismo.
- **Complejidad:** más difíciles de entender y gestionar.
- *Ejemplo:* **MongoDB**. Una colección `Estudiantes` donde cada documento es un objeto que representa a un estudiante, con propiedades (`nombre`, `apellido`, `edad`) y también métodos (comportamientos, como matricularse en un curso).
#### Comparativa rápida

| Tipo | Cómo organiza | Punto fuerte | Punto débil | Ejemplo (PDF) |
|---|---|---|---|---|
| Relacional | Tablas + claves | Muy usado; integridad, seguridad, eficiencia | (el PDF no cita ninguno) | MySQL, Oracle, SQL Server |
| Red | Registros unidos por enlaces | Flexibilidad | Complejo | IDS (IBM) |
| Jerárquico | Árbol | Simple y eficiente con jerarquías | Poco flexible | IMS (IBM) |
| Orientado a objetos | Objetos con herencia y polimorfismo | Flexible y reutilizable | Complejo | MongoDB |

### ==Más info: las Reglas de Codd==
> las "12 reglas de Codd" son en realidad **13** (numeradas de la 0 a la 12) y que establecen las características que debe tener una BD para poder catalogarse como relacional.
**El PDF solo da los nombres.** La idea sencilla de cada una es explicación mía:

| Nº | Nombre | Idea sencilla |
|---|---|---|
| 0 | Regla fundamental | Para ser relacional, el sistema debe gestionar los datos usando solo sus capacidades relacionales |
| 1 | Regla de la información | Toda la información se representa de una única forma: valores dentro de tablas |
| 2 | Acceso garantizado | Cualquier dato se puede localizar con tabla + clave primaria + columna |
| 3 | Tratamiento sistemático de los valores nulos | "No hay dato" (NULL) se trata de forma uniforme y no es lo mismo que 0 o texto vacío |
| 4 | Catálogo dinámico en línea basado en el modelo relacional | La descripción de la BD (el diccionario de datos) se guarda también en tablas y se consulta igual que los datos |
| 5 | Sublenguaje de datos completo | Debe existir un lenguaje (en la práctica, SQL) que permita definir estructuras, manipular datos, controlar la seguridad y la integridad, y gestionar transacciones |
| 6 | Actualización de vistas | Las vistas que teóricamente puedan actualizarse deben poder actualizarse |
| 7 | Inserción, actualización y borrado de alto nivel | Se pueden insertar, modificar y borrar conjuntos de filas de una vez |
| 8 | Independencia física de los datos | Si cambia cómo se guardan físicamente, los programas no tienen que cambiar |
| 9 | Independencia lógica de los datos | Si cambia la estructura lógica de las tablas (cuando sea posible), los programas no se ven afectados |
| 10 | Independencia de la integridad | Las reglas de integridad se definen en el lenguaje de la BD y se guardan en el catálogo, no en los programas |
| 11 | Independencia de la distribución | Los programas no notan si los datos están en un sitio o repartidos |
| 12 | La regla de la no subversión | Un acceso de bajo nivel no puede usarse para saltarse las reglas de integridad |

Las reglas 8 y 9 se parecen a la arquitectura de 3 niveles del apartado 2, la 4 al diccionario de datos y la 5 a SQL.

---
## 2. Arquitectura del SGBD y arquitectura ANSI/SPARC 
La **arquitectura** de un SGBD es la estructura crucial que define **cómo se organizan y gestionan los datos** en el sistema.

**ANSI/SPARC** es un modelo conceptual para diseñar y administrar BD. Su nombre viene de sus creadores: **ANSI** (*American National Standards Institute*) y **SPARC** (*Standards Planning And Requirements Committee*). Divide la BD en **3 niveles**:
```
 NIVEL EXTERNO      lo que ve cada usuario (vistas)
       ▲
 NIVEL CONCEPTUAL   tablas, columnas, relaciones
       ▲
 NIVEL INTERNO      cómo se guarda físicamente
```

1. **Nivel interno (o físico):** es el más bajo. Se ocupa de **cómo se almacenan físicamente** los datos: organización de los archivos, almacenamiento de índices, de metadatos, etc. Por ejemplo, los datos pueden guardarse en discos duros con estructuras como **B-trees** o **hash maps** (formas de organizar datos para encontrarlos rápido; no hace falta profundizar ahora). También gestiona la **compresión** (ahorrar espacio) y la **encriptación** (proteger los datos).
2. **Nivel conceptual (o lógico):** se ocupa de **cómo se organizan lógicamente** los datos. Define **qué datos** se guardan y **qué relaciones** hay entre ellos. **Oculta los detalles físicos** y da una visión unificada. En una BD relacional define las tablas, las columnas y las relaciones. Los usuarios interactúan a través de este nivel con un lenguaje como SQL.
3. **Nivel externo (o de vista):** es el nivel superior y se encarga de **presentar los datos a los usuarios finales**. Puede haber **varias vistas externas** adaptadas a distintos usuarios. Por ejemplo, el departamento financiero ve una vista solo con datos financieros, y recursos humanos ve otra solo con información de los empleados.
**Analogía de la biblioteca (mía):** el nivel interno es en qué estantería y planta está cada libro. El conceptual es el catálogo (qué libros existen y cómo se relacionan). El externo es lo que ve cada tipo de lector.
---
## 3. SGBD libres y comerciales o de mercado.
==**SGBD libres:**== su licencia de código es libre; usarlos **no cuesta dinero**. El esquema:
- **MySQL:** el gestor de código abierto más popular en la web, usado sobre todo con el lenguaje PHP.
- **PostgreSQL:** potente gestor de BD relacionales orientado a objetos que amplía las funciones de SQL.
- **MariaDB:** sistema derivado de MySQL con licencia **GPL** (*General Public License*).
- **SQLite:** una biblioteca escrita en C que implementa un SGBD.
- **MongoDB:** aparece en el esquema solo con su logo.
==**SGBD de mercado:**== están programados con código protegido bajo **licencia propietaria**, usarlos **implica un coste económico**. Los 2 más populares:
- **Microsoft SQL Server:** gestor desarrollado por Microsoft, basado en el lenguaje SQL.
- **Oracle Database:** sistema de gestión de BD **objeto-relacional** (mezcla tablas con ideas de objetos), producido y comercializado por Oracle Corporation.
==*Matiz:*== MySQL lo desarrolla Oracle y tiene licencia pública general **y también comercial**.
---
## 4. El administrador de bases de datos (DBA).
El DBA (*DataBase Administrator*) es **el guardián de la base de datos**: se encarga de que todo funcione bien y de que la información esté segura y accesible para las personas adecuadas. Sus 5 funciones:
1. **Entender las necesidades de los usuarios:** saber qué información necesita la empresa para organizar la BD de forma eficiente.
2. **Gestionar la base de datos:** todas las tareas técnicas, como crear tablas, gestionar índices y modificar la estructura de la BD.
3. **Mantenerla funcionando sin problemas:** monitorizar el rendimiento y hacer ajustes para mejorar la eficiencia.
4. **Protegerla:** implementar medidas de seguridad para la información almacenada.
5. **Facilitar el acceso a los datos:** definir políticas de acceso y garantizar que los datos se presenten de forma eficiente y en el formato adecuado.
> **Ojo:** el DBA es el usuario más importante de la BD. Se encarga de que todo funcione, de que la información esté segura y accesible para las personas adecuadas. **Gestiona, mantiene, protege y facilita el acceso.**
---
## 5. Lenguaje estándar de consulta SQL.
**SQL** *Structured Query Language* (Lenguaje de Consulta Estructurada). Es un lenguaje ("de programación") para **gestionar y manipular bases de datos**, **estandarizado** y lo usa la mayoría de SGBD. Es "el idioma" con el que le hablas al SGBD.
Se divide en 3 grupos, según para qué sirven:

| Grupo | Para qué sirve | Comandos |
|---|---|---|
| **DDL** (Definición de Datos) | Definir y modificar la **estructura** | `CREATE` (crear), `ALTER` (modificar), `DROP` (eliminar) |
| **DML** (Manipulación de Datos) | Insertar, modificar, eliminar y recuperar **datos** | `SELECT`, `INSERT`, `UPDATE`, `DELETE` |
| **DCL** (Control de Datos) | Controlar el **acceso** a los datos | `GRANT` (dar permisos), `REVOKE` (quitarlos) |

**Truco (mío):** DDL = **D**efinir, DML = **M**anipular, DCL = **C**ontrolar.
Ejemplos:
- `CREATE` crea una tabla nueva, `ALTER` modifica la estructura de una tabla existente y `DROP` elimina una tabla.
- `SELECT` extrae datos, `INSERT` introduce datos nuevos, `UPDATE` cambia datos ya guardados y `DELETE` borra datos.
- `GRANT` da a un usuario permiso para acceder a una tabla y `REVOKE` se lo quita.

**Para qué se usa SQL (5 tareas del PDF):**
1. **Crear BD y tablas:** `CREATE DATABASE` y `CREATE TABLE`.
2. **Insertar datos:** `INSERT INTO`.
3. **Modificar datos:** `UPDATE`.
4. **Consultar datos:** `SELECT`.
5. **Controlar el acceso:** `GRANT`.

Aquí tienes un mini ejemplo mío para que los veas escritos:
```sql
-- DDL: estructura
CREATE DATABASE academia;
USE academia;
CREATE TABLE estudiantes (
    id_estudiante INT PRIMARY KEY,
    nombre        VARCHAR(50),
    edad          INT
);
ALTER TABLE estudiantes ADD COLUMN email VARCHAR(100);
-- DROP TABLE estudiantes;   ← borraría la tabla entera

-- DML: datos
INSERT INTO estudiantes (id_estudiante, nombre, edad) VALUES (1, 'Ana', 20);
SELECT * FROM estudiantes;
UPDATE estudiantes SET edad = 21 WHERE id_estudiante = 1;
DELETE FROM estudiantes WHERE id_estudiante = 1;

-- DCL: permisos
-- (el PDF no lo explica, pero el usuario tiene que existir antes de darle permisos)
CREATE USER 'ana'@'localhost' IDENTIFIED BY 'clave123';
GRANT SELECT ON academia.estudiantes TO 'ana'@'localhost';
REVOKE SELECT ON academia.estudiantes FROM 'ana'@'localhost';
```
---
## 6. Instalación y configuración de un SGBD: MySQL.
**MySQL:** uno de los gestores más usados, por usuarios individuales y empresas que usan software libre. Lo desarrolla **Oracle**, funciona con una **licencia pública general y también comercial**, y sirve para manejar datos **relacionales**.
Del paquete, los 2 componentes principales son:
- **MySQL Server:** el **núcleo**, un gestor relacional robusto y muy reconocido. Sirve para crear BD con tablas, vistas y relaciones, y para editarlas y consultarlas.
- **MySQL Workbench:** un conjunto avanzado de herramientas para administrar BD relacionales. Permite ejecutar consultas SQL en un **entorno visual interactivo**, con interfaces gráficas intuitivas.
*Imagina (mío):* el Server es el almacén donde viven los datos y Workbench es el mostrador desde el que le haces peticiones.
### 6.1 Instalar MySQL en Windows 10
Se empieza 1ººººººº1r MySQL Server. Primero, dónde y cómo descargarlo.
#### 6.1.1 Descargar MySQL 
1. Entra en la **web oficial de MySQL** (el PDF trae el enlace "Ver enlace") y en la página principal pulsa **"MySQL Community Server"**.
2. En la zona inferior de la nueva página, **selecciona la plataforma**, que será Windows. Pulsa la opción principal **"MySQL Installer for Windows"**. Este procedimiento es el mismo en cualquier sistema operativo.
3. En la página siguiente vuelve a elegir el sistema operativo y haz clic en **"Windows (x86, 32-bit), MSI Installer"**. Hay dos versiones: una **descarga ficheros de Internet durante la instalación** y la otra es el **paquete completo**.
4. La versión que se usa en el curso es la **8.0.28**.
5. Antes de descargar aparece una página para suscribirse o iniciar sesión. **No es necesario**: pulsa el enlace de la zona inferior.
#### 6.1.2 Proceso de instalación 
Consejo previo: ten el **sistema operativo actualizado** para evitar errores de última hora.
Ejecuta el paquete descargado y arranca el **asistente de instalación**. Para instalar Server y Workbench hay 2 opciones:
- **"Developer Default":** instala automáticamente todo lo necesario para crear y gestionar BD. Es la **recomendada para principiantes**, porque instala MySQL completo con información extra y todo el soporte disponible.
- **"Custom":** ofrece muchas opciones para elegir. Está pensada para usuarios que ya tienen experiencia con otros gestores de BD.
Opciones principales en Custom:
- **MySQL Servers:** el recurso fundamental para usar tu equipo como servidor y administrador de BD. Despliega la lista y pulsa la **flecha** para moverlo a la columna de la derecha (lo que se va a instalar).
- **MySQL Workbench:** está en el apartado **"Applications"** y será nuestro **cliente**. Se mueve igual.
- **MySQL Connections:** depende de las conexiones que quieras hacer, según los clientes y lenguajes de programación que uses. Lo mejor es instalarlos todos por si los necesitas.
> **Importante :** para instalar la conexión a **Python**, tienes que tener instalado en el sistema el paquete de ese lenguaje de programación.
#### 6.1.3 Documentación
Es el último apartado de Custom. Permite añadir información sobre cómo usar MySQL y ejemplos de ayuda. Después:
- Con los paquetes elegidos (en Developer Default o en Custom) pulsa **"Next"** y, en la pantalla siguiente, **"Execute"**. Casi todas las aplicaciones necesitan el paquete **Microsoft Visual C++ 2015**, que se instala automáticamente cuando empieza el proceso.
- El PDF dice que la preparación de los paquetes no empieza hasta que aparece el mensaje **"INSTL DONE"**. En la captura se ve que Visual Studio no está instalado, porque es imprescindible tener antes el paquete de Microsoft en el sistema. Se pulsa **"Next"**.
- En el siguiente paso ya se hace la **instalación real**. Aparece un mensaje emergente: pulsa **"Yes"**. Después sale la lista de programas que se van a instalar: pulsa de nuevo **"Execute"**.
#### 6.1.4 Configuración de MySQL.
Al terminar de instalar los módulos hay que hacer una **configuración inicial antes de arrancar los servicios**. Pulsa "Siguiente". La pantalla siguiente es una **fase crítica**: se configuran el **tipo de equipo**, los **protocolos** y los **puertos TCP** para las conexiones remotas. Esto es vital para el correcto funcionamiento y la seguridad.
Tipos de equipo:

| Opción | Para qué es |
|---|---|
| **Development Computer** | Equipo que alberga el servidor SQL y además el cliente para hacer consultas. Si tu equipo es doméstico y trabajas normal en él, **esta es la opción** |
| **Server Computer** | Ordenadores que hacen de servidor, por ejemplo un servidor web con bases de datos |
| **Dedicated Computer** | Un equipo solo y exclusivamente para bases de datos, por ejemplo una máquina virtual donde se guardan tus BD |

Después, el resto de pasos:
- **Puerto TCP:** el de las conexiones remotas. Por defecto es el **3306**. Es el puerto que tendrás que **abrir en el router** para conexiones remotas. (Un puerto es como una puerta numerada por la que el servidor atiende; explicación mía.)
- **Resto de opciones:** déjalas **por defecto**.
- **Contraseña:** eliges la contraseña para conectarte al servidor. Puedes cambiarla en cualquier momento desde el propio servidor. No hace falta definir un usuario concreto para administrar, porque por defecto es el usuario **root**.
- **Nombre del servicio** de MySQL y preferencias generales sobre el **inicio del demonio** (el programa del servidor que queda funcionando en segundo plano, por ejemplo si arranca solo con el sistema) y el **uso de cuentas de usuario**.
- **Pantalla final:** pulsa **"Execute"** para ejecutar las acciones y activar los servicios. Si algo falla, aparece una **"x" roja** junto al elemento afectado y hay que **consultar el registro de errores** (el log).
- Si instalaste extras como los ejemplos, **también hay que configurarlos**. Después hay que conectar con el servidor usando **root y la contraseña** definida. Con esto termina la instalación.
#### 6.1.5 Conectarnos a MySQL Server desde MySQL Workbench.
Si instalaste Workbench, se abre solo tras la instalación. Por defecto aparece la conexión a tu propio equipo, donde está el server. El PDF supone que no hay ninguna conexión creada, para ver cómo se crea una:
1. Pulsa el botón **"+"** de **"MySQL Connections"**.
2. En la ventana que se abre, rellena:
    - **Nombre de la conexión:** el que quieras.
    - **Protocolo:** el estándar, **TCP/IP**.
    - **Hostname:** la IP del servidor. Si es tu propio equipo, la IP del PDF aparece como "0.0.1", que es una errata: la correcta es **127.0.0.1** (la dirección de "este mismo equipo"). Si estás en una red local, será la IP que tenga asignada el servidor en su tarjeta de red. Si es una conexión remota, necesitas la dirección externa de la conexión.
    - **Puerto:** el que configuraste antes (3306 por defecto).
    - **Usuario:** `root` o el que configuraste.
3. Pulsa **"OK"** o **"Test connection"** para comprobar que funciona. Te pedirá la clave.
4. La nueva conexión aparece en la ventana principal de Workbench y te conectas con **un solo clic**. Ya estás dentro del entorno de gestión de MySQL.
==**Resumen rápido de la instalación:**== descargar (8.0.28) → ejecutar → elegir Developer Default o Custom → Next/Execute (requisitos) → Yes/Execute (instalación) → configurar (tipo de equipo, puerto 3306, contraseña de root, servicio) → Execute → conectar con Workbench.
---

## 7. Integración del SGBD en el sistema operativo
La idea central es que el SGBD es una **capa de software entre los usuarios y el sistema de archivos**:
```
Usuario → SGBD → Sistema de archivos (SO) → Disco duro
```
1. **Sistema de archivos:** parte del sistema operativo que gestiona la **lectura y escritura** de datos en el almacenamiento físico (ej;un disco duro). El SGBD lo usa para guardar las BD físicas. Cada BD puede ser **un archivo o un conjunto de archivos**, y las lecturas y escrituras en la BD se traducen en lecturas y escrituras en esos archivos.
2. **Control de usuarios:** parte crucial de la seguridad. Cada usuario tiene unos **privilegios** que determinan qué operaciones puede hacer (leer o escribir en una BD), y se **verifican cada vez** que intenta una operación. En el ejemplo de código, esto ocurre en los métodos `crear_base_de_datos` y `leer_base_de_datos` del SGBD.
3. **SGBD:** ofrece una interfaz para que los usuarios interactúen con las BD **sin preocuparse de cómo se guardan** los datos en el sistema de archivos. En el ejemplo, la interfaz son esos dos métodos.
> **Importante (PDF):** el ejemplo está **muy simplificado**. Un SGBD real tiene muchas más funciones, y su gestión de usuarios y su interacción con el sistema de archivos son mucho más complejas y seguras. Debe lidiar con la **concurrencia** (varios usuarios accediendo a la BD a la vez), la **recuperación de errores** y la **optimización de consultas**.
### El código del PDF, explicado
Está en Python (con la sangría reconstruida y comentarios míos). No necesitas dominar Python: lo importante es la idea.
```python
class SistemaOperativo:                       # simula el SO
    def __init__(self):
        self.usuarios = {}                    # "agenda" de usuarios (nombre → objeto Usuario)
        self.sistema_de_archivos = SistemaDeArchivos()   # el SO tiene su sistema de archivos

    def agregar_usuario(self, nombre, contraseña):
        self.usuarios[nombre] = Usuario(nombre, contraseña)   # registra un usuario

    def autenticar_usuario(self, nombre, contraseña):
        if nombre in self.usuarios and self.usuarios[nombre].contraseña == contraseña:
            return True                       # existe y la contraseña coincide
        return False

class SistemaDeArchivos:                      # simula el disco/archivos
    def __init__(self):
        self.archivos = {}                    # "carpeta" donde guardar archivos por nombre

    def crear_archivo(self, nombre, contenido):
        self.archivos[nombre] = contenido

    def leer_archivo(self, nombre):
        if nombre in self.archivos:
            return self.archivos[nombre]
        return None                           # si no existe, devuelve "nada"

class Usuario:                                # una persona con nombre y contraseña
    def __init__(self, nombre, contraseña):
        self.nombre = nombre
        self.contraseña = contraseña

class SGBD:                                   # nuestro gestor, "montado" sobre el SO
    def __init__(self, sistema_operativo):
        self.sistema_operativo = sistema_operativo

    def crear_base_de_datos(self, nombre, usuario, contraseña):
        if self.sistema_operativo.autenticar_usuario(usuario, contraseña):   # 1º: ¿es quien dice ser?
            self.sistema_operativo.sistema_de_archivos.crear_archivo(nombre, {})  # 2º: crea el archivo (BD vacía)
            return True
        return False

    def leer_base_de_datos(self, nombre, usuario, contraseña):
        if self.sistema_operativo.autenticar_usuario(usuario, contraseña):
            return self.sistema_operativo.sistema_de_archivos.leer_archivo(nombre)
        return None
```

Cada clase representa una pieza:
- **`SistemaOperativo`** guarda los usuarios y tiene un sistema de archivos. Comprueba la identidad con `autenticar_usuario` (autenticación).
- **`SistemaDeArchivos`** guarda "archivos" por nombre. Una BD será simplemente uno de esos archivos.
- **`Usuario`** es solo nombre y contraseña.
- **`SGBD`** es la capa intermedia. Antes de crear o leer una BD **pregunta al SO si el usuario es válido** y, solo entonces, usa el sistema de archivos.

Un ejemplo de uso mío:
```python
so = SistemaOperativo()
so.agregar_usuario("ana", "1234")
sgbd = SGBD(so)
sgbd.crear_base_de_datos("tienda", "ana", "1234")    # True  → archivo "tienda" creado
sgbd.crear_base_de_datos("otra", "ana", "mal")       # False → contraseña incorrecta
sgbd.leer_base_de_datos("tienda", "ana", "1234")     # {}    → la BD, todavía vacía
```
Por eso el PDF avisa de que es un ejemplo simplificado. Por ejemplo, aquí las contraseñas se guardan tal cual, y un sistema real las protegería.

---
## 8. Instalación de un SGBD de dos capas (págs. 40-41)
"Dos capas" significa **dos partes: cliente y servidor**. Los pasos son:
1. **Servidor de la BD:** el sistema que **alberga el SGBD y las BD**. Ahí instalas el software del SGBD. Durante la instalación puede que tengas que configurar parámetros como el **tamaño máximo** de la BD, la **ubicación de los archivos** de la BD en el sistema de archivos y las **opciones de seguridad**.
2. **Cliente de la BD:** el sistema o sistemas que **se conectan al servidor** para hacer consultas y otras operaciones. Ahí instalas el software cliente, que da las herramientas para conectarse y operar.
3. **Conexión cliente-servidor:** configurar la **red** para que ambos se comuniquen y las **opciones de seguridad** para proteger esa comunicación.
4. **Configuración del SGBD:** con cliente y servidor instalados y conectados, puede hacer falta configurar más: **crear BD**, **configurar usuarios y permisos** y **optimizar el rendimiento**.
Los detalles concretos **varían según el SGBD**. Con MySQL, el Server es la capa servidor y Workbench la capa cliente. El host/IP y el puerto 3306 son la conexión, y `root` con su contraseña es el usuario con el que entras (esta relación con MySQL es mía).
---
## 9. Relación entre el SGBD y la BD: instancias (pág. 42)
Están muy relacionados, pero cumplen **roles distintos**:

| Concepto | Qué es |
|---|---|
| **SGBD** | El **software** que interactúa con usuarios finales, aplicaciones y la BD para capturar y analizar datos. Permite **crear, leer, actualizar y eliminar** datos. Ej.: MySQL, PostgreSQL, MongoDB |
| **BD** | Un **conjunto organizado de datos**, esencialmente "un contenedor de datos", que el SGBD puede crear, recuperar, actualizar y eliminar |
| **Instancia de BD** | Una **representación completa de la BD en un momento específico**. Se crea cuando **se inicia el SGBD** y se mantiene mientras **está en funcionamiento**. Incluye la BD en sí (los datos) **y los procesos del SGBD** que manipulan esos datos |

**Ejemplo del PDF:** en una tienda online, una instancia podría incluir todos los productos, clientes y pedidos hasta el **1 de enero de 2024**. Si el 2 de enero añades un producto o un cliente hace un pedido, eso **no está** en la instancia del 1 de enero, pero **sí** en una nueva instancia creada el 2 de enero.

Piensa en la instancia como una **"foto" completa** de la BD (más los procesos que la manejan) en un momento concreto. El PDF mezcla esas dos ideas (la foto de los datos y el SGBD en marcha), así que quédate con ambas.

---
## 10. Estructura del diccionario de datos (pág. 43)
El **diccionario de datos** (también llamado **catálogo del sistema**) es una estructura esencial de todo SGBD. Guarda **metadatos**, es decir, **datos sobre los datos**, que definen la estructura de la BD. Es como el **catálogo de la biblioteca** (comparación mía): no contiene los libros, sino la información sobre ellos.
El PDF da un esbozo de su estructura, con 10 elementos:
1. **Nombre de la tabla:** cada tabla de la BD.
2. **Nombre del campo:** cada campo (columna) de cada tabla.
3. **Tipo de datos:** de cada campo (entero, cadena, fecha…).
4. **Restricciones:** condiciones sobre los valores de un campo (si es clave primaria, si puede ser nulo, etc.).
5. **Relaciones:** entre tablas, como las claves foráneas.
6. **Índices:** definidos en las tablas para acelerar las consultas.
7. **Vistas:** las vistas definidas en la BD.
8. **Procedimientos almacenados y funciones:** definidos en la BD (pequeños programas guardados dentro de ella).
9. **Información de seguridad:** roles de usuario y permisos.
10. **Información de uso:** estadísticas de acceso.
La estructura exacta **varía según el SGBD**.
---
## 11. Ficheros LOG en un SGBD (págs. 44-45)
Los **ficheros de registro (logs)** son una parte esencial de la infraestructura: garantizan la **integridad** y la **recuperación** de los datos. Son el "diario" donde el SGBD apunta lo que hace (comparación mía). Sirven para:
- **Registro de transacciones:** cada vez que se hace una operación (inserción, actualización o eliminación), el SGBD **escribe un registro** en el log: el tipo de operación, los datos implicados y el momento.
- **Recuperación de fallos:** si el sistema falla (un corte de luz o un error de software), el SGBD usa el log para devolver la BD a un **estado consistente**:
    - **Deshace** las operaciones que no se habían completado del todo cuando ocurrió el fallo.
    - **Rehace** las operaciones que sí se habían completado pero aún no se habían escrito en la BD.
- **Control de concurrencia:** si dos transacciones intentan modificar el mismo dato a la vez, el SGBD puede usar el log para determinar **cuál se ejecutó primero** y resolver el conflicto.
- **Auditoría y seguimiento:** el log es un **registro histórico** de todas las operaciones hechas en la BD.
> **Importante (PDF):** gestionar los logs es una tarea **compleja** que requiere cuidado para que los datos no se pierdan ni se corrompan. Además pueden **ocupar mucho espacio**, así que suele hacer falta implantar políticas de **rotación y purga**. Es decir (explicación mía), cambiar a ficheros nuevos y archivar los viejos (rotación) y borrar los que ya no hacen falta (purga).
---
## 12. Arquitectura del SGBD: archivos en disco, memoria y procesos (págs. 46-47)
Aquí se ve cómo funciona el SGBD **por dentro**. Imagina una oficina (comparación mía): los archivadores son los archivos en disco, la mesa de trabajo es la memoria y los empleados son los procesos.
### 12.1 Archivos en disco
Los datos de la BD se guardan en archivos. Una BD puede estar formada por **uno o más archivos**, según la configuración. Pueden ser:
- **Archivos de datos:** guardan los **datos reales**. Cada tabla puede tener su propio archivo, o varias tablas pueden compartir uno.
- **Archivos de índice:** guardan los **índices**. Cada índice es un mapa que va de los valores de una o más columnas a las ubicaciones de los registros que tienen esos valores.
- **Archivos de log:** guardan los registros de las transacciones que modifican la BD. Sirven para recuperarla a un estado consistente tras un fallo.
### 12.2 Espacios de memoria
El SGBD usa la memoria del sistema para:
- **Buffer de datos:** región de memoria que guarda **temporalmente** los datos que se están leyendo o escribiendo. Así se minimizan las costosas lecturas y escrituras en disco.
- **Caché de índices:** guarda temporalmente los índices para **acelerar las consultas**.
- **Pool de conexiones:** conjunto de conexiones a la BD **que se mantienen abiertas** para que las reutilicen las transacciones.
### 12.3 Procesos
Un SGBD tiene varios procesos que trabajan juntos:
- **Procesos de usuario:** ejecutan las consultas de los usuarios. **Cada conexión** a la BD se maneja en un proceso de usuario separado.
- **Procesos de fondo:** hacen tareas de **mantenimiento**, como limpiar la memoria, escribir de vuelta en el disco los datos modificados, gestionar los ficheros de log, etc.
---
## 13. Resumen (págs. 48-49)
El PDF resume la unidad en 5 puntos:
1. **Funciones del SGBD:** es software para gestionar una BD. Da acceso a los datos, asegura transacciones atómicas, gestiona la seguridad de los usuarios y revisa la integridad, entre otras funciones.
2. **Componentes:** el Resumen cita el DDL, el DCL, el DML, el diccionario de datos y los objetos de la BD (tablas, vistas…). La lista completa de 8 componentes es la de 1.2.
3. **Tipos de SGBD:** se clasifican por varios criterios. El modelo lógico (jerárquicos, de red, relacional y orientados a objetos) ya lo vimos. Las otras tres formas solo aparecen aquí, y el PDF no las desarrolla (la explicación es mía):

   | Criterio | Opciones | Significado |
   |---|---|---|
   | Número de usuarios | **Monousuario / Multiusuario** | Un solo usuario a la vez / varios a la vez |
   | Número de sitios donde se alojan | **Centralizados / Distribuidos** | Todo en un solo sitio / repartido en varios |
   | Ámbito de aplicación | **Propósito general / Propósito específico** | Sirve para cualquier uso / diseñado para una tarea concreta |

4. **Arquitectura:** tres niveles: **interno** (estructura física), **conceptual** (estructura lógica de la BD para una organización) y **externo** (vistas personalizadas para cada usuario).
5. **Instalación y configuración:** antes hay que **elegir qué SGBD instalar** según los requerimientos. Una vez instalado y configurado, los usuarios pueden introducir y consultar datos. Cada SGBD tiene requisitos y procesos propios, así que conviene **consultar siempre su documentación técnica**.
---
## 14. Glosario.
- **Autenticación y autorización:** verificar la identidad de un usuario (autenticación) y definir a qué recursos accede según los permisos que tiene (autorización).
- **Base de datos (BD):** conjunto organizado de datos interrelacionados, estructurados según ciertos criterios, que permite acceder a ellos, gestionarlos y actualizarlos fácilmente.
- **Concurrencia:** gestión del acceso simultáneo de varios usuarios, asegurando que las transacciones se ejecuten de forma consistente y sin interferirse.
- **Copia de seguridad (backup) y recuperación:** crear copias de los datos para restaurarlas si se pierden, y recuperar el sistema a un estado anterior tras un fallo o error.
- **Diccionario de datos:** base de datos de **metadatos** (datos sobre los datos de la BD principal): nombres de tablas, campos, tipos de datos y restricciones.
- **Índices:** estructuras que **aceleran la recuperación** de datos, pero pueden **reducir la velocidad** de inserción, actualización y borrado por el mantenimiento extra que requieren.
- **Lenguaje de Definición de Datos (DDL):** parte de SQL para definir y modificar la estructura de la BD (`CREATE`, `ALTER`, `DROP`).
- **Lenguaje de Manipulación de Datos (DML):** parte de SQL para operar sobre los datos (`SELECT`, `INSERT`, `UPDATE`, `DELETE`).
- **Sistema Gestor de Bases de Datos (SGBD):** software que facilita crear, manipular y administrar bases de datos, asegurando integridad, seguridad y eficiencia.
- **Transacción:** secuencia de operaciones que forman **una sola unidad lógica de trabajo** y debe completarse **entera** para que la BD mantenga su integridad.


