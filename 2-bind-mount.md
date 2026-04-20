# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# COMPLETAR CON EL COMANDO
docker run -d -P --name volumen-nginx --mount type=bind,source=C:\Users\wwwal\consEvoSw\nginx\html,target=/usr/share/nginx/html nginx:alpine

### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Muestra error 403-Forbidden, y debería ser porque la carpeta html está vacía
<img width="830" height="265" alt="image" src="https://github.com/user-attachments/assets/401fef52-f3ad-4536-8086-0ff0b834a062" />

### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El archivo index.html se oculta ya que al usar el bind mount, se prioriza el contenido correspondiente al html que se encuentra en la ruta dada de la computadora.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Ahora muestra la página correspondiente al template que descargué y descomprimí en la carpeta html
<img width="1919" height="957" alt="image" src="https://github.com/user-attachments/assets/e502063f-d5d2-4490-9a19-d28fb301dc44" />

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
docker rm -f volumen-nginx

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El nuevo contenedor muestra exactamente lo mismo que el anterior, y esto es correspondiente a la persistencia de datos del volumen creado anteriormente, ya que aunque el contenedor se eliminó, el template quedó guardado en la computadora.


