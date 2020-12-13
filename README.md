    ______                 ______           _     
    | ___ \                | ___ \         | |    
    | |_/ / ___  __ _ _ __ | |_/ / __ _ ___| |__  
    | ___ \/ _ \/ _` | '_ \| ___ \/ _` / __| '_ \
    | |_/ /  __/ (_| | | | | |_/ / (_| \__ \ | | |
    \____/ \___|\__,_|_| |_\____/ \__,_|___/_| |_|

# Funcionamiento

BeanBash es un script escrito en Bash dedicado a bloquear el servicio epoptes y poder evitar la conexión remota desde este servicio. A demás, tiene la posibilidad de bloquear también el servicio SSH para impedir que vuelvan a habilitar epoptes de forma remota. Epoptes utiliza VMWare, por lo que este servicio también debe detenerse.

Cada vez que se vuelve a iniciar sesión, epoptes vuelve a iniciarse con todos los servicios, por lo que el script se debe ejecutar cada vez.

Este script utiliza los comandos "service" y "route" por lo que solo funciona con Debian y sus derivados como Ubuntu por el momento, se planea adaptar el script también a ArchLinux y derivados como Manjaro.

Las opciones de bloqueo detienen los servicios de VMWare y epoptes, luego detecta la dirección IP del equipo servidor y lo bloquea desde el kernel. Tras esto, mata los procesos activos de epoptes.

Las opciones de activación eliminan el bloqueo de la dirección IP del servidor, inicia los servicios de epoptes y vmware y vuelve a ejecutar epoptes-client para su activación. Es posible que, tras su ejecución, la conexión se recupere y se caiga una vez antes de recuperarse por completo.

# Descarga

Puedes descargar el script directamente desde GitHub, existen dos maneras de realizar la descarga: mediante clonación del repositorio y descargando el archivo comprimido.

## Descargar desde repositorio
Para descargar desde el repositorio se tiene que tener instalado git, se puede instalar con el siguiente comando:
```
sudo apt install git
```
Con git instalado, tienes que posicionarte en el directorio donde quieras tener el script y ejecutar la siguiente orden:
```
git clone https://github.com/TheRussianHetzer/BeanBash.git
```
Este comando creará un directorio que contendrá el script listo para ser ejecutado.

## Descargar archivo comprimido

Desde [este enlace](https://github.com/TheRussianHetzer/BeanBash/archive/main.zip) podrás obtener la versión en inglés. A través de [este enlace](https://github.com/TheRussianHetzer/BeanBash/archive/es.zip) tendrás la versión en español. La versión en español siempre se lanza con antelación y es posible que tenga más fallos.
Una vez descargado se puede descomprimir usando el siguiente comando:
```
tar -xvzf ejemplo.zip
```
Debemos cambiar ```ejemplo.zip``` por el nombre del archivo.

# Posibles errores
## No es un archivo ejecutable

Es posible que se requiera añadir permisos de ejecución al script para poder funcionar. Para ello primero hay que ubicarse en el directorio donde está almacenado el script y ejecutar el siguiente comando:
```
chmod u+x ./BeanBash.sh
```
