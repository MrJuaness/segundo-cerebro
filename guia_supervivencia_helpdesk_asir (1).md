# 🛟 Guía de Supervivencia: de cero a Helpdesk Nivel 1 / Operador de Sistemas Junior

> **Para:** Juan · 2º ASIR · principiante que necesita repasar todo · Zorin OS · ASUS TUF A15 (Ryzen 7, 32 GB, 1 TB)
> **Objetivo:** tener la base mínima para optar a puestos y prácticas de soporte IT, **sin programar más de lo imprescindible**.
> **Fecha de partida:** 15/10/2026

---

## 0. Diagnóstico honesto (léelo primero)

**Lo que veo en tus capturas:**

1. **Compatibilidad: Conocimientos 58 % / Competencias 0 %.** Los conocimientos suben con las etiquetas que marques en tu perfil del portal; las **competencias a 0 %** casi seguro significan que tienes **el apartado de competencias vacío**. Rellenarlo cuesta 15 minutos y es la mejora más rápida que tienes hoy. (Compruébalo dentro del portal: es un dato del portal, no mío.)
2. **La mayoría de ofertas son presenciales en Madrid.** Tú estudias a distancia. Con el filtro de *Modalidad: remoto* solo aparecen **6** ofertas en total. Prácticas de soporte 100 % remotas son escasas: hay que **buscar en tres frentes a la vez** (ver sección 7).
3. **No todo lo que sale son prácticas.** *Técnico informático – Córdoba* y *Técnicos Post Venta (Alcorcón)* son **empleo a jornada completa**, no FCT. Lee cada oferta antes de inscribirte.
4. **Las fechas importan.** Las tarjetas muestran fechas desde el 20/10/2026 hasta 21/05/2027 (no está claro si son fecha de inicio o de cierre: míralo en cada oferta). Si alguna es fecha límite, **la de Inmho (20/10) vence en 5 días**.
5. **Tu ventaja real:** 4 años de hostelería = trato con el cliente bajo presión, turnos, resolver problemas en el momento. En un Helpdesk eso **pesa casi tanto como el técnico**. Úsalo en el CV y en la entrevista.

**Lo que NO vas a poder hacer:** aprenderlo todo en una semana. **Lo que sí puedes:** en **4 semanas** llegar a una entrevista de Helpdesk N1 sin hacer el ridículo, si estudias a diario con el laboratorio abierto.

---

## 1. Qué piden de verdad (mapa de habilidades)

Prioridad: 🔴 imprescindible · 🟠 muy valorado · 🟡 suma

| # | Habilidad | Prioridad | Qué te preguntarán |
|---|---|---|---|
| 1 | **Windows 10/11 a nivel usuario avanzado** (administrador de tareas, visor de eventos, actualizaciones, perfiles, impresoras, drivers) | 🔴 | "Un PC va lento / no arranca / no imprime, ¿qué haces?" |
| 2 | **Active Directory básico** (usuarios, grupos, OU, reset de contraseña, desbloqueo, unir equipo al dominio, GPO simple) | 🔴 | "¿Cómo desbloqueas a un usuario? ¿Qué es una OU?" |
| 3 | **Redes básicas** (IP, máscara, puerta de enlace, DNS, DHCP, ping/ipconfig/tracert/nslookup) | 🔴 | "Un usuario no tiene internet, ¿cómo diagnosticas?" |
| 4 | **Atención al usuario + tickets** (empatía, priorizar, escalar, documentar) | 🔴 | "Usuario enfadado, 3 tickets a la vez, ¿qué haces?" |
| 5 | **Microsoft 365 / Entra ID / Outlook / Teams** (buzones, licencias, MFA, restablecer acceso) | 🟠 | "Un usuario no recibe correos / perdió el móvil con el MFA" |
| 6 | **Herramientas de acceso remoto** (RDP, AnyDesk, Quick Assist, TeamViewer) | 🟠 | "¿Cómo ayudas a alguien que está en casa?" |
| 7 | **Linux básico** (terminal, permisos, servicios, logs, usuarios) | 🟠 | "¿Cómo ves si un servicio está caído?" |
| 8 | **Hardware y periféricos** (montaje, RAM, disco, BIOS, impresoras, cableado) | 🟠 | "El PC pita al encender / no detecta el disco" |
| 9 | **Seguridad básica** (contraseñas, MFA, phishing, copias de seguridad, antivirus) | 🟠 | "Un usuario hizo clic en un enlace sospechoso" |
| 10 | **Virtualización / laboratorio** (VirtualBox, snapshots) | 🟡 | "¿Tienes experiencia práctica?" → enseñas tu laboratorio |
| 11 | **Cloud básico** (qué es IaaS/PaaS/SaaS, Azure/AWS a nivel concepto) | 🟡 | "¿Qué es SaaS?" |
| 12 | **SQL y Python mínimos** | 🟡 | Solo para **aprobar el módulo**; en Helpdesk casi no lo piden |
| 13 | **Inglés técnico de lectura** | 🟠 | Documentación y tickets; imprescindible para Alemania/Suiza |

