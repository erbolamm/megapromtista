# AGENTS.md — MegaPromtista

> Portal oficial de ingeniería de prompts, factoría de agentes autónomos y
> herramientas open source.
>
> 🌐 **Web en vivo**: https://megapromtista.com
> 📦 **GitHub Pages**: https://erbolamm.github.io/megapromtista/
> 🏷️ **Marca**: ApliArte / ErBolamm — F. Javier Mateo Márquez

Este archivo es el contrato canónico de trabajo para cualquier agente o
desarrollador que entre a este repositorio. Convive con la central
[`erbolamm-trabajo/AGENTS.md`](../erbolamm-trabajo/AGENTS.md) — ante
conflicto manda el archivo local solo si aporta una regla específica del
proyecto; en todo lo demás gana la central.

---

## 1. Identidad del proyecto

- **Nombre**: MegaPromtista
- **Dominio**: `megapromtista.com` (vía `CNAME` para GitHub Pages)
- **Tipo**: SPA estática de una sola página (`index.html` en la raíz)
- **Stack**: HTML5 + CSS canónico + Canvas 2D Retina (efectos hero).
  Sin build, sin bundler, sin framework. Servido por GitHub Pages.
- **Licencia**: MIT © 2026 F. Javier Mateo Márquez (ApliArte / ErBolamm).
- **Marca gráfica**: ApliArte. **Aplica** todo el
  [`APLIARTE_BRAND_KIT.md`](../erbolamm-trabajo/ingredientes/marca/APLIARTE_BRAND_KIT.md).

## 2. Skills del ecosistema que aplican aquí

Este proyecto **NO** tiene skills propias. Lo que aplica viene de la central:

| Skill | Para qué sirve | ¿Aplica? |
|---|---|---|
| [`skills/auditoria-web/`](../erbolamm-trabajo/skills/auditoria-web/) | Auditar web existente por URL para SEO, conversión y accesibilidad. | ✅ cuando se pida una revisión externa |
| [`skills/big-school-webs/references/landing-editorial.md`](../erbolamm-trabajo/skills/big-school-webs/references/landing-editorial.md) | Estándar de metadata y calidad técnica para landings editoriales. **Esta es la fuente del estándar de metadatos abajo.** | ✅ línea 101 |

**Pendiente**: no existe una skill específica de "metadatos / AI-readable"
en la central. Si este estudio se repite en otros proyectos, merece crearse
una; hoy basta con esta nota y con la regla de la referencia de
`big-school-webs`.

## 3. Reglas canónicas heredadas

1. **Kit de Marca ApliArte** (`ingredientes/marca/APLIARTE_BRAND_KIT.md`):
   paleta, tipografías, logotipo maestro (chevron geométrico). Es
   **fuente única de verdad visual**. Si algo en este archivo lo
   contradice, gana el Kit.
2. **Modo claro por defecto + interruptor sol/luna** (regla 3.1).
3. **Cero IA en el frontend** (regla 3.1.bis): este `index.html` ya cumple
   la regla; mantenerlo así en futuras ediciones.
4. **Regla de Oro de Git y Árbol Limpio** (central §): commits
   quirúrgicos, nunca `git add .` ni `git commit -a`, sin `--force`.

## 4. Diagnóstico de metadatos (auditoría 2026-09-22)

Auditado contra la regla *"Metadata completa: título, descripción,
canonical, Open Graph y tarjeta social con URL pública válida"* de
`big-school-webs/references/landing-editorial.md` línea 101.

### 4.1 Lo que ya tiene ✅

- `<meta charset="utf-8">`, viewport, color-scheme, theme-color.
- Bloque favicon completo (SVG + PNG 32/16 + apple-touch-icon 180).
- `<title>` correcto.
- Tipografías canónicas ApliArte.
- HTML semántico: `<header> <nav> <main> <section> <footer> <h1> <h2>`.
- `<html lang="es">`.

### 4.2 Lo que falta ❌

| Elemento | Estado | Impacto |
|---|---|---|
| `<meta name="description">` | falta | SEO on-page y preview de búsqueda |
| `<meta name="author">` | falta | atribución |
| `<meta name="robots">` | falta | directivas de indexación (por defecto `index, follow` si se omite, pero conviene declararlo) |
| `<link rel="canonical">` | falta | consolidar URL canónica |
| **Open Graph** (`og:title`, `og:description`, `og:image`, `og:url`, `og:type`, `og:site_name`, `og:locale`) | falta todo | preview en Facebook, LinkedIn, WhatsApp, Discord, Slack, Telegram |
| **Twitter Card** (`twitter:card`, `twitter:title`, `twitter:description`, `twitter:image`) | falta todo | preview en 𝕏 (Twitter) |
| **JSON-LD Schema.org** (`WebSite` + `Organization`) | falta | legibilidad por IA y rich snippets de Google |
| `robots.txt` | falta | directivas globales para crawlers |
| `sitemap.xml` | falta | ayuda a Google a descubrir todas las secciones |
| `<meta name="theme-color" media="(prefers-color-scheme: dark)">` | falta | barra del navegador en modo oscuro |

### 4.3 Datos que se necesitan antes de implementar

Estos no son del código, son **decisiones de contenido** que solo
Javier puede tomar:

1. **description** (≤ 160 caracteres) — propuesta borrador:
   *"Portal de ingeniería de prompts, factoría de agentes autónomos y
   herramientas open source de ApliArte."*
2. **og:image** — dimensiones recomendadas 1200×630 px. Hoy no existe
   ninguna imagen social propia del proyecto.
3. **JSON-LD Organization** — confirmar si el `publisher` se modela como
   `ApliArte` o como `ErBolamm` (en GitHub aparece como
   `erbolamm/megapromtista`).
4. **Robots** — ¿se quiere permitir indexación completa o restringir
   alguna sección? (Por defecto: todo permitido.)

## 5. Plan propuesto (cuando se apruebe)

Orden de aplicación recomendado para minimizar regresiones:

1. **Bloque metadatos en `<head>`** — description, author, robots,
   canonical, Open Graph, Twitter Card, JSON-LD `WebSite`+`Organization`.
   ≈ 25 líneas nuevas en `<head>`. No toca CSS ni body.
2. **`robots.txt`** mínimo en la raíz,允许 todo y señalando sitemap.
3. **`sitemap.xml`** mínimo listando `/` como única URL.
4. **og:image 1200×630** — generar desde el chevron ApliArte sobre
   fondo azul con la promesa. Bloquea hasta decidir copy.
5. **Theme-color oscuro** — `<meta name="theme-color" media="(prefers-color-scheme: dark)">`
   usando `#303030` del Kit de Marca.

Cada paso se commitea por separado con Conventional Commits. Push y
publicación son decisiones del usuario.

## 6. Recibo de cambios previos

- `feat(web): add ApliArte chevron favicon` — `9e0f172` —
  4 archivos nuevos (`favicon.svg`, `favicon-32x32.png`,
  `favicon-16x16.png`, `apple-touch-icon.png`) + 1 línea en `<head>`.

## 7. Lo que NO hay que hacer

- No crear `package.json`, build pipeline ni dependencias. El sitio es
  estático a propósito.
- No añadir Google Analytics, Tag Manager, ni servicios de terceros que
  rompan la regla 3.1.bis (cero IA en frontend).
- No cambiar el `CNAME` ni la rama de despliegue (`main`) sin
  autorización expresa.
- No inventar certificaciones, métricas, números de usuarios ni
  testimonios.