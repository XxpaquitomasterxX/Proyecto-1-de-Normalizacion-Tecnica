# Cronograma de trabajo — Proyecto 1 (3 personas)
### Sistema de Detección y Alarma Contra Incendios · EL-4601

**Equipo:** Walter · Thomas · Sebas
**Inicio:** sábado 22 de agosto · **Meta interna:** miércoles 2 de septiembre · **Entrega oficial:** miércoles 9 de septiembre (colchón de 1 semana)

---

## Reparto general (carga equilibrada)

Cada quien lidera **una columna** del proyecto de punta a punta, y las tareas conjuntas se dividen en 3.

| | **Walter** | **Thomas** | **Sebas** |
|---|---|---|---|
| **Eje principal** | Normas (Sec. 1) + Cálculos eléctricos (Sec. 5c) | Edificio (Sec. 2) + Planos/Diseño (Sec. 4) | Equipos (Sec. 3) + BOM y Análisis (Sec. 5d, 6) |
| **Cierre** | Conclusiones (Sec. 7) | Diagrama de interconexión (Sec. 5.2) | Resumen ejecutivo |
| **Compartido** | Referencias + Anexo de prompts (c/u agrega los suyos) · Presentación (c/u expone su eje) |

> Los 3 alimentan el **cuaderno de NotebookLM** y guardan **sus prompts** en el Doc "Prompts de IA".

---

## Fase 0 — Arranque conjunto · Sáb 22 – Dom 23 ago
*Todos juntos. Estas decisiones condicionan TODO lo demás, así que se toman en equipo.*

- [ ] **Los 3:** configurar Claude + MCP de NotebookLM y autenticarse (ver `GUIA_Trabajo_con_Claude.md`).
- [ ] **Los 3:** montar la carpeta compartida de Google Drive + subir plantilla, guía y CSVs.
- [ ] **DECISIÓN 1 — Edificio:** elegir el edificio real en EE.UU. con planos públicos (Thomas propone 2-3 opciones, votan). *Define ocupación y normas.*
- [ ] **DECISIÓN 2 — Fabricante:** elegir la familia principal (Notifier / EST / Simplex…). *Sebas propone, votan.*
- [ ] **DECISIÓN 3 — Arquitectura:** convencional vs direccionable (según tamaño del edificio).

**Hito Dom 23:** edificio, fabricante y arquitectura definidos. Sin esto no arranca la Fase 1.

---

## Fase 1 — Investigación en paralelo · Lun 24 – Mié 26 ago
*Cada quien en su eje, en paralelo.*

**Walter — Normas (Sec. 1)**
- [ ] Subir NFPA 72, NEC, IBC, IFC al cuaderno de NotebookLM.
- [ ] Resumir requisitos por dispositivo (tabla 1.2) con sección exacta.
- [ ] Investigar la AHJ de la ciudad y qué ediciones aplican en ese estado.

**Thomas — Edificio (Sec. 2)**
- [ ] Conseguir y descargar los planos arquitectónicos del edificio.
- [ ] Documentar: ubicación, pisos, áreas, dimensiones, pasillos, cuartos de servicio.
- [ ] Clasificar la ocupación según IBC.

**Sebas — Equipos (Sec. 3)**
- [ ] Seleccionar panel (FACP) + detectores + pull stations + horn/strobes compatibles.
- [ ] Descargar datasheets → carpeta Drive/Datasheets.
- [ ] Empezar a llenar la BOM (fabricante, modelo, V, I standby, I alarma).

**Hito Mié 26:** Secciones 1, 2 y 3 en borrador + datasheets con datos eléctricos listos.

---

## Fase 2 — Diseño y cálculos · Jue 27 – Sáb 29 ago
*Aquí se usan los resultados de la Fase 1.*

**Thomas — Diseño sobre planos (Sec. 4)** *(usa normas de Walter + equipos de Sebas)*
- [ ] Importar el plano a draw.io; crear leyenda de símbolos.
- [ ] Ubicar cada dispositivo justificando con la norma (espaciamiento, salidas, cobertura).
- [ ] Trazar circuitos SLC/NAC y cableado; conexión entre pisos.

**Walter — Cálculos eléctricos (Sec. 5c)** *(usa la BOM de Sebas)*
- [ ] Corriente total standby y alarma (hojas 2 y 3 del Sheet).
- [ ] Caída de tensión en cada NAC (hoja 4) — verificar voltaje mínimo.
- [ ] Dimensionar baterías + verificar capacidad de NAC y lazo (hoja 5).

**Sebas — BOM final + Análisis (Sec. 5.4 y 6)**
- [ ] Cerrar la BOM y el Device Schedule con cantidades finales del diseño de Thomas.
- [ ] Redactar el análisis: convencional vs direccionable, ventajas/desventajas, cumplimiento, mantenimiento.

**Hito Sáb 29:** planos con dispositivos + cálculos verificados + BOM completa.

---

## Fase 3 — Integración · Dom 30 – Lun 31 ago
*Unir todo en el Google Doc.*

- [ ] **Thomas:** diagrama de interconexión general (riser) en draw.io (Sec. 5.2).
- [ ] **Walter:** conclusiones (Sec. 7) — normas de mayor influencia, dificultades.
- [ ] **Sebas:** resumen ejecutivo + revisar coherencia de la BOM con el diseño.
- [ ] **Los 3:** pegar cada sección en el documento; unificar nomenclatura de dispositivos.

**Hito Lun 31:** documento completo de la Sec. 1 a la 8 (aún sin pulir).

---

## Fase 4 — Revisión y cierre · Mar 1 – Mié 2 sep
- [ ] **Los 3:** revisión cruzada (cada quien revisa el eje de otro, no el propio).
- [ ] Verificar que **cada decisión tenga su cita de norma**.
- [ ] Completar **Referencias** (todos) y **Anexo A de prompts de IA** (cada quien pega los suyos).
- [ ] Revisar formato, numeración de figuras, leyendas de planos.
- [ ] Exportar el documento a PDF.

**Hito Mié 2 sep:** 📦 documento LISTO (queda 1 semana de colchón).

---

## Semana de colchón · 3 – 8 sep
- [ ] Pulir detalles, correcciones de última hora.
- [ ] **Preparar presentación oral:** cada quien expone su eje (Walter=normas+cálculos, Thomas=edificio+diseño, Sebas=equipos+análisis).
- [ ] Ensayo general.

**📅 Entrega documento: mié 9 sep · Presentación: vie 11 y mié 16 sep.**

---

## Resumen de responsabilidades por persona

**Walter:** Sec. 1 (Normas) → Cálculos eléctricos (5c) → Conclusiones (7). Sube las NFPA al cuaderno.
**Thomas:** Sec. 2 (Edificio) → Diseño en draw.io (4) → Diagrama de interconexión (5.2). Dueño de los planos.
**Sebas:** Sec. 3 (Equipos) → BOM/Device Schedule (5.4) → Análisis (6) + Resumen ejecutivo. Dueño de los datasheets.
**Los 3:** decisiones de Fase 0, referencias, anexo de prompts, revisión cruzada y presentación.
