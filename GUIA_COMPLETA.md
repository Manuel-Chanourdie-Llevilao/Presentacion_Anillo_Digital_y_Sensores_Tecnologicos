# 📦 Guía Completa — División Anillo Digital 2026

> **Presentación institucional interactiva** — Superintendencia de Prevención y Gestión de Emergencias · Dirección Videoseguridad · Departamento Coordinación Operativa  
> **Demo:** https://manuel-chanourdie-llevilao.github.io/Presentacion_Anillo_Digital/ · **Repo:** \Manuel-Chanourdie-Llevilao/Presentacion_Anillo_Digital\ · **Branch:** \main\

---

## 1. Resumen ejecutivo

- **Vista única hub circular:** un escudo central (01.png) despliega dos satélites (04.png y 06.jpeg). Cada satélite abre su panel de detalle; el círculo queda como botón \"Volver"\.
- **Sin slides clásicos:** la versión anterior de 5 diapositivas fue retirada; todo el contenido vive en los dos paneles del hub.
- **Datos comparativos 2025 vs 2026 (ENE–AGO)** con tablas y gráficos de barras. Los totales se muestran **siempre visibles sobre cada barra, fuera de la misma**.
- **100% responsive** (320px → 4K) y sin build: basta abrir \index.html\.

---

## 2. Estructura de archivos (estado real 2026-09-08)

\\\
01. Presentacion DCO/
├── index.html              # Presentación completa (HTML + CSS + JS embebidos)
├── 01.png                  # Escudo central — Anillo Digital
├── 02.png                  # Escudo SIPGE (intro del hub)
├── 03.png                  # Recurso adicional
├── 04.png                  # Escudo División Anillo Digital
├── 05.webp                 # Recurso adicional
├── 06.jpeg                 # Escudo División Sensores Tecnológicos
├── .nojekyll               # Evita que Pages ignore archivos con _
├── .gitignore              # Solo temporales (Thumbs.db, *.log, body_*.json)
├── .gitattributes          # Imágenes binary, texto eol=lf
├── README.md               # Resumen técnico + flujo Git
├── GITHUB_PUBLICACION.md   # Paso a paso para publicar/actualizar
├── GUIA_COMPLETA.md        # Esta guía
├── INSTRUCCIONES.md        # Manual para usuario no técnico
└── LICENSE                 # Apache 2.0
\\\

**Rutas de imágenes:** siempre relativas (\./01.png\). Las rutas absolutas \C:/...\ rompen en GitHub Pages.

---

## 3. Paleta corporativa y estilo — cómo debe quedar

### 3.1 Paleta (no cambiar sin acordar)

| Uso | Código | Dónde se usa |
|-----|--------|--------------|
| Azul principal | \#2373aa\ | Títulos, bordes, botones |
| Azul secundario | \#267ca2\ | Acentos, bordes secundarios |
| Celeste | \#7dc1e5\ | Subtítulos, highlights, cabeceras de tabla |
| Gris claro | \#b8b8b8\ | Texto principal |
| Gris medio | \#5d5d5d\ | Texto secundario, footer |
| Fondo | \#06090a\ | Body y hub |
| Verde ↑ | \#4ade80\ | \adge-up\, \positive\ |
| Rojo ↓ | \#f87171\ | \adge-down\ |
| Fondo tarjetas | \gba(35,115,170,0.07)\ | \.detail-card\ |
| Borde tarjetas | \gba(35,115,170,0.22)\ | \.detail-card\ |

### 3.2 Tipografía y efectos

- **Fuente:** \Poppins\ 300/400/600/700 (Google Fonts) + fallback \Segoe UI\.
- **Fondo hub:** degradado \#06090a → #1a1d20 → #0f1214\ + dos radiales sutiles (\gba(35,115,170,0.08)\).
- **Tarjetas:** \.detail-card\ — fondo translúcido, borde 1px, radius 10px, padding 12px.
- **Tablas:** \.mini-table\ — cabecera \gba(35,115,170,0.12)\, filas alternas \gba(93,93,93,0.06)\.
- **Gráficos:** Chart.js barras + plugin propio \hubBarLabelsPlugin\ (dibuja el total sobre cada barra, con sombra, siempre visible). Requiere \layout.padding.top:16\ para no recortar.
- **Animaciones:** \pulseGlow\ (círculo), \loatA/B\ (satélites), \hintPulse\ (pista). Se desactivan con \prefers-reduced-motion\.
- **Responsive:** breakpoints 360/430/767/1024/1366/1920/2560px. En móvil el hub pasa a columna y los gráficos a 1 columna.

### 3.3 Comentarios para entender el código

- **CSS:** cada bloque está comentado por sección (hub, tarjetas, tablas, responsive). Buscar \/* ========== NUEVO SISTEMA CIRCULO ANIMADO ========== */\.
- **JS:** funciones clave comentadas:
  - \handleMainClick()\ — expande/colapsa satélites.
  - \showDetail('04'|'06')\ — muestra panel, cambia imagen central, inicializa gráficos.
  - \ackToHub()\ — restaura intro y destruye gráficos.
  - \hubBarLabelsPlugin\ — plugin Chart.js que pinta totales fuera de la barra.
  - \initHubCharts()\ / \initSensoresCharts()\ — crean los 4 gráficos comparativos.

