# Imagenes

**Construir una imagen**
```sh
docker build --tag nombre_imagen .
```

**Renombrar una imagen local**
```sh
docker image tag source[:TAG] new_name[:TAG]

docker image tag cron-ticker:1.0.0 cron-ticker:buffalo
```

**Correr una imagen**
```sh
docker container run nombre_imagen
```

**Forzar una plataforma en la construccion**
```sh
FROM --platform=linux/amd64 node:19.2-alpine3.16
```

**Build imagenes multiplataformas**
```sh
docker buildx create --name mybuilder --driver docker-container --bootstrap

docker builder ls

docker buildx use mybuilder

Dentro del docker file cambiar el from a:
FROM --platform=$BUILDPLATFORM node:19.2-alpine3.16

ahora al construir la imagen podemos especificar las plataformas y hacer el push al repositorio
```
