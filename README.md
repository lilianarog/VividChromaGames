# PimPamBoing — Proyecto Integrador

Proyecto final de Ciencia de Datos y Analítica de Negocios (Mayo–Agosto 2026). PimPamBoing es un videojuego infantil de VividChroma Games con una tienda de mercancía física (mochilas, stickers, peluches, cómics) en el estado de Puebla. Este repositorio documenta el proyecto de punta a punta: generación y limpieza de datos, análisis exploratorio, catálogo de KPI, dashboards interactivos para el dueño y para el cliente, y el reporte ejecutivo con hallazgos y recomendaciones de negocio.

## Qué se hizo en cada parte técnica

**Proceso ETL** (`notebooks/Proceso_ETL.ipynb`) — Extrae las 4 fuentes crudas (jugadores, productos, ubicaciones, ventas), audita y limpia `ventas_sucias` (116 duplicados exactos y 68 registros con cantidad inválida eliminados), corrige nombres de producto mal capturados, verifica integridad referencial entre tablas, une las 4 fuentes en un dataset maestro y calcula Ingreso Total, Costo Total y Utilidad por transacción. Incluye el catálogo de 4 KPI de negocio (Etapa 7) con metas, alertas y semáforos. Exporta 5 CSV limpios listos para el análisis.

**Análisis Exploratorio** (`notebooks/EDA.ipynb`) — Lee el dataset maestro ya limpio y responde las preguntas de negocio: comportamiento de ventas en el tiempo (año, mes, estacionalidad, día de la semana), productos más y menos rentables, comportamiento de clientes por tipo de suscripción, concentración geográfica de ventas (con mapa de burbujas y mapa de calor), y evolución de la rentabilidad. Cierra con conclusiones accionables para el negocio.

**Dashboard del dueño** (`dashboards/dashboard_dueno.html`) — Panel interactivo de una sola página con navegación por secciones (Resumen, Ventas, Productos, Clientes, Geografía, Alertas), filtros en vivo por año/categoría/municipio/suscripción, tarjetas de KPI con semáforo, y alertas de negocio ligadas a las metas del catálogo de KPI (caída de ventas, margen bajo, conversión a Premium). No requiere instalación ni servidor — es un solo archivo HTML.

**Dashboard del cliente** (`dashboards/dashboard_cliente.html`) — Panel personal por jugador: buscas tu ID y ves solo tu propia información (historial de compras, gasto por categoría, producto y categoría favorita, nivel de "explorador" calculado con tu gasto real, beneficios de tu suscripción, y una recomendación de producto explicada). Nunca muestra información de otros jugadores — cumple el requisito de privacidad de la Etapa 9.

## Cómo correr el proyecto

1. Corre `notebooks/Proceso_ETL.ipynb` de principio a fin — genera los CSV limpios.
2. Corre `notebooks/EDA.ipynb` — lee esos CSV y genera el análisis.
3. Abre los dashboards `.html` en `dashboards/` directo en el navegador (no requieren instalación).

## Entregables del proyecto

### Contexto y planeación
| # | Entregable | Qué es para PimPamBoing | Ubicación |
|---|---|---|---|
| 1 | Contexto del negocio | Qué es PimPamBoing, quién lo opera y por qué existe la tienda de mercancía física | [docs/Contexto-del-negocio.md](docs/Contexto-del-negocio.md) |
| 2 | Planteamiento del problema | Qué decisión de negocio no se puede tomar hoy sin este proyecto (falta de visibilidad de ventas/rentabilidad) | [docs/Planteamiento del problema.README.md](docsPlanteamiento-del-problema.md) |
| 3 | Objetivos | Metas concretas del proyecto (limpiar datos, definir KPI, construir dashboards) | [docs/Objetivos.md](docs/Objetivos.md) |
| 4 | Preguntas de negocio | Las preguntas que el EDA y los dashboards responden (¿qué se vende más? ¿dónde? ¿quién compra?) | [docs/Preguntas-de-negocio.md](docs/Preguntas-de-negocio.md) |
| 5 | Identificación de stakeholders | Quién usa cada entregable: el dueño (decisiones), el jugador/cliente (su cuenta) | [docs/Identificación-de-stakeholders.md](docs/Identificación-de-stakeholders.md) · [docs/Lista-de-Stakeholders.md](docs/Lista-de-Stakeholders.md) |
| 6 | Modelo de entidades | Cómo se relacionan jugadores, productos, ubicaciones y ventas entre sí | [docs/Modelo-de-Entidades.md](docs/Modelo-de-Entidades.md) |
| 7 | Alcances y limitaciones | Qué cubre el proyecto y qué se dejó fuera (p. ej. no hay datos de inventario) | [docs/Alcances y limitaciones.md](docs/Alcances-y-limitaciones.md) |

