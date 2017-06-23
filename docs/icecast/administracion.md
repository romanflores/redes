====== Administración del servidor ======
Es posible administrar el servidor web mediante una interfaz web. Para ello, procederemos a abrir un navegador web y colocar la **dirección IP** o **nombre de dominio** del servidor, seguido del número de puerto (ambos valores fueron definidos en el archivo de configuración): 

```bash
http://192.168.0.232:8000
```

Y nos **logueamos con el usuario administrador** que hemos configurado previamente. Al acceder, veremos la siguiente página: 

![Administración de Icecast](imgIcecast/icecastadmin1.png)

Al hacer clic sobre el menu **Administration** veremos los datos del servidor: 

![Administración de Icecast](imgIcecast/icecastadmin2.png)

Si damos clic sobre **Mountpoint List** veremos listados los clientes que se encuentran transmitiendo. Naturalmente, la página se verá vacía si nadie está transmitiendo contenido: 

![Administración de Icecast](imgIcecast/icecastadmin3.png)

Cuando un usuario comienza a transmitir contenido, automáticamente aparece listado en la sección **Mountpoint List**: 

![Administración de Icecast](imgIcecast/icecastadmin4.png)

Y la información anterior, aparecerá listada también al pié de la página de **Administration**: 

![Administración de Icecast](imgIcecast/icecastadmin5.png)
