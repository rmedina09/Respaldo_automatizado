# Manual para Respaldo Automatizado

El objetivo de este script es automatizar el respaldo de archivos especificos que se encuentran en un servidor  
remoto OWGIS desde nuestro equipo local.

## Requerimientos Técnicos
   * Sistemas operativo Ubuntu
   * Lenguaje __bash__
   * Herramienta __RSYNC__  

## Configuración del ambiente
Se debe tener una serie de configuraciones previas que nos permitiran hacer los respaldos de los archivos de manera  
automatizada sin que tengamos que supervisar personalmente cada vez que se ejecuta el script.

__Creamos un alias del servidor remoto__

   1. Ingresamos al archivo `.ssh/config` para crear el alias de nuestro servidor  
      ```bash
      Host servidor_OWGIS  
      HostName 132.248.xxx.xxx  
      User user  
      Port xxxx  
      ```  
   2. Creamos nuestras credenciales para poder ingresar al servidor sin la necesidad de autenticarnos explicitamente,  
      generando una llave privada ```id_rsa``` y una llave publica ```id_rsa.pub``` de la siguiente manera :  
      ```ssh-keygen -b 4096 -t rsa```
      Despues de generar as llaves, copiamos la llave pública al servidor remoto OWGIS:  
      ```ssh-copy-id  -i  ~/.ssh/id_rsa.pub  user@servidor_OWGIS```  
      
   Ahora ya podremos ejecutar el script sin la necesidad de autenticarnos explicitamente.
   
## Lista de archivos a respaldar

A continuación listamos una serie de carpetas que contienen los archivos que necesitamos:

  * var/www/html
  * ServerScripts
  * ServerData/OWGIS/Atlas
  * ServerData/ncWMS_Layers
  * ServerData/DataFestData
  * ServerData/GeoserverCenapredLayers
  * ServerData/GeoserverCenapredData/styles
  * ServerData/GeoserverCenapredData/workspaces
  * ServerData/GeoserverLayers
  * ServerData/GeoserverData/styles
  * ServerData/GeoserverData/workspaces
  * ServerData/ViajandoDFData
  * ServerData/GeoserverViajandoDFData/workspaces
  * ServerData/GeoserverViajandoDFData/styles
  * ServerData/GeoserverDataCaro/styles
  * ServerData/GeoserverDataCaro/workspaces
  * ServerData/GeoserverDataBeatTheBeast/styles
  * ServerData/GeoserverDataBeatTheBeast/workspaces
  * owgisconfig/ncwms/config.xml
  * owgisconfig/ncwms/palettes
 
 ## Descripción del Código
   
   
  
   
   
