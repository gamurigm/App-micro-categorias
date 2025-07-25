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

## Ejecución

1. Compila el proyecto:
   ```sh
   mvn clean package
   ```
2. Construye y levanta los contenedores:
   ```sh
   docker-compose up --build
   ```

La API estará disponible en http://localhost:8080/api/categorias

## Modelo de datos
- id: Long (autogenerado, PK)
- nombre: String (obligatorio, único, 3-50)
- descripcion: String (opcional, máx 255)
- fechaCreacion: LocalDateTime (asignada automáticamente)
