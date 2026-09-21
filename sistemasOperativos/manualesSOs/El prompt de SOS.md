## Lo que le pedimos a Gemini: 
- soy estudiante de 2º de ASIR, cómo le puedo pedir a claude que explique de forma fácil de entender y aprender este tema 1 , sin olvidarse de nada, el objetivo es dominar de forma super fácil lo que tengo que saber hacer y aprender , necesito una explicación de todo el tema sin olvidarse de nada haciendo que lo difícil sea fácil, un resumen del cual le vamos a pedir preguntas de ese resumen en formato .PDF o que me lo cree en .DOCX el que mejor sea para las IAs, el objetivo es conseguir que lo importante de ese PDF que te he pasado lo explique todo en menos páginas sin olvidarse ni dejarse nada, todo en formato super estrecho, letra como mucho tamaño 10.5, estilo chuleta examen, pero que tenga sentido , QUE NO SEAN FRASES O PÁRRAFOS SUELTOS, usando las palabras técnicas que piden para aprender de la forma correcta y traducido para que sea todo entendible , saber qué es cada cosa
- ### lo que responde:
	- Actúa como un Profesor Senior del Grado Superior de ASIR (Administración de Sistemas Informáticos en Red). Tu objetivo es explicarme el "Tema 1: Administración de servidores de directorio" del módulo de Administración de Sistemas Operativos (ASO) sin omitir ningún concepto del temario oficial.
	- Instrucciones de formato y contenido:
		- 1.Explica todo el tema con lenguaje técnico pero perfectamente traducido y fácil de comprender, conectando los párrafos de forma lógica (sin frases o viñetas sueltas sin contexto).
		- 2.Agrupa la información en estilo "chuleta de examen técnica": denso, al grano, directo y sin paja, pero 100% explicativo.
		- 3.Para cada término técnico (como LDAP, DN, RDN, Schema, GPO, FSMO, Kerberos, Trust, DC), incluye su definición formal y una traducción/analogía fácil para recordar en el examen.
		- 4.Asegúrate de cubrir todos los puntos:
			- Definición y elementos del servicio de directorio (BD, Esquema, Objetos, Atributos, DN/RDN, Interfaz).
			- Protocolo LDAP (modelo cliente-servidor, operaciones Bind/Search/Add/Modify/Delete, seguridad SSL/TLS, puertos 389 y 636).
			- Esquema del servicio de directorio (ObjectClasses, atributos MUST/MAY, reglas y restricciones).
			- Funciones del dominio (autenticación vs autorización, GPO, centralización, dependencia crítica de DNS, replicación).
			- Controladores de Dominio (DC) (roles, BD ntds.dit, Kerberos, FSMO, mantenimiento y copias de seguridad).
			- Pasos para la instalación, configuración, personalización y creación de dominios (planificación, OUs, unirse al dominio).
			- Objetos del dominio (Usuarios globales, Grupos de seguridad/distribución, Ámbitos local/global/universal, Equipos, OUs).
			- Herramientas gráficas (MMC: dsa.msc, dssite.msc, domain.msc; ADAC y papelera de reciclaje; Apache Directory Studio; phpLDAPadmin).
			- Filtros de búsqueda LDAP (operadores &, |, ! y sintaxis con ejemplos prácticos).
			- Integración con correo (Exchange), SGBD, ERP y Nube (Microsoft Entra ID / Azure AD).
			- Relaciones de confianza (Unidireccional, Bidireccional, Transitiva, Externa y de Bosque).
		- 5. Tras la explicación, genera un banco de 15 preguntas de examen (tipo test con justificación y preguntas de supuestos prácticos con soluciones) para poner a prueba mi aprendizaje.

## Lo que le pedimos a CLAUDE PROMPT:
Actúa como un Profesor Senior del Grado Superior de ASIR (Administración de Sistemas Informáticos en Red). Tu objetivo es explicarme el "Tema 1: Administración de servidores de directorio" del módulo de Administración de Sistemas Operativos (ASO) sin omitir ningún concepto del temario oficial.

Instrucciones de formato y contenido:
1. Explica todo el tema con lenguaje técnico pero perfectamente traducido y fácil de comprender, conectando los párrafos de forma lógica (sin frases o viñetas sueltas sin contexto).
2. Agrupa la información en estilo "chuleta de examen técnica": denso, al grano, directo y sin paja, pero 100% explicativo.
3. Para cada término técnico (como LDAP, DN, RDN, Schema, GPO, FSMO, Kerberos, Trust, DC), incluye su definición formal y una traducción/analogía fácil para recordar en el examen.
4. Asegúrate de cubrir todos los puntos:
   - Definición y elementos del servicio de directorio (BD, Esquema, Objetos, Atributos, DN/RDN, Interfaz).
   - Protocolo LDAP (modelo cliente-servidor, operaciones Bind/Search/Add/Modify/Delete, seguridad SSL/TLS, puertos 389 y 636).
   - Esquema del servicio de directorio (ObjectClasses, atributos MUST/MAY, reglas y restricciones).
   - Funciones del dominio (autenticación vs autorización, GPO, centralización, dependencia crítica de DNS, replicación).
   - Controladores de Dominio (DC) (roles, BD ntds.dit, Kerberos, FSMO, mantenimiento y copias de seguridad).
   - Pasos para la instalación, configuración, personalización y creación de dominios (planificación, OUs, unirse al dominio).
   - Objetos del dominio (Usuarios globales, Grupos de seguridad/distribución, Ámbitos local/global/universal, Equipos, OUs).
   - Herramientas gráficas (MMC: dsa.msc, dssite.msc, domain.msc; ADAC y papelera de reciclaje; Apache Directory Studio; phpLDAPadmin).
   - Filtros de búsqueda LDAP (operadores &, |, ! y sintaxis con ejemplos prácticos).
   - Integración con correo (Exchange), SGBD, ERP y Nube (Microsoft Entra ID / Azure AD).
   - Relaciones de confianza (Unidireccional, Bidireccional, Transitiva, Externa y de Bosque).
5. Tras la explicación, genera un banco de 15 preguntas de examen (tipo test con justificación y preguntas de supuestos prácticos con soluciones) para poner a prueba mi aprendizaje.