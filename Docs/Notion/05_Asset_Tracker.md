# 📦 Fase 4: Asset Tracker

**Tiempo estimado:** 25 minutos

## 🎯 Objetivo

Crear un inventario completo de todos los assets del juego (modelos 3D, animaciones, audio, UI) con tracking de status, previews y metadata técnica.

---

## 📊 Estructura del Asset Tracker

```
📦 Asset Tracker
│
├── 📊 Base de Datos: "Assets"
│   ├── Propiedades
│   │   ├── Asset Name (título)
│   │   ├── Type (select)
│   │   ├── Status (select)
│   │   ├── Assignee (persona)
│   │   ├── Priority (select)
│   │   ├── File Path (text)
│   │   ├── Preview (files & media)
│   │   ├── Specs (text)
│   │   ├── Integrated (checkbox)
│   │   └── Notes (text)
│   │
│   └── Vistas
│       ├── 🎨 All Assets (galería)
│       ├── 📊 By Type (board)
│       ├── ✅ By Status (board)
│       └── 🎯 Priority Assets
```

---

## 🛠️ Instrucciones Paso a Paso

### Paso 1: Crear la Base de Datos de Assets

1. Abre tu página template
2. Busca la sección `## 📦 Asset Tracker`
3. Borra el placeholder
4. Escribe `/database` → **"Database - Inline"**
5. Nombra la base de datos: `Assets`

### Paso 2: Configurar Propiedades

#### Lista Completa de Propiedades

| Propiedad | Tipo | Configuración |
|-----------|------|---------------|
| **Asset Name** | Title | (Por defecto) |
| **Type** | Select | 3D Model, Animation, Texture, Audio SFX, Music, UI Element, VFX, Other |
| **Status** | Select | 📋 To Do, 🔄 In Progress, 🔍 Review, ✅ Done, 🔗 Integrated |
| **Assignee** | Person | - |
| **Priority** | Select | 🔴 P0, 🟠 P1, 🟡 P2, 🟢 P3 |
| **File Path** | Text | Ubicación del archivo |
| **Preview** | Files & media | Imagen/archivo del asset |
| **Poly Count** | Number | (Solo para 3D models) |
| **Duration** | Number | (Solo para audio/animaciones, en segundos) |
| **Resolution** | Text | (Para texturas/UI: "1024x1024") |
| **Integrated** | Checkbox | ¿Está en Unity? |
| **Related Task** | Relation | Relacionar con base de datos Tasks |
| **Notes** | Text | Notas técnicas |

#### Configurar Select: "Type"

Añade estas opciones:
- `🎨 3D Model` (Morado)
- `🎬 Animation` (Rosa)
- `🖼️ Texture` (Azul)
- `🎵 Audio SFX` (Amarillo)
- `🎼 Music` (Naranja)
- `🖥️ UI Element` (Verde)
- `✨ VFX` (Celeste)
- `📦 Other` (Gris)

#### Configurar Select: "Status"

Añade estas opciones:
- `📋 To Do` (Gris)
- `🔄 In Progress` (Azul)
- `🔍 Review` (Amarillo)
- `✅ Done` (Verde claro)
- `🔗 Integrated` (Verde oscuro)

#### Configurar Relation: "Related Task"

1. Tipo: **Relation**
2. Relacionar con: **Tasks** (la base de datos que creaste en Fase 3)
3. Esto permite vincular un asset con la tarea que lo requiere

### Paso 3: Crear Vistas

#### Vista 1: Gallery View (Principal)

1. Click en el botón de vista → **"Gallery"**
2. **Nombre:** `🎨 All Assets`
3. **Card preview:** `Preview`
4. **Card size:** Medium

**Configuración:**
- **Show:** Type, Status, Assignee
- **Sort by:** Priority, luego Type
- Esta vista muestra miniaturas de todos los assets

#### Vista 2: By Type

1. `+ Add a view` → **"Board"**
2. **Nombre:** `📊 By Type`
3. **Group by:** `Type`

**Uso:** Ver todos los modelos juntos, todas las animaciones juntas, etc.

#### Vista 3: By Status

1. `+ Add a view` → **"Board"**
2. **Nombre:** `✅ By Status`
3. **Group by:** `Status`

**Uso:** Pipeline de producción - qué está en progreso, qué falta integrar

#### Vista 4: Priority Assets

1. `+ Add a view` → **"Table"**
2. **Nombre:** `🎯 Priority`
3. **Filter:** `Priority` → `Is` → `🔴 P0` OR `🟠 P1`
4. **Filter:** `Status` → `Is not` → `🔗 Integrated`

**Uso:** Focus en los assets críticos que aún faltan

#### Vista 5: Not Integrated

1. `+ Add a view` → **"Table"**
2. **Nombre:** `⚠️ Needs Integration`
3. **Filter:** `Status` → `Is` → `✅ Done`
4. **Filter:** `Integrated` → `Is` → `Unchecked`