> **Regla:** domina 1-4 antes de tocar 7-13. Un candidato que sabe AD + redes + tickets le gana a uno que "sabe un poco de todo".

---

## 2. Tu laboratorio (tu portátil lo aguanta de sobra)

### 2.1 Máquinas virtuales recomendadas

Deja siempre al host (Zorin) **mínimo 4 hilos y 6–8 GB de RAM**.

| VM | SO | vCPU | RAM | Disco | Para qué |
|---|---|---|---|---|---|
| `DC01` | Windows Server 2022 (ISO evaluación de Microsoft) | 2 | 4 GB | 50 GB dinámico | Active Directory, DNS, DHCP |
| `PC01` | Windows 10/11 (ISO evaluación o la que tengas) | 2 | 4 GB | 50 GB dinámico | Cliente unido al dominio |
| `PC02` | Windows 10/11 (clonada de PC01) | 2 | 4 GB | 50 GB dinámico | Segundo cliente (opcional) |
| `LX01` | Ubuntu Server o Debian sin escritorio | 1 | 1–2 GB | 20 GB | Prácticas Linux, servicios |

Total ≈ 10–14 GB de RAM: cabe de sobra en tus 32 GB.

### 2.2 Red del laboratorio

- Usa una **red interna** de VirtualBox (por ejemplo `labnet`) para que las VM solo se vean entre sí.
- Añade un **segundo adaptador en NAT** a la VM que necesite Internet (actualizaciones, descargas).
- **No uses modo puente por Wi-Fi** (suele fallar). Si quieres puente, usa el cable `eno1`.
- Plan de direccionamiento sugerido:

| Equipo | IP | Nota |
|---|---|---|
| DC01 | `192.168.10.10/24` | IP **estática**, DNS = ella misma (`192.168.10.10`) |
| DHCP (en DC01) | rango `192.168.10.100–200` | Los clientes la reciben automáticamente |
| PC01/PC02 | DHCP | DNS lo reparte el DHCP |
| LX01 | `192.168.10.20/24` | Estática |

### 2.3 Reglas de oro del laboratorio

1. **Snapshot antes de cada práctica** y otro al terminar bien. Romper cosas es parte del aprendizaje; perder 3 horas, no.
2. Tras actualizar el kernel de Zorin, comprueba que VirtualBox arranca (si no carga, mira **Secure Boot / firma MOK**).
3. No mezcles VirtualBox y KVM a la vez: elige uno (recomendado: **VirtualBox** por simplicidad).
4. Si el instalador de Windows 11 se queja de TPM/Secure Boot, activa **EFI y TPM 2.0** en la configuración de la VM (VirtualBox 7+) o usa una ISO de Windows 10.
5. Copia las VM importantes (`.ova`) a un disco externo: tu portátil tiene **un solo disco**.

---

## 3. Plan de 4 semanas (mínimo viable)

**Ritmo:** 2 h/día entre semana (1 h teoría rápida + 1 h laboratorio) y 3–4 h el fin de semana. Si tienes menos tiempo, alarga las semanas, **pero no cambies el orden**.

