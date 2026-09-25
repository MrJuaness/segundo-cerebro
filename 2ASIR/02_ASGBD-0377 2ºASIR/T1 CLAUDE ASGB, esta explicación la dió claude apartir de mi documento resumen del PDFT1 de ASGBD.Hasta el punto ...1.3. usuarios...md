Tranquilo, suena a chino por el vocabulario, pero las ideas de fondo son sencillas. Para todo el tema voy a usar una misma analogía: **una biblioteca**.

### Lo básico: BD vs. SGBD

- **Base de datos (BD)**: los libros ya colocados en sus estanterías. Es información organizada con algún criterio.
- **SGBD**: la biblioteca entera funcionando, con el edificio, los bibliotecarios, el catálogo, las normas y el carnet de socio. Es el **programa** que sirve para crear, usar y proteger bases de datos. MySQL es un SGBD.

Sin SGBD tendrías los libros amontonados en el suelo. El idioma con el que "hablas" con el SGBD es **SQL**.

Los **3 modelos** de BD son tres formas de organizar los datos por dentro:

- **Relacional**: tablas con filas y columnas conectadas entre sí. Es el de MySQL y el que vas a usar.
- **Jerárquico**: un árbol donde cada dato tiene un único "padre", como carpetas dentro de carpetas.
- **En red**: como el jerárquico, pero un dato puede tener varios "padres", como un mapa de metro con muchos cruces.

De que todo funcione se encarga el **DBA** (administrador de bases de datos). Instala y configura el SGBD, hace copias de seguridad, gestiona usuarios y permisos y vigila el rendimiento. Puede trabajar con **comandos** o con **interfaz gráfica**, y tus apuntes recomiendan comandos por ser más ágiles. También dicen que es clave saber acudir a fuentes oficiales, como el manual de MySQL (dev.mysql.com/doc).

### Las 10 funciones (1.1): lo que un SGBD tiene que saber hacer

1. **Crear la BD.** Montar las "estanterías": tablas, campos (columnas) y relaciones entre tablas. Cada campo tiene un _tipo de dato_ (número, texto, fecha...) para que en "edad" no puedas escribir "hola".
2. **Manipular datos.** El día a día con la información: `INSERT` añade, `UPDATE` modifica, `DELETE` borra y `SELECT` consulta.
3. **Integridad.** Que los datos sean correctos y coherentes. Se logra con claves. La **clave primaria** identifica cada fila de forma única, como un DNI. La **clave externa** apunta a la clave primaria de otra tabla, por ejemplo un pedido que guarda el DNI del cliente que lo hizo. Así no puede existir un pedido de un cliente que no existe, y el SGBD te frena solo si lo intentas.
4. **Seguridad de acceso.** Tiene dos pasos: _autenticación_ (¿quién eres? usuario y contraseña) y _autorización_ (¿qué te dejo hacer? permisos). Como en la biblioteca: el carnet dice quién eres y luego se decide a qué salas entras.
5. **Concurrencia y transacciones.** Muchos usuarios a la vez sin pisarse. Una **transacción** es un grupo de operaciones que se hace _entero o no se hace_. Ejemplo: transferir 100 € es quitárselos a Ana y sumárselos a Luis, y si falla a mitad el dinero no puede desaparecer. `COMMIT` confirma todo y `ROLLBACK` lo deshace todo. Se resume en **ACID**:
    - Atomicidad: todo o nada.
    - Consistencia: la BD siempre queda en un estado válido.
    - Aislamiento: unas transacciones no molestan a otras.
    - Durabilidad: lo confirmado queda guardado aunque se vaya la luz.
6. **Respaldo y recuperación.** El _backup_ es una copia de seguridad planificada. La _recuperación_ es usarla para volver al último estado bueno tras un fallo.
7. **Optimización.** Que todo vaya rápido. Un **índice** funciona como el índice de un libro: vas directo a la página en lugar de leerlo entero. El _ajuste de consultas_ es reescribir consultas pesadas para que gasten menos recursos.
8. **Diccionario de datos.** El catálogo de la biblioteca. Guarda los **metadatos**, que son "datos sobre los datos" (nombres de tablas, tipos, reglas...). En una foto, los datos son la imagen y los metadatos son la fecha, el tamaño y la cámara.
9. **Interfaz y herramientas.** Las formas de manejar el SGBD: **gráfica (GUI)**, con ventanas y botones (por ejemplo MySQL Workbench), o **consola (CLI)**, escribiendo comandos. Incluye herramientas para diseñar y escribir consultas.
10. **Escalabilidad y tolerancia a fallos.** _Escalabilidad_: seguir yendo bien aunque crezcan los datos y los usuarios. _Tolerancia a fallos_: seguir disponible aunque algo se rompa, gracias a la redundancia (tener copias de lo importante).

