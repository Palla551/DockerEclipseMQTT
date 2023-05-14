# Comandos de docker interesantes

## Instalación de docker y docker-compose
https://docs.docker.com/engine/install/ubuntu/

## El arhcivo mosquitto.conf
Este archivo contiene toda la configuración del contenedor, una vez arrancado la configuración se copia desde el archivo local al contenedor de docker. Es por esto que, si se modifica cualquier parámetro del archivo, es necesario volver a arrancar el contenedor.

Nota: El contenedor tiene abiertos los puertos 1883 y 9001, está preparado tambien para funcionar con WebSocket, pero es necesario descomentar la linea 285 del archivo o añadir `protocol websockets`. 

Nota-2: Por otro lado, el archivo trabaja con usuario y contraseña, por lo que si se quiere utilizar sin autenticación hay que modificar la linea 535 `allow_anonymous false` => `allow_anonymous true`.

## El archivo password.txt
Este archivo contiene los usuarios y las contraseñas --encriptadas, evidentemnte-- para acceder al Broker, si quiere ignorar este archivo permita los usuarios anónimos (linea 535 `allow_anonymous false` => `allow_anonymous true`)

## Arrancar el contenedor
    1. Accede a la carpeta donde se encuentra el archivo `docker-compose.yml`
    2. docker-compose up

## Para agregar un nuevo usuario
(El contenedor debe de estar iniciado)

`docker-compose exec mqtt mosquitto_passwd -b /mosquitto/config/password.txt USUARIO CONTRASEÑA`
