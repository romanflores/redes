Es posible que necesitamos que **cada usuario del sistema sea capaz de leer y escribir en su directorio de trabajo vía **Samba**, según el siguiente esquema: 

<br />
![Directorios para cada usuario](imgSamba/sambaejemplo.png)

Para ello agregamos al archivo de configuración `/etc/samba/smb.conf` debajo del bloque `[global]`:

```apache
[homes]
	# Comentario
	comment = Carpeta personal de cada usuario
	
	# ¿La carpeta será visible por el resto de los usuarios?
	browseable = no

	# %S es reemplazado por el nombre del usuario actual
	valid users = %S

	# ¿Se puede escribir dentro de la carpeta?
	writable = yes

	# Máscara de permisos con la que se crearán los archivos	
	create mask = 0700

	# Máscara de permisos con la que se crearán las carpetas
	directory mask = 0700
```

Luego, reiniciamos Samba (lo haremos cada vez que modifiquemos el archivo de configuración):

```apache
sudo service samba restart
```

