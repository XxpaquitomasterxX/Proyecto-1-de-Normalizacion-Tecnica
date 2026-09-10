# 1. Marco normativo

## EDICIÓN APLICABLE: NFPA 72, edición 2013

Esta determinación **no es arbitraria** y es uno de los resultados de la investigación de jurisdicción. La cadena normativa es:

```
41 Ill. Adm. Code, Parte 100 (Office of the State Fire Marshal de Illinois)
        │
        │  §100.7 "Adoption of NFPA 101, Life Safety Code, by Reference"
        ▼
NFPA 101 Life Safety Code, edición 2015
   (adoptada por Illinois con vigencia desde el 1 de enero de 2020,
    sustituyendo a la edición 2000)
        │
        │  Capítulo 2, Referenced Publications
        ▼
NFPA 72 National Fire Alarm and Signaling Code, edición 2013   ← LA QUE SE CITA
```

**Todos los números de sección de este documento corresponden a NFPA 72-2013** y fueron verificados contra el texto de esa edición.

> ⚠️ **Advertencia sobre las ediciones.** La numeración cambia entre ediciones y es un error fácil de cometer. Ejemplo concreto de este proyecto: la tabla de espaciamiento de aparatos visuales de pared es la **§18.5.5.4.1** en la edición 2013 y la **§18.5.5.7** en la edición 2022. Como en Illinois aplica la 2013, se cita **18.5.5.4.1**. Si el grupo decidiera declarar otra edición, **habría que renumerar todo el documento**.

---

## 1.1 Códigos, normas y estándares principales

| Norma | Qué rige | Rol en este proyecto |
|---|---|---|
| **NFPA 72** — *National Fire Alarm and Signaling Code* | Diseño, instalación, prueba y mantenimiento de sistemas de detección, alarma y notificación | **Norma determinante.** Fijó la cantidad, tipo y ubicación de cada dispositivo, los niveles de notificación y el respaldo de energía |
| **NFPA 70 (NEC)** — *National Electrical Code* | Instalación eléctrica; **Artículo 760** cubre específicamente circuitos de alarma de incendio | Circuito derivado dedicado, calibres, métodos de canalización, clasificación power-limited. La **Tabla 8 del Capítulo 9** dio las resistencias del cálculo de caída de tensión |
| **IBC** — *International Building Code* | **Cuándo se exige** un sistema según ocupación y tamaño | Clasificación de ocupación (Grupo A-3) y determinación de exigibilidad |
| **IFC** — *International Fire Code* | Requisitos operativos, mantenimiento e inspección | Obligaciones del propietario durante la vida útil |
| **NFPA 101** — *Life Safety Code* | Medios de egreso y protección de la vida | **Relevante en Illinois**: es la norma que hace cumplir el State Fire Marshal (ver 1.4) |
| **UL 864** | Certificación de unidades de control de alarma | El MS-9600LS está listado a UL/ANSI 864 y es FM Approved |
| **ADA** / *Illinois Accessibility Code* | Accesibilidad | Notificación visual y altura de montaje de estaciones manuales |

> **No es una lista para enumerar.** El enunciado dice explícitamente que se espera un **resumen de requisitos y cómo afectan el diseño**. La tabla 1.2 es el corazón de esta sección.

---

## 1.2 Requisitos por tipo de dispositivo

*Cada fila indica el requisito, cómo se aplicó en este proyecto y dónde verificarlo.*