---

## 4. Contenido por panel

### Panel 04 — División Anillo Digital (\#detail04\)

- **Capacidades Operativas:** \Posee Dos Centros de Monitoreo de Patentes\, \886 Lectores de Patentes\, \75 Cámaras 24/7\, \43 móviles\, \254 efectivos\ + 4 bullets de funciones.
- **Tabla Resultados 2025 vs 2026:** Intercept. c/ secuestro, Aprehendidos, Actuaciones, Alarmas, Alarmas atendidas, Promedio Incremento Personal (variaciones con \adge-up\).
- **Gráficos:** \hubChartProcedimientos\ (Intercept./Aprehendidos/Actuaciones) y \hubChartAlarmas\ (Alarmas/Atendidas).

### Panel 06 — División Sensores Tecnológicos (\#detail06\)

- **Fuerza Efectiva:** \Fuerza Efectiva: 104 efectivos\ + bullets: \Posee un Centro de Monitoreo\, \Recepción y gestión de Dispositivos Antipánico, Pulseras y Tobilleras\, \Monitoreo de Dispositivos judicializados\.
- **Dependencia:** texto art. 176° + dos secciones.
- **Tabla Resultados:** Fuerza efectiva 90→104, Dispositivos Antipánico Monitoreados, Accionamiento 7.339→6.549, Detenidos 173→230, Pulseras Monitoreadas, Cantidad Alertas 657.710→662.653, Detenidos 93→122.
- **Gráficos:** \hubChartPulseras\ (Alertas/Detenidos) y \hubChartAntipanico\ (Accionamiento/Detenidos).

---

## 5. Tecnologías

- HTML5 + CSS3 (Grid, Flex, clamp, aspect-ratio)
- JavaScript vanilla
- Chart.js (CDN) + Google Fonts (Poppins)
- Sin bundler ni build

---

## 6. Uso local

\\\powershell
# Opción 1: doble clic en index.html
# Opción 2: servidor local
python -m http.server 8000
# abrir http://localhost:8000
\\\

Navegación: clic en escudo central → elegir satélite → \Volver\ o \Esc\. Teclado: Enter/Espacio sobre escudos.

---

## 7. Cómo actualizar datos (mapa de edición)

| Qué | Dónde en index.html | Nota |
|-----|---------------------|------|
| Capacidades 04 | \#detail04\ → primer \.detail-card ul\ | Mantener orden: Centros → Lectores → Cámaras → móviles → efectivos |
| Tabla 04 | \#detail04 .mini-table tbody\ | Variación: \(2026-2025)/2025*100\ → \adge-up/down\ |
| Gráficos 04 | \initHubCharts()\ datasets | Totales automáticos por plugin |
| Fuerza 06 | \#detail06\ primer \.detail-card h4\ | Formato: \Fuerza Efectiva: 104 efectivos\ |
| Tabla 06 | \#detail06 .mini-table tbody\ | Incluir Accionamiento y Cantidad Alertas con variaciones |
| Gráficos 06 | \initSensoresCharts()\ datasets | Pulseras: Alertas/Detenidos; Antipánico: Accionamiento/Detenidos |

Tras editar, recargar con \Ctrl+F5\.

---

## 8. Flujo Git / GitHub (sin fricción)

\\\powershell
git status
git add index.html
git commit -m "feat: descripción clara"
git push origin main
\\\

- **Remote:** \https://github.com/Manuel-Chanourdie-Llevilao/Presentacion_Anillo_Digital.git\ (sin token en URL)
- **Credential helper:** \manager\ (Windows) guarda el PAT.
- **Pages:** deploy automático 1–2 min en https://manuel-chanourdie-llevilao.github.io/Presentacion_Anillo_Digital/
- **Verificación:** \git check-ignore -v 01.png\ debe dar vacío; \git ls-files\ lista versionados.

Si pide password, usar **PAT classic** scope \epo\.

---

## 9. Checklist antes de presentar

- [ ] \index.html\ abre y el hub anima
- [ ] Satélites 04 y 06 abren sus paneles
- [ ] Tablas con variaciones correctas (↑ verde / ↓ rojo)
- [ ] Gráficos con totales visibles fuera de la barra
- [ ] Responsive probado (móvil y desktop)
- [ ] \git push\ sin errores y Pages en verde

---

## 10. Historial

| Fecha | Cambio |
|-------|--------|
| 2026-09-08 | Hub circular, paneles 04/06 completos, totales sobre barras, sanitización de credenciales, docs reescritos |
| 2026-09-03 | Escudos a raíz, rutas relativas, .gitignore/.gitattributes corregidos |
| 2026-08 | Versión inicial 5 slides |

---

**Última actualización:** 2026-09-08 · **Estado:** Producción
