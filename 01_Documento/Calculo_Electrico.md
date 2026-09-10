# Cálculos eléctricos — Sección 5.3
### Sistema Fire•Lite MS-9600LS · Paxton Carnegie Library

**Fuentes de los datos:**
- Fire•Lite Alarms, *MS-9600LS Series Addressable FACP Installation Manual*, **PN 52646:B**, 17/06/2008 — **Tabla 5.3** (System Current Draw Calculations) y **Tabla 5.4** (Total Secondary Power Requirements). Archivo `Panel/52646.pdf`.
- Fire•Lite Alarms, hoja técnica **DF-60334:A6**. Archivo `Panel/`.

> **Todos los cálculos siguen el método del propio fabricante** (Tablas 5.3 y 5.4 del manual), no un método genérico. Eso es lo que pide el enunciado: *"acompañados de los datos obtenidos de las hojas técnicas"*.

---

## 5.3.0 Decisión previa: ubicación del panel

**FACP en el Electrical Room del sótano**, con un **anunciador remoto ANN-80 en el East Foyer** (entrada principal).

*Justificación:* el cuerpo de bomberos necesita leer el estado del sistema al entrar, pero el East Foyer es un vestíbulo histórico decorado de 5,5 × 8 ft donde un gabinete de 19 × 17 in sería inviable y agresivo con el bien patrimonial. El Electrical Room ya concentra la acometida eléctrica y permite el circuito derivado dedicado. El MS-9600LS soporta el ANN-80 por ANN-BUS de fábrica, y el manual da sus corrientes en la Tabla 5.3. Es una solución del catálogo del propio fabricante, no un apaño.

---

## 5.3.a Corriente en condición normal (standby)

Corrientes unitarias tomadas de la **Tabla 5.3** del manual:

| Dispositivo | Modelo | Cant. | Col. 1 unit. (A) | Col. 1 total (A) | Col. 3 unit. (A) | Col. 3 total (A) |
|---|---|---:|---:|---:|---:|---:|
| Panel (placa principal) | MS-9600LS | 1 | 0,150 | 0,1500 | 0,120 | 0,1200 |
| Anunciador remoto LCD | ANN-80 | 1 | 0,037 | 0,0370 | 0,015 | 0,0150 |
| Detector de humo fotoeléctrico | SD355 | 15 | 0,00030 | 0,0045 | 0,00030 | 0,0045 |
| Detector térmico rate-of-rise | H355R | 2 | 0,00030 | 0,0006 | 0,00030 | 0,0006 |
| Estación manual direccionable | BG-12LX | 4 | 0,00030 | 0,0012 | 0,00030 | 0,0012 |
| **TOTAL** | | **23** | | **0,1933 A** | | **0,1413 A** |

- **Columna 1** = carga sobre la fuente primaria con AC presente → **0,1933 A**
- **Columna 3** = carga sobre las **baterías** sin AC → **0,1413 A** ← *esta es la que entra al cálculo de batería*

## 5.3.b Corriente en condición de alarma

> **Método del fabricante:** la Tabla 5.3 permite entrar un **valor global de 0,400 A** para el consumo en alarma de **todos** los dispositivos del lazo SLC cuando se usa **un (1) lazo**, en vez de sumarlos uno por uno. Se usa ese valor.

| Concepto | Valor (A) |
|---|---:|
| Panel (placa principal), Col. 2 | 0,170 |
| ANN-80, Col. 2 | 0,040 |
| Todos los dispositivos SLC (valor global, 1 lazo) | 0,400 |
| **Subtotal sin notificación** | **0,610** |
| NAC-1 … NAC-4 (15 dispositivos de notificación) | **1,314** |
| **TOTAL EN ALARMA** | **1,924 A** |

**Verificación contra el límite del panel: 1,924 A ≤ 7,0 A → utilización 27,5 % ✔**

### Corrientes de los dispositivos de notificación

Fuente: **System Sensor**, *SpectrAlert Advance — Indoor Wall Horns, Strobes, Horn Strobes*, datasheet **AVDS102**, tablas *UL Max. Current Draw*. Archivo `Panel/SystemSensor_SpectrAlert_Advance_Indoor_Wall_AVDS102.pdf`.
Valores tomados en **16–33 V, entrada DC, patrón Temporal High** (temporal 3 es el patrón de evacuación que exige NFPA 72; se toma High dBA como caso desfavorable).

