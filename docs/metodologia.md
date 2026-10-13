# Metodología | Benidorm 3D

## 1. Objetivo y alcance

Benidorm 3D es un prototipo de visualización geoespacial tridimensional orientado a la exploración del tejido urbano de Benidorm (Alicante, España).

El proyecto integra datos de edificios procedentes del Catastro INSPIRE, un proceso de preparación y comprobación de información geográfica y una aplicación web interactiva desarrollada con MapLibre GL JS.

Su finalidad es facilitar la exploración visual de las construcciones y la consulta de los atributos disponibles. No constituye un sistema oficial de información catastral ni una herramienta de certificación urbanística.

**[Abrir el visor web](https://ronaldalvarez777-jpg.github.io/Benidorm-3D/)**

## 2. Fuente y estructura de los datos

La fuente de información de edificios utilizada es el Catastro INSPIRE.

El conjunto procesado contiene 21.324 objetos cartográficos almacenados en formato GeoJSON, con geometrías de tipo `MultiPolygon` y atributos asociados.

Los registros pueden representar edificios completos o partes de edificios. Por tanto, el número de objetos cartográficos no equivale necesariamente al número de edificios únicos.

Los identificadores y atributos se conservan para permitir la consulta de los objetos y su trazabilidad dentro del conjunto procesado.

## 3. Preparación de la información

Los datos se organizan en un archivo GeoJSON para su integración en la aplicación web.

Entre los campos utilizados se encuentran:

- `localId`: identificador local del objeto.
- `gml_id`: identificador del objeto en los datos de origen.
- `numberOfFloorsAboveGround`: número de plantas sobre rasante.
- `numberOfFloorsBelowGround`: número de plantas bajo rasante.
- `height_m`: altura estimada utilizada para la representación tridimensional.

El GeoJSON reúne las geometrías y los atributos que consume el visor. La documentación describe el conjunto procesado y sus controles; no implica que todos los atributos de origen hayan sido verificados individualmente frente a fuentes externas.

## 4. Estimación de alturas

Para generar la representación volumétrica se utiliza una altura aproximada basada en el número de plantas sobre rasante:

`height_m = numberOfFloorsAboveGround × 3`

Se aplica una equivalencia de tres metros por planta como hipótesis de representación cartográfica.

Esta regla permite asignar una dimensión vertical a los objetos, pero no representa una medición de la altura real de cada construcción ni una altura oficial proporcionada por el Catastro.

Los registros sin plantas sobre rasante registradas pueden conservar una altura estimada de cero. En consecuencia, la representación visual depende de la disponibilidad y el contenido del atributo de origen.

## 5. Controles de calidad

Se realizaron comprobaciones técnicas sobre la estructura, los identificadores, los atributos seleccionados y las geometrías del conjunto procesado.

Los resultados documentados son:

- 21.324 objetos examinados.
- Sin identificadores duplicados detectados en `localId` y `gml_id`.
- Sin valores ausentes en los campos principales examinados.
- Coherencia entre `height_m` y el cálculo basado en el número de plantas.
- 21.324 geometrías de tipo `MultiPolygon`.
- 21.324 geometrías válidas según la comprobación topológica realizada con Shapely.
- Sin geometrías vacías o ausentes detectadas en la auditoría.

Estos resultados corresponden a las comprobaciones realizadas sobre el conjunto procesado. La validez topológica no demuestra por sí sola que una geometría represente exactamente la construcción real, ni que los atributos sean completos, actuales o administrativamente correctos.

## 6. Visualización y consulta web

La aplicación utiliza MapLibre GL JS para representar la cartografía interactiva y mostrar los edificios mediante extrusión tridimensional.

Las funcionalidades documentadas incluyen:

- Búsqueda mediante `localId` y `gml_id`.
- Filtrado por altura estimada y número de plantas sobre rasante.
- Consulta de atributos disponibles en ventanas emergentes.
- Estadísticas descriptivas del conjunto.
- Controles para mostrar u ocultar los edificios.

La geometría y los atributos se integran mediante GeoJSON. La visualización 3D facilita la exploración del entorno construido, pero no sustituye a un modelo tridimensional validado mediante mediciones de altura.

## 7. Tecnologías utilizadas

- **QGIS:** exploración y trabajo con información geográfica.
- **Python:** preparación, inspección y comprobación de datos.
- **Shapely:** comprobación de validez geométrica.
- **GeoJSON:** formato de intercambio de geometrías y atributos.
- **MapLibre GL JS:** cartografía web interactiva y representación 3D.
- **Catastro INSPIRE:** fuente de los datos de edificios utilizados.

## 8. Limitaciones

- Las alturas son estimaciones calculadas a partir del número de plantas.
- Algunos objetos pueden representar partes de edificios y no edificios únicos.
- La disponibilidad y precisión de los atributos dependen de los datos de origen.
- Las comprobaciones geométricas no certifican la exactitud temática, métrica o administrativa.
- El visor tiene fines de exploración y demostración; no sustituye a los servicios oficiales del Catastro ni a las herramientas técnicas municipales.

## 9. Documentación relacionada

- [README del proyecto](../README.md)
- [Flujo de trabajo SIG](flujo-trabajo.md)
- [Repositorio en GitHub](https://github.com/ronaldalvarez777-jpg/Benidorm-3D)
- [Visor publicado](https://ronaldalvarez777-jpg.github.io/Benidorm-3D/)

---

**GeoNOV | Geospatial Intelligence**
