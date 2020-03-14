
## Primeros pasos

1. Creamos e inicializamos todos los contenedores
```sh
docker-compose up -d --build
```

2. Entramos en el contenedor php
```sh
docker exec -it <nombre_proyecto>_php bash
```

3. Eliminamos el fichero `.gitignore` y creamos el proyecto del tipo deseado

```sh
rm .gitignore
```
```sh
# Symfony, aplicación web tradicional
composer create-project symfony/website-skeleton .

# Symfony, aplicación de consola, microservicio o API
composer create-project symfony/skeleton .

# Laravel
composer create-project --prefer-dist laravel/laravel .
```

4. En el navegador, acceder a la URL
```
localhost:8080
```


### Comandos Docker

```sh
# Visualiza los contenedores en ejecución
docker-compose top

# Acceder a un contenedor
docker exec -it <nombre_contenedor> bash

# Inicializar servicios
docker-compose start

# Paramos todos los contenedores
docker-compose stop

# Paramos y borramos todos los contenedores
docker-compose down
```

