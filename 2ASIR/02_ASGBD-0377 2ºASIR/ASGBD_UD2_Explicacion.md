# ASGBD_U2_Acceso a la información

**Explicación para principiantes**, basada solo en el PDF «ASGBD_UD2» (Tech Hub FP Euroformac, Administración de Sistemas Gestores de Bases de Datos).

## Contenido

- Objetivos e introducción
- 1. Tipos de objetos de la BD
- 2. Crear, modificar y eliminar vistas
- 3. Operaciones DML sobre vistas
- 4. Crear, modificar y eliminar usuarios
- 5. Asignar y retirar permisos a usuarios (5.1 Puntos de acceso al sistema)
- 6. Roles: paquetes de permisos (6.1, 6.2, 6.3)
- 7. Normativa legal sobre protección de datos
- 8. Perfiles: límites en el SGBD
- 9. Retirada de límites a usuarios
- 10. Resumen del PDF
- 11. Glosario
- 12. Bibliografía
- Notas mías (no están en el PDF)

---

Antes de empezar, dos palabras que vas a ver todo el rato. Un **SGBD** (Sistema de Gestión de Bases de Datos) es el programa que guarda y gestiona las bases de datos. **SQL** es el lenguaje con el que le das órdenes. Cada SGBD (MySQL, Oracle...) escribe algunas órdenes a su manera, así que la sintaxis cambia un poco de un apartado a otro. El propio PDF lo avisa.

## Objetivos e introducción

**Objetivos del PDF:** dominar ciertos comandos de administración y conocer los esenciales para crear vistas y para gestionar usuarios, permisos, perfiles y recursos de las bases de datos.

**Introducción, en fácil.** Una base de datos tiene que ser accesible de forma **controlada y eficiente**, para proteger dos cosas:

- la **integridad**: que los datos sean correctos y no se estropeen;
- la **privacidad**: que solo los vea quien debe.

La unidad avanza en este orden:

1. **Tipos de objetos** de una base de datos, cada uno con su papel al organizar y recuperar datos.
2. **Vistas**: mostrar los datos de forma distinta a distintos usuarios sin tocar la estructura de la base de datos (útil para la seguridad y para personalizar el acceso).
3. **DML sobre vistas**: cambiar la información que muestran las vistas de forma controlada y segura.
4. **Usuarios y permisos**: cómo se controla quién entra y qué puede hacer.
5. **Roles**: paquetes de permisos que simplifican la administración y hacen que la seguridad siga siendo manejable cuando hay muchos usuarios (eso es la «escalabilidad»).
6. **Normativa legal** sobre datos personales, para que los sistemas que administras la cumplan.

Los **perfiles** (límites de recursos) no salen en la introducción, pero sí en los objetivos y en el índice.

## 1. Tipos de objetos de la BD

Un **objeto** es cada cosa que puedes crear dentro de una base de datos. El PDF presenta cinco.

### 1.1 Tablas

Es la estructura principal, donde se guardan los datos. Piensa en una hoja de Excel: cada **columna** es un dato (nombre, edad...) y cada **fila** es un registro (un empleado).

```sql
CREATE TABLE Empleados (
    ID INT PRIMARY KEY,
    Nombre VARCHAR(100),
    Edad INT,
    Salario DECIMAL(10, 2)
);
```

- `CREATE TABLE Empleados (...)`: crea una tabla llamada Empleados. Entre paréntesis van sus columnas.
- `ID INT PRIMARY KEY`: columna ID de tipo número entero (`INT`). `PRIMARY KEY` (clave primaria) la convierte en el identificador único de cada fila: no puede haber dos empleados con el mismo ID.
- `Nombre VARCHAR(100)`: texto de hasta 100 caracteres.
- `Edad INT`: número entero.
- `Salario DECIMAL(10, 2)`: número con decimales, de hasta 10 cifras en total y 2 decimales (por ejemplo, 1500.75).

### 1.2 Vistas

