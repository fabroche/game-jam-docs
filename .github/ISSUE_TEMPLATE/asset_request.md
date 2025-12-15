---
name: 🎨 Asset Request
about: Solicitar creación o modificación de un asset (modelo, animación, audio, UI)
title: '[ASSET] '
labels: ['🎨 art', '🚀 ready']
assignees: ''
---

## 🎨 Asset: [Nombre del Asset]

### 📝 Descripción
<!-- Describe qué asset se necesita -->


### 🎭 Tipo de Asset
<!-- Marca UNA opción -->
- [ ] 🧊 Modelo 3D
- [ ] 🎬 Animación
- [ ] 🎵 Audio (SFX)
- [ ] 🎶 Música
- [ ] 🖼️ UI/HUD
- [ ] 🎨 Textura/Material
- [ ] 🌟 VFX/Particles

### 📐 Especificaciones Técnicas

**Para Modelos 3D:**
- **Estilo:** <!-- Low-poly, realistic, stylized, etc. -->
- **Triángulos/Polys:** <!-- <5k, <10k, etc. -->
- **Dimensiones aproximadas:** <!-- Tamaño en unidades Unity -->
- **Requiere rig:** <!-- Sí/No -->
- **Requiere animaciones:** <!-- Sí/No -->

**Para Animaciones:**
- **Personaje/Objeto:** <!-- ¿A qué modelo se aplica? -->
- **Duración:** <!-- Segundos o frames -->
- **Loop:** <!-- Sí/No -->
- **Animation Events:** <!-- ¿Necesita eventos específicos? -->

**Para Audio:**
- **Tipo:** <!-- SFX/Música -->
- **Duración:** <!-- Si es música, loop o one-shot -->
- **Mood/Estilo:** <!-- Épico, tranquilo, tenso, etc. -->
- **Trigger:** <!-- ¿Cuándo se reproduce? -->

**Para UI:**
- **Tipo:** <!-- Botón, panel, icono, etc. -->
- **Resolución:** <!-- Tamaño en píxeles -->
- **Estilo:** <!-- Seguir estilo del juego -->

### 🖼️ Referencias
<!-- Imágenes, links, sketches de referencia -->
<!-- Arrastra y suelta imágenes aquí -->


### 🔗 Dependencias
<!-- ¿Este asset depende de otro? -->
- [ ] Depende de Issue #
- [ ] Bloquea Issue #

### 📦 Entregables
<!-- Lista específica de archivos que se entregarán -->
- [ ] `asset_name.fbx` (o formato correspondiente)
- [ ] Texturas (si aplica)
- [ ] Prefab configurado en Unity (si aplica)

### ⚙️ Formato de Export
**Para 3D (Blender → Unity):**
- Formato: FBX 7.4 ASCII
- Scale: 1.00
- Forward: -Z, Up: Y
- Apply Modifiers: ✅

**Para Audio:**
- Formato: WAV (sin comprimir) o OGG
- Sample Rate: 44100 Hz
- Bit Depth: 16-bit

### ⏱️ Estimación
**Tiempo:** X horas

### 🎯 Prioridad
<!-- Marca UNA opción -->
- [ ] 🔴 P0-critical (Bloqueante, necesario para MVP)
- [ ] 🟠 P1-high (Importante para MVP)
- [ ] 🟡 P2-medium (Mejora visual/audio notable)
- [ ] 🟢 P3-low (Polish, nice to have)

### 📅 Sprint
**Target:** Day X

### 👤 Asignado a
<!-- Mencionar al artist/compositor -->
@username

---
### 📝 Notas Adicionales
<!-- Cualquier detalle extra que el artista deba saber -->


### ✅ Checklist de Integración
<!-- Para cuando esté listo -->
- [ ] Asset exportado correctamente
- [ ] Importado en Unity sin errores
- [ ] Configurado en prefab (si aplica)
- [ ] Testeado en escena
- [ ] Comunicado al programador que está listo
