# Proceso ETL -PimPamBoing

## 1. Extracción

Se cargaron las 4 fuentes de datos crudas del proyecto:

| Fuente | Contenido | Registros |
|---|---|---|
| `jugadores` | Datos del niño/jugador (edad, tipo de suscripción, fecha de registro) | 250 |
| `productos` | Catálogo de mercancía (nombre, categoría, precio, costo) | 8 |
| `ubicaciones` | Catálogo geográfico (estado, municipio, latitud, longitud) | 289 |
| `ventas_sucias` | Transacciones de venta, con errores intencionales de captura | 3,379 |

## 2. Transformación (limpieza)

La tabla `ventas_sucias` presentaba dos tipos de anomalías, detectadas mediante una auditoría inicial con `isnull()` y `duplicated()`:

- **116 registros duplicados exactos**: renglones idénticos (misma venta, mismo jugador, mismo producto, misma ubicación, misma cantidad) capturados más de una vez con distinto `id_renglon`. Se eliminaron con `drop_duplicates()` sobre las columnas relevantes.
- **68 registros con cantidad inválida**: 34 con valor nulo y 34 con valor cero. Se descartaron en lugar de imputarse, ya que no existe una variable confiable en el dataset que permita estimar la cantidad real sin distorsionar los cálculos financieros posteriores.

Adicionalmente, se verificó la **integridad referencial**: que cada `producto_id`, `jugador_id` y `ubicacion_id` de las ventas existiera en su catálogo correspondiente (resultado: 0 llaves huérfanas). Los tres catálogos se normalizaron en texto (mayúsculas/minúsculas consistentes) y se tiparon las fechas correctamente.

Como resultado, `ventas_sucias` pasó de 3,379 a **3,195 registros limpios**.

## 3. Enriquecimiento

Con las ventas ya limpias, se unieron (`merge`) las tres tablas de catálogo para construir un dataset relacional único, y se calcularon los indicadores financieros por transacción:

- **Ingreso_Total** = cantidad × precio
- **Costo_Total** = cantidad × costo
- **Utilidad** = Ingreso_Total − Costo_Total

## 4. Carga (Load)

El proceso ETL exporta 5 archivos CSV listos para el análisis exploratorio (EDA), sin necesidad de volver a tocar los datos crudos:

- `dataset_maestro_vividchroma.csv` (3,195 filas × 21 columnas)
- `jugadores_limpio.csv`
- `productos_limpio.csv`
- `ubicaciones_limpio.csv`
- `ventas_limpio.csv`

## Diagrama del proceso



![diagrama-etl](diagrama-etl-link-imagen)
