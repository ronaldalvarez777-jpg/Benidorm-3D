# Flujo de trabajo SIG | Benidorm 3D

## Visión general

El proyecto sigue un flujo de trabajo que conecta la adquisición de datos geoespaciales con su preparación, control de calidad y publicación en un visor cartográfico web tridimensional.

## Fases del proceso

### 1. Obtención de datos

**Entrada:** datos de edificios del Catastro INSPIRE.

Se utilizan los identificadores, atributos y geometrías disponibles en los datos de origen.

### 2. Preparación de la información

**Proceso:** transformación y organización de los datos para su uso en la aplicación.

El conjunto de edificios se integra en un archivo GeoJSON que contiene las geometrías y los atributos necesarios para la consulta y visualización.

### 3. Generación de alturas estimadas

**Proceso:** cálculo de una altura aproximada a partir del número de plantas sobre rasante.

`height_m = numberOfFloorsAboveGround × 3`

La equivalencia de tres metros por planta es una hipótesis de representación, no una medición oficial.

### 4. Control de calidad

**Herramientas:** Python y Shapely.

Se comprueban, entre otros aspectos:

- Presencia de geometrías y atributos principales.
- Duplicidad de identificadores.
- Coherencia entre plantas y altura estimada.
- Tipo y validez topológica de las geometrías.

### 5. Desarrollo del visor

**Tecnología:** MapLibre GL JS.

El GeoJSON se integra en la aplicación web para representar los edificios mediante extrusión 3D y permitir la exploración interactiva de sus atributos.

### 6. Consulta y análisis exploratorio

El usuario puede buscar objetos por identificador, filtrar edificios por altura o número de plantas y consultar estadísticas y atributos disponibles.

### 7. Revisión y mejora

El proyecto queda abierto a futuras mejoras, como incorporar modelos digitales del terreno, enriquecer los atributos, optimizar el rendimiento y ampliar las herramientas de análisis espacial.

## Resumen del flujo

**Catastro INSPIRE → Preparación de datos → GeoJSON → Control de calidad → MapLibre GL JS → Visor urbano 3D**

## Alcance

Este flujo documenta el proceso de desarrollo del prototipo. No implica que se hayan realizado análisis de terreno, cálculos de alturas reales ni validaciones oficiales que no estén descritos expresamente en la documentación.
