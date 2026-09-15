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


