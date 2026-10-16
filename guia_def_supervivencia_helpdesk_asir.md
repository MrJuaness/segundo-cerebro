# 🛟 Guía de Supervivencia: de ASIR a Helpdesk N1 / Operador de Sistemas Junior

> **Para:** alumno de 2º de ASIR, principiante y oxidado, que necesita entrar al mercado laboral ya.
> **Fecha:** 16 de octubre de 2026 · **Equipo:** ASUS TUF A15 (Ryzen 7 7435HS · 32 GB · NVMe 1 TB) con Zorin OS
> **Complementa a:** `plan_de_supervivencia_express_para_helpdesk_y_asir.md` y `resumen_portatil_ASIR.md`. Esta guía es el plan de acción; no repite lo que ya tienes en esos documentos.
> **Cómo se usa:** lee la sección 0 → haz la sección 1 **hoy** → monta el laboratorio (sección 3) → sigue el plan de 14 días (sección 4). Los prompts están en la sección 14.

## Índice

0. Lee esto primero
1. Lo que dice el mercado (tus capturas)
2. Mapa de habilidades
3. Tu laboratorio
4. Plan de 14 días (y ruta ultra-express de 5)
5. Módulo A · Active Directory y Windows Server
6. Módulo B · Redes y diagnóstico
7. Módulo C · Windows cliente: los 12 tickets
8. Módulo D · Microsoft 365, SaaS y asistencia remota
9. Módulo E · Linux
10. Módulo F · SQL, Python y PowerShell (mínimo)
11. Módulo G · Hardware 101
12. Módulo H · Tickets, ITIL mínimo y trato al usuario
13. Portafolio, CV y entrevistas
14. Suite de prompts
15. Recursos y fuentes
16. Checklists finales

---

## 0. Lee esto primero (3 minutos)

### El objetivo realista

No vas a salir sabiendo "de todo". Vas a salir **sabiendo hacer, explicar y documentar** diez cosas que se repiten en casi todas las ofertas de Helpdesk N1, prácticas FCT/Dual de ASIR y operador de sistemas junior:

1. Crear, desbloquear y resetear usuarios en **Active Directory** y unir equipos al dominio.
2. Diagnosticar un problema de **red** con la "escalera del ping" y media docena de comandos.
3. Resolver los **12 tickets** más frecuentes de usuario (sesión, red, impresora, carpetas, lentitud, correo, VPN…).
4. Moverte con soltura en **Windows 10/11** (servicios, visor de eventos, herramientas de administración).
5. Defenderte en **Linux** por terminal (navegar, permisos, servicios, logs, SSH).
6. Escribir **consultas SQL** básicas y saber hacer una copia de seguridad.
7. Entender **Microsoft 365 y SaaS** a nivel de administrador básico.
8. Trabajar con **tickets**: prioridad, escalado, documentación.
9. **Documentar** lo que haces (eso es tu portafolio).
10. **Comunicarte** con un usuario enfadado sin perder la calma.

### Las 6 reglas del maestro

| # | Regla | Por qué |
|---|---|---|
| 1 | **Practica, no leas.** Cada concepto = una práctica en tu laboratorio. | En la entrevista te preguntan "¿lo has hecho?", no "¿lo has leído?". |
| 2 | **Windows primero, Linux después.** | El soporte de oficina es casi todo Windows + Active Directory + Microsoft 365. Zorin es tu *anfitrión*; tu práctica de soporte la harás dentro de las máquinas virtuales. |
| 3 | **Rompe y arregla.** Provoca averías a propósito y diagnostícalas. | Es la forma más rápida de pensar como técnico. |
| 4 | **Documenta como si fuera un ticket.** | Cada práctica documentada = una línea de CV y una respuesta de entrevista. |
| 5 | **Inscríbete ya, estudia mientras te evalúan.** | Los procesos tardan semanas. El plan de 14 días corre en paralelo a tus candidaturas. |
| 6 | **La IA es tu profesor, no tu cerebro.** | Verifica siempre en tu pantalla. Si no coincide con lo que ves, pega el error y pide que corrija. |

### Qué NO estudiar ahora (te quita tiempo y el nivel 1 no lo pide)

Docker/Kubernetes · Proxmox/ESXi anidados · GNS3 avanzado · OSPF/BGP · IPv6 en profundidad · Vagrant · GPU passthrough · ciberseguridad ofensiva · programación más allá del mínimo para aprobar · certificaciones de pago (antes de tener prácticas o trabajo). Tu portátil aguanta todo eso, pero **no es lo que piden las ofertas que has capturado**.

---

## 1. Lo que dice el mercado 

### 1.1 Qué se ve en tus 24 ofertas

- **6 de las 8 tarjetas visibles son prácticas** (FCT/Dual) para ASIR/SMR. Las otras dos parecen empleo: un *Técnico informático* (telecomunicaciones, Córdoba) y *Técnicos Post Venta* (Alcorcón). **Tu puerta de entrada más realista es la FCT/Dual**, y de ahí al contrato.
- Etiquetas de "Conocimientos" que más se repiten (el número entre paréntesis es el nº de ofertas con esa etiqueta; compruébalo en el enlace "¿Qué significan los números?"): **Sistemas operativos (5)**, **Soporte a usuarios finales (4)**, **Administración de bases de datos (4)**, **Informática (3)**, **SaaS (3)**. Es decir: Windows/Linux, soporte, **SQL** y **Microsoft 365/SaaS** no son opcionales.
- Ubicación: dominan **Madrid (13)** y **remoto (6)**.
- Tu compatibilidad de *Conocimientos* ronda el **55–58 %** y la de *Competencias* es **0 %** en todas las tarjetas (casi seguro porque no has rellenado esa parte del perfil o no coincide con lo que piden).

| Empresa | Puesto | Tipo / jornada | Zona | Prepárate sobre todo en… |
|---|---|---|---|---|
| DIUSFRAMI SA | Administración de Sistemas Informáticos en Red (estudiantes ASIR) | Prácticas · media jornada | Madrid | AD / Windows Server, Linux básico, redes |
| Plus Ibérica Distribución | Prácticas FCT/Dual (perfiles ASIR / DAM / DAW) | Prácticas · media jornada | Madrid (San Blas) | Soporte, Windows, SQL básico |
| Inmho Gestión de la Propiedad | Prácticas Dpto. de Tecnología (ASIR / SMR) | Prácticas · media jornada | Las Rozas | Soporte a usuarios, hardware, Windows 10/11 |
| Eurofirms | Prácticas FP ASIR · Soporte / Operaciones IT | Prácticas · jornada completa | Madrid (Tetuán) | Tickets, AD, atención al usuario |
| EDAS Ingenieros | Técnico informático (dpto. de telecomunicaciones) | Empleo (probable) · completa | Córdoba | Redes, cableado, soporte |
| Hispa Software Systems | Prácticas Dpto. IT | Prácticas · jornada completa | Madrid (Chamartín) | Soporte IT general (el detalle no se ve) |
| Fundación Virgen de la Almudena | Prácticas de Redes | Prácticas · jornada completa | Madrid (Villa de Vallecas) | IP, DHCP/DNS, switching básico |
| Korporate Technologies | Técnicos Post Venta (SPV) | Empleo (probable) · completa | Alcorcón | Hardware, atención al cliente, soporte en campo |

> La última columna es una **inferencia** a partir de lo visible en la captura. Abre cada oferta, copia sus requisitos literales y pásalos por el **Prompt 14**.

### 1.2 Contexto del mercado (verificado en octubre de 2026)

- **Windows 10** perdió el soporte estándar el 14/10/2025, pero el programa de actualizaciones de seguridad extendidas (ESU) sigue: en consumo se amplió hasta el 12/10/2027 y en empresas puede llegar hasta 3 años (octubre de 2028). Resultado: vas a ver **Windows 10 y 11 mezclados** y muchas migraciones, que son trabajo de helpdesk.
- **Windows Server 2016** termina su soporte el 12/01/2027: migraciones a Server 2022/2025 (trabajo de operador de sistemas).
- Active Directory sigue siendo muy habitual y cada vez va acompañado de **Microsoft 365 / Entra ID** (entorno híbrido). Por eso la sección 8 existe.

### 1.3 Acciones de hoy (30–45 min, antes de estudiar nada)

1. **Rellena "Competencias" en tu perfil** (por ejemplo: comunicación, resolución de problemas, atención al cliente, trabajo en equipo, aprendizaje continuo, organización). Es la mejora más rápida de tu porcentaje.
2. **Completa "Conocimientos"** solo con lo que puedas demostrar en un laboratorio. Ve añadiendo etiquetas según terminas módulos: *Active Directory, Windows Server, Windows 10/11, Linux, redes TCP/IP, DHCP/DNS, soporte técnico, SQL, virtualización, Microsoft 365*.
3. **Habla con tu tutor de FCT**: en FCT/Dual el convenio con la empresa normalmente lo firma el centro. Pregúntale si ya existe con esas empresas, o si puede firmarlo, qué jornada (media o completa) encaja con tu calendario y **si el centro acepta FCT en remoto** (mira 1.4).
4. **Inscríbete ya en 3–5 ofertas** con mejor encaje. Las tarjetas muestran fechas (20/10, 02/11, 03/11, 24/11 y 01/12 de 2026, y 21/05/2027): confirma en cada oferta si son fechas límite o de inicio. Si son límites, la de Inmho (20/10) es la primera en vencer (martes 20/10).
5. **Crea la carpeta de trabajo** `~/ASIR-Lab` con subcarpetas `isos/`, `vms/`, `docs/` y `capturas/`.
6. **Haz el Prompt 13** (CV) en su versión inicial. Lo mejorarás cuando tengas el laboratorio documentado.

### 1.4 Si necesitas trabajar a distancia (tus ofertas son de Madrid)

Una de tus capturas lleva la nota de que las ofertas son de Madrid y tú necesitas remoto. Cuatro cosas que te sirven:

**a) Cómo filtrar de verdad.** En tu captura estaban marcadas varias casillas a la vez (Informática, Soporte a usuarios finales, dos áreas laborales y *Modalidad: remoto*) y el botón activo era *Ofertas que cumplen con algún filtro*. Por su nombre, devuelve las ofertas que cumplan **cualquiera** de ellas, y por eso salen tantas de Madrid: ninguna de las 8 tarjetas visibles lleva etiqueta de remoto, todas muestran una localidad. Para ver solo las remotas, deja marcada únicamente *Modalidad: remoto* y pulsa *Ofertas que cumplen todos los filtros*; si salen muy pocas, añade un filtro de conocimientos cada vez. (Es una deducción a partir de los textos de los botones: compruébala en tu pantalla.)

**b) Expectativas realistas.** Remoto sin experiencia es la combinación más disputada: en general, un junior aprende más y más rápido con alguien al lado. En FCT/Dual, además, **decide el centro** si acepta una modalidad remota: pregunta a tu tutor *antes* de inscribirte. Si no la acepta, valora un híbrido o una presencial en una zona a la que puedas llegar; la FCT es la vía más corta hacia el primer contrato.

**c) Qué suma para remoto**

- **Puesto en casa:** Ethernet por cable (tu portátil tiene puerto Gigabit), auriculares con micro, webcam (la tienes), un sitio sin ruido, datos del móvil como plan B de conexión y el portátil siempre enchufado.
- **Herramientas:** asistencia remota (8.4), VPN (ticket 11 de la sección 7), videollamadas (Teams, Meet, Zoom) y ticketing. En remoto pesa más Microsoft 365 / Entra ID (sección 8).
- **Escribir bien:** sin ver al usuario, tu ticket y tus mensajes de seguimiento son tu trabajo. Practica con la plantilla de 12.2.
- **Equipo de la empresa:** pregunta en la entrevista qué equipo y acceso te darían (portátil, VPN, escritorio virtual). Es probable que trabajen sobre Windows: aprende en tus VM y **no instales software corporativo en tu portátil personal sin permiso por escrito**.
- **Seguridad en casa:** bloquea la sesión al levantarte (`Win+L` en Windows; `Super+L` en Zorin), usa gestor de contraseñas y MFA, y mantén actualizado el router.
- **Inglés técnico básico:** documentación y mensajes de error; con Professor Messer lo practicas a la vez.

**d) Practica el remoto en el laboratorio**

1. **Soporte a ciegas:** no toques el equipo del "usuario"; dirígelo solo con preguntas e instrucciones (Prompt 19). Después, dale asistencia a `PC-CLI01` por RDP y por Asistencia rápida.
2. **Un screencast de 3 minutos** resolviendo "cuenta bloqueada" y explicándolo en voz alta (OBS Studio sirve en Zorin): es práctica de videollamada y una pieza más para tu portafolio.

