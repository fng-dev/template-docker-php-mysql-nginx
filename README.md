# Template basico Docker PHP MYSQL NGINX

### La idea inicial de esta plantilla es facilitar la creación de entornos que necesiten versiones específicas para cada aplicación (php y mysql)

## Estructuras de carpetas

+ api
+ database
+ images
+ mysql
+ nginx

### API

+ Dentro de la carpeta api, es donde estará tu proyecto php. Pegue en esta carpeta la carpeta con su proyecto.

+ Ejemplo de estructura:

```
    + api
        + project-name
    + database
    + images
    + mysql
    + nginx
    - docker-compose.yml
```

### DATABASE

+ Dentro de la carpeta database, debe quedar cualquier archivo que sea necesario para configuracion o restauración de una bbdd. Por ejemplo, un backup de la base de datos del proyecto. Todo que esta dentro de esta carpeta, sera cargado en el container de mysql.

+ Ejemplo de estructura:

```
    + api
        + project-name
    + database
        - backup-16-06-23.sql
    + images
    + mysql
    + nginx
    - docker-compose.yml
```

### IMAGES

+ Dentro de la carpeta images, es donde estará los archivos de configuración de los containers. Ahí ya tienes la configuración necesaria para instalar php 8.1, composer y la mayoría de las librerías necesarias para instalar Lumen.

+ Ejemplo de estructura:

```
    + api
        + project-name
    + database
        - backup-16-06-23.sql
    + images
        + php
            - Dockerfile
    + mysql
    + nginx
    - docker-compose.yml
```

### MYSQL

+ Dentro de la carpeta mysql, es donde quedará los archivos relacionados a mysql. Es en esta carpeta que quedará toda las acciones relacionadas a la base de datos. Aquí es donde se va persistir la información de la bbdd, para que cada vez que se vuelva a levantar el container, no se perca la informacion guardada en la bbdd.

### NGINX

+ Dentro de la carpeta nginx, es donde queda el archivo de configuracion del virtual host.

+ Ejemplo de estructura:

```
    + api
        + project-name
    + database
        - backup-16-06-23.sql
    + images
        + php
            - Dockerfile
    + mysql
    + nginx
        - site.conf
    - docker-compose.yml
```

# Configuraciones

### Que tener instalado?

+ Docker
+ Docker Compose

### Configurando docker-compose.yml

Todos los cambios informados aquí, deben ser hechos en el archivo docker-compose.yml

+ Reemplazar texto de la variable container_name de los servicios (web, php, db), la palabra project-name por el nombre de su proyecto.

Ejemplo: 

```
    - container_name: nginx-project-name
    + container_name: nginx-gux
```

+ Reemplazar texto de la variable MYSQL_DATABASE en el servicio db, la palabra project-db-name por el nombre de su base de datos.

Ejemplo: 

```
    - MYSQL_DATABASE: project-db-name
    + MYSQL_DATABASE: gux_db
```

### Configurando nginx

Todos los cambios informados aquí, deben ser hechos en el archivo site.conf, dentro de la carpeta nginx

+ Cambiar el texto en la variable server_name, para la direccion configurado en su archivo de hosts

Ejemplo: 

```
    - server_name: api.project-name.develop
    + server_name: api.gux.develop
```

+ Cambiar el texto en la variable root, para el path configurado en su archivo docker-compose.yml

Ejemplo: 

```
    - root /var/www/project-name/public;
    + root /var/www/gux/public;
```

# Levantando los containers

### Para levantar los containers, ejecute el seguiente comando en la carpeta donde esta el docker-compose file del proyecto:

```
    docker-compose up --build -d
```

### Ahora que se ha montado el contenedor, instalemos las dependencias del proyecto y configuremos el archivo de entorno.

Para accesar el container con el proyecto, ejecute el seguiente comando:

+ Recuerda cambiar {php_container_name} por el nombre del container php

```
    docker exec -it {php_container_name} /bin/bash
```

Este comando ingresará al container, en la carpeta /var/www. Ahora es solo entrar a la carpeta de su proyecto y instalar las dependencias y configurar el archivo de enviroment

# Comandos utiles

## Listar containers en ejecucion

```
    docker ps
```

## Parar un container en ejecucion

```
    docker stop {CONTAINER_ID}
```

## Parar todos containers en ejecucion

```
    docker stop $(docker ps -a -q)
```

## Eliminar un container

```
    docker rm {CONTAINER_ID}
```

## Parar todos containers en ejecucion

```
    docker rm $(docker ps -a -q)
```

## Entrar en un container

```
    docker exec -it {container_name} /bin/bash
```
