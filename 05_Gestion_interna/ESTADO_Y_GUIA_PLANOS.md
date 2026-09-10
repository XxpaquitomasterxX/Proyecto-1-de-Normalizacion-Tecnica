# Estado del proyecto y guía para hacer los planos
**Corte al 5 de septiembre · Entrega 9 de septiembre · Equipo: Walter y Sebastián**

---

# PARTE 1 — Estado real, sección por sección

| Sec. | Qué pide | Estado | Qué falta |
|---|---|---|---|
| **Resumen ejec.** | Media página | 🟢 **100 %** | en `Secciones_6_7_8_Anexos.md` |
| **1** | Marco normativo | 🟢 **90 %** | edición y jurisdicción resueltas; quedan 6 subsecciones por afinar |
| **2** | Análisis del edificio | 🟢 **100 %** | — |
| **3** | Selección de equipos | 🟢 **95 %** | confirmar la base B350LP en el DCD |
| **4** | Diseño sobre planos | 🟢 **100 %** | — |
| **5.1** | Planos por piso | 🟢 **95 %** | solo falta exportar a PDF/PNG |
| **5.2** | Riser | 🟢 **100 %** | página 3 del draw.io |
| **5.3** | Cálculos eléctricos | 🟢 **100 %** | — |
| **5.4** | BOM | 🟢 **95 %** | agregar precios si los piden |
| **6** | Análisis del diseño | 🟢 **100 %** | — |
| **7** | Conclusiones | 🟢 **100 %** | — |
| **8** | Referencias | 🟢 **100 %** | declarar ediciones |
| **Anexo A** | **Prompts de IA** | 🟢 **95 %** | solo falta el texto del prompt de Gemini |
| **Anexo B** | Datasheets | 🟢 **100 %** | los 4 PDF en `Panel/` |

## Mapa de archivos → secciones del documento

| Sección del entregable | Archivo |
|---|---|
| Resumen ejecutivo | `Secciones_6_7_8_Anexos.md` (al final) |
| 1. Marco normativo | `Seccion1_Normas_BORRADOR.md` |
| 2. Análisis del edificio | `Seccion2_Edificio.md` |
| 3. Selección de equipos | `Seccion3_Equipos.md` |
| 4. Diseño sobre planos | `Calculo_Deteccion_NFPA72.md` + planos |
| 5.1 / 5.2 Planos y riser | `Planos/Paxton_Sistema_Alarma.drawio` (3 páginas) |
| 5.3 Cálculos eléctricos | `Calculo_Electrico_Seccion5.md` |
| 5.4 BOM | `BOM_Calculos/1_BOM_Device_Schedule.csv` |
| 6, 7, 8, Anexos A y B | `Secciones_6_7_8_Anexos.md` |

## Lo que está terminado y no hay que volver a tocar

- **Sección 2 completa.** Ubicación, niveles, cotas verificadas contra el TIFF, alturas de cielo (15'-3¾" piso 1 / 17'-3" rotonda / 8'-3" sótano), distribución de los dos pisos, accesos, cuartos de servicio, carga ocupacional (≈53 → IBC Grupo A-3).
- **Todos los cálculos de la Sección 5.3.** Standby 0,1413 A · alarma 1,924 A (27,5 % del panel) · caída peor caso 19,98 V ≥ 16 V · SLC 10,7 % · batería 12 AH.
- **Cálculo de detección**, recinto por recinto con la regla del 0,7S, y las dos incógnitas normativas cerradas (el domo es un ático, no el cielo; las estanterías no compartimentan).
- **Los 7 documentos fuente** en `Panel/` y `Planos/`.

## Los 4 pendientes reales

1. **Exportar los planos** a PDF y PNG 300 dpi desde draw.io (File → Export as). El dibujo ya está terminado.
2. **Preparar la presentación oral** — es el entregable 6 y no tiene nada.
3. **Confirmar si Paxton tiene ordenanza propia** (método en §1.4 del borrador de la Sección 1) y revisar **NFPA 101-2015 cap. 13**.
4. **Pegar el prompt de Gemini** en la fila 5 del Anexo A.

## Correcciones aplicadas al dibujo (7 sep)

