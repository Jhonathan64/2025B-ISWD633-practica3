# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado o utilizó otros comandos que no se mencionan al realizar la práctica también se debe documentar.

Lo que realmente aprendí de la práctica con Docker es cómo funciona la cosa en serio, más allá de solo escribir comandos.

1. Los datos y los contenedores: Antes creía que si metía un archivo o una base de datos en un contenedor, ahí se quedaba. Pero no, los contenedores son temporales. El principal aprendizaje fue que hay que sacar los datos si queremos que sobrevivan.

Bind Mounts (Nginx/WordPress): Me enseñó a decirle a Docker: "Oye, en lugar de usar tu carpeta interna, usa esta carpeta de mi Windows". El problema fue con el famoso error 403 Forbidden de Nginx. Descubrí que el usuario interno del contenedor no tiene permiso para leer los archivos de mi PC. Por lo que tuve que arreglar los permisos en Windows o usar comandos como :ro (solo lectura) para que funcione.

Volúmenes Nombrados (PostgreSQL/Drupal): Esto es lo más práctico. En lugar de decir dónde guardar los datos en mi PC, le di un nombre (vol-postgres) y dejé que Docker se encargara de guardarlo donde quisiera, ya que esto es mucho más estable y limpio para bases de datos.

El punto es que si borras un contenedor, los datos siguen seguros en un volumen o en la carpeta mapeada, eso se denomina persistencia.

2. La Comunicación Secreta entre Contenedores
Aprendí que los contenedores no se conectan por la IP normal de mi computadora. Si tengo varios (como Drupal y PostgreSQL), hay que crearles una red privada (como net-drupal).

Una vez en la misma red, los contenedores se hablan usando sus nombres. Por eso pude conectar Drupal a server-postgres sin saber su dirección IP interna.

Esto es clave para la arquitectura: mantenemos nuestra base de datos (PostgreSQL) segura dentro de la red y solo expones la aplicación web (Drupal) al puerto que usa la gente (9700).

3. De Usuario a Solucionador de Problemas
Lo más valioso fue tener que solucionar los errores porque la práctica no salió perfecta:

Cuando la página no cargaba (error ERR_CONNECTION_REFUSED o ERR_EMPTY_RESPONSE), aprendí que el navegador miente. En lugar de actualizar, hay que ir a la terminal y usar docker logs <nombre_contenedor>. y ahi se observa si WordPress falló por una contraseña incorrecta o porque MySQL no estaba listo.

Descubrí que a veces, la base de datos o Drupal no arrancan bien porque no tienen permiso para escribir en los volúmenes nombrados al inicio. La solución fue usar la opción -u 0 (ejecutar temporalmente como usuario root) al lanzar el contenedor, forzando la escritura de los archivos iniciales para que el servicio pudiera empezar.

En resumen, pasé de solo copiar comandos a entender por qué fallan los contenedores y cómo aplicar la estrategia correcta (Bind Mount o Volumen Nombrado, y red personalizada) para que una aplicación compleja como Drupal funcione de forma robusta.