**Uso:** Assets terminados pero no integrados a Unity aún

---

## 📋 Template para Añadir Assets

Cuando añadas un asset, usa esta estructura en la página interna:

### Template: 3D Model Asset

```markdown
## 📝 Asset Information

**Type:** 🎨 3D Model
**Created for:** [Descripción del uso]

---

## 🎨 Technical Specifications

| Spec | Value |
|------|-------|
| **Poly Count** | [X triángulos] |
| **Vertices** | [X verts] |
| **Textures** | [Sí/No] |
| **Rigged** | [Sí/No] |
| **Animated** | [Sí/No] |

### Dimensions
- **Scale:** [X × Y × Z] units
- **Pivot Point:** [Center / Bottom / etc.]

### Materials
- Material 1: [Nombre y tipo]
- Material 2: [Si aplica]

---

## 📁 File Locations

**Source (Blender):** `[Path]/[Name].blend`
**Export (FBX):** `[Path]/[Name].fbx`
**Unity Location:** `Assets/Models/[Name].fbx`

---

## 🔗 Related Assets

- Textures: [Link a texture assets]
- Animations: [Link a animation assets]

---

## ✅ Production Checklist

- [ ] Modelo base completado
- [ ] UVs unwrapped correctamente
- [ ] Texturas aplicadas
- [ ] Normals correctas
- [ ] Exportado a FBX
- [ ] Importado en Unity
- [ ] Testeado en escena
- [ ] Performance aceptable

---

## 📸 Preview

[Subir render/screenshot del modelo aquí]

---

## 📝 Notes

[Notas técnicas, problemas encontrados, etc.]
```

### Template: Animation Asset

```markdown
## 📝 Asset Information

**Type:** 🎬 Animation
**Character:** [Nombre del personaje]
**Action:** [Idle / Walk / Attack / etc.]

---

## 🎨 Technical Specifications

| Spec | Value |
|------|-------|
| **Duration** | [X] segundos |
| **Frame Rate** | 30 fps |
| **Frame Count** | [X frames] |
| **Loop** | [Sí/No] |
| **Root Motion** | [Sí/No] |

### Animation Events (if applicable)
- Frame [X]: [Event name] - [Description]

---

## 📁 File Locations

**Source (Blender):** `[Path]/[Name].blend`
**Export (FBX):** `[Path]/[Name].fbx`
**Unity Location:** `Assets/Animations/[Name].fbx`

---

## ✅ Production Checklist

- [ ] Animación blocked out
- [ ] Timing refinado
- [ ] Secondary motion añadido
- [ ] Exportado correctamente
- [ ] Importado en Unity
- [ ] Configurado en Animator Controller
- [ ] Transiciones funcionando

---

## 📸 Preview

[Subir GIF de la animación aquí]

---

## 📝 Notes
```

### Template: Audio Asset

```markdown
## 📝 Asset Information

**Type:** 🎵 Audio SFX / 🎼 Music
**Usage:** [Cuándo se reproduce]

---

## 🎨 Technical Specifications

| Spec | Value |
|------|-------|
| **Duration** | [X] segundos |
| **Format** | WAV / MP3 / OGG |
| **Sample Rate** | 44.1 kHz |
| **Bit Depth** | 16-bit |
| **Channels** | Mono / Stereo |
| **Loop** | [Sí/No] |

---

## 📁 File Locations

**Source:** `[Path]/[Name].[ext]`
**Unity Location:** `Assets/Audio/[SFX or Music]/[Name].[ext]`

---

## 🔗 Trigger

**Event:** [Qué acción del jugador/juego lo dispara]
**Script:** [Script que lo llama, si aplica]

---

## ✅ Production Checklist

- [ ] Audio grabado/descargado
- [ ] Editado (fade in/out, trim, etc.)
- [ ] Normalizado
- [ ] Exportado en formato correcto
- [ ] Importado en Unity
- [ ] Integrado en AudioSource/AudioManager
- [ ] Volumen balanceado

---

## 📝 Notes

**Source:** [Freesound / Incompetech / Grabación propia / etc.]
**License:** [CC0 / CC-BY / etc.]
```

---

## 💡 Tips de Uso del Asset Tracker

### Durante la Fase de Planificación

1. **Lista exhaustiva de assets:**
   - Game Designer y Artistas hacen brainstorm
   - Crear entrada para CADA asset necesario
   - Asignar prioridades realistas

2. **Budget de assets:**
   - Definir límite de poly count total
   - Priorizar assets que se reutilizan (modular design)

### Durante la Producción

1. **Pipeline claro:**
   ```
   📋 To Do → 🔄 In Progress → 🔍 Review → ✅ Done → 🔗 Integrated
   ```

2. **Review process:**
   - Modelador marca como "Review" cuando termina
   - Programador o Designer revisa
   - Si OK → "Done"
   - Si necesita cambios → vuelve a "In Progress" con notas

