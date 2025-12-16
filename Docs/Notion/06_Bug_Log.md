# 🐛 Fase 5: Bug Log

**Tiempo estimado:** 15 minutos

## 🎯 Objetivo

Crear un sistema de tracking de bugs vinculado con GitHub Issues, con priorización clara y información técnica detallada para facilitar el debugging.

---

## 📊 Estructura del Bug Log

```
🐛 Bug Log
│
├── 📊 Base de Datos: "Bugs"
│   ├── Propiedades
│   │   ├── Bug Title (título)
│   │   ├── Severity (select)
│   │   ├── Status (select)
│   │   ├── Assignee (persona)
│   │   ├── Found By (persona)
│   │   ├── Category (select)
│   │   ├── Platform (select)
│   │   ├── GitHub Issue (url)
│   │   ├── Fixed In Build (text)
│   │   └── Created (created time)
│   │
│   └── Vistas
│       ├── 🔥 Critical Bugs
│       ├── 📊 All Bugs (tabla)
│       ├── ✅ By Status
│       └── 📱 By Platform
```

---

## 🛠️ Instrucciones Paso a Paso

### Paso 1: Crear la Base de Datos de Bugs

1. Abre tu página template
2. Busca la sección `## 🐛 Bug Log`
3. Borra el placeholder
4. Escribe `/database` → **"Database - Inline"**
5. Nombra la base de datos: `Bugs`

### Paso 2: Configurar Propiedades

#### Lista Completa de Propiedades

| Propiedad | Tipo | Configuración |
|-----------|------|---------------|
| **Bug Title** | Title | (Por defecto) |
| **Severity** | Select | 🔴 Critical, 🟠 High, 🟡 Medium, 🟢 Low |
| **Status** | Select | 📋 New, 🔍 Investigating, 🔄 In Progress, ✅ Fixed, 🚫 Won't Fix |
| **Assignee** | Person | Quien lo va a arreglar |
| **Found By** | Person | Quien lo encontró |
| **Category** | Select | Gameplay, UI, Graphics, Audio, Performance, Other |
| **Platform** | Select | Windows, Mac, Linux, WebGL, All |
| **GitHub Issue** | URL | Link al issue de GitHub |
| **Fixed In Build** | Text | Versión donde se arregló |
| **Created** | Created time | (Automático) |
| **Priority** | Formula | (Calculado basado en Severity) |

#### Configurar Select: "Severity"

Añade estas opciones:
- `🔴 Critical` (Rojo) - Game breaking, bloquea juego
- `🟠 High` (Naranja) - Afecta jugabilidad significativamente
- `🟡 Medium` (Amarillo) - Afecta experiencia pero no crítico
- `🟢 Low` (Verde) - Visual menor, polish

#### Configurar Select: "Status"

Añade estas opciones:
- `📋 New` (Gris)
- `🔍 Investigating` (Azul claro)
- `🔄 In Progress` (Azul)
- `🧪 Testing Fix` (Amarillo)
- `✅ Fixed` (Verde)
- `🚫 Won't Fix` (Rojo oscuro)
- `📝 Duplicate` (Gris oscuro)

#### Configurar Select: "Category"

Añade estas opciones:
- `🎮 Gameplay`
- `🖥️ UI`
- `🎨 Graphics`
- `🎵 Audio`
- `⚡ Performance`
- `🔧 Build/Deploy`
- `📦 Other`

#### Configurar Select: "Platform"

Añade estas opciones:
- `🪟 Windows`
- `🍎 Mac`
- `🐧 Linux`
- `🌐 WebGL`
- `📱 All Platforms`

### Paso 3: Crear Vistas

#### Vista 1: Critical Bugs (Principal)

1. Click en vista → **"Table"**
2. **Nombre:** `🔥 Critical & High`
3. **Filter:** `Severity` → `Is` → `🔴 Critical` OR `🟠 High`
4. **Filter:** `Status` → `Is not` → `✅ Fixed`
5. **Sort by:** Severity (Ascending), Created (Ascending)

**Uso:** Focus en bugs que bloquean el desarrollo

#### Vista 2: All Bugs

1. `+ Add a view` → **"Table"**
2. **Nombre:** `📊 All Bugs`
3. **No filters**
4. **Sort by:** Status, Severity

**Uso:** Vista completa de todos los bugs

#### Vista 3: By Status

1. `+ Add a view` → **"Board"**
2. **Nombre:** `✅ By Status`
3. **Group by:** `Status`

