# Informe de revisión de planos — Revisión B
### Paxton Carnegie Library · Sistema de detección y alarma contra incendios
Archivo revisado: `Planos/Revision de planos/Paxton_Sistema_Alarma.drawio.pdf` (4 páginas)
Fuente corregida: `Planos/Paxton_Sistema_Alarma.drawio`
Copia de la versión anterior: `_backup_prerevision/`

---

## 0. Resumen

El diseño **de fondo es correcto**: la selección de equipos, el criterio de detección y las
cuentas eléctricas están bien planteados y verifiqué los números uno por uno contra los
datasheets. Lo que fallaba estaba casi todo en el **dibujo**: los circuitos de notificación
no llegaban al panel, el anunciador estaba conectado al circuito equivocado, y tres
aparatos estaban puestos en el sitio equivocado. Además había cuatro datos que no
coincidían entre el plano, el riser, el BOM y la memoria de cálculo.

Encontré **19 problemas**. Corregí 16 en los archivos; 3 los dejo señalados porque son
decisiones tuyas o requieren verificación en obra.

| Gravedad | Nº | Qué son |
|---|---|---|
| 🔴 Grave | 3 | El sistema, tal como estaba dibujado, no funcionaría |
| 🟠 Medio | 6 | Errores de ubicación e identificación de dispositivos |
| 🟡 Datos | 6 | Cifras que se contradicen entre documentos |
| 🔵 Forma | 4 | Presentación del plano y del PDF |

---

## 1. 🔴 Errores graves de cableado

### 1.1 Ningún circuito NAC llegaba al panel
En las dos plantas, los cuatro NAC estaban dibujados como **cadenas sueltas**: NAC-1 iba
de N-101 a N-104 a N-102 y ahí terminaba, sin ninguna conexión con el FACP. Lo mismo los
otros tres. Tampoco había montante que llevara NAC-1 y NAC-2 del sótano al piso 1.

Un NAC dibujado así no tiene alimentación ni supervisión: es el error más serio del juego
de planos porque el sistema, literalmente, no sonaría.

**Corregido.** Los cuatro circuitos arrancan ahora en el FACP:
- NAC-3: FACP → N-003 → N-002 → N-001 → EOL
- NAC-4: FACP → N-007 → N-006 → N-005 → N-004 → EOL
- NAC-1: FACP → montante → N-104 → N-101 → N-102 → EOL
- NAC-2: FACP → montante → N-108 → N-105 → N-106 → N-103 → N-107 → EOL

Reordené las cadenas para que cada circuito empiece en el punto por donde entra la
alimentación. Como consecuencia **cambian las longitudes y las caídas de tensión** — ver §3.1.

### 1.2 El anunciador ANN-80 estaba intercalado en el lazo SLC
En el piso 1 el lazo iba `… → D-107 → M-101 → **ANN-1** → D-104 → D-105`. El ANN-80 **no
es un dispositivo direccionable**: va en el **ANN-BUS EIA-485** de 4 conductores, en bornes
propios del panel (TB6). Lo dice el propio riser de la página 4 y la fila ANN-1 del BOM,
así que el plano se contradecía con el resto del proyecto.

**Corregido.** El SLC pasa ahora directo `M-101 → D-104`, y se dibujó el ANN-BUS como línea
punteada morada desde el FACP, por el montante, hasta el ANN-80 del East Foyer.

### 1.3 No se dibujaban las resistencias de fin de línea
La nota 6 del riser las mencionaba, pero en los planos no aparecía ninguna. Sin EOL, un
NAC Clase B no está supervisado.

**Corregido.** Se añadió el símbolo EOL (4,7 kΩ ½ W, P/N 71252) al final de los cuatro
circuitos, más una fila en la leyenda.

> **Ojo con lo contrario:** el **lazo SLC Style 4 NO lleva EOL**. Se supervisa por la propia
> comunicación con los dispositivos. La resistencia de 47 kΩ (P/N R-47K) del manual es para
> los circuitos de entrada de los módulos MMF/CMF-300, que este diseño no usa
> (manual 52646:B §1.6.4). Lo dejé anotado en el plano para que nadie lo "corrija" al revés.

---

## 2. 🟠 Errores de ubicación e identificación

### 2.1 N-003 estaba fuera de la rotonda del sótano
El horn/strobe de 30 cd que cubre el Children's Reading Room circular estaba dibujado
**al otro lado del muro**, en el vestíbulo delante del Electrical Room. Un estrobo detrás de
un muro cubre exactamente nada, y era el único aparato visual de esa sala.
**Corregido:** movido a la cara interior del muro, dentro de la sala redonda.

