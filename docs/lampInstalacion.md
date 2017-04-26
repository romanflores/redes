Se denomina **LAMP** a un grupo de software de código libre que se instala normalmente en conjunto para habilitar un servidor para alojar sitios y aplicaciones web dinámicas. Este término en realidad es un acrónimo que representa un sistema operativo **GNU/Linux** con un servidor web **[Apache](https://httpd.apache.org/)**, donde los datos del sitio son almacenados en base de datos **[MySQL](https://www.mysql.com/)** o **[MariaDB](https://mariadb.org/)** y el contenido dinámico es procesado con **[PHP](https://secure.php.net/)**.


Para disponer de un servidor web **LAMP** ejecutaremos el siguiente comando:

```bash
sudo apt install lamp-server^
```
![LAMP Server](lamp/lampServer.gif)

O bien: 

```bash
sudo apt install tasksel
```

Y luego seleccionar la opción **LAMP Server** del menú que nos aparecerá en pantalla:

![LAMPTasksel](lamp/lampTasksel.gif)

!!! done "Instalación"
	En ambos casos realizamos la instalación del servidor web a través de 	  un _metapaquete_ que se encarga de instalar los paquetes necesarios 	  para el correcto funcionamiento del servidor. Sin embargo, podemos realizar una instalación manual, seleccionando los paquetes que deseamos instalar de manera individual. 

Adicionalmente podemos instalar un gestor para nuestra base de datos: **phpmyadmin**, ejecutando el siguiente comando: 

```bash
sudo apt-get install phpmyadmin
```
Donde se nos pedirá la contraseña del usuario root de MySQL, definida con anterioridad al instalar el metapaquete LAMP: 

![PhpMyAdmin](lamp/lampPhpMyAdmin.gif)

!!! note "Instalación de phpMyAmin"
	Durante la instalación se solicitará la intervención del usuario. En cualquier caso, nos desplazaremos por las opciones con la tecla TAB, seleccionando nuestra elección presionando la tecla ESPACIO. 