| Candelas | Horn/strobe **P2R** (A) | Strobe **SR** (A) |
|---:|---:|---:|
| 15 | 0,079 | 0,066 |
| 30 | 0,107 | 0,094 |
| 75 | 0,176 | 0,158 |
| 95 | 0,194 | 0,181 |
| 110 | 0,212 | 0,202 |

**Rango de tensión de operación (24 V nominal): 16 a 33 V** → el mínimo del fabricante es **16 V**, que es el criterio de aceptación de 5.3.c.

### Reparto por circuito

| Circuito | Zona | Disp. | **I (A)** | % de 3,0 A |
|---|---|---:|---:|---:|
| NAC-1 | Piso 1 — ala norte | 3 | 0,334 | 11,1 % ✔ |
| NAC-2 | Piso 1 — ala sur | 5 | 0,397 | 13,2 % ✔ |
| NAC-3 | Sótano — ala norte | 3 | 0,293 | 9,8 % ✔ |
| NAC-4 | Sótano — ala sur | 4 | 0,290 | 9,7 % ✔ |
| **Total** | | **15** | **1,314** | |

Total de aparatos: **11 horn/strobe + 4 strobes solos** (oficina, baño y los dos sanitarios del sótano llevan solo notificación visual). El detalle de candelas por recinto está en `BOM_Calculos/6_Notificacion_Candelas.csv`.

### Criterio de candelas 

La tabla de NFPA 72 de espaciamiento en recintos para aparatos visuales **de pared** (un aparato por sala) tiene una fila intermedia que se suele pasar por alto:

| Tamaño máx. de sala | Candelas mínimas |
|---|---|
| 20 × 20 ft | 15 cd |
| **28 × 28 ft** | **30 cd** |
| **30 × 30 ft** | **34 cd** ← *no 30 cd* |
| 40 × 40 ft | 60 cd |
| 50 × 50 ft | 95 cd |

**Un estrobo de 30 cd cubre hasta 28×28 ft, no hasta 30×30.** Para 30×30 la norma pide 34 cd.

Impacto en este diseño: **un solo recinto**. La zona de *Stacks* tiene una envolvente de **28,3 × 28,3 ft**, que supera por poco la fila de 28×28 y cae en la de 30×30 → exige 34 cd. Como el SpectrAlert Advance no tiene ajuste de 34 cd (sus pasos son 15, 15/75, 30, 75, 95, 110), **se sube al siguiente disponible: 75 cd**. Todos los demás recintos quedan por debajo de 28×28 y mantienen 15 o 30 cd.

**Alternativa válida** si se quisiera evitar el salto a 75 cd: usar **dos aparatos de 15 cd** en la zona de Stacks, amparándose en la tabla de la norma para más de un aparato por sala. Es igual de defendible y consume menos.

> **Edición y cita — RESUELTO.** La edición aplicable en Illinois es **NFPA 72-2013** (el *41 Ill. Adm. Code* Parte 100 adopta NFPA 101-2015, que referencia NFPA 72-2013). En esa edición la cita correcta es **Tabla 18.5.5.4.1(a)**. *(En NFPA 72-2022 la misma materia está en §18.5.5.7; no se usa esa numeración aquí.)*
>
> **Además, §18.5.5.4.4 y §18.5.5.4.5 respaldan directamente el caso de Stacks:** para salas no cuadradas el tamaño se determina por el cuadrado que encierre la sala completa, **o subdividiéndola en varios cuadrados**. Eso valida tanto subir a 75 cd como la alternativa de dos aparatos de 15 cd.

## 5.3.c Caída de tensión en los NAC

Fórmula: `V_caída = 2 × L × I × R_u`  (el 2 es ida y vuelta)

Resistencias — **NEC Capítulo 9, Tabla 8** (cobre sin recubrir, Ω por cada 1 000 ft):

