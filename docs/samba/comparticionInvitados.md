Por último, si necesitamos que **cualquier usuario de la red (incluso si no es un usuario Samba) pueda acceder as una carpeta compartida**, daremos los siguientes pasos: 

Primeramente tendremos que crear la carpeta a compartir: 

```apache
mkdir -p /home/compartir/anonimo/
```

Luego, modificar la propiedad de la carpeta: 
```apache
chown -R root:users /home/compartir/anonimo/ 
```

Y los permisos:  
```apache
chmod -R ug+rwx,o+rx-w /home/compartir/anonimo/ 
```
Por último, tendremos que agregar al archivo de configuración principal de Samba (`/etc/samba/smb.conf`) el siguiente bloque de código: 

```apache
[anonimo]

	# Carpeta a compartir
	path = /home/compartir/anonimo
	
	# Grupo de usuarios
	force group = users

	# Máscara de permisos con la que se crearán los archivos 
	create mask = 0660

	# Máscara de permisos con la que se crearán las carpetas
	directory mask = 0771

	# ¿La carpeta será visible por el resto de los usuarios?
	browsable = yes

	# ¿Se puede escribir dentro de la carpeta?
	writable = yes

	# ¿Se permite el acceso anónimo?
	guest ok = yes
```

!!!warning "Atención"
		Cualquier usuario del sistema Windows podrá leer y escribir en esta carpeta, aún cuando no posea una contraseña para el inicio de sesión en Windows ni esté registrado en el servidor Samba.  