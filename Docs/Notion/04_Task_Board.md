# ✅ Fase 3: Task Board (Kanban)

**Tiempo estimado:** 40 minutos

## 🎯 Objetivo

Crear un sistema Kanban completo para gestión de tareas durante la Game Jam, con múltiples vistas, propiedades detalladas y templates reutilizables.

---

## 📊 Estructura del Task Board

```
✅ Task Board
│
├── 📊 Base de Datos: "Tasks"
│   ├── Propiedades
│   │   ├── Name (título)
│   │   ├── Assignee (persona)
│   │   ├── Role (select)
│   │   ├── Priority (select)
│   │   ├── Status (select)
│   │   ├── Estimate (number)
│   │   ├── Sprint (select)
│   │   ├── Tags (multi-select)
│   │   └── GitHub Link (url)
│   │
│   └── Vistas
│       ├── 📋 Kanban Board (principal)
│       ├── 📊 Table View (detallada)
│       ├── 📅 Calendar View
│       └── 👤 By Assignee
│
└── 📝 Templates de Tareas
    ├── Programming Task
    ├── Art Task
    ├── Design Task
    └── Bug Fix
```

---

## 🛠️ Instrucciones Paso a Paso

### Paso 1: Crear la Base de Datos de Tareas

1. Abre tu página template
2. Busca la sección `## ✅ Task Board`
3. Borra el placeholder
4. Escribe `/database` → Selecciona **"Database - Inline"**
5. Nombra la base de datos: `Tasks`

### Paso 2: Configurar Propiedades

Ahora vamos a añadir todas las propiedades necesarias:

#### Lista Completa de Propiedades

| Propiedad | Tipo | Configuración |
|-----------|------|---------------|
| **Task Name** | Title | (Por defecto) |
| **Assignee** | Person | - |
| **Role** | Select | Programador, Modelador, Animador, Designer |
| **Priority** | Select | 🔴 P0-Critical, 🟠 P1-High, 🟡 P2-Medium, 🟢 P3-Low |
| **Status** | Select | Backlog, To Do, In Progress, Testing, Done |
| **Estimate** | Number | (en horas) |
| **Sprint** | Select | Day 1, Day 2, Day 3, Day 4, Day 5, Polish |
| **Tags** | Multi-select | Core, Polish, Bug, Feature, Art, Code, Audio, Blocked |
| **GitHub Link** | URL | - |
| **Created** | Created time | (automático) |
| **Completed** | Checkbox | - |

#### Cómo Configurar Select: "Status"

1. Añade propiedad → Select → Nombra "Status"
2. Añade estas opciones con colores:
   - `Backlog` (Gris)
   - `To Do` (Azul claro)
   - `In Progress` (Azul)
   - `Testing` (Amarillo)
   - `Done` (Verde)

#### Cómo Configurar Select: "Priority"

1. Añade propiedad → Select → Nombra "Priority"
2. Añade estas opciones:
   - `🔴 P0-Critical` (Rojo)
   - `🟠 P1-High` (Naranja)
   - `🟡 P2-Medium` (Amarillo)
   - `🟢 P3-Low` (Verde)

#### Cómo Configurar Select: "Role"

1. Añade propiedad → Select → Nombra "Role"
2. Añade estas opciones:
   - `Programador` (Azul)
   - `Modelador` (Morado)
   - `Animador` (Rosa)
   - `Designer` (Verde)

#### Cómo Configurar Multi-select: "Tags"

1. Añade propiedad → Multi-select → Nombra "Tags"
2. Añade estas opciones:
   - `Core` (Rojo)
   - `Polish` (Verde)
   - `Bug` (Naranja)
   - `Feature` (Azul)
   - `Art` (Morado)
   - `Code` (Azul oscuro)
   - `Audio` (Amarillo)
   - `Blocked` (Rojo oscuro)

### Paso 3: Crear Vistas

Ahora vamos a crear diferentes vistas de la misma base de datos:

#### Vista 1: Kanban Board (Principal)

1. En tu base de datos, haz clic en el botón de vista (arriba a la izquierda)
2. Selecciona **"Board"**
3. **Group by:** `Status`
4. **Nombre de la vista:** `📋 Kanban`

**Configuración adicional:**
- Click en `⋮` de la vista → Properties
- Muestra: Assignee, Priority, Estimate, Tags
- Oculta: Created, Completed

#### Vista 2: Table View

1. Haz clic en `+ Add a view`
2. Selecciona **"Table"**
3. **Nombre:** `📊 All Tasks`

**Configuración:**
- Muestra todas las propiedades
- **Sort by:** Priority (Ascending), luego Status
- Útil para overview completo

#### Vista 3: Calendar View

1. `+ Add a view` → **"Calendar"**
2. **Nombre:** `📅 Timeline`
3. **Show calendar by:** `Created` (o Sprint si prefieres)

**Uso:** Ver distribución temporal de tareas

#### Vista 4: By Assignee

