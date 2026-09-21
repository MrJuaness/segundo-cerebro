Para instalar Visual Studio Code en Zorin OS de forma rápida y segura, la mejor opción es usar el archivo oficial `.deb`.

**1.Descargar el instalador .deb:**Navegador web.

Ingresa al sitio oficial [code.visualstudio.com](https://code.visualstudio.com/?utm_source=gemini) y haz clic en la opción de descarga **.deb** (destinada a Debian/Ubuntu).

_Verificación:_ Abre la carpeta `Descargas` en tu explorador de archivos y confirma que exista un archivo similar a `code_1.xx.x_amd64.deb`.

**2.Instalar el paquete:**Terminal.

Abre la terminal presionando `Ctrl` + `Alt` + `T` e introduce el siguiente comando:
Bash
```
sudo apt install ./code_1.138.0-1789458761_amd64.deb
```
Ingresa tu contraseña cuando el sistema la solicite y presiona `Enter` para confirmar.
![[Captura desde 2026-09-18 22-50-30.png]]
Selecciona **`<Sí>`** y presiona la tecla **Enter**.

Esto agregará el repositorio oficial de Microsoft a tu sistema, lo que permitirá que Visual Studio Code se actualice automáticamente cada vez que actualices Zorin OS.

Verificación:_ Al presionar **Enter**, la ventana morada desaparecerá y la terminal terminará el proceso de instalación mostrando nuevamente la línea de comandos `admin-net@lab-sec:~/Descargas$`

_Verificación:_ La instalación habrá finalizado correctamente cuando la terminal vuelva a mostrar la línea de comandos sin devolver mensajes de error.

**3.Ejecutar Visual Studio Code:**Menú o Terminal.

Abre el menú de aplicaciones de Zorin OS y busca **Visual Studio Code**, o escribe `code` dentro de la terminal y presiona `Enter`.

_Verificación:_ Se abrirá la interfaz gráfica principal de Visual Studio Code.




















































![[Pasted image 20260918224236.png]]
Debes hacer clic en el botón de la izquierda: **Download for Linux (.deb)**.

Zorin OS está basado en Ubuntu/Debian, por lo que utiliza paquetes en formato `.deb`.

_Verificación:_ Al presionar ese botón, la descarga se iniciará automáticamente y obtendrás un archivo con extensión `.deb` en tu carpeta de Descargas.