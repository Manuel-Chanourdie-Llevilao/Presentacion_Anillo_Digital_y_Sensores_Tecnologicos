# División Anillo Digital y Sensores Tecnológicos — Presentación 2026

Presentación institucional interactiva de la **Superintendencia de Prevención y Gestión de Emergencias — Dirección Videoseguridad — Departamento Coordinación Operativa**. Vista única circular (hub) con dos divisiones: **Anillo Digital (04)** y **Sensores Tecnológicos (06)**.

> **Demo en vivo (GitHub Pages):** https://manuel-chanourdie-llevilao.github.io/Presentacion_Anillo_Digital_y_Sensores_Tecnologicos/

---

## 1. Qué contiene

- **Hub circular animado:** escudo central (01.png) que despliega dos satélites (04.png y 06.jpeg).
- **Panel 04 — División Anillo Digital:** capacidades, tabla Resultados 2025 vs 2026 (ENE–AGO) y dos gráficos comparativos con totales visibles sobre cada barra.
- **Panel 06 — División Sensores Tecnológicos:** fuerza efectiva, dependencia, tabla Resultados 2025 vs 2026 y dos gráficos (Pulseras y Tobilleras / Dispositivos Antipánico).
- **Diseño 100% responsive** (320px → 4K) y sin dependencias de build.

---

## 2. Estructura de archivos

\\\
01. Presentacion DCO/
├── index.html              # Presentación completa (HTML + CSS + JS en un solo archivo)
├── 01.png                  # Escudo central — Anillo Digital
├── 02.png                  # Escudo SIPGE (intro del hub)
├── 03.png                  # Recurso adicional
├── 04.png                  # Escudo División Anillo Digital
├── 05.webp                 # Recurso adicional
├── 06.jpeg                 # Escudo División Sensores Tecnológicos
├── .nojekyll               # Evita que GitHub Pages ignore archivos con _
├── .gitignore              # Ignora temporales (Thumbs.db, *.log, body_*.json)
├── .gitattributes          # Imágenes como binary, texto con eol=lf
├── README.md               # Este archivo
├── GITHUB_PUBLICACION.md   # Paso a paso para publicar/actualizar en GitHub
├── GUIA_COMPLETA.md        # Guía completa del proyecto
├── INSTRUCCIONES.md        # Manual de uso para usuarios no técnicos
└── LICENSE                 # Apache 2.0
\\\

> **Nota:** todas las imágenes se referencian con rutas relativas (\./01.png\) para que funcionen tanto en local como en GitHub Pages.

---

## 3. Paleta de colores y estilo

### Paleta corporativa

| Uso | Color | Código |
|-----|-------|--------|
| Azul principal (títulos, bordes) | Azul DAD | \#2373aa\ |
| Azul secundario (acentos) | Azul medio | \#267ca2\ |
| Azul claro (subtítulos, highlights) | Celeste | \#7dc1e5\ |
| Texto principal | Gris claro | \#b8b8b8\ |
| Texto secundario / footer | Gris medio | \#5d5d5d\ |
| Fondo | Negro azulado | \#06090a\ |
| Éxito / variación positiva | Verde | \#4ade80\ |
| Variación negativa | Rojo suave | \#f87171\ |
| Fondo tarjetas | Azul translúcido | \gba(35,115,170,0.07)\ |

### Tipografía y efectos

- **Fuente:** \Poppins\ (Google Fonts, pesos 300/400/600/700) + fallback \Segoe UI\.
- **Fondo:** degradado \#06090a → #1a1d20 → #0f1214\ + radiales sutiles.
- **Tarjetas:** \detail-card\ con borde \gba(35,115,170,0.22)\, radio 10px.
- **Tablas:** \mini-table\ con cabecera \gba(35,115,170,0.12)\.
- **Gráficos:** Chart.js (barras) + plugin propio \hubBarLabelsPlugin\ que dibuja el total sobre cada barra, fuera de la misma, siempre visible.
- **Animaciones:** \pulseGlow\ en círculo central, \loatA/B\ en satélites, \hintPulse\ en pista de interacción. Respeta \prefers-reduced-motion\.

