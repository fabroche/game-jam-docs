# ⚙️ Fase 0: Setup Inicial

**Tiempo estimado:** 10 minutos

## 🎯 Objetivo

Crear la estructura base del workspace: una base de datos principal que contendrá todas tus Game Jams, con un template reutilizable.

---

## 📊 Qué vamos a crear

```
Notion Workspace
│
└── 📊 Game Jams (Database)
    │
    ├── Properties (columnas)
    │   ├── Name (título)
    │   ├── Status
    │   ├── Start Date
    │   ├── End Date
    │   ├── Duration
    │   ├── Theme
    │   ├── Team Size
    │   └── Final Submission URL
    │
    └── 🎮 [Template] Game Jam Workspace
        └── [Aquí irá toda la estructura interna]
```

---

## 🛠️ Instrucciones Paso a Paso

### Paso 1: Crear la Base de Datos Principal

1. **Abre Notion** y ve a tu workspace
2. **Crea una nueva página** (presiona `+` o `/page`)
3. **Nombre de la página:** `🎮 Game Jams Archive`
4. **Dentro de esta página**, escribe `/database` y selecciona **"Database - Full page"**
5. **Nombre de la base de datos:** `Game Jams`

### Paso 2: Configurar Propiedades de la Base de Datos

Ahora vamos a añadir las columnas (propiedades) que necesitamos:

#### Propiedades Básicas

| Propiedad | Tipo | Configuración |
|-----------|------|---------------|
| **Name** | Title | (Ya existe por defecto) |
| **Status** | Select | Opciones: Planning, In Progress, Completed, Submitted |
| **Start Date** | Date | Include time: No |
| **End Date** | Date | Include time: No |
| **Duration** | Formula | `dateBetween(prop("End Date"), prop("Start Date"), "hours")` |
| **Theme** | Text | - |
| **Team Size** | Number | - |
| **Platform** | Select | Opciones: itch.io, GameJolt, Ludum Dare, Global Game Jam, etc. |
| **Final Build URL** | URL | - |
| **Submission URL** | URL | - |
| **Final Score/Ranking** | Number | (Para después del jam) |

#### Cómo añadir cada propiedad:

1. Haz clic en el **"+"** a la derecha de las columnas existentes
2. Selecciona el **tipo** de propiedad
3. Escribe el **nombre**
4. Para **Select**, añade las opciones haciendo clic en "Edit property" → "Add an option"

### Paso 3: Crear la Primera Entrada de Ejemplo

1. Haz clic en **"+ New"** en la base de datos
2. Dale un nombre temporal: `[TEMPLATE] Game Jam Workspace`
3. **No llenes los datos aún**, solo crea la página vacía
4. **Abre esta página** haciendo clic en ella

---

## 📋 Template de Página Interna

Dentro de la página que acabas de crear (`[TEMPLATE] Game Jam Workspace`), vamos a crear la estructura que se reutilizará para cada jam.

### Estructura de la Página Template

Copia y pega esto en tu página de Notion:

```
# 🎮 [Nombre del Game Jam]

---

## 📊 Quick Stats

**Status:** [Select de la DB]
**Dates:** [Start] → [End]
**Theme:** [Theme de la DB]
**Team:** [Team Size] personas
**Platform:** [Platform de la DB]

---

## 📑 Table of Contents

- 📄 [Dashboard](#dashboard)
- 📋 [Game Design Document](#gdd)
- ✅ [Task Board](#tasks)
- 📦 [Asset Tracker](#assets)
- 🐛 [Bug Log](#bugs)
- 📅 [Schedule & Milestones](#schedule)
- 📚 [Resources](#resources)

---

<a id="dashboard"></a>
## 📄 Dashboard

[Aquí irá el dashboard - Fase 1]

---

<a id="gdd"></a>
## 📋 Game Design Document

[Aquí irá el GDD - Fase 2]

---

<a id="tasks"></a>
## ✅ Task Board

[Aquí irá el Task Board - Fase 3]

---

<a id="assets"></a>
## 📦 Asset Tracker

[Aquí irá el Asset Tracker - Fase 4]

---

<a id="bugs"></a>
## 🐛 Bug Log

[Aquí irá el Bug Log - Fase 5]

---

<a id="schedule"></a>
## 📅 Schedule & Milestones

[Aquí irá el Schedule - Fase 6]

---

<a id="resources"></a>
## 📚 Resources

[Aquí irá Resources - Fase 7]

---

## 🎉 Post-Jam

### Retrospective
**What went well:**
-

**What could be improved:**
-

**Lessons learned:**
-

### Metrics
- Time spent:
- Lines of code:
- Assets created:
- Bugs fixed:
- Final ranking/score:
```

