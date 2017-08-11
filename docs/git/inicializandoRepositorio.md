Puedes obtener un proyecto Git de dos maneras. La primera es tomar un proyecto o directorio existente e importarlo en Git. La segunda es clonar un repositorio existente en Git desde otro servidor.

## Inicializando un repositorio vacío
Para comenzar un repositorio vacío primero debes crear la carpeta que alojará al mismo:

```bash
mkdir miProyecto
```
Luego, desplazarse al directorio: 

```bash
cd miProyecto
```
Por último, inicializar el repositorio con el siguiente comando: 

```bash
git init --bare
```

##Clonando un repositorio existente
Si deseas obtener una copia de un repositorio Git existente — por ejemplo, un proyecto en el que te gustaría contribuir — el comando que necesitas es `git clone`. Cada versión de cada archivo de la historia del proyecto es descargada por defecto cuando ejecutas `git clone`. De hecho, si el disco de tu servidor se corrompe, puedes usar cualquiera de los clones en cualquiera de los clientes para devolver al servidor al estado en el que estaba cuando fue clonado (puede que pierdas algunos hooks del lado del servidor y demás, pero toda la información acerca de las versiones estará ahí).

Puedes clonar un repositorio con `git clone [url]`. Por ejemplo:

```bash
git clone https://dominio.com/proyecto
```

Esto crea un directorio llamado `proyecto`, inicializa un directorio `git` en su interior, descarga toda la información de ese repositorio y saca una copia de trabajo de la última versión. Si te metes en el directorio `proyecto`, verás que están los archivos del proyecto listos para ser utilizados. Si quieres clonar el repositorio a un directorio con otro nombre que no sea `proyecto`, puedes especificarlo con la siguiente opción de línea de comandos:

```bash
git clone https://dominio.com/proyecto miProyecto
```

Ese comando hace lo mismo que el anterior, pero el directorio de destino se llamará `miProyecto`.

Git te permite usar distintos protocolos de transferencia. El ejemplo anterior usa el protocolo https://, pero también puedes utilizar git:// o el protocolo de transferencia SSH:

```bash
git clone usuario@servidor:ruta/del/repositorio 
```

Donde _servidor_ hace referencia a la dirección IP o dominio del servidor donde se encuentra alojado el recurso que deseamos clonar. 

!!!done "Directorio oculto .git"
        En el repositorio existe un directorio oculto llamado `.git` el cual contiene todos los archivos necesarios para el correcto funcionamiento de Git. 