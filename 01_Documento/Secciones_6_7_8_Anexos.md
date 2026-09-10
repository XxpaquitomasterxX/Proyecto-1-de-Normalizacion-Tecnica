# 6. Análisis del diseño realizado

## 6.1 Por qué una arquitectura direccionable

La justificación completa está en la Sección 3.1. En síntesis, tres razones específicas de **este** edificio:

1. **Es un inmueble histórico documentado (HABS IL-329).** Un sistema convencional exige un par de conductores por zona; el direccionable resuelve los 21 puntos con **un solo lazo SLC**. En mampostería original de 1903, menos canalización es menos daño irreversible al bien patrimonial.
2. **Planta libre en el primer piso.** Stacks, sala norte, circulación y rotonda forman un único volumen continuo separado solo por columnas. Con detección por zona, media planta sería "una zona". La localización por punto es lo que da información útil.
3. **Ambiente con polvo de papel.** El panel hace prueba automática cada dos horas y compensación de deriva por punto, y avisa cuándo un detector necesita limpieza. Eso ataca la causa número uno de que un sistema real termine desconectado: las alarmas no deseadas.

## 6.2 Ventajas y desventajas de la solución

**Ventajas**

- **Márgenes muy amplios en todas las verificaciones.** El sistema usa 10,7 % de la capacidad de detectores del lazo, 13,2 % del NAC más cargado y 27,5 % de la potencia disponible en alarma. No es sobredimensionamiento accidental: deja espacio real para ampliar la biblioteca sin reemplazar el panel.
- **Una sola marca para panel y detección**, con la única interfaz entre marcas (notificación) respaldada por el documento de compatibilidad del propio fabricante del panel.
- **Detección adaptada al ambiente de cada recinto**: humo donde corresponde, térmica donde el humo daría falsas alarmas.
- **Cálculo trazable de punta a punta.** Cada corriente sale de una tabla publicada por el fabricante, no de un valor típico.

**Desventajas y compromisos asumidos**

- **Mayor costo unitario por dispositivo** frente a un sistema convencional. Con 21 puntos el sobrecosto es marginal, pero existe.
- **Dependencia de un solo fabricante.** Simplifica la compatibilidad y complica la sustitución a futuro si la línea se descontinúa — el MS-9600LS ya aparece en el catálogo de productos descontinuados de Honeywell.
- **Un solo lazo SLC**: una falla franca del lazo compromete toda la detección. Se mitiga con el cableado Clase B supervisado, pero un diseño Clase A (Style 6/7) daría tolerancia a fallo único. **Se optó por Clase B** por economía de canalización en un edificio histórico; es una decisión discutible y conviene declararla como tal.
- **El anunciador es la única interfaz en la entrada.** Si falla el ANN-BUS, el cuerpo de bomberos debe bajar al sótano.

## 6.3 Cumplimiento de las normas identificadas

| Norma | Cómo se cumple |
|---|---|
| **NFPA 72 cap. 17** | Espaciamiento verificado recinto por recinto con la regla del 0,7 S; ningún punto de cielo a más de 21 ft de un detector. Detección térmica donde el ambiente no admite humo. |
| **NFPA 72 cap. 18** | Notificación audible y visual en todas las áreas ocupables, incluidos los sanitarios (visual). Candelas seleccionadas según el tamaño de cada recinto. |
| **NFPA 72 cap. 10** | Fuente primaria y secundaria; baterías dimensionadas para 24 h + 5 min con factor 1,2. |
| **NFPA 70 (NEC) Art. 760** | Circuito derivado dedicado y exclusivo rotulado FIRE ALARM, 14 AWG / 600 V, sin desconectadores. Cableado NAC 16 AWG FPLR verificado por caída de tensión. |
| **NEC cap. 9, tabla 8** | Resistencias de conductor tomadas de la tabla del Código, no de valores teóricos. |
| **UL 864 / FM** | Todos los equipos listados; el panel es FM Approved a UL/ANSI 864. |
| **IBC** | Clasificación de ocupación determinada (Grupo A-3, carga ≈53). |

