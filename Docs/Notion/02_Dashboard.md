# 📄 Fase 1: Dashboard / Home

**Tiempo estimado:** 20 minutos

## 🎯 Objetivo

Crear un dashboard que sirva como "command center" de tu Game Jam: información clave de un vistazo, countdown timer, quick links y contactos del equipo.

---

## 📊 Componentes del Dashboard

```
📄 Dashboard
│
├── ⏰ Countdown Timer
├── 📊 Progress Overview
├── 🔗 Quick Links
├── 👥 Team Contacts
└── 🎯 Current Sprint Goals
```

---

## 🛠️ Instrucciones Paso a Paso

### Paso 1: Ubicar la Sección Dashboard

1. Abre tu página template: `[TEMPLATE] Game Jam Workspace`
2. Busca la sección `## 📄 Dashboard`
3. Borra el placeholder `[Aquí irá el dashboard - Fase 1]`

### Paso 2: Crear el Countdown Timer

Notion no tiene countdown nativo, pero podemos usar estas alternativas:

#### Opción A: Embed de Countdown Externo

```markdown
### ⏰ Time Remaining

/embed → Pega este URL: https://www.tickcounter.com/countdown/[tu-countdown-id]
```

**Cómo crear tu countdown:**
1. Ve a https://www.tickcounter.com/
2. Crea un countdown con tu fecha límite
3. Copia el URL del embed
4. En Notion: `/embed` → Pega el URL

#### Opción B: Cálculo Manual con Fórmula

Si no quieres usar embeds externos, simplemente muestra las fechas:

```markdown
### ⏰ Timeline

**Start:** [Fecha de inicio]
**Deadline:** [Fecha límite]
**Status:** [Días restantes - calcular manualmente o con @mention a la propiedad]
```

### Paso 3: Progress Overview

Vamos a crear una sección que muestre el progreso general:

```markdown
### 📊 Progress Overview

#### By Category
- **Design:** ⬜⬜⬜⬜⬜ 0%
- **Programming:** ⬜⬜⬜⬜⬜ 0%
- **Art:** ⬜⬜⬜⬜⬜ 0%
- **Audio:** ⬜⬜⬜⬜⬜ 0%

#### Tasks Status
- ✅ Done: 0
- 🔄 In Progress: 0
- 📋 To Do: 0
- 🔴 Blocked: 0

**Overall Progress:** 0% → [Actualizar diariamente]
```

**Tip:** Usa estos emojis para las barras de progreso:
- Vacío: ⬜
- Lleno: ⬛ o 🟩
- Medio: 🟨

Actualiza manualmente después de cada daily standup.

### Paso 4: Quick Links

Esta sección centraliza todos los links importantes:

```markdown
### 🔗 Quick Links

#### Development
- 💻 [GitHub Repository](enlace)
- 🎨 [Shared Assets Drive](enlace)
- 🎵 [Audio Files](enlace)

#### Communication
- 💬 [Discord Server](enlace)
- 📞 [Team Video Call](enlace)
- 📧 [Email Thread](enlace)

#### Game Jam Platform
- 🎮 [Game Jam Page](enlace)
- 📜 [Rules & Guidelines](enlace)
- 🏆 [Submission Page](enlace)

#### References
- 📚 [Notion Resources Page](#resources)
- 📋 [GDD](#gdd)
- ✅ [Task Board](#tasks)
```

### Paso 5: Team Contacts

Información de contacto rápida del equipo:

```markdown
### 👥 Team Contacts

| Rol | Nombre | Discord | GitHub | Disponibilidad |
|-----|--------|---------|--------|----------------|
| 🎮 Game Designer | [Nombre] | @user#1234 | @username | 9-18h |
| 💻 Programador | [Nombre] | @user#1234 | @username | 10-20h |
| 🎨 Modelador 3D | [Nombre] | @user#1234 | - | 14-22h |
| 🎬 Animador | [Nombre] | @user#1234 | - | 9-17h |

**Emergency Contact:** [Nombre] - [Teléfono/WhatsApp]
```

### Paso 6: Current Sprint Goals

Objetivos del sprint actual (actualizar diariamente):

```markdown
### 🎯 Current Sprint Goals

**Day:** [Día X del Jam]
**Sprint:** [Ej: Day 1 - Foundation]

#### Today's Goals
- [ ] Goal 1
- [ ] Goal 2
- [ ] Goal 3

#### Critical Path
🔴 **BLOCKER:** [Si hay algún bloqueador crítico]
🟢 **ON TRACK:** [Si todo va bien]

#### Daily Standup Notes
**Last Update:** [Fecha y hora]

- **Programador:** [Qué está haciendo]
- **Modelador:** [Qué está haciendo]
- **Animador:** [Qué está haciendo]
- **Designer:** [Qué está haciendo]
```

---

## 📋 Template Completo del Dashboard

Aquí está todo junto para que lo copies y pegues:

```markdown
## 📄 Dashboard

### ⏰ Timeline

**Start:** [Fecha de inicio]
**Deadline:** [Fecha límite]
**Days Remaining:** [X días]

---

### 📊 Progress Overview

#### By Category
- **Design:** ⬜⬜⬜⬜⬜ 0%
- **Programming:** ⬜⬜⬜⬜⬜ 0%
- **Art:** ⬜⬜⬜⬜⬜ 0%
- **Audio:** ⬜⬜⬜⬜⬜ 0%

#### Tasks Status
- ✅ Done: 0
- 🔄 In Progress: 0
- 📋 To Do: 0
- 🔴 Blocked: 0

**Overall Progress:** 0%

---

### 🔗 Quick Links

#### Development
- 💻 [GitHub Repository](enlace)
- 🎨 [Shared Assets Drive](enlace)
- 🎵 [Audio Files](enlace)

#### Communication
- 💬 [Discord Server](enlace)
- 📞 [Team Video Call](enlace)

#### Game Jam Platform
- 🎮 [Game Jam Page](enlace)
- 📜 [Rules & Guidelines](enlace)
- 🏆 [Submission Page](enlace)

#### Internal Pages
- 📚 [Resources](#resources)
- 📋 [GDD](#gdd)
- ✅ [Task Board](#tasks)
- 📦 [Assets](#assets)

---

### 👥 Team Contacts

| Rol | Nombre | Discord | GitHub | Disponibilidad |
|-----|--------|---------|--------|----------------|
| 🎮 Game Designer | [Nombre] | @user#1234 | @username | 9-18h |
| 💻 Programador | [Nombre] | @user#1234 | @username | 10-20h |
| 🎨 Modelador 3D | [Nombre] | @user#1234 | - | 14-22h |
| 🎬 Animador | [Nombre] | @user#1234 | - | 9-17h |

**Emergency Contact:** [Nombre] - [Teléfono]

---

### 🎯 Current Sprint Goals

**Day:** [Día 1]
**Sprint:** [Foundation / Core Mechanics / Polish / etc.]

#### Today's Goals
- [ ] Goal 1
- [ ] Goal 2
- [ ] Goal 3

#### Status
🟢 **ON TRACK** / 🟡 **NEEDS ATTENTION** / 🔴 **BLOCKER**

**Notes:** [Notas del daily standup]

---

### 📝 Quick Notes

[Espacio para notas rápidas y decisiones importantes]

-

---
```

---

## 🎨 Mejoras Visuales (Opcional)

### Añadir Callouts

En vez de texto plano, puedes usar callouts de Notion:

1. Escribe `/callout`
2. Elige un emoji representativo
3. Cambia el color de fondo

**Ejemplo para Current Sprint Goals:**
```
/callout 🎯
Background color: Azul claro
```

### Añadir Divisores

Entre secciones, usa:
```
/divider
```

### Añadir Indicadores Visuales

Para el status del proyecto:
```
/callout 🟢
"PROJECT STATUS: On Track - All teams making good progress"
Background: Verde claro
```

---

## 💡 Tips de Uso

### Durante el Jam

1. **Actualiza el Dashboard 2 veces al día:**
   - Mañana: Después del daily standup
   - Noche: Antes de terminar la jornada

2. **Usa el Dashboard en el Daily Standup:**
   - Proyéctalo en pantalla compartida
   - Todos ven el mismo contexto
   - Actualiza los "Today's Goals" en vivo

3. **Mantén Quick Links actualizado:**
   - Si cambia un link de Discord/Meet, actualízalo inmediatamente
   - Prueba los links regularmente

4. **Progress Overview es motivacional:**
   - Ver progreso visual motiva al equipo
   - Celebra cuando una categoría llegue a 100%

### Post-Jam

El Dashboard se convierte en un snapshot del proyecto:
- Puedes ver "cómo iba todo" en cualquier momento
- Útil para retrospectivas
- Comparar con futuras jams

---

## ✅ Verificación

Al terminar esta fase, tu Dashboard debe tener:

- [x] Timeline con fechas clave
- [x] Progress overview actualizable
- [x] Quick links a todos los recursos importantes
- [x] Team contacts completos
- [x] Sección de current sprint goals
- [x] Todo visualmente organizado y fácil de leer

---

## 🚀 Próximo Paso

Ahora que tienes tu command center, continúa con:

👉 **`03_GDD.md`** - Estructurar el Game Design Document

---

## 📸 Vista Previa Conceptual

Tu Dashboard debería verse algo así:

```
╔════════════════════════════════════════════╗
║          📄 DASHBOARD                      ║
╠════════════════════════════════════════════╣
║ ⏰ 2 días, 14 horas restantes              ║
║                                            ║
║ 📊 Progress: ▰▰▰▰▱▱▱▱▱▱ 40%               ║
║                                            ║
║ 🔗 [GitHub] [Discord] [Drive]              ║
║                                            ║
║ 👥 Team: 4 personas online                 ║
║                                            ║
║ 🎯 Sprint Day 2: Core Mechanics            ║
║    ✅ Player movement done                 ║
║    🔄 Enemy AI in progress                 ║
║    📋 Combat system to do                  ║
╚════════════════════════════════════════════╝
```

---

**¿Completaste el Dashboard?** ✅ Continúa con el GDD.

---

## 🧭 Navegación

**📍 Estás en:** Fase 1 - Dashboard

| ⬅️ Anterior | 🏠 Inicio | ➡️ Siguiente |
|------------|----------|-------------|
| [⚙️ Setup](01_Setup_Inicial.md) | [🏠 README](README.md) | [📋 GDD](03_GDD.md) |

**🔗 Todas las Guías:**
[Plan](00_PLAN_IMPLEMENTACION.md) • [Setup](01_Setup_Inicial.md) • [Dashboard](02_Dashboard.md) • [GDD](03_GDD.md) • [Tasks](04_Task_Board.md) • [Assets](05_Asset_Tracker.md) • [Bugs](06_Bug_Log.md) • [Schedule](07_Schedule_Milestones.md) • [Resources](08_Resources.md) • [Checklist](CHECKLIST_IMPLEMENTACION.md)

---
