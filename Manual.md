# Manual para Respaldo Automatizado

El objetivo de este script es automatizar el respaldo de archivos especificos que se encuentran en un servidor  
remoto OWGIS desde nuestro equipo local.

## Requerimientos Técnicos
   * Sistemas operativo Ubuntu
   * Lenguaje __bash__
   * Herramienta __rsync__  

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

__Configuracion de nuestro manejador de base de datos__

Para poder generar los respaldos de las bases de datos en necesario que nuestro usuario tenga los permisos necesarios.  
  
  * En caso de no tener un usuario , hay que crearlo con los permisos necesarios
  ```CREATE ROLE <user> WITH LOGIN SUPERUSER CREATEROLE CREATEDB PASSWORD '<password>' VALID UNTIL 'infinity';  ```
  
  * Si el usuario no tiene los permisos entonces hay que asignarselos
  ```ALTER ROLE borrar WITH LOGIN SUPERUSER CREATEROLE CREATEDB VALID UNTIL 'infinity'; ```  
  
__Crear un cronjob que genere los archivos de respaldos .sql__

Esto se hace para que despues con ```rsync``` respaldemos la carpeta en donde se encuantran los *archivos backup*  
de las diferentes bases de datos.  
Enonces en un archivo ```.sh``` ponemos lo siguiente:

  ``` 
      #!/bin/sh 
      pg_dump -v -h <host> -d <base_datos_1> -f /$PATH/respaldos/BasesDatos/<base_datos_backup_1.sql>
      pg_dump -v -h <host> -d <base_datos_2> -f /$PATH/respaldos/BasesDatos/<base_datos_backup_2.sql>
      .
      .
      .
  ```

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
  
Estas son las bases de datos que vamos a respaldar que se encuentran en ```home/user/respaldos/BasesDatos/``` :  

  * contingencia
  * datafest
  * db_sms
  * maincca
  * pumabus
  * viajandodf
 
 ## Descripción de los scripts
 
 ___
   
   
  
   
   
