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
En el esquema del ejercicio carpeta del contenedor (a) es (COMPLETAR CON LA RUTA)

Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA

### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/
En el esquema del ejercicio la carpeta del contenedor (b) es (COMPLETAR CON LA RUTA)

Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?

# COMPLETAR CON LA RESPUESTA A LA PREGUNTA



