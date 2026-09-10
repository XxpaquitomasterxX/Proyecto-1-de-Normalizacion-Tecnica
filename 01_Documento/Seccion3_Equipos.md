# 3. Selección de equipos

**Fabricante principal seleccionado: Fire•Lite Alarms (Honeywell).**

*Justificación:* se requiere una **única familia comercialmente compatible** (enunciado, punto 4). Fire•Lite es una línea de Honeywell orientada precisamente a edificios pequeños y medianos como este, con paneles direccionables de gama de entrada, y publica dos documentos que permiten sustentar documentalmente todo el diseño: el **manual de instalación PN 52646**, que trae las tablas de consumo de cada dispositivo y el método de cálculo de baterías, y el **Device Compatibility Document P/N 15384**, que lista qué dispositivos de terceros están probados con cada panel.

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

Todos los datos eléctricos de esta tabla provienen de la **hoja técnica de cada dispositivo**
(columna *Hoja técnica*), no de fuentes secundarias. Los PDF están en `04_Datasheets/`.

| # | Dispositivo | Fabricante | Modelo | Función | Características eléctricas | Alimentación | Compatible c/ panel | Conexión | Hoja técnica |
|---|---|---|---|---|---|---|---|---|---|
| 1 | **FACP** | Fire•Lite Alarms (Honeywell) | **MS-9600LS** | Control central del sistema | Entrada 120 VAC 50/60 Hz, 3,0 A · consumo 0,150 A standby / 0,170 A alarma · fuente conmutada 7 A · 4 NAC de 3,0 A c/u | 120 VAC circuito dedicado + baterías 24 VDC | — (es el panel) | Bornera principal | **DF-60334:A6** · manual **52646:B** |
| 2 | **Detector de humo** | Fire•Lite Alarms (Honeywell) | **SD355** | Detección fotoeléctrica de humo, direccionable | Rango **15–32 VDC** · standby **300 µA** @ 24 VDC · LED 6,5 mA · direcciones 01–159 | Lazo SLC (2 hilos) | Sí *(Tabla 5.3 del manual 52646:B)* | Direccionable, base enchufable | **DF-52384:D** |
| 3 | **Detector térmico** | Fire•Lite Alarms (Honeywell) | **H355R** | Detección térmica: 135 °F fijo + razón de aumento **15 °F/min** | Rango **15–32 VDC** · standby **300 µA** @ 24 VDC · LED 6,5 mA · espaciamiento listado **50 ft** | Lazo SLC (2 hilos) | Sí *(Tabla 5.3)* | Direccionable, base enchufable | **DF-52385:D** |
| 4 | **Base de detector** | Fire•Lite Alarms (Honeywell) | **B210LP** | Base de montaje y cableado, bajo perfil, 6,1" ø | Sin consumo propio · admite hasta 12 AWG | SLC (el detector se alimenta por ella) | Sí — es la base **incluida** con el SD355 y el H355R | Enchufable | **DF-52384:D** · **DF-52385:D** · **DF-60059:G** |
| 5 | **Estación manual** | Fire•Lite Alarms (Honeywell) | **BG-12LX** | Alarma manual direccionable, **doble acción** | 24 VDC nominal (máx. 28 VDC) · standby **375 µA** máx. · alarma **5 mA** máx. · admite hasta 12 AWG | Lazo SLC | Sí *(Tabla 5.3)* | Direccionable | **DF-52013:D** |
| 6 | **Horn/Strobe** | System Sensor (Honeywell) | **P2R** | Notificación audible + visual | Rango **16–33 VDC** · 15 cd → 79 mA · 30 cd → 107 mA · 75 cd → 176 mA (DC, Temporal High) · **88 dBA a 10 ft** | Circuito NAC 24 VDC, 2 hilos | **Sí — DCD 15384:BR, pág. 12** | NAC Clase B (Style Y) | **AVDS102** |
| 7 | **Strobe** | System Sensor (Honeywell) | **SR** | Notificación visual únicamente | Rango **16–33 VDC** · 15 cd → 66 mA · 30 cd → 94 mA · 1 destello/s | Circuito NAC 24 VDC, 2 hilos | **Sí — DCD 15384:BR, pág. 12** | NAC Clase B (Style Y) | **AVDS102** |
| 8 | **Anunciador remoto** | Fire•Lite Alarms (Honeywell) | **ANN-80** | Anunciador LCD de 80 caracteres en la entrada principal | Rango **18–28 VDC** · 0,037 A standby / 0,040 A alarma / 0,015 A en batería · hasta **6 000 ft** del panel | ANN-BUS del FACP (2 hilos de datos + 2 de potencia) | Sí — accesorio del catálogo del propio panel | ANN-BUS (EIA-485), Clase B | **DF-52417:D** |
| 9 | **Baterías de respaldo** | Fire•Lite Alarms (Honeywell) — celdas **Power-Sonic** | **BAT-12120** ×2 *(Power-Sonic PS-12120)* | Energía secundaria | 12 V / **12 AH** c/u @ 20 h · selladas plomo-ácido, sin mantenimiento · 151 × 98 × 100 mm · 3,59 kg c/u | Cargador del panel | Sí — serie BAT recomendada por Fire•Lite para todos sus paneles; el MS-9600LS exige mín. 12 AH | Terminales de batería, **2 en serie → 24 VDC** | **DF-52397:C1** |
| 10 | **Resistencia EOL** | Fire•Lite Alarms (Honeywell) | **P/N 71252** | Supervisión de fin de línea del NAC | 4,7 kΩ, ½ W | — | Sí — es la EOL que especifica el propio panel | Extremo de cada NAC | manual **52646:B** |
| 11 | **Cableado SLC** | Belden / Genesis *(cualquiera de los listados)* | **Belden 5220UL / 6220UL** o **Genesis WG-4311 / WG-4511** | Lazo de detección | Par trenzado sin blindaje **16 AWG** · máx. **4 875 ft** en modo LiteSpeed · R c.c. del lazo ≤ 40 Ω en Style 4 | — | Cables listados por Fire•Lite para LiteSpeed | Style 4 (Clase B) | doc. **51309**, Tabla 2.2 |
| 12 | **Cableado NAC** | — *(cualquier cable listado)* | **16 AWG FPLR** | Circuitos de notificación | 4,89 Ω/kft (NEC cap. 9 tabla 8) · verificado por caída de tensión | — | — | Clase B (Style Y) | NEC Art. 760 |

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

## 3.4 Justificación de la selección, modelo por modelo

El enunciado pide, para cada dispositivo, la **justificación de su selección**. La §3.1 explica
por qué la arquitectura es direccionable y la §3.3 demuestra la compatibilidad; aquí se
justifica **por qué ese modelo concreto y no otro** del mismo catálogo.

| Dispositivo | Por qué ese modelo | Alternativa descartada y motivo |
|---|---|---|
| **MS-9600LS** | Es el panel direccionable de gama de entrada de Fire•Lite que cubre el edificio con **un solo lazo** (159 detectores + 159 módulos, usamos 17 y 4) y trae de fábrica los 4 NAC, los 3 relés y la sincronización de estrobos que necesita el diseño. Fuente de 7 A, muy por encima de los 1,924 A del sistema | **MS-9200UDLS** (menor): un solo lazo pero fuente de 2,7 A y sin margen de ampliación. **MS-9600UDLS**: idéntico pero con DACT integrado; se descarta porque el sistema es **local**, sin reporte a estación central. Si el AHJ exigiera reporte, es el reemplazo directo — o un módulo IPDACT |
| **SD355** | Detección **fotoeléctrica**, que es la adecuada para fuegos latentes con humo visible: papel y estanterías de biblioteca. Prueba de sensibilidad desde el panel (NFPA 72 cap. 14) y compensación de deriva por polvo | **Iónico**: mejor ante llama viva y combustibles líquidos, que aquí no hay, y mucho más propenso a falsas alarmas con polvo de papel. **SD355T** (con sensor térmico añadido): innecesario en recintos climatizados y limita la temperatura de operación a 38 °C |
| **H355R** | En los cuartos mecánicos el humo daría falsas alarmas (combustión y polvo). El **R** añade **razón de aumento de 15 °F/min** al umbral fijo de 135 °F: detecta un fuego de crecimiento rápido antes de que el cuarto llegue a 135 °F | **H355** (solo temperatura fija): más lento. **H355HT** (190 °F): es para recintos que ya operan calientes, no es el caso |
| **B210LP** | Es la base **incluida** con el SD355 y el H355R, y la única versión vigente para montaje estándar en EE. UU. (la B350LP es la versión *legacy*, ver aviso abajo) | **B501**: flangeless, formato europeo. **B200SR** (base con sirena) y **B224RB** (base con relé): añaden funciones que este diseño no usa |
| **BG-12LX** | **Doble acción** (dos movimientos para activar), que reduce activaciones accidentales en un edificio de acceso público, y direccionable, así que el panel indica *cuál* estación se accionó | **BG-12L** convencional: obligaría a un módulo monitor por estación y perdería la identificación por punto |
| **P2R** | Horn/strobe de **2 hilos**, compatible con NAC Clase B sin cablear la parte visual aparte, con candelas seleccionables en campo (15/15-75/30/75/95/110). Rojo, que es el acabado esperado en equipo de incendio | **P2W** (blanco): estético, sin diferencia técnica. **P2RH** (alta candela 135–185): innecesario, el máximo requerido aquí es 75 cd. Versiones de 4 hilos: exigirían un circuito de potencia adicional |
| **SR** | Estrobo solo, para los recintos donde la norma exige notificación **visual** pero no audible: sanitarios y la oficina. Consume 66 mA en vez de los 79 del horn/strobe | **P2R** en todas partes: sería más caro y añadiría 13 mA por aparato sin aportar nada |
| **ANN-80** | Permite al cuerpo de bomberos leer el estado del sistema **al entrar**, sin bajar al sótano. Es accesorio del catálogo del propio panel, va en el ANN-BUS y su consumo está tabulado en el manual | Montar el **panel** en el vestíbulo: el East Foyer mide 5,5 × 8 ft y es un vestíbulo histórico; un gabinete de 19 × 17 in no cabe ni es admisible en un inmueble protegido |
| **BAT-12120** | Es la batería de **12 V / 12 AH** de la propia serie BAT de Fire•Lite, recomendada por el fabricante para todos sus paneles. El cálculo pide 4,26 AH pero el MS-9600LS **no admite menos de 12 AH**, así que gobierna el mínimo del equipo | **BAT-1270** (7 AH): cubriría el cálculo pero está por debajo del mínimo del panel. **BAT-12180** (18 AH): cabe en el gabinete, pero es sobredimensionar sin motivo |

> ⚠️ **Corrección sobre la base del detector.** Una versión anterior de este documento
> especificaba la base **B350LP**, citando el apéndice D.1 del *SLC Wiring Manual* 51309.
> Ese apéndice se titula literalmente **"Intelligent Detector Base Layouts for Legacy
> Devices"**: la B350LP es la base **descontinuada**. El propio manual lo dice —
> *"Only the B501 Detector Base, **B210LP Detector Base (replacement base for B350LP)**,
> B224RB Relay Base, and B224BI Isolator Base are available as newer type bases"*— y la
> B350LP **no aparece** en su tabla de dispositivos compatibles. Las hojas técnicas
> DF-52384:D y DF-52385:D confirman que la base que viene **incluida** con el SD355 y el
> H355R es la **B210LP(A)**. Corregido a B210LP en toda la documentación.

> **Nota sobre la corriente de standby de los dispositivos del lazo.** El cálculo de la
> §5.3.a usa **0,30 mA por punto**, que es el valor que da la **Tabla 5.3 del manual 52646:B**
> —el método del propio fabricante— para todos los dispositivos SLC. La hoja técnica del
> BG-12LX declara un máximo algo mayor, **375 µA**. Usar el valor de la hoja técnica en las
> 4 estaciones subiría el standby de 0,1933 A a 0,1936 A y la batería calculada de 4,263 AH
> a 4,265 AH: **sin efecto sobre ninguna conclusión**, porque la batería la gobierna el
> mínimo de 12 AH del panel. Se conserva el método del fabricante, que es el citable.

---

## 3.3 Demostración documental de compatibilidad

El enunciado exige: *"No se permitirá combinar dispositivos de diferentes fabricantes sin demostrar documentalmente su compatibilidad y aprobación para trabajar conjuntamente."*

El sistema usa **dos marcas**: Fire•Lite (panel, detección, estación manual, anunciador) y System Sensor (notificación). La compatibilidad se demuestra así:

1. **Fire•Lite *Device Compatibility Document*, P/N 15384:BR (25/01/2022), página 12.** En la sección *System Sensor SpectrAlert Advance*, el **MS-9600LS aparece listado explícitamente** en la columna de UL 864 10.ª edición, junto a los modelos base **P2R, P2RH, SR y SRH**. Es el documento emitido por el fabricante del panel, y es la prueba directa.
2. **Hoja técnica del panel DF-60334:A6, página 1.** Declara *"Selectable strobe synchronization per NAC for **System Sensor**, Wheelock, and Gentex devices"* — es decir, el panel incorpora de fábrica el circuito de sincronización de estrobos de System Sensor.
3. Ambas marcas pertenecen a **Honeywell**, lo que explica la integración, pero **el argumento válido es el documental**, no el corporativo.

> Los dos documentos están en `04_Datasheets/` y se adjuntan al entregable, junto con
> las hojas técnicas de todos los dispositivos de la tabla 3.2.