3. **Integración inmediata:**
   - Cuando un asset esté "Done", integrarlo a Unity lo antes posible
   - Marcar checkbox "Integrated"
   - Esto evita acumulación de assets al final

### Organización de Archivos

Mantén una convención de nombres consistente:

**3D Models:**
```
Character_Player_LP.fbx
Enemy_Goblin_LP.fbx
Prop_Tree_01.fbx
```

**Animations:**
```
Player_Idle.fbx
Player_Walk.fbx
Enemy_Attack.fbx
```

**Audio:**
```
SFX_Jump.wav
SFX_Footstep_01.wav
Music_MainTheme_Loop.ogg
```

**Texturas:**
```
TEX_Player_Diffuse.png
TEX_Ground_Normal.png
```

### Integración con Task Board

Cuando crees una tarea de "Crear modelo de personaje":
1. Crea la tarea en Task Board
2. Crea el asset en Asset Tracker
3. Usa la propiedad "Related Task" para vincularlos
4. Ahora puedes ver qué task requiere qué asset

---

## 🎨 Mejoras Opcionales

### Añadir Property: "Source"

Para rastrear de dónde vino el asset:

- `In-house` - Creado por el equipo
- `Asset Store` - Unity Asset Store
- `Freesound` - Freesound.org
- `Mixamo` - Mixamo.com
- `Kenney` - Kenney.nl
- `Other` - Otra fuente

### Añadir Property: "License"

Importante para assets externos:

- `CC0` - Dominio público
- `CC-BY` - Requiere atribución
- `Free` - Uso gratuito
- `Purchased` - Comprado

### Subir Previews

Para cada asset, sube una preview:
- Modelos: Screenshot o render desde Blender
- Animaciones: GIF del ciclo
- Audio: (No aplica, pero puedes subir waveform screenshot)
- UI: Screenshot del elemento

Esto hace que la Gallery View sea super visual y útil.

---

## ✅ Verificación

Al terminar esta fase, tu Asset Tracker debe tener:

- [x] Base de datos con todas las propiedades
- [x] Vista Gallery mostrando previews
- [x] Vistas By Type y By Status
- [x] Vista de Priority Assets
- [x] Vista de Not Integrated
- [x] Relación configurada con Task Board
- [x] Templates listos para cada tipo de asset

---

## 🚀 Próximo Paso

Con tus assets organizados, ahora gestiona los bugs:

👉 **`06_Bug_Log.md`** - Crear el sistema de tracking de bugs

---

## 📸 Vista Previa Conceptual

Tu Asset Tracker en Gallery View debería verse así:

```
╔═══════════════════════════════════════════════════════════╗
║              📦 ASSET TRACKER (GALLERY)                   ║
╠═══════════════════════════════════════════════════════════╣
║                                                           ║
║  ┌─────────┐  ┌─────────┐  ┌─────────┐  ┌─────────┐    ║
║  │ [IMG]   │  │ [IMG]   │  │ [IMG]   │  │ [IMG]   │    ║
║  │ Player  │  │ Enemy   │  │ Sword   │  │ Tree    │    ║
║  │ 🎨 Model│  │ 🎨 Model│  │ 🎨 Model│  │ 🎨 Model│    ║
║  │ 🔗 Done │  │ 🔄 WIP  │  │ ✅ Done │  │ 📋 ToDo │    ║
║  │ @Artist │  │ @Artist │  │ @Artist │  │ @Artist │    ║
║  └─────────┘  └─────────┘  └─────────┘  └─────────┘    ║
║                                                           ║
║  ┌─────────┐  ┌─────────┐  ┌─────────┐                  ║
║  │ 🎵      │  │ 🎬      │  │ 🖼️      │                  ║
║  │ Jump SFX│  │ Walk    │  │ UI Btn  │                  ║
║  │ ✅ Done │  │ 🔄 WIP  │  │ 📋 ToDo │                  ║
║  └─────────┘  └─────────┘  └─────────┘                  ║
╚═══════════════════════════════════════════════════════════╝
```

---

**¿Completaste el Asset Tracker?** ✅ Continúa con el Bug Log.

---

## 🧭 Navegación

**📍 Estás en:** Fase 4 - Asset Tracker

| ⬅️ Anterior | 🏠 Inicio | ➡️ Siguiente |
|------------|----------|-------------|
| [✅ Task Board](04_Task_Board.md) | [🏠 README](README.md) | [🐛 Bug Log](06_Bug_Log.md) |

**🔗 Todas las Guías:**
[Plan](00_PLAN_IMPLEMENTACION.md) • [Setup](01_Setup_Inicial.md) • [Dashboard](02_Dashboard.md) • [GDD](03_GDD.md) • [Tasks](04_Task_Board.md) • [Assets](05_Asset_Tracker.md) • [Bugs](06_Bug_Log.md) • [Schedule](07_Schedule_Milestones.md) • [Resources](08_Resources.md) • [Checklist](CHECKLIST_IMPLEMENTACION.md)

---
