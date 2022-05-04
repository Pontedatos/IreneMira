#RESUMEN 

##A continuación, detallaré lo aprendido a lo largo del curso en la asignatura Periodismo de Datos.

##Instalación de un programa de emulación de la terminal

Antes de centrarme en la instalación de emulación de la terminal, he considerado que es importante saber lo que es una terminal. Para ello, he acudido a diferentes fuentes. Según la página de Wikipedia una terminal, dentro del lenguaje informático, se trata de un dispositivo electrónico o electromecánico que se utiliza para interactuar con un computador. En clase hemos estado viendo como se usaba indistintamente el concepto de terminal y consola como sinónimos. La función de un terminal está confinada a la exhibición, entrada de datos y ejecutar comandos. 

Lo que nosotras hemos aprendido es la instalación de un programa de emulación de la terminal, acción que se suele confundir con el concepto de terminal. Sin embargo, la emulación de la terminal hace referencia a un programa informático que simula el funcionamiento de un terminal del ordenador en cualquier dispositivo de visualización. En mi caso particular cabe destacar que mi sistema operativo es Windows, por ello, he tenido que instalar dos programas de emulación de la terminal, el primero de ellos WSL con el que estuvimos trabajando una parte del cuatrimestre y el segundo ha sido Cygwin utilizado ya al final del curso.

###Explicación de la instalación de la emulación de la terminal

WSL: Instalación de Ubuntu

Para poder instalar WSL se hizo a través de la terminal de Windows desarrollada por Microsoft, PowerShell (debido a que mi sistema operativo es Windows). Para hacerlo heos tenido que iniciar una sesión como administradores, y ejecutar el comando [`wsl --install -d Ubuntu`]. Una vez instalada es necesario reiniciar el ordenador. Una vez hecho e iniciado por primera vez, se nos pide la creación de un usuario y una contraseña para el usuario UNIX, que es el usuario administrador.

Cygwin: Unix en Windows

El caso de Cygwin fue distinto, ya que no es una herramienta del propio Microsoft sino que requiere de instalación. Por ello, esta instalación consistió en la descarga desde su web su instalador.
Una vez hecho esto se nos preguntó desde dónde queríamos instalarlo, y seleccionamos la opción «Instalar desde Internet». A continuación había que escoger dónde queríamos instalar el programa y para ello, escogimos la ruta que se establece por defecto. Después había que elegir el dominio de España [`.es`]. Para finalizar, lo que hicimos fue la instalación de los paquetes [`libcurl4, wget, ca-certificates-letsencrypt, lynx, nano y openssl.`].

Tras todo este proceso ya hemos aprendido la instalación de un programa de emulación de la terminal. 

##Configuración del programa

Tras la instalación de los programas, hemos también llevado a cabo una configuración de parámetros tanto de WSL como de Cygwin, como algún alias, cambiar la home o configurar [`git`]

### Establecer alias
El primer paso realizado fue establecer un alias (algo así como una abreviatura de la ruta de nuestra carpeta de Periodismo de datos). En mi caso, en vez de escribir esta ruta: [`/mnt/c/Users/UsuarioPC/Desktop#`], con poner [`micasa`] vale. 

Una de las cosas que hemos aprendido es a establecer este alias mediante la edición del archivo de configuración de Bash. Desde la línea de comandos, escribimos el comando [`echo`] y enviamos la salida con [`>>`] al final del archivo [`bashrc: echo “alias micasa=“cd ‘/mnt/c/Users/UsuarioPC/Desktop#” >> $HOME/.bashrc`].

Con este comando, cada vez que accedemos a Ubuntu o a Cygwin al teclear el alias en la terminal nos lleva de manera inmediata a la ruta asignada. Por otro lado, para ver el archivo de configuración del alias lo podemos hacer con [`cat $HOME/.bashrc y para editarlo con nano $HOME/.bashrc.`]. 

### Cambiar la home de Cygwin a la de Windows

En Cygwin hemos cambiado también la ruta de nuestra “casa” y de nuestro usuario para que sea la misma que la de Windows. Para eso hemos tenido que editar el archivo «hogar» o «casa» de nuestro usuario para que sea la de Windows. Editamos el archivo con  [`nsswith.conf con nano: nano /etc/nsswith.conf poniendo db_home`] al final del archivo. Guardamos (CTRL + O) y cerramos (CTRL + X) para que se conserven los cambios. 

Para comprobar que funcionaba al volver a abrir el programa escribimos [`pwd`] y volvemos a entrar para que se actualice. Comprobamos con [`pwd: /cygdrive/c/Users/usuario.`]

### Configurar git

Otro de los pasos realizados y por tanto, aprendidos ha sido configurar nuestro usuario de GitHub en la terminal para que los cambios que hagamos en nuestros archivos en local con nuestros repositorios en la nube (GitHub). 

Para poder hacer esto, en nuestra terminal se pone el comando [`git config --global user.name nuestrousuario`], siendo mi usuario IreneMira y luego [`git config --global user.email correogithub`] poniendo ahora mi correo con el que me he abierto la sesión en la plataforma. 

# Configuración de un programa de edición de texto

Además, también podemos editar el comportamiento de nuestro editor de texto [`nano`] a través del archivo de configuración. 

Lo que nosotras hemos hecho ha sido ajustar el texto a la resolución de la pantalla y de esta forma aparece el número de líneas. Esto se ha podido hacer mediante: [`nano $HOME/.nanorc`]. Una vez dentro hemos tenido que poner:

