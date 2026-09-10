# 3. Selección de equipos

**Fabricante principal seleccionado: Fire•Lite Alarms (Honeywell).**

*Justificación:* se requiere una **única familia comercialmente compatible** (enunciado, punto 4). Fire•Lite es una línea de Honeywell orientada precisamente a edificios pequeños y medianos como este, con paneles direccionables de gama de entrada, y publica dos documentos que permiten sustentar documentalmente todo el diseño: el **manual de instalación PN 52646**, que trae las tablas de consumo de cada dispositivo y el método de cálculo de baterías, y el **Device Compatibility Document P/N 15384**, que lista qué dispositivos de terceros están probados con cada panel.

> ⚠️ **Precisión de marca:** el MS-9600LS es de **Fire•Lite Alarms**, no de Notifier. Ambas pertenecen a Honeywell, pero son líneas de producto distintas con catálogos separados. En el documento debe escribirse *Fire•Lite Alarms (Honeywell)*.

---

## 3.1 Arquitectura: convencional vs. direccionable

**Se selecciona una arquitectura DIRECCIONABLE.**

| Criterio | Convencional | Direccionable | Decisión |
|---|---|---|---|
| Localización de la alarma | por zona (varios dispositivos comparten una zona) | **por punto individual** | ▶ direccionable |
| Cableado | un par por zona → muchos recorridos | **un solo lazo para todo el edificio** | ▶ direccionable |
| Diagnóstico y mantenimiento | hay que recorrer la zona | el panel identifica el dispositivo exacto | ▶ direccionable |
| Costo por dispositivo | menor | mayor | ▷ convencional |
| Ampliación futura | requiere cableado nuevo | se agrega una dirección al lazo | ▶ direccionable |

**Las tres razones de peso en este edificio concreto:**

1. **Es un edificio histórico (HABS IL-329).** Cada metro de canalización implica perforar mampostería original y dejar tubería vista. Una arquitectura direccionable resuelve los 21 puntos de detección con **un solo lazo SLC** en lugar de un par de conductores por zona. Es el argumento más fuerte, y es específico de este edificio.
2. **Localización por punto.** Con planta libre en el primer piso y un sótano compartimentado, saber *cuál* detector se activó —y no solo *qué zona*— cambia el tiempo de respuesta. El MS-9600LS admite además etiquetas de texto por punto ("SOTANO CUARTO MECANICO"), que se muestran en el anunciador de la entrada.
3. **Supervisión y mantenimiento.** El panel hace prueba automática de cada detector cada dos horas, compensación de deriva por acumulación de polvo y aviso de mantenimiento por punto. En una biblioteca con estanterías y polvo de papel, eso reduce alarmas no deseadas — que es la causa número uno de que un sistema real termine desactivado.

*Contrapartida asumida:* el costo unitario de un detector direccionable es mayor que el de uno convencional. Con solo 21 puntos, el sobrecosto es marginal frente a la reducción de canalización en un inmueble protegido.

---

## 3.2 Tabla de dispositivos seleccionados