### 2.2 N-108 estaba mal en dos cosas a la vez
- Dibujado como **ST (estrobo solo)** cuando el BOM, `6_Notificacion_Candelas.csv` y el
  riser dicen los tres **H/S 15 cd**. El South Foyer es una salida y una caja de escalera:
  necesita audible.
- Colocado sobre el muro de la Librarian's Office, ~7 ft fuera del recinto que le toca.

**Corregido:** ahora es H/S y está dentro del South Foyer.

> Este error, además, se colaba en el cálculo: con ST el NAC-2 daría 0,384 A y no los
> 0,397 A que usa toda la memoria. Al corregir el símbolo, el número vuelve a cuadrar.

### 2.3 N-102 estaba flotando en medio del recinto
A ~4 ft del muro este del North Reading Room, sin apoyo, cuando la propia nota del plano
dice que los aparatos van montados **sobre muro**. **Corregido:** pegado al muro norte.

### 2.4 El ANN-80 estaba encima del vano de la puerta de entrada
El símbolo quedaba a caballo del muro sur del East Foyer, justo sobre las hojas de la
puerta principal. **Corregido:** movido a un paño ciego del muro este del vestíbulo.

### 2.5 M-002 estaba dentro del espesor del muro exterior
La estación manual de la salida este quedaba dibujada dentro de la mampostería.
**Corregido:** llevada a la cara interior del muro del Mechanical Room este.

### 2.6 Los símbolos de montante no coincidían entre plantas
El del piso 1 estaba al **norte** de la escalera y el del sótano al **sur**: ~11 ft de
diferencia en la realidad, cuando un montante es vertical y tiene que caer en el mismo
punto en las dos plantas. **Corregido:** ambos en el mismo punto físico, junto a la
escalera del South Foyer, y ahora rotulados `SLC / NAC / ANN` porque por ahí suben las
tres cosas.

---

## 3. 🟡 Datos que no coincidían entre documentos

### 3.1 Longitud máxima del lazo SLC: se citaba el límite del calibre equivocado
El riser y `Calculo_Electrico_Seccion5.md` §5.3.d comparaban los ≈1 200 ft del lazo contra
**10 000 ft**. Ese es el máximo del **12 AWG**. El BOM especifica **16 AWG**, cuyo máximo son
**4 875 ft** (Fire•Lite doc. 51309, Tablas 2.1 y 2.2, iguales en CLIP y en LiteSpeed).

Utilización real: **24,6 %**, no 12 %. Sigue cumpliendo con holgura, pero el dato citado
estaba mal — y es de los que un jurado comprueba.

Curiosamente el `RECAP_PROYECTO.md` §3.4 **ya decía bien** los 4 875 ft: el error solo se
había propagado al riser y a la tabla de cálculo.

**Corregido en los tres sitios.** Y añadí la verificación que faltaba: el doc. 51309 §2.2.1
exige que la resistencia c.c. del lazo no pase de **40 Ω** en Style 4 →
`2 × 1,2 kft × 4,89 Ω/kft = 11,7 Ω` ✔.

### 3.2 Longitudes de los NAC y caídas de tensión
Las longitudes de la revisión A (130 / 110 / 90 / 70 ft) decían estar "medidas sobre los
planos desde el Electrical Room", pero eso era imposible: los NAC no llegaban al panel en
el plano. Al cerrar los circuitos y medir el recorrido real (métrica ortogonal a 25 px/pie,
más la subida entre niveles, más el 25 % de holgura), los valores suben:

| Circuito | Antes | Ahora | V_final 16 AWG |
|---|---:|---:|---|
| NAC-1 | 130 ft → 19,98 V | **167 ft** | **19,85 V** ✔ |
| NAC-2 | 110 ft → 19,97 V | **174 ft** | **19,72 V** ✔ ← peor caso |
| NAC-3 | 90 ft → 20,14 V | **100 ft** | **20,11 V** ✔ |
| NAC-4 | 70 ft → 20,20 V | **74 ft** | **20,19 V** ✔ |

**El 16 AWG sigue cumpliendo en los cuatro**, con 3,7 V de margen en el peor caso en vez de
4,0 V. La conclusión del proyecto no cambia; el dato sí, y ahora es defendible.

