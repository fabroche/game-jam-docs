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