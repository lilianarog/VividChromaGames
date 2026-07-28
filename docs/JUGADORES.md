JUGADORES
──────────────
PK jugador_id
fecha_registro
edad_nino
tipo_suscripcion
      │
      │ 1:M
      ▼

VENTAS_DETALLE

PK id_renglon
venta_id
fecha_venta
FK jugador_id
FK producto_id
FK ubicacion_id
cantidad
canal_venta

      ▲
      │
      │ M:1
PRODUCTOS

PK producto_id
nombre
categoria
precio
costo

      ▲
      │
      │ M:1

UBICACIONES

PK ubicacion_id
estado
municipio
latitud
longitud