Son una representación **virtual** de una tabla o de la combinación de varias. Sirven para simplificar consultas complejas y para dar un nivel extra de seguridad. «Virtual» significa que no es una tabla con datos propios: es una consulta guardada con nombre, una ventana que solo deja ver lo que tú decidas.

```sql
CREATE VIEW VistaEmpleados AS
SELECT Nombre, Salario
FROM Empleados;
```

- `CREATE VIEW VistaEmpleados AS`: crea una vista llamada VistaEmpleados que será el resultado de la consulta que sigue.
- `SELECT Nombre, Salario FROM Empleados`: la consulta, que coge solo esas dos columnas de la tabla Empleados.

Quien use esta vista verá nombre y salario, pero no el ID ni la edad. Ahí está la seguridad extra.

### 1.3 Índices

Sirven para que las consultas sean más rápidas. Crean una estructura de datos especializada que facilita y acelera las búsquedas (el glosario lo resume como «ordenar los datos de un campo»). Es como el índice de un libro: en vez de leer todas las páginas para encontrar un tema, vas directo a la página.

```sql
CREATE INDEX idx_Empleados_Nombre
ON Empleados (Nombre);
```

Crea un índice llamado `idx_Empleados_Nombre` sobre la columna `Nombre` de la tabla `Empleados`, así que buscar por nombre será más rápido. El nombre del índice lo eliges tú. Aquí sigue el patrón idx_Tabla_Columna.

### 1.4 Procedimientos almacenados

Son bloques de código SQL que se guardan en la propia base de datos para realizar una tarea concreta. Es como una receta guardada: la escribes una vez y la ejecutas cuando la necesites.

```sql
CREATE PROCEDURE AumentarSalario
    @ID INT,
    @Aumento DECIMAL
AS
    UPDATE Empleados
    SET Salario = Salario + @Aumento
    WHERE ID = @ID;
```

- `@ID INT, @Aumento DECIMAL`: los **parámetros**, los datos que le das cada vez que lo usas (a qué empleado y cuánto sube). La `@` marca esos nombres como variables.
- `AS`: a partir de aquí viene lo que hace el procedimiento.
- `UPDATE Empleados SET Salario = Salario + @Aumento WHERE ID = @ID`: nuevo salario = salario actual + aumento, solo para el empleado cuyo ID coincide. Sin el `WHERE` subiría el sueldo a todos.

### 1.5 Funciones

Son parecidas a los procedimientos, pero **pueden devolver un valor**, y además se pueden usar dentro de otras instrucciones SQL.

```sql
CREATE FUNCTION ObtenerSalario(@ID INT)
RETURNS DECIMAL
AS
BEGIN
    DECLARE @Salario DECIMAL;
    SELECT @Salario = Salario FROM Empleados WHERE ID = @ID;
    RETURN @Salario;
END;
```

- `ObtenerSalario(@ID INT)`: el nombre y el dato que necesita (un ID).
- `RETURNS DECIMAL`: avisa de que devolverá un número decimal.
- `BEGIN ... END`: marcan el principio y el final del cuerpo (en el PDF el `END;` cae ya en la página 8).
- `DECLARE @Salario DECIMAL`: crea una variable, una cajita temporal.
- `SELECT @Salario = Salario ...`: busca el salario de ese empleado y lo guarda en la cajita.
- `RETURN @Salario`: devuelve el contenido de la cajita.

Según el resumen del PDF, los procedimientos automatizan tareas comunes dentro de la base de datos. Las funciones están pensadas para devolver valores, para hacer cálculos o procesar información.

El PDF cierra el apartado diciendo que estos son solo algunos ejemplos y que cada objeto tiene un propósito específico para gestionar y manipular los datos de forma eficiente.

## 2. Crear, modificar y eliminar vistas

Recuadro «Importante» del PDF: en un SGBD que siga el **modelo relacional** (datos organizados en tablas), una vista es una **tabla virtual** que representa el resultado de una consulta.