[`# Ajustar el texto a pantalla

set softwrap

# Numerar las líneas

set linenumbers`]

Por otro lado, es importante mencionar que en el caso de Cygwin el método es diferente. En este caso lo que hay que hacer es copiar el archivo de configuración de  [`nano`] que se sitúa en el directorio [`/etc.`]. Una vez hecho esto, lo copiamos a nuestro directorio home con  [`cp /etc/nanorc .nanorc`] y lo editamos mediante [`nano .nanorc.`]

Buscamos con CTRL + W “linenumbers” (sin comillas), y en su línea (# [`set linenumbers`]) le quitamos la #. Volvemos a buscar con CTRL + W “softwrap” (sin las comillas), y en su línea (# [`set softwrap`]) le quitamos la #. Guardamos con CTRL + O y salimos con CTRL + X.

# Configuración y funcionamiento de un gestor de paquetes/programas del emulador de la terminal

Según lo visto en clase un paquete es “una forma de organizar grupos de clases. Un paquete contiene un conjunto de clases relacionadas bien por finalidad, por ámbito o por herencia. Las clases tienen ciertos privilegios de acceso a los miembros dados y a las funciones miembro de otras clases dentro de un mismo paquete”. Por tanto, un gestor de paquetes según  la web del blog Colaboratorio  “es un programa que consta de una serie de herramientas que automatizan el proceso de instalación, actualización, desinstalación, del software.
En el caso de Ubuntu se hace mediante [`apt`] y en el caso de Cygwin tiene el suyo propio, mediante [`apt-cyg`]. El proceso para instalar [`apt-cyg`]. Lo instalamos con [`lynx -source rawgit.com/transcode-open/apt-cyg/master/apt-cyg > apt-cyg y luego install apt-cyg /bin.`]

Este gestor de paquetes lo que nos permite es instalar herramientas como vimos en una de las últimas clases con [`lolcat`] 

# Versión del lenguaje de SHELL utilizado: 

Shell, según lo estudiado en clase se trata del “idioma de la terminal (dentro está el BASH y el CSH: Windows y Mac respectivamente)”. Dentro de la Shell hay dialectos: uno es para
/bin/bash/

Para comprobar la versión del lenguaje de Shell que hemos estado utilizado usamos la variable de entorno  [`$0`].Para consultarla tenemos que realizar el comando [`echo $0`]. Una vez hecho esto nos damos cuenta de que tanto para Cygwin como para WSL es Bash. 

Para poder comprobar la versión de Bash hay dos opciones: la primera, usar la variable de entorno [`$BASH_VERSION`] con [`echo`] y  la segunda, mediante el propio bash, especificando la opción [` --help: bash --help.`]

# Valor de la variable de entorno PATH.

Para consultar la variable de entorno [`$PATH`], esto también lo hacemos con [`echo $PATH`]. La terminal nos devuelve las rutas donde se encuentran los programas instalados que puede ejecutar la terminal. 

Separados por dos puntos [`(:)`], aparecen los directorios donde la terminal ha estado buscando los programas para poder ejecutarlos cuando se indique mediante los comandos.


# Comandos utilizados y ejemplos

Todos los comandos tienen la siguiente estructura: comando / opciones / argumentos
Los comandos más utilizados han sido los siguientes:

[`pwd`] siendo el primer comando a utilizar cuando abrimos la terminal, es importante porque nos indica dónde estamos. 
[`cd`] sirve para cambiar el directorio, para cambiar dónde tienes algo. (con cd -y un espacio- te lleva a home). [`cd -`] te lleva al anterior sitio donde estabas.
[`ls=`] es el comando que significa “listar”, es decir,te dice qué tienes en la carpeta. Ejemplo: [`s -l `] es lístame con más detalle.
[`nano`] sirve para editar archivos de texto .md
[`mkdir`] es el comando utilizado para la creación de carpetas.
[`&&`] sirve para unir comandos, es decir, hacer dos comandos de una vez. Ejemplo: [`mkdir (crear carpeta) && cd (cambiar de directorio)`]
[`push`] es el comando que sirve para descargar y subir las cosas a GitHub.
[`ls -l/`]: la línea diagonal significa raíz.
 [`cat`] sirve para concatenar (unir o enlazar dos o más cosas). También lo hemos usado para leer archivos o para previsualizar, por ejemplo ponemos   [`cat README.md`] para previsualizar nuestro readme.
[`mv`] se utiliza para mover las cosas de un sitio a otro (en los argumentos de este comando indican el destino a donde queremos mover nuestra cosa). Este comando también se puede usar para cambiar de nombre un archivo o carpeta. Ejemplos:
-   [`mv capeta/ nuevo destino/.`] (“nuevo destino” es donde vas a mover “carpeta”, hay que poner un punto para que no se lie con el nuevo destino)
[`echo`] sirve para la impresión de un texto en pantalla., la terminal te responde lo que has escrito entre comillas. Ejemplo: Si queremos que nos diga cuál es nuestra home, escribimos [`echo $HOME`] (variable de entorno).
[`cp`] es un comando que sirve para copiar un archivo o carpeta a otra. Ejemplo: [`cp nombre de la carpeta/nombre del archivo.md  carpeta a donde lo quieres mover/.`]
[`rm`] es el comando que sirve para eliminar archivos o directorios, pero de forma irrecuperable, sin pasar por una Papelera de reciclaje o similar.
[`whoami`] comando que sirve para decirte quién eres.
[`git clone`] sirve para clonar en la carpeta en la que estés el repositorio que indiques con el enlace. 

