Antes que nada hay que decir que **las opciones de configuración de Samba exceden ampliamente los alcances de esta guía**. En los ejemplos dados a continuación se explica como: 

  * Dotar a cada usuario del sistema de su propia carpeta almacenada en el servidor
  * Compartir una carpeta entre los usuarios del sistema
  * Compartir una carpeta de manera anónima en la red


## Modificando el archivo de configuración de Samba

```apache
sudo nano /etc/samba/smb.conf
```

Y procedemos al incluir los datos de configuración del servidor:

```apache
[global]
	# Grupo de trabajo
	workgroup = WORKGROUP

	# Nombre visible del servidor en la red
	server string = Servidor Samba %v en %L

	# Nombre corto del servidor en la red NetBIOS
	netbios name = debian

	# Un usuario válido deberá iniciar sesión para 
	# poder acceder a los recursos compartidos.
	security = user

	# Comportamiento del servidor en caso del ingreso de no usuarios. 
	# En este caso, será anónimo.
	map to guest = bad user

	# Descativar servidor de nombres. 
	# Sólo útil si Samba actúa como servidor Wins.  
	dns proxy = no

```


!!!done "Grupo de trabajo"
		Reemplazar **WORKGROUP** por el nombre de **grupo de trabajo** de los clientes **Windows**. Si no conocés el nombre de trabajo en el que se encuentra un cliente, ejecutá en la terminal de Windows (cmd):

		```apache
		net config workstation
		```