### Semana 1 — Redes + Windows (los cimientos)
- [ ] Entender IP, máscara, puerta de enlace, DNS vs DHCP (explicado con ejemplos, no de memoria).
- [ ] Dominar `ping`, `ipconfig /all`, `ipconfig /release /renew`, `ipconfig /flushdns`, `nslookup`, `tracert`, `netstat -ano`.
- [ ] Crear `DC01` y `PC01` en VirtualBox y que se hagan ping.
- [ ] Windows: administrador de tareas, visor de eventos, servicios, reparar con `sfc /scannow`, modo seguro.
- ✅ **Entregable:** una hoja tuya con el "flujo de diagnóstico de red" (ver sección 5.3).

### Semana 2 — Active Directory (lo que más pesa)
- [ ] Instalar rol AD DS en `DC01` y promover a controlador de dominio (`lab.local`).
- [ ] Crear OUs (`Empleados`, `Equipos`), usuarios y grupos.
- [ ] Instalar rol DHCP y rol DNS; comprobar que PC01 recibe IP.
- [ ] Unir `PC01` al dominio, iniciar sesión con un usuario del dominio.
- [ ] Reset de contraseña, desbloqueo de cuenta, forzar cambio de contraseña en el próximo inicio.
- [ ] Una GPO sencilla (fondo de pantalla o bloqueo del Panel de control) y una carpeta compartida con permisos por grupo.
- ✅ **Entregable:** capturas de tu dominio funcionando + documento "cómo hice X" (tu portfolio).

### Semana 3 — Helpdesk real: tickets, remoto, M365, seguridad
- [ ] 20 tickets simulados resueltos (sección 5.4), con respuesta redactada al usuario.
- [ ] Practicar acceso remoto (RDP entre tus VM; Quick Assist/AnyDesk).
- [ ] Conceptos de Microsoft 365: licencias, buzones, MFA, restablecer acceso, grupos de distribución.
- [ ] Seguridad básica: phishing, contraseñas, copias de seguridad, qué hacer ante un incidente.
- [ ] Hardware: simulacro de diagnóstico (pitidos, disco no detectado, RAM, sobrecalentamiento).
- ✅ **Entregable:** 5 tickets documentados con formato profesional.

### Semana 4 — Linux mínimo, SQL/Python de supervivencia, entrevistas, CV
- [ ] Linux: `ls cd pwd cp mv rm mkdir cat less grep find chmod chown sudo systemctl journalctl ip ss df du ps top`.
- [ ] SQL: `SELECT / WHERE / ORDER BY / JOIN / INSERT / UPDATE / DELETE` (solo lo del examen).
- [ ] Python: variables, `if`, `for`, `while`, funciones, listas (solo lo del examen).
- [ ] CV de 1 página + carta + perfil del portal completo (competencias incluidas).
- [ ] 3 simulacros de entrevista (sección 6).
- ✅ **Entregable:** CV final + 10 inscripciones enviadas.

> **A partir de la semana 2 empieza a inscribirte en ofertas.** No esperes a "estar listo": las entrevistas son parte del entrenamiento.

---

## 4. Recursos mínimos (solo lo que merece la pena)

| Tema | Recurso | Nota |
|---|---|---|
| Laboratorio AD | **Microsoft Evaluation Center** (ISO de Windows Server) | Licencia de evaluación para pruebas; comprueba la duración al descargar |
| AD / Windows | **TryHackMe** (Windows Fundamentals, Active Directory Basics) | Gratis la parte básica, comprueba qué salas son de pago |
| Redes | **Cisco Skills for All** (Networking Basics) | Gratis con cuenta |
| Redes en español | **Píldoras Informáticas**, **NetworkChuck** (inglés) | YouTube |
| Linux | **linuxjourney.com**, **OverTheWire – Bandit** | Práctica de terminal |
| Linux interactivo | **Killercoda** | En el navegador, sin instalar |
| SQL | **SQLZoo** | Interactivo |
| Python | **W3Schools Python** | Referencia rápida |
| Microsoft 365 | **Microsoft Learn** (rutas de fundamentos) | Gratis |

