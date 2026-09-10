Linux es el sistema operativo más utilizado en los servidores con un 96,3% de participación de mercado. La mayoría de las herramientas de hacking son construidas para Linux, y si estás aprendiendo a programar, en algún momento vas a tener que aprender Linux, ya que lo más probable es que tus aplicaciones las termines montando en un servidor Linux

linux un SO al igual que Windows, MAC OS, Android, IOS. Los sistemas operativos se componen de dos partes:
1. Las aplicaciones: Como el explorador de archivos, un explorador web, una terminal o un editor de texto.
2.  El kernel: se encarga de comunicarse con el hardware (la parte física del computador, memoria RAM, CPU, la tarjeta gráfica, etc.).
Cuando tu quieres usar una app, esta se va acomunicar con el kernel y el kernel se va a encargar de comunicarse con el hardware físico algo así como : 
- Oye hardware fśicio me puedes dar un pcoo de CPU y memoria RAM para que use esta app que quiero ejecurar.

Popularmente se le llama "Linux" al sistema operativo completo. Sin embargo, Linux es estrictamente el nombre del kernel, te tratarán de corregir porque Linux es el nombre del kernel

Historia y origen:
- En el comienzo, **Richard Stallman** quería construir herramientas que fuesen de código libre construyó muchas aplicaciones dentro de esta capa en un proyecto llamado GNU , que consta de muchas apps q son de código libre tmb llamado código abierto
- Richard para poder crear un SO completo él tmb necesitaba un kernel, y en ese momento Richard concoció a Linux Torvald, quién estaba creando un kernel de código abierto , y entre los 2 se juntaron y crearon un proyecti llamdo GNU linux
- En la actualidad esto ha cambiado , puedes estar usando muchasapps que pertenecen al proyecto GNU , y tmb otras que no , en conjunto con el kernel de Linux, para poder crearte tú tu propio SO. 
- A estos SOs que usan Linux como su kernel se les concoe como Distribuiones o Sabores de Linux
	- Entonces nosotros podemos tomar un grupo de apps A + el kernel de Linux, y así crear una distribución 
	- EN otro lado tenemos un grupo de apps las B y las vamos ajuntar tmb con el kernel de Linux y crearíamos otra distribución bajo el nomer de por ejemplo chanchito Feliz
- Distribuiones más usadas: Debian, Fedora, Ubunut, Linux Mint
- Y si te gusta el hacking : kali linux, Parrot OS, 
- Para nuestro curso usaremos Ubuntu mantenida por Canonical
- Con código libre puedes hacer lo que quieras, modificarlo, redistribuirlo , etc

Empresas que mantienen distribuciones:Canonical (Ubuntu), Oracle (Oracle Linux/Solaris), Novell (SUSE) 

El **kernel** (o _núcleo_) es el **traductor y jefe de tráfico** dentro de tu computadora o teléfono.

Es el programa principal que se encarga de conectar las **aplicaciones** (como WhatsApp, Google Chrome o un juego) con el **hardware físico** (la pantalla, el procesador, la memoria RAM o la cámara).

### Un ejemplo sencillo: El Restaurante

Imagínate que tu computadora es un restaurante:

1. **Las Aplicaciones (los Clientes):** Tienen hambre y quieren cosas (ej. _"quiero tomar una foto"_, _"quiero reproducir un sonido"_).
    
2. **El Hardware (los Cocineros):** Es la capacidad real del equipo (la cámara, los altavoces, el procesador). Los cocineros solo hablan un idioma técnico muy complejo y no pueden atender directamente a los clientes.
    
3. **El KERNEL (el Mesero / Mesera):**
    
    - Toma el pedido de la aplicación.
        
    - Va a la cocina (hardware) y les dice: _"Oigan, denme un poco de memoria RAM y usen el lente de la cámara para tomar esta foto"_.
        
    - Recibe el resultado y se lo entrega de vuelta a la aplicación.
        

### ¿Por qué existe y por qué es tan importante?

Sin el kernel, **cada aplicación tendría que saber exactamente cómo funciona la marca y modelo de tu procesador, tu memoria o tu tarjeta gráfica**, lo cual sería imposible para los programadores.

El kernel se encarga de tres tareas críticas:

- **Repartir el trabajo (Administrar el Procesador):** Decide qué programa se ejecuta primero y cuánto tiempo usa el procesador para que la computadora no se trabe.
    
- **Repartir la memoria (Administrar la RAM):** Le asigna a cada app su propio espacio de memoria y evita que una app invada o borre la información de otra.
    
- **Controlar los dispositivos (Hardware):** Gestiona el teclado, el mouse, la red Wi-Fi, la pantalla, etc.