| Calibre | Sólido | Trenzado |
|---|---:|---:|
| 12 AWG | 1,93 | 2,01 |
| 14 AWG | 3,07 | 3,19 |
| **16 AWG** | **4,89** | **5,08** |
| 18 AWG | 7,77 | 8,08 |



**Tensión de partida:** 24 VDC nominal, pero el caso desfavorable es con las baterías al final de la descarga. Se adopta **20,4 V** como tensión de partida del cálculo (85 % de 24 V), que es la práctica estándar y el caso que exige NFPA 72 verificar.

**Criterio de aceptación:** `V_último dispositivo ≥ V_mín del datasheet del horn/strobe` (típicamente 16 V en la familia SpectrAlert Advance — **confirmar en el datasheet**).

**Método conservador:** se supone que **toda** la corriente del circuito recorre **toda** la longitud (es decir, todos los aparatos concentrados en el extremo). Es el peor caso posible.

**Longitudes (revisión B).** Se midieron sobre el recorrido dibujado en los planos
corregidos, punto por punto y con métrica ortogonal (|Δx|+|Δy|) a la escala del fondo
(25 px = 1 pie), sumando: (a) el tramo desde el FACP en el Electrical Room hasta el
montante de la escalera del South Foyer, (b) el tramo vertical del montante entre
niveles (≈12 ft) para NAC-1 y NAC-2, y (c) el recorrido en planta de cada circuito.
Sobre ese total se aplica una holgura del 25 % por recorrido real de canalización.



### Resultados

| Circuito | Recorrido medido (ft) | L con 25 % (ft) | I (A) | **16 AWG** V_caída → V_final | **14 AWG** V_caída → V_final |
|---|---:|---:|---:|---|---|
| NAC-1 | 133,8 | **167** | 0,334 | 0,546 → **19,85 V** ✔ | 0,343 → **20,06 V** ✔ |
| NAC-2 | 138,9 | **174** | 0,397 | 0,676 → **19,72 V** ✔ | 0,424 → **19,98 V** ✔ |
| NAC-3 | 80,0 | **100** | 0,293 | 0,287 → **20,11 V** ✔ | 0,180 → **20,22 V** ✔ |
| NAC-4 | 59,5 | **74** | 0,290 | 0,210 → **20,19 V** ✔ | 0,132 → **20,27 V** ✔ |

Ejemplo desarrollado (NAC-2, el caso más desfavorable, con 16 AWG):

```
Recorrido: FACP → montante (14,5 ft) → subida al piso 1 (12 ft) →
           N-108 (3,5) → N-105 (22,4) → N-106 (12,0) → N-103 (37,0) → N-107 (37,5)
           = 138,9 ft   →  con 25 % de holgura  →  L = 174 ft

V_caída = 2 × (174/1000) × 0,397 A × 4,89 Ω/kft = 0,676 V
V_final = 20,40 − 0,676                          = 19,72 V
Criterio: V_final ≥ 16 V (mínimo SpectrAlert Advance, datasheet AVDS102)
19,72 V ≥ 16 V  →  CUMPLE, con 3,72 V de margen
```

> **Conclusión: 16 AWG cumple en los cuatro circuitos, con margen amplio.** El peor caso
> deja 3,7 V de reserva sobre el mínimo del fabricante.
>
> El edificio es pequeño y las corrientes resultaron bajas (0,27–0,40 A por circuito), así que la caída de tensión **no es restrictiva aquí**. Se especifica **16 AWG FPLR** como calibre base; el 14 AWG queda como opción si se quiere margen adicional para ampliaciones, pero no lo exige el cálculo.

## 5.3.d Verificación de capacidad de circuitos

### Lazo SLC ✔

| Concepto | Usado | Máximo | Utilización |
|---|---:|---:|---:|
| Detectores direccionables | 17 | 159 | **10,7 %** ✔ |
| Módulos direccionables | 4 | 159 | **2,5 %** ✔ |
| Lazos SLC requeridos | **1** | 2 | — |
| Longitud del lazo (16 AWG) | ≈1 200 ft | **4 875 ft** | **24,6 %** ✔ |
| Resistencia c.c. del lazo | **11,7 Ω** | 40 Ω | **29 %** ✔ |



