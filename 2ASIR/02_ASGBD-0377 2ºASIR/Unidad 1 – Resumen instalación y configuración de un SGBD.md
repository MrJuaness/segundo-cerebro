# Unidad 1: Instalación y configuración de un SGBD

Resumen explicado de forma sencilla para estudiar rápido. Recoge todos los apartados de la unidad en versión corta.

## 1. Lo básico para empezar

**Vocabulario que aparece todo el rato:**

- **Tabla**: donde se guardan los datos, en filas y columnas (como una hoja de Excel).
- **Campo (columna)**: cada tipo de dato de la tabla (nombre, edad…).
- **Registro (fila)**: un elemento concreto (un estudiante en particular).
- **Clave primaria**: campo que identifica a cada registro y no se repite (como el DNI).
- **Clave foránea**: campo que apunta a la clave primaria de otra tabla; así se relacionan las tablas.
- **Vista**: una «ventana» que enseña solo una parte de los datos, según quién mire.
- **Metadatos**: datos sobre los datos (estructura, restricciones, relaciones).

**BD y SGBD.** Una **base de datos (BD)** es un conjunto de datos relacionados, estructurados y organizados. Un **Sistema Gestor de Bases de Datos (SGBD)** es el software que permite **crearla, manipularla y administrarla**, garantizando **integridad, seguridad y eficiencia**.

> **Analogía de la biblioteca:** la BD son los libros bien ordenados; el SGBD es el bibliotecario que sabe dónde está todo, quién puede llevarse qué y que nada se pierda.

**El DBA (administrador de la BD)** es el guardián de la base de datos y el usuario más importante. En una frase: **gestiona, mantiene, protege y facilita el acceso**. Sus 5 funciones:

1. Entender qué información necesita la empresa.
2. Gestionar la BD (crear tablas, índices, modificar la estructura).
3. Mantenerla funcionando bien (monitorizar y ajustar el rendimiento).
4. Protegerla (medidas de seguridad).
5. Facilitar el acceso (políticas de acceso y datos en el formato adecuado).

A eso se suman las copias de seguridad y la gestión de usuarios y permisos. Dos consejos del libro: acudir siempre a la **documentación oficial** y administrar preferiblemente **con comandos** (más ágil que la interfaz gráfica).

## 2. Las 10 funciones de un SGBD (lo que hace)

| Nº | Función | En una frase |
| --- | --- | --- |
| 1 | Creación de la BD | Definir la estructura: tablas, tipos de dato, relaciones y restricciones |
| 2 | Manipulación de datos | Insertar (`INSERT`), actualizar (`UPDATE`), eliminar (`DELETE`) y consultar con SQL |
| 3 | Integridad | Datos correctos y sin contradicciones, con claves primarias y foráneas (no puedes matricular a un alumno en un curso que no existe) |
| 4 | Seguridad | **Autenticación** (¿quién eres?) + **autorización** (¿qué puedes hacer?). Ejemplo: el DNI en la puerta y la tarjeta que solo abre ciertas plantas |
| 5 | Concurrencia y transacciones | Que varios usuarios trabajen a la vez sin estropear datos; confirmar (`COMMIT`) o deshacer (`ROLLBACK`) |
| 6 | Respaldo y recuperación | Copias de seguridad y volver a un estado anterior si hay fallos |
| 7 | Rendimiento | **Índices** (como el índice de un libro: aceleran las lecturas, pero ralentizan insertar, actualizar y borrar) y optimización de consultas |
| 8 | Diccionario de datos | Registro de los metadatos de la BD |
| 9 | Interfaz y herramientas | Interfaz gráfica (GUI) o de comandos, y herramientas de desarrollo |
| 10 | Escalabilidad y tolerancia a fallos | Aguantar más datos y usuarios, y seguir funcionando ante fallos usando redundancia (copias) |

**Transacciones y ACID.** Una transacción es un conjunto de operaciones que se ejecutan como **una unidad: o se hace todo o no se hace nada**. Se asegura con las propiedades ACID:

| Letra | Propiedad | Significa |
| --- | --- | --- |
| A | Atomicidad | Se hace entera o no se hace |
| C | Consistencia | La BD pasa de un estado válido a otro válido |
| I | Aislamiento | Las transacciones simultáneas no se interfieren |
| D | Durabilidad | Lo confirmado queda guardado de forma permanente |

*Ejemplo:* transferir 100 € de A a B son dos pasos (restar a A, sumar a B). Si el sistema falla entre ambos, se pierden 100 €. Con una transacción, o se hacen los dos (`COMMIT`) o se deshace todo (`ROLLBACK`).

## 3. Componentes de un SGBD (de qué piezas está hecho)

Las funciones son **lo que hace**; los componentes son **las piezas**. Son 8:

1. **Motor de BD**: el núcleo. Interpreta consultas y comandos y gestiona los recursos para ejecutarlos.
2. **Diccionario de datos**: guarda los metadatos (nombres de tablas y campos, tipos, restricciones, índices).
3. **DML** (manipulación): `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
4. **DDL** (definición): `CREATE`, `ALTER`, `DROP`.
5. **Gestor de transacciones**: las ejecuta aisladas entre sí y confirma sus cambios de forma permanente.
6. **Gestor de recuperación**: devuelve la BD a un estado consistente tras un fallo.
7. **Gestor de concurrencia**: controla el acceso simultáneo y evita conflictos.
8. **Interfaz de usuario**: GUI (ventanas y botones) o CLI (línea de comandos).

## 4. Usuarios de una BD

| Perfil | Qué puede hacer |
| --- | --- |
| **DBA** | Nivel de acceso más alto: crea y elimina BD y objetos, **da y quita permisos**, optimiza y define la seguridad |
| **RESOURCE** | **Crea sus propios objetos** (tablas, vistas…), pero no da permisos a otros. Suelen ser desarrolladores |
| **CONNECT** | Solo **accede** a lo que le han permitido. No crea objetos ni da permisos. Suelen ser usuarios finales |
| **Especializados** | Escriben aplicaciones para interactuar con la BD; conocen bien su estructura |
| **Casuales** | Usan un procesador de consultas; pueden no conocer la estructura |
| **Esporádicos** | Hacen consultas especializadas y complejas (analistas, científicos de datos) |

**Truco:** los tres primeros son una escalera de poder: DBA (todo) → RESOURCE (crea lo suyo) → CONNECT (solo usa lo que le dan).

## 5. Tipos de SGBD

Se clasifican según **cómo organizan los datos**:

| Tipo | Cómo organiza | Pros / contras | Ejemplo |
| --- | --- | --- | --- |
| **Relacional** | Tablas unidas por claves primarias y foráneas; se manejan con **SQL** | El más usado. Integridad, seguridad (control de acceso y cifrado) y eficiencia (índices y particionamiento) | MySQL, Oracle, SQL Server |
| **De red** | Registros unidos por **enlaces** (un empleado puede estar en varios departamentos y proyectos) | Muy flexible, pero complejo de diseñar y gestionar | IDS (IBM) |
| **Jerárquico** | **Árbol**: nodos (registros) y aristas (relaciones). Cada empleado pertenece a un solo departamento | Simple y eficiente con jerarquías, poco flexible con lo demás | IMS (IBM) |
| **Orientado a objetos** | Datos como **objetos** (instancias de clases) con herencia y polimorfismo | Flexible y reutilizable, pero complejo | MongoDB (según el libro) |

*Vocabulario de objetos:* la **clase** es el molde («Estudiante»), el **objeto** es una pieza hecha con ese molde («Ana»), la **herencia** deja reutilizar lo de otra clase y el **polimorfismo** hace que un mismo método se comporte distinto según el objeto.

**Ejemplo relacional:** `Estudiantes` (1 Ana, 2 Luis), `Cursos` (10 Bases de Datos, 11 Redes) y `Registro` (1-10, 1-11, 2-10). `Registro` relaciona las otras dos con claves foráneas: Ana está en los dos cursos y Luis solo en Bases de Datos.

**Otras formas de clasificarlos** (el libro solo las nombra):

| Criterio | Opciones |
| --- | --- |
| Número de usuarios | Monousuario (uno a la vez) / Multiusuario (varios a la vez) |
| Sitios donde se alojan | Centralizados (en un sitio) / Distribuidos (repartidos) |
| Ámbito | Propósito general (cualquier uso) / Propósito específico (una tarea concreta) |

**Las reglas de Codd.** Edgar F. «Ted» Codd (1923-2003) creó el modelo relacional. Sus «12 reglas» son en realidad **13 (de la 0 a la 12)** y marcan qué debe cumplir una BD para ser relacional:

| Nº | Regla | Idea |
| --- | --- | --- |
| 0 | Fundamental | Gestionar los datos solo con capacidades relacionales |
| 1 | Información | Todo se representa como valores en tablas |
| 2 | Acceso garantizado | Cualquier dato se localiza con tabla + clave primaria + columna |
| 3 | Valores nulos | «No hay dato» (NULL) se trata siempre igual y no es 0 ni texto vacío |
| 4 | Catálogo dinámico | La descripción de la BD está también en tablas y se consulta igual |
| 5 | Sublenguaje completo | Un lenguaje (SQL) para definir, manipular, asegurar y gestionar transacciones |
| 6 | Actualización de vistas | Las vistas actualizables deben poder actualizarse |
| 7 | Operaciones de alto nivel | Insertar, modificar y borrar conjuntos de filas |
| 8 | Independencia física | Si cambia el almacenamiento, los programas no cambian |
| 9 | Independencia lógica | Si cambia la estructura lógica, los programas no se ven afectados |
| 10 | Independencia de integridad | Las reglas se guardan en el catálogo, no en los programas |
| 11 | Independencia de distribución | Los programas no notan dónde están los datos |
| 12 | No subversión | Un acceso de bajo nivel no puede saltarse la integridad |

Las reglas 8 y 9 recuerdan a los 3 niveles de ANSI/SPARC, la 4 al diccionario de datos y la 5 a SQL.

## 6. Arquitectura ANSI/SPARC (3 niveles)

Modelo para diseñar y administrar BD (ANSI y SPARC son sus creadores). Divide la BD en 3 niveles:

| Nivel | Qué ve o hace | Ejemplo |
| --- | --- | --- |
| **Externo** (de vista) | Presenta los datos a cada usuario final. Puede haber **varias vistas** | Finanzas ve solo datos financieros; RR. HH. solo datos de empleados |
| **Conceptual** (lógico) | **Qué datos** hay y **qué relaciones** tienen (en relacional: tablas, columnas, relaciones). Oculta los detalles físicos. Aquí se usa SQL | El catálogo de la biblioteca |
| **Interno** (físico) | **Cómo se guardan** los datos: archivos, índices, compresión y cifrado (con estructuras como B-trees o hash maps) | En qué estantería está cada libro |

## 7. SGBD libres y comerciales

- **Libres**: código libre, **no cuestan dinero**. MySQL (el más popular en la web, sobre todo con PHP), PostgreSQL (relacional orientado a objetos), MariaDB (derivado de MySQL, licencia GPL), SQLite (biblioteca en C) y MongoDB.
- **De mercado**: **licencia propietaria**, **tienen coste**. Los dos más populares: **Microsoft SQL Server** y **Oracle Database** (objeto-relacional).
- **Matiz:** MySQL lo desarrolla Oracle y tiene licencia pública general **y también comercial**.

## 8. SQL, el idioma del SGBD

**SQL** (*Structured Query Language*) es el lenguaje estándar para gestionar y manipular BD. Se divide en 3 grupos:

| Grupo | Sirve para | Comandos |
| --- | --- | --- |
| **DDL** (Definición) | Definir y modificar la **estructura** | `CREATE`, `ALTER`, `DROP` |
| **DML** (Manipulación) | Trabajar con los **datos** | `SELECT`, `INSERT`, `UPDATE`, `DELETE` |
| **DCL** (Control) | Controlar el **acceso** | `GRANT` (dar permisos), `REVOKE` (quitarlos) |

**Truco:** DDL = **D**efinir, DML = **M**anipular, DCL = **C**ontrolar.

```sql
CREATE DATABASE academia;                          -- DDL
CREATE TABLE estudiantes (id INT PRIMARY KEY, nombre VARCHAR(50));
INSERT INTO estudiantes VALUES (1, 'Ana');         -- DML
SELECT * FROM estudiantes;
UPDATE estudiantes SET nombre = 'Ane' WHERE id = 1;
DELETE FROM estudiantes WHERE id = 1;
GRANT SELECT ON academia.estudiantes TO 'ana'@'localhost';   -- DCL
```

## 9. Instalar y configurar MySQL (Windows 10)

**MySQL** lo desarrolla Oracle, es relacional y muy usado. Tiene dos componentes principales: **MySQL Server** (el núcleo, el «almacén» donde viven los datos) y **MySQL Workbench** (herramienta visual para hacer consultas, el «mostrador»).

**1. Descarga**

- Web oficial → **MySQL Community Server** → **MySQL Installer for Windows** → *Windows (x86, 32-bit), MSI Installer*.
- Hay dos versiones: la que descarga ficheros durante la instalación y el paquete completo. La del curso es la **8.0.28**.
- No hace falta registrarse: usa el enlace de la zona inferior.

**2. Instalación** (con el sistema operativo actualizado)

- **Developer Default**: instala todo lo necesario; recomendada para principiantes.
- **Custom**: para quien ya tiene experiencia. Eliges **MySQL Servers**, **MySQL Workbench** (en *Applications*, será el cliente) y **MySQL Connections** (lo mejor es instalar todas; para la de Python hay que tener Python instalado), y opcionalmente la documentación.
- Pulsa **Next** → **Execute** (se instala el paquete *Microsoft Visual C++ 2015* si falta) → **Yes** → **Execute**.

**3. Configuración inicial** (fase crítica)

| Tipo de equipo | Para qué |
| --- | --- |
| **Development Computer** | Equipo que tiene servidor y cliente. **El de uso doméstico** |
| **Server Computer** | Equipos que hacen de servidor (p. ej. servidor web con BD) |
| **Dedicated Computer** | Equipo solo para BD (p. ej. una máquina virtual) |

- **Puerto TCP: 3306** por defecto (el que se abre en el router para conexiones remotas). El resto de opciones, por defecto.
- **Contraseña** del usuario administrador, que es **root** (se puede cambiar luego).
- Nombre del servicio y arranque del demonio (el programa servidor que queda en segundo plano).
- **Execute** para activar los servicios. Si sale una **x roja**, hay que revisar el **log de errores**.

**4. Conectar con Workbench**

Pulsa **+** en *MySQL Connections* y rellena: nombre de la conexión, protocolo **TCP/IP**, hostname **127.0.0.1** (este mismo equipo; en red local, la IP del servidor), puerto **3306** y usuario **root**. Pulsa *Test connection* (pide la clave) y después te conectas con un clic.

**Resumen:** descargar (8.0.28) → ejecutar → Developer Default o Custom → Next/Execute → Yes/Execute → configurar (equipo, puerto 3306, clave de root, servicio) → Execute → conectar con Workbench.

## 10. Integración con el sistema operativo e instalación en dos capas

**El SGBD es una capa entre los usuarios y el sistema de archivos:**

`Usuario → SGBD → Sistema de archivos (SO) → Disco duro`

1. **Sistema de archivos**: parte del SO que lee y escribe en el disco. Cada BD es un archivo o un conjunto de archivos.
2. **Control de usuarios**: cada usuario tiene privilegios que se **comprueban en cada operación**.
3. **SGBD**: ofrece una interfaz para usar las BD sin preocuparse de cómo se guardan.

El libro lo ilustra con un código en Python muy simplificado: el SGBD, antes de crear o leer una BD, **pregunta al SO si el usuario es válido** (autenticación) y solo entonces usa el sistema de archivos. Un SGBD real es mucho más complejo: gestiona concurrencia, recuperación de errores y optimización, y protege las contraseñas.

**Instalación de dos capas** (cliente y servidor):

1. **Servidor**: instalas el SGBD, que aloja las BD. Puede haber que configurar el tamaño máximo, la ubicación de los archivos y la seguridad.
2. **Cliente**: instalas el software que se conecta al servidor para hacer consultas.
3. **Conexión**: configurar la red y la seguridad de la comunicación.
4. **Configuración del SGBD**: crear BD, usuarios y permisos, y optimizar el rendimiento.

En MySQL: el Server es la capa servidor, Workbench la cliente, el host/IP y el puerto 3306 son la conexión, y `root` es el usuario con el que entras.

## 11. SGBD, BD e instancia

| Concepto | Qué es |
| --- | --- |
| **SGBD** | El **software** (MySQL, PostgreSQL, MongoDB…) que crea, lee, actualiza y elimina datos |
| **BD** | El **conjunto organizado de datos**, el «contenedor» |
| **Instancia** | Una **representación completa de la BD en un momento concreto**. Se crea al **iniciar el SGBD** y dura mientras funciona. Incluye los datos **y los procesos** que los manejan |

*Ejemplo:* en una tienda online, la instancia del 1 de enero de 2024 incluye los productos, clientes y pedidos hasta ese día. Lo que se añada el día 2 no está en esa instancia, pero sí en la nueva. Piensa en una «foto» de la BD más los procesos que la manejan.

## 12. Diccionario de datos (catálogo del sistema)

Guarda **metadatos**: es como el catálogo de la biblioteca, que no contiene los libros sino información sobre ellos. Incluye:

- **Estructura**: nombres de tablas y campos, y tipo de dato de cada campo.
- **Reglas**: restricciones (clave primaria, si admite nulos…), relaciones (claves foráneas) e índices.
- **Objetos programados**: vistas, procedimientos almacenados y funciones.
- **Seguridad y uso**: roles y permisos, y estadísticas de acceso.

La estructura exacta varía según el SGBD.

## 13. Ficheros LOG

El log es el «diario» donde el SGBD apunta lo que hace. Garantiza **integridad** y **recuperación**. Sirve para:

- **Registrar transacciones**: cada inserción, actualización o borrado queda anotado (tipo, datos y momento).
- **Recuperarse de fallos** (corte de luz, error de software): **deshace** lo que quedó a medias y **rehace** lo que se completó pero aún no se había escrito en la BD.
- **Controlar la concurrencia**: ver cuál de dos transacciones en conflicto fue primero.
- **Auditar**: es un registro histórico de todo lo que pasó.

Ocupan mucho espacio, así que se aplican políticas de **rotación** (cambiar a ficheros nuevos y archivar los viejos) y **purga** (borrar los que ya no hacen falta).

## 14. Cómo funciona por dentro

Imagina una oficina: los archivadores son el disco, la mesa de trabajo es la memoria y los empleados son los procesos.

| Parte                 | Elementos                                                                                                                                                                                                   |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Archivos en disco** | **De datos** (los datos reales), **de índice** (mapas hacia la ubicación de los registros) y **de log** (transacciones, para recuperar tras un fallo)                                                       |
| **Memoria**           | **Buffer de datos** (guarda temporalmente lo que se lee o escribe, para evitar accesos al disco), **caché de índices** (acelera consultas) y **pool de conexiones** (conexiones abiertas que se reutilizan) |
| **Procesos**          | **De usuario** (ejecutan las consultas; uno por conexión) y **de fondo** (mantenimiento: limpiar memoria, escribir en disco los datos modificados, gestionar logs)                                          |

## 15. Chuleta final

- **Funciones**: 10 · **Componentes**: 8 · **Usuarios**: 6 · **Tipos de SGBD**: 4 · **Reglas de Codd**: 13 (0-12) · **Niveles ANSI/SPARC**: 3 · **Funciones del DBA**: 5 · **Grupos de SQL**: 3.
- **Ideas clave:** el SGBD es el software y la BD son los datos; la instancia es la BD en marcha en un momento dado; los metadatos viven en el diccionario de datos; los logs permiten deshacer y rehacer.
- **MySQL:** versión 8.0.28, puerto **3306**, usuario **root**, host **127.0.0.1**, Workbench como cliente.
- **Antes de instalar un SGBD**, elige cuál según tus requisitos y consulta siempre su documentación técnica.
