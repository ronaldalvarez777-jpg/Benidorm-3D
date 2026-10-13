# Benidorm 3D | GeoNOV

### Visor urbano 3D y exploración de datos geoespaciales

Proyecto de cartografía web que integra datos de edificios del **Catastro INSPIRE** en un visor interactivo tridimensional de Benidorm (Alicante, España).

El objetivo es explorar la estructura urbana, consultar atributos catastrales disponibles y facilitar la interpretación espacial de las construcciones mediante tecnologías de información geográfica y visualización web.

**[Abrir el visor interactivo](https://ronaldalvarez777-jpg.github.io/Benidorm-3D/)**

![Vista general del visor Benidorm 3D](docs/capturas/vista-general.png)

---

## Funcionalidades principales

- **Visualización 3D:** representación extruida de las geometrías de los edificios.
- **Consulta de atributos:** inspección de identificadores y propiedades disponibles.
- **Búsqueda de objetos:** localización mediante los campos `localId` y `gml_id`.
- **Filtros espaciales visuales:** exploración por altura estimada y número de plantas sobre rasante.
- **Estadísticas descriptivas:** consulta de indicadores generales del conjunto de datos.
- **Control de visualización:** opción para mostrar u ocultar los edificios.
- **Interfaz cartográfica interactiva:** navegación y exploración del entorno urbano.

## Exploración tridimensional

![Edificios altos de Benidorm](docs/capturas/edificios-altos.png)

La representación permite explorar la distribución de los edificios y destacar construcciones que superan determinados umbrales de altura estimada.

La extrusión se basa en el número de plantas sobre rasante disponible en los datos procesados. Por tanto, la representación tridimensional es una aproximación visual y no un modelo de alturas reales verificadas.

## Consulta de información catastral

![Detalle de un objeto catastral en el visor](docs/capturas/detalle-edificio.png)

Las ventanas emergentes permiten consultar los identificadores y los atributos disponibles de cada objeto cartográfico seleccionado.

## Tecnologías

| Tecnología | Aplicación en el proyecto |
|---|---|
| MapLibre GL JS | Cartografía web interactiva y representación 3D |
| GeoJSON | Almacenamiento e intercambio de geometrías y atributos |
| Python | Preparación, inspección y validación de datos |
| Shapely | Comprobaciones de validez geométrica |
| QGIS | Exploración y tratamiento de información geográfica |
| Catastro INSPIRE | Fuente de los datos de edificios |

## Datos y metodología

El conjunto procesado contiene **21.324 objetos cartográficos** con geometrías de tipo `MultiPolygon`.

Los objetos pueden representar edificios completos o partes de edificios. En consecuencia, el número de registros no equivale necesariamente al número de edificios únicos.

### Estimación de altura

El campo `height_m` se obtiene mediante la siguiente regla:

`height_m = numberOfFloorsAboveGround × 3`

Se utiliza una equivalencia aproximada de tres metros por planta para facilitar la representación tridimensional. Esta estimación no constituye una medición oficial de la altura real de cada edificio.

Los objetos sin plantas sobre rasante registradas conservan una altura estimada de cero.

### Controles de calidad realizados

Las comprobaciones documentadas sobre el conjunto procesado indican:

- 21.324 objetos examinados.
- Sin identificadores duplicados detectados en `localId` y `gml_id`.
- Sin valores ausentes en los campos principales examinados.
- Coherencia entre `height_m` y el cálculo de plantas por tres metros.
- 21.324 geometrías de tipo `MultiPolygon`.
- 21.324 geometrías válidas según la comprobación topológica realizada con Shapely.
- Sin geometrías vacías o ausentes detectadas en la auditoría.

Estas comprobaciones evalúan propiedades técnicas concretas. No certifican por sí solas la exactitud temática, la altura real, la integridad de todos los atributos ni la correspondencia administrativa de cada objeto.

## Aplicaciones potenciales

La combinación de información catastral, análisis geoespacial y visualización tridimensional puede servir como punto de partida para explorar cuestiones relacionadas con:

- Morfología y estructura urbana.
- Distribución espacial de edificios y construcciones.
- Exploración preliminar de entornos urbanos.
- Comunicación cartográfica de información territorial.
- Desarrollo futuro de herramientas de apoyo a la planificación urbana.

Estas son posibles líneas de aplicación; el visor actual no implementa por sí mismo análisis urbanísticos reglados ni sustituye a los sistemas oficiales.

## Documentación

- [Metodología del proyecto](docs/metodologia.md)
- [Flujo de trabajo SIG](docs/flujo-trabajo.md)

## Estructura del proyecto

```text
Benidorm-3D/
├── data/
├── docs/
│   ├── capturas/
│   ├── flujo-trabajo.md
│   ├── metodologia.md
│   ├── index.html
│   └── benidorm_buildings.geojson
├── qgis/
├── web/
│   ├── index.html
│   └── benidorm_buildings.geojson
└── README.md
```

## Ejecución local

Se requiere Python 3.

Desde la carpeta raíz del proyecto, ejecuta:

```bash
cd web
python3 -m http.server 8000
```

Abre [http://localhost:8000](http://localhost:8000) en el navegador. Mantén abierta la terminal mientras utilizas la aplicación. Para detener el servidor, pulsa `Control + C`.

## Limitaciones

- Las alturas representadas son estimaciones basadas en el número de plantas.
- Algunos objetos pueden representar partes de edificios.
- La disponibilidad y precisión de los atributos dependen de los datos de origen.
- La validez geométrica no garantiza por sí sola la exactitud temática, geométrica o administrativa.
- El visor es un proyecto de exploración geoespacial y no sustituye a los servicios oficiales del Catastro ni a las herramientas técnicas municipales.

## Autoría

Proyecto personal desarrollado en el ámbito de las tecnologías de información geográfica, el tratamiento de datos espaciales y la cartografía web tridimensional.

**GeoNOV | Geospatial Intelligence**

[Visor web](https://ronaldalvarez777-jpg.github.io/Benidorm-3D/) · [Repositorio en GitHub](https://github.com/ronaldalvarez777-jpg/Benidorm-3D)