**e) Cuidado con las ofertas falsas.** Desconfía de cualquier "trabajo o prácticas remotas" que te pida pagar una formación o una fianza por el equipo, te solicite DNI o IBAN antes de una entrevista, o te contacte solo por WhatsApp o Telegram. Unas prácticas FCT van siempre con convenio del centro y un contrato real no se paga. Si dudas, enséñasela a tu tutor.

---

## 2. Mapa de habilidades: qué dominar y hasta dónde

| Nivel | Bloque | "Lo sé" significa… | Sección |
|---|---|---|---|
| 🔴 Imprescindible | Active Directory + Windows Server | Montas un dominio, creas OU/usuarios/grupos, unes un PC, aplicas una GPO y resuelves "contraseña / cuenta bloqueada". | 5 |
| 🔴 Imprescindible | Redes y diagnóstico | Explicas IP, máscara, gateway, DNS y DHCP, y localizas una avería con la escalera del ping. | 6 |
| 🔴 Imprescindible | Windows cliente (tickets) | Resuelves los 12 tickets típicos con un procedimiento claro. | 7 |
| 🔴 Imprescindible | Tickets, ITIL mínimo y trato al usuario | Redactas un ticket, priorizas, escalas y mantienes la calma. | 12 |
| 🟠 Suma mucho | Microsoft 365, SaaS y asistencia remota | Creas un usuario, asignas licencia, reseteas MFA y das asistencia remota. | 8 |
| 🟠 Suma mucho | Linux por terminal | Navegas, gestionas permisos y servicios, lees logs y entras por SSH. | 9 |
| 🟠 Suma mucho | SQL básico + copias de seguridad | Haces SELECT/INSERT/UPDATE/DELETE, JOIN y GROUP BY, y restauras un backup. | 10 |
| 🟡 Extra | Hardware 101 (para SPV / campo) | Diagnosticas por descarte y cambias RAM o disco. | 11 |
| 🟡 Extra | Python mínimo y PowerShell de copiar-pegar | Lees un script corto y sabes qué hace. | 10 |
| ⚪ Más adelante | Certificaciones (A+, ITIL, Microsoft) | Solo cuando tengas prácticas o trabajo. | 13.5 |

---

## 3. Tu laboratorio (receta cerrada para tu portátil)

### 3.1 Lo que tu equipo permite

Ryzen 7 7435HS (8 núcleos / 16 hilos, AMD-V activo), 32 GB DDR5 y NVMe de 1 TB: el laboratorio completo cabe con holgura. Solo recuerda tu regla: **deja al host (Zorin) al menos 4 hilos y 6–8 GB de RAM**. Los detalles de hardware ya están en `resumen_portatil_ASIR.md`.

### 3.2 Máquinas virtuales

| VM | Sistema | vCPU | RAM | Disco (dinámico) | Red |
|---|---|---|---|---|---|
| `DC01` | Windows Server en evaluación (2025; la 2022 también vale, los pasos son iguales) · edición **Standard (Desktop Experience)** | 2 | 4 GB | 60 GB | Adaptador 1: red interna `labnet` · Adaptador 2: NAT |
| `PC-CLI01` | Windows 11 Enterprise (evaluación) | 2 | 4 GB | 64 GB | Adaptador 1: red interna `labnet` · Adaptador 2: NAT |
| `LNX01` | Ubuntu Server LTS (sin escritorio; marca "OpenSSH server" al instalar) | 1 | 2 GB | 25 GB | NAT con reenvío de puerto 2222 → 22 |
| `PC-CLI02` *(opcional)* | Windows 11 (clon de `PC-CLI01`) | 2 | 4 GB | 64 GB | Red interna `labnet` |

Con las tres VM principales usas unos **10 GB de RAM y 5 vCPU**: te quedan ~22 GB y 11 hilos para Zorin.

### 3.3 Instalar VirtualBox en Zorin (ojo con tu kernel)

- Tu kernel es `7.0.0-38-generic`. **VirtualBox 7.2.8** (abril de 2026) fue la primera versión en añadir soporte inicial para los kernels 6.19 y 7.0. Instala **7.2.8 o superior** desde la web oficial (paquete `.deb`). Una versión anterior, por ejemplo la de los repositorios de la distribución, puede no compilar el módulo del kernel.
- Con **Secure Boot** activo, la instalación te pedirá una contraseña MOK; al reiniciar elige *Enroll MOK*.
- Si tras actualizar el kernel las VM no arrancan ("Kernel driver not installed"): `sudo /sbin/vboxconfig`.
- Si creas un invitado **Linux con escritorio** y kernel 7.0 o superior, usa el controlador gráfico **VMSVGA** (el módulo `vboxvideo` de las Guest Additions está obsoleto para esos kernels).
- Instala las **Guest Additions** en las VM con escritorio (Dispositivos → Insertar imagen de CD de las Guest Additions).
- **No mezcles VirtualBox y KVM/virt-manager** en la misma sesión. Plan B si VirtualBox da guerra: virt-manager (KVM), aunque con Windows exige drivers virtio (más trabajo).

### 3.4 Descargas

| Qué | Dónde | Notas |
|---|---|---|
| Windows Server (evaluación, 180 días) | Microsoft Evaluation Center | La ISO incluye Standard y Datacenter. **Conéctalo a Internet (adaptador NAT) en los primeros 10 días** para que se active; si no, se apagará solo. |
| Windows 11 Enterprise (evaluación, 90 días) | Microsoft Evaluation Center | Microsoft indica que requiere iniciar sesión con cuenta Microsoft. Si en el asistente aparece *Configurar para trabajo o escuela → Opciones de inicio de sesión → Unirse a un dominio en su lugar*, úsalo para crear una cuenta local; si no, usa una cuenta Microsoft de pruebas. |
| Ubuntu Server LTS | ubuntu.com/download/server | Última LTS disponible. |

### 3.5 Red del laboratorio

| Elemento | Valor |
|---|---|
| Red interna | `labnet` · 192.168.50.0/24 |
| Dominio | `empresa.local` (NetBIOS `EMPRESA`) |
| `DC01` | 192.168.50.10 (estática) · DNS: ella misma (192.168.50.10) |
| DHCP (en `DC01`) | 192.168.50.100 – 192.168.50.200 · DNS 192.168.50.10 |
| `PC-CLI01` | IP por DHCP |
| `LNX01` | NAT · SSH desde Zorin: `ssh -p 2222 usuario@127.0.0.1` |

> ⚠️ **Regla de oro:** mientras trabajes con el dominio, **desconecta el cable virtual del adaptador NAT** de `DC01` y `PC-CLI01` (VirtualBox: Dispositivos → Red → desmarca el adaptador NAT). Con los dos conectados, el cliente puede usar el DNS del NAT y no encontrará el dominio. Conéctalo solo para actualizar, activar o descargar.

No necesitas modo puente en este plan (así evitas el problema del Wi-Fi que ya anotaste en tu resumen del portátil).

### 3.6 Snapshots (instantáneas)

`00-limpio` (SO recién instalado) · `01-base` (nombre + IP fija) · `02-ad-listo` · `03-dominio-ok` · `04-gpo-carpetas` · `99-antes-de-romper` (antes de las averías de la sección 6.4). Exporta a `.ova` cuando algo quede estable.

### 3.7 Verificación del laboratorio (tras el Día 4)

```text
En PC-CLI01 (cmd o PowerShell):
  ipconfig /all                      -> IP 192.168.50.1xx · DNS 192.168.50.10 · servidor DHCP 192.168.50.10
  nslookup empresa.local             -> responde 192.168.50.10
  ping DC01                          -> responde
  nltest /dsgetdc:empresa.local      -> muestra DC01
  whoami                             -> empresa\lgomez
  gpresult /r                        -> lista la GPO aplicada
```

### 3.8 Problemas típicos del laboratorio

| Síntoma | Causa probable | Solución |
|---|---|---|
| VM no arranca: "Kernel driver not installed" | Módulo de VirtualBox sin compilar o sin firmar (Secure Boot) | `sudo /sbin/vboxconfig`; si hay Secure Boot, completa *Enroll MOK*. |
| Windows 11: "este equipo no cumple los requisitos" | Falta EFI/TPM, o poca RAM/disco | Activa EFI y TPM 2.0 en Configuración → Sistema (mínimo 4 GB de RAM y 64 GB de disco). El asistente con tipo "Windows 11" suele activarlos. |
| El cliente no encuentra el dominio al unirse | DNS del cliente no apunta al DC, o NAT conectado | `ipconfig /all`: DNS = 192.168.50.10; desconecta el NAT; `ping 192.168.50.10`. |
| Windows Server se apaga solo tras unos días | Evaluación sin activar | Conecta el adaptador NAT para que se active en línea. |
| El cliente no recibe IP (169.254.x.x) | DHCP sin autorizar o ámbito inactivo | En `DC01`: *Complete DHCP configuration* y activar el ámbito. |
| Pantalla diminuta o sin portapapeles | Faltan Guest Additions | Instálalas y reinicia la VM. |

---

## 4. Plan de 14 días

**Ritmo:** 90–120 min al día = 10 min de repaso (Prompt 17) + 60–80 min de práctica + 10–20 min documentando. Si un día falla, **no lo recuperes**: sigue con el siguiente y repite el hueco el fin de semana.

| Día | Objetivo | Haz | "Lo sé" cuando puedo… | Prompts |
|---|---|---|---|---|
| 1 | Laboratorio listo | Instalar VirtualBox ≥ 7.2.8, descargar ISOs, crear la red `labnet`, test de nivel | Arrancar una VM de prueba y tengo mi diagnóstico | 0, 1, 2 |
| 2 | Windows Server instalado | Crear `DC01`, instalar (Desktop Experience), nombre, IP fija, actualizar y activar por NAT | Ver `192.168.50.10` en `ipconfig` y tengo snapshot `01-base` | 2, 3 |
| 3 | Active Directory I | Roles AD DS + DNS, promover a DC `empresa.local`, crear OU, usuarios y grupos | Abrir `dsa.msc` con mi estructura y `nslookup empresa.local` responde | 3 |
| 4 | Active Directory II | DHCP, crear `PC-CLI01`, unirlo al dominio, iniciar sesión con usuario de dominio | Ejecutar `whoami` → `empresa\usuario` en el cliente | 3 |
| 5 | AD del día a día + GPO + carpetas | Resetear, desbloquear, deshabilitar; GPO de Panel de control; política de bloqueo; carpeta con permisos NTFS | Resolver "cuenta bloqueada" y "no accedo a la carpeta" sin guía | 3, 5 |
| 6 | Redes I | IP, máscara, gateway, DNS, DHCP; escalera del ping; subredes /24–/30 | Explicar la escalera del ping y calcular los hosts de un /26 | 4 |
| 7 | Redes II + repaso | Provocar y arreglar 5 averías del laboratorio; repaso de la semana | Tener 5 averías resueltas y anotadas | 4, 17 |
| 8 | Windows cliente I | Tickets 1–6 de la sección 7 | Escribir 6 procedimientos con mis palabras | 5, 6 |
| 9 | Windows cliente II + remoto | Tickets 7–12; Asistencia rápida y RDP | Dar asistencia remota a `PC-CLI01` | 5, 6 |
| 10 | Microsoft 365 y SaaS | Conceptos de Entra ID, Exchange, Teams, licencias y MFA (practica si consigues un tenant de prueba) | Explicar qué hace un helpdesk en M365 | 7 |
| 11 | Linux I | Terminal en Zorin (en `~/practica`), permisos, Bandit niveles 0–10 | Usar 15 comandos de memoria | 8 |
| 12 | Linux II + SQL | `LNX01`: SSH, systemctl, logs. SQL: SELECT → JOIN y un backup | Entrar por SSH a `LNX01` y resolver 10 consultas | 8, 9 |
| 13 | Tickets + documentación | 5 simulacros de ticket; documentar el laboratorio; Python mínimo si lo necesitas para aprobar | Entregar un documento de 3–5 páginas del laboratorio | 5, 10, 12 |
| 14 | CV + entrevista | CV final, LinkedIn, simulacros técnico y de competencias | Tener CV de 1 página y 2 simulacros evaluados | 13, 15, 16 |

> **Si buscas remoto:** el día 13 dedica 20 minutos al ejercicio 1.4 (d) y el día 14 haz el Prompt 19 además de los simulacros.

### Ruta ultra-express (si solo tienes 5 días)

1. **Día 1:** laboratorio + `DC01` + promover a DC + OU, usuarios y grupos.
2. **Día 2:** DHCP + unir `PC-CLI01` + reset/desbloqueo de cuentas + carpeta compartida con permisos.
3. **Día 3:** escalera del ping + comandos de red + leer los 12 tickets + Prompt 5 (simulador).
4. **Día 4:** 15 comandos de Linux + SELECT/JOIN en SQL + Prompt 6 con tus errores reales.
5. **Día 5:** CV + 3 proyectos resumidos + simulacros de entrevista (Prompts 15 y 16) + 10 candidaturas.

---