**Uso:** Pipeline de bug fixing

#### Vista 4: Active Bugs Only

1. `+ Add a view` → **"Table"**
2. **Nombre:** `⚠️ Active`
3. **Filter:** `Status` → `Is not` → `✅ Fixed`
4. **Filter:** `Status` → `Is not` → `🚫 Won't Fix`
5. **Filter:** `Status` → `Is not` → `📝 Duplicate`

**Uso:** Solo bugs que requieren atención

---

## 📋 Template para Reportar Bugs

Cuando añadas un bug, usa esta estructura en la página interna:

```
## 🐛 Bug Description

[Descripción clara y concisa del problema]

---

## 📍 Steps to Reproduce

1. [Paso 1]
2. [Paso 2]
3. [Paso 3]
4. [Bug occurs]

**Reproducibility:** Always / Sometimes / Rare

---

## ❌ Expected Behavior

[Qué debería pasar]

---

## ⚠️ Actual Behavior

[Qué está pasando actualmente]

---

## 📸 Evidence

### Screenshots

[Añadir screenshots aquí]

### Video

[Añadir video/GIF si aplica]

### Console Output

[Pegar error logs de Unity Console aquí]

---

## 🔍 Technical Details

| Detail | Value |
|--------|-------|
| **Unity Version** | [Ej: 6.0.0] |
| **Platform** | [Windows/Mac/Linux/WebGL] |
| **Build Type** | [Development/Release] |
| **Scene** | [Nombre de la escena donde ocurre] |
| **Affected GameObject** | [Si aplica] |
| **Script** | [Script relacionado] |

---

## 💡 Possible Cause

[Hipótesis sobre qué está causando el bug]

**Related Code:**
// Código sospechoso o relacionado en C#

---

## 🔧 Attempted Fixes

- [ ] [Intento 1] - [Resultado]
- [ ] [Intento 2] - [Resultado]

---

## ✅ Fix Verification Checklist

Una vez el bug esté arreglado, verificar:

- [ ] Bug no se reproduce siguiendo los pasos originales
- [ ] No se introdujeron nuevos bugs
- [ ] Funciona en todas las plataformas afectadas
- [ ] Code review realizado
- [ ] Commit pusheado a GitHub
- [ ] GitHub Issue cerrado

---

## 📝 Resolution Notes

**Root Cause:** [Qué causó el bug]

**Fix Applied:** [Qué se hizo para arreglarlo]

**Files Modified:**
- `[Path/to/file1.cs]`
- `[Path/to/file2.cs]`

**Fixed in Build:** [Version number]

---

## 🔗 Related Issues

- Related to: [Link a otros bugs similares]
- Duplicate of: [Link si es duplicado]

---

## 📝 Additional Notes

[Cualquier otra información relevante]
```

---

## 💡 Tips de Uso del Bug Log

### Durante el Testing

1. **Reporta todo:**
   - Incluso bugs pequeños
   - Es mejor tener un "Won't Fix" que perder track de un bug

2. **Asigna Severity correctamente:**
   - 🔴 **Critical:** Crash, no se puede jugar, pérdida de datos
   - 🟠 **High:** Mecánica principal no funciona, experiencia muy afectada
   - 🟡 **Medium:** Feature secundaria no funciona, bug notable pero workaround existe
   - 🟢 **Low:** Visual/audio menor, typo, polish

3. **Steps to Reproduce claros:**
   - Debe ser reproducible por otra persona siguiendo los pasos
   - Si es random, indica la frecuencia (50% de las veces, etc.)

### Durante el Bug Fixing

1. **Prioriza por Severity:**
   - Fix 🔴 Critical primero, siempre
   - Luego 🟠 High
   - 🟡 Medium y 🟢 Low solo si hay tiempo

2. **Update Status en tiempo real:**

   📋 New → 🔍 Investigating → 🔄 In Progress → 🧪 Testing → ✅ Fixed

3. **Documenta el fix:**
   - Qué causó el bug (para aprender)
   - Qué se cambió
   - Testing realizado

### Last 24 Hours Rule

En las últimas 24 horas del jam:

⚠️ **Solo fixear bugs 🔴 Critical y 🟠 High**

Los bugs 🟡 Medium y 🟢 Low se marcan como "Won't Fix" o se dejan para post-jam.

Razón: Cada cambio puede introducir nuevos bugs. Minimizar riesgo.

---

