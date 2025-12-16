# 📅 Fase 6: Schedule & Milestones

**Tiempo estimado:** 20 minutos

## 🎯 Objetivo

Crear un timeline visual del Game Jam con milestones clave, deliverables por día y tracking de progreso para asegurar que el equipo llegue al deadline a tiempo.

---

## 📊 Estructura del Schedule

```
📅 Schedule & Milestones
│
├── 📊 Timeline Overview (visual)
├── 🎯 Milestones (base de datos)
│   ├── Milestone Name
│   ├── Date & Time
│   ├── Deliverables
│   ├── Status
│   └── Notes
├── 📆 Daily Breakdown
└── ⏰ Critical Deadlines
```

---

## 🛠️ Instrucciones Paso a Paso

### Paso 1: Crear Timeline Overview

1. Abre tu página template
2. Busca la sección `## 📅 Schedule & Milestones`
3. Borra el placeholder

### Paso 2: Añadir Timeline Visual

Primero, vamos a crear un timeline visual simple:

```
## 📅 Schedule & Milestones

### ⏰ Timeline Overview

Day 0 (Kickoff)          Day 1 (Foundation)      Day 2 (Core + Polish)
    ↓                         ↓                         ↓
    📋 Planning          🎮 First Playable       ✨ Feature Complete
    │                         │                         │
    ├─ Concept               ├─ Movement              ├─ All features done
    ├─ GDD                   ├─ Basic enemy           ├─ All assets integrated
    └─ Task breakdown        └─ Greybox level         ├─ Testing
                                                       └─ Polish
                                                            │
                                                            ↓
                                                       🎉 SUBMISSION
                                                       [Deadline: XX:XX]

**Para Game Jam de 48h:**

┌─────────────────────────────────────────────────────────────┐
│ Hour 0-3    │ Hour 3-12   │ Hour 12-24  │ Hour 24-36 │ 36-48│
│ Kickoff     │ Foundation  │ Integration │ Content    │Final │
│ Planning    │ Setup + MVP │ Mechanics   │ + Polish   │Push  │
└─────────────────────────────────────────────────────────────┘
  📋 Concept   🎮 Playable    🔧 Features    ✨ Polish   🚀 Ship

**Para Game Jam de 72h (3 días):**

┌─────────────────────────────────────────────────────────────────────┐
│  Day 1         │       Day 2        │       Day 3        │   Final  │
│ Foundation     │  Core Mechanics    │  Content + Polish  │ 6h       │
└─────────────────────────────────────────────────────────────────────┘
  📋 Planning     🎮 First Playable    ✨ Feature Complete  🚀 Submit
  🎨 Prototyping  🔧 Integration       🐛 Bug Fixing        📦 Build
```

### Paso 3: Crear Base de Datos de Milestones

Debajo del timeline visual:

1. Escribe `/database` → **"Database - Inline"**
2. Nombra: `Milestones`

#### Propiedades de Milestones

| Propiedad | Tipo | Configuración |
|-----------|------|---------------|
| **Milestone Name** | Title | (Por defecto) |
| **Target Date** | Date | Include end date: No, Include time: Yes |
| **Status** | Select | 📋 Upcoming, 🔄 In Progress, ✅ Completed, ⚠️ At Risk, 🔴 Missed |
| **Critical** | Checkbox | ¿Es milestone crítico? |
| **Deliverables** | Text | Lista de entregables |
| **Owner** | Person | Responsable principal |
| **Actual Date** | Date | Cuándo realmente se completó |
| **Notes** | Text | Notas sobre el milestone |

#### Configurar Status

- `📋 Upcoming` (Gris)
- `🔄 In Progress` (Azul)
- `✅ Completed` (Verde)
- `⚠️ At Risk` (Amarillo)
- `🔴 Missed` (Rojo)

### Paso 4: Añadir Milestones Pre-definidos

Crea estos milestones para un Game Jam de 48h:

#### Milestone 1: Kickoff Complete

**Target Date:** [Día 0, Hora 3]
**Status:** 📋 Upcoming
**Critical:** ✅

**Deliverables:**
- [ ] GDD completo (80%+)
- [ ] Concepto claro del juego
- [ ] Tareas creadas y priorizadas
- [ ] Repositorio configurado
- [ ] Equipo alineado

**Notes:**
Este milestone es crítico. Sin un plan claro, el resto del jam será caótico.

