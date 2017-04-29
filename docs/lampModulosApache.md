El servidor web Apache contiene diversos módulos que proveen al servidor de funcionalidades extra. La mayoría de ellos están deshabilitados por defecto. 

##Gestionando módulos

La sintáxis básica para tabajar con módulos es la siguiente: 

```bash
sudo a2[en|dis]mod nombreDelModulo
```

Donde: 

| Sistema operativo      | Ubicación del archivo _hosts_           |
| ---------------------- | --------------------------------------- |
|`a2`                    | Inicio del comando de Apache2           |
|`en` 					 | _Enable_ es decir, habilitar el sitio web|
|`dis`     				 | _Disable_, es decir, deshabilitar el sitio web|
| `mod`                	 | Simboliza el concepto de _módulo_       |
| `nombreDelModulo`   	 | Nombre del modulo que deseamos habilitar o deshabilitar|


Por ejemplo, la siguiente acción habilitará el módulo `userdir`:

```bash
sudo a2enmod userdir
```

En otras palabras, creará un [enlace simbólico](https://es.wikipedia.org/wiki/Enlace_simb%C3%B3lico) del módulo `userdir` desde la carpeta  `/etc/apache2/mods-available` hacia la carpeta `/etc/apache2/mods-enabled`.