1. `+ Add a view` → **"Board"**
2. **Nombre:** `👤 By Person`
3. **Group by:** `Assignee`

**Uso:** Ver qué está haciendo cada miembro del equipo

#### Vista 5: By Priority

1. `+ Add a view` → **"Board"**
2. **Nombre:** `🔥 By Priority`
3. **Group by:** `Priority`
4. **Filter:** Status is not "Done"

**Uso:** Focus en tareas críticas

### Paso 4: Crear Templates de Tareas

Los templates te permiten crear tareas pre-configuradas con estructura.

#### Template 1: Programming Task

1. En la base de datos, click en `⌄` junto a "New"
2. Click en **"+ New template"**
3. **Nombre del template:** `💻 Programming Task`

**Contenido del template:**

```
## 📝 Description
[Descripción detallada de la tarea de programación]

## ✅ Acceptance Criteria
- [ ] Criterio 1
- [ ] Criterio 2
- [ ] Criterio 3

## 🔗 Dependencies
- Depende de: [TASK-XXX]
- Bloquea: [TASK-XXX]

## 📦 Technical Details

### Implementation Notes
// Notas técnicas o pseudocódigo en C#

### Files to Modify
- `Assets/Scripts/[File].cs`
-

### Testing Checklist
- [ ] Unit tests pass
- [ ] Funciona en build
- [ ] No hay warnings/errors

## 🐛 Known Issues
-

## 📝 Notes
[Notas adicionales]
```

**Propiedades por defecto:**
- Role: `Programador`
- Tags: `Code`, `Feature`

#### Template 2: Art Task

1. Crear nuevo template: `🎨 Art Task`

**Contenido:**

```
## 📝 Description
[Descripción del asset a crear]

## ✅ Deliverables
- [ ] Modelo base
- [ ] Texturas
- [ ] Exportado a Unity

## 🎨 Specifications

### Technical Requirements
- **Poly count:** <5k triángulos
- **Texture size:** 1024x1024
- **Format:** FBX

### Style Guidelines
- Paleta de colores: [Referencia]
- Estilo: [Low-poly / Realistic / etc.]

## 📸 References
[Añadir imágenes de referencia]

## 📦 Assets Location
**Blender file:** `[Path]`
**Exported to:** `Assets/Models/[Name].fbx`

## ✅ Checklist
- [ ] Modelo completado
- [ ] UVs unwrapped
- [ ] Texturas aplicadas
- [ ] Exportado correctamente
- [ ] Testeado en Unity

## 📝 Notes
[Añadir notas adicionales]
```

**Propiedades por defecto:**
- Role: `Modelador` o `Animador`
- Tags: `Art`

#### Template 3: Design Task

1. Crear nuevo template: `🎮 Design Task`

**Contenido:**

```
## 📝 Description
[Descripción de la tarea de diseño]

## 🎯 Objective
[Qué problema resuelve esta feature/mecánica]

## ✅ Acceptance Criteria
- [ ] Criterio 1
- [ ] Criterio 2

## 🎮 Gameplay Details

### Mechanics
[Descripción detallada de la mecánica]

### Controls (if applicable)
- [Key]: [Action]

### Balancing
- [Stat]: [Value]

## 📋 Implementation Notes for Team
**Para Programador:**
-

**Para Artista:**
-

## 🧪 Testing Plan
- [ ] Test scenario 1
- [ ] Test scenario 2

## 📝 Notes
[Añadir notas adicionales]
```

**Propiedades por defecto:**
- Role: `Designer`
- Tags: `Design`, `Feature`

#### Template 4: Bug Fix

1. Crear nuevo template: `🐛 Bug Fix`

**Contenido:**

```
## 🐛 Bug Description
[Descripción clara del bug]

## 📍 Steps to Reproduce
1.
2.
3.

## ❌ Expected Behavior
[Qué debería pasar]

## ⚠️ Actual Behavior
[Qué está pasando]

## 📸 Screenshots/Video
[Si aplica]

## 🔍 Possible Cause
[Hipótesis sobre la causa]

## ✅ Fix Checklist
- [ ] Bug identificado
- [ ] Fix implementado
- [ ] Testeado
- [ ] No se introdujeron nuevos bugs

## 📝 Notes
[Añadir notas adicionales]
```

**Propiedades por defecto:**
- Tags: `Bug`
- Priority: `🟠 P1-High` (ajustar según severidad)

---

## 📋 Template para Añadir Tareas Rápidas

Cuando añades tareas durante el jam, usa esta convención:

**Nombre de tarea:** `[TASK-XXX] Descripción Clara`

Ejemplos:
- `[TASK-001] Implementar movimiento del jugador`
- `[TASK-002] Modelar personaje principal`
- `[TASK-003] Animar ciclo de caminar`
- `[TASK-004] Diseñar nivel 1`

Esto facilita referenciar tareas entre Notion y GitHub.

---

## 🎨 Configuraciones Avanzadas

### Filtros Útiles

