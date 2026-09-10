# RECAP DEL PROYECTO
### Sistema de detección y alarma contra incendios — Paxton Carnegie Library
**EL-4601 Normalización Técnica para Electrónica · Proyecto No. 1 · Entrega 9 de septiembre**

---

# 1. Entregables del enunciado (punto 8) — verificación

| # | Entregable exigido | Estado | Dónde está |
|---|---|---|---|
| 1 | **Documento escrito**: investigación normativa, análisis del edificio, selección de equipos, cálculos, justificaciones y conclusiones | 🟢 **Listo** | 5 archivos `.md` — ver mapa en §2 |
| 2 | **Planos arquitectónicos modificados** con la ubicación de todos los dispositivos | 🟡 **Falta terminar** | `Planos/Paxton_Sistema_Alarma.drawio`, págs. 1 y 2 |
| 3 | **Diagrama completo del sistema** | 🟢 **Listo** | `Paxton_Sistema_Alarma.drawio`, pág. 3 (Riser) |
| 4 | **Device Schedule y BOM** con fabricante y modelo | 🟢 **Listo** | `BOM_Calculos/1_BOM_Device_Schedule.csv` |
| 5 | **Datasheets / referencias técnicas** | 🟢 **Listo** | 5 PDF en `Panel/` |
| 6 | **Presentación oral** | 🔴 **No empezada** | ⚠️ ver §5 |
| 7 | **Todas las fuentes referenciadas** | 🟢 **Listo** | `Secciones_6_7_8_Anexos.md` §8 — 13 referencias |
| 8 | **Prompts de IA incluidos íntegramente** | 🟡 **95 %** | `Secciones_6_7_8_Anexos.md`, Anexo A — falta el de Gemini |

## Mínimos del punto 5 (documentación técnica)

| Requisito | Estado | Dónde |
|---|---|---|
| Plano de cada piso con ubicación e identificación | 🟡 | drawio págs. 1–2 |
| Diagrama general de interconexión | 🟢 | drawio pág. 3 |
| Identificación de circuitos o lazos | 🟢 | SLC + NAC-1 a NAC-4, en los tres planos |
| Nomenclatura de dispositivos | 🟢 | `D-`, `M-`, `N-`, `H-` + nivel |
| Lista de materiales (BOM) | 🟢 | `1_BOM_Device_Schedule.csv` |
| Especificaciones de cableado | 🟢 | §3.2 filas 11–13 y §5.3.c/f |

## Cálculos exigidos (punto 5)

| Cálculo | Resultado | Verificación |
|---|---|---|
| Consumo en standby | **0,1933 A** primaria · **0,1413 A** batería | — |
| Consumo en alarma | **1,924 A** | ≤ 7,0 A → **27,5 %** ✔ |
| Caída de tensión en NAC | peor caso **19,72 V** (NAC-2, 174 ft) | ≥ 16 V ✔ |
| Carga NAC ≤ máximo del panel | máx. **0,397 A** | ≤ 3,0 A → **13,2 %** ✔ |
| Capacidad de lazos direccionables | 17 det. + 4 mód. | ≤ 159 c/u → **10,7 %** ✔ |
| *(adicional)* Baterías | 4,26 AH calculado → **12 AH** instalada | mínimo del panel ✔ |

---

# 2. Mapa de archivos → secciones del documento

| Sección del entregable | Archivo | Estado |
|---|---|---|
| Resumen ejecutivo | `Secciones_6_7_8_Anexos.md` *(al final)* | 🟢 |
| **1.** Marco normativo | `Seccion1_Normas_BORRADOR.md` | 🟢 90 % |
| **2.** Análisis del edificio | `Seccion2_Edificio.md` | 🟢 |
| **3.** Selección de equipos | `Seccion3_Equipos.md` | 🟢 |
| **4.** Diseño sobre planos (criterios y ubicaciones) | `Calculo_Deteccion_NFPA72.md` | 🟢 |
| **5.1** Planos por piso | `Planos/Paxton_Sistema_Alarma.drawio` págs. 1–2 | 🟡 |
| **5.2** Diagrama de interconexión | `Planos/Paxton_Sistema_Alarma.drawio` pág. 3 | 🟢 |
| **5.3** Cálculos eléctricos | `Calculo_Electrico_Seccion5.md` | 🟢 |
| **5.4** BOM | `BOM_Calculos/1_BOM_Device_Schedule.csv` | 🟢 |
| **6.** Análisis del diseño | `Secciones_6_7_8_Anexos.md` | 🟢 |
| **7.** Conclusiones | `Secciones_6_7_8_Anexos.md` | 🟢 |
| **8.** Referencias | `Secciones_6_7_8_Anexos.md` | 🟢 |
| **Anexo A** Prompts de IA | `Secciones_6_7_8_Anexos.md` | 🟡 |
| **Anexo B** Datasheets | `Panel/` (5 PDF) | 🟢 |

**Documentos de apoyo (no se entregan):** `RECAP_PROYECTO.md`, `ESTADO_Y_GUIA_PLANOS.md`, `Panel/MS-9600LS_Datos_Panel.md`, y los CSV 0 y 2–6 de `BOM_Calculos/`.

---

# 3. Cómo se justifica CADA decisión técnica

## 3.1 Decisiones de arquitectura del sistema

| Decisión | Justificación | Fuente |
|---|---|---|
| **Arquitectura direccionable** (no convencional) | Edificio histórico: un lazo SLC en vez de un par por zona reduce canalización en mampostería original. Planta libre en piso 1 → la localización por zona sería inútil. Prueba automática cada 2 h y compensación de deriva reducen falsas alarmas en ambiente con polvo de papel | `Seccion3_Equipos.md` §3.1 |
| **Panel Fire•Lite MS-9600LS** (variante sencilla, sin DACT) | Sistema local sin reporte a estación central. Alternativa documentada: MS-9600UDLS o módulo IPDACT | Hoja técnica DF-60334:A6 |
| **Un solo lazo SLC**, sin módulo SLC-2LS | 17 detectores /159 y 4 módulos /159 → 10,7 % de utilización | Manual 52646:B; `Calculo_Electrico_Seccion5.md` §5.3.d |
| **4 circuitos NAC Clase B** | Los 4 vienen integrados; el más cargado usa 13,2 % de su límite | Hoja técnica DF-60334:A6 |
| **Clase B y no Clase A** | Economía de canalización en inmueble protegido. **Declarada como decisión discutible** — Clase A daría tolerancia a fallo único | `Secciones_6_7_8_Anexos.md` §6.2 |
| **Panel en el Electrical Room del sótano** | Es donde está la acometida. El East Foyer mide 5,5 × 8 ft y es un vestíbulo histórico: no admite un gabinete de 19 × 17 in | `Calculo_Electrico_Seccion5.md` §5.3.0 |
| **Anunciador ANN-80 en el East Foyer** | El cuerpo de bomberos lee el estado al entrar sin bajar al sótano. Es accesorio del catálogo del propio panel | Manual 52646:B, Tabla 5.3 |

## 3.2 Decisiones de detección

| Decisión | Justificación | Norma / fuente |
|---|---|---|
| **Espaciamiento de detectores de humo** | S = 30 ft nominal; ningún punto del cielo a más de **0,7 S = 21 ft**; detectores a ≤ 15 ft de paredes | **NFPA 72-2013 §17.7.3.2.3.1** ✅ |
| **2 detectores en Stacks (no 1)** | La esquina crítica del polígono queda a **20,8 ft** del segundo detector; con uno solo, la diagonal supera 42 ft | `Calculo_Deteccion_NFPA72.md` §2 — cálculo desarrollado |
| **1 detector al centro de la rotonda** | d_max = radio = **13,5 ft ≤ 21 ft**. Geometría pura | §17.7.3.2.3.1 |
| **La rotonda se trata como cielo liso**, no inclinado | La lámina 10 muestra que el domo de 43 ft es un **ático**; el cielo del recinto es un casquete con **1'-11" de flecha en 27 ft (≈7 %)**, muy por debajo del umbral de 1 en 8 | `Seccion2_Edificio.md` §2.7 |
| **Las estanterías no obligan a más detectores** | Rematan a **7'-9"** contra cielo de **15'-3¾"** → 7'-7" libres (49 % de la altura). La regla del 15 % no se activa | **§17.7.3.2.3.1** + lámina 9 |
| **Detección térmica en los 2 cuartos mecánicos** | Ambiente con combustión y polvo: el humo daría falsas alarmas | NFPA 72-2013 cap. 17 |
| **Un solo detector térmico por cuarto mecánico** | El sótano mide **8'-3"** de alto: por debajo de los 10 ft donde §17.6.3.5.1 obliga a reducir el espaciamiento | **§17.6.3.5.1** + Tabla 17.6.3.5.1 ✅ |
| **Sin detector en sanitarios ni baño** | No requerido; sí llevan notificación visual | — |
| **1 detector en cabeza de escalera (South Foyer)** | Es la **única** conexión vertical interior del edificio | `Seccion2_Edificio.md` §2.5 |
| **Solo una escalera interior** | Verificado ampliando el TIFF: las otras dos "DN" están fuera del muro exterior (fosos y escalinata de entrada), confirmado por la *Section at Steps* de la lámina 5 | Láminas 3, 4 y 5 |

## 3.3 Decisiones de notificación

| Decisión | Justificación | Norma / fuente |
|---|---|---|
| **Candelas según tamaño de recinto** | 15 cd hasta 20×20 ft · 30 cd hasta 28×28 ft · 34 cd hasta 30×30 ft | **Tabla 18.5.5.4.1(a)** ✅ |
| **75 cd en Stacks (no 30)** | Envolvente **28,3 × 28,3 ft**: supera la fila de 28×28 y cae en la de 30×30 → exige 34 cd. El SpectrAlert no tiene 34, el siguiente paso es 75 | **Tabla 18.5.5.4.1(a)** + **§18.5.5.4.5** ✅ |
| *Alternativa válida no adoptada* | Dos aparatos de 15 cd subdividiendo la sala en cuadrados | **§18.5.5.4.5** |
| **Strobe en sanitarios y baño, sin detector** | Se requiere notificación visual en servicios sanitarios | NFPA 72-2013 cap. 18 |
| **Montaje de strobes a 80 in** | La lente completa entre **80 in y 96 in**. Sótano: cielo a 99 in → válido con 19 in de margen, sin aplicar la reducción de §18.5.5.2 | **§18.5.5.1 / §18.5.5.2** ✅ |
| **Patrón Temporal High** para el cálculo | Temporal 3 es el patrón de evacuación; High dBA es el caso desfavorable de consumo | AVDS102 |
| **4 estaciones manuales, una por salida** | Dentro de **5 ft** de cada salida; elemento operable entre **42 y 48 in** del piso | **§17.14.8.4 / §17.14.5** ✅ |

## 3.4 Decisiones eléctricas

| Decisión | Justificación | Fuente |
|---|---|---|
| **Método de cálculo del fabricante** | Se usaron las Tablas 5.3 y 5.4 del manual, no un método genérico | Manual **52646:B** |
| **Valor global de 0,400 A para el SLC en alarma** | El propio manual lo permite con un solo lazo, en vez de sumar dispositivo por dispositivo | Manual 52646:B, Tabla 5.3 |
| **Cableado NAC 16 AWG FPLR** | Caída peor caso **0,676 V** → 19,72 V ≥ 16 V, con 3,7 V de margen. El 14 AWG no lo exige el cálculo | **NEC cap. 9 Tabla 8** |
| **Resistencias del NEC, no teóricas** | La plantilla traía valores a 20 °C (4,02 Ω/kft para 16 AWG); el NEC da **4,89** y es la fuente citable. Los teóricos **subestiman** la caída | NEC cap. 9 Tabla 8 |
| **Tensión de partida 20,4 V** | Caso desfavorable: baterías al final de la descarga (85 % de 24 V) | práctica estándar |
| **V mínimo = 16 V** | Rango de operación del SpectrAlert a 24 V nominal: **16 a 33 V** | AVDS102 |
| **Método conservador de caída** | Toda la corriente recorre toda la longitud (aparatos concentrados en el extremo) | — |
| **Batería 12 AH** | Calculado **4,26 AH**, pero el panel **no admite menos de 12 AH** → gobierna el mínimo del equipo | Manual 52646:B §5.4.2 |
| **Sin gabinete externo BB-26** | 12 AH < 18 AH que admite el gabinete | Manual 52646:B §5.4.2 |
| **Circuito AC dedicado, 14 AWG/600 V** | Derivado exclusivo, rotulado FIRE ALARM, sin desconectadores | Manual 52646:B §5.2 · **NEC Art. 760** |
| **Cableado SLC 16 AWG** | 16 AWG admite hasta **4 875 ft** (el límite de 10 000 ft es del 12 AWG); el lazo mide ≈1 200 ft → 24,6 %. R c.c. 11,7 Ω ≤ 40 Ω exigidos en Style 4 | **Fire•Lite doc. 51309**, Tablas 2.1/2.2 y §2.2.1 |

