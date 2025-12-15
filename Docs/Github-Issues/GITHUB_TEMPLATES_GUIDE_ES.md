# 🎯 Guía de GitHub Issue Templates para Game Jam

## 📦 Contenido

Has recibido **4 templates profesionales** optimizados para game jams:

1. **🎮 Feature Request** - Para nuevas funcionalidades y mecánicas
2. **🐛 Bug Report** - Para reportar errores y problemas
3. **🎨 Asset Request** - Para solicitar assets (modelos, animaciones, audio, UI)
4. **📐 Game Design Task** - Para tareas de diseño (level design, balanceo, testing)

## 🚀 Instalación en tu Repositorio

### Opción 1: A través de la interfaz web de GitHub (Recomendado)

1. **Ve a tu repositorio en GitHub**
   ```
   https://github.com/tu-usuario/tu-repo
   ```

2. **Navega a Settings → Features**
   - Asegúrate de que "Issues" esté activado

3. **Crea la carpeta de templates**
   - En la raíz de tu repositorio, crea esta estructura:
   ```
   .github/
   └── ISSUE_TEMPLATE/
       ├── feature_request.md
       ├── bug_report.md
       ├── asset_request.md
       ├── design_task.md
       └── config.yml
   ```

4. **Copia el contenido**
   - Abre cada archivo `.md` que te he proporcionado
   - Crea el archivo correspondiente en GitHub
   - Copia y pega el contenido

### Opción 2: Desde Git local (Más rápido si ya tienes el repo clonado)

```bash
# Desde la raíz de tu repositorio local

# Crear la estructura de carpetas
mkdir -p .github/ISSUE_TEMPLATE

# Copiar los archivos que descargaste
cp /ruta/a/.github/ISSUE_TEMPLATE/* .github/ISSUE_TEMPLATE/

# Commit y push
git add .github/
git commit -m "feat: add GitHub issue templates for game jam"
git push origin main
```

## 🎨 Personalización

### 1. Editar config.yml

**IMPORTANTE:** Actualiza estos links con los de tu proyecto:

```yaml
contact_links:
  - name: 💬 Pregunta General o Discusión
    url: https://github.com/TU-USUARIO/TU-REPO/discussions  # 👈 Cambiar aquí
    
  - name: 📚 Documentación del Proyecto
    url: https://notion.so/TU-WORKSPACE  # 👈 Cambiar aquí
    
  - name: 🎮 Game Jam Community
    url: https://discord.gg/TU-SERVIDOR  # 👈 Cambiar aquí
```

Si no usas alguno de estos (Discord, Notion, Discussions), simplemente elimina esa sección.

### 2. Personalizar Labels

Los templates usan estos labels. **Créalos en tu repo:**

Ve a: `Issues → Labels → New label`

| Label | Color | Descripción |
|-------|-------|-------------|
| 🎮 feature | `#0E8A16` | Nueva funcionalidad |
| 🐛 bug | `#D73A4A` | Error a corregir |
| 🎨 art | `#FFA500` | Assets artísticos |
| 🎵 audio | `#9C27B0` | Assets de audio |
| 📐 design | `#1E90FF` | Tareas de diseño |
| 🔴 P0-critical | `#B60205` | Prioridad crítica |
| 🟠 P1-high | `#FF6B00` | Prioridad alta |
| 🟡 P2-medium | `#FFD700` | Prioridad media |
| 🟢 P3-low | `#00FF00` | Prioridad baja |
| 🚀 ready | `#0075CA` | Listo para trabajar |
| 🔒 blocked | `#6A737D` | Bloqueado |
| 💻 code | `#000000` | Requiere programación |
| 🎬 animation | `#E99695` | Requiere animación |

