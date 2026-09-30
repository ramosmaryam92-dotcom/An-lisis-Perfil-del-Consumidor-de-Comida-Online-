# Analisis-Perfil-del-Consumidor-de-Comida-Online-
Este repositorio contiene un script en Python utilizando **Pandas** para realizar la limpieza, transformación y análisis exploratorio de un conjunto de datos sobre preferencias y comportamiento de clientes de comida en línea.

##  Estructura y Descripción del Proyecto

El análisis parte de un archivo CSV local (`onlinef.csv`) con un total de 388 registros y 14 columnas iniciales que describen aspectos demográficos, geográficos y de satisfacción del consumidor.

### 1. Limpieza y Preparación de Datos (`Data Cleaning`)
Durante la fase inicial de inspección, se identificaron y eliminaron columnas irrelevantes o con ruido para optimizar el dataset:
* **`Unnamed: 13`**: Columna vacía o sin metadatos útiles. Fue eliminada del DataFrame.
* **`Output`**: Contenía valores binarios (Sí/No) que no correspondían a la descripción original de estados de pedidos (ej. *pending, confirmed, delivered*). Al no aportar valor analítico claro, se decidió eliminarla.

### 2. Resumen Estadístico
El dataset incluye variables numéricas clave como la edad (`Age`), tamaño de familia (`Family size`), coordenadas geográficas (`latitude`, `longitude`) y código postal (`Pin code`).
* **Edad promedio**: $\approx 24.6$ años (con un rango entre 18 y 33 años).
* **Tamaño familiar promedio**: $\approx 3.28$ miembros.

---

##  Hallazgos y Análisis Clave

El análisis profundiza en la segmentación de clientes y su nivel de satisfacción (**Feedback**):

* **Distribución de Opiniones (`Feedback`)**:
  * **Positive**: 317 registros
  * **Negative**: 71 registros
  * Esto muestra una clara tendencia mayoritaria de satisfacción entre los encuestados.

* **Segmentación por Edades (`Age Categories`)**:
  Se agrupó a los clientes en rangos etarios para identificar al público principal:
  * **Entre 20 y 25 años**: 255 clientes (segmento dominante).
  * **Mayor a 25 años**: 119 clientes.
  * **Entre 18 y 20 años**: 13 clientes.
  
  *Nota analítica:* Los usuarios de **23 y 22 años** son los que reportan mayor cantidad de feedback positivo (65 y 53 menciones respectivamente).

* **Relación de Ingresos y Ocupación en el Segmento Principal (20-25 años con Feedback Positivo)**:
  * El cruce de datos muestra que la gran mayoría de este segmento corresponde a **estudiantes sin ingresos monetarios formales (`No Income / Student`)**, seguidos por empleados con ingresos moderados (`10001 to 25000`).

* **Distribución Geográfica (`Pin code`)**:

  * Al filtrar por el código postal principal (`560009`), se observa que la base de usuarios predominante sigue siendo de estudiantes sin ingresos o con ingresos bajos (`Below Rs.10000`).

---

## Exportación de Resultados
Una vez finalizado el proceso de transformación y filtrado, el DataFrame limpio y enriquecido con la nueva columna de categorías de edad es exportado a un archivo CSV listo para reportes o dashboards:
```python
datos.to_csv("Analisis_definitivo.csv", index=False)
```

##  Requisitos y Ejecución
* Python 3.12+
* Librería Pandas