### 3.3 El BOM contaba 8 horn/strobe de 15 cd; son 7
Con 8 salían 12 H/S + 4 ST = **16 aparatos**, y todo el resto del proyecto (memoria, riser,
tabla de candelas, corriente de 1,314 A) trabaja con **15**: 11 H/S + 4 ST. Los de 15 cd son
N-102, N-104, N-107, N-108, N-002, N-004 y N-007 = **7**. **Corregido**, y le puse la lista de
posiciones a la fila para que no vuelva a descuadrar.

### 3.4 El BOM decía 26,5 % donde el resto dice 27,5 %
`1,924 / 7,0 = 27,5 %`. **Corregido.**

### 3.5 Faltaba el cable del ANN-BUS en el BOM
Estaban CBL-1 (SLC), CBL-2 (NAC) y CBL-3 (acometida), pero no el bus del anunciador.
**Añadido CBL-4:** 4 conductores 18 AWG, Clase B, ~60 ft. Con el consumo del ANN-80 de
0,040 A la Tabla 1.1 del manual admite hasta 4 688 ft en 18 AWG — sobra.

### 3.6 Quedaban celdas "PENDIENTE" en dos CSV
`3_Corriente_Alarma.csv` y `5_Baterias_y_Capacidad.csv` seguían con los marcadores de la
plantilla ("Falta datasheet horn/strobe") y con fórmulas sin evaluar, además de contar
6 y 5 dispositivos en NAC-2 y NAC-4 donde hay 5 y 4. Si se entregan así, parecen trabajo
sin terminar. **Rellenados y corregidos.**

---

## 4. 🟠 Lo que faltaba por norma

### 4.1 Sincronización de los estrobos — esto sí es un requisito
El piso 1 es de planta libre: desde la circulación central se ven a la vez los estrobos de
Stacks, North Reading y circulación. Con **más de dos aparatos visibles en un mismo campo
de visión**, el capítulo 18 de NFPA 72 exige que **destellen sincronizados**. El proyecto no
lo mencionaba en ninguna parte.

La buena noticia: **no hace falta comprar nada.** El MS-9600LS trae sincronización
seleccionable por NAC y soporta el protocolo **System Sensor**, que es justo el de la
familia SpectrAlert Advance (manual 52646:B §3.6.5.5.8 y §4.16). El límite es de 46 estrobos
sincronizados por NAC; el circuito más cargado tiene 5 → 10,9 %.

**Añadido:** nota en las dos plantas, nota 8 del riser, apartado nuevo §5.3.g en la memoria
de cálculo y fila en el BOM. Es, además, un buen punto para la presentación oral: muestra
que se leyó el manual del panel y no solo la norma.

### 4.2 Verificación de la resistencia del lazo (§3.1) — añadida.

### 4.3 Falta el cálculo de audibilidad
El proyecto verifica la parte visual con la Tabla 18.5.5.4.1(a), pero **no hay ni una línea
sobre la parte audible**, que NFPA 72 §18.4.4 exige igual: 15 dBA sobre el ambiente medio.

No lo añadí porque requiere decidir un ambiente de referencia, pero el margen es enorme y
es media página fácil de escribir: el P2R da **88 dBA a 10 ft** (24 V, DC, reverberante,
Temporal High). Con un ambiente de biblioteca de ~45 dBA hace falta ≥60 dBA, y a 30 ft el
aparato todavía entrega ~78 dBA. **Te recomiendo escribirlo**: es un requisito explícito y
ahora mismo es el único hueco de fondo que le queda al documento.

---

## 5. 🔵 Presentación del plano y del PDF

### 5.1 El riser se partía en dos páginas del PDF
La página 3 salía **prácticamente en blanco**, solo con el título al pie, y la página 4 con
el diagrama sin título. Causa: en el `.drawio`, el título del riser estaba en `y = −40`,
fuera de la página, y drawio añadía una hoja para recogerlo.
**Corregido:** todo el contenido del riser desplazado 60 unidades y el título dentro de la
hoja. Verificado: las tres páginas caben ahora dentro de sus límites. **El PDF nuevo tendrá
3 páginas, no 4.**

### 5.2 En el riser, la línea de NAC tachaba el texto
La línea roja pasaba por encima de los cuadros NAC-2 y NAC-4 (se leía
"N̶-̶0̶0̶6̶ ̶S̶T̶ ̶1̶5̶ ̶c̶d̶ ̶M̶e̶n̶s̶ ̶R̶e̶s̶t̶r̶o̶o̶m̶"). **Corregido:** las cuatro salidas bajan por el pasillo
libre en x = 965, entre los cuadros del SLC y los del NAC, y entran por el lado izquierdo.