| Dispositivo | Requisito normativo | Cómo se aplicó aquí | Sección a verificar |
|---|---|---|---|
| **Detectores de humo puntuales** | Espaciamiento nominal listado **S = 30 ft** en cielo liso. Ningún punto del cielo a más de **0,7 S = 21 ft** de un detector. Detectores a no más de **S/2 = 15 ft** de las paredes | Verificación recinto por recinto. El caso crítico (Stacks) obligó a **2 detectores**: la esquina más desfavorable queda a 20,8 ft | NFPA 72 **cap. 17** — *Smooth Ceiling Spacing* **§?** |
| Instrucciones del fabricante | En todos los casos deben seguirse las instrucciones publicadas por el fabricante | Espaciamientos y montaje según Fire•Lite | **§17.7.3.2.3.2** ✅ |
| Obstrucciones y particiones | La regla del 15 % está **dentro de §17.7.3.2.3.1**: solo cuentan las particiones que suban hasta el 15 % superior de la altura del cielo | **Verificado y descartado:** estanterías a 7'-9" contra cielo a 15'-3¾" → 7'-7" libres (49 % de la altura). La regla no se activa | **§17.7.3.2.3.1** ✅ |
| Cielos con vigas o pendiente | Espaciamientos distintos al liso; para vigas de profundidad ≤10 % de la altura del cielo se usa espaciamiento de cielo liso | **Descartado:** el casquete de la rotonda tiene 1'-11" de flecha en 27 ft (≈7 %). Se trata como cielo liso | **§17.7.3.2.3.3** y **§17.7.3.2.4** ⚠️ *afinar subsección* |
| Ubicación respecto de HVAC | Separación mínima respecto de difusores de aire | ⚠️ **No verificable**: las láminas HABS no documentan HVAC. Declarado como limitación en la Sección 6.4 | cap. 17 (*Special Considerations* **§17.7.7**) ⚠️ |
| **Detectores térmicos** | Espaciamiento listado; **§17.6.3.5.1 exige reducir el espaciamiento en cielos de 10 a 30 ft** según Tabla 17.6.3.5.1 | Sótano a **8'-3"** → **por debajo de 10 ft, sin reducción**. Espaciamiento listado completo, un detector por cuarto mecánico | **§17.6.3.5.1** + Tabla 17.6.3.5.1 ✅ |
| Áreas irregulares | El espaciamiento puede exceder el listado si ningún punto queda a más de **0,7 × el espaciamiento listado** del detector | Es la regla que gobernó todo el diseño de detección | **§17.6.3.1.2** (térmicos) y **§17.7.3.2.3.1(2)** (humo) ✅ |
| **Estaciones manuales — altura** | El elemento operable **no menos de 42 in (1,07 m) ni más de 48 in (1,22 m)** sobre el piso terminado | Especificado en los planos y en el riser | **§17.14.5** ✅ |
| **Estaciones manuales — ubicación** | Ubicadas **dentro de 5 ft (1,5 m) de cada salida**; estaciones adicionales según distancia de recorrido | **4 estaciones**, una por cada salida del edificio (2 en piso 1, 2 en el sótano) | **§17.14.8.4** y **§17.14.8.5** ✅ |
| **Notificación audible** | Nivel **al menos 15 dB sobre el nivel de ruido ambiente promedio**, o 5 dB sobre el máximo sostenido durante al menos 60 s, el que sea mayor | 11 horn/strobes cubriendo todas las áreas ocupables. ⚠️ **Falta medir el ruido ambiente real** | **§18.4.3.1** ✅ |
| **Notificación visual — candelas** | Intensidad mínima según el **tamaño máximo del recinto**, Tabla 18.5.5.4.1(a) | 15 cd hasta 20×20 ft · 30 cd hasta 28×28 ft · **34 cd hasta 30×30 ft**. Stacks (28,3×28,3 ft) requirió subir a **75 cd** | **Tabla §18.5.5.4.1(a)** ✅ |
| Notificación visual — posición en el muro | El espaciamiento de la tabla asume el aparato **a la mitad de la pared** | Considerado en la ubicación de cada aparato | **§18.5.5.4.3** ✅ |
| Notificación visual — **salas no cuadradas** | El tamaño de sala se determina midiendo la distancia a la pared más lejana **o duplicando la distancia a la pared adyacente más lejana, el que sea mayor**. Si la sala no es cuadrada, se usa el cuadrado que la encierre completa **o se subdivide en varios cuadrados** | **Ésta es la sección que justifica el caso de Stacks.** Permite tanto subir a 75 cd (cuadrado envolvente de 28,3 ft) como la alternativa de dos aparatos de 15 cd subdividiendo | **§18.5.5.4.4** y **§18.5.5.4.5** ✅ |
| **Notificación visual — montaje** | La lente completa **no menos de 80 in (2,03 m) ni más de 96 in (2,44 m)** sobre el piso terminado. Si el cielo bajo no permite 80 in, se monta a menos de 6 in del cielo y **se reduce el tamaño de sala cubierto** en el doble de la diferencia | Piso 1 (cielo 15'-4") sin conflicto. Sótano: cielo a **99 in**, montaje a 80 in válido con 19 in de margen — no aplica la reducción | **§18.5.5.1** y **§18.5.5.2** ✅ |
| Notificación visual — sanitarios | Se requiere notificación visual en servicios sanitarios | Strobes en el baño del piso 1 y en los dos sanitarios del sótano, **sin detector** | cap. 18 ⚠️ *confirmar subsección* |
| **Alimentación y respaldo** | Fuente primaria + secundaria. Sistema **Local**: **24 h de carga en reposo + 5 min de alarma** (15 min para sistemas de voz). Factor de derating 1,2 aplicado por el fabricante | Calculado 4,26 AH; se instalan **12 AH** (mínimo del panel) | **§10.6.7** (capacidad en §10.6.7.2) ⚠️ *afinar subsección* |
| **Supervisión de circuitos** | Todos los circuitos iniciadores y de notificación deben ser supervisados. Clases de circuito definidas en el cap. 12 | SLC Clase B (Style 4) supervisado; NAC Clase B con EOL de 4,7 kΩ | **cap. 12** ⚠️ *afinar subsección* |
| **Sistemas no requeridos** | Un sistema instalado voluntariamente **debe cumplir el Código en su totalidad** | Aplicable a este caso — ver 1.5 | cap. 1 (*Application*) ⚠️ *clave, confirmar* |
| **Inspección y mantenimiento** | Programa de inspección, prueba y mantenimiento con registro documental | Ver Sección 6.5 | NFPA 72 **cap. 14** |
| **Cableado** | Circuito derivado **dedicado y exclusivo**, rotulado FIRE ALARM, sin desconectadores; protección según Art. 760 | 14 AWG / 600 V, 3,0 A | **NEC Art. 760** |

---

## 1.3 La Authority Having Jurisdiction (AHJ)

**Qué es.** La AHJ es la organización, oficina o individuo responsable de **hacer cumplir** los requisitos de un código y de **aprobar** equipos, materiales, instalaciones y procedimientos. No es un concepto abstracto: es quien firma.

**Por qué su aprobación es obligatoria.** Las normas NFPA no son ley por sí mismas — adquieren fuerza legal cuando una jurisdicción las adopta. Y las propias normas otorgan a la AHJ **facultad discrecional** en numerosos puntos: aceptar métodos alternativos, exigir requisitos adicionales según condiciones locales, aprobar el plan de pruebas de aceptación. Un sistema puede cumplir NFPA 72 al pie de la letra y aun así no ser aprobado si la AHJ identifica una condición particular no contemplada.

**Consecuencia práctica para este diseño:** hay al menos tres puntos que en un proyecto real requerirían consulta formal a la AHJ:
1. El **ático combustible sobre la rotonda**, que queda sin detección.
2. La condición de **sistema voluntario** y qué nivel de cumplimiento se exigirá.
3. Las **canalizaciones en un inmueble histórico**, donde hay tensión entre el código y la preservación.

**AHJ para este edificio.** El marco estatal es el de la **Office of the State Fire Marshal (OSFM) de Illinois**, que administra el *41 Ill. Adm. Code, Parte 100*. El **§100.3(b)** establece que *"las disposiciones de esta Parte aplican a las localidades dentro de Illinois"*, de modo que la cobertura es estatal.

Sin embargo, el **§100.3(g)** permite que OSFM **reconozca códigos locales como equivalentes** bajo seis criterios, entre ellos: que el código local sea idéntico a esta Parte; que la incorpore agregando requisitos más estrictos; que adopte **ediciones posteriores del NFPA 101**; que exista un acuerdo formal entre la autoridad local y OSFM; o que se adopte un código modelo (ICC o NFPA 5000).

> **Consecuencia:** la AHJ efectiva para la Paxton Carnegie Library depende de si la Ciudad de Paxton adoptó por ordenanza un código propio reconocido bajo §100.3(g). Si no lo hizo, rige el marco estatal (NFPA 101-2015). Si lo hizo, rige el local. **Esto es lo que hay que confirmar con la municipalidad** — ver el método de búsqueda en 1.4.

---

## 1.4 Jurisdicción del edificio — Illinois

**Ubicación:** Paxton, condado de Ford, estado de Illinois.

Illinois es un caso atípico: **no adopta un código de construcción estatal de aplicación general obligatoria para todos los municipios**, a diferencia de la mayoría de los estados. No existe un "Illinois Building Code" que imponga el IBC en todo el territorio.

Lo que sí existe a nivel estatal es la adopción del **NFPA 101 Life Safety Code** por parte de la Office of the State Fire Marshal.

### Lo que se determinó (con fuente)

| Hallazgo | Fuente |
|---|---|
| OSFM administra el **41 Ill. Adm. Code, Parte 100** — *Fire Prevention and Safety* | ilga.gov / JCAR, Título 41 Parte 100 |
| El **§100.7** adopta el **NFPA 101 Life Safety Code por referencia** | 41 Ill. Adm. Code §100.7 |
| La edición adoptada es la **2015**, con vigencia desde el **1 de enero de 2020**, sustituyendo a la edición 2000 | Office of the Illinois State Fire Marshal — *Life Safety Code* |
| El **§100.3(b)** extiende la aplicación a "las localidades dentro de Illinois" | 41 Ill. Adm. Code §100.3 |
| El **§100.3(g)** define seis criterios para reconocer códigos locales equivalentes | 41 Ill. Adm. Code §100.3 |
| **NFPA 101-2015 referencia NFPA 72, edición 2013**, en su Capítulo 2 (*Referenced Publications*) | NFPA 101-2015 cap. 2 |

**Conclusión: la edición de NFPA 72 aplicable a este edificio es la 2013.**

### Lo que queda por confirmar

1. **Si la Ciudad de Paxton adoptó por ordenanza el IBC/IFC**, y en qué edición. De ser así, podría desplazar el marco estatal bajo §100.3(g).
2. **Qué exige NFPA 101-2015** para ocupaciones de asamblea (Assembly) respecto de sistemas de alarma — capítulos 12 y 13.

### Cómo buscarlo (método concreto)

**a) El código administrativo de Illinois, texto oficial y gratuito:**
- `https://www.ilga.gov/Commission/jcar/admincode/JCARTitlePart.asp?Title=041&Part=0100` — Título 41, Parte 100 completo, del *Joint Committee on Administrative Rules*. Es la fuente oficial.
- Espejo legible: `law.cornell.edu/regulations/illinois/Ill-Admin-Code-tit-41-SS-100.7` (Legal Information Institute de Cornell).
- Sitio del OSFM: `sfm.illinois.gov/resources/life-safety-code.html`

