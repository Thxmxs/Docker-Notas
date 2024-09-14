**Descargar una imagen**
```sh
docker pull IMAGE_NAME
docker pull postgres:15.1
```

**Ejecutar una imagen** 

```sh
docker container run IMAGE_NAME
```
**Ejecutar una imagen dettached(no bloquea la consola) en el puerto 80 (puerto de mi equipo: puerto del contenedor)** 
```sh
docker container run -d -p 80:80 IMAGE_NAME
```

**Asignar nombre al contenedor** 
```sh
docker container run -d -p 80:80 IMAGE_NAME
```

**Mostrar todos los contenedores** 
```sh
docker container ls
```

**Mostrar todos los contenedores + los ocultos** 
```sh
docker container ls -a
```

**Detener y eliminar un contenedor** 
```sh
docker container ls -a
```

**detener contenedor y removerlo de forma forzada** 
```sh
docker container rm -f <container-id>
```


**listado de las imagenes** 
```sh
docker images ls
```

**Eliminar imagen** 
```sh
docker image rm <image-id>
```

**Eliminar todas las imagenes sin utilizar** 
```sh
docker image prune
```
**ver logs**

```sh
docker container logs <container-id>
```

**Iniciar un comando shell dentro del contenedor (it = interactive terminal)**

```sh
docker exec -it CONTAINER EXECUTABLE
docker exec -it web bash
docker exec -it web /bin/sh
```

**variables de entorno**

```sh
#Ejemplo postgres creacion de contenedor con env variable
$ docker run --name some-postgres -e POSTGRES_PASSWORD=mysecretpassword -d postgres
```