- **Cableado con recorrido explícito**: 25 tramos con vértices para que el cable corra pegado a muros y por la circulación, entrando a cada recinto por su vano de puerta. Ya no atraviesa tabiques en puntos arbitrarios ni cruza salas por el medio.
- **N-103 movido al muro de la rotonda** (31,5 · 41,5) — antes flotaba fuera de la sala que debe cubrir.
- **N-104 movido al muro norte del bloque de servicios** (18 · 30) — antes flotaba en piso abierto.
- **N-108 movido al muro del South Foyer** (11,8 · 47).
- **M-102 movida junto a la puerta de salida sur** (18,5 · 50) para cumplir los 5 ft de §17.14.8.4.
- **N-004, N-005 y N-006 llevados sobre muro** en el sótano.
- **Marcadores de riser** en el South Foyer de ambas plantas (subida/bajada del lazo SLC).
- **Cuadro de acometida y baterías** junto al FACP en la página del sótano.
- **Etiquetas reubicadas** en 10 dispositivos que chocaban con los rótulos de recinto.
- **Nota de criterio de recorrido** agregada al cuadro de circuitos.

---

# PARTE 2 — Cómo hacer los planos

## Ya les dejé el archivo armado

**`Planos/Paxton_Sistema_Alarma.drawio`** — ábranlo en https://app.diagrams.net (File → Open From → Device). Trae:

- **2 páginas:** *Piso 1* y *Sótano*, con el plano arquitectónico de fondo **a escala** (25 px = 1 pie).
- **Los 36 dispositivos ya colocados** en las coordenadas exactas del cálculo, con su nomenclatura (D-101, N-103, M-002…).
- **El cableado dibujado:** lazo SLC en azul continuo, circuitos NAC en rojo punteado.
- **Leyenda de símbolos** y cajetín con datos del edificio.
- **5 capas** (Extras → Edit Diagram… o el panel de capas): Plano de fondo *(bloqueada)*, Detección, Notificación, Cableado, Leyenda.
- **Tooltips:** pasen el mouse por cualquier dispositivo y les dice qué es y por qué está ahí.

> El fondo está bloqueado a propósito para que no se les mueva. Si necesitan moverlo, desbloqueen la capa "Plano de fondo".

## Qué debe llevar exactamente

Esto sale textual del enunciado (puntos 4 y 5). Úsenlo de checklist:

| # | Requisito | ¿Está? |
|---|---|---|
| 1 | Ubicación del panel de control | ✔ FACP en Electrical Room del sótano |
| 2 | Ubicación de detectores de humo y/o temperatura | ✔ 15 humo + 2 térmicos |
| 3 | Ubicación de estaciones manuales | ✔ 4, una por salida |
| 4 | Ubicación de horn/strobes y strobes | ✔ 11 + 4 |
| 5 | Dispositivos adicionales | ✔ anunciador ANN-80 |
| 6 | **Identificación de circuitos o lazos** | ✔ SLC + NAC-1 a NAC-4 |
| 7 | **Distribución del cableado** | ✔ trazado, revisar recorrido |
| 8 | **Conexión entre pisos** | ⚠️ **falta** — ver abajo |
| 9 | Integración de supervisión/monitoreo | ⚠️ mencionar el ANN-80 |
| 10 | Alimentación principal y respaldo | ⚠️ **falta** dibujar la acometida y las baterías |
| 11 | **Nomenclatura de dispositivos** | ✔ |
| 12 | **Leyenda de símbolos clara y consistente** | ✔ |

**Los tres pendientes (8, 9, 10) se resuelven en el riser, no en las plantas.**

## Los 5 pasos que faltan en draw.io

**1. Revisar que cada dispositivo cayó en el recinto correcto.**
Las posiciones salen del cálculo, pero conviene verificarlas contra el fondo. Si mueven uno, **anoten cuánto lo movieron** — si se aleja del centro puede romper la regla de los 21 ft.

**2. Ajustar el recorrido del cableado.**
Las líneas hoy van en ruta ortogonal automática. En un plano real el cable va **por pasillos y junto a muros**, no cruzando salas en diagonal. Arrastren los puntos intermedios de cada línea. Es lo que más "cara de plano profesional" le da.

**3. Marcar la subida entre pisos.**
En ambas páginas, poner un símbolo en el **South Foyer** (la única escalera interior) que diga `SLC ↑ AL PISO 1` / `SLC ↓ AL SÓTANO`. Eso cubre el requisito 8.

