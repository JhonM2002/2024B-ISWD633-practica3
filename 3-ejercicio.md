## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO

docker network create net-wp

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

La carpeta db del host almacenará los datos de la base de datos de MySQL, incluyendo archivos que representan tablas y datos de la base de datos configurada.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD

docker run -d --name mysqlejercicio3 --network net-wp -v D:/2024-B/CONSTRUCCION/practica3/ej
ercicio3/db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -e MYSQL_DATABASE=dbjhon -e MYSQL_USER=jhon -e MYSQL_
PASSWORD=123456 mysql:8

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?

Ahora contiene archivos y carpetas correspondientes a la base de datos MySQL, que almacenan la estructura y datos de la base de datos creada.

![image](https://github.com/user-attachments/assets/01fcb851-17d6-47ad-b376-5e8ca5095bfb)

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO

docker run -d --name wordpressejercicio3 --network net-wp -p 9500:80 -v D:/2024-B/CONSTRUCCI
ON/practica3/ejercicio3/www:/var/www/html -e WORDPRESS_DB_HOST=mysqlejercicio3 -e WORDPRESS_DB_USER=jhon -e WO
RDPRESS_DB_PASSWORD=123456 -e WORDPRESS_DB_NAME=dbjhon wordpress

### Personalizar la apariencia de wordpress y agregar una entrada

![image](https://github.com/user-attachments/assets/0282308c-18d2-4209-b872-6dbf75fac93c)

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

Al recrear el contenedor de WordPress, los cambios realizados como la personalización y las entradas se mantienen, ya que están almacenados en la carpeta www del host, que sigue montada en el contenedor.