## 3.5 Decisiones normativas de fondo

| Decisión | Justificación | Fuente |
|---|---|---|
| **Se cita NFPA 72 edición 2013** | Cadena: *41 Ill. Adm. Code* Parte 100 §100.7 → NFPA 101-2015 → NFPA 72-2013 (cap. 2, Referenced Publications) | `Seccion1_Normas_BORRADOR.md` §1.4 |
| **Clasificación IBC Grupo A-3** | Carga ocupacional **≈53** por Tabla 1004.5, apenas sobre el umbral de 50 | `Seccion2_Edificio.md` §2.8 |
| **El sistema es voluntario (no requerido)** | Con ≈53 ocupantes y área muy inferior a 12 000 ft², el IBC probablemente no lo exige. Pero NFPA 72 obliga a que un sistema no requerido cumpla el Código completo | `Seccion2_Edificio.md` §2.8 · `Seccion1` §1.5 |
| **Compatibilidad Fire•Lite + System Sensor** | El **MS-9600LS aparece listado** con los modelos P2R/P2RH/SR/SRH en la pág. 12 del DCD, emitido por el fabricante del panel | **DCD P/N 15384:BR** |
| **Base B350LP** | Confirmada en el apéndice D.1 del SLC Wiring Manual | **Fire•Lite doc. 51309** |
| **Medición de áreas a 100 px/pie** | TIFF a 400 dpi × escala ¼"=1'-0". Verificado contra la barra gráfica (8 ft = 800 px) y contra las cotas rotuladas | `Seccion2_Edificio.md` §2.3 |

---

# 4. Referencias completas

## Normas y códigos

1. NFPA. *NFPA 72: National Fire Alarm and Signaling Code*, **edición 2013**. Quincy, MA.
2. NFPA. *NFPA 101: Life Safety Code*, **edición 2015**. Quincy, MA.
3. Office of the Illinois State Fire Marshal. **41 Ill. Adm. Code, Parte 100** — *Fire Prevention and Safety*. §100.3 (jurisdicción), §100.7 (adopción de NFPA 101). https://www.ilga.gov/Commission/jcar/admincode/JCARTitlePart.asp?Title=041&Part=0100
4. NFPA. *NFPA 70: National Electrical Code*. Artículo 760; Capítulo 9, Tabla 8.
5. International Code Council. *International Building Code (IBC)*. Tabla 1004.5; §903.2.1.3; §907.2.1.
6. International Code Council. *International Fire Code (IFC)*.
7. Underwriters Laboratories. *UL 864: Control Units and Accessories for Fire Alarm Systems*, 10.ª edición.

## Planos arquitectónicos

8. Historic American Buildings Survey. *Paxton Carnegie Library, 254 South Market Street, Paxton, Ford County, Illinois*. **HABS No. IL-329**. Charles E. Peterson Prize Competition Entry, 2012. National Park Service, U.S. Department of the Interior. Library of Congress, Prints and Photographs Division. https://www.loc.gov/item/il0998/
   - Lám. 2 — *Site Plan* (1"=20'-0"), Lauren Nurse y Theresa Scott
   - Lám. 3 — *Basement Plan* (¼"=1'-0"), Travis Dean
   - Lám. 4 — *First Floor Plan* (¼"=1'-0"), Brodie Bricker
   - Lám. 5 — *East Elevation* (¼"=1'-0"), Laura Mann
   - Lám. 9 — *East-West Section* (⅜"=1'-0"), Brodie Bricker
   - Lám. 10 — *North-South Section* (⅜"=1'-0"), Brodie Bricker
   - Lám. 11 — *Elevation at Entry* (¾"=1'-0"), Laura Mann