Son tareas fundamentales de la administración de bases de datos:

| Tarea | Instrucción | Cómo se usa |
|---|---|---|
| Crear | `CREATE VIEW` | seguida de la consulta SQL que define la vista |
| Modificar | `ALTER VIEW` | seguida de la nueva definición de la vista |
| Eliminar | `DROP VIEW` | seguida del nombre de la vista |

Ejemplo mío (el PDF solo da las instrucciones), con la vista del apartado 1:

```sql
ALTER VIEW VistaEmpleados AS
SELECT Nombre, Edad, Salario
FROM Empleados;            -- ahora la vista también muestra la edad

DROP VIEW VistaEmpleados;  -- la vista desaparece
```

Como la vista es solo una «ventana», borrarla no borra los datos de la tabla Empleados.

**Ojo:** tanto modificar como eliminar una vista **puede afectar a las aplicaciones que dependen de ella**. Si un programa usa la vista y le cambias las columnas o la borras, puede dejar de funcionar.

El PDF repite en casi todos los apartados dos recordatorios, y aquí van una vez más:

- Estas operaciones las debe hacer un usuario con **los permisos adecuados** (más adelante concreta: el administrador de la base de datos, o DBA).
- Conviene hacer una **copia de seguridad** (backup) antes de cambios significativos.

## 3. Operaciones DML sobre vistas

**DML** (*Data Manipulation Language*, Lenguaje de Manipulación de Datos) son las instrucciones para trabajar con los datos. El PDF incluye `INSERT` (añadir), `UPDATE` (modificar), `DELETE` (borrar) y `SELECT` (consultar). Se pueden usar con vistas, pero con restricciones.

**Idea clave:** si haces INSERT, UPDATE o DELETE sobre una vista, el cambio se aplica a la **tabla subyacente**, la tabla real de la que sale la vista. Lo que escribes en la ventana se escribe en lo que hay detrás.