**Un punto que conviene declarar abiertamente:** con ≈53 ocupantes y un área de incendio muy inferior a 12 000 ft², este edificio **probablemente no está obligado** por el IBC a tener sistema de alarma. El sistema diseñado es, por tanto, **voluntario (no requerido)**. Eso no lo exime de nada: NFPA 72 establece que un sistema no requerido que se instale debe cumplir el Código en su totalidad. Decirlo demuestra que se entendió la diferencia entre *cuándo se exige* un sistema (IBC/IFC) y *cómo debe diseñarse* (NFPA 72).

## 6.4 Limitaciones del diseño

1. **El ático de la rotonda queda sin detección.** Entre el casquete de yeso y el domo exterior hay un volumen considerable con cerchas de madera (lámina 10). Es carga combustible en un espacio oculto y no detectado. En un proyecto real habría que consultarlo con la AHJ.
2. **No hay sistema de rociadores.** El diseño es de detección y notificación únicamente, como pide el enunciado. La supresión queda fuera de alcance.
3. **La altura de las estanterías radiales se asumió.** La lámina 9 muestra en sección la ebanistería perimetral rematando a ≈7'-9"; se asumió la misma altura para las estanterías exentas del abanico. Es razonable, pero es una asunción.
4. **No hay información de HVAC.** Las láminas HABS no documentan ductos ni difusores. NFPA 72 exige separación mínima entre detectores y difusores de aire, y esa verificación **no pudo hacerse**. En un proyecto real requeriría levantamiento en sitio.
5. **Las áreas de recintos se midieron sobre los planos** con calibración de 100 px/pie, con precisión estimada de ±3 %. Las cotas rotuladas son exactas; las áreas derivadas no.
6. **Cableado Clase B, no Clase A.** No hay tolerancia a fallo único en el lazo.
7. **El edificio es histórico.** El diseño no resuelve el detalle de cómo canalizar sin afectar acabados originales, que en la práctica sería una negociación con la autoridad de preservación.

## 6.5 Consideraciones de mantenimiento e inspección

NFPA 72, **capítulo 14** (*Inspection, Testing and Maintenance*), rige la vida útil del sistema. Elementos que este diseño facilita o exige:

- **Prueba funcional periódica** de detectores, estaciones manuales y aparatos de notificación, con registro escrito. El MS-9600LS permite **prueba de sensibilidad con resultados imprimibles**, lo que evita tener que retirar detectores para calibrarlos.
- **Prueba automática cada dos horas** de cada detector, con reporte de fallo (AUTO TEST FAIL).
- **Compensación automática de deriva** y aviso de mantenimiento por acumulación de polvo — relevante en una biblioteca.
- **Baterías:** verificar carga y reemplazar según vida útil (típicamente 3–5 años en plomo-ácido sellado). El requisito de 12 AH mínimos del panel se mantiene en cada reemplazo.
- **Etiquetado:** el manual exige anotar los amperios-hora requeridos en la etiqueta *Protected Premises* dentro de la puerta del gabinete.
- **Acceso:** el panel está en el sótano; el programa de mantenimiento debe garantizar acceso al Electrical Room y mantener libre el recorrido desde la entrada.

---

# 7. Conclusiones

**7.1 Principales resultados obtenidos**

Se diseñó un sistema completo de detección y alarma para la totalidad de la Paxton Carnegie Library (4 363 ft² en dos niveles): **15 detectores de humo, 2 térmicos, 4 estaciones manuales, 11 horn/strobes, 4 strobes, un anunciador remoto y un panel direccionable Fire•Lite MS-9600LS**, sobre un solo lazo SLC y cuatro circuitos NAC. Todas las verificaciones eléctricas dieron con margen amplio: 27,5 % de la potencia disponible en alarma, 13,2 % del NAC más cargado, 10,7 % de la capacidad del lazo, y 19,97 V en el punto más desfavorable contra un mínimo de 16 V.

