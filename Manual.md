# Manual para Respaldo Automatizado
El objetivo de este script es automatizar el respaldo de archivos especificos que se encuentran en un servidor  
remoto OWGIS desde nuestro equipo local.

## Requerimientos Técnicos
   * Sistemas operativo Ubuntu
   * Lenguaje __bash__
   * Herramienta __RSYNC__  

## Pasos previos
Se debe tener una serie de configuraciones previas que nos permitiran hacer los respaldos de los archivos de manera  
automatizada sin que tengamos que supervisar personalmente cada vez que se ejecuta el script.

__Creamos alias al servidor remoto__

   1. Ingresamos al archivo `.ssh/config` para crear el alias de nuestro servidor  
   ```bash
   Host servidor_OWGIS  
   HostName 132.248.xxx.xxx  
   User user  
   Port xxxx  
   ```  
   2. Creamos nuestras credenciales para poder ingresar al servidor sin la necesidad de autenticarnos  
  ```ssh-keygen -b 4096 -t rsa ```  
  nos genera dos llaves 
  Copiamos nuestra llave pública al servidor remoto OWGIS
  ```ssh-copy-id user@servidor_OWGIS```
  
   
   
