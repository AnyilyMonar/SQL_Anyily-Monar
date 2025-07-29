# SQL_Anyily-Monar
## Descripción del negocio – Inmobiliaria Nacional

La base de datos está diseñada para una inmobiliaria con operación a nivel nacional, que administra la compra, venta y arriendo de propiedades residenciales y comerciales en distintas ciudades del país.
La inmobiliaria cuenta con un equipo de agentes que representan las propiedades y gestionan el contacto con los clientes interesados.
El sistema permite registrar información detallada de cada propiedad, su ubicación, su agente responsable, clientes interesados, historial de precios y contratos realizados.

Esta base de datos facilita el manejo de inventario inmobiliario, la trazabilidad de clientes, y la gestión de operaciones de venta y arriendo.

## Listado de Tablas
| **Nombre Tabla**    | **Descripción**                                                        |
| ------------------- | ---------------------------------------------------------------------- |
| `Propiedad`         | Almacena información de propiedades disponibles para venta o arriendo. |
| `Tipo_Propiedad`    | Define los tipos de propiedad que maneja la inmobiliaria.              |
| `Estatus_Propiedad` | Define el estado actual de la propiedad.                               |
| `Agente`            | Datos del personal que gestiona las propiedades.                       |
| `Cliente`           | Información de personas interesadas en comprar o arrendar.             |
| `Propietario`       | Propietarios que registran propiedades con la inmobiliaria.            |
| `Sucursal`          | Sedes físicas de la inmobiliaria.                                      |
| `Ciudad`            | Ciudades donde hay sucursales o propiedades.                           |
| `Estado`            | Departamentos o regiones del país.                                     |
| `Contrato`          | Relación formal entre cliente y propiedad (venta o arriendo).          |

### Tabla 1. Estado
| Campo      | Tipo de Dato | NOT NULL | Key | Otros           |
| ---------- | ------------ | -------- | --- | --------------- |
| estado\_id | INT          | ✅        | PK  | AUTO\_INCREMENT |
| nombre     | VARCHAR(100) | ✅        |     |                 |