En el PDF verás ``` y ** sueltos. Son restos de formato, no forman parte del código. Y `vista`, `columna1`, `valor1`, `condicion`... son huecos que sustituirías por nombres reales.

**INSERT** añade filas. La vista debe estar definida sobre **una única tabla**:

```sql
INSERT INTO vista (columna1, columna2)
VALUES (valor1, valor2);
```

Inserta una fila nueva con esos valores en esas columnas, y el dato acaba en la tabla subyacente.

**UPDATE** modifica filas. También se aplica a la tabla subyacente, pero **no todas las vistas son actualizables**: si la consulta de la vista contiene `JOIN`, `GROUP BY`, `HAVING` o `UNION`, no se puede actualizar.

```sql
UPDATE vista
SET columna1 = nuevo_valor
WHERE condicion;
```

Para entender esas cuatro palabras:

- `JOIN` une datos de varias tablas.
- `GROUP BY` agrupa filas (por ejemplo, para sumar por departamento).
- `HAVING` filtra esos grupos.
- `UNION` junta los resultados de varias consultas.

En todos esos casos una fila de la vista deja de corresponder a una única fila de una única tabla, y el SGBD no sabría qué modificar. Esa explicación es mía, el PDF solo da la regla. `WHERE condicion` limita qué filas se cambian. Sin él se cambiarían todas.

**DELETE** borra filas de la tabla subyacente. Igual que con UPDATE, no todas las vistas son «eliminables»:

```sql
DELETE FROM vista
WHERE condicion;
```

**SELECT** consulta. Como una vista es una tabla virtual, se usa igual que una tabla:

```sql
SELECT columna1, columna2
FROM vista
WHERE condicion;
```

Con nuestra vista, por ejemplo (ejemplo mío): `SELECT Nombre, Salario FROM VistaEmpleados WHERE Salario > 2000;`

El apartado cierra igual que el anterior: solo un usuario con los permisos necesarios debe ejecutar estas operaciones, y se aconseja encarecidamente una copia de seguridad antes de cambios importantes.

## 4. Crear, modificar y eliminar usuarios

Un **usuario** es la cuenta con la que alguien entra al SGBD. Gestionarlos es una tarea fundamental de administración.

**Crear:**

```sql
CREATE USER 'nombre_usuario'@'localhost' IDENTIFIED BY 'contraseña';
```

- `CREATE USER`: crea el usuario.
- `'nombre_usuario'@'localhost'`: el nombre, una `@` y el equipo desde el que puede conectarse. `localhost` es el propio equipo donde está el servidor de la base de datos.
- `IDENTIFIED BY 'contraseña'`: su contraseña.

En un caso real sustituyes `nombre_usuario` y `contraseña` por valores reales.

**Modificar** se hace con `ALTER USER`, seguida del nombre del usuario y los nuevos valores. El PDF enseña el ejemplo de cambiar la contraseña:

```sql
ALTER USER 'nombre_usuario'@'localhost' IDENTIFIED BY 'nueva_contraseña';
```

**Eliminar** se hace con `DROP USER`, seguida del nombre del usuario:

```sql
DROP USER 'nombre_usuario'@'localhost';
```

Como siempre, lo debe hacer alguien con permisos adecuados, como el **DBA** (administrador de la base de datos), y conviene copia de seguridad antes de cambios significativos.

**Recuadro «Sabías que»** (una curiosidad, no es un comando): el modelo relacional fue propuesto en **1970** por el Dr. **E. F. Codd** en el Laboratorio de Investigación de **IBM** en San José, California. Se desarrolló durante la década siguiente en universidades y laboratorios de investigación. **SQL** es uno de varios lenguajes que surgieron de ese trabajo y hoy domina casi por completo el mundo de los lenguajes de bases de datos relacionales.

## 5. Asignar y retirar permisos a usuarios

Crear un usuario no basta: hay que decidir qué puede hacer. Eso son los **permisos**, también llamados **privilegios**. Piensa en llaves: `GRANT` entrega llaves y `REVOKE` las retira.

**Asignar (GRANT):**

```sql
GRANT SELECT, INSERT ON mi_base_de_datos.* TO 'nombre_usuario'@'localhost';
```

- `GRANT SELECT, INSERT`: concede leer (`SELECT`) y añadir registros (`INSERT`).
- `ON mi_base_de_datos.*`: sobre qué. Es la base de datos `mi_base_de_datos`, y el `*` significa «todas sus tablas».
- `TO 'nombre_usuario'@'localhost'`: a quién.

**Retirar (REVOKE):**

```sql
REVOKE SELECT, INSERT ON mi_base_de_datos.* FROM 'nombre_usuario'@'localhost';
```

Le quita esos dos permisos en todas las tablas de la base. Truco para no liarte: **GRANT va con TO, REVOKE va con FROM**.

De nuevo: lo hace alguien con permisos adecuados (DBA) y conviene copia de seguridad antes.

### 5.1 Puntos de acceso al sistema

El PDF llama así a los **permisos que tiene un usuario para interactuar con la base de datos** (lectura, escritura, actualización, eliminación, entre otros). Los permisos o privilegios definen qué acciones puede realizar un usuario concreto. Estos son los que cita:

| Permiso | Qué permite |
|---|---|
| `CREATE` | Crear nuevas tablas o bases de datos |
| `DROP` | Eliminar tablas o bases de datos |
| `SELECT` | Leer los datos de una base de datos |
| `INSERT` | Agregar nuevos registros |
| `UPDATE` | Modificar registros existentes |
| `DELETE` | Eliminar registros |
| `GRANT OPTION` | Otorgar o quitar privilegios a otros usuarios |

Para no confundirte: `CREATE` y `DROP` trabajan con las **estructuras** (tablas, bases de datos). `INSERT`, `UPDATE` y `DELETE` trabajan con los **datos** (registros) que hay dentro.

Además, el PDF distingue tres **categorías de usuarios**:

| Categoría | Qué puede hacer |
|---|---|
| **DBA** (Database Administrator) | Tiene el nivel más alto de privilegios. Su función es administrar la base de datos |
| **RESOURCE** | Puede crear sus propios objetos y acceder a aquellos para los que ha recibido permisos |
| **CONNECT** | Solo puede acceder a los objetos a los que se le ha otorgado permiso de acceso |

De más a menos poder: DBA, RESOURCE, CONNECT.

El apartado cierra repitiendo que los permisos los asigna un usuario con permisos adecuados (como el DBA) y que conviene una copia de seguridad antes de cambios significativos.

## 6. Roles: paquetes de permisos

Un **rol** es un conjunto de permisos que se asignan a los usuarios según lo que necesiten. Facilitan la administración porque agrupan varias entidades de seguridad. Dicho en fácil: en vez de dar diez llaves sueltas a cada empleado, le das un llavero ya preparado (el de «administrativo», por ejemplo). Es lo que la introducción llama simplificar la administración y facilitar la escalabilidad de la seguridad.

Hay dos tipos de roles en el nivel de base de datos:

- **Roles fijos de base de datos:** vienen preestablecidos y existen en todas las bases de datos. Los miembros del rol `db owner` (así escrito en el PDF) pueden gestionar quién pertenece a estos roles fijos.
- **Roles personalizados:** los crea el usuario. Sus permisos se ajustan con `GRANT` (dar), `REVOKE` (retirar) y `DENY`. El PDF nombra `DENY` pero no lo desarrolla. Viene a ser «denegar» un permiso expresamente.

### 6.1 Creación y eliminación

```sql
CREATE ROLE nombre_rol;                            -- crear el rol
DROP ROLE nombre_rol;                              -- eliminar el rol
ALTER ROLE nombre_rol ADD MEMBER nombre_usuario;   -- meter un usuario en el rol
ALTER ROLE nombre_rol DROP MEMBER nombre_usuario;  -- sacar un usuario del rol
```

Fíjate en la diferencia: `DROP ROLE` borra el rol entero. `ALTER ROLE ... DROP MEMBER` solo saca a un usuario del rol, que sigue existiendo. «Miembro» es un usuario que está dentro del rol.

Otra vez: DBA y copia de seguridad.

### 6.2 Dar y quitar permisos a roles

Se usan las mismas instrucciones `GRANT` y `REVOKE`, pero el destinatario es un rol:

```sql
GRANT SELECT, INSERT ON mi_base_de_datos.* TO nombre_rol;
REVOKE SELECT, INSERT ON mi_base_de_datos.* FROM nombre_rol;
```

La plantilla es `GRANT permiso ON base_de_datos_o_tabla TO rol` y `REVOKE permiso ON base_de_datos_o_tabla FROM rol`. La primera da `SELECT` e `INSERT` al rol en todas las tablas de `mi_base_de_datos`. La segunda se los quita.

El PDF cierra recomendando consultar la documentación específica de tu SGBD para instrucciones más detalladas y ejemplos de código. También repite lo de DBA y copia de seguridad.

### 6.3 Dar y quitar roles a usuarios (ejemplo en MySQL)

Es el flujo completo en cinco pasos. La numeración del PDF sale un poco desordenada, pero los pasos son estos:

```sql
-- Paso 1: crear el rol
CREATE ROLE 'rol_ejemplo';

