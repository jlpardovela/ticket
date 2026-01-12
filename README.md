Helpdesk API – Ticket Management System

API REST para la gestión de incidencias (tickets) con autenticación JWT y control de roles.
Pensada como proyecto de portfolio orientado a backend junior, aplicando buenas prácticas habituales en entornos reales.

📌 Descripción

Este proyecto implementa un sistema de helpdesk donde los usuarios pueden crear y gestionar incidencias, y los administradores pueden supervisarlas y resolverlas.

El foco está en:

Diseño de una API REST limpia

Seguridad (JWT, roles y control de acceso)

Reglas de negocio en capa de servicio

Persistencia con JPA

Documentación y tests básicos

🛠️ Tecnologías

Java 17

Spring Boot

Spring Web

Spring Data JPA

Spring Security + JWT

Hibernate

PostgreSQL / MySQL

Flyway (migraciones)

Swagger / OpenAPI

JUnit 5, Mockito

Docker & Docker Compose

🧱 Arquitectura

Arquitectura por capas:

Controller → expone endpoints REST

Service → lógica de negocio y validaciones

Repository → acceso a datos (JPA)

DTOs → separación entre API y modelo de dominio

Security → autenticación y autorización

Exception handling → manejo centralizado de errores

👥 Roles y permisos
USER

Crear tickets

Ver y modificar sus propios tickets

Añadir comentarios

Cerrar tickets propios

ADMIN

Ver todos los tickets

Cambiar estado, prioridad y asignación

Añadir comentarios a cualquier ticket

📂 Modelo de datos (simplificado)

User

id

email

password

role

createdAt

Ticket

id

title

description

status (OPEN, IN_PROGRESS, RESOLVED, CLOSED)

priority (LOW, MEDIUM, HIGH)

createdBy

assignedTo

createdAt / updatedAt

Comment

id

ticket

author

message

createdAt

🔐 Autenticación

Registro y login mediante email y contraseña

Autenticación basada en JWT

Contraseñas almacenadas con BCrypt

Control de acceso por rol y por propietario del recurso

📡 Endpoints principales
Autenticación

POST /auth/register

POST /auth/login

Tickets

POST /tickets

GET /tickets

GET /tickets/{id}

PATCH /tickets/{id}

POST /tickets/{id}/comments

POST /tickets/{id}/close

Incluyen:

Paginación (page, size)

Ordenación (sort)

Filtros por estado y prioridad

📑 Documentación API

Swagger disponible en:

/swagger-ui.html


Incluye:

Descripción de endpoints

DTOs

Ejemplos de request/response

Autenticación JWT desde la interfaz

🧪 Tests

Tests unitarios de la capa de servicio:

Reglas de negocio

Restricciones de acceso

Tests de integración básicos de endpoints protegidos

▶️ Ejecución en local
Requisitos

Java 17+

Maven

Base de datos (PostgreSQL o MySQL)

Pasos
git clone https://github.com/usuario/helpdesk-api.git
cd helpdesk-api
mvn spring-boot:run


Configurar las variables de entorno o application.yml según el perfil activo.

🐳 Ejecución con Docker
docker compose up --build


Esto levanta:

API Spring Boot

Base de datos

Migraciones automáticas

🚧 Posibles mejoras

Tests de integración más completos

Soft delete de tickets

Historial de cambios de estado

Notificaciones (email)

Frontend en Angular

Rate limiting y auditoría avanzada

🎯 Objetivo del proyecto

Este proyecto no pretende ser un producto final, sino demostrar:

Capacidad para diseñar y estructurar un backend realista

Conocimiento de Spring Boot y seguridad

Aplicación de buenas prácticas básicas

Código mantenible y defendible en entrevista técnica