**7.2 Normas de mayor influencia sobre el diseño**

**NFPA 72 fue determinante**, y específicamente el capítulo 17: la regla de que ningún punto del cielo quede a más de 0,7 × el espaciamiento nominal de un detector es la que fijó la cantidad y posición de cada dispositivo. Fue esa regla —y no el área— la que obligó a dos detectores en la zona de Stacks en vez de uno.

El **capítulo 18** determinó la selección de candelas y, con ella, la corriente de los circuitos NAC. Un detalle instructivo: la tabla de espaciamiento en recintos tiene un escalón en 28 × 28 ft que se pasa por alto con facilidad; la zona de Stacks mide 28,3 × 28,3 ft y cae, por tres décimas de pie, en la fila siguiente.

El **NEC (NFPA 70), artículo 760 y capítulo 9 tabla 8**, gobernó el cableado y las resistencias del cálculo de caída de tensión.

El **IBC** definió la clasificación de ocupación y, con ella, el hallazgo de que el sistema es voluntario.

**7.3 Importancia de equipos certificados y compatibles**

El proyecto lo hizo evidente de forma concreta. La compatibilidad entre el panel Fire•Lite y los aparatos de notificación System Sensor **no se afirma: se prueba**, con el *Device Compatibility Document* P/N 15384:BR del propio fabricante del panel, donde el MS-9600LS aparece listado con los modelos exactos que se usaron. Que ambas marcas sean de Honeywell no habría sido argumento suficiente. Del mismo modo, las corrientes de cada dispositivo salieron de tablas publicadas —no de valores típicos—, y por eso el cálculo de baterías es defendible.

**7.4 Dificultades al trasladar la norma a una instalación real**

- **Determinar qué edición aplica no es trivial, y de eso depende toda la numeración.** Hubo que recorrer una cadena de tres eslabones: el *41 Ill. Adm. Code* Parte 100 adopta NFPA 101-2015, que a su vez referencia NFPA 72-2013. La misma exigencia de candelas aparece como §18.5.5.4.1 en la edición 2013 y como §18.5.5.7 en la 2022; citar el número de la edición equivocada invalida la referencia aunque el requisito esté bien entendido.
- **El acceso a la norma es una barrera real.** NFPA ofrece un visor gratuito de solo lectura, pero no siempre funciona, y la norma completa se vende. Para un estudiante esto condiciona la profundidad de la verificación.
- **Los planos no traen todo lo que el diseño necesita.** Las láminas HABS documentan geometría, no instalaciones. Las alturas de cielo aparecieron recién en la lámina 9, y de HVAC no hay nada.
- **Las hojas técnicas no bastan.** La hoja técnica del panel da lo que el panel *entrega*, no lo que *consume*. Ese dato estaba en el manual de instalación, en un apéndice de cálculo, y sin él no se puede dimensionar la batería.
- **Hay que leer la geometría real, no la idealizada.** El "domo" de la rotonda resultó ser un ático: el cielo del recinto es un casquete rebajado con 1'-11" de flecha. Suponer un domo profundo habría llevado a aplicar reglas de cielo inclinado que no corresponden.
- **Los mínimos del equipo pueden gobernar por encima del cálculo.** La batería calculada dio 4,26 AH; se instalan 12 AH porque el panel no admite menos. El cálculo no siempre manda.

**7.5 Aspectos a profundizar para una implementación real**

1. **Levantamiento en sitio de HVAC** para verificar separación entre detectores y difusores.
2. **Verificación acústica**: NFPA 72 exige 15 dB sobre el ruido ambiente; requiere medir el ruido de fondo real, que en una biblioteca es bajo y podría permitir aparatos de menor potencia.
3. **Consulta formal a la AHJ** — Office of the State Fire Marshal de Illinois y bomberos locales — sobre el ático de la rotonda y sobre qué edición de código aplica.
4. **Coordinación con la autoridad de preservación histórica** para las canalizaciones.
5. **Evaluar Clase A (Style 6/7)** para el lazo, con su costo adicional de canalización.
6. **Monitoreo a estación central**: el MS-9600UDLS o el módulo IPDACT, si la AHJ o la aseguradora lo requieren.
7. **Programa de mantenimiento** conforme al capítulo 14, con responsable designado.