**Certificaciones (después del primer empleo/prácticas, no antes):** CompTIA A+ es muy reconocida en soporte; **MS-900** y **AZ-900** son baratas y encajan con M365/Azure. Comprueba precios y requisitos vigentes en la web oficial antes de decidir; no pagues nada hasta tener el plan de estudio hecho.

---

## 5. Cheatsheets rápidas (imprímelas)

### 5.1 Comandos de red (Windows)

```text
ipconfig /all            → IP, máscara, puerta, DNS, ¿DHCP?
ipconfig /release        → liberar IP
ipconfig /renew          → pedir IP nueva
ipconfig /flushdns       → vaciar caché DNS
ping 127.0.0.1           → ¿funciona mi pila TCP/IP?
ping <puerta de enlace>  → ¿llego a mi red?
ping 8.8.8.8             → ¿salgo a Internet?
ping google.com          → ¿funciona el DNS?
nslookup google.com      → resolución DNS
tracert google.com       → por dónde va el tráfico
netstat -ano             → conexiones y puertos
```

### 5.2 Comandos útiles Windows / AD

```text
sfc /scannow                         → reparar archivos del sistema
chkdsk C: /f                         → revisar disco
gpupdate /force                      → aplicar GPO ya
gpresult /r                          → ver qué GPO se aplican
whoami /groups                       → a qué grupos pertenezco
net user <usuario> /domain           → info de usuario del dominio
services.msc / eventvwr / compmgmt.msc / devmgmt.msc / diskmgmt.msc
dsa.msc                              → "Usuarios y equipos de Active Directory"
```

### 5.3 Flujo de diagnóstico: "no tengo internet"

1. ¿Cable/Wi-Fi conectado? ¿Otros equipos tienen internet? (¿es de uno o de todos?)
2. `ipconfig /all` → ¿IP válida o `169.254.x.x` (sin DHCP)?
3. `ping` a la puerta de enlace → ¿falla? Problema local/switch/cable.
4. `ping 8.8.8.8` → ¿funciona pero `ping google.com` no? Problema de **DNS**.
5. `ipconfig /flushdns`, `ipconfig /release` + `/renew`.
6. ¿Proxy/VPN/firewall? ¿Cambió algo reciente?
7. Si no se resuelve → **escalar** con lo que has comprobado documentado.

### 5.4 Los 10 tickets más típicos de Helpdesk

1. Olvidó la contraseña / cuenta bloqueada.
2. No puede imprimir (cola atascada, impresora offline, driver).
3. No tiene internet / Wi-Fi.
4. El PC va lento.
5. No accede a una carpeta compartida (permisos).
6. Outlook no sincroniza / buzón lleno.
7. VPN / acceso remoto no conecta.
8. Pantalla azul / el equipo no arranca.
9. Correo sospechoso (phishing).
10. Solicitud de alta/baja de usuario y equipo nuevo.

### 5.5 Linux mínimo

```bash
pwd; ls -la; cd /var/log; cat; less; grep -i error archivo.log
sudo apt update && sudo apt upgrade
systemctl status ssh | systemctl restart ssh | systemctl enable ssh
journalctl -u ssh --since "1 hour ago"
ip -br a ; ip route ; ss -tulpn
df -h ; free -h ; top
chmod 640 archivo ; chown usuario:grupo archivo
sudo adduser nombre ; sudo usermod -aG grupo nombre
```
Permisos: `r=4 w=2 x=1`. `chmod 755` = dueño todo, grupo y resto leer+ejecutar.

### 5.6 Subnetting mínimo

| CIDR | Máscara | Hosts útiles |
|---|---|---|
| /24 | 255.255.255.0 | 254 |
| /25 | 255.255.255.128 | 126 |
| /26 | 255.255.255.192 | 62 |
| /27 | 255.255.255.224 | 30 |
| /28 | 255.255.255.240 | 14 |
| /30 | 255.255.255.252 | 2 |

Rangos privados: `10.0.0.0/8` · `172.16.0.0/12` · `192.168.0.0/16`. `169.254.x.x` = APIPA (no hay DHCP).

---

## 6. 🎓 PROMPTS: tu "profesor ingeniero maestro"

