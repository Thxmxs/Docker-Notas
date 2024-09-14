#FROM node:19.2-alpine3.16
#FROM --platform=amd64 node:19.2-alpine3.16
FROM --platform=$BUILDPLATFORM node:19.2-alpine3.16

# cd app dentro del contenedor
WORKDIR /app

#copiamos los archivos al Destino que es /app
COPY app.js package.json ./

#Ejecutar comandos
RUN npm install

COPY . .

#Realizar testing
RUN npm run test

#Eliminar archivos no necesarios en produccion
RUN rm -rf tests && rm -rf node_modules

#Unicamente las dependencias de prod
RUN npm install --prod

#Ultimo comando para hacer el run de la imagen
CMD [ "node", "app.js" ]