---

## 💾 Convertir en Template

Para que puedas reutilizar esta estructura en cada nueva Game Jam:

### Opción A: Duplicar Manualmente
Cada vez que empieces una nueva jam:
1. Duplica la página template (`⋮` → `Duplicate`)
2. Renombra con el nombre de la nueva jam
3. Llena los datos específicos

### Opción B: Template de Notion (Recomendado)
1. Ve a la base de datos "Game Jams"
2. Haz clic en el menú `⌄` junto a "New"
3. Selecciona **"+ New template"**
4. Nombra el template: `Game Jam Template`
5. Copia toda la estructura que creamos arriba
6. Guarda

Ahora cada vez que crees un nuevo registro, podrás elegir este template.

---

## ✅ Verificación

Al terminar esta fase, deberías tener:

- [x] Base de datos "Game Jams" con todas las propiedades
- [x] Una página template con la estructura básica
- [x] Table of Contents que funciona (links internos)
- [x] Secciones marcadas para las próximas fases

---

## 🎨 Personalización (Opcional)

### Añadir un Cover y Icon
1. Abre la página template
2. Haz clic en **"Add cover"** → Elige una imagen de videojuegos
3. Haz clic en **"Add icon"** → Elige 🎮

### Añadir Colores a Status
1. En la base de datos, haz clic en la propiedad **"Status"**
2. Haz clic en cada opción para cambiar su color:
   - Planning: Gris
   - In Progress: Azul
   - Completed: Verde
   - Submitted: Morado

---

## 🚀 Próximo Paso

Ahora que tienes la estructura base, continúa con:

👉 **`02_Dashboard.md`** - Crear el Dashboard principal

---

## 💡 Tips

- **Nombra bien tus jams:** Usa formato `YYYY-MM - [Nombre del Jam]` para orden cronológico
  - Ejemplo: `2025-01 - Global Game Jam 2025`
- **No borres el template:** Siempre duplica, nunca edites el template directamente
- **Backups:** Notion hace backups automáticos, pero puedes exportar tu workspace periódicamente

---

**¿Completaste esta fase?** ✅ Marca este archivo como leído y continúa con el Dashboard.

---

## 🧭 Navegación

**📍 Estás en:** Fase 0 - Setup Inicial

| ⬅️ Anterior | 🏠 Inicio | ➡️ Siguiente |
|------------|----------|-------------|
| [📋 Plan](00_PLAN_IMPLEMENTACION.md) | [🏠 README](README.md) | [📄 Dashboard](02_Dashboard.md) |

**🔗 Todas las Guías:**
[Plan](00_PLAN_IMPLEMENTACION.md) • [Setup](01_Setup_Inicial.md) • [Dashboard](02_Dashboard.md) • [GDD](03_GDD.md) • [Tasks](04_Task_Board.md) • [Assets](05_Asset_Tracker.md) • [Bugs](06_Bug_Log.md) • [Schedule](07_Schedule_Milestones.md) • [Resources](08_Resources.md) • [Checklist](CHECKLIST_IMPLEMENTACION.md)

---
