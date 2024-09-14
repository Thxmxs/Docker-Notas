docker compose nos sirve para crear un multiples contenedores reutilizables

# Ejecutar docker compose
docker compose up -d

# Nomenclatura  de los contenedores creados automaticamente
<project-name>_<service-name>_<replica_number>

# Limpiar todo
docker compose down

# Revisar los logs de los contenedores levantados con el compose
docker compose logs -f

# Volumes
agregando al final, le indicamos que nos cree un volumen llamado postgres-db
volumes:
  postgres-db:

si agregamos external:true va a usar un volumen que ya se creo anteriormente
volumes:
  postgres-db:
    external: true

Bind volumes en docker compose
(aqui mapeamos la carpeta relativa ./postgres con data del container)
volumes:
      - ./postgres:/var/lib/postgresql/data


# COMANDOS ADICIONALES
si necesitamos que se ejecute un comando despues que se monte el contenedor podemos hacerlo con:

 command: ['--comando_a_ejecutar'] 

 al final del archivo

 # Variables de entornos

 se define como un listado debajo de environment utilizando key=value

  environment:
      - MONGO_INITDB_ROOT_USERNAME=${MONGO_USERNAME}

# Utilizar variables de entorno del .env file

se utiliza ${nombreVariable}

# para hacer referencia los dns de los contenedores es por el nombre del contenedor no del servicio

# ver builds creadas

docker buildx ls