-- Paso 2: darle privilegios al rol (SELECT e INSERT en todas las tablas)
GRANT SELECT, INSERT ON mi_base_de_datos.* TO 'rol_ejemplo';

-- Paso 3: crear un usuario con contraseña segura
CREATE USER 'usuario_ejemplo'@'localhost' IDENTIFIED BY 'contraseña_segura';

-- Paso 4: asignar el rol al usuario
GRANT 'rol_ejemplo' TO 'usuario_ejemplo'@'localhost';

-- Paso 5: retirar el rol del usuario
REVOKE 'rol_ejemplo' FROM 'usuario_ejemplo'@'localhost';
```

Tras el paso 4, `usuario_ejemplo` tiene los privilegios que se dieron a `rol_ejemplo`. El paso 5 se los quita.

Compara con 6.1. Allí se mete un usuario en un rol con `ALTER ROLE ... ADD MEMBER`. Aquí, en MySQL, se hace con `GRANT rol TO usuario`. Es la misma idea con sintaxis distinta según el SGBD.

## 7. Normativa legal sobre protección de datos

El PDF cita tres normas vigentes en España:

1. **RGPD** (Reglamento General de Protección de Datos): Reglamento (UE) 2016/679 del Parlamento Europeo y del Consejo, de 27 de abril de 2016.
   - Se aplica en todos los países de la UE.
   - Fija las directrices generales de protección de datos personales.
   - Da a las personas más control sobre sus datos y pone normas estrictas a las empresas que los recogen y procesan.
2. **Ley Orgánica 3/2018, de 5 de diciembre**, de Protección de Datos Personales y garantía de los derechos digitales.
   - Es específica de España y desarrolla el derecho fundamental a la protección de datos personales.
   - Da pautas sobre cómo recoger, procesar, almacenar y compartir datos personales.
   - Establece los derechos de las personas: **acceder** a sus datos, **corregirlos**, **borrarlos** y **oponerse** a su tratamiento.
3. **Real Decreto 389/2021, de 1 de junio**, por el que se aprueba el Estatuto de la Agencia Española de Protección de Datos. Establece el estatuto de la AEPD, que es la autoridad encargada de garantizar que se cumplan las leyes de protección de datos en España.

Estas normas forman el marco legal. Fijan las responsabilidades de las empresas y organizaciones que gestionan datos personales y los derechos de las personas cuyos datos se procesan. **Incumplirlas puede acarrear sanciones severas**, económicas y legales, así que empresas e individuos deben entenderlas y cumplirlas. Por eso aparecen en una unidad de administración: los sistemas que gestionas tienen que cumplirlas.

## 8. Perfiles: límites en el SGBD

Un **perfil** es una forma de gestionar y controlar los **recursos del sistema** que puede usar un usuario o un grupo de usuarios. Pone límites para evitar un uso excesivo o abusivo. Es como el límite de datos de tu tarifa del móvil: hasta aquí puedes gastar.

No lo confundas con los roles: un rol dice **qué puedes hacer** (permisos), y un perfil dice **cuántos recursos puedes gastar** (límites).

### Ejemplo en Oracle

**1. Crear un perfil:**

```sql
CREATE PROFILE perfil_ejemplo LIMIT
  SESSIONS_PER_USER 10
  CPU_PER_SESSION 30000
  CPU_PER_CALL 10000
  LOGICAL_READS_PER_SESSION 10000
  LOGICAL_READS_PER_CALL 1000
  PRIVATE_SGA 15K
  COMPOSITE_LIMIT 500000;
