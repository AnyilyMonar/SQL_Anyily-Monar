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

### Tabla 2. Ciudad
| Campo                   | Tipo de Dato | NOT NULL | Key | Otros           |
| ----------------------- | ------------ | -------- | --- | --------------- |
| ciudad\_id              | INT          | ✅        | PK  | AUTO\_INCREMENT |
| nombre                  | VARCHAR(100) | ✅        |     |                 |
| estado\_id              | INT          | ✅        | FK  |                 |
| codigo\_postal\_prefijo | VARCHAR(10)  |          |     |                 |

### Tabla 3. Sucursal
| Campo        | Tipo de Dato | NOT NULL | Key | Otros               |
| ------------ | ------------ | -------- | --- | ------------------- |
| sucursal\_id | INT          | ✅        | PK  | AUTO\_INCREMENT     |
| nombre       | VARCHAR(100) | ✅        |     |                     |
| direccion    | VARCHAR(150) | ✅        |     |                     |
| ciudad\_id   | INT          | ✅        | FK  |                     |
| telefono     | VARCHAR(15)  | ✅        |     |                     |
| email        | VARCHAR(100) | ✅        |     |                     |
| gerente\_id  | INT          |          | FK  | referencia a agente |

### Tabla 4. Agente
| Campo                  | Tipo de Dato | NOT NULL | Key | Otros           |
| ---------------------- | ------------ | -------- | --- | --------------- |
| agente\_id             | INT          | ✅        | PK  | AUTO\_INCREMENT |
| nombre                 | VARCHAR(50)  | ✅        |     |                 |
| apellido               | VARCHAR(50)  | ✅        |     |                 |
| telefono               | VARCHAR(15)  | ✅        |     |                 |
| email                  | VARCHAR(100) | ✅        |     |                 |
| fecha\_contratacion    | DATE         | ✅        |     |                 |
| sucursal\_id           | INT          | ✅        | FK  |                 |
| licencia\_inmobiliaria | VARCHAR(50)  |          |     |                 |
| especializacion        | VARCHAR(100) |          |     |                 |

### Tabla 5. Tipo_Propiedad
| Campo               | Tipo de Dato | NOT NULL | Key | Otros           |
| ------------------- | ------------ | -------- | --- | --------------- |
| tipo\_propiedad\_id | INT          | ✅        | PK  | AUTO\_INCREMENT |
| nombre              | VARCHAR(50)  | ✅        |     |                 |
| descripcion         | VARCHAR(150) |          |     |                 |

### Tabla 6. Estatus_Propiedad
| Campo       | Tipo de Dato | NOT NULL | Key | Otros           |
| ----------- | ------------ | -------- | --- | --------------- |
| estatus\_id | INT          | ✅        | PK  | AUTO\_INCREMENT |
| nombre      | VARCHAR(50)  | ✅        |     |                 |
| descripcion | VARCHAR(100) |          |     |                 |

### Tabla 7. Propietario
| Campo                | Tipo de Dato | NOT NULL | Key | Otros             |
| -------------------- | ------------ | -------- | --- | ----------------- |
| propietario\_id      | INT          | ✅        | PK  | AUTO\_INCREMENT   |
| nombre               | VARCHAR(50)  | ✅        |     |                   |
| apellido             | VARCHAR(50)  | ✅        |     |                   |
| telefono             | VARCHAR(15)  | ✅        |     |                   |
| email                | VARCHAR(100) | ✅        |     |                   |
| direccion            | VARCHAR(150) |          |     |                   |
| documento\_identidad | VARCHAR(50)  | ✅        |     |                   |
| tipo                 | VARCHAR(20)  | ✅        |     | Persona o Empresa |

### Tabla 8. Cliente
| Campo           | Tipo de Dato  | NOT NULL | Key | Otros                     |
| --------------- | ------------- | -------- | --- | ------------------------- |
| cliente\_id     | INT           | ✅        | PK  | AUTO\_INCREMENT           |
| nombre          | VARCHAR(50)   | ✅        |     |                           |
| apellido        | VARCHAR(50)   | ✅        |     |                           |
| telefono        | VARCHAR(15)   | ✅        |     |                           |
| email           | VARCHAR(100)  | ✅        |     |                           |
| tipo            | VARCHAR(20)   | ✅        |     | Comprador/Inquilino/Ambos |
| presupuesto     | DECIMAL(12,2) |          |     |                           |
| preferencias    | TEXT          |          |     |                           |
| fecha\_registro | DATE          | ✅        |     |                           |

### Tabla 9. Propiedad
| Campo                       | Tipo de Dato  | NOT NULL | Key | Otros           |
| --------------------------- | ------------- | -------- | --- | --------------- |
| propiedad\_id               | INT           | ✅        | PK  | AUTO\_INCREMENT |
| direccion                   | VARCHAR(150)  | ✅        |     |                 |
| ciudad\_id                  | INT           | ✅        | FK  |                 |
| codigo\_postal              | VARCHAR(10)   |          |     |                 |
| superficie                  | DECIMAL(10,2) | ✅        |     | m²              |
| habitaciones                | INT           | ✅        |     |                 |
| baños                       | INT           | ✅        |     |                 |
| año\_construccion           | INT           | ✅        |     |                 |
| descripcion                 | TEXT          |          |     |                 |
| precio                      | DECIMAL(15,2) | ✅        |     |                 |
| tipo\_propiedad\_id         | INT           | ✅        | FK  |                 |
| estatus\_id                 | INT           | ✅        | FK  |                 |
| fecha\_listado              | DATE          | ✅        |     |                 |
| agente\_id                  | INT           | ✅        | FK  |                 |
| propietario\_id             | INT           | ✅        | FK  |                 |
| caracteristicas\_especiales | TEXT          |          |     |                 |

### Tabla 10. Contrato
| Campo            | Tipo de Dato  | NOT NULL | Key | Otros                         |
| ---------------- | ------------- | -------- | --- | ----------------------------- |
| contrato\_id     | INT           | ✅        | PK  | AUTO\_INCREMENT               |
| cliente\_id      | INT           | ✅        | FK  |                               |
| propiedad\_id    | INT           | ✅        | FK  |                               |
| tipo\_contrato   | VARCHAR(20)   | ✅        |     | Venta/Arriendo                |
| fecha\_inicio    | DATE          | ✅        |     |                               |
| fecha\_fin       | DATE          |          |     | Solo arriendos                |
| valor            | DECIMAL(15,2) | ✅        |     |                               |
| estado\_contrato | VARCHAR(30)   | ✅        |     | Activo, Finalizado, Cancelado |