### 5.3 No se distinguía NAC-1 de NAC-2 en el plano
La leyenda listaba los circuitos por separado, pero en el dibujo todos eran la misma línea
roja punteada: era imposible saber qué tramo era cuál. El enunciado pide expresamente
"identificación de circuitos". **Corregido:** rótulos `NAC-1`, `NAC-2`, `NAC-3`, `NAC-4` y
`SLC` sobre los recorridos, con fondo blanco.

### 5.4 Faltaban cajetín, norte y escala
- **Cajetín añadido** en las dos plantas: proyecto, edificio, curso, normas aplicables,
  número de lámina, escala, revisión. **Deja en blanco la fecha y los autores —
  rellénenlas ustedes.**
- **Norte añadido.** Va hacia arriba: lo confirmé contra el propio plano (North Reading
  Room arriba, South Reading Room abajo, East Foyer a la derecha).
- El subtítulo decía *"Escala del fondo: 25 px = 1 pie"*, que es una unidad de pantalla y no
  significa nada en una hoja impresa. **Cambiado** por la referencia a la lámina HABS y su
  escala original de 1/4"=1'-0", con la advertencia de comprobarla al imprimir.

### 5.5 El bocadillo de la acometida tapaba la escalera del sótano
Estaba encima del dibujo, ocultando el arranque de escalera y parte del South Foyer, con
una flecha naranja que cruzaba media planta. **Movido al margen derecho** y rotulado
"ALIMENTACIÓN DEL FACP".

---

## 6. Lo que NO cambié (decisión tuya)

1. **D-003 cae justo sobre el pilar central bajo la rotonda del sótano.** No es
   necesariamente un error —un detector en el cielo sobre un pilar es admisible— pero si
   ese cuadrado es un pilar que llega al cielo, conviene desplazarlo 3–4 ft. Verifícalo en
   la lámina 3 antes de decidir.

2. **El Storage pequeño del oeste (45 ft²) no lleva detector**, y el Janitor's Closet
   (35 ft², más pequeño) sí. `0_Room_Schedule.csv` lo justifica como "cubierto por hallway",
   pero un detector en el pasillo no cubre un cuarto con puerta. **Es una inconsistencia de
   criterio, no necesariamente un incumplimiento**: solo lo sería si declaran *cobertura
   total* (NFPA 72 §17.5.3.1). Dos salidas igual de válidas: o añaden D-008 ahí, o escriben
   explícitamente en la Sección 4 que la cobertura es selectiva y por qué. Yo pondría el
   detector: cuesta un punto de lazo del 90 % que tienen libre.

3. **N-104 está montado sobre una columna**, no sobre un muro, y la nota del plano dice
   "sobre muro". En la práctica se monta en columnas sin problema; si quieren ser
   estrictos, muevan el aparato o matizen la nota.

---

## 7. Lo que verifiqué y está bien

Para que no queden dudas de qué se revisó y salió limpio:

- **Corrientes de los aparatos**, una por una contra la tabla *UL Max. Current Draw* del
  AVDS102, columna *2-Wire Horn Strobe, DC Input, Temporal High, 16–33 V*: 15 cd = 79 mA,
  30 cd = 107 mA, 75 cd = 176 mA; estrobos SR 15 cd = 66 mA. **Todas correctas.**
- **Rango de operación 16–33 V** → el criterio de 16 V de la §5.3.c es el correcto.
- **Standby 0,1933 A / 0,1413 A** y **alarma 1,924 A**: recalculados, cuadran.
- **Reparto por circuito** 0,334 / 0,397 / 0,293 / 0,290 = 1,314 A: cuadra.
- **Batería 4,26 AH → 12 AH por mínimo del panel**: recalculado, correcto. Buen hallazgo.
- **Recuento de puntos del lazo**: 8+7 = 15 humo + 2 térmicos = 17 detectores, 4 módulos,
  21 puntos. Coincide en plano, riser y BOM.
- **Criterio de candelas**: la lectura de la Tabla 18.5.5.4.1(a) es correcta, incluida la
  fila de 30×30 → 34 cd que casi todo el mundo se salta, y el salto a 75 cd en Stacks.
- **Detección**: D-105 está exactamente en el centro geométrico de la rotonda (13,5 ft ≤
  21 ft), D-103 prácticamente centrado en el North Reading Room, y H-002 a 10 ft de la
  esquina más lejana del Mechanical Room este. Los dos detectores de Stacks, bien.
- **D-108 está en la escalera interior correcta** — la que sube desde el sótano —, no en una
  de las dos exteriores. Lo comprobé cruzando las dos plantas.
