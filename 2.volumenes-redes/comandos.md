# Administración de volumenes

**Creación**
```sh
docker volume create todo-db
```

**Listar volumes**
```sh
docker volume ls
```

**Inspeccionar volume**
```sh
docker volume inspect todo-db
```

**Borrar volumes no usados**
```sh
docker volume prune
```

**Borrar volume especifico**
```sh
docker volume rm volume_name
```

**Usar un volumen al correr un contenedor**
```sh
docker run -v todo-db:/etc/todos getting-started
```

**Tipos de volumes**

1. **named volumes**: es el mas utilizado le asignamos el nombre a un volume
2. **bind volumes**: sirve para enlazar el filesystem local con el de docker
3. **anonymous volume**: docker le asigna un nombre random al volume

**Creación mariadb con un volume**
```sh
--volume nombre_volume:fileSystemContenedor (ver doc image)

 docker container run \
-dp 3306:3306 \
--name world-db \
--env MARIADB_USER=example-user \
--env MARIADB_PASSWORD=user-password \
--env MARIADB_ROOT_PASSWORD=root-secret-password \
--env MARIADB_DATABASE=world-db \
--volume world-db:/var/lib/mysql \
mariadb:jammy
```

**Creación contenedor phpmyadmin**

```sh
docker container run \
--name phpmyadmin \
-dp 8080:80 \
-e PMA_ARBITRARY=1 \
phpmyadmin:5.2.0-apache
```

# Administración de networks

**Crear una nueva red**
```sh
docker network create todo-app
```

**Listar redes**
```sh
docker network ls
 ```
 
**Borrar redes sin utilizar**
```sh
docker network prune
 ```

**conectar contenedores a una network**
```sh
docker network connect nombre_red id_contenedor
 ```

**Levantar container con la red desde el inicio**
```sh
docker container run \
-dp 3306:3306 \
--name world-db \
--env MARIADB_USER=example-user \
--env MARIADB_PASSWORD=user-password \
--env MARIADB_ROOT_PASSWORD=root-secret-password \
--env MARIADB_DATABASE=world-db \
--volume world-db:/var/lib/mysql \
--network world-app \
mariadb:jammy

docker container run \
--name phpmyadmin \
-dp 8080:80 \
-e PMA_ARBITRARY=1 \
--network world-app \
phpmyadmin:5.2.0-apache
 ```


**Bind volumes**
Nos permite conectar nuestro filesystem con el filesystem del container, y reflejar los cambios que se hagan en local
dentro de el container y viceversa

**Test con app de nest**
```sh
-w es el working directory
sh -c abre una terminal interactiva al final de la creacion y ejecuta los comandos
-v "$(pwd)":/app monta los archivos actuales en la ruta /app dentro del container

docker container run \
 --name nest-app \
 -w /app \
 -dp 80:3000 \
 -v "$(pwd)":/app \
 node:18-alpine3.20 \
 sh -c "yarn install && yarn start:dev"
  ```

**Abrir terminal interactiva dentro del contenedor**
 ```sh
 docker exec -it <container-id> /bin_/sh
 
  ```

