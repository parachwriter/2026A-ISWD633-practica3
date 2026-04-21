RESUMEN DE MI APRENDIZAJE- VOLÚMENES EN DOCKER

Los volúmenes en Docker sirven para guardar datos de forma persistente, es decir, que no se pierdan cuando se elimina un contenedor. Son muy importantes cuando se trabaja con bases de datos o aplicaciones web.

Existen tres tipos principales:
- Bind mount: conecta una carpeta del host con el contenedor. Si la carpeta del host está vacía, puede causar errores (como el 403 en nginx). También sobrescribe los archivos internos del contenedor.
- Volumen nombrado: lo gestiona Docker y no necesita una ruta específica del host. Es más fácil de manejar.
- Volumen anónimo: se crea automáticamente, pero es más difícil de identificar después.

Algo importante es que los volúmenes se deben definir cuando se crea el contenedor, ya que después no se pueden modificar.

En la práctica con nginx entendí que si la carpeta está vacía no carga nada, pero al agregar archivos HTML ya funciona correctamente. Además, los datos se mantienen aunque elimine el contenedor.

En el caso de MySQL y WordPress, aprendí que:
- MySQL guarda datos en /var/lib/mysql
- WordPress en /var/www/html
Cuando se usan volúmenes, toda la información (bases de datos, configuraciones, etc.) se guarda en el host y no se pierde.

También aprendí a usar redes en Docker para que los contenedores se comuniquen entre sí usando nombres en lugar de IP.

En Drupal se usan varios volúmenes para diferentes partes del sistema, lo que ayuda a organizar mejor los datos.

Comandos importantes:
- docker volume create
- docker volume rm
- docker volume prune
- docker network create

APRENDIZAJES:
Antes solo sabía usar contenedores básicos, pero ahora entiendo cómo funciona la persistencia de datos, cómo conectar servicios y cómo montar aplicaciones reales. También aprendí a leer la documentación de las imágenes para saber qué rutas usar.

Usé solo los comandos especificados en esta práctica.