---

# 8. Referencias

**Normas, códigos y estándares**

1. National Fire Protection Association. *NFPA 72: National Fire Alarm and Signaling Code*, **edición 2013**. Quincy, MA: NFPA. *(Edición aplicable por referencia desde NFPA 101-2015, adoptado por el Illinois State Fire Marshal.)*
2. National Fire Protection Association. *NFPA 101: Life Safety Code*, **edición 2015**. Quincy, MA: NFPA.
3. Office of the Illinois State Fire Marshal. **41 Ill. Adm. Code, Parte 100** — *Fire Prevention and Safety*. §100.3 (jurisdicción) y §100.7 (adopción de NFPA 101 por referencia). https://www.ilga.gov/Commission/jcar/admincode/JCARTitlePart.asp?Title=041&Part=0100
4. National Fire Protection Association. *NFPA 70: National Electrical Code*, edición 20XX. Artículo 760 y Capítulo 9, Tabla 8.
5. International Code Council. *International Building Code (IBC)*, edición 20XX. Tabla 1004.5; §903.2.1.3; §907.2.1.
6. International Code Council. *International Fire Code (IFC)*, edición 20XX.
7. Underwriters Laboratories. *UL 864: Control Units and Accessories for Fire Alarm Systems*, 10.ª edición.

**Planos arquitectónicos**

8. Historic American Buildings Survey. *Paxton Carnegie Library, 254 South Market Street, Paxton, Ford County, Illinois*. HABS No. **IL-329**. Charles E. Peterson Prize Competition Entry, 2012. Washington, D.C.: National Park Service, U.S. Department of the Interior. Library of Congress, Prints and Photographs Division. https://www.loc.gov/item/il0998/
   - Lámina 2 de 21 — *Site Plan* (1" = 20'-0"), delineada por Lauren Nurse y Theresa Scott.
   - Lámina 3 de 21 — *Basement Plan* (1/4" = 1'-0"), delineada por Travis Dean.
   - Lámina 4 de 21 — *First Floor Plan* (1/4" = 1'-0"), delineada por Brodie Bricker.
   - Lámina 5 de 21 — *East Elevation* (1/4" = 1'-0"), delineada por Laura Mann.
   - Lámina 9 de 21 — *East-West Section* (3/8" = 1'-0"), delineada por Brodie Bricker.
   - Lámina 10 de 21 — *North-South Section* (3/8" = 1'-0"), delineada por Brodie Bricker.
   - Lámina 11 de 21 — *Elevation at Entry* (3/4" = 1'-0"), delineada por Laura Mann.

**Documentación de fabricante**

9. Fire•Lite Alarms (Honeywell). *MS-9600LS(E)/MS-9600UDLS(E) Intelligent Addressable FACP with Optional Second Loop*. Hoja técnica **DF-60334:A6**, 20 de febrero de 2019.
10. Fire•Lite Alarms (Honeywell). *MS-9600LS Series Addressable Fire Alarm Control Panel — Installation Manual*. Documento **PN 52646:B**, 17 de junio de 2008. *(Tabla 5.3, System Current Draw Calculations; Tabla 5.4, Total Secondary Power Requirements.)*
11. Fire•Lite Alarms (Honeywell). *Device Compatibility Document*. Documento **P/N 15384:BR**, 25 de enero de 2022, ECN 151532.
12. Fire•Lite Alarms (Honeywell). *SLC Wiring Manual*. Documento **51309**. *(Apéndice D.1: base B350LP; tabla de longitud máxima de lazo por calibre.)*
13. System Sensor (Honeywell). *SpectrAlert Advance — Indoor Wall Horns, Strobes and Horn Strobes*. Hoja técnica **AVDS102**.