**4. Agregar la acometida.**
En la página del sótano, junto al FACP, dibujar: `120 VAC ← circuito derivado dedicado, rotulado FIRE ALARM, 14 AWG` y `2 × batería 12 V / 12 AH`. Cubre el requisito 10.

**5. Exportar.**
File → Export as → **PDF**, marcando *Selection Only: no* y *Crop: no*. Para pegar en el documento, exporten también **PNG a 300 dpi** (marcar "Transparent: no"). Una página por piso.

## El riser diagram (Sección 5.2) — qué es

Es el **diagrama unifilar del sistema**: no es un plano, no tiene escala y no representa geometría. Es un esquema de bloques que muestra **cómo se conecta todo eléctricamente**. Se lee de arriba abajo por niveles.

Debe mostrar, de arriba abajo:

```
        120 VAC ── circuito derivado dedicado "FIRE ALARM", 14 AWG, NEC Art. 760
                        │
              ┌─────────┴──────────┐
              │  FACP MS-9600LS    │──── 2 x bateria 12V/12AH (24 V, 12 AH)
              │  Electrical Room   │──── ANN-BUS ──> ANN-80 (East Foyer)
              └─┬────┬────┬────┬───┘
                │    │    │    │
        SLC ────┘    │    │    └──── NAC-1  0,334 A  Piso 1 norte  (3 disp.)
     1 lazo,         │    └───────── NAC-2  0,397 A  Piso 1 sur    (5 disp.)
     21 puntos       └────────────── NAC-3  0,293 A  Sotano norte  (3 disp.)
     Clase B                         NAC-4  0,290 A  Sotano sur    (4 disp.)
     (Style 4)
```

Y en cada rama, listar los dispositivos con su etiqueta. Poner al lado la corriente de cada circuito y la verificación (≤3,0 A por NAC, ≤7,0 A total).

**Se dibuja en draw.io igual, en una tercera página, con cajas y líneas.** No lleva plano de fondo.

## Reglas de dibujo que el profesor va a mirar

1. **Un símbolo = un tipo de dispositivo, siempre igual.** Si el detector de humo es un círculo azul, lo es en las dos páginas.
2. **Toda etiqueta en la leyenda.** Ningún símbolo sin explicar.
3. **Nomenclatura con lógica.** La que usamos: `D-` detección, `M-` manual, `N-` notificación. Primer dígito = nivel (1 = piso 1, 0 = sótano).
4. **Distinguir detección de notificación por color.** Azul vs rojo.
5. **Cajetín** con nombre del edificio, escala, nivel, autores y fecha.
6. **La escala se declara.** El fondo está a 25 px = 1 pie; al exportar a PDF, poner la barra gráfica del plano original o escribir la escala.

---

# Referencias (para la Sección 8, ya identificadas)

1. **NFPA 72**, *National Fire Alarm and Signaling Code*, edición 20XX. NFPA, Quincy, MA. *(declarar la edición que usen)*
2. **NFPA 70**, *National Electrical Code* — Artículo 760 y Capítulo 9 Tabla 8.
3. **International Building Code (IBC)** — Tabla 1004.5, §903.2.1.3, §907.2.1.
4. **International Fire Code (IFC)**.
5. Historic American Buildings Survey, **HABS IL-329**, *Paxton Carnegie Library, 254 S. Market Street, Paxton, Ford County, IL*. Charles E. Peterson Prize Competition Entry 2012. National Park Service, U.S. Dept. of the Interior. Library of Congress, https://www.loc.gov/item/il0998/ — láminas 2, 3, 4, 5, 9, 10 y 11.
6. Fire•Lite Alarms, *MS-9600LS(E)/MS-9600UDLS(E) Intelligent Addressable FACP*, hoja técnica **DF-60334:A6**, 2019.
7. Fire•Lite Alarms, *MS-9600LS Series Addressable FACP Installation Manual*, **PN 52646:B**, 2008.
8. Fire•Lite Alarms, *Device Compatibility Document*, **P/N 15384:BR**, 25/01/2022.
9. System Sensor, *SpectrAlert Advance — Indoor Wall Horns, Strobes and Horn Strobes*, datasheet **AVDS102**.