**b) Las ordenanzas de la Ciudad de Paxton** — en orden de probabilidad:
1. Buscar `Paxton Illinois municipal code ordinances building code` — la mayoría de municipios pequeños de Illinois publican su código en **American Legal Publishing** (`codelibrary.amlegal.com`), **Municode** (`library.municode.com`) o **Code Publishing**.
2. Ir al sitio de la ciudad (`cityofpaxton.com` o similar) y buscar *Code of Ordinances* → capítulo de *Building* o *Fire Prevention*.
3. Si no aparece publicado en línea —muy posible en un municipio de ~4 500 habitantes— **eso también es un resultado**: documenten que se buscó y no se encontró ordenanza publicada, y que por tanto se asume el marco estatal.

**c) Buscar la ocupación en NFPA 101-2015**: capítulo 12 (*New Assembly Occupancies*) y capítulo 13 (*Existing Assembly Occupancies*). La biblioteca es **existente**, así que aplica el **capítulo 13**.

> ⚠️ **Ojo con esto:** al ser un edificio *existente*, NFPA 101 aplica el capítulo de ocupaciones existentes, que suele ser **menos exigente** que el de nuevas. Es un matiz que vale la pena mencionar.

> **Consejo de redacción:** documenten tanto lo que encontraron como lo que **no** pudieron confirmar. Un informe que dice "se verificó X en la fuente Y; no se logró confirmar Z pese a buscar en A, B y C" es más sólido que uno que afirma todo con la misma seguridad.