#### Milestone 2: First Playable

**Target Date:** [Día 1, Hora 24]
**Status:** 📋 Upcoming
**Critical:** ✅

**Deliverables:**
- [ ] Personaje placeholder que se mueve
- [ ] Nivel greybox básico
- [ ] 1 enemigo funcional (básico)
- [ ] Build compilada y compartida
- [ ] Mecánica core #1 funcionando

**Notes:**
Si no tenemos algo jugable al final del día 1, estamos en problemas.

#### Milestone 3: Feature Complete

**Target Date:** [Día 2, Hora 42]
**Status:** 📋 Upcoming
**Critical:** ✅

**Deliverables:**
- [ ] Todas las mecánicas P0 implementadas
- [ ] Todos los assets P0 integrados
- [ ] Nivel(es) completados
- [ ] UI básica funcionando
- [ ] Audio integrado

**Notes:**
Después de este punto: SOLO bug fixing y polish.

#### Milestone 4: Code Freeze

**Target Date:** [Día 2, Hora 45] (3h antes del deadline)
**Status:** 📋 Upcoming
**Critical:** ✅✅✅

**Deliverables:**
- [ ] NO MÁS cambios de código
- [ ] Build final compilada
- [ ] Testing completado
- [ ] Bugs críticos resueltos

**Notes:**
🚨 CRÍTICO: Después de este punto solo builds y submission.

#### Milestone 5: Submission

**Target Date:** [Deadline exacto]
**Status:** 📋 Upcoming
**Critical:** ✅✅✅

**Deliverables:**
- [ ] Build subida a plataforma
- [ ] Página de itch.io completa
- [ ] Screenshots/GIFs subidos
- [ ] Descripción y controles documentados
- [ ] Créditos del equipo
- [ ] Submission confirmada

**Notes:**
El único milestone que NO se puede fallar.

### Paso 5: Daily Breakdown

Debajo de los milestones, añade una sección detallada por día:

```
---

## 📆 Daily Breakdown

### Day 0: Kickoff (Hour 0-3)

**Focus:** Planning and Alignment

**Schedule:**
- **00:00 - 00:30** | Brainstorming del concepto
- **00:30 - 01:30** | Refinamiento y decisión final
- **01:30 - 02:30** | Escritura del GDD
- **02:30 - 03:00** | Task breakdown y asignación

**Key Deliverable:** GDD + Task Board lleno

---

### Day 1: Foundation (Hour 3-24)

**Focus:** Setup and First Playable

#### Hour 3-8: Setup
**Programador:**
- [ ] Proyecto Unity configurado
- [ ] Git setup
- [ ] Movimiento básico

**Modelador:**
- [ ] Placeholder assets
- [ ] Dimensiones correctas

**Animador:**
- [ ] Mixamo placeholder animations

**Designer:**
- [ ] Greybox nivel 1

#### Hour 8-12: Core Mechanics
**Programador:**
- [ ] Sistema de salto
- [ ] Cámara funcional
- [ ] Enemy AI básica

**Modelador:**
- [ ] Personaje principal (60%+)

**Animador:**
- [ ] Rigging si modelo está listo

#### Hour 12-18: Integration
**All:**
- [ ] Integrar assets reales
- [ ] Testing continuo
- [ ] Primeros ajustes

#### Hour 18-24: First Build
**All:**
- [ ] Primera build jugable
- [ ] Main menu básico
- [ ] Testing de equipo
- [ ] Bug log inicial

**Checkpoint:** Build compartida, todos la juegan, feedback documentado

---

### Day 2: Content & Polish (Hour 24-48)

**Focus:** Feature Complete → Polish → Submit

#### Hour 24-30: Wake Up Sprint
- [ ] Fix bugs críticos del día 1
- [ ] Implementar features P1
- [ ] Mejorar juice/feel

#### Hour 30-36: Feature Complete Push
- [ ] TODAS las features P0 y P1 done
- [ ] Todos los assets integrados
- [ ] Audio integrado

#### Hour 36-42: Bug Fixing Marathon
- [ ] Playtesting intensivo
- [ ] Fix bugs 🔴 y 🟠
- [ ] Balance y ajustes

#### Hour 42-45: Final Polish
- [ ] Últimos ajustes de feel
- [ ] Compilar builds finales
- [ ] Testing de builds

#### Hour 45-48: Submission
- [ ] **Hour 45: CODE FREEZE** ⚠️
- [ ] Setup de itch.io page
- [ ] Subir builds
- [ ] Screenshots/GIFs
- [ ] Verificación final
- [ ] **SUBMIT** 🎉

---
```

