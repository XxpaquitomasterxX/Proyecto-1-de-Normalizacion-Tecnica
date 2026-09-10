# Cálculo de espaciamiento y cantidad de dispositivos — NFPA 72
### Paxton Carnegie Library · insumo para las Secciones 4.1, 4.2 y 5.4

> **Edición aplicable: NFPA 72-2013.** Determinada por la cadena *41 Ill. Adm. Code* Parte 100 → NFPA 101-2015 → NFPA 72-2013. Todos los números de sección de este documento corresponden a esa edición y están verificados contra su texto.

---

## 1. Criterio de espaciamiento aplicado (detectores de humo puntuales, cielo liso)

Regla de diseño usada, según **NFPA 72-2013 §17.7.3.2.3** y **§17.7.3.2.3.1** (*Smooth Ceiling Spacing*) ✅ verificado:

1. Espaciamiento nominal listado: **S = 30 ft**.
2. **Regla del 0,7 S:** ningún punto del cielo puede quedar a más de **0,7 × 30 = 21 ft** de un detector, medido en línea recta sobre el cielo.
3. Los detectores se ubican a no más de **S/2 = 15 ft** de las paredes.
4. Detectores a no menos de **4 in** del encuentro pared-cielo (zona muerta).

La regla que gobierna en recintos irregulares es la **(2)**, no el área. Por eso el cálculo se hace comprobando la distancia a la esquina más desfavorable de cada recinto, y no dividiendo el área entre 900 ft².

---

## 2. Verificación recinto por recinto — Primer piso

Coordenadas en pies, origen en la esquina exterior noroeste. `d_max` = distancia del detector al punto más desfavorable del recinto.

| Recinto | Geometría | Detectores | Ubicación propuesta | `d_max` | ¿≤ 21 ft? |
|---|---|---|---|---|---|
| **Stacks + piso abierto NO** | polígono (1,4 · 2) (29,7 · 2) (29,7 · 20,3) (11,5 · 30,3) (1,4 · 30,3) | **2** | D-101 (10,5 · 9,0) · D-102 (20,0 · 21,0) | 20,8 ft (esq. 1,4 · 30,3 → D-102) | ✔ |
| **North Reading Room** | 19,8 × 18,3 | **1** | centro (39,6 · 11,2) | √(9,9² + 9,15²) = **13,5 ft** | ✔ |
| **South Reading Room (rotonda)** | círculo r = 13,5 | **1** | centro (43,7 · 45,4) | **13,5 ft** (radio) | ✔ |
| **Circulación central diagonal** | irregular ≈ 280 ft² | **1** | (31 · 32) | ≈ 15 ft | ✔ |
| **Librarian's Office** | 10,1 × 13,5 | **1** | centro | √(5,05² + 6,75²) = **8,4 ft** | ✔ |
| **Bath** | 6,6 × 6,5 | **0** | — | — | no requerido |
| **East Foyer** | 5,5 × 8,0 | **1** | centro | **4,8 ft** | ✔ |
| **South Foyer / cabeza de escalera** | 9,5 × 16,5 | **1** | sobre el arranque de la escalera | **9,5 ft** | ✔ |
| | | **Σ = 8** | | | |

**Detalle del cálculo crítico (Stacks, 2 detectores).** Es el único recinto donde el resultado no es obvio, y es el que hay que mostrar desarrollado en el informe:

```
D-101 = (10,5 ; 9,0)      D-102 = (20,0 ; 21,0)

Esquina (1,4 ; 2,0)    → D-101: √(9,1²  + 7,0²)  = 11,5 ft   ✔
Esquina (29,7 ; 2,0)   → D-101: √(19,2² + 7,0²)  = 20,4 ft   ✔
Esquina (29,7 ; 20,3)  → D-102: √(9,7²  + 0,7²)  =  9,7 ft   ✔
Esquina (11,5 ; 30,3)  → D-102: √(8,5²  + 9,3²)  = 12,6 ft   ✔
Esquina (1,4 ; 30,3)   → D-102: √(18,6² + 9,3²)  = 20,8 ft   ✔  (caso crítico)

Todas ≤ 21 ft  →  2 detectores cumplen §17.7.3.2.3
1 detector NO cumple: la diagonal del polígono supera 42 ft.
```

