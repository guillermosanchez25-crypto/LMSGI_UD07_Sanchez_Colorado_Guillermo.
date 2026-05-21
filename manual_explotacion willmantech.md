# Manual de Explotación en WillmanTech S.L

-----------------------------------------------------------------------------------

## 1. Introducción y Arquitectura

El sistema ERP/CRM ha sido desplegado mediaante contenedores Docker utilizando Docker Compose 

 ### Se divide la arquitectura en estos servicios:  

- Servicio ERP principal
- Base de datos PostgreSQL
- Servicio CRM para gestion comercial
- Servicios de generacion de archivos PDF

 ### El sistema permite gestionar:

- Clientes
- Ventas
- Facturas
- Informes de empresa
- Exportacion de datos

## 2. Guia de instalacion y reinstalación: 

### Requisitos antes de empezar: 

- Docker
- Docker Compose
- PostgreSQL
- Acceso a la terminal de Linux

  En el entorno escribes:

POSTGRES_DB=erp

POSTGRES_USER=odoo

POSTGRES_PASSWORD=admin

 En la terminal escribes:

 docker compose up -d 

 Y lo verificas con:

 docker ps

 Desde el navegador:

 http://localhost:8069

 Reinstalas el entorno con:

 docker compose down
 
 docker compose up -d
