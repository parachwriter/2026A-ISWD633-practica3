## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
```
docker network create net-wp
```
### Para que persista la información es necesario conocer en dónde mysql almacena la información.

En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
La carpeta contiene los archivos de datos de MySQL, incluyendo las bases de datos, tablas, registros y archivos internos necesarios para el funcionamiento del motor de base de datos.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
```
docker run -d --name mysql-wp --network net-wp -e MYSQL_ROOT_PASSWORD=root123 -e MYSQL_DATABASE=wordpress -e MYSQL_USER=wp_user -e MYSQL_PASSWORD=wp_pass -v "E:\6to_Semestre\Docker\sql\db:/var/lib/mysql" mysql:8
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
Se crean automáticamente múltiples archivos y carpetas correspondientes al sistema de almacenamiento de MySQL, incluso si la carpeta estaba inicialmente vacía. Esto indica que la base de datos ya está persistiendo la información en el host.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
````
docker run -d --name wordpress-wp --network net-wp -p 8080:80 -e WORDPRESS_DB_HOST=mysql-wp:3306 -e WORDPRESS_DB_USER=wp_user -e WORDPRESS_DB_PASSWORD=wp_pass -e WORDPRESS_DB_NAME=wordpress -v "E:\6to_Semestre\Docker\wordpress\ejercicio3\www:/var/www/html" wordpress
````

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Al eliminar y volver a crear el contenedor, la información (como configuraciones, temas y entradas creadas) se mantiene intacta. Esto ocurre porque los datos están almacenados en volúmenes montados en el host, lo que permite la persistencia de la información incluso cuando los contenedores son eliminados.
