# Instalación de Prestashop a través de contenedores Docker

Vamos a crear una tienda de Prestashop utilizando contenedores Docker.

## Instalando docker y docker-compose

Para instalar ambas utilidades tenemos que ejecutar el siguiente comando:

>apt install docker docker-compose

Cuando se descargue, cada vez que las queramos utilizar deberá de ser con el comando sudo, para evitar esto, tenemos que meter al usuario en el grupo de usuarios de Docker, esto se hace con la siguiente instrucción:

>sudo usermod -aG docker $USER

Después de esto, tenemos que habilitar el servicio docker para que se arranque cada vez que iniciemos el sistema, para ello ejecutamos:

>sudo systemctl enable docker

Ahora reiniciamos la máquina haciendo un reboot y podremos empezar a utilizar docker con total normalidad.

## Utilizando docker-compose

Como se explico en la práctica anterior, docker-compose nos permite crear un archivo de configuración con los parámetros necesarios de tal forma que en el momento en el que invoquemos al archivo, se levante toda la infraestructura que queremos.

En el repositorio de esta práctica subiré el archivo .yml utilizado.

El comando para llamar al archivo de configuración y ponerlo todo en marcha es el siguiente:

>docker-compose up -d

Después de ejecutarlo, el sistema se encarga de obtener las imágenes y aplicar las configuraciones que hemos especificado para cada contenedor.

## Variables

Se pueden hacer uso de variables para no tener que estar constantemente cambiando los parámetros necesarios en el archivo, así, solo establecemos el parámetro una vez, y cada vez que o necesitemos solo tenemos que llamarlo.

Para ello tenemos que crear un archivo .env (tiene que llamarse así solamente) en el mismo directorio en el que se encuentra nuestro .yml.

Dentro del archivo escribimos el parámetro al que tiene que pertenecer la variable seguido del signo = y la variabe, un ejemplo es el siguiente:

>MYSQL_PASSWORD=contraseña_super_segura_12345

Para llamar a la variable en el archivo de configuración solo hay que poner el parámetro, el signo igual, y poner ${Nombre variable}, es decir, algo así:

>MYSQL_PASSWORD=${MYSQL_PASSWORD}

Después de esto, podremos levantar toda nuestra infraestructura.

## Demostración

Aquí se ven unas capturas de la infraestructura en marcha:

![Imagen de demostracion 1](/capturas/demostracion_2.png)

![Imagen de demostracion 2](/capturas/demostracion_1.png)

![Imagen de demostracion 3](/capturas/demostracion_3.png)
