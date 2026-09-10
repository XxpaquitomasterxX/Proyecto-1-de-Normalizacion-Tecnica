# Diseño de un Sistema de Detección y Alarma Contra Incendios
### EL-4601 Normalización Técnica para Electrónica — Proyecto No. 1
### Unidad de Ingeniería Electrónica, Centro Académico de Alajuela

**Integrantes:** [Nombre 1] · [Nombre 2] · [Nombre 3] · [Nombre 4]
**Fecha de entrega:** miércoles 9 de septiembre
**Edificio seleccionado:** [Nombre del edificio, ciudad, estado]

> ⚠️ **Cómo usar esta plantilla:** cada sección tiene (a) lo que pide el enunciado y (b) qué escribir.
> Reemplacen todo lo que esté [entre corchetes]. Borren las notas en *cursiva* antes de entregar.
> **Recuerden:** cada decisión de diseño debe justificarse citando la norma exacta (ej. "NFPA 72, sección 17.7.3.2").

---

## Resumen ejecutivo
*Media página. Escríbanlo AL FINAL. Qué edificio, qué normas aplicaron, qué arquitectura (convencional/direccionable), fabricante principal y resultado del diseño.*

[...]

---

## 1. Marco normativo — Revisión de normas aplicables

*Objetivo: NO es una lista de normas, es un resumen de los requisitos y CÓMO afectan el diseño.*

### 1.1 Códigos, normas y estándares principales
- **NFPA 72** — National Fire Alarm and Signaling Code. [Edición: 20XX]. Rige diseño, instalación, prueba y mantenimiento de sistemas de detección y notificación.
- **NFPA 70 (NEC)** — National Electrical Code. Rige el cableado eléctrico y la alimentación del sistema.
- **IBC** (International Building Code) — cuándo se REQUIERE un sistema de alarma según ocupación y tamaño del edificio.
- **IFC** (International Fire Code) — requisitos operativos y de mantenimiento.
- [Otras que determine el grupo: NFPA 101 Life Safety Code, ADA para dispositivos visuales, UL 864, etc.]

### 1.2 Requisitos por tipo de dispositivo
*Resuman qué exige la norma para cada tipo (espaciamiento, altura, ubicación).*
| Dispositivo | Requisito normativo (resumen) | Norma / sección |
|---|---|---|
| Detectores de humo | Espaciamiento máx., distancia a paredes/HVAC | NFPA 72 §17.7 |
| Estaciones manuales | A la salida, altura 1.07–1.22 m, cada 60 m | NFPA 72 §17.14 |
| Notificación audible | Nivel sonoro mín. 15 dB sobre ruido ambiente | NFPA 72 §18.4 |
| Notificación visual (strobes) | Intensidad (cd) según área, sincronización | NFPA 72 §18.5 |
| [...] | [...] | [...] |

### 1.3 Authority Having Jurisdiction (AHJ)
*Expliquen qué es la AHJ y por qué su aprobación es obligatoria. Identifiquen la AHJ de la ciudad elegida.*
[...]

### 1.4 Jurisdicción del edificio
*Estado y ciudad → qué edición de cada código está adoptada localmente (esto varía por estado).*
[...]

### 1.5 Requisitos según ocupación
*Clasificación de ocupación del edificio (Grupo A, B, E, R, etc. según IBC) y qué exige eso.*
[...]

---

## 2. Análisis del edificio seleccionado

*Debe ser un edificio REAL en EE.UU. con planos públicos. Incluir los planos originales como referencia.*

- **Ubicación:** [dirección, ciudad, estado]
- **Tipo / ocupación:** [oficinas, escuela, etc.]
- **Cantidad de pisos:** [...]
- **Dimensiones generales:** [área por piso, altura de cielos]
- **Distribución de áreas:** [...]
- **Pasillos y accesos / rutas de evacuación:** [...]
- **Cuartos eléctricos / mecánicos / de servicio:** [...]
- **Características particulares que afectan el diseño:** [cielos altos, ductos HVAC, áreas peligrosas...]

**Planos arquitectónicos originales:** [insertar imágenes / enlace a Drive]

---

## 3. Selección de equipos

*Equipos REALES y comerciales. UNA sola familia compatible (un fabricante principal: Honeywell/Notifier, Edwards/EST, Simplex, Bosch, etc.).*

**Fabricante principal seleccionado:** [...]  — *Justificación:* [...]

### 3.1 Arquitectura: convencional vs direccionable
*Cuál eligieron y por qué (tamaño del edificio, cantidad de dispositivos, necesidad de localización por punto).*
[...]

