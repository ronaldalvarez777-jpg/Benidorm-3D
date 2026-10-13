# Flujo de trabajo SIG | Benidorm 3D

## 1. Visión general

Benidorm 3D integra información geoespacial de edificios, comprobaciones de calidad y cartografía web tridimensional en un prototipo interactivo.

El flujo documentado conecta la fuente de datos con su preparación, la estimación de alturas, la validación técnica, el desarrollo del visor y su publicación.

## 2. Fases del proceso

### Fase 1. Obtención de datos

**Fuente:** Catastro INSPIRE.

Se parte de datos de edificios que incluyen geometrías, identificadores y atributos disponibles en origen. Los objetos pueden representar edificios completos o partes de edificios.

### Fase 2. Preparación de la información

**Formato de trabajo web:** GeoJSON.

Los datos se organizan en un conjunto de geometrías y atributos compatible con la aplicación. El resultado permite identificar los objetos y consultar los campos seleccionados desde el visor.

### Fase 3. Cálculo de alturas estimadas

**Atributo generado:** `height_m`.

La altura para la representación 3D se calcula mediante la regla:

`height_m = numberOfFloorsAboveGround × 3`

La equivalencia de tres metros por planta es una hipótesis de representación cartográfica. No es una medición de la altura real ni una validación oficial de cada edificio.

### Fase 4. Control de calidad

**Herramientas documentadas:** Python y Shapely.

Se comprueban propiedades técnicas del conjunto procesado, entre ellas:

- Presencia de geometrías y atributos principales.
- Duplicidad de identificadores.
- Coherencia entre el número de plantas y la altura estimada.
- Tipo de geometría.
- Validez topológica y ausencia de geometrías vacías.

Los controles realizados permiten detectar determinados problemas de estructura y geometría, pero no certifican la exactitud de todos los atributos ni la correspondencia con la realidad.

### Fase 5. Desarrollo del visor web

**Tecnología principal:** MapLibre GL JS.

El conjunto GeoJSON se integra en una aplicación web que permite visualizar las construcciones mediante extrusión 3D y explorar sus atributos.

Entre las herramientas disponibles se encuentran la búsqueda por identificadores, los filtros por altura y número de plantas, las estadísticas descriptivas y los controles de visualización.

### Fase 6. Publicación

**Plataforma:** GitHub y GitHub Pages.

El proyecto se mantiene en un repositorio Git para gestionar los cambios del código y la documentación. La versión web se publica mediante GitHub Pages a partir del directorio configurado para el sitio.

- [Repositorio del proyecto](https://github.com/ronaldalvarez777-jpg/Benidorm-3D)
- [Visor web publicado](https://ronaldalvarez777-jpg.github.io/Benidorm-3D/)

### Fase 7. Exploración y mejoras futuras

El visor permite explorar la distribución de los objetos, consultar sus atributos y aplicar filtros temáticos.

Como posibles líneas de evolución se plantean la optimización del rendimiento, el enriquecimiento de atributos, la incorporación de modelos digitales del terreno y el desarrollo de nuevas herramientas de análisis espacial. Estas mejoras son propuestas futuras, no funcionalidades que se den por implementadas.

## 3. Resumen del flujo

**Catastro INSPIRE → Preparación de datos → GeoJSON → Estimación de alturas → Control de calidad → MapLibre GL JS → GitHub Pages → Exploración web**

## 4. Alcance y reproducibilidad

Este documento describe las etapas generales del prototipo y las comprobaciones documentadas. No presupone que se hayan realizado procesos adicionales que no consten en el proyecto.

La reproducción exacta del proceso depende de disponer de los datos de entrada, los archivos de preparación y las herramientas utilizadas. La publicación del visor facilita la consulta de la aplicación, mientras que el repositorio permite inspeccionar el código y la documentación.

---

**GeoNOV | Geospatial Intelligence**
