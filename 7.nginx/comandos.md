# Nginx 
es un servidor web que se puede usar como proxy inverso, balanceador de carga, proxy de correo y cache http

**A Continuacion se explica el paso a paso por la construccion del dockerfile**
```sh
#Instalacion de las dependencias

FROM node:19-alpine3.15 as dev-deps
WORKDIR /app
COPY package.json package.json
RUN yarn install --frozen-lockfile

#Se copian los modulos de node dentro de el contenedor y se hace build de prod

FROM node:19-alpine3.15 as builder
WORKDIR /app
COPY --from=dev-deps /app/node_modules ./node_modules
COPY . .
RUN yarn build

#Se expone el puerto 80 de nginx
FROM nginx:1.23.3 as prod
EXPOSE 80

#Se copia build de prod dentro de nginx
COPY --from=builder /app/dist /usr/share/nginx/html

#Se copian los assets dentro de la build de prod
COPY assets/ /usr/share/nginx/html/assets

#Se elimina archivo default de nginx
RUN rm /etc/nginx/conf.d/default.conf

#Se copia archivo de configuracion de nginx para utilizar router de react dentro de nginx
COPY nginx/nginx.conf /etc/nginx/conf.d/

#Se ejecuta nginx y con daemon off se ejecuta en primer plano
CMD [ "nginx","-g", "daemon off;" ]
```
