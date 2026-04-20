## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO
docker network create net-wp

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mys

Ruta carpeta host: C:\Users\wwwal\docker\ejercicio3\db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Como no se ha ejecutado ni creado el contenedor, no contiene nada la carpeta

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO
docker run -d --name srv-mysql8 --network net-wp -v C:\Users\wwwal\docker\ejercicio3:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=admin -e MYSQL_DATABASE=wordpressdb -e MYSQL_USER=user -e MYSQL_PASSWORD=admin mysql:8<img width="1451" height="82" alt="image" src="https://github.com/user-attachments/assets/8191fe34-253e-46df-a6be-99f6405a81ba" />

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Se crearon varios archivos y carpetas donde estaba vacío.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html

Ruta carpeta host: C:\Users\wwwal\docker\ejercicio3\www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO
docker run -d --name cont-wordpress --network net-wp -p 9500:80 -v C:\Users\wwwal\docker\ejercicio3\www:/var/www/html -e WORDPRESS_DB_HOST=srv-mysql8 -e WORDPRESS_DB_USER=user -e WORDPRESS_DB_PASSWORD=admin -e WORDPRESS_DB_NAME=wordpressdb wordpress

### Personalizar la apariencia de wordpress y agregar una entrada
<img width="1658" height="968" alt="image" src="https://github.com/user-attachments/assets/a8609cdb-1e0c-4697-b72b-4abf5410339d" />

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA 
Al ejecutar nuevamente el comando run con los mismos volúmenes, toda la información se mantuvo como estaba antes de borrar el anterior contenedor, gracias a la persistencia de datos del volumen creado.