### Datos y simulación
| # | Entregable | Qué es para PimPamBoing | Ubicación |
|---|---|---|---|
| 8 | Descripción de fuentes | Qué contiene cada una de las 4 tablas crudas | [docs/Descripción-de-Fuentes.md](docs/Descripción-de-Fuentes.md) |
| 9 | Diccionario de datos | Significado de cada columna del dataset maestro | [docs/Diccionario-de-Datos.md](docs/Diccionario-de-Datos.md) |
| 9 | Reglas de simulación | Cómo se generaron los datos sintéticos de venta | [docs/Reglas-de-Simulación.md](docs/Reglas-de-Simulación.md) |
| 10 | Script generador | Código que produjo el dataset crudo | [`notebooks/generador_csv.ipynb`](./notebooks/generador_csv.ipynb) |
| # | Descripción | Detalle | Enlaces / Rutas |
|---|---|---|---|
| # | Descripción | Detalle | Enlaces / Rutas |
|---|---|---|---|
| **11** | **Dataset original** | Los 4 CSV/XLS crudos, tal como se recibieron | • [`jugadores-sucio.csv`](ProcesoETL/datos-antes/jugadores-sucio.csv)<br>• [`productos-sucio.csv`](ProcesoETL/datos-antes/productos-sucio.csv)<br>• [`ubicaciones-sucio.csv`](ProcesoETL/datos-antes/ubicaciones-sucio.csv)<br>• [`ventas_sucias-sucio.csv`](./ProcesoETL/datos-antes/ventas_sucias-sucio.csv) |
| **12** | **Dataset procesado** | Los CSV limpios que produce el ETL | • [`jugadores_limpio.csv`](Notebook-etl/jugadores_limpio.csv)<br>• [`productos_limpio.csv`](Notebook-etl/productos_limpio.csv)<br>• [`ubicaciones_limpio.csv`](Notebook-etl/ubicaciones_limpio.csv)<br>• [`ventas_limpio.csv`](Notebook-etl/ventas_limpio.csv) |
| 13 | Justificación de los datos / Jugadores | Por qué el perfil de jugadores simulado es representativo | [docs/JUGADORES.md](docs/JUGADORES.md) · [docs/Justificación-de-los-Datos.md](docs/Justificación-de-los-Datos.md) |
| 14 | Clasificación de tipos de datos | Tipo de dato de cada campo (categórico, numérico, fecha, etc.) | [docs/clasificacion-tipos-datos.md](docs/clasificacion-tipos-datos.md) |

### ETL 
| # | Entregable | Qué es para PimPamBoing | Ubicación |
|---|---|---|---|
| 15 | Proceso ETL | Limpieza real: 116 duplicados y 68 cantidades inválidas eliminadas, nombres de producto corregidos, integridad referencial verificada | [notebooks/Proceso_ETL.ipynb](Notebook-etl/Proceso_ETL_VividChroma-Games.ipynb) |

### Análisis
| # | Entregable | Qué es para PimPamBoing | Ubicación |
|---|---|---|---|
| 16 | Notebook de análisis exploratorio | Ventas en el tiempo, productos, clientes, geografía y rentabilidad | [notebooks/EDA.ipynb](notebooks/Proceso_EDA_VividChroma-Games.ipynb) |
| 17 | Catálogo de KPI | Los 4 KPI de negocio con fórmula, meta, alerta y semáforo | [notebooks/Proceso_ETL.ipynb — Etapa 7](docs/Reporte_Ejecutivo-KPI.md)  |

### Dashboards
| # | Entregable | Qué es para PimPamBoing | Ubicación |
|---|---|---|---|
| 18 | Dashboard del dueño | Vista ejecutiva del negocio: KPI, ventas, productos, clientes, geografía y alertas | [dashboards/dashboard_dueño](Dashboard-dueño.pbix) |
| 19 | Dashboard del cliente | Vista personal del jugador: su historial, gasto y recompensas, sin exponer datos de otros | [dashboards/dashboard_cliente.html](./dashboards/dashboard_cliente.html) |

### Resultados
| # | Entregable | Qué es para PimPamBoing | Ubicación |
|---|---|---|---|
| 20 | Hallazgos Diagnóstico Recomendaciones | Qué muestran los datos: caída de ventas 2026, Premium sin diferencia de gasto, concentración geográfica | [docs/Reporte_Ejecutivo.md — Sección 2](docs/Reporte_Ejecutivo-KPI.md) |



### Presentación
| # | Entregable | Ubicación |
|---|---|---|
| 21 | Presentación | (docs/DiapositivasExposicionPasilloPIMPAMPRESENTACIÓN.mp4) |
