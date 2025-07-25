## Subir imagen a Docker Hub (resumen rápido)

```sh
# 1. Inicia sesión en Docker Hub (solo la primera vez)
docker login

# 2. Construye la imagen (si no la tienes ya)
docker build -t ryuzakizeitan/categorias:tagname .

# 3. Sube la imagen al repositorio de Docker Hub
docker push ryuzakizeitan/categorias:tagname
```
# API REST de Categorías

Este proyecto es una API REST desarrollada en Java con Spring Boot 3 (JDK 17) para gestionar un catálogo de categorías, persistiendo datos en MySQL y ejecutándose completamente en contenedores Docker.

## Características
- CRUD completo de categorías
- Persistencia en MySQL
- Ejecución con Docker Compose (app + base de datos)

## Endpoints principales
- `POST /api/categorias` — Crear categoría
- `GET /api/categorias` — Listar categorías
- `GET /api/categorias/{id}` — Buscar por id
- `PUT /api/categorias/{id}` — Actualizar
- `DELETE /api/categorias/{id}` — Eliminar


## Ejecución y despliegue

### 1. Compilar el proyecto localmente (opcional)
```sh
mvn clean package
```

### 2. Construir la imagen Docker
```sh
docker build -t ryuzakizeitan/categorias:latest .
```

### 3. Probar localmente con Docker Compose
```sh
docker compose up --build
```
La API estará disponible en http://localhost:8089/api/categorias

### 4. Subir la imagen a Docker Hub
1. Inicia sesión en Docker Hub:
   ```sh
   docker login
   ```

2. (Opcional) Etiqueta la imagen con un tag personalizado:
   ```sh
   docker tag ryuzakizeitan/categorias:latest ryuzakizeitan/categorias:tagname
   ```
3. Sube la imagen:
   ```sh
   docker push ryuzakizeitan/categorias:latest
   # O con un tag personalizado
   docker push ryuzakizeitan/categorias:tagname
   ```

### 5. Comandos útiles
- Ver contenedores activos:
  ```sh
  docker ps
  ```
- Ver logs de la app:
  ```sh
  docker logs <nombre_contenedor_app>
  ```
- Acceder a la base de datos MySQL:
  ```sh
  docker exec -it <nombre_contenedor_db> mysql -u root -p
  ```
- Detener y eliminar contenedores:
  ```sh
  docker compose down
  ```

### Repositorio de Docker Hub
https://hub.docker.com/r/ryuzakizeitan/categorias

## Modelo de datos
- id: Long (autogenerado, PK)
- nombre: String (obligatorio, único, 3-50)
- descripcion: String (opcional, máx 255)
- fechaCreacion: LocalDateTime (asignada automáticamente)