## Documentación de fabricante

9. Fire•Lite Alarms (Honeywell). *MS-9600LS(E)/MS-9600UDLS(E) Intelligent Addressable FACP*. Hoja técnica **DF-60334:A6**, 20/02/2019.
10. Fire•Lite Alarms (Honeywell). *MS-9600LS Series Addressable FACP — Installation Manual*. **PN 52646:B**, 17/06/2008.
11. Fire•Lite Alarms (Honeywell). *Device Compatibility Document*. **P/N 15384:BR**, 25/01/2022, ECN 151532.
12. Fire•Lite Alarms (Honeywell). *SLC Wiring Manual*. Documento **51309**.
13. System Sensor (Honeywell). *SpectrAlert Advance — Indoor Wall Horns, Strobes and Horn Strobes*. Hoja técnica **AVDS102**.

## Fuentes consultadas para determinar la jurisdicción

14. Office of the Illinois State Fire Marshal. *Life Safety Code*. https://sfm.illinois.gov/resources/life-safety-code.html
15. Cornell Legal Information Institute. *Ill. Admin. Code tit. 41, §100.3 y §100.7*. https://www.law.cornell.edu/regulations/illinois/
16. NFPA. *Free access to codes and standards*. https://www.nfpa.org/for-professionals/codes-and-standards/list-of-codes-and-standards/free-access

---

# 5. Lo que falta

| # | Pendiente | Quién | Riesgo |
|---|---|---|---|
| 1 | **Terminar el dibujo**: ajustar recorrido del cableado, marcar subida entre pisos, dibujar acometida y baterías, exportar a PDF/PNG | Walter | 🔴 alto — es el entregable 2 |
| 2 | **Preparar la presentación oral** | ambos | 🔴 alto — es el entregable 6 y no tiene nada |
| 3 | Pegar el prompt de Gemini en el Anexo A, fila 5 | Walter | 🟡 |
| 4 | Confirmar si Paxton tiene ordenanza propia | Walter | 🟡 |
| 5 | Revisar NFPA 101-2015 cap. 13 y las 6 subsecciones ⚠️ de la tabla 1.2 | Walter | 🟡 |
| 6 | Consolidar los `.md` en el documento final y exportar a PDF | ambos | 🟡 |

## ⚠️ Un archivo que NO se debe usar

`Panel/72-29.9 Power Supplies.pdf` es un extracto del **capítulo 29** de NFPA 72-2019, que trata de **alarmas de estación única y sistemas domésticos** (*Single- and Multiple-Station Alarms and Household Fire Alarm Systems*). Su requisito de **7 días + 4 minutos** aplica a detectores de humo residenciales, **no** a este proyecto.

Este edificio tiene un **sistema de premisas protegidas** en una ocupación de asamblea: el respaldo de energía se rige por el **capítulo 10 (§10.6.7)** con **24 h + 5 min**, que es lo que se usó. Citar el §29.9 sería un error de fondo. Además ese extracto es de la edición **2019** y aquí aplica la **2013**.

## Sobre la presentación oral

Cada quien expone su eje. Las decisiones que conviene destacar, porque son las que tienen mejor respaldo:

1. **Por qué direccionable** — el argumento del edificio histórico es el más fuerte y es específico de este caso.
2. **Los dos detectores de Stacks** — es el único cálculo de espaciamiento no obvio y está desarrollado paso a paso.
3. **El domo que resultó ser un ático** — muestra que se leyó la sección y no se asumió.
4. **La batería que la gobierna el mínimo del panel, no el cálculo** — resultado contraintuitivo y bien sustentado.
5. **La cadena de jurisdicción de Illinois** — explica por qué se cita la edición 2013 y no la última.
6. **Los cinco errores que detectó la verificación** (Anexo A) — el enunciado exige mencionar los prompts en la presentación; esto convierte ese requisito en un punto a favor.
