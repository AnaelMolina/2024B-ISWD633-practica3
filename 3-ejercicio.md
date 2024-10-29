## Esquema para el ejercicio
![Imagen](img/esquema-ejercicio3.PNG)

### Crear red net-wp
# 
```Windows PowerShell
Copyright (C) Microsoft Corporation. Todos los derechos reservados.

Instale la versión más reciente de PowerShell para obtener nuevas características y mejoras. https://aka.ms/PSWindows

PS C:\Users\PC> docker network create net-wp
>>
a98e4daf1bf68c166195d7b548a81c99b7a6d62a823c44c3d5fcbcd3275a45d6
PS C:\Users\PC>docker run -d --name mysql_container --network net-wp -v ${PWD}/ejercicio3/db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root_password -e MYSQL_DATABASE=wordpress_db mysql:latest
>>
Unable to find image 'mysql:latest' locally
c0880e4b3737: Download complete
4bab267f9ce1: Download complete
78308a3437c4: Download complete
Digest: sha256> docker run -d --name wordpress_container --network net-wp -p 9500:80 -v ${PWD}/ejercicio3/www:/var/www/html -e WORDPRESS_DB_HOST=mysql_container -e WORDPRESS_DB_USER=root -e WORDPRESS_DB_PASSWORD=root_password -e WORDPRESS_DB_NAME=wordpress_db wordpress:latest 
>> C:\Users\PC>
Unable to find image 'wordpress:latest' locally
latest: Pulling from library/wordpress
a480a496ba95: Pulling fs layer
c0fa9286e198: Pulling fs layer
24cbeb13063d: Pulling fs layer
3d76291219c3: Pulling fs layer
72c6dbb62161: Pulling fs layer
8a1846dfbe9a: Pulling fs layer                                                                            
4e0d1246ed19: Pulling fs layer                                                                            
72c6dbb62161: Download complete
acd6e8eb134b: Download complete
72a1501f3910: Download complete
8e16f05140fd: Download complete
ed249af23b65: Download complete
c8e14935230b: Download complete
95ab1cc5ca33: Download complete
f3380324bcbe: Download complete
78ee5e1490ca: Download complete
7c65c4fca52e: Download complete
e807ae4973d0: Download complete
af2e2799aa38: Download complete
27f1d0bbde81: Download complete
8fac5e585cd6: Download complete
Digest: sha256:362bc4b4df5a46f5a2bfc51ea53f85f51c0a422860c25ef3e7a8a6622dd7a33c
Status: Downloaded newer image for wordpress:latest
22d9f1dcbebf1ea3bdd8ba7841094a591865381e21e29c0c4cc9e23aa9af5961
 ```

### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio carpeta del contenedor (a) es /var/lib/mysql
Ruta carpeta host: .../ejercicio3/db


### ¿Qué contiene la carpeta db del host?
#### La carpeta db del host contiene los datos de MySQL, todos los archivos de la base de datos necesarios para que MySQL funcione, incluyendo tablas, índices y configuraciones de la base de datos, para que persistan incluso cuando el contenedor se detiene o elimina.

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
#### 
```
PS C:\Users\PC> docker run -d --name mysql_container --network net-wp -v ${PWD}/ejercicio3/db:/var/lib/mys docker run -d --name mysql_container --network net-wp -v ${PWD}/ejercicio3/db:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root_password -e MYSQL_DATABASE=wordpress_db -e MYSQL_USER=wp_user -e MYSQL_PASSWORD=wp_password mysql:8
57454bbb3e3ffdea9ee959862c60fd45038e5bb0b4ce508a8372811f1b89bd8c
PS C:\Users\PC> docker ps
CONTAINER ID   IMAGE              COMMAND                  CREATED          STATUS          PORTS         
         NAMES
22d9f1dcbebf   wordpress:latest   "docker-entrypoint.s…"   40 minutes ago   Up 40 minutes   0.0.0.0:9500->80/tcp   wordpress_container
PS C:\Users\PC> 
```

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
##### Inicialmente estaba vacía, ahora observo varios archivos y carpetas. Estos contienen los datos de MySQL, como las tablas y configuraciones de la base de datos. Estos archivos son generados automáticamente por MySQL para almacenar y gestionar la información de la base de datos de manera persistente.

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es /var/www/html
Ruta carpeta host: .../ejercicio3/www


### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# 
```
PS C:\Users\PC> docker run -d --name wordpress_container --network net-wp -p 9500:80 -v ${PWD}/ejercicio3/www:/var/www/html -e WORDPRESS_DB_HOST=mysql_container -e WORDPRESS_DB_USER=wp_user -e WORDPRESS_DB_PASSWORD=wp_password -e WORDPRESS_DB_NAME=wordpress_db wordpress:latest
>>
3dfbe50372d1a4e7f8fa86c01697865c366aec6cf0f205748625551b3679b4ee
PS C:\Users\PC>
```

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA



