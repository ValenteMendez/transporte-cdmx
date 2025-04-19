# Transporte CDMX - Datos Consolidados

Este directorio contiene datos consolidados del sistema de transporte público de la Ciudad de México, integrados a partir de diferentes fuentes de datos. Fuente: https://datos.cdmx.gob.mx/dataset/ 

## Archivos disponibles

### GeoPackage 
- **transporte_cdmx.gpkg**: Contiene dos capas
  - `estaciones`: Todas las estaciones/paradas de los diferentes modos de transporte
  - `rutas`: Todas las rutas/líneas de los diferentes modos de transporte

## Cómo usar en QGIS

1. **Carga del GeoPackage**:
   - En QGIS, ve a "Capa > Añadir capa > Añadir capa de GeoPackage"
   - Selecciona el archivo `transporte_cdmx.gpkg`
   - Selecciona ambas capas (`estaciones` y `rutas`)

2. **Filtrado por modo de transporte**:
   - Haz clic derecho en la capa > Propiedades > Filtro de entidades
   - Usa expresiones como: `"transport_mode" = 'Metro'` o `"transport_mode" = 'Metrobus'`
   - También puedes crear grupos de capas para diferentes modos de transporte

3. **Simbología por modo de transporte**:
   - Haz clic derecho en la capa > Propiedades > Simbología
   - Selecciona "Categorizado" y usa el campo "transport_mode" para asignar colores distintos

## Modos de transporte incluidos

### Definiciones detalladas

- **Metro** (estaciones y rutas): Sistema de Metro de la Ciudad de México, operado por el Sistema de Transporte Colectivo (STC). Incluye las 12 líneas del Metro y todas sus estaciones.

- **Metrobus** (estaciones y rutas): Sistema de autobuses de tránsito rápido que opera en carriles exclusivos. Actualmente incluye 7 líneas con sus respectivas estaciones.

- **RTP** (estaciones y rutas): Red de Transporte de Pasajeros, sistema de autobuses operado por el gobierno de la Ciudad de México que complementa la red de transporte masivo.

- **Trolebus** (estaciones y rutas): Sistema de autobuses eléctricos operados por el Servicio de Transportes Eléctricos (STE), que funcionan con energía eléctrica proporcionada por cables aéreos.

- **Cablebus** (estaciones y rutas): Sistema de teleférico urbano inaugurado en 2021, que conecta zonas de difícil acceso en la Ciudad de México.

- **Tren Ligero** (estaciones y rutas): Sistema de tren ligero operado por el STE que corre principalmente al sur de la ciudad, de Tasqueña a Xochimilco.

- **Concesionado** (estaciones y rutas): Transporte público operado por particulares bajo concesión gubernamental, principalmente microbuses y combis. Este conjunto incluye las paradas (13,084) y algunas rutas (331) con información detallada sobre origen-destino, corredor, empresa y nomenclatura.

- **Concesionado Ruta** (solo rutas): Conjunto de datos diferente que contiene 995 rutas del transporte concesionado. Este archivo contiene una estructura de datos distinta, enfocada en ramales y detalles específicos de cada ruta.

- **CETRAM** (solo estaciones): Centros de Transferencia Modal, puntos donde convergen diferentes sistemas de transporte para facilitar la transferencia de pasajeros. Son nodos importantes donde se conectan diferentes modos de transporte.

### Aclaración sobre conjuntos de datos similares

- **Concesionado vs Concesionado Ruta**: Son dos conjuntos de datos distintos sobre el transporte concesionado con estructuras diferentes:
  - "Concesionado rutas" (331 rutas) incluye campos como: ORIG_DEST, RUTA, SISTEMA, CORREDOR, NOMEN_COR, NOMEN_OD, EMPRESA, NOMENCL.
  - "Concesionado_Ruta" (995 rutas) incluye campos como: SISTEMA, RUTA, RAMAL, DETALLE.
  
  Ambos conjuntos representan distintos aspectos o subconjuntos del sistema de transporte concesionado, posiblemente recopilados en diferentes momentos o con diferentes metodologías.

- **Algunos conjuntos solo tienen estaciones o solo rutas** porque así estaban en los datos originales. Por ejemplo, los CETRAM son puntos de transferencia fijos, por lo que solo existen como estaciones y no como rutas.

## Disponibilidad de datos por modo de transporte

| Modo de Transporte | Estaciones | Rutas |
|--------------------|------------|-------|
| Metro              | ✓          | ✓     |
| Metrobus           | ✓          | ✓     |
| RTP                | ✓          | ✓     |
| Trolebus           | ✓          | ✓     |
| Cablebus           | ✓          | ✓     |
| Tren Ligero        | ✓          | ✓     |
| Concesionado       | ✓          | ✓     |
| Concesionado Ruta  | ✗          | ✓     |
| CETRAM             | ✓          | ✗     |

## Notas técnicas

- Todos los datos están proyectados en UTM Zona 14N (EPSG:32614)
- Se han preservado los campos originales en el GeoPackage

## Fuente de los datos

Datos integrados a partir de archivos shapefile individuales para cada modo de transporte.

## Propuesta de investigación

### Preguntas para investigación

1. **Análisis de cobertura del transporte público:**
   - ¿Cómo se distribuye espacialmente el transporte público en la Ciudad de México?
   - ¿Existen áreas de la ciudad con menor cobertura de transporte público?
   - ¿Qué zonas tienen mejor integración entre diferentes modos de transporte?

2. **Diferencias entre transporte concesionado y oficial:**
   - ¿Qué diferencias hay entre las rutas del transporte concesionado y el transporte oficial (Metro, Metrobús, etc.)?
   - ¿El transporte concesionado complementa o compite con el transporte oficial?
   - ¿Qué porcentaje de la ciudad está cubierto únicamente por transporte concesionado?

3. **Análisis de conectividad:**
   - ¿Cuáles son los principales nodos de conexión entre diferentes sistemas de transporte?
   - ¿Existen zonas aisladas que dependan de un solo tipo de transporte?
   - ¿Cómo se conectan los diferentes sistemas entre sí?

4. **Comparación entre "Concesionado" y "Concesionado Ruta":**
   - ¿Qué diferencias específicas existen entre los dos conjuntos de datos de rutas concesionadas?
   - ¿Representan diferentes tipos de servicios o son registros complementarios del mismo sistema?
   - ¿Hay superposición geográfica entre ambos conjuntos o cubren zonas diferentes?

### Metodología sugerida

Para abordar estas preguntas, sería útil:

1. Crear un mapa de calor de densidad de estaciones/paradas
2. Realizar un análisis de proximidad con áreas de influencia (buffers)
3. Comparar la cobertura espacial de los diferentes sistemas
4. Examinar detalladamente los datos de Concesionado vs Concesionado_Ruta
5. Analizar la conectividad mediante técnicas de análisis de redes