### Paso 6: Critical Deadlines Section

Al final, añade una sección de deadlines críticos con callouts:

**Instrucciones para crear callouts:**

1. Para el callout de First Playable:
   - Escribe `/callout` y selecciona el ícono 🎯
   - Escribe el contenido:
     ```
     **Milestone:** First Playable
     **Deadline:** Day 1, Hour 24
     **Status:** [Update daily]
     ```
   - Cambia el color a: Azul

2. Para el callout de CODE FREEZE:
   - Escribe `/callout` y selecciona el ícono ⚠️
   - Escribe el contenido:
     ```
     **CODE FREEZE**
     **Deadline:** 3 hours before submission
     **After this:** NO code changes allowed
     ```
   - Cambia el color a: Amarillo/Naranja

3. Para el callout de FINAL SUBMISSION:
   - Escribe `/callout` y selecciona el ícono 🚀
   - Escribe el contenido:
     ```
     **FINAL SUBMISSION**
     **Deadline:** [Fecha y hora exacta]
     **NO EXTENSIONS**
     ```
   - Cambia el color a: Rojo

Luego añade esta sección:

```
---

## 📊 Progress Tracking

**Current Day:** [Día X]
**Hours Remaining:** [XX hours]
**Next Milestone:** [Nombre]
**Status:** 🟢 On Track / 🟡 Needs Attention / 🔴 Behind Schedule

---
```

---

## 💡 Tips de Uso del Schedule

### Durante el Jam

1. **Update diariamente:**
   - Marca milestones completados con ✅
   - Update "Current Day" y "Hours Remaining"
   - Ajusta "Status" si van retrasados

2. **Daily Check-in:**
   - Cada mañana, revisar el schedule
   - Comparar con el progreso real
   - Ajustar prioridades si es necesario

3. **Warning Signs:**
   - Si un milestone crítico se marca "At Risk" → Reunión de emergencia
   - Si van >6h retrasados → Scope cut decision

### Milestones como Motivation

- **Celebra cada milestone completado:**
  - Toma un break de 10 min
  - Reconoce el trabajo del equipo
  - Momentum es importante

### Adaptación en Tiempo Real

Si van retrasados:

```
## 🚨 Scope Adjustment Log

**Date:** Day X, Hour Y
**Reason:** [Por qué ajustamos]

**Cuts:**
- ❌ [Feature que se cortó]
- ❌ [Otro elemento cortado]

**New Focus:**
- ✅ [Prioridad ajustada]
- ✅ [Nueva meta realista]

**Impact on Milestones:**
- Milestone X: Adjusted deliverables
- Milestone Y: Still achievable
```

---

## 🎨 Mejoras Opcionales

### Gantt Chart View

Si quieres un timeline más visual:

1. Crea una vista **Timeline** de la base de datos Milestones
2. Notion lo mostrará como un Gantt chart
3. Útil para ver dependencies visuales

### Countdown Timer en Dashboard

En el Dashboard (Fase 1), puedes vincular al "Hours Remaining":

```
### ⏰ Time Status

**Jam Start:** [Fecha/Hora]
**Current Time:** [Update manual o embed]
**Hours Elapsed:** [X]
**Hours Remaining:** [Y]
**Next Milestone:** [Link a milestone en schedule]
```

### Hourly Checklist (Para Endgame)

En las últimas 6 horas, puedes crear un checklist hora por hora:

```
## ⏰ Final 6 Hours Checklist

### Hour 42-43
- [ ] Compile Windows build
- [ ] Test Windows build
- [ ] Compile Mac build (if applicable)

### Hour 43-44
- [ ] All critical bugs fixed
- [ ] Final playtesting

### Hour 44-45
- [ ] CODE FREEZE
- [ ] Final build ready

### Hour 45-46
- [ ] itch.io page setup
- [ ] Upload builds

### Hour 46-47
- [ ] Screenshots uploaded
- [ ] Description written
- [ ] Controls documented

### Hour 47-48
- [ ] Final verification
- [ ] SUBMIT
- [ ] Celebrate! 🎉
```

---