## 5. Módulo A · Active Directory y Windows Server (🔴 imprescindible)

### 5.1 Lo que tienes que poder explicar

- **Dominio:** grupo de equipos y usuarios gestionados de forma centralizada.
- **Active Directory (AD DS):** el servicio de directorio de Microsoft; la base de datos de usuarios, equipos, grupos y políticas.
- **Controlador de dominio (DC):** el servidor que ejecuta AD DS y autentica a los usuarios.
- **DNS:** AD depende de él. Si el DNS falla, falla el inicio de sesión, la unión al dominio y las GPO.
- **OU (unidad organizativa):** carpeta lógica para organizar objetos, aplicar GPO y delegar tareas.
- **Grupos:** de *seguridad* (dan permisos) y de *distribución* (correo). Regla: usuarios en grupos, permisos a grupos, **nunca permisos a usuarios sueltos** (modelo AGDLP: Cuentas → Global → Dominio local → Permisos).
- **GPO:** políticas para usuarios o equipos, enlazadas a dominio u OU. Orden de aplicación: Local → Sitio → Dominio → OU (la última gana).
- **Kerberos:** autenticación por tickets; exige hora sincronizada (tolerancia por defecto: 5 minutos).
- **Windows Home no se une a un dominio**; Pro, Enterprise y Education sí.

### 5.2 Laboratorio paso a paso

**A. Instalar `DC01`**

1. VirtualBox → Nueva: nombre `DC01`, ISO de Windows Server, 4096 MB, 2 CPU, 60 GB. Marca *Omitir instalación desatendida* para elegir tú la edición.
2. Red: Adaptador 1 → *Red interna* → `labnet`. Adaptador 2 → *NAT*.
3. Al instalar, elige **Standard Evaluation (Desktop Experience)**. La que no dice "Desktop Experience" es modo consola, sin interfaz gráfica. Instalación personalizada y contraseña del Administrador.
4. Instala las Guest Additions y reinicia.
5. Conecta el NAT, ejecuta Windows Update y deja que se active en línea (hazlo en los primeros 10 días). Después desconecta el NAT.
6. Server Manager → Local Server → nombre del equipo → `DC01` → reiniciar.
7. IP fija: `ncpa.cpl` → el adaptador de la red interna (el que muestra 169.254.x.x; el NAT suele tener 10.0.2.15) → IPv4: IP `192.168.50.10`, máscara `255.255.255.0`, puerta de enlace vacía, DNS `192.168.50.10`.
8. Snapshot `01-base`.

**B. Promover el servidor a controlador de dominio**

1. Server Manager → Manage → *Add Roles and Features* → rol basado en roles → marca **Active Directory Domain Services** (acepta las características) y **DNS Server** → instalar.
2. Banner amarillo → *Promote this server to a domain controller* → *Add a new forest* → nombre raíz `empresa.local` → contraseña DSRM (apúntala) → NetBIOS `EMPRESA` → siguiente… → Install. Se reinicia solo.
3. ✅ Comprobación: entras como `EMPRESA\Administrator`; `nslookup empresa.local` responde `192.168.50.10`; AD DS y DNS salen en verde en Server Manager.
4. El aviso "no se puede crear la delegación del servidor DNS" es normal en un laboratorio.
5. Snapshot `02-ad-listo`.

**C. Estructura: OU, usuarios y grupos**

1. Herramientas → *Active Directory Users and Computers* (`dsa.msc`).
2. Crea la OU `Empresa` y dentro `Ventas`, `IT`, `Direccion`, `Equipos` y `Deshabilitados`.
3. Crea usuarios: `lgomez` (Laura Gómez, Ventas), `pruiz` (Pablo Ruiz, IT), `mtorres` (Marta Torres, Dirección).
4. Crea grupos de seguridad globales: `GG_Ventas`, `GG_IT`, `GG_Direccion`, y añade cada usuario al suyo.
5. ✅ Comprobación: arrastra un usuario a otra OU y mira su pestaña *Member Of*.

**D. DHCP**

1. Añade el rol **DHCP Server** → en el banner amarillo, *Complete DHCP configuration* (autoriza el servidor en AD).
2. Herramientas → DHCP → IPv4 → *Nuevo ámbito*: nombre `labnet`, rango `192.168.50.100`–`192.168.50.200`, máscara /24, sin puerta de enlace, DNS `192.168.50.10`, dominio `empresa.local`. Activa el ámbito.

**E. Crear `PC-CLI01` y unirlo al dominio**

1. VM con 4 GB, 2 CPU, 64 GB, EFI y TPM 2.0. Adaptador 1: `labnet`; Adaptador 2: NAT (conectado solo durante la instalación).
2. Instala Windows 11 Enterprise (ver nota de cuenta en 3.4).
3. Desconecta el NAT. `ipconfig /all` debe mostrar una IP 192.168.50.1xx y DNS `192.168.50.10`.
4. Renombra a `PC-CLI01` y únelo: `sysdm.cpl` → Cambiar → Dominio `empresa.local` → credenciales `EMPRESA\Administrator` → reiniciar.
5. Inicia sesión como `EMPRESA\lgomez`.
6. ✅ Comprobación: `whoami` → `empresa\lgomez`; `echo %logonserver%` → `\\DC01`.
7. En `DC01`, mueve el objeto equipo de *Computers* a `Empresa\Equipos`.
8. Snapshot `03-dominio-ok` en ambas VM.

**F. GPO sencillas**

1. `gpmc.msc` → clic derecho en la OU `Ventas` → *Create a GPO in this domain, and Link it here* → `GPO_Ventas_BloquearPanel` → editar → User Configuration → Policies → Administrative Templates → Control Panel → **Prohibit access to Control Panel and PC settings** = Enabled.
2. En el cliente: `gpupdate /force`, cierra sesión y entra otra vez como `lgomez`. El Panel de control debe estar bloqueado. `gpresult /r` muestra la GPO aplicada.
3. Para practicar cuentas bloqueadas: Default Domain Policy → Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → *Account Lockout Policy* → umbral de 3 intentos y 5 minutos. Falla 3 veces la contraseña de `lgomez` y desbloquéala desde `dsa.msc`.

**G. Carpeta compartida con permisos**

1. En `DC01`: carpeta `C:\Datos\Ventas` (en una empresa real iría en un servidor de archivos, no en el DC).
2. Propiedades → Compartir → Uso compartido avanzado → recurso `Ventas`; permisos de recurso compartido: `Authenticated Users` = Cambiar.
3. Pestaña Seguridad (NTFS): desactiva la herencia, quita `Users`, añade `GG_Ventas` = Modificar y `GG_IT` = Control total (y deja `SYSTEM` y `Administrators`).
4. En el cliente: `net use S: \\DC01\Ventas`. `lgomez` entra; `mtorres` recibe "acceso denegado".
5. Dos ideas para llevarte: el acceso efectivo es el **más restrictivo** entre permisos de recurso compartido y NTFS, y tras añadir a alguien a un grupo **debe cerrar sesión y volver a entrar** para que se actualice su token.
6. Snapshot `04-gpo-carpetas`.

### 5.3 Tareas diarias de helpdesk en AD

> Antes de resetear una contraseña, **verifica la identidad** según el protocolo de la empresa (llamada a un número registrado, confirmación del responsable…). Nunca pidas la contraseña al usuario y entrega la temporal por un canal seguro.

| Tarea | En `dsa.msc` | PowerShell (opcional, copiar-pegar; en el DC o con RSAT) |
|---|---|---|
| Resetear contraseña | Clic derecho → *Reset Password* → marca "User must change password at next logon" | `Set-ADAccountPassword -Identity lgomez -Reset -NewPassword (ConvertTo-SecureString "Temporal#2026" -AsPlainText -Force)` y después `Set-ADUser lgomez -ChangePasswordAtLogon $true` |
| Desbloquear cuenta | Propiedades → pestaña *Account* → *Unlock account* | `Unlock-ADAccount -Identity lgomez` |
| Ver cuentas bloqueadas | — | `Search-ADAccount -LockedOut` |
| Estado de una cuenta | Pestaña *Account* | `Get-ADUser lgomez -Properties LockedOut,PasswordExpired,Enabled,LastLogonDate` |
| Deshabilitar / habilitar | Clic derecho → *Disable / Enable Account* | `Disable-ADAccount -Identity lgomez` / `Enable-ADAccount -Identity lgomez` |
| Añadir a un grupo | Propiedades → *Member Of* → *Add* | `Add-ADGroupMember -Identity GG_Ventas -Members lgomez` |
| Mover a otra OU | Arrastrar, o clic derecho → *Move* | (mejor con la interfaz gráfica) |
| Alta de empleado | *New → User*, grupos, OU correcta y, si hay M365, licencia | — |
| Baja de empleado | *Disable* + quitar de grupos + mover a `Deshabilitados` + reset de contraseña + avisar al responsable | — |

En el cliente, tus herramientas son: `gpupdate /force`, `gpresult /r`, `whoami /groups`, `nltest /dsgetdc:empresa.local`, `net user lgomez /domain` y, en PowerShell, `Test-ComputerSecureChannel -Verbose`.

### 5.4 Errores típicos de AD

| Síntoma | Causa probable | Solución |
|---|---|---|
| No se puede contactar con un controlador de dominio al unir el equipo | El DNS del cliente no apunta al DC, o el NAT está conectado | `ipconfig /all` → DNS = IP del DC; `ping 192.168.50.10`; desconecta el NAT. |
| "La relación de confianza entre esta estación de trabajo y el dominio principal falló" | La contraseña de la cuenta de equipo se desincronizó (por ejemplo, tras restaurar un snapshot viejo) | Entra con cuenta local de administrador y ejecuta en PowerShell `Test-ComputerSecureChannel -Repair -Credential EMPRESA\Administrator`; si no, saca el equipo del dominio y vuelve a unirlo. |
| Inicio de sesión lento o fallido | DC apagado o servicio DNS parado | Arranca `DC01` primero; comprueba el servicio DNS. |
| Error de Kerberos / login falla | Hora del cliente desfasada más de 5 min | Corrige la zona horaria; `w32tm /resync`. |
| La cuenta se bloquea sola | Credenciales viejas en unidades de red, tareas programadas, móvil con correo… | En el DC: Visor de eventos → Seguridad → evento **4740**, que indica el equipo origen. |
| Sigue "acceso denegado" tras añadir al grupo | El token no se ha actualizado | Cerrar sesión y volver a entrar. |

---

## 6. Módulo B · Redes y diagnóstico (🔴 imprescindible)

### 6.1 Lo mínimo que debes poder explicar

| Concepto | En una frase |
|---|---|
| Dirección IP | Identificador de un equipo en una red (IPv4: cuatro números de 0 a 255). |
| Máscara | Indica qué parte de la IP es red y cuál es equipo (/24 = 255.255.255.0). |
| Puerta de enlace (gateway) | El router por el que salen los paquetes hacia otras redes. |
| DNS | Traduce nombres (`google.com`) a direcciones IP. |
| DHCP | Entrega IP, máscara, gateway y DNS automáticamente (proceso DORA: Discover, Offer, Request, Acknowledge). |
| NAT | El router traduce IP privadas a una pública para salir a Internet. |
| MAC / ARP | Dirección física de la tarjeta / protocolo que relaciona IP con MAC en la red local. |
| Switch / router / firewall / punto de acceso | Conecta equipos de una red / conecta redes distintas / filtra tráfico / da Wi-Fi. |
| VLAN | Separa redes lógicas dentro del mismo switch. |
| VPN | Túnel cifrado para conectarse a la red de la empresa desde fuera. |
| Puerto | Número que identifica un servicio dentro de un equipo. |

- **Rangos privados:** 10.0.0.0/8 · 172.16.0.0/12 · 192.168.0.0/16. **169.254.x.x (APIPA)** = el equipo no consiguió IP por DHCP.
- **Hosts de una subred:** 2^(32 − prefijo) − 2. Así: /24 → 254 · /25 → 126 · /26 → 62 · /27 → 30 · /28 → 14 · /30 → 2.
- **Puertos que debes conocer:** 20/21 FTP · 22 SSH · 25 SMTP · 53 DNS · 67/68 DHCP · 80 HTTP · 88 Kerberos · 110 POP3 · 123 NTP · 143 IMAP · 389 LDAP · 443 HTTPS · 445 SMB · 636 LDAPS · 993 IMAPS · 1433 SQL Server · 3306 MySQL/MariaDB · 3389 RDP · 5432 PostgreSQL.

### 6.2 La escalera del ping (de abajo hacia arriba)

