 
# descargar una imagen (dockerhub)
docker pull IMAGE_NAME
docker pull postgres:15.1

# ejecutar una imagen
docker container run IMAGE_NAME

# ejecutar una imagen dettached en el puerto 80 (puerto de mi equipo: puerto del contenedor)
docker container run -d -p 80:80 IMAGE_NAME

# asignar nombre al contenedor
docker container run --name MyContainer IMAGE_NAME

# Mostrar todos los contenedores
docker container ls

# Mostrar todos los contenedores corriendo
docker container ls -a

# detener y eliminar un contenedor
docker container stop <container-id>
docker container rm <container-id>

# detener contenedor y removerlo de forma forzada
docker container rm -f <container-id>

## Limpieza de imagenes

# listado de las imagenes
docker images

# Eliminar una imagen especifica
docker image rm <image-id>

# Eliminar imagenes paradas
docker image prune

# Eliminar todas las imagenes no usadas
docker image prune -a

## Logs y examinar contenedores

# Logs
docker container logs <container-id>

# Iniciar un comando shell dentro del contenedor (it = interactive terminal)
docker exec -it CONTAINER EXECUTABLE
docker exec -it web bash
docker exec -it web /bin/sh

## Variables de entorno
depende de la imagen

# Ejemplo postgres creacion de contenedor con env variable
$ docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