#### Filtro: "Mis Tareas"

1. Crea una nueva vista: `👤 My Tasks`
2. **Filter:** `Assignee` → `Contains` → `[Tu nombre]`
3. **Filter:** `Status` → `Is not` → `Done`

#### Filtro: "Tareas Críticas"

1. Crea una nueva vista: `🚨 Critical`
2. **Filter:** `Priority` → `Is` → `🔴 P0-Critical`
3. **Filter:** `Status` → `Is not` → `Done`

#### Filtro: "Bloqueadas"

1. Crea una nueva vista: `🔒 Blocked`
2. **Filter:** `Tags` → `Contains` → `Blocked`

### Ordenamiento Recomendado

Para la vista Kanban principal:
- **Sort:** Priority (Ascending) - Las P0 arriba
- **Sub-sort:** Created (Ascending) - Las más antiguas primero

---

## 💡 Tips de Uso del Task Board

### Durante el Kickoff

1. **Brainstorm de tareas** (30 min):
   - Todo el equipo crea tareas en "Backlog"
   - No se preocupen por detalles, solo capturar TODO
   - Usar templates apropiados

2. **Priorización** (30 min):
   - Game Designer asigna prioridades (P0/P1/P2/P3)
   - Tareas P0 = MVP absoluto
   - Tareas P3 = "Nice to have"

3. **Asignación** (15 min):
   - Asignar tareas a personas
   - Mover P0 y P1 a "To Do"
   - Planificar sprints por día

### Durante el Desarrollo

1. **Actualiza en tiempo real:**
   - Cuando empieces una tarea → Mueve a "In Progress"
   - Cuando termines → Mueve a "Testing"
   - Después de testing → Mueve a "Done"

2. **Limit Work in Progress:**
   - Idealmente 1-2 tareas en "In Progress" por persona
   - Terminar antes de empezar otra

3. **Daily Standup:**
   - Abre la vista "By Person"
   - Cada uno habla sobre sus tareas
   - Actualiza status en vivo

### Integración con GitHub

Cuando crees un GitHub Issue:
1. Copia el URL del issue
2. Pégalo en la propiedad "GitHub Link" de la tarea en Notion
3. En el GitHub Issue, añade un link al Notion task

```
Design Doc: [Notion Task](url-de-notion)
```

---

## ✅ Verificación

Al terminar esta fase, tu Task Board debe tener:

- [x] Base de datos con todas las propiedades configuradas
- [x] Vista Kanban principal funcionando
- [x] Al menos 3 vistas adicionales (Table, Calendar, By Assignee)
- [x] 4 templates de tareas (Programming, Art, Design, Bug)
- [x] Filtros y ordenamiento configurados
- [x] Colores asignados a Status y Priority

---

## 🚀 Próximo Paso

Con el sistema de tareas listo, ahora gestiona tus assets:

👉 **`05_Asset_Tracker.md`** - Crear el tracker de assets

---

## 📸 Vista Previa Conceptual

Tu Task Board debería verse así:

```
╔═══════════════════════════════════════════════════════════╗
║                  ✅ TASK BOARD (KANBAN)                   ║
╠═══════════════════════════════════════════════════════════╣
║                                                           ║
║ Backlog │ To Do │ In Progress │ Testing │ Done           ║
║─────────┼───────┼─────────────┼─────────┼──────          ║
║         │🔴[001]│ 🟠[005]     │ 🟡[012] │ ✅[002]        ║
║ 🟢[020] │Player │ Enemy AI    │ Jump    │ Setup          ║
║ Cutscene│Movement│ @Programmer │ @Prog   │ @Designer      ║
║         │@Prog  │             │         │                ║
║         │       │ 🟠[007]     │         │ ✅[003]        ║
║ 🟢[021] │🔴[004]│ Character   │         │ Repository     ║
║ Polish  │Combat │ Model       │         │ @All           ║
║         │@Prog  │ @Modeler    │         │                ║
╚═══════════════════════════════════════════════════════════╝
```

---

**¿Completaste el Task Board?** ✅ Continúa con el Asset Tracker.

---

## 🧭 Navegación

**📍 Estás en:** Fase 3 - Task Board

| ⬅️ Anterior | 🏠 Inicio | ➡️ Siguiente |
|------------|----------|-------------|
| [📋 GDD](03_GDD.md) | [🏠 README](README.md) | [📦 Asset Tracker](05_Asset_Tracker.md) |

**🔗 Todas las Guías:**
[Plan](00_PLAN_IMPLEMENTACION.md) • [Setup](01_Setup_Inicial.md) • [Dashboard](02_Dashboard.md) • [GDD](03_GDD.md) • [Tasks](04_Task_Board.md) • [Assets](05_Asset_Tracker.md) • [Bugs](06_Bug_Log.md) • [Schedule](07_Schedule_Milestones.md) • [Resources](08_Resources.md) • [Checklist](CHECKLIST_IMPLEMENTACION.md)

---