## 🔗 Integración con GitHub Issues

### Workflow Recomendado

1. **Bug encontrado:**
   - Crear entrada en Notion Bug Log primero
   - Llenar toda la información

2. **Si es bug técnico (código):**
   - Crear GitHub Issue
   - Copiar información desde Notion
   - Añadir link del GitHub Issue en Notion

3. **Formato del GitHub Issue:**

```
## 🐛 Bug Report

**From Notion:** [Link al Notion bug]

## Description
[Copiar de Notion]

## Steps to Reproduce
[Copiar de Notion]

## Expected vs Actual
[Copiar de Notion]

## Technical Details
[Copiar de Notion]

## Labels
`bug` `🔴 P0-critical` (según severity)

## Assignee
@username
```

4. **Al fixear:**
   - Commit con referencia: `fix: player falling through floor (#23)`
   - Cerrar GitHub Issue
   - Actualizar Notion a "✅ Fixed"
   - Anotar en qué build se arregló

---

## 🎨 Mejoras Opcionales

### Añadir Property: "Time to Fix"

Para retrospectives:

- Tipo: **Number**
- Descripción: Horas que tomó arreglar
- Útil para aprender qué tipos de bugs toman más tiempo

### Añadir Tags

Tipo: **Multi-select**

Opciones:
- `🔥 Game Breaking`
- `🎯 Affects Core Loop`
- `✨ Polish`
- `🔄 Regression` (Bug que ya se había arreglado)
- `📦 External` (Bug de un asset externo/plugin)

### Dashboard de Bugs

Puedes crear un mini-dashboard al inicio de la sección:

```
## 🐛 Bug Log

### 📊 Bug Statistics

**Total Bugs:** [Cuenta manualmente o con fórmula]
**Active:** [Bugs no Fixed]
**Critical:** [Bugs 🔴]
**Fixed Today:** [X]

---

[Luego la base de datos]
```

---

## ✅ Verificación

Al terminar esta fase, tu Bug Log debe tener:

- [x] Base de datos con todas las propiedades
- [x] Vista de Critical & High bugs
- [x] Vista de todos los bugs
- [x] Vista By Status (board)
- [x] Template para reportar bugs consistentemente
- [x] Severities configuradas con colores
- [x] Integración lista con GitHub Issues

---

## 🚀 Próximo Paso

Con el sistema de bugs listo, ahora planifica el timeline:

👉 **`07_Schedule_Milestones.md`** - Crear el schedule y milestones

---

## 📸 Vista Previa Conceptual

Tu Bug Log debería verse así:

```
╔═══════════════════════════════════════════════════════════╗
║              🐛 BUG LOG (CRITICAL & HIGH)                 ║
╠═══════════════════════════════════════════════════════════╣
║ Title                    │ Severity │ Status    │ Assignee║
║──────────────────────────┼──────────┼───────────┼─────────║
║ Player falls through     │ 🔴 Crit  │ 🔄 Fixing │ @Dev1   ║
║ floor on jump            │          │           │         ║
║──────────────────────────┼──────────┼───────────┼─────────║
║ Attack animation not     │ 🟠 High  │ 📋 New    │ @Dev2   ║
║ playing                  │          │           │         ║
║──────────────────────────┼──────────┼───────────┼─────────║
║ UI button disappears on  │ 🟠 High  │🔍 Invest  │ @Dev1   ║
║ resolution change        │          │           │         ║
╚═══════════════════════════════════════════════════════════╝
```

---

**¿Completaste el Bug Log?** ✅ Continúa con Schedule & Milestones.

---

## 🧭 Navegación

**📍 Estás en:** Fase 5 - Bug Log

| ⬅️ Anterior | 🏠 Inicio | ➡️ Siguiente |
|------------|----------|-------------|
| [📦 Asset Tracker](05_Asset_Tracker.md) | [🏠 README](README.md) | [📅 Schedule](07_Schedule_Milestones.md) |

**🔗 Todas las Guías:**
[Plan](00_PLAN_IMPLEMENTACION.md) • [Setup](01_Setup_Inicial.md) • [Dashboard](02_Dashboard.md) • [GDD](03_GDD.md) • [Tasks](04_Task_Board.md) • [Assets](05_Asset_Tracker.md) • [Bugs](06_Bug_Log.md) • [Schedule](07_Schedule_Milestones.md) • [Resources](08_Resources.md) • [Checklist](CHECKLIST_IMPLEMENTACION.md)

---