> **Cómo usarlos:** copia el **Prompt 0** al inicio de un chat nuevo y después pega el prompt de la habilidad que toque. Pega cada prompt **completo** (están sin recortar). Si algo no lo entiendes, escribe: *"Explícamelo con una analogía de hostelería"*.

### Prompt 0 — Configuración del profesor (pégalo siempre primero)

```text
Actúa como un profesor ingeniero de sistemas senior con 15 años de experiencia
en soporte IT y administración de sistemas, que prepara a un alumno de 2º de
ASIR para su primer empleo en Helpdesk Nivel 1 / Operador de Sistemas Junior.

Mi perfil: soy principiante, vengo de 4 años de hostelería, he olvidado casi
todo lo estudiado y quiero lo MÍNIMO Y DIRECTO para el mundo real. Mi equipo
es un portátil con Zorin OS (Linux), Ryzen 7, 32 GB de RAM y VirtualBox para
los laboratorios.

Reglas para todas tus respuestas:
1. Sé directo y honesto. Si me equivoco, corrígeme sin suavizarlo.
2. Explica con lenguaje sencillo y una analogía cuando haga falta.
3. Estructura cada lección: (a) qué es en 2 frases, (b) por qué lo piden en
   el trabajo, (c) pasos prácticos en mi laboratorio, (d) errores típicos,
   (e) 5 preguntas de entrevista con respuesta modelo corta.
4. Dame comandos exactos cuando proceda y explica qué hace cada uno.
5. No avances a un tema nuevo hasta que yo diga "listo". Después de cada tema
   hazme 3 preguntas de comprobación y corrígelas.
6. Si algo es opcional o no se pregunta en entrevistas de Helpdesk, dímelo
   para que no pierda tiempo.
7. Responde siempre en español; los términos técnicos en inglés ponlos
   entre paréntesis la primera vez.

Confírmame que has entendido y pregúntame cuántas horas al día puedo estudiar.
```

### Prompt 1 — Redes básicas

```text
Enséñame redes básicas para un técnico de Helpdesk, partiendo de cero.
Cubre, en este orden: IP, máscara de subred, puerta de enlace, DNS, DHCP,
diferencia entre IP pública y privada, qué es APIPA (169.254.x.x), puertos
más comunes (22, 53, 80, 443, 3389, 445) y la diferencia entre switch,
router y punto de acceso.

Después:
1. Dame un laboratorio paso a paso en VirtualBox con una red interna,
   un servidor con IP estática (192.168.10.10/24) y un cliente que reciba
   IP por DHCP.
2. Enséñame a usar ping, ipconfig /all, /release, /renew, /flushdns,
   nslookup, tracert y netstat -ano, y qué significa cada resultado.
3. Dame 8 problemas de red "rotos a propósito" para que yo los diagnostique
   siguiendo un flujo ordenado. Dame las pistas de una en una, sin darme la
   solución hasta que yo diga mi diagnóstico.
4. Hazme el examen final: 10 preguntas de entrevista sobre redes.
```

### Prompt 2 — Windows 10/11 como técnico

```text
Quiero ser el técnico al que llama el usuario cuando su Windows 10/11 falla.
Dame una guía práctica de las 15 herramientas y acciones imprescindibles:
administrador de tareas, visor de eventos, servicios, msconfig, modo seguro,
puntos de restauración, sfc /scannow, DISM, chkdsk, Windows Update (errores
típicos), perfiles de usuario corruptos, drivers, impresoras (cola atascada),
almacenamiento lleno y arranque lento.

Para cada una: cuándo usarla, cómo ejecutarla y un ejemplo de ticket real.
Termina con 10 tickets de Windows para resolver, tipo "caso clínico": tú me
describes los síntomas, yo propongo el diagnóstico paso a paso y tú me
corriges.
```

### Prompt 3 — Active Directory (el más importante)