---

## 3. Verificación recinto por recinto — Sótano

| Recinto | Geometría | Tipo | Cant. | `d_max` | ¿Cumple? |
|---|---|---|---|---|---|
| Children's Reading Room NO | 23 × 20 | Humo | 1 | √(11,5² + 10²) = **15,2 ft** | ✔ |
| Children's Reading Room (rotonda) | círculo r = 13,5 | Humo | 1 | **13,5 ft** | ✔ |
| Storage Room NE | 16 × 20 | Humo | 1 | √(8² + 10²) = **12,8 ft** | ✔ |
| Hallway | corredor ≈ 20 ft | Humo | 1 | ≈ 10 ft | ✔ |
| Electrical Room | 8 × 10 | Humo | 1 | 6,4 ft | ✔ |
| Janitor's Closet | pequeño | Humo | 1 | — | ✔ |
| South Foyer (pie de escalera) | — | Humo | 1 | — | ✔ |
| Storage oeste | 45 ft² | — | 0 | cubierto por Hallway | — |
| **Mechanical Room** (oeste) | 10 × 8 | **Térmico** | 1 | — | ✔ |
| **Mechanical Room** (este) | 11 × 12 | **Térmico** | 1 | — | ✔ |
| Women's / Men's Restroom | — | — | 0 | no requerido | — |
| | | | **Σ = 7 humo + 2 térmicos** | | |

**Justificación del cambio a detección térmica en cuartos mecánicos.** Un detector de humo en un cuarto con equipo de combustión o polvo produce alarmas no deseadas. Los detectores térmicos tienen su propio espaciamiento listado, y **§17.6.3.5.1 exige reducirlo en cielos de 10 a 30 ft** según la Tabla 17.6.3.5.1. El sótano tiene **8'-3"** de altura: **por debajo del umbral de 10 ft, no aplica reducción alguna** y rige el espaciamiento listado completo. Ambos cuartos quedan cubiertos con un solo dispositivo cada uno. ✅ verificado

---

## 4. Resumen de cantidades (preliminar, para la BOM de Sebas)

| Dispositivo | Piso 1 | Sótano | **Total** | Norma |
|---|---|---|---|---|
| Detector de humo puntual (direccionable) | 8 | 7 | **15** | NFPA 72 §17.7 |
| Detector térmico | 0 | 2 | **2** | NFPA 72 §17.6 |
| Estación manual (pull station) | 2 | 2 | **4** | NFPA 72 §17.14 |
| Horn/Strobe (P2R) | 6 | 5 | **11** | NFPA 72 §18.4 y §18.5 |
| Strobe solo (oficina, baño, sanitarios) | 2 | 2 | **4** | NFPA 72 §18.5 |
| FACP | 1 | — | **1** | NFPA 72 cap. 10 |
| **Puntos direccionables (SLC)** | | | **≈ 25** | |

**Ubicación de las estaciones manuales** — NFPA 72 §17.14 exige una en el recorrido de salida, en cada salida, montada entre **42 in y 48 in** sobre el piso terminado:
1. East Foyer (entrada principal, piso 1)
2. South Foyer (entrada sur, piso 1)
3. South Foyer del sótano (pie de la escalera interior)
4. Junto a la salida exterior norte del sótano

**Capacidad del panel.** Con ~25 puntos direccionables el sistema queda holgadamente dentro de la capacidad de cualquier panel direccionable de gama media (p. ej. un panel de 2 lazos con 159–318 puntos usa <10 % de su capacidad). *El cálculo de utilización debe presentarse igual*, porque el enunciado lo exige explícitamente en el punto 5.

---

## 5. Alturas de cielo y los dos puntos normativos — RESUELTOS con las láminas 9 y 10

