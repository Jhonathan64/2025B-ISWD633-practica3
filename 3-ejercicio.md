## Esquema para el ejercicio
![Imagen](esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO
<img width="808" height="72" alt="image" src="https://github.com/user-attachments/assets/b6a00ca3-b8fa-4158-8f85-9d6dc008f7f0" />

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es (COMPLETAR CON LA RUTA)

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Inicialmente, la carpeta db del host esta vacía. Una vez que se ejecute el contenedor de MySQL con el Bind Mount activo, esta carpeta contiene todos los archivos de datos de la base de datos (tablas, logs, configuraciones) que MySQL necesita para funcionar.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO
<img width="1464" height="114" alt="image" src="https://github.com/user-attachments/assets/8a8a3ef5-9da0-4997-ae0d-8e5ce3f845ab" />

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Se observa que la carpeta db ahora contiene varios archivos y carpetas generados por MySQL (como ibdata1, mysql, performance_schema, etc.). Esto confirma que el Bind Mount está funcionando y la información de la base de datos es persistente en el host.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es (COMPLETAR CON LA RUTA)

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO
<img width="1458" height="114" alt="image" src="https://github.com/user-attachments/assets/b3b10184-e605-4c86-8297-066853e6e66b" />

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA 
Al crear nuevamente el contenedor, WordPress se inicia inmediatamente con toda la configuración, apariencia y entrada de blog que se había guardado anteriormente, esto no requiere la pantalla de instalación inicial.

