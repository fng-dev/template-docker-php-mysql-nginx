# Template basico Docker PHP MYSQL NGINX

### La idea inicial de esta plantilla es facilitar la creación de entornos que necesiten versiones específicas para cada aplicación (php y mysql)

## Estructuras de carpetas

+ api
+ database
+ images
+ mysql
+ nginx

### API

+ Dentro de la carpeta api, es donde estará tu proyecto php. Copie en esta carpeta la carpeta con su proyecto.

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

+ Dentro de la carpeta images, es donde estará los archivos de configuración de las instancias. Ahí ya tienes la configuración necesaria para instalar php 8.1, composer y la mayoría de las librerías necesarias para instalar Lumen.

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