Para memorizarlas, agrúpalas en 4 ideas: **usar** (1, 2, 9), **proteger** (3, 4, 5, 6), **rendir y crecer** (7, 10) y **catalogar** (8).

### Los 8 componentes (1.2): las piezas por dentro

Para no confundirte: las **funciones** son lo que hace el SGBD y los **componentes** son las piezas que lo hacen posible.

1. **Motor de BD.** El corazón, el bibliotecario jefe. Tiene 3 trabajos: _interpretar_ lo que le pides, _traducirlo_ a algo ejecutable y _gestionar los recursos_ (memoria, disco...).
2. **Diccionario de datos.** El mismo catálogo de antes: una BD interna que solo guarda metadatos (tablas, tipos de campo, restricciones, índices).
3. **DML** (manipulación de datos). Trabaja con el _contenido_: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, sin tocar la estructura.
4. **DDL** (definición de datos). Trabaja con la _estructura_: `CREATE`, `ALTER`, `DROP`. Regla rápida: **DDL = las estanterías, DML = los libros que pones en ellas.** Ambos son "familias" de comandos de SQL.
5. **Gestor de transacciones.** Se asegura de que cada bloque de trabajo se ejecute aislado y de que lo confirmado quede guardado de forma permanente.
6. **Gestor de recuperación.** Si se va la luz o algo falla a medias, devuelve la BD a un estado coherente y repara lo que quedó a medio hacer.
7. **Gestor de concurrencia.** El árbitro: cuando cientos de usuarios quieren tocar el mismo registro a la vez, los coordina para que no choquen.
8. **Interfaz de usuario.** El mostrador de atención, por donde pides cosas y ves los resultados: GUI (gráfica) o CLI (consola).

No confundas el 5 con el 7. El gestor de transacciones vela por que cada trabajo sea "todo o nada", y el de concurrencia por que varios trabajos a la vez no se estorben.

### Los usuarios (1.3)

Hay dos formas de clasificarlos. Los tres primeros se definen por **qué permisos tienen** y los tres últimos por **cómo usan** la BD.

- **DBA.** El director de la biblioteca, con todas las llaves. Crea y borra bases de datos y tablas, da y quita permisos, optimiza, planifica la capacidad y define la seguridad. En MySQL, el equivalente aproximado es la cuenta `root`.
- **RESOURCE.** Un investigador con su propio despacho. Puede crear sus propios objetos (tablas, vistas...) pero no puede dar permisos a otros, y para usar objetos ajenos necesita autorización. Suelen ser desarrolladores. Una _vista_ es una consulta guardada que se usa como si fuera una tabla.
- **CONNECT.** El lector con carnet. Entra y usa solo lo que le dejen, y no crea objetos ni da permisos. Suelen ser usuarios finales.
- **Especializados.** Programan aplicaciones que usan la BD (para sí mismos o para otros) y conocen a fondo su estructura.
- **Casuales.** Lanzan consultas (suyas o hechas por otros) mediante un procesador de consultas, sin necesidad de conocer cómo está montada por dentro.
- **Esporádicos.** Entran de vez en cuando, pero con consultas complejas que exigen conocer mejor la estructura, como los analistas o científicos de datos.

Ojo: RESOURCE y CONNECT son roles clásicos de **Oracle**. En MySQL no existen con esos nombres, y allí se dan permisos concretos a cada usuario con `GRANT`. Los conceptos te sirven igual, pero que no te pille por sorpresa en la práctica.

### Para explicarlo con tus palabras

> Una base de datos es un conjunto de datos organizados y relacionados entre sí. Un SGBD, como MySQL, es el programa que permite crearla, usarla y protegerla. Para ello debe saber crear estructuras, manipular datos, mantenerlos correctos, controlar quién entra, gestionar transacciones y accesos simultáneos, hacer copias, ir rápido, guardar metadatos, ofrecer una interfaz y crecer sin romperse. Por dentro tiene piezas (motor, diccionario, DDL, DML y varios gestores), y lo usan perfiles muy distintos, desde el DBA, que lo controla todo, hasta el usuario que solo consulta.

Un detalle de tus apuntes: hay dos erratas. Donde pone "integridad **lúdica**" debería ser _lógica_, y en "fallos o lógicos" falta _físicos_.