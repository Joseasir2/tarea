#Esto es una prueba con SSH



Descargar imagen y comprobación en equipo.

Entraremos en la terminal y descargaremos la imagen de Ubuntu que queramos, para saber el nombre podemos ir a “Docker hub” y podremos ver que tenemos una lista de imágenes que podremos descargar, en mi caso será la imagen 22.04. Cuando hayamos localizado la imágen deseado escribiremos en la terminal el siguiente comando:

-docker pull ubuntu:22.04

Con esto se habrá DESCARGADO la imágen pero para comp

Para comprobar que lo hemos descargado y está en el equipo o bien podemos verlo por Visual Code o bien por consola de comandos con el siguiente comando:

-docker ps



Crear un contenedor sin ponerle nombre y comprobar si está arrancado.

Para crear un contenedor sin nombre nos vamos a la terminal y ponemos

-docker run -it hello-world (por ejemplo hello-world)

Y si ahora lanzamos el comando “docker ps -a” nos saldrá una lista con toda la información de imágenes y contenedores y al irnos a las últimas modificaciones veremos que se nos ha creado con un nombre predeterminado, en mi caso se llama awesome_goldstine.



Crear un contenedor que se llame ubu1.

Escribiendo el siguiente comando a parte de crearlo también lo lanzaremos (accedemos a él)

-docker run -it –name ubu1 ubuntu:22.04


Comprueba qué IP tiene y si puedes hacer ping a google+

Entramos dentro del contenedor cn el comando “docker exec -it ubu1 bash” y una vez dentro hacemos una actualización con “apt-get update” y si falta algún paquete pondremos “apt-get upgrade” y por último instalamos el net-tools con “apt install net-tools” y una vez instalado, para ver la IP lanzaremos el comando “ifconfig” y en mi caso la IP es 172.17.0.2. Ahora para hacer ping tendremos que instalar “ping” con el siguiente comando “apt-get update && apt-get install -y iputils-ping”. Ahora ya podemos hacer ping a google.


Crear un contenedor llamado ubu2 y haz ping entre ubu1 y ubu2

Hacemos lo mismo que con ubu1, instalamos actualizaciones, net-tools etc y este contenedor tiene la IP 172.17.0.3. Efectivamente cuando hacemos ping a 172.17.0.2 nos lo hace y además, dato importante, hay que acordarse de dejar el otro contenedor corriendo para poder hacer ping.





Salir de la terminal y ver qué ocurre con el contenedor

Si salimos de la terminal y antes le pusimos “start” no se nos detendrá el contenedor, en cambio si dentro de la terminal ponemos exit y la cerramos, se nos dentrendrá.

Cuanto ocupa en disco los contenedores

Para ello lanzamos el comando docker ps –size, como no tienen nada ambos ocupan entre 70mb (ubu1) y 62mb (ubu2)

Cuanta RAM ocupan los contenedores

Para ello ponemos el comando “docker stats” y podremos ver cuanto ocupan de RAM cada contenedor. Teniendo ubu1 y ubu2 corriendo, cada uno ocupa 880-900KiB.
