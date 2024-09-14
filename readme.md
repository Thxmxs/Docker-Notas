# Docker: notas y ejemplos

Este repositorio contiene apuntes y ejemplos relacionados con Docker. Organizado en diferentes carpetas, cubre desde comandos básicos hasta configuraciones más avanzadas como multistage builds, Docker Compose, y GitHub Actions.

## Estructura del repositorio

### 1. **bases**
   - Comandos básicos para trabajar con Docker, incluyendo:
     - Descargar imágenes desde DockerHub.
     - Ejecutar y gestionar contenedores.
     - Limpiar imágenes y contenedores.
     - Examinar logs y ejecutar comandos dentro de contenedores.
     - Uso de variables de entorno.

### 2. **volumenes-redes**
   - Comandos relacionados con la creación y gestión de volúmenes y redes en Docker.
   -  persistir datos y conectar contenedores entre sí.

### 3. **multi-container**
   - Explicación sobre Docker Compose para levantar múltiples contenedores de forma organizada.
   - **Incluye:**
     - Ejecución de Docker Compose.
     - Uso de volúmenes en Compose.
     - Variables de entorno y bind volumes.
   - **Proyectos:** Ejemplos con MongoDB + Nest y Postgres + PgAdmin.

### 4. **imagenes**
   - Comandos para la creación y gestión de imágenes en Docker.
   - Ejemplo de creación de imagen Docker con el proyecto `cron-ticker`.
   - **Proyecto cron-app -> ver Dockerfile**

### 5. **multistage-build**
   - Información sobre cómo realizar un build multistage en Docker Compose y construir imágenes multiplataforma.
   - Optimización de imágenes Docker y despliegues en diferentes entornos.
   - **ver proyectos teslo-shop y cron-app**

### 6. **github-actions**
   - Explicación de cómo usar GitHub Actions para la construcción automática de contenedores.
   - **ver yaml graphql/actions/.github/workflows/docker-image.yml**

### 7. **nginx**
   - Uso de Nginx como servidor web en contenedores Docker.
   - Servir aplicaciones o archivos usando Nginx en Docker.
   - **ver proyecto react-heroes -> Dockerfile y nginx/nginx.conf**

## Ver repositorio localmente

1. Clona el repositorio:
   ```bash
   git clone https://github.com/Thxmxs/Docker-Notas.git
