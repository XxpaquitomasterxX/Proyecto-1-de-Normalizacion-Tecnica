# Guía de trabajo con Claude + NotebookLM (para los 4 integrantes)
### Proyecto 1 — Sistema de Detección y Alarma Contra Incendios

Esta guía es para que **cada integrante** trabaje su parte usando su **propio Claude** y el
**cuaderno de NotebookLM compartido**. Léanla completa una vez.

---

## 🔧 Parte 0 — Configuración única (cada quien en su máquina)

Cada integrante debe hacer esto UNA vez en su computadora:

1. **Instalar Node.js** (si no lo tienen). En Linux/Mac, lo más limpio es `nvm`:
   ```bash
   curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
   # cierra y reabre la terminal, luego:
   nvm install --lts
   ```
2. **Agregar el servidor MCP de NotebookLM a Claude Code:**
   ```bash
   claude mcp add notebooklm -s user -- npx notebooklm-mcp@latest
   ```
   *(Si usan nvm, usen la ruta completa de npx: `which npx` para obtenerla.)*
3. **Reiniciar Claude Code** para que carguen las herramientas.
4. Pedirle a Claude: **"autentícame en NotebookLM"** → se abre Chrome, inician sesión con
   **su propia cuenta de Google** (la que tiene acceso al cuaderno compartido).

> El dueño del cuaderno (Wally) debe **compartir el cuaderno de NotebookLM** con los correos
> de los otros 3 desde la interfaz de NotebookLM antes de este paso.

---

## 📌 Reglas de oro para todos

1. **Guarden CADA prompt** que le den a Claude o NotebookLM → péguenlo en el Google Doc
   "Prompts de IA" (columna: quién, herramienta, para qué, prompt). Es **obligatorio** entregarlos.
2. **Verifiquen todo.** La IA puede equivocarse en números de norma. Siempre confirmen con la
   cita real que da NotebookLM (que sí apunta a la fuente).
3. **Citen la sección exacta** de la norma en cada decisión (ej. "NFPA 72 §17.7.3").
4. Trabajen sobre la **carpeta compartida de Google Drive**, no en archivos locales sueltos.
5. Un solo **fabricante principal** para todo el sistema — pónganse de acuerdo antes de comprar/elegir.

---

## 👤 Persona 1 — Investigación normativa (Sección 1)

**Objetivo:** resumir NFPA 72, NEC, IBC, IFC y explicar cómo afectan el diseño.

**Con NotebookLM (tu mejor herramienta):** sube los PDFs de las normas al cuaderno y pregunta.
Ejemplos de prompts:
- "Según NFPA 72, ¿cuáles son los requisitos de espaciamiento y ubicación para detectores de humo puntuales? Dame las secciones exactas."
- "¿Qué exige NFPA 72 sobre el nivel sonoro mínimo de los dispositivos de notificación audible?"
- "¿Qué intensidad en candelas (cd) requieren los strobes según el área de la sala? Cítame la tabla."
- "¿Cuánto tiempo de respaldo por batería exige NFPA 72 (standby y alarma)?"
- "¿Qué es la AHJ y qué rol tiene en la aprobación del sistema?"

**Con Claude (esta sesión):** pídele que organice tus hallazgos en la tabla de la sección 1.2 de
la plantilla, o que te explique un concepto que no entiendas.

**Entregable:** Sección 1 del documento + fuentes en Referencias.

---

## 👤 Persona 2 — Selección y análisis del edificio (Sección 2)

**Objetivo:** elegir un edificio real en EE.UU. con planos públicos y describirlo.

**Con Claude:**
- "Ayúdame a encontrar edificios en EE.UU. cuyos planos arquitectónicos sean de acceso público
  (bibliotecas, escuelas, edificios municipales). Dame opciones y dónde buscar los planos."
- "Este edificio está en [ciudad, estado]. ¿Qué clasificación de ocupación tiene según el IBC?"
- Sube el plano y pídele: "Describe la distribución, pisos, pasillos y cuartos de servicio de
  este plano."

**Tips:** busquen planos en sitios de gobierno local, permisos de construcción, o
proyectos universitarios públicos. El plano debe tener escala/dimensiones.

**Entregable:** Sección 2 + los planos originales en Drive/Planos.

---

## 👤 Persona 3 — Selección de equipos (Sección 3)

**Objetivo:** elegir UNA familia compatible (panel + dispositivos) de un fabricante real.

**Con Claude:**
- "Compara familias de sistemas de alarma contra incendios (Notifier, EST/Edwards, Simplex,
  Bosch) para un edificio de [X] pisos. ¿Cuál conviene y por qué?"
- "Para el panel [modelo], ¿qué detectores, pull stations y horn/strobes son compatibles?
  Dame modelos reales."
- "Extrae de este datasheet: voltaje, corriente en standby, corriente en alarma y tipo de conexión."
  *(sube el datasheet PDF)*

**Con NotebookLM:** sube los datasheets al cuaderno y pregunta por características eléctricas
con cita a la página.

**Entregable:** Sección 3 (tabla de dispositivos) + datasheets en Drive/Datasheets.

---

## 👤 Persona 4 — Diseño, cálculos y planos (Secciones 4 y 5)

**Objetivo:** ubicar dispositivos en draw.io y hacer los cálculos eléctricos.

**Planos (draw.io / diagrams.net):**
1. Importa el plano arquitectónico como imagen de fondo.
2. Coloca símbolos por dispositivo (crea una leyenda clara y consistente).
3. Dibuja el recorrido del cableado y los circuitos (SLC/NAC).
4. Guarda en Drive/Planos.

**Cálculos con Claude:**
- "Tengo estos dispositivos con estas corrientes [pega la tabla]. Calcula la corriente total en
  standby y en alarma."
- "Calcula la caída de tensión en este NAC: longitud [X] m, corriente [Y] A, calibre [Z] AWG.
  ¿El último dispositivo recibe el voltaje mínimo de [V] V? Muestra la fórmula."
- "Dimensiona la batería de respaldo para 24 h standby + 5 min en alarma con estas corrientes."

> ⚠️ **Verifiquen los cálculos a mano.** Claude ayuda con el método, pero un error de decimales
> en caída de tensión invalida el diseño. Confirmen las fórmulas.

**Entregable:** Secciones 4 y 5 + planos draw.io + cálculos + BOM en el Google Sheet.

---

## 📅 Ritmo sugerido (entrega: mié 9 de septiembre)

| Semana | Meta |
|---|---|
| **Ahora – 27 ago** | Config de todos + Persona 1 avanza normas + Persona 2 elige edificio |
| **28 ago – 2 sep** | Persona 3 cierra equipos (familia compatible) + Persona 4 empieza draw.io |
| **3 – 6 sep** | Cálculos, diseño final sobre planos, unir todo en el Google Doc |
| **7 – 8 sep** | Revisión conjunta, referencias, anexo de prompts, formato |
| **9 sep** | 📤 Entrega del documento |
| **11 y 16 sep** | Presentación oral (repartir quién explica qué) |

---

## 🆘 Si algo falla en la configuración
- **"npx: command not found"** → Node no está en el PATH. Usen la ruta completa: `which npx`.
- **El servidor MCP no conecta** → `claude mcp list` para ver el estado; reinicien Claude.
- **Chrome no abre en `setup_auth`** → necesitan entorno gráfico (no funciona en servidor sin
  pantalla / WSL1).
- **No veo el cuaderno compartido** → confirmen que el dueño compartió con SU correo exacto.
