# Diccionario de Datos

Tabla Jugadores
| Campo            | Tipo    | Descripción                         |
| ---------------- | ------- | ----------------------------------- |
| jugador_id       | VARCHAR | Identificador único del jugador     |
| fecha_registro   | DATE    | Fecha en que el jugador se registró |
| edad_nino        | INT     | Edad del jugador                    |
| tipo_suscripcion | VARCHAR | Tipo de suscripción                 |


Tabla Productos
| Campo       | Tipo    | Descripción                |
| ----------- | ------- | -------------------------- |
| producto_id | VARCHAR | Identificador del producto |
| nombre      | VARCHAR | Nombre del producto        |
| categoria   | VARCHAR | Categoría                  |
| precio      | DECIMAL | Precio de venta            |
| costo       | DECIMAL | Costo del producto         |

Tabla Ubicaciones
| Campo        | Tipo    | Descripción                |
| ------------ | ------- | -------------------------- |
| ubicacion_id | VARCHAR | Identificador de ubicación |
| estado       | VARCHAR | Estado                     |
| municipio    | VARCHAR | Municipio                  |
| latitud      | DECIMAL | Coordenada geográfica      |
| longitud     | DECIMAL | Coordenada geográfica      |

