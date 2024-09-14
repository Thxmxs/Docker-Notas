# Construir una imagen

docker build --tag nombre_imagen .

# Renombrar una imagen local

docker image tag source[:TAG] new_name[:TAG]

docker image tag cron-ticker:1.0.0 cron-ticker:buffalo

# Correr una imagen

docker container run nombre_imagen

# Forzar una plataforma en la construccion

FROM --platform=linux/amd64 node:19.2-alpine3.16

# Build imagenes multiplataformas
docker buildx create --name mybuilder --driver docker-container --bootstrap

docker builder ls

docker buildx use mybuilder

en docker file
FROM --platform=$BUILDPLATFORM node:19.2-alpine3.16

ahora al construir la imagen podemos especificar las plataformas y hacer el push al repositorio
docker buildx build --platform linux/amd64,linux/arm64,linux/arm/v8,linux/arm/v7 -t thxmxs/cron-app:latest --push .