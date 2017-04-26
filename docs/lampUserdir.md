Es posible crear un **espacio web para cada usuario del sistema**, donde éstos pueden alojar su propio contenido web. Para hacerlo, seguimos las siguientes instrucciones: 

##Creando el contenido del sitio web


En primer lugar, creamos el directorio en el cual se agregarán las páginas webs del usuario:

```bash
mkdir /home/tuUsuario/public_html
```

Solo resta agregar **"las páginas webs"** dentro de la carpeta `public_html` que acabamos de crear (debe existir necesariamente un archivo llamado index.html o index.php) 

##Habilitando el módulo userdir

Para permitir que los usuarios posean su propio sitio web aún resta un paso: la habilitación del módulo de Apache correspondiente. Entre los distintos módulos de Apache, quien cumple con nuestro cometido es el módulo llamado `userdir`. Para habilitar dicho módulo, ejecutamos en la terminal: 

```bash
sudo a2enmod userdir
```

Luego, reiniciamos el servidor para que incorpore los cambios:

```bash
sudo service apache2 restart
```