- **Modelos y compatibilidad**: SD355, H355R, B350LP, BG-12LX, ANN-80, P2R, SR, EOL 71252.
  Todos existen, todos son de catálogo y todos encajan con el MS-9600LS.

---

## 8. Archivos modificados

| Archivo | Qué cambió |
|---|---|
| `Planos/Paxton_Sistema_Alarma.drawio` | Las tres páginas: cableado, ubicaciones, EOL, montante, rótulos, leyenda, cajetín, norte, riser |
| `Calculo_Electrico_Seccion5.md` | §5.3.c longitudes y caídas · §5.3.d límite de 4 875 ft y resistencia del lazo · **§5.3.g nueva** (sincronización) · resumen |
| `RECAP_PROYECTO.md` | Caída peor caso y nota del límite del SLC |
| `BOM_Calculos/1_BOM_Device_Schedule.csv` | HS-1 de 8 a 7 · 26,5 → 27,5 % · CBL-4 ANN-BUS · notas de sincronización y EOL |
| `BOM_Calculos/3_Corriente_Alarma.csv` | Celdas PENDIENTE y conteos de NAC-2 y NAC-4 |
| `BOM_Calculos/4_Caida_Tension_NAC.csv` | Longitudes y caídas nuevas |
| `BOM_Calculos/5_Baterias_y_Capacidad.csv` | Celdas PENDIENTE, fórmulas evaluadas, verificación del SLC |

La versión anterior está íntegra en `_backup_prerevision/`.

## 9. Segunda pasada sobre el PDF regenerado

Revisada la exportación de Walter (3 páginas, correcto). Sobre ella aparecieron 5 defectos
de maquetación que ya están corregidos y reexportados:

| # | Qué pasaba | Corregido |
|---|---|---|
| 1 | Las tres etiquetas sueltas `SLC` / `NAC-1` / `NAC-2` de la revisión A quedaban **encima del texto** de la caja "Circuitos y criterio de recorrido", en las dos plantas | Eliminadas: ya están los rótulos sobre el recorrido y la descripción en la caja |
| 2 | En el riser, el tronco rojo de los NAC **rozaba la caja de baterías** y cruzaba el rótulo azul "SLC Clase B (Style 4)" | Bajado a un pasillo libre entre el FACP y las baterías |
| 3 | El texto de NAC-2 **se salía del cuadro** ("desfavorable" caía fuera del borde) | Reordenado y cuadro más alto |
| 4 | El cuadro de acometida **tapaba el rótulo "SOTANO"** de la banda | Bajado 22 unidades |
| 5 | En el piso 1, el tramo N-108 → N-105 **cruzaba por encima del símbolo de montante** | Rebajado a y = 1345, por debajo del hexágono |

## 10. Cómo regenerar el PDF a partir de ahora

Se instaló **drawio-desktop 31.4.4** en modo portátil, sin tocar el sistema y sin `sudo`:

- Aplicación: `~/opt/drawio/` (AppImage extraído, no necesita FUSE)
- Comando: `drawio` (enlace en `~/.local/bin`, que ya está en el PATH)
- Lanzador de escritorio: aparece como **draw.io** en el menú de aplicaciones

Para reexportar el juego completo después de cualquier cambio:

```bash
drawio -x -f pdf -a --crop=false \
  -o "$HOME/Documentos/Norma/Planos/Revision de planos /Paxton_Sistema_Alarma.drawio.pdf" \
  "$HOME/Documentos/Norma/Planos/Paxton_Sistema_Alarma.drawio"
```

`-a` exporta **todas las páginas** y `--crop=false` evita que recorte a los márgenes del
contenido. Debe salir con **3 páginas** (piso 1, sótano, riser). Si salen 4, algo quedó
fuera de hoja.

> ⚠️ **Ojo con el nombre de la carpeta.** `Revision de planos ` **termina en un espacio**.
> Por eso en el comando la ruta va entre comillas y con ese espacio antes de la barra. Si se
> copia sin él, el PDF se escribe en otra carpeta y parece que la exportación "no hizo nada".
> Vale la pena renombrar la carpeta y quitarle el espacio final.

## 11. Lo que queda pendiente en el proyecto

Del `RECAP_PROYECTO.md` §5, y sigue vigente:

1. **Presentación oral** — sin empezar, y es el entregable 6.
2. **Cálculo de audibilidad** (§4.3 de este informe) — media página, es el último hueco
   de fondo del documento.
3. Prompt de Gemini en el Anexo A.
4. Consolidar los `.md` y exportar el documento final.