**Resistencia c.c. del lazo (requisito propio del fabricante, no de NFPA).** El doc. 51309
§2.2.1 exige que, en Style 4, la resistencia c.c. desde el panel hasta el final de cada
ramal no supere **40 Ω**:

```
R = 2 × (1200/1000) × 4,89 Ω/kft = 11,7 Ω   ≤ 40 Ω  →  CUMPLE
```

*(Los ≈1 200 ft son una envolvente conservadora: el recorrido medido sobre los planos
corregidos es de ≈433 ft más las bajadas a cada dispositivo, del orden de 600 ft con
holgura. Se conserva el valor de 1 200 ft por ser el caso desfavorable.)*

**El lazo SLC Style 4 no lleva resistencia de fin de línea.** Se supervisa por la propia
comunicación con los dispositivos direccionables; la EOL de 4,7 kΩ es exclusiva de los
NAC, y la de 47 kΩ (P/N R-47K) es para los circuitos de entrada de los módulos
MMF/CMF-300, que este diseño no usa (manual 52646:B §1.6.4).

→ **Un solo lazo SLC.** No se requiere el módulo de expansión SLC-2LS. El margen se deja deliberadamente para ampliaciones futuras.

### Circuitos NAC

| Concepto | Valor |
|---|---|
| NAC disponibles | 4 Style Y (Clase B) |
| Máximo por circuito | 3,0 A |
| Máximo global (NAC + auxiliares) | 7,0 A |
| Resistencia de fin de línea | 4,7 kΩ ½ W (P/N 71252), una por NAC |
| Carga máxima en un circuito | **0,397 A** (NAC-2) → **13,2 %** de 3,0 A ✔ |
| Carga total de notificación | **1,314 A** ✔ |
| Total en alarma (NAC + panel + SLC) | **1,924 A** → **27,5 %** de 7,0 A ✔ |
| Estado | **✔ CUMPLE con margen amplio** |

## 5.3.e Dimensionamiento de baterías

Método: **Tabla 5.4** del manual. NFPA 72, sistema **Local**: **24 h de standby + 5 min de alarma** (factor 0,084 h).

```
AH standby = Carga secundaria (Col. 3) × 24 h
           = 0,1413 A × 24 h
           = 3,3912 AH

AH alarma  = Carga en alarma (Col. 2) × 0,084 h
           = (0,610 + I_NAC) × 0,084

Batería    = 1,2 × (AH standby + AH alarma)        ← derating obligatorio de la Tabla 5.4
```

**Cálculo con los valores reales:**

```
AH standby = 0,1413 A × 24 h                = 3,3912 AH
AH alarma  = 1,924 A × 0,084 h              = 0,1616 AH
Suma                                        = 3,5528 AH
Batería    = 3,5528 × 1,2                   = 4,26 AH
```

**El hallazgo:** el término de standby domina por completo — la notificación aporta solo el 4,4 % del total, porque solo actúa 5 minutos. De hecho, aunque la corriente de notificación se llevara al máximo posible del panel (6,39 A), la batería apenas subiría a 4,7 AH.

| I_NAC | AH alarma | Batería calculada |
|---:|---:|---:|
| **1,314 A (el diseño real)** | 0,162 | **4,26 AH** |
| 3,0 A | 0,303 | 4,43 AH |
| 6,39 A (máximo del panel) | 0,588 | 4,78 AH |

> **Conclusión:** para **cualquier** corriente de notificación físicamente posible en este panel, la batería calculada queda entre **4,3 y 4,8 AH**.
>
> Pero el MS-9600LS **no admite baterías menores de 12 AH** (hoja técnica DF-60334 y manual §5.4.2). Por lo tanto:
>
> ### **La batería no la gobierna el cálculo, la gobierna el mínimo del panel: se seleccionan dos baterías selladas de 12 V / 12 AH en serie (24 V, 12 AH).**
>
> Margen sobre lo calculado: **≈2,7×**. Caben holgadamente en el gabinete (que acepta hasta 18 AH) y no se requiere gabinete externo BB-26/BB-55F.

Este resultado **es** el análisis, no un trámite: muestra que en un edificio pequeño el dimensionamiento de baterías lo fija el mínimo del equipo y no la carga, y conviene decirlo así en la Sección 6.


