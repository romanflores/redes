Es posible crear un **espacio web para cada usuario del sistema**, donde éstos pueden alojar su propio contenido web. Para hacerlo, seguimos las siguientes instrucciones: 

## Creando el contenido del sitio web


En primer lugar, creamos el directorio en el cual se agregarán las páginas webs del usuario:

```bash
mkdir /home/usuario/public_html
```

!!! note "Usuarios"
	En los ejemplos listados en esta página deberás cambiar **usuario** por el nombre de usuario al que deseemos dotar de un espacio web.

Solo resta agregar **"las páginas webs"** dentro de la carpeta `public_html` que acabamos de crear (debe existir necesariamente un archivo llamado index.html o index.php) 

## Habilitando el módulo userdir

Para permitir que los usuarios posean su propio sitio web aún resta un paso: la habilitación del módulo de Apache correspondiente. Entre los distintos módulos de Apache, quien cumple con nuestro cometido es el módulo llamado `userdir`. Para habilitar dicho módulo, ejecutamos en la terminal: 

```bash
sudo a2enmod userdir
```

Luego, reiniciamos el servidor para que incorpore los cambios:

```bash
sudo systemctl restart apache2
```

## Habilitando el módulo php7.0

En caso de querer ejecutar **PHP** en las webs personales de los usuarios tendremos que instalar el módulo correspondiente:  

```bash
sudo apt-get install libapache2-mod-php7.0
```

Acto seguido, habilitamos el módulo: 

```bash
sudo a2enmod php7.0
```

Por último, debemos permitir la ejecucción de scripts PHP dentro de directorio `home` de los usuarios. Para ello, abrimos el archivo:

```bash
nano /etc/apache2/mods-available/php5.conf
```

Un vez abierto el archivo, tenemos que modificar el siguiente bloque de código (casi al final del archivo):

```apache
<IfModule mod_userdir.c>
    <Directory /home/*/public_html>
        php_admin_flag engine Off
    </Directory>
</IfModule>
```
De manera que quede así: 

```apache
<IfModule mod_userdir.c>
    <Directory /home/*/public_html>
        php_admin_flag engine On
    </Directory>
</IfModule>
```

Para hacer efectivos los cambios realizados, reiniciamos Apache: 

```bash
sudo systemctl restart apache2
```

## Aceso a la web del usuario

Una vez concluidos los pasos anteriores, podemos acceder a la web del usuario escribiendo en el navegador `http://nombreDominioServidor/~usuario` o `http://direccionIPServidor/~usuario`