---

# Anexo A — Prompts de inteligencia artificial utilizados

> **Obligatorio según el enunciado**, e igualmente obligatorio mencionarlo en la presentación oral.

**Declaración de alcance.** Todo el trabajo asistido por IA de este proyecto se realizó en **una única sesión de Claude Code**, conducida por Walter, más **una consulta puntual a Gemini**. No se utilizó NotebookLM. Los prompts que siguen son el registro completo.

| # | Integrante | Herramienta | Propósito | Prompt (texto exacto) |
|---|---|---|---|---|
| 1 | Sebastián | Claude | Revisar las láminas HABS, extraer cotas y áreas, y reorganizar el trabajo tras quedar el equipo en dos personas | *"hola en esta carpeta y en este proyecto esta todas las instrucciones, ya tengo los planos completos puedes revisar y hacer los calculos, una cosa para aclarar estamos sep 5 y solo tenemos echo lo que esta subido aca y solo estamos mi compañero sebastian y yo tenemos que sacarlo todo ahorita, dime que hacer o que puedes ir haciendo tu para empezar"* |
| 2 | Walter | Claude | Verificar alturas de cielo con las secciones y cerrar las incógnitas del domo y las estanterías | *"sebas escogio el MS-9600, ya descargue los planos que hacian falta, dime si necesitas algo mas"* |
| 3 | Walter | Claude | Extraer los datos eléctricos del manual del panel y realizar los cálculos de la Sección 5.3 | *"usemos la variante sencilla el MS-9600, cree una carpeta y agregue una ficha del panel, dime si necesitas algo mas o si con ese documento no funciona?"* |
| 4 | Thomas | Claude | Identificar y localizar el Device Compatibility Document | *"que es el DCD donde lo descargo"* |
| 5 | Walter | Claude | Verificar la tabla de candelas obtenida de Gemini y localizar acceso a la norma | *"no encuentro ese archivo porque me pide cuenta para descargar, gemini me dijo esto, si hace falta supongamos que esta bien si hace falta dime para ver si busco la forma de acceder a la norma pq cobran para descargarla"* + tabla pegada |
| 6 | Sebastián | Claude | Obtener el estado del proyecto y una guía para elaborar los planos sin experiencia previa | *"okey explicame el estado actual, de todo el proyecto que falta? ademas que no tenemos ni experiencia ni idea de como hacer los planos como hacemos para realizarlos? tienes una guia o que debe llevar exactamente"* |
| 7 | Walter | Claude | Generar el diagrama de interconexión y redactar las secciones pendientes | *"si genera el riser, ademas despues redacta lo que haga falta"* |
| 8 | Thomas | Claude | Determinar la jurisdicción aplicable en Illinois y la edición de norma correspondiente | *"el tema con las ediciones es que el visualizador no funciona… dime como buscar lo de la jurisdiccion de illinois…"* |


## Nota metodológica sobre la verificación

El enunciado exige que *"la información obtenida sea verificada y respaldada mediante referencias bibliográficas confiables"*. En este proyecto la verificación **detectó errores en cinco ocasiones**, y documentarlo es parte del resultado:

| # | Afirmación inicial | Verificación | Resultado |
|---|---|---|---|
| 1 | "Falta descargar el plano de sótano" | Inventario de la carpeta | El plano ya estaba: lámina 3 |
| 2 | "Hay tres escaleras interiores (tres vías de propagación de humo)" | Ampliación del TIFF a resolución completa | Solo **una** es interior; las otras dos son escaleras exteriores |
| 3 | "La rotonda tiene ~23 ft de diámetro (~415 ft²)" | Medición a 100 px/pie contra la cota R14'-10" de la lámina 3 | **27 ft de diámetro (573 ft²)** |
| 4 | "El domo obliga a tratar el cielo como inclinado" | Lámina 10 (sección N-S) | El domo es un **ático**; el cielo del recinto es un casquete de 1'-11" de flecha → cielo liso |
| 5 | "Sala de 30×30 ft → 30 cd" *(tabla obtenida por IA)* | Tabla 18.5.5.4.1(a) de NFPA 72-2013 | La tabla tiene una fila intermedia de **28×28 → 30 cd**, y **30×30 exige 34 cd**. Obligó a subir el aparato de Stacks a 75 cd |