## 5.3.g Sincronización de los aparatos visibles

El piso 1 es de **planta libre**: desde la circulación central se ven simultáneamente los
estrobos de Stacks (N-101), North Reading (N-102) y la propia circulación (N-104). Con
**más de dos aparatos visibles en un mismo campo de visión**, el capítulo 18 de NFPA 72
exige que **destellen sincronizados** (destellos no sincronizados pueden provocar
malestar y, en personas susceptibles, crisis fotosensibles).

**No hace falta un módulo externo MDL3.** El MS-9600LS trae **sincronización seleccionable
por NAC** y admite el protocolo **System Sensor**, que es el de la familia SpectrAlert
Advance empleada aquí:

- Manual **52646:B §3.6.5.5.8** — *Synced Type*: opción 1 = System Sensor.
- Manual **52646:B §3.6.5.5.8.1** — máximo **46 estrobos System Sensor por NAC**
  sincronizados; aquí el circuito más cargado tiene **5** → **10,9 %** ✔.
- Manual **52646:B §4.16** — *Synchronized NAC Operation*.

**Programación requerida:** los cuatro NAC se configuran como *Synced Strobe* con
*NAC Sync Type = System Sensor*. Queda anotado en el plano y en el diagrama riser.

---

## 5.3.f Circuito derivado de AC

Del manual §5.2 y de la Tabla 5.1:

- Circuito **derivado dedicado y exclusivo**, rotulado **FIRE ALARM**, conectado al lado de línea de la acometida principal.
- **Ningún** equipo ajeno al sistema puede alimentarse de él.
- Sin dispositivos de desconexión en el recorrido.
- Conductor: **14 AWG con aislamiento para 600 V**.
- Corriente: **3,0 A** (120 VAC, 50/60 Hz) — un solo panel, sin CHG-120F.
- Protección contra sobrecorriente conforme al **NEC Artículo 760** y códigos locales.

---

---

## Resumen — todos los cálculos de la Sección 5.3, cerrados

| Cálculo | Resultado | Verificación |
|---|---|---|
| **a) Standby** | 0,1933 A primaria · **0,1413 A** desde batería | — |
| **b) Alarma** | **1,924 A** | ≤ 7,0 A → **27,5 %** ✔ |
| **c) Caída de tensión** | peor caso **19,72 V** (NAC-2, 16 AWG, L = 174 ft) | ≥ 16 V ✔ |
| **d) Capacidad NAC** | máx. 0,397 A en un circuito | ≤ 3,0 A → **13,2 %** ✔ |
| **d) Capacidad SLC** | 17 detectores · 4 módulos · 1 lazo | ≤ 159 c/u → **10,7 %** ✔ |
| **d) Longitud SLC** | ≈1 200 ft · R = 11,7 Ω | ≤ 4 875 ft (16 AWG) y ≤ 40 Ω ✔ |
| **g) Sincronización** | 4 NAC en *Synced Strobe*, tipo System Sensor | 5 estrobos ≤ 46 ✔ |
| **e) Baterías** | calculado 4,26 AH → **se instalan 12 AH** | mínimo del panel gobierna ✔ |
| **f) Circuito AC** | 3,0 A, 14 AWG/600 V, dedicado | NEC Art. 760 ✔ |

### Tabla 18.5.5.4.1(a) — valores confirmados (NFPA 72-2013)

| Tamaño máx. de sala | Un aparato por sala |
|---|---|
| 20 × 20 ft | 15 cd |
| **28 × 28 ft** | **30 cd** |
| **30 × 30 ft** | **34 cd** |
| 40 × 40 ft | 60 cd |
| 45 × 45 ft | 75 cd |
| 50 × 50 ft | **94 cd** |
| 54 × 54 ft | 110 cd |
| 55 × 55 ft | 115 cd |
| 60 × 60 ft | 135 cd |
| 63 × 63 ft | 150 cd |
| 68 × 68 ft | 177 cd |
| 70 × 70 ft | **184 cd** |

**Los datos eléctricos están respaldados por datasheet y el criterio de candelas por la norma. La Sección 5.3 está cerrada.**