**Tip:** Puedes crear estos labels automáticamente con un script. [Ver sección de automatización](#automatización-de-labels).

### 3. Ajustar Assignees Default

En cada template, puedes preconfigurar assignees:

```yaml
assignees: 'tu-programador-usuario'
```

O dejar vacío:
```yaml
assignees: ''
```

## 📋 Cómo Usar los Templates

### Crear un Nuevo Issue

1. **Ve a la pestaña Issues de tu repo**
2. **Click en "New Issue"**
3. **Selecciona el template apropiado:**

```
🎮 Feature Request       →  Para implementar mecánicas
🐛 Bug Report           →  Para reportar errores
🎨 Asset Request        →  Para solicitar modelos/audio/UI
📐 Game Design Task     →  Para diseño/testing/balanceo
```

4. **Llena el template** (no elimines las secciones, aunque estén vacías)
5. **Asigna labels, milestone, assignee**
6. **Submit issue**

### Workflow Recomendado

#### Para Features (Programador):

```markdown
1. Game Designer crea Issue con template 🎮 Feature Request
2. Define criterios de aceptación claramente
3. Lista dependencias (¿necesita assets?)
4. Asigna al programador
5. Programador acepta y empieza desarrollo
6. Al terminar, marca subtareas como completadas
7. Mueve a Testing (label o columna en Project)
8. Game Designer testea según "Testing" del template
9. Si OK → Close issue
   Si bugs → Crear Bug Report y linkear
```

#### Para Assets (Modelador/Animador):

```markdown
1. Programador o Designer crea 🎨 Asset Request
2. Especifica detalles técnicos (polys, formato, etc.)
3. Adjunta referencias visuales
4. Asigna al artist
5. Artist crea el asset según specs
6. Exporta según "Formato de Export" del template
7. Importa a Unity y testea
8. Marca checklist de integración
9. Notifica que está listo (menciona al programador)
10. Close issue
```

#### Para Bugs:

```markdown
1. Cualquiera que encuentre un bug crea 🐛 Bug Report
2. Llena pasos para reproducir (MUY IMPORTANTE)
3. Asigna prioridad P0/P1/P2/P3
4. Si es P0-critical → Notificar al equipo inmediatamente
5. Programador investiga y arregla
6. Tester verifica que esté arreglado
7. Close issue
```

#### Para Game Design:

```markdown
1. Designer crea 📐 Game Design Task
2. Especifica tipo (Level Design, Balanceo, Testing, etc.)
3. Si es testing → Lista escenarios de prueba
4. Ejecuta la tarea
5. Documenta resultados en la misma issue
6. Si genera cambios necesarios → Crea issues de Feature/Bug
7. Close issue cuando esté completo
```

## 🏷️ Sistema de Labels

### Priorización (usar SOLO UNA por issue)

```
🔴 P0-critical  →  Bloquea desarrollo, debe arreglarse YA
🟠 P1-high      →  Importante para MVP, alta prioridad
🟡 P2-medium    →  Mejora notable, media prioridad  
🟢 P3-low       →  Nice to have, baja prioridad
```

**Regla de Game Jam:** 
- Si quedan <24h → Solo trabajar en P0 y P1
- Si quedan <12h → Solo P0

### Tipo (puede tener varios)

```
🎮 feature      →  Nueva funcionalidad
🐛 bug          →  Error
🎨 art          →  Asset visual
🎵 audio        →  Asset audio
📐 design       →  Tarea de diseño
```

### Estado

```
🚀 ready        →  Listo para empezar
🔒 blocked      →  Bloqueado por dependencias
👀 in-review    →  En revisión/testing
✅ tested       →  Testeado y aprobado
```

### Rol Requerido

```
💻 code         →  Requiere programación
🎨 art-3d       →  Requiere modelado
🎬 animation    →  Requiere animación
📐 design       →  Requiere game design
```

## 🔗 Integración con Notion

Para mantener sincronización con Notion:

### En el Issue de GitHub:
```markdown
### Dependencias
- Notion: TASK-045
```

### En Notion:
```
GitHub Issue: #23
```

**Enlace bidireccional:** Siempre incluye el link del otro sistema.

## 📊 GitHub Projects (Kanban Board)

### Setup Recomendado:

1. **Crea un Project en tu repo:**
   - Ve a Projects → New Project
   - Elige "Board" template

2. **Columnas sugeridas:**
   ```
   📋 Backlog  →  Issues sin empezar
   📝 To Do    →  Priorizados para este sprint
   🔄 In Progress  →  En desarrollo activo
   🧪 Testing  →  Esperando testing/review
   ✅ Done     →  Completados
   ```

3. **Automatización:**
   - Issue creado → Va a "Backlog"
   - Issue asignado → Va a "To Do"
   - Issue cerrado → Va a "Done"

4. **Workflow:**
   ```
   Backlog → To Do (durante daily standup)
   To Do → In Progress (cuando empiezas a trabajar)
   In Progress → Testing (cuando terminas)
   Testing → Done (cuando está aprobado)
   ```

## 🤖 Automatización de Labels

### Script para crear labels automáticamente

Crea un archivo `create-labels.sh`:

```bash
#!/bin/bash

# Colores
RED="#B60205"
ORANGE="#FF6B00"
YELLOW="#FFD700"
GREEN="#00FF00"
BLUE="#0075CA"
PURPLE="#9C27B0"
BLACK="#000000"
GRAY="#6A737D"
PINK="#E99695"

# Tu repo (CAMBIAR AQUÍ)
REPO="tu-usuario/tu-repo"

# Tipos
gh label create "🎮 feature" --color "$GREEN" --description "Nueva funcionalidad" --repo $REPO
gh label create "🐛 bug" --color "$RED" --description "Error a corregir" --repo $REPO
gh label create "🎨 art" --color "$ORANGE" --description "Assets artísticos" --repo $REPO
gh label create "🎵 audio" --color "$PURPLE" --description "Assets de audio" --repo $REPO
gh label create "📐 design" --color "$BLUE" --description "Tareas de diseño" --repo $REPO

# Prioridades
gh label create "🔴 P0-critical" --color "$RED" --description "Prioridad crítica" --repo $REPO
gh label create "🟠 P1-high" --color "$ORANGE" --description "Prioridad alta" --repo $REPO
gh label create "🟡 P2-medium" --color "$YELLOW" --description "Prioridad media" --repo $REPO
gh label create "🟢 P3-low" --color "$GREEN" --description "Prioridad baja" --repo $REPO

# Estados
gh label create "🚀 ready" --color "$BLUE" --description "Listo para trabajar" --repo $REPO
gh label create "🔒 blocked" --color "$GRAY" --description "Bloqueado" --repo $REPO
gh label create "👀 in-review" --color "$YELLOW" --description "En revisión" --repo $REPO
gh label create "✅ tested" --color "$GREEN" --description "Testeado y aprobado" --repo $REPO

# Roles
gh label create "💻 code" --color "$BLACK" --description "Requiere programación" --repo $REPO
gh label create "🎨 art-3d" --color "$ORANGE" --description "Requiere modelado" --repo $REPO
gh label create "🎬 animation" --color "$PINK" --description "Requiere animación" --repo $REPO

echo "✅ Labels creados exitosamente!"
```

**Ejecutar:**
```bash
chmod +x create-labels.sh
./create-labels.sh
```

**Requisito:** Tener [GitHub CLI](https://cli.github.com/) instalado.

## 💡 Tips y Mejores Prácticas

### ✅ DO:
- **Usar templates siempre** - No crear issues en blanco
- **Llenar todas las secciones** - Incluso si dices "N/A"
- **Asignar labels correctamente** - Especialmente prioridad
- **Linkear issues relacionados** - Usa `#número` para auto-link
- **Cerrar issues cuando estén TESTEADOS** - No solo cuando el código esté hecho
- **Actualizar el issue durante el desarrollo** - Marca checkboxes mientras avanzas

### ❌ DON'T:
- No crear issues duplicados (busca primero)
- No dejar issues sin asignar
- No usar lenguaje vago ("arreglar el juego", "mejorar gráficos")
- No cerrar bugs sin verificar que estén arreglados
- No abusar de P0-critical (reservar para bloqueantes reales)

### 🎯 Durante el Game Jam:

**Day 1:**
- Crear ~10-15 issues de features core
- Asignar todas con prioridades
- Enfocar en P0 y P1

**Day 2:**
- Crear issues de bugs según se encuentren
- Crear issues de assets faltantes
- Re-priorizar según progreso

**Day 3+ (si aplica):**
- Limitar a P0 y P1 solo
- Cerrar agresivamente P2 y P3 (moverlos a "Post-Jam")

**Últimas 12 horas:**
- **NO crear nuevas features**
- Solo bugs P0 y P1
- Focus en polish visible (UI, audio, juice)

## 📱 GitHub Mobile

Los templates también funcionan en la app móvil de GitHub, útil para:
- Reportar bugs sobre la marcha
- Crear issues de assets mientras estás en Blender
- Revisar y comentar issues durante descansos

## 🆘 Troubleshooting

### "No veo los templates al crear issue"
- Verifica que los archivos estén en `.github/ISSUE_TEMPLATE/`
- Espera 5-10 minutos (GitHub puede tardar en procesar)
- Revisa que los archivos tengan extensión `.md`
- Verifica que el YAML front matter esté correcto

### "Los labels no aparecen"
- Crea los labels primero en `Issues → Labels`
- Los nombres deben coincidir EXACTAMENTE con los del template

### "Quiero modificar un template"
- Edita el archivo en `.github/ISSUE_TEMPLATE/`
- Commit y push
- Los cambios se reflejan inmediatamente en nuevos issues

## 🎓 Recursos Adicionales

- [GitHub Issue Templates Documentation](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)
- [GitHub Projects Guide](https://docs.github.com/en/issues/planning-and-tracking-with-projects)
- [GitHub CLI](https://cli.github.com/)

---

## 📞 Preguntas Frecuentes

**Q: ¿Puedo usar estos templates fuera de game jams?**
A: ¡Sí! Son genéricos pero están optimizados para desarrollo ágil rápido.

**Q: ¿Necesito usar los 4 templates?**
A: No, usa solo los que necesites. El mínimo recomendado es Feature + Bug.

**Q: ¿Puedo agregar más templates?**
A: Sí, sigue el mismo formato y agrégalos a `.github/ISSUE_TEMPLATE/`

**Q: ¿Funcionan con GitHub Free?**
A: Sí, todas estas features son gratis, incluyendo Projects.

---

**¡Buena suerte con tu Game Jam!** 🎮🚀

Si tienes preguntas, abre un issue usando el template apropiado 😉
