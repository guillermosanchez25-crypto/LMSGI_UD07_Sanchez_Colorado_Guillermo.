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

  ### 1. Requisitos antes de empezar: 

- Docker
- Docker Compose
- PostgreSQL
- Acceso a la terminal de Linux

 ### 2.En el entorno escribes:

POSTGRES_DB=erp

POSTGRES_USER=odoo

POSTGRES_PASSWORD=admin

 ### 3. En la terminal escribes:

 docker compose up -d 

 Y lo verificas con:

 docker ps

 ### 4. Desde el navegador:

 http://localhost:8069

 ### 5. Reinstalas el entorno con:
 
 docker compose up -d


 ## 3. Seguridad y Control de Acceso: 

 ### 1. Controles de acceso (Roles):

 Permisos de Administrador:

 - Acceso completo
 - Gestion de usuarios
 - Configuracion total
 - Administrar modulos

Permisos de Contable:

- Gestion de facturas
- Gestion tributaria
- Exportar informes

Permisos de Comercial:

- Gestion de clientes
- Gestion de ventas
- Consulta de pedidos
  
### 2. Politica de seguridad:

- Contraseña de 8 caracteres minimo
- Usar mayusculas y numeros
- Permisos segun tu rol
- Proteger la BBDD mediante autenticacion


  ## 4. Procedimiento de Backup y Restauración:

  - En terminal ejecutas: pg_dump -U odoo erp > backup.sql
  - Para restauralo: psql -U odoo erp < backup.sql
  - Para detener servicios: docker compose stop
  - Para copiar volumenes: cp -r volumes/ backup_volumes/


  ## 5. Flujo Operativo de Facturación e Informes:

  Primero el usuario "Comercial" crea un pedido

  Despues el ERP genera una factura de forma automatica

  Luego los datos se almacenan en PostgreSQL

  Mas tarde el modulo QWeb procesa la plantilla XML

  Despues se genera el HTML dinamico

  Usamos wkhtmltopdf para transformar los HTML a archivo PDF

  Finalmente el PDF queda disponible para descargar
