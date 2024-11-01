# VOLUMEN TIPO HOST
Un volumen host (o bind mount) es un tipo de volumen donde se monta un directorio o archivo específico del sistema de archivos del host en un contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](img/directorio.PNG)

### Crear un volumen tipo host con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](img/volumen-host.PNG)
# COMPLETAR CON EL COMANDO
``` docker run -d -p 80:80 -v /c/Users/PC/Desktop/nginx/html:/usr/share/nginx/html nginx:alpine ```

### ¿Qué sucede al ingresar al servidor de nginx?
##### Al momento que ingresamos al servidor de Nginx en la siguiente direccion https:localhost, nos indica el contenido del archivo index. En el cual, nos refleja en el navegador un mensaje de "Hola, este es un servidor Nginx en Docker"

### ¿Qué pasa con el archivo index.html del contenedor?
#### El archivo index.html es servido directamente por Nginx desde el contenedor. Como se ha configurado un volumen, Nginx accede al archivo index.html desde mi carpeta local del host (C:\Users\PC\Desktop\nginx\html), y cualquier cambio en este archivo se refleja de inmediato en el servidor sin necesidad de reconstruir el contenedor.

### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
#### Al ingresar al servidor de Nginx en http://localhost, apreciamos la página web del template que hemos descargado. Nginx servirá este contenido como la nueva página principal.

### Eliminar el contenedor
# COMPLETAR CON EL COMANDO
```
PS C:\Users\PC> docker rm -f  f55451628425            
f55451628425
PS C:\Users\PC> 
```

### ¿Qué sucede al crear nuevamente el mismo contenedor con volumen de tipo host a los directorios definidos anteriormente?
#### Cualquier cambio que se realice en los archivos dentro de html se reflejará automáticamente en el servidor sin necesidad de reconstruir el contenedor, ya que el volumen enlaza la carpeta local con el contenedor.

### ¿Qué hace el comando pwd?
#### El comando pwd muestra la ruta completa del directorio de trabajo actual en la terminal. Es útil para saber en qué carpeta nos ubicamos y para especificar rutas en comandos de Docker o scripts de configuración, especialmente para enlazar volúmenes en Docker.



### Volumen tipo host usando PWD y PowerShell
```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v ${PWD}/<ruta relativa>:<ruta absoluta> <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (Git Bash)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd -W)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

### Volumen tipo host usando PWD (en Linux)

```
docker run -d --name <nombre contenedor> --publish published=<valorPuertoHost>,target=<valor> -v $(pwd)/html:/usr/share/nginx/html <nombre imagen>:<tag> 
```