| Paso | Comando | Si falla, el problema está en… |
|---|---|---|
| 1 | `ping 127.0.0.1` | La pila TCP/IP del propio equipo (rarísimo: reiniciar o `netsh winsock reset`). |
| 2 | `ping <tu IP>` (la de `ipconfig`) | Tarjeta, driver o adaptador deshabilitado. |
| 3 | `ping <puerta de enlace>` | Cable, Wi-Fi, switch, o IP/máscara mal configuradas. |
| 4 | `ping 8.8.8.8` | Salida a Internet (router, ISP, firewall, NAT). |
| 5 | `ping google.com` | **DNS** (si el paso 4 funcionó y este no). |
| 6 | `Test-NetConnection servidor -Port 443` (o el puerto del servicio) | El servicio, el puerto o el firewall del destino. |

> ⚠️ El firewall puede bloquear el ping (ICMP) y darte un falso negativo. Confírmalo con otra prueba antes de concluir.

### 6.3 Comandos de red en Windows

| Comando | Para qué | Cuándo |
|---|---|---|
| `ipconfig /all` | IP, máscara, gateway, DNS, DHCP y MAC | Siempre el primero |
| `ipconfig /release` y `ipconfig /renew` | Pedir IP nueva al DHCP | IP 169.254.x.x o cambio de red |
| `ipconfig /flushdns` | Vaciar la caché DNS | Un nombre lleva a una IP antigua |
| `nslookup nombre [servidor_dns]` | Probar la resolución DNS | Distinguir "DNS" de "red" |
| `tracert destino` | Ver los saltos hasta el destino | Lentitud o cortes |
| `pathping destino` | Pérdida de paquetes por salto | Conexión inestable |
| `netstat -ano` | Conexiones y puertos con el PID del proceso | "¿Quién usa el puerto 80?" |
| `arp -a` | Tabla IP ↔ MAC | Sospecha de IP duplicada |
| `route print` | Tabla de rutas | Rutas raras tras una VPN |
| `netsh winsock reset` (y reiniciar) | Reparar la pila de red | Red extraña tras malware o VPN |
| `netsh wlan show wlanreport` | Informe de Wi-Fi | Wi-Fi inestable |
| `Test-NetConnection host -Port N` | Probar un puerto TCP (PowerShell) | "¿Llego al servicio?" |
| `nltest /dsgetdc:empresa.local` | Ver qué controlador de dominio me atiende | Problemas de dominio |
| `gpupdate /force` y `gpresult /r` | Forzar y consultar GPO | Una política no se aplica |

### 6.4 Averías para provocar en tu laboratorio

Haz snapshot `99-antes-de-romper`. Ciclo: **rompe → diagnostica → arregla → documenta**. Con el **Prompt 4** puedes pedir que otra persona (la IA) te proponga las averías sin decirte la causa.

| # | Provoca | Síntoma esperado | Qué comprobar |
|---|---|---|---|
| 1 | Cambia el DNS del cliente a 8.8.8.8 | No habla con el dominio; Internet sí | `nslookup empresa.local` |
| 2 | Detén el servicio DHCP en `DC01` y reinicia el cliente | IP 169.254.x.x | `ipconfig /all` |
| 3 | Pon una máscara o IP fuera de rango en el cliente | El ping al DC falla | `ipconfig`, `ping` |
| 4 | Deshabilita el adaptador de red del cliente | "Sin conexión" | Paso 2 de la escalera |
| 5 | Adelanta la hora del cliente 10 minutos | Error de Kerberos / login falla | `w32tm /resync` |
| 6 | Detén el servicio DNS en `DC01` | Login lento o fallido, no resuelve | `Get-Service DNS`, `nslookup` |
| 7 | Quita a `lgomez` de `GG_Ventas` | "Acceso denegado" a la carpeta | `whoami /groups`; cerrar sesión y entrar |
| 8 | Detén el servicio *Cola de impresión* | No imprime | `services.msc` |
| 9 | Bloquea el puerto 445 en el firewall de `DC01` | La carpeta falla aunque la red esté bien | `Test-NetConnection DC01 -Port 445` |
| 10 | Elimina el objeto equipo del cliente en AD | "La relación de confianza falló" | `Test-ComputerSecureChannel` |

### 6.5 Método de diagnóstico en 6 pasos (úsalo siempre, también en entrevistas)

1. **Escucha y concreta:** ¿qué intentabas hacer?, ¿qué ves exactamente (mensaje literal o captura)?, ¿desde cuándo?, ¿qué cambió?
2. **Alcance:** ¿solo a ti o a más gente?, ¿en un sitio o en todos?, ¿siempre o a veces?
3. **De lo simple a lo complejo:** cable o Wi-Fi, reinicio, credenciales, espacio en disco…
4. **Hipótesis → prueba → resultado:** cambia **una** cosa cada vez y anótala.
5. **Resuelve y confirma con el usuario** (que lo vea funcionando) y explícale en 1–2 frases qué pasó.
6. **Documenta** el ticket o **escala** con todos los datos.

---

## 7. Módulo C · Windows cliente: los 12 tickets (🔴 imprescindible)

Para cada ticket: qué preguntar, qué probar (de simple a complejo) y cuándo escalar. Practica cada uno en `PC-CLI01`.

**1. No puedo iniciar sesión**
- Pregunta el mensaje exacto: contraseña incorrecta, cuenta bloqueada o deshabilitada, contraseña caducada, "no hay servidores de inicio de sesión disponibles".
- Comprueba teclado (bloq. mayús., idioma), formato `EMPRESA\usuario` y si hay red (sin red solo entran con credenciales en caché).
- En AD: ¿bloqueada, caducada, deshabilitada? Desbloquea o resetea (con verificación de identidad).
- Si solo falla en un equipo: relación de confianza (ticket 9), hora, DNS.
- **Escala si** la cuenta se bloquea otra vez sola (causa raíz: evento 4740) o es una cuenta privilegiada.

**2. No tengo Internet / Wi-Fi**
- Escalera del ping (6.2). Revisa cable, Wi-Fi, modo avión. ¿Afecta a más compañeros? Si sí: red, switch o ISP → escala.
- `ipconfig /all`: ¿169.254? → DHCP. ¿IP correcta pero sin gateway? `ipconfig /release` y `/renew`; `/flushdns`.
- Wi-Fi: olvidar y reconectar; informe con `netsh wlan show wlanreport`.
- Último recurso: `netsh winsock reset` y reinicio.
- **Escala si** el fallo está en gateway, switch, punto de acceso o ISP.

**3. La impresora no imprime**
- ¿Solo yo o todos? ¿Está encendida, sin atasco, con tóner y papel, y conectada a la red?
- Cola atascada (en cmd como administrador): `net stop spooler`, borrar el contenido de `C:\Windows\System32\spool\PRINTERS`, `net start spooler`.
- Comprueba que no esté en "Usar impresora sin conexión", que sea la predeterminada, que el puerto/IP responda al `ping` y que el driver sea correcto.
- Quita la impresora y vuelve a añadirla (por IP o desde el servidor de impresión).
- **Escala si** es fallo de hardware o del servidor de impresión.

**4. No accedo a una carpeta compartida**
- "No se encuentra la ruta" = red/DNS/servidor. "Acceso denegado" = permisos. Pide credenciales = autenticación.
- `ping servidor`; prueba también por IP (`\\192.168.50.10\Ventas`). Si por IP va y por nombre no, es DNS.
- `Test-NetConnection servidor -Port 445`.
- Permisos: ¿está en el grupo correcto? Tras añadirlo, cerrar sesión y volver a entrar.
- Credenciales obsoletas: `control /name Microsoft.CredentialManager` → borrar la entrada; `net use * /delete` y reconectar.
- **Escala si** los permisos NTFS/recurso no te corresponden o el servidor de archivos está caído.

**5. El PC va lento**
- ¿Desde cuándo? ¿Siempre o con una aplicación concreta? ¿Se reinicia a menudo?
- Administrador de tareas (`Ctrl+Mayús+Esc`): CPU, RAM, disco y red → proceso culpable.
- Espacio libre en disco, programas de inicio, actualizaciones pendientes, antivirus analizando.
- `sfc /scannow` y, si hay errores, `DISM /Online /Cleanup-Image /RestoreHealth`.
- **Escala si** es hardware (RAM insuficiente, disco con errores) o hay sospecha de malware.

**6. Outlook / Teams / Office no funciona**
- ¿Una sola aplicación o todo Microsoft 365? ¿Es una incidencia general del servicio?
- Reinicia la aplicación, cierra sesión y entra, revisa si pide MFA o contraseña y si la licencia está asignada.
- Outlook: modo sin conexión, `outlook.exe /safe`, perfil nuevo, buzón lleno.
- Reparar Office: Configuración → Aplicaciones → Microsoft 365 → Modificar → *Reparación rápida* (y si no, *en línea*).
- Teams: limpiar caché o probar en el navegador (si funciona en web, el fallo es del cliente).
- **Escala si** hace falta licencia, buzón o MFA desde administración de M365.

**7. Pantalla azul o reinicios**
- Anota el código de parada y qué hacías.
- Visor de eventos (`eventvwr`) → Registros de Windows → Sistema → eventos críticos.
- ¿Driver o actualización reciente? Arranque en modo seguro y desinstalar.
- `sfc /scannow`, `DISM`, `chkdsk /f`, prueba de memoria.
- **Escala si** se repite: RAM, disco o placa; sustituir equipo.

**8. Perfil temporal / escritorio vacío**
- Mensaje típico: "Hemos iniciado sesión con un perfil temporal".
- Reinicia; comprueba espacio en disco y que el DC sea alcanzable.
- Solución habitual: crear un perfil nuevo y **copiar los datos** del antiguo (Escritorio, Documentos, Favoritos).
- **Escala si** hay redirección de carpetas, perfiles móviles o datos críticos sin copia.

**9. "La relación de confianza entre esta estación de trabajo y el dominio principal falló"**
- Causa: la contraseña de la cuenta de equipo no coincide con la de AD.
- Entra con una cuenta local de administrador y ejecuta `Test-ComputerSecureChannel -Repair -Credential EMPRESA\Administrator`. Si no, saca el equipo del dominio, reinicia y vuelve a unirlo.
- **Escala si** no tienes permiso para unir equipos.

**10. BitLocker pide la clave de recuperación**
- Causas típicas: cambio de BIOS o de hardware, actualización de firmware, TPM modificado.
- **Verifica la identidad.** Localiza la clave en AD (pestaña *BitLocker Recovery* del objeto equipo), en Entra ID/Intune o en la cuenta Microsoft, según cómo se guardara. El identificador que muestra la pantalla debe coincidir con el de la clave.
- Entrégala por un canal seguro y anótalo en el ticket.
- **Escala si** la clave no está guardada en ningún sitio (es grave).

**11. La VPN no conecta**
- ¿Hay Internet? (escalera del ping). ¿Credenciales y MFA correctos? ¿Hora correcta? ¿Cliente VPN actualizado? Prueba con otra red (datos del móvil).
- Anota el mensaje o código de error y mira los logs del cliente.
- Una vez conectado: ¿resuelve nombres internos (DNS)? ¿llega a los recursos (`Test-NetConnection`)?
- **Escala si** el problema es del servidor, del firewall, de un certificado o la cuenta no tiene permiso VPN.

**12. Quiero instalar un programa / necesito ser administrador**
- **Mínimo privilegio:** no se da administrador local por defecto.
- Sigue el procedimiento: solicitud aprobada y Centro de software / Portal de empresa / Intune, o instalación por el técnico.
- Comprueba licencia y origen del software.
- Anota quién lo aprobó.
- **Escala si** el software no está catalogado o plantea dudas de seguridad.

**Extras frecuentes**
- *Teclado, ratón, monitor, dock, USB:* prueba otro puerto u otro equipo, Administrador de dispositivos, reinstalar driver.
- *Windows Update atascado:* reinicia, comprueba espacio, solucionador de problemas, `DISM`.
- *Correo sospechoso (phishing):* no clicar, reportar, cambiar contraseña, aislar el equipo si procede y **escalar a seguridad** (no investigues por tu cuenta).

### Herramientas de Windows que debes tener a mano (Win+R)

| Comando | Abre | Comando | Abre |
|---|---|---|---|
| `compmgmt.msc` | Administración de equipos | `services.msc` | Servicios |
| `eventvwr.msc` | Visor de eventos | `devmgmt.msc` | Administrador de dispositivos |
| `diskmgmt.msc` | Administración de discos | `resmon` | Monitor de recursos |
| `msconfig` | Configuración del sistema | `sysdm.cpl` | Propiedades del sistema (dominio) |
| `ncpa.cpl` | Conexiones de red | `msinfo32` | Información del sistema |
| `lusrmgr.msc` | Usuarios locales | `gpedit.msc` | Directivas locales (no en Home) |
| `dsa.msc` | Usuarios y equipos de AD | `gpmc.msc` | Administración de GPO |

---

## 8. Módulo D · Microsoft 365, SaaS y asistencia remota (🟠 suma mucho)

### 8.1 SaaS en tres líneas

Software que usas por Internet y que mantiene el proveedor (Microsoft 365, Google Workspace, Salesforce, Slack, Zoom, Jira, ServiceNow). Tu trabajo como soporte: **accesos, licencias, configuración y ayuda al usuario**, no la infraestructura. Aparece en 3 de tus ofertas.

### 8.2 Qué hace un helpdesk en Microsoft 365

| Tarea | Dónde |
|---|---|
| Crear usuario y asignar licencia | Centro de administración de Microsoft 365 (`admin.microsoft.com`) → Usuarios → Usuarios activos |
| Restablecer contraseña | El mismo sitio. **Si el usuario viene de un AD local sincronizado, se hace en AD**, salvo que exista escritura de vuelta (password writeback). |
| Resetear o registrar MFA | Entra ID (`entra.microsoft.com`) → Usuarios → Métodos de autenticación |
| Buzón compartido, lista de distribución, grupo | Centro de administración de Exchange / Grupos |
| Alias, reenvío o delegación de buzón | Exchange |
| Recuperar un archivo borrado | Papelera de OneDrive o SharePoint |
| Teams: añadir a un equipo, problemas de audio | Administración de Teams / dispositivos del usuario |
| Baja de empleado | Bloquear inicio de sesión, convertir el buzón en compartido, quitar licencia, revisar OneDrive |

### 8.3 Entorno híbrido y seguridad en una línea cada uno

- **Híbrido:** los usuarios sincronizados desde AD con Microsoft Entra Connect se gestionan en AD local; los cambios tardan en reflejarse (por defecto, en torno a 30 minutos).
- **MFA:** segundo factor además de la contraseña (app, SMS, llave); reduce el riesgo de robo de credenciales.
- **SSO:** un solo inicio de sesión para varias aplicaciones.
- **Acceso condicional:** reglas del tipo "solo desde equipos de la empresa" (a nivel de concepto).

### 8.4 Asistencia remota

| Herramienta | Cómo | Notas |
|---|---|---|
| Asistencia rápida (Quick Assist) | `Win+Ctrl+Q`; el usuario te da un código | Viene en Windows 10/11. |
| Escritorio remoto (RDP) | `mstsc`, puerto 3389 | El equipo destino debe ser Pro/Enterprise con RDP habilitado; normalmente por VPN. |
| AnyDesk / TeamViewer / herramienta de la empresa | Con autorización | Usa solo la que permita la empresa. |

**Reglas:** pide permiso, explica qué vas a hacer, no abras información personal, cierra la sesión al terminar y anótalo en el ticket.

### 8.5 Cómo practicar sin un tenant

Opciones: el tenant educativo de tu centro (pregunta a tu tutor), una prueba gratuita de Microsoft 365 Business si Microsoft la ofrece en ese momento, o Microsoft Learn con capturas. Si no consigues ninguno, dominar el modelo mental (qué se gestiona dónde) ya cubre el 80 % de la entrevista.

---

## 9. Módulo E · Linux (🟠 suma mucho)

Recuerda la regla 2: en soporte de oficina Linux **suma**, pero Windows decide. Dedica a esto los días 11 y 12.

### 9.1 Cómo practicar sin romper nada

- En Zorin, trabaja dentro de `~/practica`. Lo que sea peligroso, hazlo en `LNX01` con snapshot.
- `rm` no tiene papelera. No ejecutes con `sudo` comandos que no entiendas.

### 9.2 Los comandos que tienes que usar sin pensar

| Grupo | Comandos |
|---|---|
| Dónde estoy y moverme | `pwd`, `ls -la`, `cd /ruta`, `cd ..`, `cd ~` |
| Archivos | `mkdir`, `touch`, `cp -r`, `mv`, `rm`, `rm -r` (con cuidado) |
| Ver contenido | `cat`, `less`, `head`, `tail -f` (seguir un log en directo) |
| Buscar | `grep -i "texto" archivo`, `find / -name "x" 2>/dev/null`, `which`, `man comando` |
| Editar | `nano archivo` |
| Permisos y propietarios | `ls -l`, `chmod`, `chown`, `id`, `groups` |
| Usuarios | `sudo`, `whoami`, `adduser`, `passwd`, `usermod -aG grupo usuario`, `deluser` |
| Paquetes (Debian/Ubuntu/Zorin) | `sudo apt update`, `sudo apt upgrade`, `sudo apt install x`, `apt search x` |
| Servicios y logs | `systemctl status/start/stop/restart/enable/disable servicio`, `journalctl -u servicio -f`, `journalctl -xe`, carpeta `/var/log/` |
| Procesos | `ps aux`, `top` o `htop`, `kill PID`, `pkill nombre` |
| Disco y memoria | `df -h`, `du -sh *`, `free -h`, `lsblk` |
| Red | `ip a`, `ip r`, `ss -tulpn`, `ping`, `curl -I url`, `nslookup` o `dig`, `traceroute` |
| Acceso remoto | `ssh usuario@host`, `scp archivo usuario@host:/ruta` |
| Comprimir | `tar -czf x.tar.gz carpeta`, `tar -xzf x.tar.gz` |

### 9.3 Permisos en 30 segundos

`-rwxr-xr--` = tipo + **dueño** (`rwx`) + **grupo** (`r-x`) + **otros** (`r--`). Valores: `r=4`, `w=2`, `x=1`.

| Número | Significa | Uso típico |
|---|---|---|
| `755` | Dueño todo; grupo y otros leer y ejecutar | Scripts y carpetas públicas |
| `644` | Dueño leer y escribir; resto leer | Archivos normales |
| `700` / `600` | Solo el dueño | Claves y datos privados |
| `770` | Dueño y grupo todo; otros nada | Carpeta compartida de un grupo |

Ejemplos: `chmod 755 script.sh`, `chmod u+x script.sh`, `chown usuario:grupo archivo`.

### 9.4 Diagnóstico de un servicio

```text
¿Está activo?        systemctl status ssh
¿Escucha en su puerto? ss -tulpn | grep :22
¿Qué dice el log?     journalctl -u ssh -n 50
¿Lo bloquea el firewall? sudo ufw status
```

### 9.5 Práctica mínima en `LNX01`

1. Instala Ubuntu Server con "OpenSSH server". En VirtualBox, NAT → Avanzado → Reenvío de puertos: Host `127.0.0.1:2222` → Invitado `:22`.
2. Desde Zorin: `ssh -p 2222 tuusuario@127.0.0.1`.
3. `sudo apt update && sudo apt upgrade -y`.
4. Crea dos usuarios y un grupo; una carpeta `/srv/compartida` con permisos `770` para ese grupo.
5. Instala `apache2`; comprueba `systemctl status apache2` y `curl -I localhost`; mira el log con `tail -f /var/log/apache2/access.log`.
6. **Rompe y arregla:** `sudo systemctl stop apache2`, diagnostica y recupéralo.
7. Opcional: una tarea programada con `crontab -e` y una regla `sudo ufw allow 22/tcp`.

### 9.6 Retos recomendados

OverTheWire **Bandit** (niveles 0–10), **Linux Journey** (Command Line, Users and Groups, Permissions, Processes) y **Killercoda** para entornos listos en el navegador. Usa el **Prompt 8** para retos diarios de 5 minutos.

---

## 10. Módulo F · SQL, Python y PowerShell (mínimo) (🟠 / 🟡)

### 10.1 SQL: lo que de verdad piden

"Administración de bases de datos" aparece en 4 de tus ofertas. Usa el motor que use tu clase (MariaDB/MySQL o PostgreSQL); la sintaxis básica es casi idéntica.

```sql
CREATE DATABASE tienda;
USE tienda;

CREATE TABLE departamentos (
  id INT PRIMARY KEY AUTO_INCREMENT,
  nombre VARCHAR(50) NOT NULL
);

CREATE TABLE empleados (
  id INT PRIMARY KEY AUTO_INCREMENT,
  nombre VARCHAR(80) NOT NULL,
  salario DECIMAL(8,2),
  id_dpto INT,
  FOREIGN KEY (id_dpto) REFERENCES departamentos(id)
);

INSERT INTO departamentos (nombre) VALUES ('IT'), ('Ventas');
INSERT INTO empleados (nombre, salario, id_dpto) VALUES
  ('Laura', 1700, 2), ('Pablo', 1900, 1), ('Marta', 2400, 2);
```

Las consultas que tienes que dominar:

```sql
-- 1. Leer todo
SELECT * FROM empleados;
-- 2. Columnas concretas + filtro + orden
SELECT nombre, salario FROM empleados WHERE salario > 1500 ORDER BY salario DESC;
-- 3. Contar
SELECT COUNT(*) FROM empleados;
-- 4. Agrupar
SELECT id_dpto, COUNT(*) AS total, AVG(salario) AS media FROM empleados GROUP BY id_dpto;
-- 5. Unir tablas
SELECT e.nombre, d.nombre AS departamento FROM empleados e JOIN departamentos d ON e.id_dpto = d.id;
-- 6. Insertar
INSERT INTO empleados (nombre, salario, id_dpto) VALUES ('Ana', 1800, 1);
-- 7. Actualizar (¡siempre con WHERE!)
UPDATE empleados SET salario = 1900 WHERE nombre = 'Ana';
-- 8. Borrar (¡siempre con WHERE!)
DELETE FROM empleados WHERE nombre = 'Ana';
-- 9. Patrón de texto
SELECT * FROM empleados WHERE nombre LIKE 'A%';
-- 10. Limitar resultados
SELECT * FROM empleados ORDER BY salario DESC LIMIT 3;
```

Usuarios, permisos y copias de seguridad:

```sql
CREATE USER 'soporte'@'localhost' IDENTIFIED BY 'CambiaEstaClave!';
GRANT SELECT ON tienda.* TO 'soporte'@'localhost';
SHOW GRANTS FOR 'soporte'@'localhost';
```

```bash
# Copia de seguridad y restauración (en MariaDB reciente puede llamarse mariadb-dump)
mysqldump -u root -p tienda > tienda_backup.sql
mysql -u root -p tienda < tienda_backup.sql
```

**Reglas de oro:** antes de un `UPDATE` o `DELETE`, ejecuta el `SELECT` con el mismo `WHERE`; haz backup antes de tocar datos reales; usa `START TRANSACTION;` … `ROLLBACK;` o `COMMIT;` cuando puedas.

**Conceptos para la entrevista:** clave primaria, clave foránea, índice, normalización (evitar duplicados), transacción (ACID: atomicidad, consistencia, aislamiento, durabilidad), copia completa vs incremental y principio de mínimo privilegio en usuarios.

### 10.2 Python: lo mínimo para aprobar y leer scripts

No necesitas ser programador; necesitas **leer un script corto y saber qué hace**. Conceptos: variables y tipos, `print`/`input`, `if/elif/else`, `for`/`while`, listas y diccionarios, funciones (`def`), leer ficheros y `try/except`.

```python
# Cuenta cuántas líneas con "ERROR" hay en un log
total = 0
with open("servidor.log", encoding="utf-8") as f:
    for linea in f:
        if "ERROR" in linea:
            total += 1
print(f"Líneas con ERROR: {total}")
```

Lectura: abre el fichero, recorre línea a línea, suma uno cada vez que aparece "ERROR" y al final lo imprime. Truco: puedes pedir a la IA que genere el script, pero **léelo línea a línea y pruébalo en una VM con snapshot**; nunca ejecutes en un equipo real código que no entiendes. Usa el **Prompt 10**.

### 10.3 PowerShell de copiar-pegar (nivel "lo entiendo", no "lo escribo")

```powershell
Get-Service -Name Spooler                          # estado de un servicio
Restart-Service -Name Spooler                      # reiniciarlo
Get-Process | Sort-Object CPU -Descending | Select-Object -First 5   # 5 procesos que más CPU usan
Test-NetConnection 192.168.50.10 -Port 445         # ¿llego al puerto 445?
Get-WinEvent -LogName System -MaxEvents 20         # últimos 20 eventos del sistema
Get-NetIPConfiguration                             # configuración de red
Get-Volume                                         # espacio de los discos
Get-LocalUser                                      # usuarios locales
```

---

## 11. Módulo G · Hardware 101 (🟡 extra, clave para SPV)

- **Componentes y función:** CPU, RAM, almacenamiento (HDD, SSD SATA, NVMe), placa base, fuente, GPU, refrigeración, batería.
- **RAM:** DDR4 vs DDR5; SODIMM (portátil) vs DIMM (sobremesa). Almacenamiento: SATA vs M.2 NVMe. Puertos: USB-A/C, HDMI, DisplayPort, RJ45.
- **Diagnóstico por descarte ("no enciende"):** alimentación (cable, cargador, regleta, LED, batería) → pantalla (¿enciende pero no da imagen? prueba monitor externo) → RAM (reasentar, probar módulo a módulo) → disco → periféricos desconectados.
- **BIOS/UEFI:** cómo entrar (la tecla depende del fabricante: F2, Supr, F10, Esc…), orden de arranque, Secure Boot y TPM.
- **Seguridad física:** descarga electrostática (toca el chasis metálico o usa pulsera), desconecta corriente y batería, ordena los tornillos y haz fotos antes de desmontar.
- **RAID:** 0 reparte sin redundancia · 1 espejo (tolera 1 disco) · 5 paridad (mínimo 3 discos, tolera 1) · 10 espejo + reparto (mínimo 4). **RAID no es una copia de seguridad.**
- **Impresoras:** tóner, tambor, fusor, atascos, conexión de red.

