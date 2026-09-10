# Sistema de detección y alarma contra incendios — Paxton Carnegie Library

Diseño completo de un sistema de detección, alarma y notificación de incendios para un edificio
real en Estados Unidos, aplicando la normativa estadounidense vigente en su jurisdicción.

**EL-4601 Normalización Técnica para Electrónica** · Proyecto No. 1
Escuela de Ingeniería Electrónica — Centro Académico de Alajuela, Instituto Tecnológico de Costa Rica

---

## De qué se trata

El proyecto recorre la cadena completa **de la norma al plano**: determinar qué códigos —y qué
edición de cada uno— son exigibles en la jurisdicción del inmueble, caracterizar el edificio a
partir de planos públicos, seleccionar una familia de equipos compatible, ubicar cada dispositivo
según un criterio normativo verificable y comprobar eléctricamente el sistema.

El principio de trabajo fue que **ningún dispositivo se coloca «a ojo»**: cada cantidad, posición
y característica responde a una sección concreta de la norma.

## El edificio

**Paxton Carnegie Library** — 254 S. Market Street, Paxton, Ford County, Illinois, EE. UU.
Biblioteca Carnegie de 1903, documentada en el registro **HABS IL-329** (planos públicos de la
Library of Congress).

Dos niveles ocupados · 4 363 ft² (405 m²) · carga ocupacional ≈53 → **IBC Grupo A-3** ·
una sola conexión vertical interior · planta irregular con rotonda semicircular y estanterías en
abanico radial.

## La solución

Arquitectura **direccionable** sobre panel **Fire•Lite Alarms MS-9600LS**, con un lazo SLC y
cuatro circuitos NAC.

| Dispositivo | Modelo | Cantidad |
|---|---|---:|
| Detector de humo fotoeléctrico | Fire•Lite SD355 | 15 |
| Detector térmico | Fire•Lite H355R | 2 |
| Estación manual | Fire•Lite BG-12LX | 4 |
| Horn/strobe | System Sensor P2R | 11 |
| Estrobo | System Sensor SR | 4 |
| Anunciador remoto | Fire•Lite ANN-80 | 1 |
| Panel de control | Fire•Lite MS-9600LS | 1 |

## Resultados

| Verificación | Resultado | Límite | Utilización |
|---|---|---|---|
| Consumo en alarma | 1,924 A | 7,0 A | 27,5 % |
| NAC más cargado | 0,397 A | 3,0 A | 13,2 % |
| Caída de tensión, peor caso | 19,72 V | ≥ 16 V | 3,72 V de margen |
| Capacidad del lazo SLC | 21 puntos | 318 | 10,7 % |
| Nivel sonoro, peor caso | 74,3 dBA | ≥ 70 dBA | 4,3 dB de margen |
| Batería | 4,26 AH calculados → 12 AH instalados | mínimo del panel | 2,8× de margen |

Los cálculos siguen el método del propio fabricante (Tablas 5.3 y 5.4 del manual PN 52646:B) y
las resistencias de conductor salen del NEC, Capítulo 9, Tabla 8.

## Normativa aplicada

La edición exigible no era evidente. Illinois no adopta un código de construcción estatal general,
así que hubo que recorrer la cadena:

> **41 Ill. Adm. Code Parte 100** (§100.7) → **NFPA 101-2015** (cap. 2) → **NFPA 72, edición 2013**

Todas las citas del proyecto corresponden a esa edición. Se aplicaron además **NFPA 70 (NEC)**
Art. 760 para el cableado, el **IBC** para clasificación de ocupación y exigibilidad, y
**UL 864** para el listado de los equipos.

## Estructura del repositorio

```
Informe_Tecnico_Proyecto1_Paxton.docx   Entregable principal (62 páginas)
Planos/                                 Fuente draw.io + exportaciones PDF/PNG
Planos_HABS/                            Planos originales del registro HABS IL-329
BOM_Calculos/                           Lista de materiales y hojas de cálculo
Datasheets/                             Documentación de fabricante
Secciones/                              Borradores por sección y registro de revisión
```

Los planos se abren en [app.diagrams.net](https://app.diagrams.net) →
`Planos/Paxton_Sistema_Alarma.drawio` (3 páginas: piso 1, sótano y riser).

## Notas

El diseño declara **cobertura selectiva** y no total, y documenta siete limitaciones con sus
recomendaciones asociadas (Sección 9 del informe). El proceso de verificación detectó cinco
errores de dato y diecinueve defectos en el juego de planos, registrados en el Anexo D.

Se usaron herramientas de IA como apoyo; los prompts están íntegros en el Anexo A y toda la
información obtenida por esa vía fue contrastada contra la fuente primaria.

## Equipo

Walter Alfaro Ulate · Sebastián Meneses Castillo · Thomas Reed Víquez
Setiembre de 2026

---

Trabajo académico. No constituye un diseño aprobado para construcción. Los planos HABS son de
dominio público (Library of Congress); la documentación de fabricante pertenece a sus titulares y
se incluye solo como respaldo de los cálculos; los textos de las normas no se reproducen.