```

**2. Asignarlo a un usuario:**

```sql
ALTER USER usuario_ejemplo PROFILE perfil_ejemplo;
```

El primer comando crea `perfil_ejemplo` con varios límites, y `ALTER USER` se lo asigna a `usuario_ejemplo`. Qué significa cada límite:

| Límite | Valor | Significado |
|---|---|---|
| `SESSIONS_PER_USER` | 10 | Máximo de 10 sesiones simultáneas |
| `CPU_PER_SESSION` | 30000 | Máximo de 30000 unidades de CPU por sesión |
| `CPU_PER_CALL` | 10000 | Máximo de 10000 unidades de CPU por llamada a la base de datos |
| `LOGICAL_READS_PER_SESSION` | 10000 | Máximo de 10000 lecturas lógicas por sesión |
| `LOGICAL_READS_PER_CALL` | 1000 | Máximo de 1000 lecturas lógicas por llamada |
| `PRIVATE_SGA` | 15K | Máximo de 15K de memoria del área global del sistema (SGA) para uso privado |
| `COMPOSITE_LIMIT` | 500000 | Límite compuesto: según el PDF, se calcula multiplicando el uso de CPU por el factor de sesión y sumando el uso de SGA privada |

Vocabulario:

- **Sesión:** una conexión abierta del usuario con la base de datos.
- **Llamada:** cada petición que el usuario envía a la base de datos.
- **Lecturas lógicas:** lecturas de datos que hace el usuario, o sea, cuántos datos consulta.
- **SGA:** área global del sistema, una zona de memoria del servidor.
- **COMPOSITE_LIMIT**, en fácil: un tope total que mezcla varios recursos a la vez en lugar de uno solo.

El PDF avisa de que estos límites pueden variar según el SGBD.

### Ejemplo en MySQL

MySQL no tiene «perfiles» como tal. Los límites se establecen sobre todo a través de los privilegios de los usuarios, y se controla el acceso y los recursos gestionando esos privilegios.

```sql
-- 1. Crear un nuevo usuario
CREATE USER 'usuario_ejemplo'@'localhost' IDENTIFIED BY 'contraseña_segura';