Usa el **Prompt 11** para casos de diagnóstico.

---

## 12. Módulo H · Tickets, ITIL mínimo y trato al usuario (🔴 imprescindible)

### 12.1 Vocabulario

| Término | Qué es | Ejemplo |
|---|---|---|
| Incidencia | Algo que antes funcionaba y ya no | "Mi impresora no imprime" |
| Petición de servicio | Algo que se solicita | "Acceso a la carpeta de Ventas", "alta de un empleado" |
| Problema | Causa raíz de varias incidencias | "La impresora X falla cada lunes porque…" |
| Cambio | Modificar algo en producción con planificación y aprobación | "Actualizar el servidor", "nueva GPO" |
| SLA | Acuerdo de tiempos de respuesta y resolución | "P1: respuesta en 15 min" |
| N1 / N2 / N3 | Niveles de soporte: primer contacto / especialista / experto o proveedor | Tú empiezas en N1 |

**Prioridad = impacto × urgencia.** Un servicio caído para toda la empresa es P1; una duda de un usuario sin bloqueo es P4.

### 12.2 Plantilla de ticket

```text
TÍTULO: [Sistema] + síntoma breve   (ej.: "Outlook – no abre el buzón de Laura Gómez")
USUARIO / UBICACIÓN / EQUIPO: lgomez · Ventas · PC-CLI01
DESDE CUÁNDO / CAMBIOS RECIENTES: desde hoy 09:00; instaló una actualización ayer
SÍNTOMA (mensaje literal o captura): "..."
ALCANCE: 1 usuario / varios / todos
PRIORIDAD: P3 (impacto bajo, urgencia media)
PASOS REALIZADOS: 1) ... 2) ... 3) ...
RESULTADO: resuelto / escalado a N2 (motivo)
CAUSA RAÍZ: ...
SOLUCIÓN APLICADA: ...
TIEMPO INVERTIDO: 25 min
CONFIRMACIÓN DEL USUARIO: sí (hora)
```

### 12.3 Herramientas de ticketing

GLPI (muy usado en España y gratuito), Jira Service Management, ServiceNow, Freshservice/Freshdesk, Zendesk, osTicket. El concepto es el mismo en todas. Si dominas lo demás, monta GLPI en `LNX01` como extra para el CV.

### 12.4 Seguridad básica en soporte

- Verifica la identidad antes de resetear contraseñas o dar claves de recuperación.
- Nunca pidas contraseñas. Mínimo privilegio. Accede solo a los datos imprescindibles (RGPD).
- Phishing: no clicar → reportar → cambiar contraseña → aislar el equipo → **escalar a seguridad**.
- Bloquea tu sesión (`Win+L`) cuando te levantes.

### 12.5 Trato con el usuario: frases y preguntas que funcionan

- "Entiendo que no puedes trabajar; voy a ayudarte ahora mismo."
- "¿Qué estabas haciendo justo antes de que fallara?"
- "¿Te sale algún mensaje? ¿Me lo lees tal cual o me haces una captura?"
- "¿Le pasa también a algún compañero?" · "¿Ha cambiado algo hoy (actualización, contraseña, sitio)?"
- "Voy a probar esto; si no funciona, probamos lo otro."
- Cierre: "¿Puedes comprobar que ya funciona? Te dejo el ticket con lo que he hecho."
- Si no lo sabes: "Déjame comprobarlo y te digo algo en X minutos." **Nunca inventes.**
- Ante un usuario enfadado: escucha sin interrumpir → empatiza → no culpes → da un plazo realista → haz seguimiento.

---

## 13. Portafolio, CV y entrevistas

### 13.1 Portafolio: 3 mini-proyectos (solo documentación, sin código)

Formato: un PDF o un repositorio con `README.md` (te encaja: ya escribes en Markdown). Sin contraseñas ni datos personales.

1. **Dominio `empresa.local`:** AD + DNS + DHCP + GPO + carpetas con permisos por grupo. Incluye esquema de red (draw.io), tabla de IP, pasos, capturas y problemas encontrados.
2. **Runbook de 12 tickets:** tu versión de la sección 7 con capturas y comandos.
3. **Servidor Linux `LNX01`:** SSH, usuarios/grupos/permisos, Apache, logs y backup básico.

Extra: la documentación de las 10 averías de red (6.4). Cada proyecto: 1 página de resumen (objetivo, tecnologías, qué aprendí) + anexo con los pasos. Usa el **Prompt 12**.

### 13.2 CV de 1 página

| Bloque | Contenido |
|---|---|
| Cabecera | Nombre, zona, teléfono, correo, LinkedIn o enlace al portafolio |
| Perfil (2–3 líneas) | "Estudiante de 2º de ASIR con laboratorio propio de Active Directory, redes y soporte. Busco prácticas FCT/Dual en soporte IT o administración de sistemas. Disponibilidad: …" |
| Formación | ASIR (centro, curso) |
| Proyectos de laboratorio | 3 viñetas con verbo de acción + tecnologías + resultado. Ej.: "Monté un dominio Windows Server con 3 OU, 3 grupos y 3 usuarios; uní un cliente Windows 11, apliqué GPO y carpeta compartida con permisos NTFS por grupo (VirtualBox)." |
| Habilidades | Windows 10/11, Windows Server (AD DS, DNS, DHCP, GPO), Linux (Ubuntu), redes TCP/IP, VirtualBox, SQL básico, Microsoft 365 (básico), ticketing, PowerShell (básico) |
| Otros | Idiomas, carné/vehículo, disponibilidad horaria |

Reglas: máximo 1 página, en PDF (`Nombre_Apellido_CV_ASIR.pdf`). **Solo pon lo que puedas demostrar en pantalla en 2 minutos.** Prompt 13.

### 13.3 Mensaje corto para empresas o tutor

```text
Asunto: Prácticas FCT ASIR – [Nombre Apellido]

Hola [nombre / equipo de selección]:
Soy [Nombre], estudiante de 2º de ASIR en [centro]. Me interesa la oferta de [puesto] porque [una razón concreta sobre la empresa].
He montado un laboratorio propio con Windows Server (Active Directory, DNS, DHCP, GPO), clientes Windows 11 y un servidor Linux, y lo tengo documentado (adjunto/enlace).
Mi disponibilidad es [horario/fechas]. Quedo atento a una posible entrevista.
Un saludo,
[Nombre] · [teléfono] · [LinkedIn]
```

### 13.4 Preguntas de entrevista con respuesta corta

1. **Un usuario no puede iniciar sesión, ¿qué haces?** Verifico identidad, miro el mensaje exacto y en AD compruebo si la cuenta está bloqueada, caducada o deshabilitada. Desbloqueo o reseteo con cambio obligatorio al siguiente inicio, confirmo con el usuario y documento. Si se bloquea otra vez, busco la causa (credenciales guardadas, evento 4740).
2. **¿Diferencia entre DHCP y DNS?** DHCP asigna automáticamente la configuración IP; DNS traduce nombres a IP.
3. **¿Qué es Active Directory?** El servicio de directorio de Microsoft: centraliza usuarios, equipos, grupos y políticas; el controlador de dominio autentica.
4. **¿OU o grupo?** La OU organiza objetos y permite aplicar GPO y delegar; el grupo agrupa usuarios para asignar permisos.
5. **¿Qué es una GPO y cómo compruebo que se aplica?** Políticas para usuarios o equipos enlazadas a dominio u OU; uso `gpupdate /force` y `gpresult /r`.
6. **¿Cómo unes un equipo a un dominio?** Necesito Windows Pro/Enterprise, DNS apuntando al DC, conectividad y credenciales con permiso: `sysdm.cpl` → Cambiar → dominio → reiniciar; luego muevo el objeto a su OU.
7. **No tengo Internet, ¿qué compruebas?** La escalera del ping con `ipconfig /all`. 169.254 apunta a DHCP; si el ping a IP va y a nombre no, es DNS. Pregunto si afecta a más usuarios.
8. **¿Qué es una IP 169.254.x.x?** APIPA: el equipo no obtuvo IP por DHCP.
9. **¿Diferencia entre `ping` y `tracert`?** `ping` comprueba si llego y la latencia; `tracert` muestra el camino por saltos y dónde se corta.
10. **La impresora no imprime.** Alcance, estado físico, cola (spooler), conexión/IP, driver y, si hace falta, reañadirla.
11. **El PC va lento.** Administrador de tareas, espacio en disco, programas de inicio, malware, actualizaciones, `sfc`/`DISM`; si es hardware, escalo.
12. **¿Qué es una VPN?** Un túnel cifrado a la red de la empresa a través de una red no confiable.
13. **¿RAID 0, 1 y 5?** RAID 0 reparte sin redundancia; RAID 1 es espejo (tolera un fallo); RAID 5 usa paridad (mínimo 3 discos, tolera un fallo). RAID no es copia de seguridad.
14. **¿Regla 3-2-1?** 3 copias, en 2 soportes distintos, 1 fuera de sitio.
15. **¿Qué significa `chmod 755`?** Dueño lee, escribe y ejecuta; grupo y otros leen y ejecutan.
16. **¿Cómo reinicias un servicio en Linux y ves por qué falló?** `sudo systemctl restart X`, `systemctl status X` y `journalctl -u X -n 50`.
17. **¿Qué hace un `JOIN`? ¿Qué precaución con `UPDATE`/`DELETE`?** Une filas de dos tablas por una columna relacionada. Siempre `WHERE`, probar antes con `SELECT` y tener backup.
18. **¿Incidencia, petición, problema y cambio?** Algo que falla; algo que se solicita; causa raíz de varias incidencias; modificación planificada y aprobada.
19. **¿Qué es un SLA y cómo priorizas?** Acuerdo de tiempos de respuesta y resolución; prioridad = impacto × urgencia.
20. **¿Cuándo escalas?** Cuando excede mi alcance o permisos, el SLA está en riesgo, afecta a muchos usuarios o hay un tema de seguridad; escalo con el ticket completo.
21. **Un usuario enfadado.** Escucho sin interrumpir, empatizo, no culpo, doy un plazo realista y hago seguimiento.
22. **¿Y si no sabes la solución?** Busco en la base de conocimiento, pruebo en mi laboratorio, consulto a N2; no invento y aviso del plazo.
23. **¿Qué es MFA?** Un segundo factor además de la contraseña para reducir el riesgo si se roban credenciales.
24. **Un usuario ha pinchado en un phishing.** Le pido que no siga, aíslo el equipo si procede, cambio contraseñas, reporto a seguridad y escalo; no investigo por mi cuenta.
25. **Háblame de un proyecto de tu laboratorio (método STAR).** Situación: necesitaba practicar AD. Tarea: montar un dominio. Acción: pasos, y un problema real que resolví (por ejemplo el DNS del cliente). Resultado: cliente unido, GPO aplicada y todo documentado.
26. **¿Por qué esta empresa?** Investiga a qué se dedica, qué tecnología usa y conecta con tu laboratorio.

**Preguntas que puedes hacer tú:** ¿qué herramienta de tickets usan?, ¿cómo es un día típico de una persona en prácticas en el equipo?, ¿qué se espera que haya aprendido al terminar?

### 13.5 Certificaciones (después de tener prácticas o trabajo, no ahora)

- **CompTIA A+** (Core 1 `220-1201` + Core 2 `220-1202`): estándar de entrada. Core 1 cubre hardware, redes, móviles, virtualización/nube y resolución de problemas, y se recomienda ~12 meses de experiencia. Es de pago (cientos de euros por examen). Útil si apuntas a SPV o campo.
- **Microsoft:** fundamentos (Azure, seguridad, M365) y, con experiencia, **MD-102** (administrador de endpoints).
- **ITIL 4 Foundation:** vocabulario de gestión de servicios TI; muy visto en consultoras y outsourcing.
- **Gratis y útil ya:** Microsoft Learn y Cisco Skills for All (Networking Basics).

---

## 14. Suite de prompts (copiar y pegar)

**Cómo usarlos**

- Pega el **Prompt 0** al inicio de cada conversación nueva; después, el prompt del módulo que toque. Un prompt = una sesión de 30–60 minutos.
- Sustituye lo que esté entre `[corchetes]`.
- La IA puede equivocarse en nombres de menús o versiones. **Compruébalo en tu pantalla**; si no coincide, pégale el error o describe lo que ves y pide que corrija.
- Si la IA te da la solución antes de que lo intentes, dile: "No me des la respuesta; dame una pista".