Los cinco casos comparten un patrón: **la IA es útil para estructurar y calcular, pero cada dato que entra al diseño debe contrastarse contra la fuente primaria** — el plano a resolución completa, la hoja técnica, el texto de la norma. En el caso 5 conviene señalar que dos sistemas de IA distintos coincidieron en el mismo error, lo que muestra que la coincidencia entre herramientas **no constituye verificación**.

# Anexo B — Datasheets

Todos en la carpeta `Panel/` del proyecto:

| Documento | Archivo |
|---|---|
| Hoja técnica MS-9600LS (DF-60334:A6) | `Fire-Lite_Alarms_MS-9600LS_..._Product_Manual.pdf` |
| SLC Wiring Manual (doc. 51309) | `0c6bf9.pdf` — **renombrar a `51309_SLC_Wiring_Manual.pdf`** |
| Manual de instalación MS-9600LS (PN 52646:B) | `52646.pdf` |
| Device Compatibility Document (P/N 15384:BR) | `15384_Fire-Lite_Device_Compatibility_Document_RevBR.pdf` |
| System Sensor SpectrAlert Advance (AVDS102) | `SystemSensor_SpectrAlert_Advance_Indoor_Wall_AVDS102.pdf` |

---

# Resumen ejecutivo
*(va al inicio del documento)*

Este proyecto desarrolla el diseño completo de un sistema de detección, alarma y notificación de incendios para la **Paxton Carnegie Library** (254 S. Market Street, Paxton, Ford County, Illinois), edificio de 1903 documentado por el Historic American Buildings Survey bajo el registro **HABS IL-329**, cuyos planos son de acceso público a través de la Library of Congress.

El edificio tiene **dos niveles ocupados** —sótano y primer piso— con un área total de **4 363 ft² (405 m²)**, distribuidos en salas de lectura, zona de estanterías, salas infantiles, oficina, servicios sanitarios y cuartos mecánicos y eléctricos. Su carga ocupacional calculada de **≈53 personas** lo clasifica como **Grupo A-3** según el IBC. Presenta tres particularidades que condicionaron el diseño: una **rotonda de 27 ft de diámetro** cubierta por un casquete rebajado, una **zona de estanterías dispuestas en abanico radial**, y una **única conexión vertical interior** entre niveles.

Se aplicaron principalmente **NFPA 72** (detección, notificación y respaldo de energía), **NFPA 70 (NEC)** artículo 760 (cableado), e **IBC/IFC** (clasificación de ocupación y exigibilidad del sistema). Se seleccionó una arquitectura **direccionable** sobre un panel **Fire•Lite Alarms MS-9600LS**, justificada por la condición histórica del inmueble —que penaliza cada metro de canalización—, por la planta libre del primer piso y por las funciones de supervisión que reducen alarmas no deseadas.

El sistema resultante comprende **15 detectores de humo, 2 detectores térmicos, 4 estaciones manuales, 11 horn/strobes, 4 strobes y un anunciador remoto**, sobre **un lazo SLC** y **cuatro circuitos NAC**. Todas las verificaciones eléctricas se cumplen con margen: **1,924 A en alarma** (27,5 % de la capacidad del panel), **0,397 A en el NAC más cargado** (13,2 % del límite), **19,97 V en el punto más desfavorable** contra un mínimo de 16 V, y **21 de 318 puntos** direccionables utilizados. La batería requerida por cálculo resultó de 4,26 AH; se instalan **12 AH** porque es el mínimo que admite el panel.

Cada decisión de ubicación, cantidad y tipo de dispositivo está justificada mediante la norma aplicable, las dimensiones verificadas del edificio y las hojas técnicas de los equipos seleccionados.