## ✅ Verificación

Al terminar esta fase, tu Schedule debe tener:

- [x] Timeline visual overview
- [x] Base de datos de Milestones con 5+ milestones
- [x] Daily breakdown detallado
- [x] Critical deadlines destacados
- [x] Progress tracking section
- [x] Status actualizable en tiempo real

---

## 🎯 ¿Qué es un Milestone?

Un **milestone** (hito en español) es un punto de control o evento importante en un proyecto que marca el logro de una meta específica o el fin de una fase.

### Características de un milestone:

1. **No tiene duración** - Es un momento específico en el tiempo, no una tarea que toma horas
2. **Marca progreso significativo** - Representa un logro importante o punto de decisión
3. **Tiene entregables claros** - Define qué debe estar completado en ese momento
4. **Es medible** - Puedes verificar objetivamente si se alcanzó o no

### Ejemplos en un Game Jam:

**❌ NO es un milestone:**
- "Programar el movimiento del jugador" (es una tarea)
- "Modelar assets" (es trabajo continuo)

**✅ SÍ es un milestone:**
- **"First Playable"** - Momento donde tienes algo jugable por primera vez
  - Marca el fin de la fase de setup
  - Entregables: personaje que se mueve, nivel básico, una build

- **"Code Freeze"** - Momento donde dejas de programar
  - Marca el fin del desarrollo activo
  - Después de esto solo builds y submission

### Analogía simple:

Si el desarrollo es un viaje en auto:
- **Tareas** = conducir, llenar gasolina, revisar mapa (acciones continuas)
- **Milestones** = ciudades importantes por las que pasas (puntos de referencia)

### ¿Para qué sirven en tu Game Jam?

Los milestones te ayudan a:
- ✅ Mantener al equipo alineado sobre el progreso
- ✅ Saber si van a tiempo o retrasados
- ✅ Tomar decisiones críticas (como recortar scope)
- ✅ Celebrar logros y mantener motivación

---

## 🚀 Próximo Paso

Con el timeline planificado, completa el workspace con recursos:

👉 **`08_Resources.md`** - Crear la sección de recursos y referencias

---

## 📸 Vista Previa Conceptual

Tu Schedule debería verse así:

```
╔═══════════════════════════════════════════════════════════╗
║         📅 SCHEDULE & MILESTONES                          ║
╠═══════════════════════════════════════════════════════════╣
║                                                           ║
║ Timeline:                                                 ║
║ Day 0      Day 1          Day 2          Submission      ║
║  📋  ────── 🎮  ───────── ✨  ────────────── 🚀          ║
║ Plan     Playable     Complete         SHIP              ║
║                                                           ║
║ ┌──────────────────────────────────────────────┐        ║
║ │ Milestone          │ Date  │ Status          │        ║
║ ├──────────────────────────────────────────────┤        ║
║ │ First Playable     │ Day 1 │ ✅ Completed    │        ║
║ │ Feature Complete   │ Day 2 │ 🔄 In Progress  │        ║
║ │ Code Freeze        │ -3h   │ 📋 Upcoming     │        ║
║ │ Submission         │ 00:00 │ 📋 Upcoming     │        ║
║ └──────────────────────────────────────────────┘        ║
║                                                           ║
║ ⏰ Hours Remaining: 18                                    ║
║ 📊 Status: 🟢 On Track                                    ║
╚═══════════════════════════════════════════════════════════╝
```

---

**¿Completaste el Schedule?** ✅ Continúa con Resources.

---

## 🧭 Navegación

**📍 Estás en:** Fase 6 - Schedule & Milestones

| ⬅️ Anterior | 🏠 Inicio | ➡️ Siguiente |
|------------|----------|-------------|
| [🐛 Bug Log](06_Bug_Log.md) | [🏠 README](README.md) | [📚 Resources](08_Resources.md) |

**🔗 Todas las Guías:**
[Plan](00_PLAN_IMPLEMENTACION.md) • [Setup](01_Setup_Inicial.md) • [Dashboard](02_Dashboard.md) • [GDD](03_GDD.md) • [Tasks](04_Task_Board.md) • [Assets](05_Asset_Tracker.md) • [Bugs](06_Bug_Log.md) • [Schedule](07_Schedule_Milestones.md) • [Resources](08_Resources.md) • [Checklist](CHECKLIST_IMPLEMENTACION.md)

---
