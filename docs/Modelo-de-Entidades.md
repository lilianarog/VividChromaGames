# Modelo de Entidades

## Descripción

El modelo de entidades representa la estructura lógica de la información utilizada en el proyecto **PIM PAM BOING**, permitiendo organizar los datos relacionados con los jugadores del videojuego, la mercancía infantil y la ubicación geográfica de las ventas.

Las entidades fueron definidas considerando las necesidades de análisis del negocio y las preguntas de negocio planteadas en la etapa anterior.

## Entidades principales

### Jugadores

Contiene la información básica de los usuarios registrados en el videojuego.

**Atributos**

- jugador_id
- fecha_registro
- edad_nino
- tipo_suscripcion

---

### Productos

Contiene la información de la mercancía oficial comercializada por Vivid Chroma Games.

**Atributos**

- producto_id
- nombre
- categoria
- precio
- costo

---

### Ubicaciones

Almacena la información geográfica asociada a los clientes y ventas.

**Atributos**

- ubicacion_id
- estado
- municipio
- latitud
- longitud

---

### Ventas

Registra cada compra realizada por un cliente.

**Atributos esperados**

- venta_id
- jugador_id
- producto_id
- ubicacion_id
- fecha_venta
- cantidad
- canal_venta