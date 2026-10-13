# Metodología | Benidorm 3D

## 1. Objetivo

Benidorm 3D es un proyecto de visualización geoespacial tridimensional orientado a la exploración del tejido urbano de Benidorm (Alicante, España).

El proyecto combina datos de edificios procedentes del Catastro INSPIRE, procesamiento de datos geoespaciales y tecnologías de cartografía web para facilitar la consulta y representación del entorno construido.

## 2. Fuente de datos

La base cartográfica de edificios procede de datos del Catastro INSPIRE.

El conjunto utilizado contiene 21.324 objetos cartográficos almacenados en formato GeoJSON. Las geometrías son de tipo MultiPolygon y se mantienen los identificadores y atributos disponibles en los datos de origen.

El número de objetos no debe interpretarse necesariamente como el número de edificios únicos, ya que algunos registros pueden representar partes de edificios.

## 3. Preparación de los datos

Los datos se prepararon para su utilización en un visor web basado en MapLibre GL JS.

El conjunto GeoJSON contiene geometrías y atributos que permiten identificar los objetos, consultar información disponible y aplicar filtros temáticos.

Entre los atributos utilizados se encuentran:

- `localId`: identificador local del objeto.
- `gml_id`: identificador del objeto en los datos de origen.
- `numberOfFloorsAboveGround`: número de plantas sobre rasante.
- `numberOfFloorsBelowGround`: número de plantas bajo rasante.
- `height_m`: altura estimada utilizada para la representación tridimensional.

## 4. Estimación de alturas

Para representar los edificios en tres dimensiones se utiliza una altura estimada calculada a partir del número de plantas sobre rasante:

`height_m = numberOfFloorsAboveGround × 3`

Se aplica una equivalencia de tres metros por planta como aproximación cartográfica.

Este procedimiento permite generar una representación volumétrica homogénea, pero no constituye una medición real de la altura de cada construcción. Los resultados deben interpretarse como una estimación visual.

Cuando el número de plantas sobre rasante es cero, la altura calculada también es cero. Estos registros se conservan para no eliminar datos sin una justificación técnica.

## 5. Controles de calidad

Se realizaron comprobaciones sobre la estructura, los atributos y las geometrías del conjunto de datos.

Los resultados obtenidos fueron:

- 21.324 objetos examinados.
- Ningún identificador duplicado detectado en `localId` y `gml_id`.
- Sin valores ausentes en los campos principales examinados.
- Coherencia entre la altura calculada y el número de plantas sobre rasante.
- 21.324 geometrías de tipo MultiPolygon.
- 21.324 geometrías válidas según la comprobación topológica realizada con Shapely.
- Sin geometrías vacías o ausentes detectadas.

Estas comprobaciones verifican determinadas propiedades técnicas del conjunto, pero no garantizan por sí solas la exactitud de todos los atributos ni la correspondencia con las alturas reales.

## 6. Visualización web

La aplicación utiliza MapLibre GL JS para mostrar la cartografía interactiva y representar los edificios mediante extrusión tridimensional.

La interfaz incorpora herramientas de consulta y exploración, como búsqueda por identificadores, filtros por altura y número de plantas, estadísticas y controles de visualización.

El formato GeoJSON facilita la integración de las geometrías y los atributos en el visor.

## 7. Limitaciones

- Las alturas son estimaciones basadas en el número de plantas.
- Algunos objetos pueden representar partes de edificios.
- La calidad de los atributos depende de los datos de origen.
- La validez topológica no implica necesariamente exactitud temática o administrativa.
- El visor tiene fines de exploración y demostración; no sustituye a los servicios oficiales ni a las herramientas técnicas municipales.

## 8. Tecnologías

- QGIS: exploración y trabajo con información geográfica.
- Python: inspección y comprobación de datos.
- Shapely: validación topológica de geometrías.
- GeoJSON: intercambio de datos espaciales.
- MapLibre GL JS: cartografía web y representación 3D.