| Nº | Prompt | Cuándo |
|---|---|---|
| 0 | Contexto base | Al empezar cada chat |
| 1 | Diagnóstico de nivel | Día 1 |
| 2 | Montar el laboratorio | Días 1–2 |
| 3 | Active Directory | Días 2–5 |
| 4 | Averías de red | Días 6–7 |
| 5 | Simulador de tickets | Días 5, 8, 9, 13 |
| 6 | Modo urgencias (explícame este error) | Siempre que algo falle |
| 7 | Microsoft 365 y SaaS | Día 10 |
| 8 | Linux por retos | Días 11–12 |
| 9 | SQL por niveles | Día 12 |
| 10 | Python mínimo | Si lo necesitas para aprobar |
| 11 | Hardware 101 | Si apuntas a SPV |
| 12 | Documentar el laboratorio | Día 13 |
| 13 | CV y LinkedIn | Hoy (versión inicial) y día 14 |
| 14 | Analizar una oferta | Antes de cada candidatura |
| 15 | Entrevista técnica | Día 14 y antes de cada entrevista |
| 16 | Entrevista de competencias | Día 14 |
| 17 | Repaso relámpago | Cada día, 10 min |
| 18 | Plan semanal | Cada domingo |
| 19 | Trabajo remoto | Si tu objetivo es remoto (ver 1.4) |

### Prompt 0 · Contexto base

```text
CONTEXTO (úsalo durante toda esta conversación):
- Soy estudiante de 2º de ASIR (España), principiante y oxidado: no recuerdo casi nada.
- Objetivo: conseguir prácticas FCT/Dual o un puesto de Soporte Helpdesk N1 / Operador de Sistemas Junior en las próximas semanas.
- Mi laboratorio: portátil con Zorin OS (host) y VirtualBox con tres VM: DC01 (Windows Server, dominio empresa.local, IP 192.168.50.10), PC-CLI01 (Windows 11 unido al dominio) y LNX01 (Ubuntu Server). Red interna labnet 192.168.50.0/24 más NAT.
- Tiempo disponible: 90–120 minutos al día.
- Reglas de enseñanza:
  1) Explícame como a un principiante, con analogías cortas. Si usas un término técnico, defínelo en una línea.
  2) Sin programación: solo comandos que pueda copiar, ejecutar y entender.
  3) Un bloque cada vez (máximo 6 pasos). Dime qué debo ver en pantalla al terminar cada paso y espera mi confirmación.
  4) Al final de cada bloque hazme 3 preguntas de comprobación y no avances hasta que responda.
  5) Si no estás seguro de un dato (versión, ruta de menú), dímelo en lugar de inventarlo.
  6) Responde siempre en español.
Confirma que lo has entendido con una sola línea y espera mi siguiente mensaje.
```

### Prompt 1 · Diagnóstico de nivel

```text
Actúa como un profesor de ASIR y un jefe de Helpdesk a la vez. Hazme un test diagnóstico de 15 preguntas, una a una, esperando mi respuesta, para saber qué recuerdo de: redes, Windows y Active Directory, Linux, SQL y soporte a usuarios. Empieza fácil y sube la dificultad.
No me des las respuestas hasta que haya contestado. Si digo "no sé", pasa a la siguiente sin juzgarme.
Al terminar: (1) una nota de 0 a 10 por bloque, (2) mis 5 huecos más graves, (3) cómo ajustar mi plan de 14 días: qué días puedo acelerar y cuáles debo duplicar.
```

### Prompt 2 · Montar el laboratorio

```text
Actúa como un técnico senior que me guía por videollamada para montar mi laboratorio en VirtualBox sobre Zorin OS.
Objetivo: 3 VM (DC01 con Windows Server, PC-CLI01 con Windows 11, LNX01 con Ubuntu Server), red interna labnet 192.168.50.0/24 y NAT.
Hazlo así:
1. Pregúntame primero: versión de VirtualBox instalada, si tengo Secure Boot activo y qué ISOs tengo ya descargadas.
2. Guíame VM por VM (empezando por DC01) con nombre, RAM, CPU, disco y adaptadores de red exactos.
3. Tras cada paso dime qué debería ver y cuáles son los errores típicos (módulo del kernel, TPM/EFI en Windows 11, DNS al unir al dominio, activación de la evaluación de Windows Server).
4. Cuando te pegue un error, dame: causa probable, acción exacta y cómo comprobar que quedó resuelto.
5. Termina con un checklist de verificación (ipconfig, nslookup, ping, whoami) y los nombres de los snapshots que debo crear.
```

### Prompt 3 · Active Directory

```text
Actúa como un administrador de sistemas senior que prepara a un becario para su primera semana en un Helpdesk. Vamos a trabajar Active Directory en mi laboratorio (dominio empresa.local).
Cubre, en este orden y de uno en uno:
(a) qué es un dominio, un controlador de dominio, una OU, un grupo y una GPO, explicado con la analogía de un edificio de oficinas;
(b) crear OU, usuarios y grupos;
(c) unir PC-CLI01 al dominio;
(d) tareas de helpdesk: resetear contraseña, desbloquear, deshabilitar, mover de OU y añadir a un grupo;
(e) una GPO sencilla y cómo verificarla con gpresult;
(f) una carpeta compartida con permisos NTFS por grupo.
Para cada punto: pasos en la interfaz gráfica (con la ruta exacta de menús), la versión en PowerShell (solo copiar/pegar, explicando cada parte), el error típico y una mini-prueba que yo pueda hacer.
Cierra cada bloque con 3 preguntas de entrevista sobre lo visto y corrígeme sin darme la respuesta antes de que conteste.
```

### Prompt 4 · Averías de red

```text
Actúa como mi jefe de Helpdesk y entrenador de redes. Necesito una "chuleta de supervivencia" y práctica real.
Parte 1: explícame con analogías IP, máscara, gateway, DNS, DHCP (DORA), NAT, puertos y APIPA (169.254.x.x), y enséñame la escalera del ping paso a paso.
Parte 2: dame una avería de red cada vez para provocar en mi laboratorio (DC01 y PC-CLI01), con instrucciones exactas para provocarla, SIN decirme el síntoma esperado ni la causa. Yo la diagnostico y te cuento qué comandos he usado y qué he visto.
Parte 3: evalúa mi diagnóstico (¿seguí un orden lógico?, ¿usé el comando adecuado?), explica la causa real y cómo la arreglaría un técnico senior. Después dame una avería algo más difícil.
Empieza por la Parte 1 y no pases a la 2 hasta que haya contestado 3 preguntas de comprobación. Recuérdame hacer snapshot antes de provocar cada avería.
```

### Prompt 5 · Simulador de tickets

```text
Actúa como un usuario de oficina poco técnico que llama al Helpdesk de su empresa. Inventa un ticket realista (uno cada vez) de esta lista: no puedo iniciar sesión, no hay Internet, la impresora no imprime, no accedo a una carpeta compartida, el PC va lento, Outlook no abre, pantalla azul, perfil temporal, relación de confianza fallida, BitLocker pide clave, la VPN no conecta, necesito instalar un programa.
Reglas: responde como lo haría una persona real (poca información, a veces nervioso). Solo me das la información que te pregunte. No me ayudes ni me des pistas.
Yo haré de técnico de nivel 1: te haré preguntas y te daré instrucciones. Cuando escriba RESUELTO o ESCALO, termina la simulación y evalúa mi actuación de 0 a 10 en: preguntas de diagnóstico, orden lógico, comunicación, seguridad (verificación de identidad) y documentación del ticket (pídeme que lo redacte).
Después enséñame cómo lo habría resuelto un técnico senior en menos de 10 líneas y lanza el siguiente ticket, algo más difícil.
```

### Prompt 6 · Modo urgencias (explícame este error)

```text
Actúa como un técnico senior de guardia. Voy a pegarte un mensaje de error, la salida de un comando o la descripción de una captura. Respóndeme siempre con este formato:
1) Qué significa, en cristiano (2 líneas).
2) Causas probables, de más a menos probable.
3) Pruebas en orden, de menos a más intrusiva, con el comando o la ruta exacta.
4) Cómo compruebo que está resuelto.
5) Cómo lo anoto en el ticket (síntoma, causa, solución).
Si necesitas más datos, pídemelos ANTES de proponer cambios arriesgados. Avísame cuando una acción pueda borrar datos o desconfigurar algo y recuérdame hacer un snapshot.
Mi error es: [pega aquí el mensaje o la salida del comando]
```

### Prompt 7 · Microsoft 365 y SaaS

```text
Actúa como administrador de Microsoft 365 que forma a un técnico junior. Explícame, con ejemplos de la vida diaria de un helpdesk: qué es SaaS, Microsoft Entra ID, Exchange Online, Teams, SharePoint/OneDrive, licencias, MFA, SSO y acceso condicional (solo concepto).
Después dame 12 tickets típicos de M365 (alta de usuario, reset de MFA, buzón compartido, lista de distribución, archivo borrado, Outlook que no sincroniza, baja de empleado, etc.). Para cada uno: dónde se resuelve, los pasos, y qué cambia si el usuario viene de un AD local sincronizado.
Termina con un mini-examen de 10 preguntas, una a una.
```

### Prompt 8 · Linux por retos

```text
Actúa como un sysadmin Linux paciente. Soy usuario de Zorin OS y quiero ser técnico de soporte, no programador.
Dame un reto práctico de 5 minutos cada vez: empezando por navegación y archivos, luego permisos, usuarios, servicios con systemctl, logs con journalctl y SSH a mi VM LNX01. Trabajaré en la carpeta ~/practica para no romper nada.
Para cada reto: enunciado, comando esperado (ocúltalo hasta que lo intente o te lo pida), cómo verificar el resultado y qué significa cada parte del comando.
Corrige mis salidas pegadas, avísame si un comando es peligroso y sube la dificultad solo cuando acierte 3 seguidos. Empieza con los 10 comandos imprescindibles.
```

### Prompt 9 · SQL por niveles

```text
Actúa como profesor de bases de datos para alguien que no quiere ser desarrollador pero necesita aprobar y defenderse en sistemas.
Usa MariaDB/MySQL. Dame un script que pueda copiar y pegar para crear una base "tienda" con las tablas departamentos, empleados y tickets, con datos de ejemplo.
Después, 20 ejercicios progresivos (SELECT/WHERE/ORDER BY → COUNT/GROUP BY → JOIN → INSERT/UPDATE/DELETE → usuarios y GRANT → mysqldump y restauración). Uno a uno: yo escribo mi consulta, tú me dices si es correcta, me explicas el error y, si fallo, me das una pista (no la solución).
Recuérdame siempre la regla: SELECT antes de UPDATE/DELETE y backup antes de tocar datos reales. Al final, 5 preguntas de entrevista sobre administración de bases de datos.
```

### Prompt 10 · Python mínimo

```text
Soy estudiante de ASIR, no quiero ser desarrollador, pero necesito aprobar Python y saber leer un script corto en un trabajo de sistemas.
Dame solo lo imprescindible: variables y tipos, print/input, if/elif/else, for/while, listas y diccionarios, funciones, leer ficheros y try/except.
Formato: un concepto por mensaje, con un ejemplo de 5–8 líneas relacionado con sistemas (contar líneas ERROR de un log, listar archivos de una carpeta, comprobar si un puerto responde…), explicado línea a línea. Después, un ejercicio en el que yo tenga que LEER código y decirte qué hace (no escribirlo) y otro en el que cambie una sola línea.
Al final, 10 ejercicios tipo examen con solución comentada y una lista de errores típicos de principiante.
```

### Prompt 11 · Hardware 101

```text
Actúa como un técnico de servicio post venta con 10 años de experiencia que forma a un junior. Dame un repaso de hardware para soporte: componentes y su función, RAM (DDR4/DDR5, SODIMM/DIMM), almacenamiento (HDD, SSD SATA, NVMe), fuentes de alimentación, conectores, BIOS/UEFI, RAID 0/1/5/10 y diagnóstico por descarte ("no enciende", "no da imagen", "pitidos", "va lento", "se reinicia").
Un tema por mensaje, con analogías. Incluye las normas de seguridad (descarga electrostática, desconectar corriente y batería).
Termina con 10 casos de diagnóstico: yo digo qué comprobaría y en qué orden, y tú me evalúas.
```

### Prompt 12 · Documentar el laboratorio

