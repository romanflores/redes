El **servidor HTTP Apache** se gestiona a través de comandos que ejecutaremos en la terminal. De momento, no exsite una interfaz gráfica nativa para hacerlo, aunque podemos encontrar en este sentido algunos desarrollos de terceros como [Webmin](http://www.webmin.com/) o [Ajenti](http://ajenti.org/), entre otros. 

Por otro lado, **PHP** debe gestionarse instalando algún que otro módulo (según nuestras necesidades) y modificando sus archivos de configuración.

Finalmente, la base de datos **MySQL** o **MariaDB** puede gestionarse a través de la terminal de comandos, o bien, a través de aplicaciones como [phpMyAdmin](https://www.phpmyadmin.net/) o [DBeaver](http://dbeaver.jkiss.org/) entre otras.

!!!done "Archivos y directorio de configuración"
	Para gestionar efectivamente un servidor LAMP es imprescindible conocer la ubicación de los archivos y carpetas de configuración, ya que facilitará enormente nuestro trabajo. 

## Apache
A continuación se listan directorios y archivos de configuración así como los comandos para gestionarlo desde la terminal. 

### Archivos y carpetas importantes

Una vez instalado el servidor web Apache se crea una estructura archivos y directorios, entre los que se destacan: 

| Directorio o archivo     | Descripción          |
| ---------------------- | --------------------------------------- |
| `/etc/apache2/apache.conf`     | Archivo de configuración general de Apache|
| `/etc/apache2/sites-available` | Directorio donde se alojan los archivos de configuración de los sitios  definidos pero aún no activos (es decir, no habilitados|
| `/etc/apache2/sites-enabled`     | Directorio donde se alojan los archivos de configuración de los sitios  activos o habilitados|
| `/etc/apache2/mods-available` | Directorio donde se alojan los módulos de Apache aún no activos (es decir, no habilitados|
| `/etc/apache2/mods-enabled`     | Directorio donde se alojan los módulos de Apache activos o habilitados|
| `/var/www/html`| Directorio por del sitio web por defecto, donde Apache aloja las páginas web|
| `/home/usuario/public_html`| Directorio donde se aloja el sitio web personal de cada usuario del sistema|


Una vez finalizada la instalación, el servidor web Apache se iniciará automáticamente. Podemos verificarlo, ejecutando el siguiente comando: 

```bash
sudo systemctl status apache2
```

Podemos comprobar la configuración de Apache para verificar si existen errores en su configuración:

```bash
sudo apache2ctl configtest
```

Donde obtendremos un error similar a:
```bash
Set the 'ServerName' directive globally to suppress this message 
Syntax OK
```
Para corregir esto, abrimos el archivo de configuración principal de Apache con nuestro editor de texto:

```bash
sudo nano /etc/apache2/apache2.conf
```
Y agregamos al final del archivo la directiva `ServerName`, seguida del **nombre de dominio** o **dirección IP** de nuestro servidor web. Es decir: 

```apache
ServerName dominio_del_servidor_o_IP 
```
Guardamos y cerramos el archivo. Luego, para verificar que todo está bien (es decir, que no hay errores de sintaxis en el archivo de configuración de Apache):

```bash
sudo apache2ctl configtest
```
Y como definimos la directiva global `ServerName`, veremos la siguiente salida: 

```apache
Output
Syntax OK
```

Por último, reiniciamos Apache para implementar los cambios:
```bash
sudo systemctl restart apache2
```


##Inicio y parada del servidor

Existen diversos comandos para gestionar el servidor web Apache. 

**Detener el servidor**
```bash
sudo systemctl stop apache2
```

**Iniciar el servidor**
```bash
sudo systemctl start apache2
```

**Reiniciar el servidor**
```bash
sudo systemctl restart apache2
```

**Recargar la configuración del servidor (sin reiniciar)**
```bash
sudo systemctl reload apache2
```