| # | Dispositivo | Fabricante | Modelo | Función | Características eléctricas | Alimentación | Compatible c/ panel | Conexión | Justificación normativa |
|---|---|---|---|---|---|---|---|---|---|
| 1 | **FACP** | Fire•Lite Alarms | **MS-9600LS** | Control central del sistema | Entrada 120 VAC 50/60 Hz, 3,0 A · consumo 0,150 A standby / 0,170 A alarma · fuente 7 A | 120 VAC dedicado + baterías | — | — | NFPA 72 cap. 10 · UL 864 · FM Approved |
| 2 | **Detector de humo** | Fire•Lite Alarms | **SD355** | Detección fotoeléctrica de humo | 0,30 mA standby | Lazo SLC 24 VDC | Sí *(Tabla 5.3 del manual)* | Direccionable | NFPA 72 cap. 17 (detección de humo) |
| 3 | **Detector térmico** | Fire•Lite Alarms | **H355R** | Detección térmica, temp. fija + razón de aumento | 0,30 mA standby | Lazo SLC 24 VDC | Sí *(Tabla 5.3)* | Direccionable | NFPA 72 cap. 17 (cuartos mecánicos) |
| 4 | **Base de detector** | Fire•Lite Alarms | **B350LP** | Base de bajo perfil | — | SLC | **Sí — SLC Wiring Manual 51309, apéndice D.1** | Direccionable | — |
| 5 | **Estación manual** | Fire•Lite Alarms | **BG-12LX** | Alarma manual direccionable | 0,30 mA standby | Lazo SLC | Sí *(Tabla 5.3)* | Direccionable | NFPA 72 cap. 17 (estaciones manuales) |
| 6 | **Horn/Strobe** | System Sensor | **P2R** | Notificación audible + visual | 15 cd → 79 mA · 30 cd → 107 mA · 75 cd → 176 mA (24 V, DC, Temporal High) | Circuito NAC 24 VDC | **Sí — DCD 15384:BR** | NAC Clase B | NFPA 72 cap. 18 (audible y visible) |
| 7 | **Strobe** | System Sensor | **SR** | Notificación visual únicamente | 15 cd → 66 mA · 30 cd → 94 mA | Circuito NAC 24 VDC | **Sí — DCD 15384:BR** | NAC Clase B | NFPA 72 cap. 18 (visible) |
| 8 | **Anunciador remoto** | Fire•Lite Alarms | **ANN-80** | Anunciador LCD en la entrada principal | 0,037 A standby / 0,040 A alarma / 0,015 A en batería | ANN-BUS (EIA-485) | Sí *(Tabla 5.3)* | ANN-BUS | Acceso del cuerpo de bomberos |
| 9 | **Baterías de respaldo** | — | 2 × 12 V / 12 AH selladas plomo-ácido | Energía secundaria | 24 VDC, 12 AH en serie | — | Sí (mínimo del panel: 12 AH) | Terminales de batería | NFPA 72: 24 h standby + 5 min alarma |
| 10 | **Resistencia EOL** | Fire•Lite Alarms | **P/N 71252** | Supervisión de fin de línea | 4,7 kΩ, ½ W | — | Sí | Extremo de cada NAC | Supervisión de NAC Clase B |
| 11 | **Cableado SLC** | — | Par trenzado, **16 AWG** | Lazo de detección | 16 AWG → máx. **4 875 ft** (doc. 51309). Rango admitido 18–12 AWG | — | — | Style 4 (Clase B) | NEC Art. 760 · Fire•Lite 51309 |
| 12 | **Cableado NAC** | — | **16 AWG FPLR** | Circuitos de notificación | 4,89 Ω/kft (NEC cap. 9 tabla 8) | — | — | Clase B | NEC Art. 760 · verificado por caída de tensión |

### Cantidades

| Dispositivo | Piso 1 | Sótano | Total |
|---|---:|---:|---:|
| SD355 — detector de humo | 8 | 7 | **15** |
| H355R — detector térmico | 0 | 2 | **2** |
| BG-12LX — estación manual | 2 | 2 | **4** |
| P2R — horn/strobe | 6 | 5 | **11** |
| SR — strobe | 2 | 2 | **4** |
| MS-9600LS — panel | — | 1 | **1** |
| ANN-80 — anunciador | 1 | — | **1** |
| **Puntos direccionables en el lazo SLC** | 10 | 11 | **21** |

---

## 3.3 Demostración documental de compatibilidad

El enunciado exige: *"No se permitirá combinar dispositivos de diferentes fabricantes sin demostrar documentalmente su compatibilidad y aprobación para trabajar conjuntamente."*

El sistema usa **dos marcas**: Fire•Lite (panel, detección, estación manual, anunciador) y System Sensor (notificación). La compatibilidad se demuestra así:

1. **Fire•Lite *Device Compatibility Document*, P/N 15384:BR (25/01/2022), página 12.** En la sección *System Sensor SpectrAlert Advance*, el **MS-9600LS aparece listado explícitamente** en la columna de UL 864 10.ª edición, junto a los modelos base **P2R, P2RH, SR y SRH**. Es el documento emitido por el fabricante del panel, y es la prueba directa.
2. **Hoja técnica del panel DF-60334:A6, página 1.** Declara *"Selectable strobe synchronization per NAC for **System Sensor**, Wheelock, and Gentex devices"* — es decir, el panel incorpora de fábrica el circuito de sincronización de estrobos de System Sensor.
3. Ambas marcas pertenecen a **Honeywell**, lo que explica la integración, pero **el argumento válido es el documental**, no el corporativo.

> Los dos documentos están en `Panel/` y deben adjuntarse al entregable.
