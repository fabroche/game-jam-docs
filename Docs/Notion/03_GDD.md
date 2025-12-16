# 📋 Fase 2: Game Design Document (GDD)

**Tiempo estimado:** 30 minutos

## 🎯 Objetivo

Crear una estructura para el Game Design Document adaptada a Game Jams: concisa, visual, accionable y fácil de actualizar durante el desarrollo.

---

## 📊 Estructura del GDD

Basado en la sección 3.2 del documento Guidelines_ES.md, pero adaptado para Notion:

```
📋 Game Design Document
│
├── 📋 Información General
├── 🎯 Concepto del Juego
│   ├── High Concept
│   ├── Core Loop
│   └── Pillars
├── 🕹️ Mecánicas
│   ├── Core Mechanics
│   └── Secondary Mechanics
├── 🎨 Dirección de Arte
│   ├── Estilo Visual
│   ├── Paleta de Colores
│   └── Referencias
├── 🗺️ Level Design
├── 👥 Enemigos y NPCs
├── 🖥️ UI/UX
└── 🎵 Audio
```

---

## 🛠️ Instrucciones Paso a Paso

### Paso 1: Ubicar la Sección GDD

1. Abre tu página template
2. Busca la sección `## 📋 Game Design Document`
3. Borra el placeholder

### Paso 2: Copiar la Estructura Base

Copia y pega esto en tu sección GDD:

```
## 📋 Game Design Document

> **Última actualización:** [Fecha]
> **Versión:** 1.0

---

### 📋 Información General

| Campo | Valor |
|-------|-------|
| **Título** | [Nombre del Juego] |
| **Tema del Jam** | [Si aplica] |
| **Género** | [Plataformas / Puzzle / Shooter / etc.] |
| **Plataforma** | PC (Windows/Mac/Linux) |
| **Duración de Juego** | 5-10 minutos |
| **Target Audience** | Jugadores casuales |

---

### 🎯 Concepto del Juego

#### High Concept (Una línea)

> **"Es [Juego Conocido] meets [Otro Juego], donde [Twist Único]"**
>
> Ejemplo: _"Es Super Mario meets Portal, donde usas portales para superar plataformas"_

**Nuestro juego:**
> "[Completar aquí]"

---

#### Core Loop

El ciclo central de gameplay:

1. El jugador [acción principal]
   ↓
2. Esto causa [consecuencia/desafío]
   ↓
3. El jugador debe [solución/objetivo]
   ↓
4. Al completar, obtiene [recompensa/progresión]
   ↓
   [Vuelve al paso 1 con mayor dificultad]

---

#### Pillars (Pilares de diseño)

Los 3 elementos fundamentales que definen tu juego:

1. **[Pilar 1]** - Ej: "Movimiento fluido y satisfactorio"
2. **[Pilar 2]** - Ej: "Combate táctico basado en timing"
3. **[Pilar 3]** - Ej: "Exploración recompensada"

---

### 🕹️ Mecánicas

#### Mecánicas Core (MVP - Imprescindibles)

##### 1. Movimiento

**Controles:**
- **WASD:** Movimiento en 8 direcciones
- **Space:** Salto
- **Shift:** Sprint
- **Mouse:** Control de cámara

**Referencias Técnicas:**
- CharacterController
- Velocidad base: 5 m/s
- Gravedad: -20 m/s²
- Altura de salto: 2m

##### 2. [Segunda Mecánica Core]

[Descripción]

##### 3. [Tercera Mecánica Core]

[Descripción]

---

#### Mecánicas Secundarias (Si hay tiempo)

⚠️ **REGLA:** Si queda <24 horas, NO implementar secundarias

- [ ] [Mecánica secundaria 1]
- [ ] [Mecánica secundaria 2]

---

### 🎨 Dirección de Arte

#### Estilo Visual

**Descriptor:** [Low-poly colorido / Pixel art / Realista / etc.]

**Referencia:** [Link a moodboard - crear toggle con imágenes]

---

#### Paleta de Colores

- **Primario:** #XXXXXX ⬛
- **Secundario:** #XXXXXX ⬛
- **Acento:** #XXXXXX ⬛
- **Background:** #XXXXXX ⬛

---

#### Budget de Performance

- **Target FPS:** 60
- **Triángulos en pantalla:** <100k
- **Draw calls:** <100

---

### 🗺️ Level Design

#### Estructura de Niveles

Main Menu → Tutorial → Level 1 → [Level 2] → Victory Screen

#### Level 1: [Nombre]

**Objetivo:** [Descripción del objetivo del nivel]

**Duración estimada:** [X minutos]

**Elementos clave:**
-
-
-

**Sketch:** [Añadir imagen/dibujo aquí]

---

### 👥 Enemigos y NPCs

#### Enemigo Tipo A: "[Nombre]"

**Comportamiento:**
- Patrol entre puntos
- Detección a X metros
- Attack a Y metros

**Stats:**
- HP: [X]
- Damage: [X]
- Speed: [X m/s]

**AI:** [Tipo de IA a usar]

---

### 🖥️ UI/UX

#### Pantallas

##### 1. Main Menu
**Elementos:**
- [ ] Logo del juego
- [ ] Botón "Play"
- [ ] Botón "Options" (opcional)
- [ ] Botón "Quit"
- [ ] Créditos

##### 2. HUD (In-game)
**Elementos:**
- [ ] Barra de HP (superior izquierda)
- [ ] [Otro elemento]
- [ ] [Otro elemento]

**Wireframe:** [Añadir sketch aquí]

---

### 🎵 Audio

#### SFX Necesarios

| Efecto | Trigger | Prioridad | Source | Status |
|--------|---------|-----------|--------|--------|
| Footsteps | Al caminar | P1 | Freesound | ⬜ |
| Jump | Al saltar | P1 | Freesound | ⬜ |
| Attack | Al atacar | P0 | Mixkit | ⬜ |

#### Música

| Track | Uso | Duración | Prioridad | Status |
|-------|-----|----------|-----------|--------|
| Menu Theme | Menú | 1-2 min loop | P2 | ⬜ |
| Gameplay | Durante juego | 2-3 min loop | P1 | ⬜ |

**Fuentes:** Incompetech, OpenGameArt, Purple Planet

---

### 🎯 Win/Lose Conditions

#### Condición de Victoria
- [ ] [Condición 1]
- [ ] [Condición 2]

#### Condición de Derrota
- [ ] HP llega a 0
- [ ] [Otra condición]

---

### ⚠️ Scope & Priorities

#### Must Have (P0) - MVP
- [ ] [Feature 1]
- [ ] [Feature 2]
- [ ] [Feature 3]

#### Should Have (P1) - Important
- [ ] [Feature 1]
- [ ] [Feature 2]

#### Nice to Have (P2) - Polish
- [ ] [Feature 1]
- [ ] [Feature 2]

---

### 📝 Design Notes

[Espacio para notas rápidas, decisiones de diseño, cambios de última hora]

-

---
```