```text
Actúa como un compañero técnico y editor que me ayuda a documentar mis prácticas para mi portafolio. Te voy a pasar mis notas desordenadas (pasos, comandos, errores y soluciones).
Conviértelas en un documento claro con esta estructura: Objetivo · Esquema de red (tabla de IP y roles) · Requisitos · Pasos numerados (con comandos y comprobaciones) · Problemas encontrados y cómo los resolví · Cómo verificar que funciona · Qué aprendí · Mejoras futuras.
Reglas: no inventes pasos ni datos que yo no te haya contado; si falta algo, pregúntamelo antes. No incluyas contraseñas ni datos personales. Entrégalo en Markdown, con frases cortas y manteniendo una sola persona verbal (primera persona o infinitivo).
Mis notas son: [pega aquí tus notas]
```

### Prompt 13 · CV y LinkedIn

```text
Actúa como un reclutador técnico español especializado en perfiles junior de IT. Voy a pasarte mis datos y los proyectos de mi laboratorio. Quiero:
1) Un CV de 1 página para prácticas FCT/Dual y puestos de Helpdesk N1 (cabecera, perfil de 2–3 líneas, formación, proyectos de laboratorio con verbos de acción y tecnologías, habilidades, idiomas y disponibilidad).
2) El titular y el apartado "Acerca de" de LinkedIn (máximo 5 líneas).
3) Un mensaje de 5 líneas para enviar a una empresa o a mi tutor de FCT.
Reglas: solo lo que yo pueda demostrar en pantalla en 2 minutos; nada de relleno ni adjetivos vacíos; si algo suena dudoso o exagerado, márcalo y propón una versión honesta. Pídeme primero los datos que te falten, uno por uno.
```

### Prompt 14 · Analizar una oferta

```text
Actúa como mentor de empleabilidad IT. Te voy a pegar el texto completo de una oferta de trabajo o prácticas.
Dame: (1) una tabla de requisitos con las columnas "lo piden / yo lo tengo (según mi contexto) / qué hacer", marcando lo imprescindible frente a lo deseable; (2) las 5 preguntas técnicas que probablemente me harán; (3) un plan de estudio de 3 días ajustado a esa oferta usando mi laboratorio; (4) un mensaje de candidatura de 5 líneas personalizado.
No inventes requisitos que no estén en el texto. Si el texto es ambiguo, dímelo.
La oferta es: [pega aquí la oferta]
```

### Prompt 15 · Entrevista técnica

```text
Actúa como el responsable técnico de un equipo de soporte IT que me entrevista para unas prácticas FCT/Dual de ASIR. Entrevista de 30 minutos: haz UNA pregunta cada vez y espera mi respuesta.
Mezcla: Active Directory, redes y diagnóstico, Windows cliente, Linux básico, SQL básico, ticketing y casos prácticos ("un usuario te dice que…").
No me des pistas ni me corrijas durante la entrevista. Si mi respuesta es vaga, repregunta como lo haría un entrevistador real.
Al final: nota global de 0 a 10, tabla por área (fortaleza / mejorable), las 5 respuestas que más me costaron con la versión ideal en 3–4 líneas y qué debo repasar mañana.
```

### Prompt 16 · Entrevista de competencias

```text
Actúa como una persona de RR. HH. que entrevista a un candidato junior para un puesto de soporte IT. Haz una pregunta cada vez sobre: trabajo bajo presión, atención a un usuario enfadado, equivocarse y reconocerlo, aprender algo nuevo rápido, trabajo en equipo, organización de prioridades y por qué esta empresa.
Pídeme que conteste con el método STAR (Situación, Tarea, Acción, Resultado) usando ejemplos reales míos (clase, laboratorio, trabajos, voluntariado). Si no tengo ejemplo, ayúdame a encontrar uno a partir de mis experiencias antes de seguir.
Al final, evalúa mis respuestas en claridad, honestidad, concreción y tono, y reescribe la peor en una versión mejorada.
```

### Prompt 17 · Repaso relámpago

```text
Actúa como un examinador amable. Hazme un repaso de 10 minutos de lo estudiado en los últimos días (los temas son: [lista de temas]): 8 preguntas cortas, una a una, mezclando temas antiguos y recientes (repaso espaciado).
Formato: pregunta → mi respuesta → tu corrección en 2 líneas. Anota las que falle y repítelas al final. Termina con una lista "Repasar mañana" de máximo 5 puntos.
```

### Prompt 18 · Plan semanal

```text
Actúa como mi tutor de estudio. Estos son mis resultados de la semana (te los pego: qué hice, qué me costó, simulacros y notas): [pega aquí tus resultados].
Ajusta mi plan de la semana siguiente SIN añadir carga: dime qué simplificar, qué repetir y qué eliminar, cuántas horas dedicar a cada bloque y cuántas candidaturas enviar. Dame un plan día a día de 90–120 minutos y un "mínimo viable" por si un día voy mal de tiempo.
```

### Prompt 19 · Trabajo remoto

```text
Actúa como el responsable de un equipo de soporte IT 100 % remoto que entrevista y forma a un junior de ASIR. Quiero prepararme para trabajar a distancia. Hazlo de uno en uno y espera mi respuesta en cada paso:
1) Revisa mi puesto de trabajo en casa con una lista de comprobación (conexión, auriculares, cámara, sitio, plan B de conexión, seguridad) y dime qué me falta.
2) Simula 5 situaciones de soporte por chat o llamada en las que no puedo tocar el equipo del usuario: yo te hago preguntas y te doy instrucciones; tú respondes como un usuario poco técnico, sin ayudarme. Al terminar cada una, puntúame de 0 a 10 en claridad de instrucciones, paciencia, verificación de identidad y documentación.
3) Hazme 8 preguntas de entrevista propias del trabajo remoto (autonomía, organización, comunicación escrita, qué hago si me bloqueo, cómo pido ayuda sin agobiar, seguridad en casa, disponibilidad horaria).
4) Dame una plantilla corta de ticket y de mensaje de seguimiento para trabajar a distancia.
5) Enumera las señales de una oferta falsa o estafa de "trabajo/prácticas remotas".
Corrígeme con franqueza y sin darme la respuesta antes de que conteste. Al final, un plan de 3 días para mejorar.
```

### Mini-prompts de una línea

- `Explícame [tema] en 5 líneas y con una analogía.`
- `Dame una chuleta de 10 líneas sobre [tema] para tener a mano en una entrevista.`
- `Ponme 5 preguntas tipo entrevista sobre [tema] y corrígeme una a una.`
- `Revisa mi respuesta a esta pregunta de entrevista y reescríbela más corta y concreta: [respuesta].`
- `Tengo este ticket: [descripción]. ¿Qué preguntaría un técnico senior y en qué orden?`
- `Resume esta práctica en 5 viñetas para mi CV, sin exagerar: [notas].`

---

## 15. Recursos y fuentes

### 15.1 Recursos priorizados

| Bloque | Recurso | Para qué y notas |
|---|---|---|
| Laboratorio | [VirtualBox](https://www.virtualbox.org/wiki/Downloads) | Instala 7.2.8 o superior por tu kernel 7.0. |
| Laboratorio | [Microsoft Evaluation Center](https://www.microsoft.com/evalcenter) | Windows Server (180 días) y Windows 11 Enterprise (90 días). |
| Laboratorio | [Ubuntu Server](https://ubuntu.com/download/server) | Última LTS. |
| AD y Windows | [Microsoft Learn (español)](https://learn.microsoft.com/es-es/training/) | Busca "Active Directory Domain Services" y "Windows Server". |
| AD y Windows | TryHackMe: *Windows Fundamentals* y *Active Directory Basics* | **Revisa antes si son gratis**: cuando lo comprobé, la sala *Active Directory Basics* figuraba solo para suscriptores de pago, aunque otra guía de TryHackMe la lista entre las gratuitas. Tu laboratorio cubre lo mismo. |
| AD y Windows | YouTube | Busca "Windows Server 2025 Active Directory desde cero" (o 2022) y ordena por popularidad; practica a la vez en tu laboratorio. |
| Redes | [Cisco Skills for All](https://skillsforall.com/) | Curso gratuito *Networking Basics*. |
| Redes / A+ | [Professor Messer](https://www.professormesser.com/) | Vídeos gratuitos en inglés (te sirve para inglés técnico). |
| Linux | [Linux Journey](https://linuxjourney.com/) | Módulos interactivos. |
| Linux | [OverTheWire Bandit](https://overthewire.org/wargames/bandit/) | Práctica real de terminal por SSH. |
| Linux | [Killercoda](https://killercoda.com/) | Entornos Linux en el navegador. |
| SQL | [SQLZoo](https://sqlzoo.net/) y [SQLBolt](https://sqlbolt.com/) | Práctica interactiva de consultas. |
| Python | [W3Schools Python](https://www.w3schools.com/python/) | Referencia rápida de sintaxis. |
| Documentación | [draw.io](https://www.drawio.com/) | Esquemas de red para tu portafolio. |
| Ticketing (extra) | [GLPI](https://glpi-project.org/) | Para montar un helpdesk de práctica. |
| Certificaciones | [CompTIA A+](https://www.comptia.org/en-us/certifications/a/) | Solo cuando tengas prácticas o trabajo. |

### 15.2 Datos verificados para esta guía (octubre de 2026)

- VirtualBox 7.2.8 añade soporte inicial para kernels Linux 6.19 y 7.0: [Linuxiac](https://linuxiac.com/virtualbox-7-2-8-released-with-linux-kernel-7-0-support/).
- Windows Server 2025 en evaluación: 180 días y activación en línea durante los primeros 10 días: [Microsoft Evaluation Center](https://www.microsoft.com/evalcenter/download-windows-server-2025).
- Windows 11 Enterprise en evaluación (90 días): [Microsoft Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-11-enterprise) e [IT-Connect](https://www.it-connect.tech/windows-11-26h2-how-to-download-the-evaluation-iso-image/).
- Ampliación del ESU de Windows 10 hasta el 12/10/2027 (consumo): [Pureinfotech](https://pureinfotech.com/windows-10-esu-extended-2027-microsoft-update/). Fechas de ESU en empresas: [Microsoft Q&A](https://learn.microsoft.com/en-us/answers/a/12637085).
- Fin de soporte de Windows Server 2016 el 12/01/2027: [Windows Central vía Yahoo](https://tech.yahoo.com/computing/articles/microsoft-preps-esu-program-windows-120100921.html).
- Dominios del examen CompTIA A+ Core 1 (220-1201): [Global Knowledge](https://www.globalknowledge.com/en-be/products/comptia/220-1201ra).
- Estado de la sala TryHackMe *Active Directory Basics*: [página de la sala](https://tryhackme.com/r/room/winadbasics) y [guía de salas gratuitas](https://tryhackme.com/resources/blog/free-red-teaming-training-on-tryhackme-to-build-your-skills-in-2026).

---

## 16. Checklists finales

### Checklist diaria

- [ ] Cargador conectado, perfil de energía equilibrado/rendimiento y VM con snapshot al empezar.
- [ ] 10 min de repaso (Prompt 17).
- [ ] 60–80 min de práctica en el laboratorio (no solo leer).
- [ ] 10–20 min documentando lo hecho (capturas + pasos + errores).
- [ ] Snapshot al terminar un hito.
- [ ] 2–3 candidaturas enviadas o seguimiento de las anteriores.

### Checklist semanal

- [ ] Hecho el Prompt 18 y ajustado el plan.
- [ ] Un simulacro de tickets (Prompt 5) y otro de entrevista (Prompt 15 o 16).
- [ ] Copia de seguridad de las VM importantes (`.ova`) y de la documentación.
- [ ] Perfil de la plataforma de empleo actualizado con los conocimientos nuevos que ya puedes demostrar.

### Antes de una entrevista

- [ ] He leído la oferta con el Prompt 14 y sé qué me van a preguntar.
- [ ] He investigado a qué se dedica la empresa y qué tecnología usa.
- [ ] Laboratorio arrancado y funcionando, listo para **enseñarlo en pantalla**.
- [ ] Sé explicar sin pensar: DHCP vs DNS, la escalera del ping, AD/OU/GPO y cómo resuelvo "cuenta bloqueada".
- [ ] Tengo 3 preguntas para ellos y un ejemplo STAR preparado.
- [ ] Puntualidad, cámara y conexión probadas si es remota.

### "Estoy listo" cuando puedo…

- [ ] Montar un dominio desde cero en menos de 60 minutos.
- [ ] Resolver una cuenta bloqueada o una contraseña en 2 minutos.
- [ ] Diagnosticar una avería de red con la escalera en 3 minutos.
- [ ] Explicar el procedimiento de los 12 tickets.
- [ ] Usar 15 comandos de Linux y escribir 10 consultas SQL.
- [ ] Sacar 7/10 o más en dos simulacros de entrevista.
- [ ] Enseñar un CV de 1 página y 3 proyectos documentados.
- [ ] Haber enviado al menos 10 candidaturas.

---

> **La meta no es saberlo todo.** Es poder decir en una entrevista: *"Lo he hecho; te lo enseño."*
>
> *Documento orientativo: no garantiza una contratación. Comprueba siempre los requisitos y las fechas de cada oferta.*

