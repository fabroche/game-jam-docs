# 📚 Documentación Técnica - Equipo Game Jam Unity 6

## Índice
1. [Operación como Equipo](#1-operación-como-equipo)
2. [Administración de Tareas (Notion + GitHub Issues)](#2-administración-de-tareas-notion--github-issues)
3. [Game Design Document (GDD) para Game Jams](#3-game-design-document-gdd-para-game-jams)
4. [Plan de Acción Operativo](#4-plan-de-acción-operativo)
5. [Anexos y Recursos](#5-anexos-y-recursos)

---

## 1. Operación como Equipo

### 1.1 Principios Fundamentales

#### Regla de Oro: "Done is Better than Perfect"
En una game jam, un juego funcional y simple **siempre** supera a un proyecto ambicioso sin terminar.

Ejemplo de pull request

#### Comunicación Constante
- **Daily Stand-ups:** 10-15 minutos al inicio de cada día
  - ¿Qué hice ayer?
  - ¿Qué haré hoy?
  - ¿Tengo algún bloqueador?
  
- **Canal de Comunicación:** Usar Discord/Slack con canales específicos:
  - `#general` - Coordinación general
  - `#art-assets` - Compartir modelos/animaciones
  - `#code` - Problemas técnicos
  - `#design` - Mecánicas y feedback
  - `#builds` - Versiones jugables

### 1.2 Flujo de Trabajo por Rol

```
┌─────────────────────────────────────────────────────────┐
│                    GAME DESIGNER                        │
│  Define concepto → Documenta mecánicas → Level design  │
└───────────────────┬─────────────────────────────────────┘
                    ↓
        ┌───────────┴───────────┐
        ↓                       ↓
┌───────────────┐       ┌───────────────┐
│  MODELADOR 3D │       │   PROGRAMADOR │
│ Crea assets   │←──────│ Especifica    │
│               │       │ necesidades   │
└───────┬───────┘       └───────┬───────┘
        ↓                       ↓
┌───────────────┐       ┌───────────────┐
│   ANIMADOR    │       │  INTEGRACIÓN  │
│ Rigea y anima │──────→│  EN UNITY     │
└───────────────┘       └───────┬───────┘
                                ↓
                        ┌───────────────┐
                        │ GAME DESIGNER │
                        │ Testing/Level │
                        │   Design      │
                        └───────────────┘
```

### 1.3 Gestión de Dependencias

#### Dependencias Críticas (Bloquean trabajo)
```
Modelador → Animador → Programador
   ↓
Si el modelador no entrega el personaje,
el animador NO puede rigearlo,
el programador NO puede integrarlo.
```

**Solución: Assets Temporales (Placeholders)**

**Programador:**
```csharp
// SIEMPRE usa placeholders para no bloquearte
// En vez de esperar el modelo final:

public class PlayerController : MonoBehaviour
{
    // Placeholder: Cubo de Unity con capsule collider
    // Reemplazar cuando llegue el modelo final
    
    [Header("Referencias - REEMPLAZAR CON MODELO FINAL")]
    public GameObject visualModel; // Asignar cubo temporalmente
    
    void Start()
    {
        if (visualModel == null)
        {
            Debug.LogWarning("⚠️ Usando placeholder - reemplazar con modelo final");
            CreatePlaceholder();
        }
    }
    
    void CreatePlaceholder()
    {
        GameObject placeholder = GameObject.CreatePrimitive(PrimitiveType.Cube);
        placeholder.transform.SetParent(transform);
        visualModel = placeholder;
    }
}
```

**Modelador:**
- Crea un cubo/cilindro con las dimensiones correctas PRIMERO
- Envíalo al programador el Día 1
- Trabaja en el modelo detallado en paralelo

**Animador:**
- Usa personajes de Mixamo como placeholder
- Exporta animaciones genéricas que funcionen con cualquier rig humanoide

### 1.4 Reuniones Clave

#### Día 0: Kickoff (2-3 horas)
- Brainstorming del concepto
- Definir scope realista
- Asignar tareas iniciales
- Configurar repositorio y Notion

#### Días 1-3: Check-ins Diarios (15 min)
- Por la mañana o tarde (según disponibilidad)
- Formato stand-up

#### Día 4-5: Playtesting Interno (1 hora)
- Todos juegan la build
- Anotan bugs y mejoras
- Priorizan fixes

#### Última Noche: Code Freeze
- **6 horas antes del deadline:** NO MÁS FEATURES
- Solo fixes críticos
- Builds de testing continuas

### 1.5 Resolución de Conflictos

#### Conflicto de Prioridades
```
Situación: El animador quiere hacer 10 animaciones,
el programador solo tiene tiempo de integrar 5.

Solución:
1. Game Designer prioriza las 5 más importantes
2. Se documentan las 5 restantes como "Post-Jam Features"
3. Se sigue adelante con las prioritarias
```

#### Conflicto Técnico
```
Situación: El modelo es demasiado pesado para el performance target.

Solución:
1. Programador mide FPS y identifica el problema
2. Modelador crea versión Low-Poly en 1-2 horas
3. Si no hay tiempo, usar asset gratuito de backup
```

**Regla de Escalamiento:**
- Si un problema toma >30 min discutirlo → Consultar al asesor/mentor
- Si un problema toma >2 horas resolverlo → Cambiar de enfoque

---

## 2. Administración de Tareas (Notion + GitHub Issues)

### 2.1 ¿Por qué usar ambas herramientas?

**Notion:** Diseño, planificación, documentación
**GitHub Issues:** Bugs, features técnicas, tracking de desarrollo

```
┌──────────────────────────────────────────────┐
│               NOTION                         │
│  - GDD                                       │
│  - Concept Art                               │
│  - Asset Lists                               │
│  - Meeting Notes                             │
│  - Level Design Sketches                     │
└──────────────────────────────────────────────┘
                    ↕️
        (Referencia mutua)
                    ↕️
┌──────────────────────────────────────────────┐
│            GITHUB ISSUES                     │
│  - Feature Implementation                    │
│  - Bug Tracking                              │
│  - Code Reviews                              │
│  - Technical Documentation                   │
└──────────────────────────────────────────────┘
```

### 2.2 Configuración de Notion

#### Estructura de Workspace

```
Game Jam Project Workspace
│
├── 📄 Home / Dashboard
│   ├── Countdown Timer
│   ├── Quick Links
│   └── Team Contacts
│
├── 📋 Game Design Document
│   ├── Concept
│   ├── Mechanics
│   ├── Art Style
│   └── Audio
│
├── ✅ Task Board (Kanban)
│   ├── Backlog
│   ├── To Do
│   ├── In Progress
│   ├── Testing
│   └── Done
│
├── 📦 Asset Tracker
│   ├── Models
│   ├── Animations
│   ├── Audio
│   └── UI Elements
│
├── 🐛 Bug Log
│
├── 📅 Schedule & Milestones
│
└── 📚 Resources
    ├── Reference Images
    ├── Tutorials
    └── Asset Sources
```

#### Template: Task Card en Notion

```markdown
# [TASK-001] Implementar Movimiento del Jugador

**Rol:** Programador
**Prioridad:** 🔴 Alta
**Estado:** In Progress
**Estimación:** 3 horas
**GitHub Issue:** #12

## Descripción
Implementar sistema de movimiento básico con WASD y salto con Space.

## Requisitos
- [ ] Movimiento horizontal (A/D)
- [ ] Movimiento vertical (W/S)
- [ ] Sistema de salto
- [ ] Rotación de la cámara con mouse

## Dependencias
- Modelo placeholder del jugador (TASK-005)

## Assets Necesarios
- Ninguno (usar cubo placeholder)

## Notas
Usar CharacterController en vez de Rigidbody para mayor control.

## Referencias
- [Unity CharacterController Docs](link)
```

#### Propiedades de Base de Datos en Notion

Para el **Task Board**, crear una base de datos con estas propiedades:

| Propiedad | Tipo | Valores |
|-----------|------|---------|
| Task Name | Title | - |
| Assignee | Person | Team Members |
| Role | Select | Programador, Modelador, Animador, Designer |
| Priority | Select | 🔴 Alta, 🟡 Media, 🟢 Baja |
| Status | Select | Backlog, To Do, In Progress, Testing, Done |
| Estimate | Number | Horas |
| Sprint | Select | Day 1, Day 2, Day 3, Day 4, Day 5, Polish |
| Tags | Multi-select | Core, Polish, Bug, Feature, Art, Code, Audio |
| GitHub Link | URL | - |

### 2.3 Configuración de GitHub Issues

#### Labels Recomendados

```
Tipo:
🎮 feature        - Nueva funcionalidad
🐛 bug           - Error a corregir
🎨 art           - Assets artísticos
🎵 audio         - Assets de audio
📚 documentation - Documentación
🔧 refactor      - Mejora de código

Prioridad:
🔴 P0-critical   - Bloquea el desarrollo
🟠 P1-high       - Importante para el MVP
🟡 P2-medium     - Mejora significativa
🟢 P3-low        - Nice to have

Estado:
🚀 ready         - Listo para trabajar
🔒 blocked       - Esperando dependencia
👀 in-review     - En revisión
✅ tested        - Testeado y aprobado

Rol:
💻 code          - Requiere programación
🎨 art-3d        - Requiere modelado
🎬 animation     - Requiere animación
📐 design        - Requiere diseño
```

#### Template: Issue de Feature

```markdown
## 🎮 Feature: Sistema de Combate Básico

### Descripción
Implementar sistema de combate cuerpo a cuerpo con ataque básico.

### Criterios de Aceptación
- [ ] El jugador puede presionar LMB para atacar
- [ ] La animación de ataque se reproduce correctamente
- [ ] El ataque causa daño a enemigos en un radio de 2 unidades
- [ ] Hay un cooldown de 0.5 segundos entre ataques

### Dependencias
- #15 Integración de animaciones
- Notion: TASK-023 (Animación de ataque)

### Subtareas Técnicas
- [ ] Crear script `MeleeAttack.cs`
- [ ] Implementar detección de colisión (OverlapSphere)
- [ ] Conectar con Animator
- [ ] Añadir feedback visual (particle effect)

### Assets Requeridos
- Animación: attack_01.fbx
- VFX: hit_spark prefab
- SFX: sword_swing.wav

### Notas de Implementación
```csharp
// Ejemplo de detección de enemigos
Collider[] hits = Physics.OverlapSphere(attackPoint.position, attackRadius, enemyLayer);
```

### Estimación
4 horas

### Asignado a
@programador-username

### Labels
`🎮 feature` `🟠 P1-high` `💻 code` `Day 2`
```

#### Template: Issue de Bug

```markdown
## 🐛 Bug: El jugador atraviesa el suelo

### Descripción del Problema
Cuando el jugador salta cerca de una rampa, a veces atraviesa el suelo y cae al vacío.

### Pasos para Reproducir
1. Iniciar el nivel 1
2. Ir a la rampa cerca del spawn
3. Saltar 3-4 veces seguidas
4. Bug ocurre ~50% de las veces

### Comportamiento Esperado
El jugador debería colisionar correctamente con el suelo.

### Comportamiento Actual
El jugador atraviesa el collider y cae.

### Screenshots/Video
[Adjuntar captura o GIF]

### Información Técnica
- Unity Version: 6.0
- Script afectado: `PlayerController.cs`
- Collider: Capsule Collider en jugador
- Ground: Mesh Collider

### Posible Causa
El Mesh Collider puede no ser convexo. Verificar configuración.

### Prioridad
🔴 P0-critical - Rompe la jugabilidad

### Asignado a
@programador-username

### Labels
`🐛 bug` `🔴 P0-critical` `💻 code`
```

### 2.4 Workflow de Integración Notion ↔ GitHub

#### Proceso: Tarea de Feature

```
1. Game Designer crea task en Notion
   └─→ "TASK-045: Añadir power-up de velocidad"
   
2. Añade detalles, referencias, sketch
   
3. Programador crea Issue en GitHub
   └─→ "#45 Implement Speed Power-up"
   
4. Añade enlace de GitHub en Notion
   Notion: "GitHub Issue: #45"
   
5. GitHub Issue incluye enlace a Notion
   GitHub: "Design Doc: [Notion Link]"
   
6. Desarrollo en GitHub
   - Commits con "#45" para auto-link
   - Code review
   - Merge a dev branch
   
7. Update en Notion
   - Status: Testing
   - Build donde está disponible
   
8. Game Designer testea
   
9. Si OK:
   - Notion: Status → Done
   - GitHub: Close Issue
```

#### Convención de Naming

**Notion:**
```
[TASK-XXX] Descripción Clara
Ejemplos:
- [TASK-001] Implementar movimiento del jugador
- [TASK-002] Modelar personaje principal
- [TASK-003] Animar ciclo de caminar
- [TASK-004] Diseñar nivel 1
```

**GitHub:**
```
#XXX Descripción en inglés (opcional pero profesional)
Ejemplos:
- #001 Implement player movement
- #002 Create main character model
- #003 Animate walk cycle
- #004 Design level 1
```

**Commits:**
```
git commit -m "feat: add player jump (#001)"
git commit -m "fix: player falling through floor (#023)"
git commit -m "art: add main character model (#002)"
git commit -m "anim: export walk cycle (#003)"

Prefijos:
feat - Nueva feature
fix - Bug fix
art - Asset artístico
anim - Animación
design - Cambio de diseño
refactor - Mejora de código
docs - Documentación
```

### 2.5 Workflow Diario Recomendado

```
🌅 MAÑANA (9:00 - 9:15)
- Daily stand-up
- Revisar Notion Task Board
- Mover tareas a "In Progress"
- Verificar GitHub Issues asignados

💻 TRABAJO (9:15 - 13:00)
- Desarrollar tareas
- Commits frecuentes
- Actualizar status en tiempo real

🍕 ALMUERZO (13:00 - 14:00)
- Descanso

💻 TRABAJO (14:00 - 18:00)
- Continuar desarrollo
- Code reviews
- Testing interno

📊 TARDE (18:00 - 18:30)
- Actualizar Notion con progreso
- Close Issues completados
- Crear Issues para bugs encontrados
- Preparar build si es día de milestone

🌙 NOCHE (18:30+)
- Tiempo flexible según necesidad
- En últimos días: crunch time (opcional)
```

---

## 3. Game Design Document (GDD) para Game Jams

### 3.1 ¿Qué es un GDD?

El **Game Design Document** es el documento maestro que define qué es tu juego. En una game jam, debe ser:
- ✅ Conciso (5-10 páginas máximo)
- ✅ Visual (sketches, referencias)
- ✅ Accionable (todos saben qué hacer)
- ❌ NO exhaustivo (no es un GDD de producción AAA)

### 3.2 Estructura de GDD para Game Jam

#### Template Completo

```markdown
# 🎮 [NOMBRE DEL JUEGO] - Game Design Document

## 📋 Información General

**Título:** [Nombre del Juego]
**Tema del Jam:** [Tema si aplica]
**Género:** [Plataformas, Puzzle, Shooter, etc.]
**Plataforma:** PC (Windows/Mac/Linux)
**Duración de Juego:** 5-10 minutos
**Target Audience:** Jugadores casuales

**Equipo:**
- Game Designer: [Nombre]
- Programador: [Nombre]
- Modelador 3D: [Nombre]
- Animador: [Nombre]

**Timeline:**
- Inicio: [Fecha]
- Fin: [Fecha]
- Duración: 48/72 horas

---

## 🎯 Concepto del Juego

### High Concept (Una línea)
> "Es [Juego Conocido] meets [Otro Juego], donde [Twist Único]"
>
> Ejemplo: "Es Super Mario meets Portal, donde usas portales para superar plataformas"

### Core Loop (Ciclo central de gameplay)
```
1. El jugador [acción principal]
   ↓
2. Esto causa [consecuencia/desafío]
   ↓
3. El jugador debe [solución/objetivo]
   ↓
4. Al completar, obtiene [recompensa/progresión]
   ↓
[Vuelve al paso 1 con mayor dificultad]
```

**Ejemplo:**
```
1. El jugador explora el nivel
   ↓
2. Encuentra enemigos bloqueando el camino
   ↓
3. Debe usar combate o sigilo para superarlos
   ↓
4. Obtiene llave para abrir puerta al siguiente nivel
   ↓
[Siguiente nivel más difícil]
```

### Pillars (Pilares de diseño)
Los 3 elementos fundamentales que definen tu juego:

1. **[Pilar 1]** - Ej: "Movimiento fluido y satisfactorio"
2. **[Pilar 2]** - Ej: "Combate táctico basado en timing"
3. **[Pilar 3]** - Ej: "Exploración recompensada"

---

## 🕹️ Mecánicas

### Mecánicas Core (Imprescindibles para el MVP)

#### 1. Movimiento
- **WASD:** Movimiento en 8 direcciones
- **Space:** Salto (altura: 2m, duración: 0.5s)
- **Shift:** Sprint (velocidad x1.5)
- **Mouse:** Control de cámara (3ra persona)

**Referencias Técnicas:**
- CharacterController
- Velocidad base: 5 m/s
- Gravedad: -20 m/s²

#### 2. Combate
- **LMB:** Ataque básico (cooldown: 0.7s)
- **RMB:** Bloqueo (reduce daño 50%)
- **Q:** Habilidad especial (cooldown: 5s)

**Sistema de Daño:**
- Player HP: 100
- Ataque base: 20 damage
- Enemy HP: 50

#### 3. [Otra Mecánica Core]
[Descripción detallada]

### Mecánicas Secundarias (Si hay tiempo)

#### 1. Sistema de Inventario
- Capacidad: 5 items
- Items recolectables: Pociones, llaves

#### 2. [Otra Mecánica Secundaria]
[Descripción]

**⚠️ REGLA:** Si queda 24 horas o menos, NO implementar mecánicas secundarias.

---

## 🎨 Dirección de Arte

### Estilo Visual
**Referencia:** [Link a moodboard en Notion/Pinterest]

**Descriptor:** Low-poly colorido con iluminación cell-shaded

**Paleta de Colores:**
- Primario: `#FF6B6B` (Rojo)
- Secundario: `#4ECDC4` (Turquesa)
- Acento: `#FFE66D` (Amarillo)

### Assets 3D

#### Lista de Modelos (Priorizada)

| Asset | Prioridad | Triángulos | Status | Assignee |
|-------|-----------|------------|--------|----------|
| Personaje Jugador | P0 | <5k | To Do | Modelador |
| Enemigo Tipo A | P0 | <3k | To Do | Modelador |
| Piso/Ground Tiles | P0 | <500 | To Do | Modelador |
| Props decorativos | P2 | <1k | Backlog | Modelador |

**Budget de Performance:**
- Total de triángulos en pantalla: <100k
- Draw calls target: <100

### Animaciones

#### Lista de Animaciones (Priorizada)

| Animación | Personaje | Frames | Prioridad | Status |
|-----------|-----------|--------|-----------|--------|
| Idle | Jugador | 30 | P0 | To Do |
| Walk | Jugador | 20 | P0 | To Do |
| Run | Jugador | 16 | P0 | To Do |
| Jump_Start | Jugador | 8 | P0 | To Do |
| Jump_Loop | Jugador | 8 | P0 | To Do |
| Jump_Land | Jugador | 8 | P1 | Backlog |
| Attack_01 | Jugador | 24 | P0 | To Do |
| Hit_React | Jugador | 12 | P1 | Backlog |
| Death | Jugador | 30 | P1 | Backlog |

**⚠️ MÍNIMO VIABLE:**
- Idle
- Walk
- Jump (puede ser un solo clip genérico)
- Attack

### Audio

#### SFX Necesarios

| Efecto | Trigger | Prioridad | Source |
|--------|---------|-----------|--------|
| Footsteps | Al caminar | P1 | Freesound.org |
| Jump | Al saltar | P1 | Freesound.org |
| Attack_Swing | Al atacar | P0 | Mixkit |
| Hit_Impact | Golpear enemigo | P0 | Freesound.org |
| UI_Click | Clicks de UI | P2 | Kenney.nl |

#### Música

| Track | Uso | Duración | Prioridad |
|-------|-----|----------|-----------|
| Menu Theme | Menú principal | 1-2 min loop | P2 |
| Gameplay | Durante juego | 2-3 min loop | P1 |
| Victory | Al ganar | 15-30 seg | P2 |

**Fuentes:** Incompetech, OpenGameArt, Purple Planet

---

## 🗺️ Level Design

### Estructura de Niveles

```
GAME FLOW:
Main Menu → Tutorial → Level 1 → Level 2 → Victory Screen
```

### Level 1: Tutorial
**Objetivo:** Enseñar mecánicas básicas

**Layout:**
```
[START] → [Sección Movimiento] → [Sección Combate] → [Miniboss] → [END]
   |            (30s)                 (45s)             (1min)
   |__________________________________________________|
                    ~3 minutos total
```

**Elementos:**
- Spawn del jugador
- NPCs instructivos (opcional)
- 3-5 enemigos de práctica
- Miniboss fácil

**Sketch:** [Link a imagen en Notion]

### Level 2: Desafío Principal
**Objetivo:** Aplicar lo aprendido con mayor dificultad

**Layout:** [Descripción o sketch]

**⚠️ SCOPE:** Si el tiempo apremia, quedarse con 1 solo nivel bien pulido.

---

## 👥 Enemigos y NPCs

### Enemigo Tipo A: "Goblin"
**Comportamiento:**
- Patrol entre puntos A y B
- Al detectar jugador (radio 10m) → Chase
- Al estar en rango (2m) → Attack
- Al perder de vista 5s → Return to patrol

**Stats:**
- HP: 50
- Damage: 15
- Speed: 3 m/s
- Attack cooldown: 2s

**AI Script:** SimpleEnemyAI.cs (usar NavMesh)

### Enemigo Tipo B: [Si hay tiempo]
[Descripción]

---

## 🎯 Progresión y Win/Lose Conditions

### Condición de Victoria
- Completar todos los niveles
- Derrotar al boss final
- Recolectar todos los objetos (si aplica)

### Condición de Derrota
- HP del jugador llega a 0
- Caer al vacío (insta-kill)
- Timer (si aplica)

### Sistema de Puntuación (Opcional)
- Enemigos derrotados: +100 pts
- Tiempo restante: +10 pts/segundo
- Daño recibido: -5 pts

---

## 🖥️ UI/UX

### Pantallas

#### 1. Main Menu
**Elementos:**
- Título del juego (logo)
- Botón "Play"
- Botón "Options" (opcional)
- Botón "Quit"
- Créditos del equipo

#### 2. HUD (In-game)
**Elementos:**
- Barra de HP (esquina superior izquierda)
- Contador de enemigos (esquina superior derecha)
- Cooldowns de habilidades (parte inferior centro)
- Minimapa (opcional, solo si hay tiempo)

**Wireframe:** [Link a sketch en Notion]

#### 3. Pause Menu
**Elementos:**
- "Resume"
- "Restart"
- "Main Menu"

#### 4. Game Over Screen
**Elementos:**
- "YOU DIED" / "VICTORY"
- Score (opcional)
- "Retry"
- "Main Menu"

---

## 📦 Assets y Recursos Externos

### Assets de la Asset Store / Fuentes Externas

| Asset | Fuente | Licencia | Uso |
|-------|--------|----------|-----|
| [Ejemplo: TextMesh Pro] | Unity Package | Free | UI Text |
| [Low Poly Water] | Asset Store | Free | Agua en niveles |

### Herramientas de Terceros

- **ProBuilder:** Level design
- **DOTween:** Animaciones de UI
- **Cinemachine:** Control de cámara
- **NavMesh Components:** IA de enemigos

---

## 🚀 Milestones y Deliverables

### Day 1: Foundation
**Deliverables:**
- [ ] GDD completo
- [ ] Proyecto Unity configurado
- [ ] Repositorio Git inicializado
- [ ] Personaje placeholder funcionando
- [ ] Movimiento básico implementado

**Build Target:** Personaje que camina en una escena vacía

### Day 2: Core Mechanics
**Deliverables:**
- [ ] Sistema de combate funcional
- [ ] IA de enemigos básica
- [ ] Modelo del jugador (low-poly)
- [ ] 3 animaciones core (idle, walk, attack)
- [ ] Level 1 bloqueado (greybox)

**Build Target:** Jugabilidad core funcionando

### Day 3: Content & Polish
**Deliverables:**
- [ ] Todos los modelos integrados
- [ ] Todas las animaciones
- [ ] Level 1 completo y jugable
- [ ] UI básica (menú, HUD)
- [ ] SFX integrados

**Build Target:** Versión alfa jugable de principio a fin

### Day 4: Testing & Polish (Si es Jam de 72h+)
**Deliverables:**
- [ ] Bugs críticos resueltos
- [ ] Feedback visual/audio mejorado
- [ ] Balanceo de dificultad
- [ ] Level 2 (si hay tiempo)
- [ ] Música integrada

**Build Target:** Versión Beta

### Last 6 Hours: Final Push
**Deliverables:**
- [ ] Build para todas las plataformas
- [ ] Página de itch.io configurada
- [ ] Trailer/Screenshots
- [ ] Última ronda de testing
- [ ] Submit final

**🔒 CODE FREEZE 3 HORAS ANTES DEL DEADLINE**

---

## ⚠️ Risk Management

### Riesgos Identificados

| Riesgo | Probabilidad | Impacto | Mitigación |
|--------|--------------|---------|------------|
| Scope Creep | Alta | Alto | GDD estricto, priorización P0-P2 |
| Bloqueos entre roles | Media | Alto | Placeholders, comunicación diaria |
| Bugs de última hora | Alta | Medio | Testing continuo, code freeze |
| Performance issues | Media | Alto | Target de 60 FPS desde día 1 |
| Conflictos de merge | Media | Medio | Branches por feature, merges frecuentes |

### Plan de Contingencia

**Si perdemos 1 día completo de desarrollo:**
- Cortar mecánicas secundarias
- Reducir a 1 solo nivel
- Usar más assets gratuitos
- Simplificar arte

**Si un miembro no puede continuar:**
- Game Designer asume tareas de level design/testing
- Redistribuir tareas críticas
- Buscar assets gratuitos de reemplazo

---

## 📚 Glosario Técnico

| Término | Definición |
|---------|------------|
| Greybox/Blockout | Nivel construido con cubos/formas básicas para testear gameplay antes del arte final |
| Placeholder | Asset temporal usado para no bloquear desarrollo |
| MVP | Minimum Viable Product - Versión mínima jugable |
| P0/P1/P2 | Prioridades: P0 = Crítico, P1 = Alto, P2 = Bajo |
| Code Freeze | Momento donde se dejan de añadir features, solo se arreglan bugs |

---

## ✅ Checklist Pre-Submit

### 24 Horas Antes
- [ ] Build funciona en todas las plataformas target
- [ ] Todos los bugs P0 resueltos
- [ ] Todos los bugs P1 resueltos o documentados
- [ ] Gameplay loop es satisfactorio y claro
- [ ] Controles están explicados (in-game o en página)

### 12 Horas Antes
- [ ] Página de itch.io/GameJolt completa
- [ ] Screenshots de calidad (mínimo 5)
- [ ] Descripción del juego clara
- [ ] Créditos del equipo
- [ ] Licencias de assets de terceros

### 6 Horas Antes - CODE FREEZE
- [ ] Build final compilada
- [ ] Testing de la build (30 min)
- [ ] Trailer o GIF de gameplay (opcional pero recomendado)

### 3 Horas Antes
- [ ] Build subida a plataforma
- [ ] Links verificados funcionando
- [ ] Última revisión de bugs visuales

### 1 Hora Antes
- [ ] Submit final
- [ ] Screenshot de confirmación
- [ ] Backup de la build localmente
- [ ] Celebrar 🎉

---

**Version:** 1.0  
**Última Actualización:** [Fecha]  
**Mantenido por:** Game Designer
```

---

## 4. Plan de Acción Operativo

### 4.1 Pre-Producción (Antes del Jam)

#### 2 Semanas Antes
```
✅ SETUP TÉCNICO
□ Instalar Unity 6 (todos)
□ Instalar Blender (Modelador + Animador)
□ Configurar Git + GitHub (todos)
□ Crear cuenta en itch.io/GameJolt
□ Testear pipeline: Blender → Unity

✅ ORGANIZACIÓN
□ Crear Workspace en Notion
□ Importar templates de documentación
□ Configurar canales de Discord/Slack
□ Definir horarios de disponibilidad

✅ PRÁCTICA
□ Hacer tutorial de Unity (Programador)
□ Hacer tutorial de Blender (Modelador + Animador)
□ Exportar FBX de prueba (todos los roles)
□ Hacer un micro-proyecto de 2 horas (opcional)
```

#### 1 Semana Antes
```
✅ PLANIFICACIÓN
□ Investigar tema del jam (si se anuncia)
□ Preparar lista de referencias e inspiración
□ Preparar lista de assets gratuitos de backup
□ Hacer dry-run de reunión kickoff

✅ HERRAMIENTAS
□ Descargar plugins útiles (ProBuilder, DOTween)
□ Preparar librerías de código común
□ Configurar plantillas de Notion/GitHub
□ Testear herramientas de comunicación
```

#### 1 Día Antes
```
✅ ÚLTIMA PREPARACIÓN
□ Dormir bien (crucial)
□ Verificar que todo el software funciona
□ Tener comida/bebidas preparadas
□ Silenciar notificaciones no esenciales
□ Mentalización: "Done > Perfect"
```

### 4.2 Día por Día (Jam de 48 horas)

#### 🌅 DÍA 1: FOUNDATION (0-24h)

##### Hour 0-3: Kickoff & Planning
```
🎯 OBJETIVOS:
- Definir concepto del juego
- Crear GDD simplificado
- Asignar tareas iniciales

⏰ TIMELINE:
00:00 - 00:30 | Brainstorming (todos juntos)
  - Tema del jam
  - 5 ideas rápidas
  - Votar por 1

00:30 - 01:30 | Refinamiento de concepto
  - Definir core loop
  - Identificar mecánicas core
  - Sketches rápidos de level design

01:30 - 02:30 | Documentación en Notion
  - Game Designer escribe GDD base
  - Resto del equipo añade sección de su rol

02:30 - 03:00 | Task Breakdown
  - Crear todas las tareas en Notion
  - Asignar prioridades
  - Identificar dependencias críticas
  - Crear GitHub Issues para programación

📦 DELIVERABLES:
□ GDD completo (80% hecho)
□ Notion task board populated
□ GitHub Issues creados
□ Sketches de level design
```

##### Hour 3-8: Setup & First Playable
```
👨‍💻 PROGRAMADOR:
□ Crear proyecto Unity 6
□ Configurar Git (.gitignore, README)
□ Instalar packages esenciales
□ Crear escena de prueba
□ Implementar movimiento básico (WASD)
□ Crear placeholder del personaje (cubo)
□ Setup de InputSystem / viejo Input
□ First commit & push

🎨 MODELADOR:
□ Crear personaje placeholder (cilindro con proporciones)
□ Exportar a Unity para que programador lo use
□ Investigar referencias del personaje final
□ Comenzar modelado del personaje principal
□ Crear paleta de colores

🎬 ANIMADOR:
□ Buscar personaje en Mixamo como placeholder
□ Exportar animaciones básicas (idle, walk, run)
□ Practicar export a Unity con el placeholder
□ Preparar para rigear el modelo real cuando esté listo
□ Investigar tutoriales de rigging si es necesario

🎮 GAME DESIGNER:
□ Finalizar GDD (100%)
□ Crear greybox del nivel 1 en Unity (cubos)
□ Documentar controles detalladamente
□ Preparar moodboard de referencias
□ Crear checklist de testing

📦 DELIVERABLE: Cubo que se mueve en un nivel greybox
```

##### Hour 8-12: Core Mechanics
```
👨‍💻 PROGRAMADOR:
□ Implementar sistema de salto
□ Implementar rotación de cámara
□ Crear script base de enemigo (AI simple)
□ Implementar sistema de combate básico
□ Setup de colliders y layers
□ Integrar animaciones placeholder

🎨 MODELADOR:
□ Terminar personaje principal (>60% progreso)
□ Crear modelo de enemigo simple
□ Crear props básicos del nivel (plataformas, obstáculos)
□ Export a Unity

🎬 ANIMADOR:
□ Si el modelo está >60%, comenzar rigging
□ Si no, seguir refinando animaciones placeholder
□ Preparar Animation Controller en Unity

🎮 GAME DESIGNER:
□ Iterar greybox con feedback del equipo
□ Comenzar UI básica (Main Menu sketch)
□ Testear mecánicas tempranas
□ Documentar primeros bugs

📦 DELIVERABLE: Personaje que salta, cámara funcional, enemigo básico
```

##### Hour 12-18: Integration
```
👨‍💻 PROGRAMADOR:
□ Integrar modelo del personaje (si está listo)
□ Conectar animaciones
□ Implementar sistema de vida (HP)
□ Implementar sistema de daño
□ Crear UI de HUD (barra de vida)
□ Polish de controles

🎨 MODELADOR:
□ Finalizar personaje principal (100%)
□ Texturizado básico
□ Crear variantes de enemigos (si hay tiempo)
□ Props adicionales

🎬 ANIMADOR:
□ Rigging del personaje completo
□ Exportar animaciones finales
□ Configurar Animator Controller
□ Animation events (si aplica)

🎮 GAME DESIGNER:
□ Level design del 50% del nivel 1
□ Placement de enemigos
□ Testing de dificultad
□ Ajustar balance

📦 DELIVERABLE: Personaje final animado, enemigo funcional, 50% del nivel
```

##### Hour 18-24: First Playable Build
```
👨‍💻 PROGRAMADOR:
□ Implementar Main Menu
□ Sistema de pause
□ Game Over screen
□ Preparar primera build
□ Testing de integración

🎨 MODELADOR:
□ Pulir assets existentes
□ Crear assets secundarios
□ Ayudar con level design si termina temprano

🎬 ANIMADOR:
□ Animaciones secundarias (ataque, hit reaction)
□ Transiciones de animaciones
□ Polish de timing

🎮 GAME DESIGNER:
□ Completar nivel 1 (100% greybox o con arte)
□ SFX integration (placeholder audio)
□ Testing exhaustivo
□ Documentar bugs en GitHub

📦 DELIVERABLE: Primera build jugable de principio a fin

🎉 END OF DAY 1
□ Reunion de 30 min para review
□ Build compilada y compartida con el equipo
□ Todos juegan la build
□ Hacer lista de prioridades para mañana
□ DORMIR (crucial para día 2)
```

#### 🌞 DÍA 2: CONTENT & POLISH (24-48h)

##### Hour 24-30: Wake Up & Polish Sprint
```
☕ 24:00 - 24:30 | Morning Review
- Jugar la build del día 1
- Identificar 3 mejoras críticas
- Repriorizar tareas según progreso

👨‍💻 PROGRAMADOR:
□ Fix de bugs críticos
□ Implementar feedback de audio/visual
□ Particle effects
□ Screen shake
□ Mejorar juice del juego

🎨 MODELADOR:
□ Assets faltantes de prioridad alta
□ Mejorar texturizado
□ Props decorativos
□ Skybox/Environment

🎬 ANIMADOR:
□ Animaciones faltantes
□ Mejorar transiciones
□ IK (si hay tiempo)
□ Facial animations (si aplica y hay tiempo)

🎮 GAME DESIGNER:
□ Iterar level design con arte
□ Añadir detalles y polish
□ Integrar SFX reales
□ Testing continuo
```

##### Hour 30-36: Feature Complete
```
🎯 OBJETIVO: Todas las features P0 y P1 implementadas

👨‍💻 PROGRAMADOR:
□ Últimas features críticas
□ Settings menu (audio volume, etc)
□ Save system (si aplica)
□ Build optimization

🎨 MODELADOR:
□ Todos los modelos finalizados
□ LODs (si es necesario)
□ Props finales

🎬 ANIMADOR:
□ Todas las animaciones exportadas
□ Fine-tuning de timing
□ Ayudar con nivel 2 si hay tiempo

🎮 GAME DESIGNER:
□ Nivel 2 (si hay tiempo) o pulir nivel 1
□ Música integration
□ Tutorial prompts
□ Victory screen

📦 DELIVERABLE: Feature complete build
```

##### Hour 36-42: Bug Fixing & Balancing
```
🐛 TODOS: Focus en estabilidad

□ Playtesting intensivo (todos juegan)
□ Documentar bugs en GitHub
□ Priorizar por severidad
□ Fixing sprint

👨‍💻 PROGRAMADOR: Fix bugs técnicos
🎨 MODELADOR: Fix visual bugs, optimización
🎬 ANIMADOR: Fix animation bugs
🎮 GAME DESIGNER: Balanceo, tutoriales

⚠️ CRITICAL: No añadir features nuevas
```

##### Hour 42-46: Final Polish
```
✨ POLISH CHECKLIST:
□ Menus funcionan perfectamente
□ No hay bugs visuales obvios
□ No hay bugs de gameplay críticos
□ El juego se siente satisfactorio
□ SFX/Music están en niveles correctos
□ UI es legible y clara
□ Controles son responsivos

👨‍💻 PROGRAMADOR:
□ Compilar builds para todas las plataformas
□ Testing de cada build
□ Optimización final

🎮 GAME DESIGNER:
□ Screenshots de alta calidad
□ GIF de gameplay
□ Trailer corto (30-60s) si hay tiempo
□ Preparar descripción para itch.io
```

##### Hour 46-48: SUBMISSION
```
⏰ 46:00 - CODE FREEZE
❌ NO MÁS CAMBIOS DE CÓDIGO

46:00 - 47:00 | Final Build & Testing
□ Compilar build final
□ Testear en computadora limpia (si posible)
□ Verificar que no haya bugs de último minuto

47:00 - 47:30 | itch.io Setup
□ Subir build
□ Escribir descripción
□ Añadir screenshots/GIFs
□ Añadir controles
□ Añadir créditos del equipo
□ Revisar que el juego sea público

47:30 - 47:45 | Final Testing
□ Descargar tu propio juego de itch.io
□ Verificar que funciona
□ Que otros miembros del equipo lo prueben

47:45 - 48:00 | SUBMIT
□ Submit a la game jam
□ Screenshot de confirmación
□ Compartir link en Discord/Comunidad
□ CELEBRAR 🎉🎉🎉

🎊 POST-JAM
□ Agradecer a la comunidad
□ Jugar submissions de otros
□ Dar feedback
□ Descansar
```

### 4.3 Estrategias de Contingencia

#### Si van Retrasados (Hour 30+)

```
🚨 SCOPE CUT DECISION TREE:

¿Van >6 horas retrasados?
└─ SI → Cortar nivel 2 completamente
       Enfocar en 1 nivel pulido

¿Van >12 horas retrasados?
└─ SI → Cortar mecánicas secundarias
       Solo mantener P0

¿Van >18 horas retrasados?
└─ SI → EMERGENCY MODE
       ├─ Cortar TODAS las features no-core
       ├─ Usar assets gratuitos en vez de propios
       ├─ Reducir animaciones al mínimo
       └─ Objetivo: Loop funcional en 1 nivel
```

#### Si un Miembro se Cae

```
MODELADOR AUSENTE:
└─ Usar assets de Asset Store/Kenney.nl
└─ Animador ayuda con modelado si sabe Blender
└─ Aesthetic más minimalista

ANIMADOR AUSENTE:
└─ Usar animaciones de Mixamo
└─ Programador integra animaciones pre-hechas
└─ Modelador ayuda si sabe rigging

PROGRAMADOR AUSENTE:
└─ CRÍTICO - Muy difícil de recuperar
└─ Buscar ayuda externa urgente
└─ Considerar usar herramientas no-code (Bolt, PlayMaker)

GAME DESIGNER AUSENTE:
└─ Programador asume role de director
└─ Simplificar diseño al máximo
└─ Todos contribuyen con level design
```

### 4.4 Optimizaciones de Workflow

#### Parallel Work Techniques

```
PARALELIZACIÓN MÁXIMA:

DÍA 1 - HORAS 3-12:
┌─────────────────┐  ┌─────────────────┐
│   PROGRAMADOR   │  │   MODELADOR     │
│  Código con     │  │  Modelo con     │
│  Placeholder    │  │  Referencias    │
└────────┬────────┘  └────────┬────────┘
         │                    │
         └────────┬───────────┘
                  ↓
         ┌────────────────┐
         │    ANIMADOR    │
         │  Placeholder   │
         │   Mixamo       │
         └────────┬───────┘
                  │
                  ↓
         ┌────────────────┐
         │ GAME DESIGNER  │
         │   Greybox      │
         └────────────────┘

NINGUNO ESTÁ BLOQUEADO - TODOS PROGRESAN
```

#### Técnicas de Desbloqueo

```
TÉCNICA 1: "Assume and Mock"
- Programador no tiene el modelo? → Usa cubo
- Animador no tiene el rig? → Usa Mixamo
- Designer no tiene assets? → Usa ProBuilder

TÉCNICA 2: "Versión Degradada"
- No hay tiempo para 10 enemigos? → 1 enemigo x10
- No hay tiempo para cutscene? → Text screen
- No hay tiempo para música? → Solo SFX

TÉCNICA 3: "Good Enough"
- Animación 80% bien? → Ship it
- Nivel no es perfecto? → Ship it
- Model tiene pequeño bug visual? → Ship it
```

### 4.5 Comunicación en Crisis

#### Cuando las Cosas se Ponen Difíciles

```
🔥 HORA 36 - Todavía faltan features P0

1. LLAMAR REUNIÓN DE EMERGENCIA (15 min)
   - Todos dejan de trabajar
   - Video call o Discord

2. EVALUACIÓN HONESTA
   - ¿Qué features P0 faltan?
   - ¿Cuántas horas reales quedan?
   - ¿Es realista terminar todo?

3. DECISIÓN COLECTIVA
   - Votar qué cortar
   - Redistribuir tareas
   - Nuevo plan claro

4. EJECUTAR SIN MIRAR ATRÁS
   - No lamentar decisiones
   - Focus en lo que sí se hará
   - Mantener moral alta
```

#### Frases para Mantener el Equipo Motivado

```
❌ EVITAR:
- "No vamos a terminar"
- "Esto es imposible"
- "Deberíamos haber..."

✅ USAR:
- "Vamos bien, sigamos así"
- "Esto es lo que podemos lograr"
- "Ajustemos y sigamos"
- "Aprendemos para la próxima"
- "El juego será bueno así"
```

---

## 5. Anexos y Recursos

### 5.1 Snippets de Código Útiles

#### Player Movement Controller (Básico)

```csharp
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    [Header("Movement")]
    public float moveSpeed = 5f;
    public float sprintMultiplier = 1.5f;
    public float jumpForce = 5f;
    
    [Header("Ground Check")]
    public Transform groundCheck;
    public float groundDistance = 0.2f;
    public LayerMask groundMask;
    
    private CharacterController controller;
    private Vector3 velocity;
    private bool isGrounded;
    private float gravity = -20f;
    
    void Start()
    {
        controller = GetComponent<CharacterController>();
    }
    
    void Update()
    {
        // Ground check
        isGrounded = Physics.CheckSphere(groundCheck.position, groundDistance, groundMask);
        
        if (isGrounded && velocity.y < 0)
        {
            velocity.y = -2f; // Small negative to keep grounded
        }
        
        // Input
        float horizontal = Input.GetAxis("Horizontal");
        float vertical = Input.GetAxis("Vertical");
        
        Vector3 move = transform.right * horizontal + transform.forward * vertical;
        
        // Sprint
        float currentSpeed = Input.GetKey(KeyCode.LeftShift) ? moveSpeed * sprintMultiplier : moveSpeed;
        
        controller.Move(move * currentSpeed * Time.deltaTime);
        
        // Jump
        if (Input.GetButtonDown("Jump") && isGrounded)
        {
            velocity.y = Mathf.Sqrt(jumpForce * -2f * gravity);
        }
        
        // Apply gravity
        velocity.y += gravity * Time.deltaTime;
        controller.Move(velocity * Time.deltaTime);
    }
}
```

#### Simple Enemy AI

```csharp
using UnityEngine;
using UnityEngine.AI;

public class SimpleEnemyAI : MonoBehaviour
{
    public float detectionRange = 10f;
    public float attackRange = 2f;
    public float attackCooldown = 2f;
    public int damage = 15;
    
    private Transform player;
    private NavMeshAgent agent;
    private float lastAttackTime;
    
    void Start()
    {
        player = GameObject.FindGameObjectWithTag("Player").transform;
        agent = GetComponent<NavMeshAgent>();
    }
    
    void Update()
    {
        float distanceToPlayer = Vector3.Distance(transform.position, player.position);
        
        if (distanceToPlayer <= detectionRange)
        {
            agent.SetDestination(player.position);
            
            if (distanceToPlayer <= attackRange)
            {
                if (Time.time >= lastAttackTime + attackCooldown)
                {
                    Attack();
                    lastAttackTime = Time.time;
                }
            }
        }
    }
    
    void Attack()
    {
        Debug.Log("Enemy attacks player!");
        // Implementar daño al jugador
        // player.GetComponent<PlayerHealth>().TakeDamage(damage);
    }
}
```

#### Health System

```csharp
using UnityEngine;
using UnityEngine.UI;

public class Health : MonoBehaviour
{
    public int maxHealth = 100;
    public int currentHealth;
    public Slider healthBar; // Asignar desde el inspector
    
    void Start()
    {
        currentHealth = maxHealth;
        UpdateHealthBar();
    }
    
    public void TakeDamage(int damage)
    {
        currentHealth -= damage;
        currentHealth = Mathf.Clamp(currentHealth, 0, maxHealth);
        
        UpdateHealthBar();
        
        if (currentHealth <= 0)
        {
            Die();
        }
    }
    
    public void Heal(int amount)
    {
        currentHealth += amount;
        currentHealth = Mathf.Clamp(currentHealth, 0, maxHealth);
        UpdateHealthBar();
    }
    
    void UpdateHealthBar()
    {
        if (healthBar != null)
        {
            healthBar.value = (float)currentHealth / maxHealth;
        }
    }
    
    void Die()
    {
        Debug.Log(gameObject.name + " died!");
        // Implementar lógica de muerte
        Destroy(gameObject);
    }
}
```

### 5.2 Cheat Sheet de Git para Game Jams

```bash
# SETUP INICIAL (Día 0)
git init
git remote add origin <url-del-repo>
git add .
git commit -m "Initial project setup"
git push -u origin main

# WORKFLOW DIARIO
# 1. Antes de empezar a trabajar
git pull origin main

# 2. Trabajar en tu código

# 3. Ver qué cambios hiciste
git status

# 4. Añadir tus cambios
git add .
# O específicamente:
git add Assets/Scripts/PlayerController.cs

# 5. Commit con mensaje descriptivo
git commit -m "feat: add player jump (#001)"

# 6. Push a GitHub
git push origin main

# BRANCHES (Recomendado para equipos más experimentados)
# Crear branch para tu feature
git checkout -b feature/player-combat

# Trabajar en la branch...

# Merge a main cuando esté listo
git checkout main
git merge feature/player-combat

# EMERGENCIAS
# Olvidaste hacer pull y hay conflictos
git pull origin main
# Resolver conflictos manualmente en Unity/IDE
git add .
git commit -m "fix: resolve merge conflicts"
git push origin main

# Deshacer el último commit (cuidado!)
git reset --soft HEAD~1

# Ver historial
git log --oneline
```

### 5.3 Blender to Unity Pipeline

#### Exportación FBX óptima desde Blender

```
SETTINGS DE EXPORT EN BLENDER:

1. Seleccionar objeto(s)
2. File → Export → FBX (.fbx)
3. Configurar:

[X] Selected Objects Only (si solo quieres exportar lo seleccionado)
[X] Apply Modifiers

Transform:
   Scale: 1.00 (Unity usa misma escala)
   Forward: -Z Forward
   Up: Y Up
   [X] Apply Unit
   [X] Apply Transform

Geometry:
   [X] Apply Modifiers
   [ ] Tangent Space (Unity lo calcula)
   
Armature:
   [ ] Add Leaf Bones (problemas en Unity)
   [X] Only Deform Bones

Animation:
   [X] Bake Animation (si tiene animaciones)
   [ ] NLA Strips
   [ ] All Actions (solo si quieres exportar todas)
```

#### Convenciones de Naming

```
OBJETOS:
- PlayerCharacter_LP (LP = Low Poly)
- Enemy_Goblin_LP
- Prop_Tree_01
- Weapon_Sword

MATERIALES:
- MAT_Player_Skin
- MAT_Ground_Grass
- MAT_Metal_Rusty

TEXTURAS:
- TEX_Player_Diffuse.png
- TEX_Player_Normal.png
- TEX_Ground_Albedo.png
```

#### Troubleshooting Común

```
PROBLEMA: El modelo aparece gigante en Unity
SOLUCIÓN: En Blender, Scale = 1 antes de exportar
          En Unity Inspector, Scale = 1

PROBLEMA: Las normales están invertidas (negro)
SOLUCIÓN: Blender: Select All → Shift+N (Recalculate Normals)

PROBLEMA: El rig no funciona en Unity
SOLUCIÓN: Verificar que el rig sea tipo "Humanoid" en Unity
          FBX Export: "Only Deform Bones" checked

PROBLEMA: Las texturas no se importan
SOLUCIÓN: Texturas deben estar en mismo folder que FBX
          O embederlas: FBX Export → Path Mode: "Copy"
```

### 5.4 Recursos Externos Recomendados

#### Assets Gratuitos

**3D Models:**
- [Kenney.nl](https://kenney.nl/) - Modelos low-poly gratuitos
- [Poly Haven](https://polyhaven.com/) - Modelos, texturas, HDRIs
- [Quaternius](https://quaternius.com/) - Assets low-poly
- [Mixamo](https://www.mixamo.com/) - Personajes y animaciones

**Texturas:**
- [Poly Haven](https://polyhaven.com/textures)
- [CC0 Textures](https://cc0textures.com/)
- [TextureCan](https://www.texturecan.com/)

**Audio (SFX):**
- [Freesound.org](https://freesound.org/)
- [Kenney.nl Audio](https://kenney.nl/assets?q=audio)
- [Mixkit](https://mixkit.co/free-sound-effects/)
- [ZapSplat](https://www.zapsplat.com/)

**Música:**
- [Incompetech](https://incompetech.com/music/)
- [Purple Planet](https://www.purple-planet.com/)
- [OpenGameArt Music](https://opengameart.org/art-search-advanced?keys=&field_art_type_tid%5B%5D=12)

**UI:**
- [Kenney UI Pack](https://kenney.nl/assets/ui-pack)
- [Game-icons.net](https://game-icons.net/)

#### Unity Packages Esenciales

```
FREE:
- TextMesh Pro (UI Text mejorado)
- ProBuilder (Level design en Unity)
- Cinemachine (Cámaras cinematográficas)
- Post Processing Stack (Efectos visuales)
- Input System (Nuevo sistema de input)

PAID (OPCIONAL):
- DOTween Pro ($15 - Tweening animations)
- Odin Inspector ($55 - Mejor inspector)
```

#### Tutoriales Recomendados

**Unity Basics:**
- [Brackeys Channel](https://www.youtube.com/c/Brackeys) (YouTube)
- [Unity Learn](https://learn.unity.com/)
- [Catlike Coding](https://catlikecoding.com/unity/tutorials/)

**Blender:**
- [Blender Guru - Donut Tutorial](https://www.youtube.com/watch?v=nIoXOplUvAw)
- [Grant Abbitt Low Poly](https://www.youtube.com/c/GrantAbbitt)

**Game Design:**
- [Game Maker's Toolkit](https://www.youtube.com/c/MarkBrownGMT)
- [Extra Credits](https://www.youtube.com/extracredits)

### 5.5 Templates de Notion

#### Template: Task Card (Copiar a Notion)

```markdown
# [TASK-XXX] Título de la Tarea

**👤 Assignee:** [Nombre]
**🎭 Role:** [Programador/Modelador/Animador/Designer]
**⏰ Estimate:** X hours
**🎯 Priority:** P0/P1/P2
**📅 Sprint:** Day X
**🔗 GitHub:** #XXX

## 📝 Description
[Descripción detallada de lo que hay que hacer]

## ✅ Acceptance Criteria
- [ ] Criterio 1
- [ ] Criterio 2
- [ ] Criterio 3

## 🔗 Dependencies
- Depende de: [TASK-XXX]
- Bloquea: [TASK-XXX]

## 📦 Assets/Resources Needed
- Asset 1
- Resource 2

## 📸 References
[Links a imágenes, tutoriales, etc.]

## 🪲 Known Issues
- Issue 1 (si aplica)

## 📝 Notes
Notas adicionales del desarrollador
```

#### Template: Daily Standup (Copiar a Notion)

```markdown
# Daily Standup - [Fecha]

## ⏰ Time: [Hora]

### 👨‍💻 Programador
**Yesterday:**
- [Completé X]
- [Trabajé en Y]

**Today:**
- [Voy a trabajar en Z]
- [Voy a implementar W]

**Blockers:**
- [Bloqueado por A] / [No blockers]

---

### 🎨 Modelador
**Yesterday:**
- [Completé X]

**Today:**
- [Voy a crear Y]

**Blockers:**
- [Esperando feedback de Z] / [No blockers]

---

### 🎬 Animador
**Yesterday:**
- [Rigué personaje X]

**Today:**
- [Voy a animar Y]

**Blockers:**
- [No blockers]

---

### 🎮 Game Designer
**Yesterday:**
- [Diseñé nivel X]

**Today:**
- [Voy a testear Y]

**Blockers:**
- [No blockers]

---

## 🎯 Team Goals for Today
- Goal 1
- Goal 2

## 🚨 Critical Issues
- Issue 1 (if any)
```

---

## 📌 Quick Reference Card (Imprimir esto!)

```
╔══════════════════════════════════════════════════════════╗
║        GAME JAM SURVIVAL QUICK REFERENCE                 ║
╚══════════════════════════════════════════════════════════╝

🎯 REGLA DE ORO: Done > Perfect

📅 MILESTONES:
Day 1: First Playable (movimiento + enemigo + nivel)
Day 2: Feature Complete
Day 2 (Last 6h): Polish Only
3h Before Deadline: CODE FREEZE

🚨 CUANDO CORTAR SCOPE:
-6h retraso → Cortar nivel 2
-12h retraso → Cortar mecánicas secundarias  
-18h retraso → EMERGENCY: Solo P0 features

💬 COMUNICACIÓN:
- Daily standup: 10-15 min
- Discord/Slack siempre abierto
- Si problema >30 min → Pedir ayuda
- Si problema >2h → Cambiar enfoque

📁 WORKFLOW:
1. Pull antes de trabajar
2. Commit frecuente con mensajes claros
3. Push al final del día
4. Notion = Design
5. GitHub = Code

⚠️ EMERGENCIAS:
- Bug crítico → GitHub Issue P0
- Scope creep → Reunión de equipo
- Member ausente → Redistribuir tareas
- Tech blocker → Placeholder + continue

🔑 ASSETS DE BACKUP:
- Models: Kenney.nl, Quaternius
- Animations: Mixamo
- SFX: Freesound.org
- Music: Incompetech

📞 CONTACTOS DE EMERGENCIA:
Mentor/Asesor: [Contacto]
Discord Server: [Link]
GitHub Repo: [Link]
Notion: [Link]

🎉 RECUERDA:
- Dormir es productivo
- Comer bien mantiene el cerebro activo
- Divertirse es parte del proceso
- El juego no tiene que ser perfecto
- Aprender es el verdadero premio

╔══════════════════════════════════════════════════════════╗
║ "The only way to fail a game jam is to not finish"      ║
╚══════════════════════════════════════════════════════════╝
```

---

**FIN DEL DOCUMENTO**

---

## 📖 Cómo Usar Este Documento

### Para el Equipo Completo
1. **Antes del Jam:** Leer todo el documento al menos una vez
2. **Durante el Jam:** Consultar secciones específicas según necesidad
3. **En reuniones:** Usar como referencia para tomar decisiones

### Para Cada Rol

**Game Designer:**
- Focus en Secciones 1, 3, 4
- Responsable de mantener el GDD actualizado
- Usar templates de Notion

**Programador:**
- Focus en Secciones 1, 2, 4, 5 (snippets)
- Responsable de GitHub Issues
- Consultar troubleshooting técnico

**Modelador:**
- Focus en Secciones 1, 4, 5 (Blender pipeline)
- Consultar convenciones de naming
- Verificar specs técnicos

**Animador:**
- Focus en Secciones 1, 4, 5 (Blender pipeline)
- Coordinar con programador para animation events
- Usar checklist de animaciones

---

**Version:** 1.0  
**Created:** [Fecha]  
**For:** [Nombre del Equipo]  
**Game Jam:** [Nombre del Jam]

¡BUENA SUERTE! 🎮🚀
