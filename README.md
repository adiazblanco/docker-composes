# Proyecto Docker

Este repositorio contiene archivos `docker-compose.yml` y `Dockerfile` para configurar y ejecutar varios contenedores Docker. Siga las instrucciones a continuación para configurar y ejecutar los contenedores en su máquina local.

## Prerrequisitos

- Docker: [Instalar Docker](https://docs.docker.com/get-docker/)
- Docker Compose: [Instalar Docker Compose](https://docs.docker.com/compose/install/)

## Estructura del Proyecto

```
.
├── servicio1
│   ├── Dockerfile
│   └── ...
├── servicio2
│   ├── docker-compose.yml
│   └── ...
└── README.md
```

## Cómo Usar

### 1. Clonar el Repositorio

```bash
git clone git@github.com:adiazblanco/docker-composes.git
cd docker-composes
```

### 2. Construir y Ejecutar los Contenedores

Utiliza Docker Compose para construir y ejecutar los contenedores definidos en `docker-compose.yml`.

```bash
docker-compose up --build
```

Esto construirá las imágenes de Docker y levantará los contenedores. Puedes acceder a los servicios en los puertos definidos en el archivo `docker-compose.yml`.

### 3. Detener y Eliminar los Contenedores

Para detener los contenedores, usa:

```bash
docker-compose down
```

Esto detendrá y eliminará los contenedores, redes y volúmenes definidos en el archivo `docker-compose.yml`.

## Configuración Personalizada

Si necesitas realizar configuraciones personalizadas, puedes editar los archivos `Dockerfile` y `docker-compose.yml` según tus necesidades.

### Ejemplo de `docker-compose.yml`

```yaml
version: '3.8'

services:
  servicio1:
    build: ./servicio1
    ports:
      - "8080:8080"
    environment:
      - VARIABLE_ENTORNO=valor

  servicio2:
    build: ./servicio2
    ports:
      - "8081:8081"
    environment:
      - OTRA_VARIABLE_ENTORNO=otro_valor
```

### Ejemplo de `Dockerfile` para `servicio1`

```dockerfile
# Utiliza una imagen base de Docker oficial
FROM node:14

# Establece el directorio de trabajo en el contenedor
WORKDIR /app

# Copia el package.json y el package-lock.json
COPY package*.json ./

# Instala las dependencias
RUN npm install

# Copia el resto de la aplicación
COPY . .

# Expone el puerto en el que la aplicación se ejecutará
EXPOSE 8080

# Define el comando para ejecutar la aplicación
CMD ["npm", "start"]
```
