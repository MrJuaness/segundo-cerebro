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