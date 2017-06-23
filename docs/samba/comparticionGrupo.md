En otras ocasiones, tal vez resulte práctico **compartir una carpeta entre los usuarios que pertenecen a un grupo determinado**. 

Para ello, creamos la carpeta a compartir: 
```apache
mkdir -p carpetaCompartida
```

Modificamos el usuario y grupo propietario de dicha carpeta: 

```apache
chown -R usuario:grupo carpetaCompartida
```
Donde `usuario` es el **usuario dueño** de la carpeta compartida (generalmente es el usuario `root`) y `grupo` es el **grupo de usuarios** al que deseamos dar permiso sobre la carpeta compardida. 

Y finalmente, modificamos los permisos de la carpeta: 
```apache
chmod -R ug+rwx,o+rx-w carpetaCompartida
```
O, lo que es lo mismo: 

```apache
chmod -R 775 carpetaCompartida
```


En el siguiente ejemplo, se comparte una carpeta llamada **ventas** que será accesible y escribible por todos los miembros del grupo **facturacion** (el bloque siguiente de código se deberá agregar en el archivo `/etc/samba/smb.conf`):

```apache

[ventas]
	# Comentario
	comment = Carpeta compartida entre los usuarios del grupo facturacion

	# Carpeta a compartir
	path = /opt/ventas

	# Damos permiso de acceso a todos los usuarios 
	# pertenecientes al grupo llamado "facturacion"
	valid users = @facturacion

	# Fuerza el grupo con permisos de acceso
	force group = facturacion

	# ¿Se puede escribir dentro de la carpeta?
	writable = yes

	# ¿La carpeta será visible por el resto de los usuarios?
	browseable = no
```

!!!tip "Usuarios"
		El la directiva `valid users` podríamos haber indicado el nombre de uno o varios usuarios:

		`force users = juan, pedro, jorge`

		O incluir los usuarios pertenecientes a distintos grupos: 

		`force users = @ventas, @facturacion`

		Lo indicado vale también para la directiva `force group` que es para los grupos. 

Rreiniciamos Samba para que el servidor haga efectivos los cambios:

```apache
sudo service smbd restart
```