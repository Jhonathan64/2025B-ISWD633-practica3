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
<img width="1460" height="98" alt="image" src="https://github.com/user-attachments/assets/6562537d-9f2d-41b2-a246-115f115fb8b3" />

### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Al ingresar al servidor, Nginx se puede observar que sirve el archivo index.html que está ubicado en mi computadora (el host), mostrando el mensaje que se escribio anteriormente en mi caso "¡Conexión Exitosa con Bind Mount!"). El contenido que se observa es una réplica exacta del archivo que se encuentra en la PC.
<img width="1919" height="627" alt="image" src="https://github.com/user-attachments/assets/85c5c56b-6b71-42a4-b5b0-e668c03bde74" />

### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
El archivo index.html original que venía con la imagen nginx:alpine (dentro del contenedor, en /usr/share/nginx/html) queda oculto o inaccesible. Esto se debe a que el Bind Mount superpone completamente el directorio del host sobre el directorio del contenedor (/usr/share/nginx/html). Es como si el contenedor solo pudiera ver los archivos de la computadora en esa ubicación.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Al ingresar nuevamente, el servidor de Nginx muestra instantáneamente el template recién descargado y descomprimido (con todos sus estilos e imágenes). Esto confirma que el Bind Mount proporciona una sincronización en tiempo real: el contenedor siempre sirve el contenido que exista en la carpeta del host, no fue necesario reiniciar Docker.
<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/360c1db7-b204-4476-844c-af4872c1a189" />

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
<img width="524" height="141" alt="image" src="https://github.com/user-attachments/assets/f7858f57-d0c2-4092-9d6a-7618a3cffa5a" />

### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Al crear un nuevo contenedor, Nginx nos va a servir inmediatamente el template HTML completo. Dado que los archivos de nuestro sitio web están en el host y no en el contenedor, por lo que estos nunca se eliminaron. El nuevo contenedor se conecta al directorio existente del host a través del Bind Mount y levanta el sitio web con el contenido actualizado. La información es persistente porque vive fuera del ciclo de vida del contenedor.


