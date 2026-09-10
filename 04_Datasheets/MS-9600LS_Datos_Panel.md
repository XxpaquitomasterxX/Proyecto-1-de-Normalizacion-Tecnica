# Ficha del panel — Fire•Lite Alarms MS-9600LS
### Datos extraídos de la hoja técnica (insumo para Secciones 3, 4.3 y 5.3)

**Fuentes (dos documentos, ambos en `Panel/`):**
1. Hoja técnica **DF-60334:A6** (20/02/2019, 6 pág.) — capacidades del panel.
2. **Manual de instalación PN 52646:B** (17/06/2008, 212 pág.) — **Tabla 5.3** (corrientes de todos los dispositivos) y **Tabla 5.4** (dimensionamiento de baterías). *Este es el que permite hacer los cálculos.*

> ⚠️ **Corrección de fabricante.** El MS-9600LS es de **Fire•Lite Alarms**, no de Notifier. Ambas son marcas de **Honeywell**, pero son líneas de producto distintas y **no** se citan como el mismo fabricante. En el documento hay que escribir *Fire•Lite Alarms (Honeywell)* como fabricante principal.

**Variante seleccionada: MS-9600LS** (la sencilla). La diferencia con el MS-9600UDLS es que este último trae un **DACT** (comunicador digital de alarma) instalado de fábrica para reportar a estación central. Al elegir la variante sencilla, hay que **justificarlo** en la Sección 3: el edificio es un sistema local, no se requiere reporte a estación central. Si el grupo quisiera monitoreo remoto (el enunciado menciona "dispositivos de comunicación o monitoreo remoto" en el punto 3), la vía es el **MS-9600UDLS** o el módulo **IPDACT** opcional. Conviene mencionar la alternativa aunque no se adopte.

---

## 1. Datos verificados en la hoja técnica

### Arquitectura y capacidad

| Parámetro | Valor | Pág. |
|---|---|---|
| Tipo | FACP **inteligente direccionable** (protocolo LiteSpeed™) | 1 |
| Lazos SLC | **1, expandible a 2** | 6 |
| Detectores por lazo | **159** | 6 |
| Módulos monitor/control por lazo | **159** | 6 |
| Total direccionable por lazo | **318** | 1 |
| Zonas de software programables | 99 | 6 |
| Longitud máx. del lazo SLC | **10 000 ft** @ 12 AWG, par trenzado sin blindaje | 6 |
| Estilos SLC admitidos | NFPA Style 4, 6 o 7 | 1 |

### Circuitos de notificación (NAC)

| Parámetro | Valor |
|---|---|
| NAC integrados | **4 Style Y (Clase B)** o **2 Style Z (Clase A)** (con el NACKEY incluido) |
| Corriente máx. **por circuito** | **3,0 A** (special application) · 300 mA regulated |
| **Límite global en alarma** | La suma de **todos** los NAC + salidas de potencia special application **no puede exceder 7,0 A** |
| Resistencia de fin de línea | **4,7 kΩ, ½ W** (P/N 71252) para NAC Clase B |
| Sincronización de strobes | Seleccionable por NAC para **System Sensor, Wheelock y Gentex** |
| Códigos | Continuo, March Time, Temporal, California |

### Alimentación y baterías

| Parámetro | Valor |
|---|---|
| Entrada primaria | **120 VAC, 50/60 Hz, 3,0 A** |
| Fuente conmutada | 7 A |
| Carga de baterías | 27,6 VDC @ 1,0 A máx. |
| Capacidad máx. del cargador | **26 AH** |
| **Batería mínima** | **12 AH** |
| **Máximo que cabe en el gabinete** | **dos baterías de 18 AH** (en serie para 24 V → **18 AH útiles**) |
| Potencia auxiliar resetteable (4 hilos) | hasta 1,5 A |
| Potencia auxiliar no resetteable | 2 salidas, 1,5 A c/u (**máx. 1,5 A total en standby**) |