```text
Actúa como administrador de sistemas senior y guíame para montar Active
Directory desde cero en VirtualBox, sin saltarte nada, con Windows Server
2022 (DC01) y un cliente Windows 10/11 (PC01), en red interna 192.168.10.0/24.

Quiero los pasos EXACTOS en este orden:
1. Instalar Windows Server, ponerle IP estática y nombre DC01.
2. Instalar AD DS y promover a controlador de dominio nuevo bosque lab.local.
3. Instalar y configurar DNS y DHCP (ámbito 192.168.10.100-200).
4. Crear OUs (Empleados, Equipos), usuarios y grupos con buenas prácticas
   de nombres.
5. Unir PC01 al dominio e iniciar sesión con un usuario del dominio.
6. Tareas diarias de Helpdesk: resetear contraseña, desbloquear cuenta,
   forzar cambio de contraseña, deshabilitar un usuario, mover un equipo
   de OU.
7. Una GPO simple (por ejemplo, fondo de pantalla) y cómo comprobarla con
   gpupdate /force y gpresult /r.
8. Carpeta compartida con permisos NTFS y de recurso compartido por grupo.

Explícame para cada paso POR QUÉ se hace. Después genera 10 preguntas de
entrevista sobre AD con respuesta modelo, y 5 averías típicas (por ejemplo,
"no puedo unir el equipo al dominio" -> suele ser DNS) para que yo las
diagnostique.
```

### Prompt 4 — Atención al usuario y tickets (tu ventaja)

```text
Actúa como mi jefe en un Helpdesk de Nivel 1 en una empresa mediana.
Vengo de la hostelería y quiero aprovechar esa experiencia de trato con
el cliente en un puesto de soporte IT.

Enséñame:
1. El ciclo de vida de un ticket (registrar, clasificar, priorizar, resolver,
   escalar, cerrar) y la diferencia entre incidencia y petición.
2. Cómo priorizar con urgencia e impacto (SLA, prioridades P1-P4).
3. Cuándo escalar a Nivel 2 y cómo redactar la nota de escalado.
4. Cómo hablar con un usuario enfadado o con poco conocimiento técnico.
5. Plantillas de respuesta: saludo, confirmación del problema, acción,
   cierre.

Después simula 10 tickets reales, de uno en uno: tú haces de usuario con
un problema (con poca información, como pasa en la vida real), yo hago
preguntas y propongo solución, y tú evalúas mi respuesta con una nota del
1 al 10 y qué haría un técnico senior.
```

### Prompt 5 — Microsoft 365, Entra ID y acceso remoto

```text
Quiero lo mínimo de Microsoft 365 que necesita un técnico de Helpdesk.
Explícame, con un enfoque práctico: qué es un tenant, licencias, buzones
de Exchange Online, Teams, OneDrive/SharePoint, Entra ID (antiguo Azure AD),
MFA y restablecimiento de acceso.

Después dame 10 tickets típicos (no recibe correos, buzón lleno, perdió el
móvil del MFA, quiere acceso a una carpeta de SharePoint, etc.) y cómo se
resuelven. Añade un apartado de acceso remoto: RDP, Quick Assist, AnyDesk,
y buenas prácticas para ayudar a un usuario en remoto de forma segura.
Marca claramente qué cosas son solo de administrador y cuáles hace el
Nivel 1.
```

### Prompt 6 — Linux mínimo (Zorin OS)

```text
Soy usuario de Zorin OS y quiero lo mínimo de Linux para trabajar en
soporte y sistemas. Dame, ordenados por importancia, los 30 comandos
imprescindibles agrupados en: navegación y ficheros, permisos y usuarios,
procesos y servicios (systemctl, journalctl), red (ip, ss, ping), disco y
memoria (df, du, free), y búsqueda en logs (grep, tail -f).

Para cada comando: qué hace, un ejemplo real y el error típico del principiante.
Después prepárame un laboratorio con una VM Debian/Ubuntu Server donde yo
instale y administre SSH y Apache, cree usuarios y grupos, cambie permisos,
y consulte logs para encontrar un fallo que tú provoques. Termina con 10
preguntas de entrevista sobre Linux con respuesta modelo.
```

### Prompt 7 — Hardware, seguridad básica y copias de seguridad