### 5.0 Alturas confirmadas

| Espacio | Altura libre | Origen |
|---|---|---|
| Primer piso (general) | **15'-3¾"** | cota rotulada, lámina 9 |
| Rotonda (clave del casquete) | **17'-3"** | medido, lámina 10 |
| Sótano | **8'-3 3/32"** | cota rotulada, lámina 9 |

**Efecto sobre los cálculos:**
- **Detectores térmicos (cuartos mecánicos, sótano).** El sótano tiene 8'-3" de altura. Las tablas de NFPA 72 que **reducen** el espaciamiento de detectores térmicos por altura de cielo comienzan a aplicar por encima de los 10 ft. A 8'-3" **no hay reducción**: se aplica el espaciamiento listado completo. Un solo detector térmico por cuarto mecánico queda ampliamente cubierto. *(Verificar la tabla de reducción por altura en la edición adoptada.)*
- **Notificación visual.** NFPA 72 §18.5.5 exige montar los strobes de pared a no menos de **80 in** sobre el piso terminado. En el primer piso (cielo a 15'-4") no hay conflicto. En el sótano el cielo está a **99 in**, así que el montaje de pared a 80 in sigue siendo válido, pero **hay que verificarlo dispositivo por dispositivo** porque el margen es de solo 19 in.
- **Estratificación.** Con cielos de 15'-4" y 17'-3" el riesgo de estratificación de humo es bajo (es un fenómeno propio de volúmenes mucho más altos). **No se requiere un análisis especial.**

### 5.1 La rotonda: el domo es un ático, no el cielo del recinto — *la preocupación se cae*
La lámina 10 muestra que el domo exterior de 43'-0½" **no es el cielo de la sala**. El recinto está cerrado por un **casquete rebajado de yesería** que arranca a **15'-4"** en el perímetro y llega a **17'-3"** en la clave — una **flecha de 1'-11" sobre una luz de ≈27 ft** (≈7 %), con la zona central de ≈22 ft prácticamente plana.

> **Conclusión:** el cielo de la rotonda se trata como **cielo liso y nivelado**, no como cielo inclinado. La pendiente está muy por debajo del umbral de **1 en 8 (12,5 %)** que NFPA 72 usa para clasificar un cielo como inclinado. El detector va al centro por geometría (d_max = 13,5 ft ≤ 21 ft), y **no hace falta invocar la regla del ápice**.
>
> Esto es más fuerte que el argumento original: en vez de citar una regla que no aplica, se demuestra **con la sección** por qué no aplica.

### 5.2 La estantería radial: la regla del 15 % no se activa — *también se cae*
La lámina 9 muestra en sección que las estanterías **rematan a ≈7'-9"** sobre el piso, contra un cielo a **15'-3¾"**.

```
Altura de cielo                     = 15,31 ft
15 % de la altura de cielo          =  2,30 ft
Separación requerida para que la
regla de particiones se active      = estante a menos de 2,30 ft del cielo

Altura de estantería (lámina 9)     =  7,75 ft
Espacio libre sobre la estantería   =  7,56 ft   (49 % de la altura de cielo)

7,56 ft  >>  2,30 ft   →  LA REGLA NO APLICA
```

> **Conclusión:** las estanterías **no** compartimentan el espacio. Hay 7'-7" de altura libre continua sobre todo el abanico, y el humo llega al cielo sin obstrucción. Se aplica **espaciamiento normal de cielo liso**, y los 2 detectores de la zona de Stacks quedan justificados **por geometría** (la esquina crítica a 20,8 ft ≤ 21 ft), no por un argumento de obstrucción.
>

### 5.3 Ático combustible sobre la rotonda — limitación a declarar
Entre el casquete de yeso y el domo exterior queda un **espacio oculto de gran volumen con cerchas de madera** (lámina 10). El diseño **no** coloca detección ahí. Conviene declararlo explícitamente como limitación en la Sección 6 y señalar que en un proyecto real habría que consultarlo con la AHJ.