### Aprobaciones
FM Approved a **UL/ANSI 864**. Cumple NFPA 72 para sistemas **Local, Auxiliary, Remote Station, Proprietary y Central Station**. MEA 87-08-E.

---

## 2. Verificaciones de capacidad que YA se pueden cerrar

Estas dos van directo a la Sección 5.3(d) del entregable — **no dependen de ningún otro datasheet**:

### 2.1 Capacidad del lazo SLC ✔

```
Detectores direccionables requeridos   = 17   (15 humo + 2 térmicos)
Capacidad por lazo                     = 159
Utilización                            = 17/159 = 10,7 %          ✔ CUMPLE

Módulos direccionables requeridos      =  4   (estaciones manuales, monitor)
Capacidad por lazo                     = 159
Utilización                            = 4/159 = 2,5 %            ✔ CUMPLE
```

> **Conclusión de diseño: un solo lazo SLC es suficiente.** No hace falta el módulo de segundo lazo. El sistema usa el **6,6 %** de los 318 puntos disponibles. Conviene declarar explícitamente que el margen se deja a propósito para ampliaciones futuras — es un argumento de diseño, no un sobredimensionamiento accidental.

### 2.2 Longitud del lazo SLC ✔
El edificio mide ≈60 × 58 ft en planta con dos niveles. Un recorrido de lazo generoso, incluyendo subidas y bajadas, no pasa de **~1 200 ft**, contra un máximo de **10 000 ft**. Sin problema. *(Ojo: el máximo aplica a 12 AWG.)*

### 2.3 Distribución de NAC propuesta
Con 4 circuitos Clase B disponibles y 17 dispositivos de notificación, la partición natural es:

| NAC | Zona | Dispositivos aprox. |
|---|---|---|
| NAC-1 | Primer piso — ala norte (Stacks, North Reading Room, circulación) | 3 H/S |
| NAC-2 | Primer piso — ala sur (rotonda, oficina, baño, foyers) | 4 H/S + 2 strobes |
| NAC-3 | Sótano — ala norte (salas infantiles, storage) | 3 H/S |
| NAC-4 | Sótano — ala sur (hallway, foyer, sanitarios) | 3 H/S + 2 strobes |

> **Falta verificar** que cada NAC ≤ 3,0 A y que el total ≤ 7,0 A. Depende de la corriente de los horn/strobes, que varía fuertemente con las candelas.

---

## 3. Lo que esta hoja técnica NO trae

Esta es una **hoja técnica (datasheet) de 6 páginas**, no el manual de instalación. Le faltan dos cosas para poder cerrar los cálculos de la Sección 5.3:

### 3.1 El consumo propio del panel — ✔ RESUELTO por el manual 52646

La hoja técnica sola no lo traía, pero el **manual de instalación sí**. De la **Tabla 5.3**:

| Dispositivo | Col. 1 (primaria, no alarma) | Col. 2 (primaria, alarma) | Col. 3 (batería, no alarma) |
|---|---:|---:|---:|
| **Placa principal MS-9600LS** | **0,150 A** | **0,170 A** | **0,120 A** |
| ANN-80 (anunciador remoto) | 0,037 A | 0,040 A | 0,015 A |

Y las corrientes de standby de los dispositivos del lazo, también de la Tabla 5.3:

| Dispositivo | I standby |
|---|---:|
| SD350 / **SD355** (humo fotoeléctrico) | 0,00030 A |
| H350 / **H355** (térmico) · H350R / **H355R** (rate-of-rise) | 0,00030 A |
| **BG-12LX** (estación manual) | 0,00030 A |
| MMF-300 (módulo monitor) | 0,00040 A |
| CMF-300 (módulo de control) | 0,00039 A |
| B224RB (base con relé) | 0,00050 A |
| SLC-2LS (expansor de segundo lazo) | 0,08500 A |