---

## 🎨 Mejoras para Notion

### 1. Usar Toggles para Secciones Colapsables

Para mantener el GDD limpio y navegable:

1. Selecciona una sección completa (ej: toda la sección "Mecánicas")
2. Escribe `/toggle` o haz clic derecho → "Turn into toggle"
3. Ahora se puede colapsar/expandir

**Secciones recomendadas para toggle:**
- Mecánicas (cada mecánica individual)
- Dirección de Arte
- Level Design
- Enemigos (cada enemigo individual)
- UI/UX (cada pantalla)

### 2. Añadir Callouts para Información Importante

Para warnings y notas clave:

- Escribe `/callout` y selecciona el ícono ⚠️
- Escribe: "REGLA: Si queda <24 horas, NO implementar mecánicas secundarias"
- Cambia el color a: Amarillo/Naranja

### 3. Galería de Referencias Visuales

Para el Moodboard:

1. En "Dirección de Arte → Referencia"
2. Escribe `/image` → Arrastra imágenes de referencia
3. O mejor: `/gallery` para crear una galería de imágenes

### 4. Integrar con Asset Tracker

En las secciones de Arte y Audio, puedes **vincular** a la base de datos de Assets:

- Escribe `/linked database` → Selecciona "Assets"
- Filtra por: Type = "3D Model" o "Audio"

Esto mostrará los assets relevantes directamente en el GDD.

---

## 📋 Template Simplificado (Versión Rápida)

Si tienes poco tiempo, usa esta versión minimalista:

```
## 📋 Game Design Document

### 🎯 High Concept
> "[Tu juego en una línea]"

### 🕹️ Core Mechanics (MVP)
1. [Mecánica 1]
2. [Mecánica 2]
3. [Mecánica 3]

### 🎨 Art Style
**Look:** [Descripción]
**Colors:** [Paleta]

### 🗺️ Levels
- Level 1: [Descripción breve]

### 🎵 Audio
- SFX: [Lista mínima]
- Music: [Source]

### ✅ Must Have
- [ ] [Feature P0-1]
- [ ] [Feature P0-2]
- [ ] [Feature P0-3]
```

---

## 💡 Tips de Uso del GDD

### Durante el Kickoff (Primeras 3 horas)

1. **Llena el GDD colaborativamente:**
   - Game Designer escribe la estructura base
   - Programador añade referencias técnicas
   - Modelador/Animador añade budget de performance
   - Todos contribuyen al Core Loop

2. **Usa "Comments" de Notion:**
   - Resalta texto → Add comment
   - Para discusiones sobre decisiones de diseño
   - Mantiene el contexto de por qué se tomó X decisión

3. **Prioriza brutalmente:**
   - La sección "Scope & Priorities" es CRÍTICA
   - Sé honesto sobre qué cabe en el tiempo disponible

### Durante el Desarrollo

1. **Actualiza el status de features:**
   - Marca checkboxes conforme se implementan
   - Mantén sincronizado con el Task Board

2. **Documenta cambios:**
   - Si una mecánica cambia, actualiza el GDD
   - Añade fecha en "Design Notes"

3. **Referencia técnica rápida:**
   - Los programadores pueden copiar/pegar specs directamente
   - Evita ambigüedades ("velocidad rápida" → "5 m/s")

### Post-Jam

El GDD se convierte en documentación histórica:
- Puedes ver qué mecánicas quedaron fuera
- Aprender de decisiones de diseño
- Reutilizar ideas en futuros proyectos

---

## ✅ Verificación

Al terminar esta fase, tu GDD debe tener:

- [x] Información general completa
- [x] High Concept claro y conciso
- [x] Core Loop definido
- [x] Mecánicas Core especificadas con detalles técnicos
- [x] Dirección de Arte con paleta de colores
- [x] Scope claramente priorizado (P0/P1/P2)
- [x] Estructura colapsable con toggles
- [x] (Opcional) Referencias visuales integradas

---

## 🚀 Próximo Paso

Ahora que tienes el diseño documentado, es hora de gestionarlo:

👉 **`04_Task_Board.md`** - Crear el sistema de gestión de tareas

---

## 📸 Vista Previa Conceptual

Tu GDD debería verse algo así:

```
╔════════════════════════════════════════════╗
║       📋 GAME DESIGN DOCUMENT              ║
╠════════════════════════════════════════════╣
║                                            ║
║ 🎯 High Concept                            ║
║ > "Portal meets Mario"                     ║
║                                            ║
║ ▼ 🕹️ Mecánicas [TOGGLE EXPANDIDO]         ║
║   1. Movimiento platformer                 ║
║      - WASD controls                       ║
║      - Jump: 2m height                     ║
║   2. Portal mechanic                       ║
║      - Click para crear                    ║
║                                            ║
║ ▶ 🎨 Dirección de Arte [COLLAPSED]        ║
║ ▶ 🗺️ Level Design [COLLAPSED]             ║
║                                            ║
║ ✅ Must Have (P0)                          ║
║   ☑ Player movement                        ║
║   ☐ Portal creation                        ║
║   ☐ 1 complete level                       ║
╚════════════════════════════════════════════╝
```

---

**¿Completaste el GDD?** ✅ Continúa con el Task Board.

---

## 🧭 Navegación

**📍 Estás en:** Fase 2 - Game Design Document

| ⬅️ Anterior | 🏠 Inicio | ➡️ Siguiente |
|------------|----------|-------------|
| [📄 Dashboard](02_Dashboard.md) | [🏠 README](README.md) | [✅ Task Board](04_Task_Board.md) |

**🔗 Todas las Guías:**
[Plan](00_PLAN_IMPLEMENTACION.md) • [Setup](01_Setup_Inicial.md) • [Dashboard](02_Dashboard.md) • [GDD](03_GDD.md) • [Tasks](04_Task_Board.md) • [Assets](05_Asset_Tracker.md) • [Bugs](06_Bug_Log.md) • [Schedule](07_Schedule_Milestones.md) • [Resources](08_Resources.md) • [Checklist](CHECKLIST_IMPLEMENTACION.md)

---
