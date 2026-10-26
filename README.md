# Análisis de campañas de marketing con funciones de Excel

Proyecto de limpieza, transformación y análisis de **2.535 registros de campañas de marketing digital (2025)**, desarrollado **exclusivamente con funciones de Excel**.

## Objetivo

Preparar una base de datos confiable y responder preguntas de negocio sobre inversión, ingresos y eficiencia de las campañas por canal, país, campaña, dispositivo y mes.

## Herramientas y funciones

- **Excel** (tablas, formato condicional, gráficos y segmentación en el dashboard)
- **Limpieza:** ESPACIOS, NOMPROPIO, CONTAR.SI.CONJUNTO
- **Análisis:** SUMAR.SI, SUMAR.SI.CONJUNTO, BUSCARX, BUSCARV, INDICE + COINCIDIR, FILTRAR, MAX, LET

## Estructura del libro

| Pestaña | Contenido |
|---|---|
| Data Original | Datos sin modificar |
| Auditoria | Inventario de datos y espacios en blanco |
| Control de datos | Duplicados y validaciones de coherencia |
| Datos Limpios | Base final depurada (2.484 registros) |
| Data nuevas columnas | Base limpia con las métricas calculadas |
| Preguntas de negocio | 40 preguntas resueltas con funciones |
| Dashboard | Indicadores, gráficos interactivos y hallazgos |

## Diccionario de datos resumido

**Columnas originales:** Fecha, ID_Campaña, Canal, País, Dispositivo, Impresiones, Clics, Conversiones, Gasto_EUR, Ingresos_EUR, Nuevos_Clientes, Tipo_Campaña, Responsable.

**Columnas calculadas:**

| Columna | Qué mide | Fórmula |
|---|---|---|
| CTR | % de impresiones que generan un clic | Clics / Impresiones |
| Tasa de conversión | % de clics que terminan en conversión | Conversiones / Clics |
| CPC | Coste promedio por clic | Gasto / Clics |
| CPA | Coste promedio por conversión | Gasto / Conversiones |
| ROAS | Ingresos por cada euro invertido | Ingresos / Gasto |
| % ROAS | ROAS expresado en porcentaje | ROAS × 100 |
| Rendimiento | Clasificación según ROAS: Excelente (≥ 10), Bueno (≥ 5), Débil (≥ 2), Deficiente (< 2) | Condicional sobre ROAS |
| Seguimiento | `Revisar` si ROAS < 2 o CPA > 100 €; si no, `Normal` | Condicional |
| Objetivo ROAS / CPC objetivo | Valores esperados por canal | `BUSCARX` / `BUSCARV` |
| Etiqueta canal-país, Año, Mes, Número de mes, Día de la semana | Apoyo para segmentar y ordenar | Concatenación y funciones de fecha |

## Calidad de los datos

| Etapa | Resultado |
|---|---|
| Registros originales | 2.535 |
| Valores en blanco detectados | 62 (Canal 20, País 16, Gasto 8, Responsable 18) |
| Categorías unificadas | *Espana* → *España* (7 valores) |
| Registros duplicados eliminados | 35 |
| Registros con error de gasto eliminados | 16 |
| **Base final** | **2.484 registros** (≈ 2 % descartado) |

Los vacíos de Canal, País y Responsable se rellenaron con `Por identificar` para no perder esos registros.

## Resultados clave

| Indicador | Valor |
|---|---:|
| Inversión total | 11.366.489,30 € |
| Ingreso total | 91.281.852,80 € |
| Clics | 11.419.844 |
| Conversiones | 807.971 |
| CTR global | 5,16 % |
| Tasa de conversión global | 7,08 % |
| CPC global | 0,995 € |
| CPA global | 14,07 € |
| ROAS global | 8,03 |

## Análisis general

- **Rentabilidad alta y homogénea.** Cada euro invertido generó 8,03 € de ingresos. La inversión y los ingresos están muy repartidos entre los seis canales identificados (cada uno aporta alrededor del 16 %).
- **Email es el canal más eficiente**: ROAS más alto (8,71) y CPA más bajo (12,60 €). **Display** es el de menor ROAS (7,65) y menos conversiones (125.267), y **Affiliate** el de mayor CPA (15,20 €).
- **España concentra casi la mitad del negocio**: cerca del 49 % del gasto y de los ingresos, y 379.772 conversiones. **México** lidera en ROAS (8,32) e **Italia** es el mercado más pequeño.
- **Los registros sin canal o país identificado rinden peor.** Los de país no identificado tienen un CPA de 26,46 € y un ROAS de 4,82, lo que refuerza la importancia de registrar bien esos campos en origen.
- **Estacionalidad:** noviembre es el mejor mes (ROAS 9,27) y diciembre cae a 7,47. Enero y octubre concentran más registros de buen rendimiento.
- **Puntos a revisar:** el 15,6 % de los registros (387) tiene ROAS inferior a 2, y la combinación **Paid Search - Portugal** combina gasto alto con ROAS bajo (5,51).
- **Picos que conviene estudiar:** Display en noviembre (ROAS 14,98), Email en abril (13,76) y la campaña Cmp-019 en agosto (25,77).
- **Otros destacados:** Cmp-005 tiene el mejor ROAS acumulado de las campañas (10,30), Tablet es el dispositivo con mejor ROAS (8,75) y Marta López es la responsable con mejor ROAS acumulado (8,41).

## Alcance y límites

Este proyecto se centra en demostrar el uso de funciones de Excel para limpiar, transformar y consultar datos. No incluye análisis estadístico ni pruebas de significancia; los hallazgos son descriptivos.

## Próximos pasos

Repetir el proyecto con los mismos datos usando **Power Query** (limpieza), **Power Pivot** (modelo y medidas DAX), **tablas dinámicas** y **gráficos dinámicos**, para comparar ambos enfoques.