```text
Dame una guía de supervivencia para un técnico de soporte sobre:
1. Hardware: componentes de un PC y portátil, qué síntomas apuntan a RAM,
   disco, fuente o sobrecalentamiento, pitidos de BIOS, y cómo diagnosticar.
2. Seguridad básica: phishing (cómo reconocerlo y qué hacer), contraseñas
   y MFA, antivirus/EDR a nivel conceptual, y qué hacer si un usuario hizo
   clic en un enlace sospechoso (protocolo paso a paso).
3. Copias de seguridad: regla 3-2-1, completa vs incremental vs diferencial,
   y cómo restaurar un fichero borrado.

Después hazme 10 preguntas tipo test con explicación de la respuesta.
```

### Prompt 8 — SQL y Python de supervivencia (solo para aprobar)

```text
Soy estudiante de ASIR, no quiero ser desarrollador, pero necesito aprobar
Bases de Datos y Python. Dame solo lo que cae en un examen de ASIR:

SQL: SELECT, WHERE, ORDER BY, LIMIT, JOIN (INNER y LEFT), GROUP BY con
COUNT/SUM, INSERT, UPDATE, DELETE y CREATE TABLE. Explica claves primarias
y foráneas con un ejemplo.
Python: variables, tipos, input/print, if/elif/else, for, while, listas,
diccionarios y funciones.

Para cada bloque: explicación corta, 5 ejercicios de dificultad creciente
(sin soluciones hasta que yo lo intente) y corrección línea por línea de lo
que yo escriba. Señala qué errores son los más típicos de los exámenes.
```

### Prompt 9 — Simulador de entrevista (úsalo 3 veces)

```text
Actúa como un entrevistador técnico de una empresa que contrata Técnicos
de Soporte Nivel 1. Voy a entrevistarme para un puesto de Helpdesk. Mi
perfil: 2º de ASIR, 4 años en hostelería, laboratorio propio de Active
Directory en VirtualBox.

Haz la entrevista de una en una: 3 preguntas de motivación y trayectoria,
7 técnicas (redes, Windows, AD, Linux básico), 3 de casos prácticos
y 2 de comportamiento (conflicto con un usuario, trabajar bajo presión).
Después de cada respuesta mía, dame: nota 1-10, qué ha estado bien, qué falta
y una versión mejorada de mi respuesta. No me regales buenas notas: sé
exigente y realista. Al final, dame un informe con mis 3 puntos débiles
y qué estudiar esta semana.
```

### Prompt 10 — CV, carta y perfil del portal

```text
Eres reclutador técnico especializado en perfiles junior de IT en España.
Voy a pegarte mi CV actual y una oferta de empleo/prácticas. Haz lo
siguiente:
1. Dime con franqueza qué le falta a mi CV para un Helpdesk Nivel 1.
2. Reescríbelo en una página: perfil profesional de 3 líneas, formación,
   proyectos de laboratorio (AD, redes, Linux), habilidades técnicas y
   habilidades de atención al cliente traducidas desde mi experiencia en
   hostelería (cada una con un ejemplo medible).
3. Extrae las palabras clave de la oferta y dime cuáles me faltan.
4. Escríbeme una carta de presentación de 120 palabras, sin florituras.
5. Dime qué competencias debería rellenar en el perfil del portal de ofertas
   para subir mi compatibilidad.
```

### Prompt 11 — Revisión semanal (anti-olvido)

```text
Hazme una revisión de lo que he estudiado esta semana: [escribe aquí los
temas]. Genera 15 preguntas de repaso espaciado (mezcla de temas, de lo
más fácil a lo más difícil), una a una, y al final dime qué debo repetir
mañana. Si fallo una pregunta, vuelve a preguntármela de otra forma dentro
de 5 preguntas.
```

### Prompt 12 — Documenta tu laboratorio (tu portfolio)

```text
Voy a pegarte mis notas desordenadas de un laboratorio que he hecho.
Conviértelas en un documento profesional de portfolio en Markdown con:
objetivo, esquema de red, requisitos, pasos numerados, capturas
que debo hacer (indícame cuáles), problemas encontrados y cómo los resolví,
y conclusiones. Tono claro y técnico. Añade al final un resumen de 3 líneas
para poner en el CV y en LinkedIn.
```