### 3.2 Tabla de dispositivos seleccionados
| # | Dispositivo | Fabricante | Modelo | Función | V / I (alarma) | Alimentación | Compatible c/ panel | Conexión | Justificación |
|---|---|---|---|---|---|---|---|---|---|
| 1 | FACP (panel) | [...] | [...] | Control central | [...] | 120 VAC | — | — | [...] |
| 2 | Detector de humo | [...] | [...] | Detección | [...] | Lazo SLC | Sí | Direccionable | NFPA 72 §17.7 |
| 3 | Pull station | [...] | [...] | Alarma manual | [...] | Lazo | Sí | [...] | NFPA 72 §17.14 |
| 4 | Horn/Strobe | [...] | [...] | Notificación | [...] | NAC | Sí | [...] | NFPA 72 §18 |
| ... | | | | | | | | | |

*Adjuntar los datasheets en la carpeta Drive/Datasheets.*

---

## 4. Diseño del sistema sobre los planos

*Cada ubicación JUSTIFICADA con la norma. Prohibido colocar dispositivos "a ojo".*

### 4.1 Criterios de ubicación (con norma)
- Detectores: [criterio de espaciamiento] → *NFPA 72 §[...]*
- Pull stations: [en cada salida, a ≤1.5 m] → *NFPA 72 §[...]*
- Notificación: [cobertura, candela por área] → *NFPA 72 §[...]*

### 4.2 Diseño por piso
*Por cada piso: descripción + referencia al plano en draw.io.*
- **Piso 1:** [cantidad y ubicación de cada dispositivo] — [enlace draw.io]
- **Piso 2:** [...]

### 4.3 Circuitos y lazos
- **SLC (lazos direccionables):** [cuántos, qué dispositivos, capacidad usada]
- **NAC (circuitos de notificación):** [cuántos, carga por circuito]
- **Cableado:** [tipo/calibre, ej. FPLR 16 AWG] — *justificación NEC*
- **Conexión entre pisos:** [...]

### 4.4 Alimentación y respaldo
- Fuente principal: [120 VAC]
- Baterías de respaldo: [Ah calculados — ver sección 5] — *NFPA 72 exige 24 h standby + 5 min alarma (o 15 min según caso)*

---

## 5. Diagramas, cálculos y documentación técnica

### 5.1 Planos por piso
*Insertar los planos de draw.io con dispositivos, nomenclatura y leyenda de símbolos.*

### 5.2 Diagrama de interconexión general
*Riser diagram: panel → lazos → dispositivos → NAC.*

### 5.3 Cálculos eléctricos
**a) Corriente en standby (normal):**
| Dispositivo | Cant. | I unit. (mA) | I total (mA) |
|---|---|---|---|
| [...] | | | |
| **Total standby** | | | **[...]** |

**b) Corriente en alarma:**
| Dispositivo | Cant. | I unit. (mA) | I total (mA) |
|---|---|---|---|
| [...] | | | |
| **Total alarma** | | | **[...]** |

**c) Caída de tensión en NAC:**
*Verificar que el último dispositivo del circuito reciba ≥ el mínimo del fabricante.*
- V_panel = [...] V, R_cable = [...] Ω, I_NAC = [...] A
- V_caída = I × R = [...] V → V_final = [...] V ≥ V_mín ✔/�’
- Fórmula: `Vdrop = 2 × L × I × R_por_metro`

**d) Capacidad de NAC / lazos:**
- Carga NAC = [...] A ≤ [capacidad máx panel] A ✔
- Direcciones usadas en SLC = [...] ≤ [máx del lazo] ✔

**e) Dimensionamiento de baterías:**
- Ah = (I_standby × 24 h) + (I_alarma × [5/15] min) × factor 1.2 = [...] Ah

### 5.4 Lista de materiales (BOM)
*En el Google Sheet compartido. Fabricante + modelo + cantidad + precio (si aplica).*

---

## 6. Análisis del diseño
- ¿Por qué convencional o direccionable? [...]
- Ventajas y desventajas de la solución: [...]
- Cumplimiento de las normas principales: [...]
- Limitaciones del diseño: [...]
- Consideraciones de mantenimiento e inspección (NFPA 72 cap. 14): [...]

---

## 7. Conclusiones
- Principales resultados obtenidos: [...]
- Normas de mayor influencia en el diseño: [...]
- Importancia de equipos certificados y compatibles: [...]
- Dificultades al trasladar la norma a una instalación real: [...]
- Aspectos a profundizar para una implementación real: [...]

---

## 8. Referencias
*Todas las fuentes: normas (con edición), manuales de fabricante, datasheets, planos. Formato consistente (IEEE o APA).*
1. NFPA 72, National Fire Alarm and Signaling Code, edición 20XX.
2. [...]

---

## Anexo A — Prompts de IA utilizados
*OBLIGATORIO según el enunciado. Peguen aquí TODOS los prompts usados en Claude / NotebookLM, con quién lo usó y para qué.*

| # | Integrante | Herramienta | Propósito | Prompt |
|---|---|---|---|---|
| 1 | [...] | NotebookLM | Resumen NFPA 72 detectores | "[prompt exacto]" |
| 2 | [...] | Claude | [...] | "[...]" |

## Anexo B — Datasheets
*Enlaces o PDFs de las hojas técnicas de los equipos seleccionados.*
