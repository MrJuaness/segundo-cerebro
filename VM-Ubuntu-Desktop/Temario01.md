### Dónde estoy y qué hay
==pwd== **print working directory** imprime tu ruta actual
==ls== lista lo q hay dentro
	ls -a TODO, incluido ocultos (los q empeizan por .)
	ls -l  formato largo  (perimisos, dueño,tamaño,fecha)
	ls -al combina las 2 anteriores
##### ==USAR SIEMPRE TAB para MENOS ERRORES==
### Anatomía de "ls -al"
- ![[permisos.png]]
==**Explicación**==
	 **Directorio privado**: **`snap`** --> drwx------ 6 usuario1 usuario1
		**Tipo (`d`):** Es una carpeta.
		**Propietario `usuario1` (`rwx`):** Tienes control total (leer contenido, crear/borrar archivos y entrar).
		**Grupo `usuario1` (`---`):** Ningún acceso.
		**Otros (`---`):** Ningún acceso.
		**Número de enlaces (6):** Indica que dentro de `snap` hay **4 subcarpetas** (aplicando la regla: $6 - 2 = 4$).
	**Archivo de configuración:`.profile`** -rw-r--r-- 1 usuario1 usuario1
		**Tipo (`-`):** Es un archivo normal (oculto por empezar con punto).
		**Propietario `usuario1` (`rw-`):** Puedes leerlo y editarlo.
		**Grupo `usuario1` (`r--`):** Los miembros del grupo solo pueden leerlo.
		**Otros (`r--`):** Cualquier otra persona en el sistema solo puede leerlo.
		**Número de enlaces (1):** Es el archivo físico estándar.
	**Carpeta superior del sistema: `..`** drwxr-xr-x 3 root root
		**Tipo (`d`):** Es un directorio (en este caso representa la carpeta anterior o "padre", `/home`).
		**Propietario `root` (`rwx`):** Pertenece al administrador del sistema (`root`), quien tiene acceso total.
		**Grupo `root` (`r-x`):** Puede ver qué hay dentro y entrar, pero no modificar nada.
		**Otros (`r-x`):** Tu usuario cae en esta categoría para esta carpeta. Puedes ver su contenido y navegar por ella, pero no puedes crear ni borrar elementos allí.
		**Número de enlaces (`2`):** Si aplicamos la regla mágica ($2 - 2 = 0$), nos dice que la carpeta `Desktop` **está totalmente vacía** de subcarpetas en este momento.
		
	**carpeta de usuario: `Desktop`** drwxr-xr-x 2 usuario1 usuario1 4096 Sep 14 11:48 Desktop
		
	