---

## 7. Cómo atacar las ofertas (estrategia de búsqueda)

**En el portal de ofertas:**
1. Completa **competencias** (hoy tienes 0 %) y añade en conocimientos todo lo que realmente sabes: Windows, Active Directory, Redes, Soporte a usuarios finales, Linux.
2. Prueba el filtro *"Ofertas que cumplen con algún filtro"* (más resultados) y luego afina. Mira solo **remoto (6)** como primera pasada.
3. Inscríbete en todo lo que sea realista para ti: no esperes a llegar al 100 % de compatibilidad.

**Fuera del portal (la mayoría de tus opciones reales):**
- **Habla con el tutor/coordinador de FCT de tu centro**: suelen tener convenios con empresas, incluidas las que aceptan prácticas remotas o híbridas. Pregunta literalmente: *"¿qué empresas tienen convenio con prácticas remotas o en Castilla y León?"*
- **Busca en tu zona** (Salamanca y alrededores): ayuntamientos, diputación, hospitales, gestorías, colegios, concesionarios, pymes con infraestructura propia. Ahí el soporte IT es real y a veces nadie lo cubre.
- **Portales de empleo:** InfoJobs, LinkedIn, Indeed, Tecnoempleo. Palabras clave: *técnico soporte, helpdesk, service desk, técnico microinformático, soporte usuarios, operador de sistemas junior, prácticas ASIR*.
- Si Madrid compensa (mejores oportunidades), valora **una estancia temporal o prácticas híbridas**; hazlo solo si tienes alojamiento resuelto, porque las prácticas FCT normalmente no se pagan.

**Para ofertas en Alemania/Suiza:** no pienses en ello hasta tener el primer puesto en España y un nivel de inglés (y alemán) defendible. Es un objetivo a 1–2 años, no al mes que viene.

---

## 8. Checklist "estoy listo para aplicar"

- [ ] Puedo explicar con mis palabras qué es IP, máscara, puerta de enlace, DNS y DHCP.
- [ ] Diagnostico "no tengo internet" con el flujo de la sección 5.3.
- [ ] He montado un dominio AD con DHCP y DNS, y he unido un cliente.
- [ ] Sé resetear contraseña, desbloquear cuenta y crear usuario/grupo/OU.
- [ ] Tengo 5 prácticas documentadas (mi portfolio).
- [ ] He hecho 3 simulacros de entrevista.
- [ ] CV de 1 página, carta tipo y perfil del portal con competencias rellenas.
- [ ] Tengo mi respuesta a "¿por qué dejas la hostelería?" (breve, positiva, honesta).
- [ ] Mínimo 10 candidaturas enviadas.

---

## 9. Respuesta modelo: "¿Por qué hostelería → IT?"

> *"En hostelería aprendí a atender al cliente bajo presión, a priorizar cuando todo es urgente y a resolver problemas en el momento. Siempre me ha gustado la informática y he cursado ASIR, donde he montado mi propio laboratorio con Active Directory y redes. Quiero combinar el trato con las personas con lo técnico: un puesto de soporte es el lugar donde mejor encajo."*

Adáptala solo si es verdad. Si no has montado el laboratorio todavía, **primero hazlo** y luego la dices.

---

## 10. Reglas finales

1. **Constancia sobre intensidad:** 2 h al día durante 4 semanas gana a 12 h un domingo.
2. **Laboratorio abierto siempre:** leer no es aprender; romper y arreglar sí.
3. **Documenta todo:** lo que no está escrito no existe para el reclutador.
4. **Empieza a aplicar en la semana 2:** las entrevistas enseñan más que cualquier curso.
5. **Sé honesto en la entrevista:** "no lo sé, pero así lo averiguaría" es una buena respuesta; mentir no.
6. **Cuida tu portátil:** snapshots, copias en disco externo y cargador conectado en los laboratorios.

---

*Guía orientativa: precios, certificaciones, duración de licencias de evaluación y condiciones de los portales cámbialas siempre contra la fuente oficial.*