> **Atajo del fabricante que vale oro:** para la **columna de alarma**, la Tabla 5.3 permite entrar un **valor global de 0,400 A** para *todos* los dispositivos del SLC cuando se usa **un solo lazo** (0,800 A con dos), en lugar de sumarlos uno por uno. Es el método del propio manual, así que es plenamente citable.

**Método de batería (Tabla 5.4):** `Batería = 1,2 × [ (Col.3 × 24 h) + (Col.2 × 0,084 h) ]`, con 0,084 h = 5 min. NFPA 72 para sistema Local: 24 h standby + 5 min alarma. Máximo 26 AH con el cargador interno.

Los cálculos ya hechos con estos datos están en `Calculo_Electrico_Seccion5.md`.

### 3.2 Los datasheets de los dispositivos — ⚠️ ESTO SÍ SIGUE FALTANDO
El manual da las corrientes de **standby** de los dispositivos del lazo, pero **no** las de los dispositivos de notificación (las filas NAC #1 a #4 de la Tabla 5.3 vienen en blanco a propósito: hay que llenarlas desde el *Device Compatibility Document*). Hacen falta, de la familia direccionable compatible de Fire•Lite:

| Dispositivo | Modelo candidato | Estado |
|---|---|---|
| Detector de humo fotoeléctrico direccionable | **SD355** | ✔ **confirmado en la Tabla 5.3 del manual** |
| Detector térmico direccionable | **H355R** (rate-of-rise) | ✔ **confirmado en la Tabla 5.3 del manual** |
| Base para detector | B350LP | verificar en el DCD |
| Estación manual direccionable | **BG-12LX** | ✔ **confirmado en la Tabla 5.3 del manual** |
| Módulo monitor | **MMF-300** | ✔ **confirmado en la Tabla 5.3 del manual** |
| Módulo de control (NAC) | **CMF-300 / CMF-300-6** | ✔ **nombrados en esta hoja técnica** (pág. 1) |
| Horn/Strobe | System Sensor SpectrAlert Advance (serie P2R) | compatibilidad de sincronización ✔ confirmada en pág. 1 |
| Strobe solo | System Sensor SpectrAlert Advance (serie SR) | ídem |

**Lo único que falta de verdad es la corriente en alarma de los horn/strobes y strobes, con su tabla de corriente vs. candelas.** Todo lo demás ya está cubierto por los dos documentos que hay en esta carpeta.

---

## 4. El documento que resuelve la exigencia de compatibilidad

El enunciado dice: *"No se permitirá combinar dispositivos de diferentes fabricantes sin demostrar documentalmente su compatibilidad"*.

Esta hoja técnica remite **tres veces** al **Fire•Lite Device Compatibility Document (DCD)**, y además declara en la página 1 la sincronización de strobes para **System Sensor, Wheelock y Gentex**.

> **Ese es exactamente el documento que hay que descargar y citar.** Resuelve de frente el requisito: el DCD es la prueba documental, emitida por el propio fabricante del panel, de que los dispositivos de notificación son compatibles y están listados para operar con el MS-9600LS. Sin él, mezclar Fire•Lite (panel) con System Sensor (notificación) queda sin respaldo — con él, queda blindado.

---

## 5. Restricción de baterías — ya resuelta, y el resultado es interesante

Con las corrientes reales del manual, la batería calculada da entre **4,2 y 4,7 AH** para *cualquier* corriente de notificación posible en este panel. El término de 24 h de standby domina por completo; los 5 minutos de alarma casi no pesan.

Pero el MS-9600LS **no admite baterías menores de 12 AH**.

> **Resultado: se seleccionan dos baterías de 12 V / 12 AH en serie (24 V, 12 AH). La batería la fija el mínimo del panel, no el cálculo de carga.** Margen ≈2,7× sobre lo calculado, y caben en el gabinete (que acepta hasta 18 AH), así que **no** se requiere gabinete externo BB-26 ni BB-55F.

Vale la pena decirlo así en la Sección 6: en edificios pequeños el dimensionamiento de baterías lo termina fijando el mínimo del equipo, no la demanda.