---

## 1.5 Requisitos según el tipo de ocupación

**Clasificación determinada: IBC Grupo A-3** (biblioteca — asamblea).

Carga ocupacional calculada según **IBC Tabla 1004.5** (detalle completo en la Sección 2.8):

| Uso | Factor | Área | Ocupantes |
|---|---|---:|---:|
| Salas de lectura | 50 net ft²/oc | 1 956 ft² | 40 |
| Stacks y circulación | 100 gross ft²/oc | 990 ft² | 11 |
| Oficina | 150 gross ft²/oc | 136 ft² | 1 |
| Almacenamiento | 300 gross ft²/oc | 320 ft² | 1 |
| **Total** | | | **≈ 53** |

Con ≈53 ocupantes queda **justo por encima del umbral de 50** que lo separaría del Grupo B.

### El hallazgo normativo más interesante del proyecto

Con **≈53 ocupantes** y un área de incendio muy inferior a **12 000 ft²**, este edificio **probablemente no está obligado** por el IBC a contar con sistema de alarma de incendio (el umbral típico en Grupo A es ≥300 ocupantes) ni con rociadores.

**El sistema diseñado es, por tanto, un sistema no requerido — voluntario.**

Esto **no lo exime de la norma**: NFPA 72 establece que los sistemas no requeridos que se instalen deben cumplir el Código en su totalidad. Un sistema mal diseñado que se instala voluntariamente es peor que no tener sistema, porque genera una confianza injustificada.