---

## 4. Tecnologías

- HTML5 + CSS3 (Grid/Flex, clamp, aspect-ratio, custom properties)
- JavaScript vanilla (sin framework)
- Chart.js vía CDN (\https://cdn.jsdelivr.net/npm/chart.js\)
- Google Fonts (Poppins)

Sin paso de build: basta abrir \index.html\.

---

## 5. Uso local

1. Clonar o descargar el repositorio.
2. Doble clic en \index.html\ o servir con un servidor estático:

\\\powershell
# Python
python -m http.server 8000
# Node
npx http-server
\\\

3. Abrir \http://localhost:8000\.

**Navegación:** clic en el escudo central → elegir satélite (04/06) → \Volver\ o \Esc\ para regresar. Accesible por teclado (Enter/Espacio).

---

## 6. Cómo actualizar datos

### División Anillo Digital (04)

- **Capacidades Operativas:** en \#detail04\ → primer \.detail-card\ (lista \ul\).
- **Tabla Resultados:** en \#detail04\ → \.mini-table\ (variaciones con clases \adge-up\/\adge-down\).
- **Gráficos:** en \initHubCharts()\ → datasets de \hubChartProcedimientos\ y \hubChartAlarmas\. Los totales se dibujan automáticamente por \hubBarLabelsPlugin\.

### División Sensores Tecnológicos (06)

- **Fuerza Efectiva:** en \#detail06\ → primer \.detail-card\ (\Fuerza Efectiva: 104 efectivos\).
- **Tabla Resultados:** en \#detail06\ → \.mini-table\.
- **Gráficos:** en \initSensoresCharts()\ → \hubChartPulseras\ (Alertas/Detenidos) y \hubChartAntipanico\ (Accionamiento/Detenidos).

> Tras editar \index.html\, recargar con \Ctrl+F5\ para invalidar caché.

---

## 7. Flujo Git / GitHub (sin fricción)

El repositorio ya está conectado a **GitHub Pages** (\main\ → \/\).

\\\powershell
# Ver estado
git status

# Guardar cambios
git add index.html
git commit -m "feat: descripción clara del cambio"

# Publicar (usa el credential manager de Windows, sin token en la URL)
git push origin main
\\\

- **Remote:** \https://github.com/Manuel-Chanourdie-Llevilao/Presentacion_Anillo_Digital_y_Sensores_Tecnologicos.git\
- **Branch:** \main\
- **Pages:** https://manuel-chanourdie-llevilao.github.io/Presentacion_Anillo_Digital_y_Sensores_Tecnologicos/ (deploy automático en 1–2 min tras cada push)
- **.gitignore:** solo temporales; imágenes y HTML nunca se ignoran.
- **.gitattributes:** imágenes como \inary\, texto con \eol=lf\.
- **.nojekyll:** evita que Pages ignore archivos que empiezan con \_\.

Si \git push\ pide credenciales, usar el **Personal Access Token (classic)** con scope \epo\ como password (el helper \manager\ lo guarda).

---

## 8. Historial relevante

| Fecha | Cambio |
|-------|--------|
| 2026-09-08 | Hub circular, paneles 04/06 con tablas y gráficos comparativos 2025–2026, totales sobre barras, sanitización de credenciales y docs actualizados |
| 2026-09-03 | Migración de escudos a raíz, corrección de rutas relativas |
| 2026-08 | Versión inicial 5 slides clásica |

---

## 9. Licencia y autoría

- **Licencia:** Apache 2.0 (ver \LICENSE\).
- **Autor:** División Anillo Digital — Departamento Coordinación Operativa — Superintendencia Prevención y Gestión de Emergencias — Policía de la Ciudad.

---

**Última actualización:** 2026-09-08 · **Estado:** Producción · **Branch:** main

