# Multi-stage build
Consiste en crear multiples etapas de construccion de una imagen para mejorar la lectura, optimizacion y mantención

**Crear builder multiplataforma**
```sh
 docker buildx create \
  --name mybuilder \
  --driver docker-container \
  --use --bootstrap

sudo docker buildx build --platform linux/amd64,linux/arm64 -t thxmxs/teslo-shop:1.0.0 --push .
```

**Eliminar y cambiar de builder**
```sh
docker context use default
docker buildx rm <nombre-builder>
```
**Docker compose build**
```sh
 se usa para orquestar múltiples servicios Docker, cada uno de los cuales puede ser un contenedor. 
 La directiva build en docker-compose.yml te permite definir que la imagen de Docker se construya directamente
 a partir de un Dockerfile

 build: 
      context: . #Donde quiero que busque el dockerfile
      dockerfile: Dockerfile #nombre del dockerfile

docker compose build
```
**Docker compose en produccion**
```sh
docker compose -f docker-compose-prod.yml build

docker compose -f docker-compose-prod.yml up -d
```
