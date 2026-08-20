# Registro de uso de IA — Proyecto PimPamBoing

**Herramienta utilizada:** Claude (Anthropic)
**Uso general:** apoyo para depurar el proceso ETL, construir el análisis exploratorio, definir el catálogo de KPI, generar los dashboards interactivos y redactar el reporte ejecutivo. Todo el código y los documentos generados por IA fueron revisados, probados y ajustados por el equipo antes de integrarse al proyecto — el detalle de esa revisión está en la columna "Validación".

## Cómo leer este registro

Cada fila documenta una interacción real con la IA: el prompt (redactado de forma clara, basado en lo que se preguntó en su momento), qué produjo la IA, y cómo se validó ese resultado antes de aceptarlo.

---

### 1. Diagnóstico y corrección del ETL

| Prompt | Qué generó la IA | Validación |
|---|---|---|
| "Revisa mi notebook de ETL y dime si realmente limpia los datos — no veo en ningún momento que cargue mis archivos." | Identificó que el notebook usaba un dataset inventado de 9 filas en vez de los 4 archivos CSV reales del proyecto. | Se confirmó comparando el código contra los archivos reales subidos; el diagnóstico era correcto. |
| "Corrige el ETL para que use mis archivos CSV reales y genere los CSV limpios como salida." | Reescribió la carga de datos, la limpieza (duplicados, cantidades inválidas), la unión de tablas y la exportación a 5 archivos CSV. | Se ejecutó el notebook completo de principio a fin y se verificaron las cifras resultantes (116 duplicados, 68 registros inválidos, 3,195 filas finales) contra los datos originales. |
| "El notebook marca `FileNotFoundError` al cargar los archivos." | Diagnosticó que la ruta de carga no coincidía con la ubicación real de los archivos y propuso una función de búsqueda robusta (por nombre parcial, sin depender de la extensión exacta). | Se probó en el entorno real (Jupyter local) hasta confirmar que encontraba los archivos sin importar la carpeta. |


### 2. Catálogo de KPI (Etapa 7)

| Prompt | Qué generó la IA | Validación |
|---|---|---|
| "Ayúdame a definir y calcular los KPI de negocio siguiendo esta rúbrica: [se pegó el contenido de la Etapa 7]." | Propuso 4 KPI (Ticket promedio, Margen de utilidad, Conversión a Premium, Utilidad por jugador), cada uno con fórmula, meta, alerta y semáforo, calculados sobre el dataset real. | Se validaron los valores calculados contra el dataset limpio, y se descartó un KPI candidato ("% de jugadores con 2+ compras") al comprobar que daba 100% siempre — no aportaba información útil. |

### 3. Análisis exploratorio (EDA)

| Prompt | Qué generó la IA | Validación |
|---|---|---|
| "Revisa mi notebook de EDA — ¿está usando correctamente los datos ya limpios del ETL?" | Detectó que el EDA también usaba datos inventados en vez del dataset maestro real. | Se confirmó revisando el código de carga de datos del notebook. |

### 4. Dashboards (Etapas 8 y 9)

| Prompt | Qué generó la IA | Validación |
|---|---|---|
| "Ayúdame a construir un dashboard para el dueño y uno para el cliente, siguiendo esta rúbrica: [se pegó el contenido de las Etapas 8 y 9], con navegación por botones como en este ejemplo [se adjuntó una referencia visual]." | Construyó dos archivos HTML independientes: un panel del dueño con navegación por secciones, filtros en vivo y alertas ligadas a los KPI; y un panel del cliente que muestra solo la información del jugador buscado, sin exponer datos de otros usuarios. | Se probó la navegación, los filtros y la búsqueda de distintos jugadores en el navegador antes de aceptar el resultado. |