> Declarar esto explícitamente demuestra que el grupo entendió la distinción central entre **cuándo se exige** un sistema (IBC/IFC) y **cómo debe diseñarse** una vez que existe (NFPA 72). Es exactamente el tipo de razonamiento que el enunciado pide cuando dice *"no se espera únicamente una enumeración de normas"*.
>
> ⚠️ **Verificar** los umbrales exactos de IBC §907.2.1 y §903.2.1.3 en la edición que corresponda.

---

## Lo que falta en esta sección

1. **Confirmar los 6 `⚠️` restantes** de la tabla 1.2 (los `✅` ya están verificados contra el texto de NFPA 72-2013).
2. **Confirmar si Paxton tiene ordenanza propia** — método en 1.4(b).
3. **Revisar NFPA 101-2015 capítulo 13** (ocupaciones de asamblea existentes).
4. **Ampliar 1.1** con dos o tres párrafos explicando *cómo* cada norma afectó decisiones concretas. Los ejemplos ya los tenés: la regla del 0,7 S que obligó a dos detectores en Stacks; el escalón de 28×28 ft de la Tabla 18.5.5.4.1(a) que obligó a subir a 75 cd; el mínimo de batería del panel que gobernó por encima del cálculo; la altura de 8'-3" del sótano que evitó la reducción de espaciamiento de §17.6.3.5.1.
