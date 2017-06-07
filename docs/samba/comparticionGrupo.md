En otras ocasiones, tal vez resulte práctico **compartir una carpeta entre los usuarios que pertenecen a un grupo determinado**. 

Para ello, creamos la carpeta a compartir: 
```apache
mkdir -p /home/compartir/usuarios
```

Modificamos el propietario de dicha carpeta: 

```apache
chown -R root:users /home/compartir/usuarios/
```

Y finalmente, modificamos los permisos de la carpeta: 
```apache
chmod -R ug+rwx,o+rx-w /home/compartir/usuarios/
```

La carpeta usuarios es accesible y escribible por todos los miembros del grupo `users`. Agregamos la siguiente línea al final del archivo de configuración de Samba `/etc/samba/smb.conf`:

```apache

[usuarios]
	# Comentario
	comment = Carpeta compartida entre todos los usuarios

	# Carpeta a compartir
	path = /home/compartir/usuarios

	# Todos los usuarios pertenecientes al grupo users
	valid users = @users

	# Grupo al que pertenecen los usuarios
	force group = users

	# Máscara de permisos con la que se crearán los archivos
	create mask = 0660

	# Máscara de permisos con la que se crearán las carpetas
	directory mask = 0771

	# ¿Se puede escribir dentro de la carpeta?
	writable = yes
```

!!!tip "Usuarios"
		El la directiva `valid users` también podríamos haber indicado solo un nombre de usuario o varios, se parados por comas (p.e. force users = juan, pedro, jorge). Lo mismo vale para la directiva `force group`, pero para los grupos. 
