# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado o utilizó otros comandos que no se mencionan al realizar la práctica también se debe documentar.


# Reflexión sobre los conocimientos adquiridos

### Antes de realizar esta práctica, mis conocimientos sobre Docker y la configuración de contenedores para aplicaciones complejas como Drupal y PostgreSQL eran muy escasas, especialmente en cuanto a la gestión de redes y volúmenes. Sin embargo, a lo largo de la actividad, adquirí un mejor entendimiento sobre cómo conectar contenedores, configurar variables de entorno y resolver problemas comunes que surgen en el proceso. Admito que, me estanque demasiado en como hacer un index.html y sobretodo que se ejecute bien en el docker. Fue donde mas batallé, sinceramente me llevo mucho trabajo entender.

### Uno de los mayores aprendizajes fue la importancia de entender la estructura de red entre contenedores y cómo Docker maneja los volúmenes para persistir datos. También comprendí mejor el uso de comandos avanzados como docker exec para acceder a los contenedores y crear directorios faltantes que causaban errores en la instalación de Drupal.

## Solución de problemas

Durante la práctica, enfrenté varios problemas que requirieron paciencia y múltiples intentos hasta encontrar la solución correcta y sobretodo resolverlo bien:

## Errores que presente fueron:

### nombre de contenedor en uso: Al intentar crear el contenedor server-drupal, recibi un mensaje de conflicto de nombres, y poruspuesto la solución fue detener y eliminar el contenedor existente con docker stop y docker rm.

### Directorio de traducción faltante en Drupal: La instalación de Drupal arrojó un error de falta de directorio para las traducciones. En donde revisando la practica anterior utilice el comando docker exec -it server-drupal mkdir -p /var/www/html/sites/default/files/translations para crear el directorio requerido dentro del contenedor, lo que permitió que la instalación continuara.

### Problemas de conexión: Configurar la base de datos en Drupal me llevó a aprender sobre la importancia de utilizar el nombre del servicio en lugar de una dirección IP directa.

# Conclusion 
Gracias a esta practica, ahora me siento mucho más confiada al usar Docker para realizar el proceso de aplicaciones complejas, solucionar errores de conexión y sus respectivas configuraciones pertinentes, cabe añadir que esta practica si aprendi bien aunque algunas cosas mismo no entendia por lo que me llegue a frustrar.