-- 2. Asignarle privilegios
GRANT SELECT, INSERT ON mi_base_de_datos.* TO 'usuario_ejemplo'@'localhost';

-- 3. Establecer límites de recursos
SET GLOBAL max_connections_per_hour = 100;
SET GLOBAL max_updates_per_hour = 1000;
SET GLOBAL max_user_connections = 10;
```

Los pasos 1 y 2 crean el usuario y le dan `SELECT` e `INSERT` en `mi_base_de_datos`. Los límites del paso 3 son:

- `max_connections_per_hour = 100`: máximo de 100 conexiones por hora.
- `max_updates_per_hour = 1000`: máximo de 1000 instrucciones de actualización por hora.
- `max_user_connections = 10`: máximo de 10 conexiones simultáneas.

**Recuadro «Importante»:** estos límites son **globales** y afectan a todos los usuarios. Si quieres límites específicos para un usuario, puedes fijarlos al crearlo con `CREATE USER`. Aunque el paso 3 se presenta como límites «para el usuario», quédate con esta aclaración: `SET GLOBAL` significa para todos.

## 9. Retirada de límites a usuarios

En MySQL puedes retirar los límites de un usuario con `GRANT` y la opción `WITH ... 0`. El valor **0 significa «sin límite»**:

```sql
GRANT USAGE ON *.* TO 'usuario_ejemplo'@'localhost'
WITH MAX_QUERIES_PER_HOUR 0
     MAX_CONNECTIONS_PER_HOUR 0
     MAX_UPDATES_PER_HOUR 0
     MAX_USER_CONNECTIONS 0;
```

(En el PDF va en dos líneas seguidas. Aquí está partido solo para leerlo mejor.)

- `GRANT USAGE`: no concede ningún permiso nuevo. Se usa para poder cambiar solo los límites.
- `ON *.*`: en todas las bases de datos y todas las tablas.
- `TO 'usuario_ejemplo'@'localhost'`: el usuario afectado.
- `WITH ... 0`: pone cada límite a 0.

Se retiran estos cuatro límites:

- `MAX_QUERIES_PER_HOUR 0`: consultas por hora ilimitadas.
- `MAX_CONNECTIONS_PER_HOUR 0`: conexiones por hora ilimitadas.
- `MAX_UPDATES_PER_HOUR 0`: actualizaciones por hora ilimitadas.
- `MAX_USER_CONNECTIONS 0`: conexiones simultáneas ilimitadas.

## 10. Resumen del PDF

- **Objetos:**
  - Las tablas guardan los datos en filas y columnas y son el núcleo de cualquier base de datos.
  - Las vistas son representaciones virtuales de una o varias tablas, con acceso controlado y seguro.
  - Los índices dan velocidad al organizar los datos de campos específicos.
  - Los procedimientos automatizan tareas comunes.
  - Las funciones devuelven valores, para cálculos o para procesar información.
- **Vistas:** se crean, modifican y eliminan según las necesidades del negocio. Con DML (`INSERT`, `UPDATE`, `DELETE`, `SELECT`) se gestionan los datos a través de ellas de forma segura.
- **Usuarios:** se crean, modifican y eliminan accesos, y se asignan y retiran permisos, lo que refuerza la seguridad.
- **Roles:** agrupan permisos para asignarlos según las responsabilidades de cada usuario.
- **Perfiles:** son políticas de seguridad que limitan y gestionan el uso de recursos, como los tiempos de sesión y las cantidades de datos accesibles.
- **Normativa:** hay que cumplir el RGPD, la LOPD y el Estatuto de la Agencia de Protección de Datos. Ese enfoque integral mejora la gestión y la seguridad, asegura operaciones eficientes y alineadas con la ley, y protege tanto a la entidad como a las personas cuyos datos maneja.

**Cómo encajan las piezas** (esquema mío):

1. Creas el **usuario** (apartado 4).
2. Creas un **rol** y le das **permisos** (apartados 5 y 6).
3. Le asignas el rol al usuario (6.3).
4. Si hace falta, le pones **límites** de recursos con un perfil (8 y 9).
5. Todo dentro de lo que exige la **ley** (7).

Las **vistas** (2 y 3) te permiten enseñar solo una parte de los datos.

## 11. Glosario

| Término | Qué es |
|---|---|
| Funciones | Parecidas a los procedimientos almacenados, pero pueden devolver un valor |
| Índices | Aceleran las consultas ordenando los datos de un campo |
| Perfiles | Controlan los recursos del sistema que puede usar un usuario o grupo, con límites para evitar abusos |
| Procedimientos almacenados | Bloques de código SQL que realizan una tarea concreta |
| Roles | Conjunto de permisos asignados a usuarios para las funciones que requieren |
| Tablas | Estructura principal donde se guardan los datos, formada por filas y columnas |
| Vistas | Representación virtual de una tabla o de la combinación de varias |

## 12. Bibliografía

Son las fuentes que cita el PDF. No hace falta estudiarlas:

- Carrasco, R. A. (2017). *Bases de datos desde Chen hasta Codd con OODB*.
- López, J. (2020). *Administración de bases de datos con SQL Server*.
- Martínez, P. J. (2021). *Protección de datos personales*.
- Silva, L. (2019). *SQL para principiantes*.

## Notas mías (no están en el PDF)

- **Mezcla de SGBD:** el PDF solo etiqueta el SGBD en 6.3 (MySQL), 8 (Oracle y MySQL) y 9 (MySQL). Los ejemplos de 4 y 5 tienen forma de MySQL. Los del apartado 1 y el `ALTER ROLE ... ADD MEMBER` de 6.1 tienen pinta de SQL Server (variables con `@`, `ADD MEMBER`).
- **Erratas en 6.3:** en el original falta la comilla de apertura de la contraseña (`IDENTIFIED BY contraseña_segura';`) y el `GRANT` del paso 2 no lleva `;` final. Aquí están corregidos.
- **Apartado 5:** hay un «¹» tras «nombre del usuario» que remite a una nota al pie que no aparece en el documento.
- **LOPD:** en el resumen aparece «LOPD», y por el contexto se refiere a la Ley Orgánica 3/2018 del apartado 7. Fuera del PDF, a esa ley se la suele llamar LOPDGDD, y «LOPD» era el nombre de la ley anterior.
- **Apartados 8 y 9 en MySQL:** si pruebas esos comandos en tu laboratorio y alguno da error, puede ser cosa de la versión. Hoy lo habitual es fijar y quitar límites por usuario con `CREATE USER` o `ALTER USER ... WITH ...`, que es la pista del recuadro del apartado 8. Para estudiar, quédate con lo que dice el PDF.
- **Imágenes:** las ilustraciones del PDF (servidores, manos con código, etc.) son decorativas y no añaden contenido.
