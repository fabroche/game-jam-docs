# 📚 Documentazione Tecnica - Team Game Jam Unity 6

## Indice
1. [Operazioni di Team](#1-operazioni-di-team)
2. [Gestione dei Task (Notion + GitHub Issues)](#2-gestione-dei-task-notion--github-issues)
3. [Game Design Document (GDD) per Game Jam](#3-game-design-document-gdd-per-game-jam)
4. [Piano d'Azione Operativo](#4-piano-dazione-operativo)
5. [Appendici e Risorse](#5-appendici-e-risorse)

---

## 1. Operazioni di Team

### 1.1 Principi Fondamentali

#### Regola d'Oro: "Done is Better than Perfect"
In una game jam, un gioco funzionale e semplice **sempre** supera un progetto ambizioso non finito.

#### Comunicazione Costante
- **Daily Stand-ups:** 10-15 minuti all'inizio di ogni giorno
  - Cosa ho fatto ieri?
  - Cosa farò oggi?
  - Ho dei blocchi?
  
- **Canale di Comunicazione:** Usare Discord/Slack con canali specifici:
  - `#general` - Coordinamento generale
  - `#art-assets` - Condividere modelli/animazioni
  - `#code` - Problemi tecnici
  - `#design` - Meccaniche e feedback
  - `#builds` - Versioni giocabili

### 1.2 Flusso di Lavoro per Ruolo

```
┌─────────────────────────────────────────────────────────┐
│                    GAME DESIGNER                        │
│  Definire concetto → Documentare meccaniche → Level design │
└───────────────────┬─────────────────────────────────────┘
                    ↓
        ┌───────────┴───────────┐
        ↓                       ↓
┌───────────────┐       ┌───────────────┐
│ MODELLATORE 3D│       │  PROGRAMMATORE│
│ Creare assets │←──────│ Specificare   │
│               │       │ necessità     │
└───────┬───────┘       └───────┬───────┘
        ↓                       ↓
┌───────────────┐       ┌───────────────┐
│   ANIMATORE   │       │  INTEGRAZIONE │
│ Rig e animaz  │──────→│  IN UNITY     │
└───────────────┘       └───────┬───────┘
                                ↓
                        ┌───────────────┐
                        │ GAME DESIGNER │
                        │ Testing/Level │
                        │   Design      │
                        └───────────────┘
```

### 1.3 Gestione delle Dipendenze

#### Dipendenze Critiche (Bloccano il lavoro)
```
Modellatore → Animatore → Programmatore
   ↓
Se il modellatore non consegna il personaggio,
l'animatore NON può fare il rig,
il programmatore NON può integrarlo.
```

**Soluzione: Assets Temporanei (Placeholders)**

**Programmatore:**
```csharp
// USA SEMPRE placeholders per non bloccarti
// Invece di aspettare il modello finale:

public class PlayerController : MonoBehaviour
{
    // Placeholder: Cubo di Unity con capsule collider
    // Sostituire quando arriva il modello finale
    
    [Header("Riferimenti - SOSTITUIRE CON MODELLO FINALE")]
    public GameObject visualModel; // Assegnare cubo temporaneamente
    
    void Start()
    {
        if (visualModel == null)
        {
            Debug.LogWarning("⚠️ Usando placeholder - sostituire con modello finale");
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

**Modellatore:**
- Crea un cubo/cilindro con le dimensioni corrette PER PRIMO
- Invialo al programmatore il Giorno 1
- Lavora sul modello dettagliato in parallelo

**Animatore:**
- Usa personaggi Mixamo come placeholder
- Esporta animazioni generiche che funzionano con qualsiasi rig umanoide

### 1.4 Riunioni Chiave

#### Giorno 0: Kickoff (2-3 ore)
- Brainstorming del concetto
- Definire scope realistico
- Assegnare task iniziali
- Configurare repository e Notion

#### Giorni 1-3: Check-in Giornalieri (15 min)
- La mattina o il pomeriggio (secondo disponibilità)
- Formato stand-up

#### Giorno 4-5: Playtesting Interno (1 ora)
- Tutti giocano la build
- Annotare bug e miglioramenti
- Dare priorità ai fix

#### Ultima Notte: Code Freeze
- **6 ore prima della deadline:** NO PIÙ FEATURES
- Solo fix critici
- Build di testing continue

### 1.5 Risoluzione dei Conflitti

#### Conflitto di Priorità
```
Situazione: L'animatore vuole fare 10 animazioni,
il programmatore ha tempo solo per integrarne 5.

Soluzione:
1. Game Designer dà priorità alle 5 più importanti
2. Si documentano le 5 rimanenti come "Post-Jam Features"
3. Si procede con quelle prioritarie
```

#### Conflitto Tecnico
```
Situazione: Il modello è troppo pesante per il target di performance.

Soluzione:
1. Programmatore misura FPS e identifica il problema
2. Modellatore crea versione Low-Poly in 1-2 ore
3. Se non c'è tempo, usare asset gratuito di backup
```

**Regola di Escalation:**
- Se un problema richiede >30 min per discuterlo → Consultare advisor/mentor
- Se un problema richiede >2 ore per risolverlo → Cambiare approccio

---

## 2. Gestione dei Task (Notion + GitHub Issues)

### 2.1 Perché usare entrambi gli strumenti?

**Notion:** Design, pianificazione, documentazione
**GitHub Issues:** Bug, features tecniche, tracking dello sviluppo

```
┌──────────────────────────────────────────────┐
│               NOTION                         │
│  - GDD                                       │
│  - Concept Art                               │
│  - Liste Assets                              │
│  - Note Riunioni                             │
│  - Schizzi Level Design                      │
└──────────────────────────────────────────────┘
                    ↕️
        (Riferimento reciproco)
                    ↕️
┌──────────────────────────────────────────────┐
│            GITHUB ISSUES                     │
│  - Implementazione Features                  │
│  - Tracking Bug                              │
│  - Code Reviews                              │
│  - Documentazione Tecnica                    │
└──────────────────────────────────────────────┘
```

### 2.2 Configurazione Notion

#### Struttura Workspace

```
Game Jam Project Workspace
│
├── 📄 Home / Dashboard
│   ├── Countdown Timer
│   ├── Quick Links
│   └── Contatti Team
│
├── 📋 Game Design Document
│   ├── Concept
│   ├── Meccaniche
│   ├── Stile Arte
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
│   ├── Modelli
│   ├── Animazioni
│   ├── Audio
│   └── Elementi UI
│
├── 🐛 Bug Log
│
├── 📅 Schedule & Milestones
│
└── 📚 Risorse
    ├── Immagini di Riferimento
    ├── Tutorial
    └── Fonti Assets
```

#### Template: Task Card in Notion

```markdown
# [TASK-001] Implementare Movimento del Giocatore

**Ruolo:** Programmatore
**Priorità:** 🔴 Alta
**Stato:** In Progress
**Stima:** 3 ore
**GitHub Issue:** #12

## Descrizione
Implementare sistema di movimento base con WASD e salto con Spazio.

## Requisiti
- [ ] Movimento orizzontale (A/D)
- [ ] Movimento verticale (W/S)
- [ ] Sistema di salto
- [ ] Rotazione camera con mouse

## Dipendenze
- Modello placeholder del giocatore (TASK-005)

## Assets Necessari
- Nessuno (usare cubo placeholder)

## Note
Usare CharacterController invece di Rigidbody per maggiore controllo.

## Riferimenti
- [Unity CharacterController Docs](link)
```

#### Proprietà Database in Notion

Per il **Task Board**, creare un database con queste proprietà:

| Proprietà | Tipo | Valori |
|-----------|------|--------|
| Task Name | Title | - |
| Assignee | Person | Membri Team |
| Role | Select | Programmatore, Modellatore, Animatore, Designer |
| Priority | Select | 🔴 Alta, 🟡 Media, 🟢 Bassa |
| Status | Select | Backlog, To Do, In Progress, Testing, Done |
| Estimate | Number | Ore |
| Sprint | Select | Day 1, Day 2, Day 3, Day 4, Day 5, Polish |
| Tags | Multi-select | Core, Polish, Bug, Feature, Art, Code, Audio |
| GitHub Link | URL | - |

### 2.3 Configurazione GitHub Issues

#### Label Raccomandati

```
Tipo:
🎮 feature        - Nuova funzionalità
🐛 bug           - Errore da correggere
🎨 art           - Assets artistici
🎵 audio         - Assets audio
📚 documentation - Documentazione
🔧 refactor      - Miglioramento codice

Priorità:
🔴 P0-critical   - Blocca lo sviluppo
🟠 P1-high       - Importante per MVP
🟡 P2-medium     - Miglioramento significativo
🟢 P3-low        - Nice to have

Stato:
🚀 ready         - Pronto per lavorare
🔒 blocked       - In attesa di dipendenza
👀 in-review     - In revisione
✅ tested        - Testato e approvato

Ruolo:
💻 code          - Richiede programmazione
🎨 art-3d        - Richiede modellazione
🎬 animation     - Richiede animazione
📐 design        - Richiede design
```

#### Template: Issue di Feature

```markdown
## 🎮 Feature: Sistema di Combattimento Base

### Descrizione
Implementare sistema di combattimento corpo a corpo con attacco base.

### Criteri di Accettazione
- [ ] Il giocatore può premere LMB per attaccare
- [ ] L'animazione di attacco si riproduce correttamente
- [ ] L'attacco causa danno ai nemici in un raggio di 2 unità
- [ ] C'è un cooldown di 0.5 secondi tra attacchi

### Dipendenze
- #15 Integrazione animazioni
- Notion: TASK-023 (Animazione attacco)

### Subtask Tecnici
- [ ] Creare script `MeleeAttack.cs`
- [ ] Implementare rilevamento collisione (OverlapSphere)
- [ ] Connettere con Animator
- [ ] Aggiungere feedback visivo (particle effect)

### Assets Richiesti
- Animazione: attack_01.fbx
- VFX: hit_spark prefab
- SFX: sword_swing.wav

### Note di Implementazione
```csharp
// Esempio di rilevamento nemici
Collider[] hits = Physics.OverlapSphere(attackPoint.position, attackRadius, enemyLayer);
```

### Stima
4 ore

### Assegnato a
@programmatore-username

### Labels
`🎮 feature` `🟠 P1-high` `💻 code` `Day 2`
```

#### Template: Issue di Bug

```markdown
## 🐛 Bug: Il giocatore attraversa il pavimento

### Descrizione del Problema
Quando il giocatore salta vicino a una rampa, a volte attraversa il pavimento e cade nel vuoto.

### Passi per Riprodurre
1. Avviare il livello 1
2. Andare alla rampa vicino allo spawn
3. Saltare 3-4 volte di seguito
4. Il bug si verifica ~50% delle volte

### Comportamento Atteso
Il giocatore dovrebbe collidere correttamente con il pavimento.

### Comportamento Attuale
Il giocatore attraversa il collider e cade.

### Screenshots/Video
[Allegare screenshot o GIF]

### Informazioni Tecniche
- Versione Unity: 6.0
- Script interessato: `PlayerController.cs`
- Collider: Capsule Collider sul giocatore
- Ground: Mesh Collider

### Possibile Causa
Il Mesh Collider potrebbe non essere convesso. Verificare configurazione.

### Priorità
🔴 P0-critical - Rompe il gameplay

### Assegnato a
@programmatore-username

### Labels
`🐛 bug` `🔴 P0-critical` `💻 code`
```

### 2.4 Workflow di Integrazione Notion ↔ GitHub

#### Processo: Task di Feature

```
1. Game Designer crea task in Notion
   └─→ "TASK-045: Aggiungere power-up di velocità"
   
2. Aggiunge dettagli, riferimenti, sketch
   
3. Programmatore crea Issue in GitHub
   └─→ "#45 Implement Speed Power-up"
   
4. Aggiunge link di GitHub in Notion
   Notion: "GitHub Issue: #45"
   
5. GitHub Issue include link a Notion
   GitHub: "Design Doc: [Notion Link]"
   
6. Sviluppo in GitHub
   - Commit con "#45" per auto-link
   - Code review
   - Merge a dev branch
   
7. Update in Notion
   - Status: Testing
   - Build dove è disponibile
   
8. Game Designer testa
   
9. Se OK:
   - Notion: Status → Done
   - GitHub: Close Issue
```

#### Convenzione di Naming

**Notion:**
```
[TASK-XXX] Descrizione Chiara
Esempi:
- [TASK-001] Implementare movimento del giocatore
- [TASK-002] Modellare personaggio principale
- [TASK-003] Animare ciclo di camminata
- [TASK-004] Progettare livello 1
```

**GitHub:**
```
#XXX Descrizione in inglese (opzionale ma professionale)
Esempi:
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

Prefissi:
feat - Nuova feature
fix - Bug fix
art - Asset artistico
anim - Animazione
design - Cambio di design
refactor - Miglioramento codice
docs - Documentazione
```

### 2.5 Workflow Giornaliero Raccomandato

```
🌅 MATTINA (9:00 - 9:15)
- Daily stand-up
- Rivedere Notion Task Board
- Spostare task a "In Progress"
- Verificare GitHub Issues assegnati

💻 LAVORO (9:15 - 13:00)
- Sviluppare task
- Commit frequenti
- Aggiornare status in tempo reale

🍕 PRANZO (13:00 - 14:00)
- Pausa

💻 LAVORO (14:00 - 18:00)
- Continuare sviluppo
- Code reviews
- Testing interno

📊 POMERIGGIO (18:00 - 18:30)
- Aggiornare Notion con progresso
- Chiudere Issues completati
- Creare Issues per bug trovati
- Preparare build se è giorno di milestone

🌙 SERA (18:30+)
- Tempo flessibile secondo necessità
- Negli ultimi giorni: crunch time (opzionale)
```

---

## 3. Game Design Document (GDD) per Game Jam

### 3.1 Cos'è un GDD?

Il **Game Design Document** è il documento principale che definisce cos'è il tuo gioco. In una game jam, deve essere:
- ✅ Conciso (5-10 pagine massimo)
- ✅ Visuale (schizzi, riferimenti)
- ✅ Azionabile (tutti sanno cosa fare)
- ❌ NON esaustivo (non è un GDD di produzione AAA)

### 3.2 Struttura GDD per Game Jam

#### Template Completo

```markdown
# 🎮 [NOME DEL GIOCO] - Game Design Document

## 📋 Informazioni Generali

**Titolo:** [Nome del Gioco]
**Tema del Jam:** [Tema se applicabile]
**Genere:** [Piattaforme, Puzzle, Shooter, ecc.]
**Piattaforma:** PC (Windows/Mac/Linux)
**Durata del Gioco:** 5-10 minuti
**Pubblico Target:** Giocatori casuali

**Team:**
- Game Designer: [Nome]
- Programmatore: [Nome]
- Modellatore 3D: [Nome]
- Animatore: [Nome]

**Timeline:**
- Inizio: [Data]
- Fine: [Data]
- Durata: 48/72 ore

---

## 🎯 Concetto del Gioco

### High Concept (Una riga)
> "È [Gioco Conosciuto] meets [Altro Gioco], dove [Twist Unico]"
>
> Esempio: "È Super Mario meets Portal, dove usi portali per superare piattaforme"

### Core Loop (Ciclo centrale di gameplay)
```
1. Il giocatore [azione principale]
   ↓
2. Questo causa [conseguenza/sfida]
   ↓
3. Il giocatore deve [soluzione/obiettivo]
   ↓
4. Al completamento, ottiene [ricompensa/progressione]
   ↓
[Ritorna al passo 1 con maggiore difficoltà]
```

**Esempio:**
```
1. Il giocatore esplora il livello
   ↓
2. Trova nemici che bloccano il percorso
   ↓
3. Deve usare combattimento o stealth per superarli
   ↓
4. Ottiene chiave per aprire porta al livello successivo
   ↓
[Livello successivo più difficile]
```

### Pillars (Pilastri di design)
I 3 elementi fondamentali che definiscono il tuo gioco:

1. **[Pilastro 1]** - Es: "Movimento fluido e soddisfacente"
2. **[Pilastro 2]** - Es: "Combattimento tattico basato sul timing"
3. **[Pilastro 3]** - Es: "Esplorazione ricompensata"

---

## 🕹️ Meccaniche

### Meccaniche Core (Imprescindibili per MVP)

#### 1. Movimento
- **WASD:** Movimento in 8 direzioni
- **Spazio:** Salto (altezza: 2m, durata: 0.5s)
- **Shift:** Sprint (velocità x1.5)
- **Mouse:** Controllo camera (3a persona)

**Riferimenti Tecnici:**
- CharacterController
- Velocità base: 5 m/s
- Gravità: -20 m/s²

#### 2. Combattimento
- **LMB:** Attacco base (cooldown: 0.7s)
- **RMB:** Blocco (riduce danno 50%)
- **Q:** Abilità speciale (cooldown: 5s)

**Sistema di Danno:**
- HP Giocatore: 100
- Attacco base: 20 danni
- HP Nemico: 50

#### 3. [Altra Meccanica Core]
[Descrizione dettagliata]

### Meccaniche Secondarie (Se c'è tempo)

#### 1. Sistema di Inventario
- Capacità: 5 oggetti
- Oggetti raccoglibili: Pozioni, chiavi

#### 2. [Altra Meccanica Secondaria]
[Descrizione]

**⚠️ REGOLA:** Se rimangono 24 ore o meno, NON implementare meccaniche secondarie.

---

## 🎨 Direzione Artistica

### Stile Visivo
**Riferimento:** [Link a moodboard in Notion/Pinterest]

**Descrittore:** Low-poly colorato con illuminazione cell-shaded

**Palette di Colori:**
- Primario: `#FF6B6B` (Rosso)
- Secondario: `#4ECDC4` (Turchese)
- Accento: `#FFE66D` (Giallo)

### Assets 3D

#### Lista Modelli (Prioritizzata)

| Asset | Priorità | Triangoli | Status | Assignee |
|-------|----------|-----------|--------|----------|
| Personaggio Giocatore | P0 | <5k | To Do | Modellatore |
| Nemico Tipo A | P0 | <3k | To Do | Modellatore |
| Pavimento/Ground Tiles | P0 | <500 | To Do | Modellatore |
| Props decorativi | P2 | <1k | Backlog | Modellatore |

**Budget di Performance:**
- Totale triangoli sullo schermo: <100k
- Target draw calls: <100

### Animazioni

#### Lista Animazioni (Prioritizzata)

| Animazione | Personaggio | Frames | Priorità | Status |
|------------|-------------|--------|----------|--------|
| Idle | Giocatore | 30 | P0 | To Do |
| Walk | Giocatore | 20 | P0 | To Do |
| Run | Giocatore | 16 | P0 | To Do |
| Jump_Start | Giocatore | 8 | P0 | To Do |
| Jump_Loop | Giocatore | 8 | P0 | To Do |
| Jump_Land | Giocatore | 8 | P1 | Backlog |
| Attack_01 | Giocatore | 24 | P0 | To Do |
| Hit_React | Giocatore | 12 | P1 | Backlog |
| Death | Giocatore | 30 | P1 | Backlog |

**⚠️ MINIMO VITALE:**
- Idle
- Walk
- Jump (può essere un singolo clip generico)
- Attack

### Audio

#### SFX Necessari

| Effetto | Trigger | Priorità | Fonte |
|---------|---------|----------|-------|
| Footsteps | Quando cammina | P1 | Freesound.org |
| Jump | Quando salta | P1 | Freesound.org |
| Attack_Swing | Quando attacca | P0 | Mixkit |
| Hit_Impact | Colpire nemico | P0 | Freesound.org |
| UI_Click | Click UI | P2 | Kenney.nl |

#### Musica

| Track | Uso | Durata | Priorità |
|-------|-----|--------|----------|
| Menu Theme | Menu principale | 1-2 min loop | P2 |
| Gameplay | Durante gioco | 2-3 min loop | P1 |
| Victory | Alla vittoria | 15-30 sec | P2 |

**Fonti:** Incompetech, OpenGameArt, Purple Planet

---

## 🗺️ Level Design

### Struttura dei Livelli

```
FLUSSO DI GIOCO:
Main Menu → Tutorial → Livello 1 → Livello 2 → Victory Screen
```

### Livello 1: Tutorial
**Obiettivo:** Insegnare meccaniche base

**Layout:**
```
[START] → [Sezione Movimento] → [Sezione Combattimento] → [Miniboss] → [END]
   |            (30s)                 (45s)                  (1min)
   |_______________________________________________________________|
                    ~3 minuti totali
```

**Elementi:**
- Spawn del giocatore
- NPC istruttivi (opzionale)
- 3-5 nemici di pratica
- Miniboss facile

**Sketch:** [Link a immagine in Notion]

### Livello 2: Sfida Principale
**Obiettivo:** Applicare quanto appreso con maggiore difficoltà

**Layout:** [Descrizione o sketch]

**⚠️ SCOPE:** Se il tempo stringe, rimanere con 1 solo livello ben rifinito.

---

## 👥 Nemici e NPC

### Nemico Tipo A: "Goblin"
**Comportamento:**
- Patrol tra punti A e B
- Al rilevare giocatore (raggio 10m) → Chase
- In raggio (2m) → Attack
- Perdere di vista 5s → Return to patrol

**Stats:**
- HP: 50
- Danno: 15
- Velocità: 3 m/s
- Cooldown attacco: 2s

**AI Script:** SimpleEnemyAI.cs (usare NavMesh)

### Nemico Tipo B: [Se c'è tempo]
[Descrizione]

---

## 🎯 Progressione e Condizioni di Vittoria/Sconfitta

### Condizione di Vittoria
- Completare tutti i livelli
- Sconfiggere il boss finale
- Raccogliere tutti gli oggetti (se applicabile)

### Condizione di Sconfitta
- HP del giocatore arriva a 0
- Cadere nel vuoto (insta-kill)
- Timer (se applicabile)

### Sistema di Punteggio (Opzionale)
- Nemici sconfitti: +100 pts
- Tempo rimanente: +10 pts/secondo
- Danno ricevuto: -5 pts

---

## 🖥️ UI/UX

### Schermate

#### 1. Main Menu
**Elementi:**
- Titolo del gioco (logo)
- Pulsante "Play"
- Pulsante "Options" (opzionale)
- Pulsante "Quit"
- Crediti del team

#### 2. HUD (In-game)
**Elementi:**
- Barra HP (angolo superiore sinistro)
- Contatore nemici (angolo superiore destro)
- Cooldown abilità (parte inferiore centro)
- Minimappa (opzionale, solo se c'è tempo)

**Wireframe:** [Link a sketch in Notion]

#### 3. Pause Menu
**Elementi:**
- "Resume"
- "Restart"
- "Main Menu"

#### 4. Game Over Screen
**Elementi:**
- "YOU DIED" / "VICTORY"
- Punteggio (opzionale)
- "Retry"
- "Main Menu"

---

## 📦 Assets e Risorse Esterne

### Assets da Asset Store / Fonti Esterne

| Asset | Fonte | Licenza | Uso |
|-------|-------|---------|-----|
| [Esempio: TextMesh Pro] | Unity Package | Free | Testo UI |
| [Low Poly Water] | Asset Store | Free | Acqua nei livelli |

### Strumenti di Terze Parti

- **ProBuilder:** Level design
- **DOTween:** Animazioni UI
- **Cinemachine:** Controllo camera
- **NavMesh Components:** IA nemici

---

## 🚀 Milestones e Deliverable

### Giorno 1: Foundation
**Deliverable:**
- [ ] GDD completo
- [ ] Progetto Unity configurato
- [ ] Repository Git inizializzato
- [ ] Personaggio placeholder funzionante
- [ ] Movimento base implementato

**Build Target:** Personaggio che cammina in scena vuota

### Giorno 2: Core Mechanics
**Deliverable:**
- [ ] Sistema di combattimento funzionale
- [ ] IA nemici base
- [ ] Modello del giocatore (low-poly)
- [ ] 3 animazioni core (idle, walk, attack)
- [ ] Livello 1 bloccato (greybox)

**Build Target:** Gameplay core funzionante

### Giorno 3: Content & Polish
**Deliverable:**
- [ ] Tutti i modelli integrati
- [ ] Tutte le animazioni
- [ ] Livello 1 completo e giocabile
- [ ] UI base (menu, HUD)
- [ ] SFX integrati

**Build Target:** Versione alfa giocabile dall'inizio alla fine

### Giorno 4: Testing & Polish (Se Jam di 72h+)
**Deliverable:**
- [ ] Bug critici risolti
- [ ] Feedback visivo/audio migliorato
- [ ] Bilanciamento difficoltà
- [ ] Livello 2 (se c'è tempo)
- [ ] Musica integrata

**Build Target:** Versione Beta

### Ultime 6 Ore: Final Push
**Deliverable:**
- [ ] Build per tutte le piattaforme
- [ ] Pagina itch.io configurata
- [ ] Trailer/Screenshots
- [ ] Ultimo giro di testing
- [ ] Submit finale

**🔒 CODE FREEZE 3 ORE PRIMA DELLA DEADLINE**

---

## ⚠️ Risk Management

### Rischi Identificati

| Rischio | Probabilità | Impatto | Mitigazione |
|---------|-------------|---------|-------------|
| Scope Creep | Alta | Alto | GDD rigoroso, prioritizzazione P0-P2 |
| Blocchi tra ruoli | Media | Alto | Placeholders, comunicazione giornaliera |
| Bug dell'ultimo minuto | Alta | Medio | Testing continuo, code freeze |
| Problemi di performance | Media | Alto | Target 60 FPS dal giorno 1 |
| Conflitti di merge | Media | Medio | Branch per feature, merge frequenti |

### Piano di Contingenza

**Se perdiamo 1 giorno completo di sviluppo:**
- Tagliare meccaniche secondarie
- Ridurre a 1 solo livello
- Usare più assets gratuiti
- Semplificare arte

**Se un membro non può continuare:**
- Game Designer assume task di level design/testing
- Redistribuire task critici
- Cercare assets gratuiti di sostituzione

---

## 📚 Glossario Tecnico

| Termine | Definizione |
|---------|-------------|
| Greybox/Blockout | Livello costruito con cubi/forme base per testare gameplay prima dell'arte finale |
| Placeholder | Asset temporaneo usato per non bloccare lo sviluppo |
| MVP | Minimum Viable Product - Versione minima giocabile |
| P0/P1/P2 | Priorità: P0 = Critico, P1 = Alto, P2 = Basso |
| Code Freeze | Momento in cui si smette di aggiungere features, si correggono solo bug |

---

## ✅ Checklist Pre-Submit

### 24 Ore Prima
- [ ] Build funziona su tutte le piattaforme target
- [ ] Tutti i bug P0 risolti
- [ ] Tutti i bug P1 risolti o documentati
- [ ] Il loop di gameplay è soddisfacente e chiaro
- [ ] I controlli sono spiegati (in-game o sulla pagina)

### 12 Ore Prima
- [ ] Pagina itch.io/GameJolt completa
- [ ] Screenshots di qualità (minimo 5)
- [ ] Descrizione chiara del gioco
- [ ] Crediti del team
- [ ] Licenze assets di terze parti

### 6 Ore Prima - CODE FREEZE
- [ ] Build finale compilata
- [ ] Testing della build (30 min)
- [ ] Trailer o GIF di gameplay (opzionale ma raccomandato)

### 3 Ore Prima
- [ ] Build caricata sulla piattaforma
- [ ] Link verificati funzionanti
- [ ] Ultima revisione bug visivi

### 1 Ora Prima
- [ ] Submit finale
- [ ] Screenshot di conferma
- [ ] Backup della build localmente
- [ ] Festeggiare 🎉

---

**Versione:** 1.0  
**Ultimo Aggiornamento:** [Data]  
**Mantenuto da:** Game Designer
```

---

## 4. Piano d'Azione Operativo

### 4.1 Pre-Produzione (Prima del Jam)

#### 2 Settimane Prima
```
✅ SETUP TECNICO
□ Installare Unity 6 (tutti)
□ Installare Blender (Modellatore + Animatore)
□ Configurare Git + GitHub (tutti)
□ Creare account itch.io/GameJolt
□ Testare pipeline: Blender → Unity

✅ ORGANIZZAZIONE
□ Creare Workspace in Notion
□ Importare template di documentazione
□ Configurare canali Discord/Slack
□ Definire orari di disponibilità

✅ PRATICA
□ Fare tutorial Unity (Programmatore)
□ Fare tutorial Blender (Modellatore + Animatore)
□ Esportare FBX di prova (tutti i ruoli)
□ Fare un micro-progetto di 2 ore (opzionale)
```

#### 1 Settimana Prima
```
✅ PIANIFICAZIONE
□ Ricercare tema del jam (se annunciato)
□ Preparare lista di riferimenti e ispirazione
□ Preparare lista di assets gratuiti di backup
□ Fare dry-run della riunione kickoff

✅ STRUMENTI
□ Scaricare plugin utili (ProBuilder, DOTween)
□ Preparare librerie di codice comune
□ Configurare template Notion/GitHub
□ Testare strumenti di comunicazione
```

#### 1 Giorno Prima
```
✅ ULTIMA PREPARAZIONE
□ Dormire bene (cruciale)
□ Verificare che tutto il software funzioni
□ Avere cibo/bevande preparate
□ Silenziare notifiche non essenziali
□ Mentalizzazione: "Done > Perfect"
```

### 4.2 Giorno per Giorno (Jam di 48 ore)

#### 🌅 GIORNO 1: FOUNDATION (0-24h)

##### Ora 0-3: Kickoff & Planning
```
🎯 OBIETTIVI:
- Definire concetto del gioco
- Creare GDD semplificato
- Assegnare task iniziali

⏰ TIMELINE:
00:00 - 00:30 | Brainstorming (tutti insieme)
  - Tema del jam
  - 5 idee rapide
  - Votare per 1

00:30 - 01:30 | Raffinamento del concetto
  - Definire core loop
  - Identificare meccaniche core
  - Schizzi rapidi di level design

01:30 - 02:30 | Documentazione in Notion
  - Game Designer scrive GDD base
  - Resto del team aggiunge sezione del proprio ruolo

02:30 - 03:00 | Task Breakdown
  - Creare tutti i task in Notion
  - Assegnare priorità
  - Identificare dipendenze critiche
  - Creare GitHub Issues per programmazione

📦 DELIVERABLE:
□ GDD completo (80% fatto)
□ Notion task board popolato
□ GitHub Issues creati
□ Schizzi di level design
```

##### Ora 3-8: Setup & First Playable
```
👨‍💻 PROGRAMMATORE:
□ Creare progetto Unity 6
□ Configurare Git (.gitignore, README)
□ Installare packages essenziali
□ Creare scena di prova
□ Implementare movimento base (WASD)
□ Creare placeholder del personaggio (cubo)
□ Setup InputSystem / vecchio Input
□ Primo commit & push

🎨 MODELLATORE:
□ Creare personaggio placeholder (cilindro con proporzioni)
□ Esportare in Unity per uso del programmatore
□ Ricercare riferimenti del personaggio finale
□ Iniziare modellazione del personaggio principale
□ Creare palette di colori

🎬 ANIMATORE:
□ Cercare personaggio Mixamo come placeholder
□ Esportare animazioni base (idle, walk, run)
□ Praticare export in Unity con placeholder
□ Prepararsi a fare rig del modello reale quando pronto
□ Ricercare tutorial di rigging se necessario

🎮 GAME DESIGNER:
□ Finalizzare GDD (100%)
□ Creare greybox del livello 1 in Unity (cubi)
□ Documentare controlli dettagliatamente
□ Preparare moodboard di riferimenti
□ Creare checklist di testing

📦 DELIVERABLE: Cubo che si muove in livello greybox
```

##### Ora 8-12: Core Mechanics
```
👨‍💻 PROGRAMMATORE:
□ Implementare sistema di salto
□ Implementare rotazione camera
□ Creare script base nemico (IA semplice)
□ Implementare sistema di combattimento base
□ Setup di collider e layer
□ Integrare animazioni placeholder

🎨 MODELLATORE:
□ Finire personaggio principale (>60% progresso)
□ Creare modello nemico semplice
□ Creare props base del livello (piattaforme, ostacoli)
□ Export in Unity

🎬 ANIMATORE:
□ Se il modello è >60%, iniziare rigging
□ Se no, continuare a raffinare animazioni placeholder
□ Preparare Animation Controller in Unity

🎮 GAME DESIGNER:
□ Iterare greybox con feedback del team
□ Iniziare UI base (sketch Main Menu)
□ Testare meccaniche precoci
□ Documentare primi bug

📦 DELIVERABLE: Personaggio che salta, camera funzionale, nemico base
```

##### Ora 12-18: Integration
```
👨‍💻 PROGRAMMATORE:
□ Integrare modello del giocatore (se pronto)
□ Connettere animazioni
□ Implementare sistema di vita (HP)
□ Implementare sistema di danno
□ Creare UI HUD (barra vita)
□ Polish dei controlli

🎨 MODELLATORE:
□ Finalizzare personaggio principale (100%)
□ Texturizzazione base
□ Creare varianti nemici (se c'è tempo)
□ Props aggiuntivi

🎬 ANIMATORE:
□ Rigging del personaggio completo
□ Esportare animazioni finali
□ Configurare Animator Controller
□ Animation events (se applicabile)

🎮 GAME DESIGNER:
□ Level design del 50% del livello 1
□ Placement di nemici
□ Testing di difficoltà
□ Aggiustare bilanciamento

📦 DELIVERABLE: Personaggio finale animato, nemico funzionale, 50% del livello
```

##### Ora 18-24: First Playable Build
```
👨‍💻 PROGRAMMATORE:
□ Implementare Main Menu
□ Sistema di pausa
□ Game Over screen
□ Preparare prima build
□ Testing di integrazione

🎨 MODELLATORE:
□ Rifinire assets esistenti
□ Creare assets secondari
□ Aiutare con level design se finisce presto

🎬 ANIMATORE:
□ Animazioni secondarie (attacco, reazione colpo)
□ Transizioni di animazioni
□ Polish del timing

🎮 GAME DESIGNER:
□ Completare livello 1 (100% greybox o con arte)
□ Integrazione SFX (audio placeholder)
□ Testing esaustivo
□ Documentare bug in GitHub

📦 DELIVERABLE: Prima build giocabile dall'inizio alla fine

🎉 FINE DEL GIORNO 1
□ Riunione di 30 min per review
□ Build compilata e condivisa con il team
□ Tutti giocano la build
□ Fare lista di priorità per domani
□ DORMIRE (cruciale per giorno 2)
```

#### 🌞 GIORNO 2: CONTENT & POLISH (24-48h)

##### Ora 24-30: Wake Up & Polish Sprint
```
☕ 24:00 - 24:30 | Morning Review
- Giocare la build del giorno 1
- Identificare 3 miglioramenti critici
- Ridare priorità ai task secondo il progresso

👨‍💻 PROGRAMMATORE:
□ Fix di bug critici
□ Implementare feedback audio/visuale
□ Particle effects
□ Screen shake
□ Migliorare juice del gioco

🎨 MODELLATORE:
□ Assets mancanti di priorità alta
□ Migliorare texturizzazione
□ Props decorativi
□ Skybox/Environment

🎬 ANIMATORE:
□ Animazioni mancanti
□ Migliorare transizioni
□ IK (se c'è tempo)
□ Animazioni facciali (se applicabile e c'è tempo)

🎮 GAME DESIGNER:
□ Iterare level design con arte
□ Aggiungere dettagli e polish
□ Integrare SFX reali
□ Testing continuo
```

##### Ora 30-36: Feature Complete
```
🎯 OBIETTIVO: Tutte le features P0 e P1 implementate

👨‍💻 PROGRAMMATORE:
□ Ultime features critiche
□ Menu settings (volume audio, ecc)
□ Sistema di salvataggio (se applicabile)
□ Ottimizzazione build

🎨 MODELLATORE:
□ Tutti i modelli finalizzati
□ LOD (se necessario)
□ Props finali

🎬 ANIMATORE:
□ Tutte le animazioni esportate
□ Fine-tuning del timing
□ Aiutare con livello 2 se c'è tempo

🎮 GAME DESIGNER:
□ Livello 2 (se c'è tempo) o rifinire livello 1
□ Integrazione musica
□ Prompt tutorial
□ Schermata vittoria

📦 DELIVERABLE: Build feature complete
```

##### Ora 36-42: Bug Fixing & Balancing
```
🐛 TUTTI: Focus su stabilità

□ Playtesting intensivo (tutti giocano)
□ Documentare bug in GitHub
□ Dare priorità per gravità
□ Sprint di fixing

👨‍💻 PROGRAMMATORE: Fix bug tecnici
🎨 MODELLATORE: Fix bug visivi, ottimizzazione
🎬 ANIMATORE: Fix bug animazioni
🎮 GAME DESIGNER: Bilanciamento, tutorial

⚠️ CRITICO: Non aggiungere nuove features
```

##### Ora 42-46: Final Polish
```
✨ CHECKLIST POLISH:
□ Menu funzionano perfettamente
□ Non ci sono bug visivi ovvi
□ Non ci sono bug di gameplay critici
□ Il gioco si sente soddisfacente
□ SFX/Music sono a livelli corretti
□ UI è leggibile e chiara
□ Controlli sono responsivi

👨‍💻 PROGRAMMATORE:
□ Compilare build per tutte le piattaforme
□ Testing di ogni build
□ Ottimizzazione finale

🎮 GAME DESIGNER:
□ Screenshot di alta qualità
□ GIF di gameplay
□ Trailer corto (30-60s) se c'è tempo
□ Preparare descrizione per itch.io
```

##### Ora 46-48: SUBMISSION
```
⏰ 46:00 - CODE FREEZE
❌ NESSUN'ALTRA MODIFICA AL CODICE

46:00 - 47:00 | Final Build & Testing
□ Compilare build finale
□ Testare su computer pulito (se possibile)
□ Verificare che non ci siano bug dell'ultimo minuto

47:00 - 47:30 | Setup itch.io
□ Caricare build
□ Scrivere descrizione
□ Aggiungere screenshots/GIF
□ Aggiungere controlli
□ Aggiungere crediti del team
□ Verificare che il gioco sia pubblico

47:30 - 47:45 | Final Testing
□ Scaricare il proprio gioco da itch.io
□ Verificare che funzioni
□ Far provare ad altri membri del team

47:45 - 48:00 | SUBMIT
□ Submit alla game jam
□ Screenshot di conferma
□ Condividere link in Discord/Comunità
□ FESTEGGIARE 🎉🎉🎉

🎊 POST-JAM
□ Ringraziare la comunità
□ Giocare submission degli altri
□ Dare feedback
□ Riposare
```

### 4.3 Strategie di Contingenza

#### Se si è in Ritardo (Ora 30+)

```
🚨 ALBERO DECISIONALE TAGLIO SCOPE:

In ritardo di >6 ore?
└─ SÌ → Tagliare livello 2 completamente
       Concentrarsi su 1 livello rifinito

In ritardo di >12 ore?
└─ SÌ → Tagliare meccaniche secondarie
       Mantenere solo P0

In ritardo di >18 ore?
└─ SÌ → MODALITÀ EMERGENZA
       ├─ Tagliare TUTTE le features non-core
       ├─ Usare assets gratuiti invece di propri
       ├─ Ridurre animazioni al minimo
       └─ Obiettivo: Loop funzionale in 1 livello
```

#### Se un Membro si Ritira

```
MODELLATORE ASSENTE:
└─ Usare assets da Asset Store/Kenney.nl
└─ Animatore aiuta con modellazione se sa Blender
└─ Estetica più minimalista

ANIMATORE ASSENTE:
└─ Usare animazioni Mixamo
└─ Programmatore integra animazioni pre-fatte
└─ Modellatore aiuta se sa rigging

PROGRAMMATORE ASSENTE:
└─ CRITICO - Molto difficile da recuperare
└─ Cercare aiuto esterno urgente
└─ Considerare uso di strumenti no-code (Bolt, PlayMaker)

GAME DESIGNER ASSENTE:
└─ Programmatore assume ruolo di direttore
└─ Semplificare design al massimo
└─ Tutti contribuiscono con level design
```

### 4.4 Ottimizzazioni del Workflow

#### Tecniche di Lavoro Parallelo

```
PARALLELIZZAZIONE MASSIMA:

GIORNO 1 - ORE 3-12:
┌─────────────────┐  ┌─────────────────┐
│  PROGRAMMATORE  │  │  MODELLATORE    │
│  Codice con     │  │  Modello con    │
│  Placeholder    │  │  Riferimenti    │
└────────┬────────┘  └────────┬────────┘
         │                    │
         └────────┬───────────┘
                  ↓
         ┌────────────────┐
         │   ANIMATORE    │
         │  Placeholder   │
         │   Mixamo       │
         └────────┬───────┘
                  │
                  ↓
         ┌────────────────┐
         │ GAME DESIGNER  │
         │   Greybox      │
         └────────────────┘

NESSUNO È BLOCCATO - TUTTI PROGREDISCONO
```

#### Tecniche di Sblocco

```
TECNICA 1: "Assume and Mock"
- Programmatore non ha il modello? → Usa cubo
- Animatore non ha il rig? → Usa Mixamo
- Designer non ha assets? → Usa ProBuilder

TECNICA 2: "Versione Degradata"
- Non c'è tempo per 10 nemici? → 1 nemico x10
- Non c'è tempo per cutscene? → Text screen
- Non c'è tempo per musica? → Solo SFX

TECNICA 3: "Good Enough"
- Animazione 80% bene? → Ship it
- Livello non perfetto? → Ship it
- Modello ha piccolo bug visivo? → Ship it
```

### 4.5 Comunicazione in Crisi

#### Quando le Cose si Fanno Difficili

```
🔥 ORA 36 - Mancano ancora features P0

1. CHIAMARE RIUNIONE DI EMERGENZA (15 min)
   - Tutti smettono di lavorare
   - Video call o Discord

2. VALUTAZIONE ONESTA
   - Quali features P0 mancano?
   - Quante ore reali rimangono?
   - È realistico finire tutto?

3. DECISIONE COLLETTIVA
   - Votare cosa tagliare
   - Redistribuire task
   - Nuovo piano chiaro

4. ESEGUIRE SENZA GUARDARE INDIETRO
   - Non lamentarsi delle decisioni
   - Focus su cosa SI farà
   - Mantenere morale alto
```

#### Frasi per Mantenere il Team Motivato

```
❌ EVITARE:
- "Non finiremo"
- "Questo è impossibile"
- "Avremmo dovuto..."

✅ USARE:
- "Stiamo andando bene, continuiamo così"
- "Questo è quello che possiamo realizzare"
- "Aggiustiamo e continuiamo"
- "Impariamo per la prossima volta"
- "Il gioco sarà buono così"
```

---

## 5. Appendici e Risorse

### 5.1 Snippet di Codice Utili

#### Player Movement Controller (Base)

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
            velocity.y = -2f; // Piccolo negativo per mantenere a terra
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
        
        // Applicare gravità
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
        Debug.Log("Nemico attacca giocatore!");
        // Implementare danno al giocatore
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
    public Slider healthBar; // Assegnare dall'inspector
    
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
        Debug.Log(gameObject.name + " è morto!");
        // Implementare logica di morte
        Destroy(gameObject);
    }
}
```

### 5.2 Cheat Sheet di Git per Game Jam

```bash
# SETUP INIZIALE (Giorno 0)
git init
git remote add origin <url-del-repo>
git add .
git commit -m "Initial project setup"
git push -u origin main

# WORKFLOW GIORNALIERO
# 1. Prima di iniziare a lavorare
git pull origin main

# 2. Lavorare sul codice

# 3. Vedere quali modifiche hai fatto
git status

# 4. Aggiungere le modifiche
git add .
# O specificamente:
git add Assets/Scripts/PlayerController.cs

# 5. Commit con messaggio descrittivo
git commit -m "feat: add player jump (#001)"

# 6. Push a GitHub
git push origin main

# BRANCHES (Raccomandato per team più esperti)
# Creare branch per la tua feature
git checkout -b feature/player-combat

# Lavorare sulla branch...

# Merge a main quando pronto
git checkout main
git merge feature/player-combat

# EMERGENZE
# Dimenticato di fare pull e ci sono conflitti
git pull origin main
# Risolvere conflitti manualmente in Unity/IDE
git add .
git commit -m "fix: resolve merge conflicts"
git push origin main

# Annullare l'ultimo commit (attenzione!)
git reset --soft HEAD~1

# Vedere cronologia
git log --oneline
```

### 5.3 Pipeline Blender to Unity

#### Esportazione FBX Ottimale da Blender

```
IMPOSTAZIONI DI EXPORT IN BLENDER:

1. Selezionare oggetto/i
2. File → Export → FBX (.fbx)
3. Configurare:

[X] Selected Objects Only (se si vuole esportare solo il selezionato)
[X] Apply Modifiers

Transform:
   Scale: 1.00 (Unity usa stessa scala)
   Forward: -Z Forward
   Up: Y Up
   [X] Apply Unit
   [X] Apply Transform

Geometry:
   [X] Apply Modifiers
   [ ] Tangent Space (Unity lo calcola)
   
Armature:
   [ ] Add Leaf Bones (problemi in Unity)
   [X] Only Deform Bones

Animation:
   [X] Bake Animation (se ha animazioni)
   [ ] NLA Strips
   [ ] All Actions (solo se si vogliono esportare tutte)
```

#### Convenzioni di Naming

```
OGGETTI:
- PlayerCharacter_LP (LP = Low Poly)
- Enemy_Goblin_LP
- Prop_Tree_01
- Weapon_Sword

MATERIALI:
- MAT_Player_Skin
- MAT_Ground_Grass
- MAT_Metal_Rusty

TEXTURE:
- TEX_Player_Diffuse.png
- TEX_Player_Normal.png
- TEX_Ground_Albedo.png
```

#### Troubleshooting Comune

```
PROBLEMA: Il modello appare gigante in Unity
SOLUZIONE: In Blender, Scale = 1 prima di esportare
          In Unity Inspector, Scale = 1

PROBLEMA: Le normali sono invertite (nero)
SOLUZIONE: Blender: Select All → Shift+N (Recalculate Normals)

PROBLEMA: Il rig non funziona in Unity
SOLUZIONE: Verificare che il rig sia tipo "Humanoid" in Unity
          FBX Export: "Only Deform Bones" checked

PROBLEMA: Le texture non si importano
SOLUZIONE: Le texture devono essere nella stessa cartella dell'FBX
          O incorporarle: FBX Export → Path Mode: "Copy"
```

### 5.4 Risorse Esterne Raccomandate

#### Assets Gratuiti

**Modelli 3D:**
- [Kenney.nl](https://kenney.nl/) - Modelli low-poly gratuiti
- [Poly Haven](https://polyhaven.com/) - Modelli, texture, HDRI
- [Quaternius](https://quaternius.com/) - Assets low-poly
- [Mixamo](https://www.mixamo.com/) - Personaggi e animazioni

**Texture:**
- [Poly Haven](https://polyhaven.com/textures)
- [CC0 Textures](https://cc0textures.com/)
- [TextureCan](https://www.texturecan.com/)

**Audio (SFX):**
- [Freesound.org](https://freesound.org/)
- [Kenney.nl Audio](https://kenney.nl/assets?q=audio)
- [Mixkit](https://mixkit.co/free-sound-effects/)
- [ZapSplat](https://www.zapsplat.com/)

**Musica:**
- [Incompetech](https://incompetech.com/music/)
- [Purple Planet](https://www.purple-planet.com/)
- [OpenGameArt Music](https://opengameart.org/art-search-advanced?keys=&field_art_type_tid%5B%5D=12)

**UI:**
- [Kenney UI Pack](https://kenney.nl/assets/ui-pack)
- [Game-icons.net](https://game-icons.net/)

#### Package Unity Essenziali

```
GRATUITI:
- TextMesh Pro (Testo UI migliorato)
- ProBuilder (Level design in Unity)
- Cinemachine (Camere cinematografiche)
- Post Processing Stack (Effetti visivi)
- Input System (Nuovo sistema di input)

A PAGAMENTO (OPZIONALE):
- DOTween Pro ($15 - Animazioni tweening)
- Odin Inspector ($55 - Inspector migliore)
```

#### Tutorial Raccomandati

**Unity Base:**
- [Brackeys Channel](https://www.youtube.com/c/Brackeys) (YouTube)
- [Unity Learn](https://learn.unity.com/)
- [Catlike Coding](https://catlikecoding.com/unity/tutorials/)

**Blender:**
- [Blender Guru - Donut Tutorial](https://www.youtube.com/watch?v=nIoXOplUvAw)
- [Grant Abbitt Low Poly](https://www.youtube.com/c/GrantAbbitt)

**Game Design:**
- [Game Maker's Toolkit](https://www.youtube.com/c/MarkBrownGMT)
- [Extra Credits](https://www.youtube.com/extracredits)

### 5.5 Template di Notion

#### Template: Task Card (Copiare in Notion)

```markdown
# [TASK-XXX] Titolo del Task

**👤 Assignee:** [Nome]
**🎭 Role:** [Programmatore/Modellatore/Animatore/Designer]
**⏰ Estimate:** X ore
**🎯 Priority:** P0/P1/P2
**📅 Sprint:** Day X
**🔗 GitHub:** #XXX

## 📝 Descrizione
[Descrizione dettagliata di cosa va fatto]

## ✅ Criteri di Accettazione
- [ ] Criterio 1
- [ ] Criterio 2
- [ ] Criterio 3

## 🔗 Dipendenze
- Dipende da: [TASK-XXX]
- Blocca: [TASK-XXX]

## 📦 Assets/Risorse Necessarie
- Asset 1
- Risorsa 2

## 📸 Riferimenti
[Link a immagini, tutorial, ecc.]

## 🪲 Known Issues
- Issue 1 (se applicabile)

## 📝 Note
Note aggiuntive dello sviluppatore
```

#### Template: Daily Standup (Copiare in Notion)

```markdown
# Daily Standup - [Data]

## ⏰ Time: [Ora]

### 👨‍💻 Programmatore
**Ieri:**
- [Ho completato X]
- [Ho lavorato su Y]

**Oggi:**
- [Lavorerò su Z]
- [Implementerò W]

**Blocchi:**
- [Bloccato da A] / [Nessun blocco]

---

### 🎨 Modellatore
**Ieri:**
- [Ho completato X]

**Oggi:**
- [Creerò Y]

**Blocchi:**
- [In attesa di feedback su Z] / [Nessun blocco]

---

### 🎬 Animatore
**Ieri:**
- [Ho fatto rig personaggio X]

**Oggi:**
- [Animerò Y]

**Blocchi:**
- [Nessun blocco]

---

### 🎮 Game Designer
**Ieri:**
- [Ho progettato livello X]

**Oggi:**
- [Testerò Y]

**Blocchi:**
- [Nessun blocco]

---

## 🎯 Obiettivi del Team per Oggi
- Obiettivo 1
- Obiettivo 2

## 🚨 Problemi Critici
- Problema 1 (se presenti)
```

---

## 📌 Quick Reference Card (Stampare Questo!)

```
╔══════════════════════════════════════════════════════════╗
║      GAME JAM SURVIVAL QUICK REFERENCE                   ║
╚══════════════════════════════════════════════════════════╝

🎯 REGOLA D'ORO: Done > Perfect

📅 MILESTONES:
Giorno 1: First Playable (movimento + nemico + livello)
Giorno 2: Feature Complete
Giorno 2 (Ultime 6h): Solo Polish
3h Prima Deadline: CODE FREEZE

🚨 QUANDO TAGLIARE SCOPE:
-6h ritardo → Tagliare livello 2
-12h ritardo → Tagliare meccaniche secondarie  
-18h ritardo → EMERGENZA: Solo features P0

💬 COMUNICAZIONE:
- Daily standup: 10-15 min
- Discord/Slack sempre aperto
- Se problema >30 min → Chiedere aiuto
- Se problema >2h → Cambiare approccio

📁 WORKFLOW:
1. Pull prima di lavorare
2. Commit frequenti con messaggi chiari
3. Push a fine giornata
4. Notion = Design
5. GitHub = Codice

⚠️ EMERGENZE:
- Bug critico → GitHub Issue P0
- Scope creep → Riunione di team
- Membro assente → Redistribuire task
- Blocco tecnico → Placeholder + continuare

🔑 ASSETS DI BACKUP:
- Modelli: Kenney.nl, Quaternius
- Animazioni: Mixamo
- SFX: Freesound.org
- Musica: Incompetech

📞 CONTATTI DI EMERGENZA:
Mentor/Advisor: [Contatto]
Server Discord: [Link]
Repo GitHub: [Link]
Notion: [Link]

🎉 RICORDA:
- Dormire è produttivo
- Mangiare bene mantiene il cervello attivo
- Divertirsi fa parte del processo
- Il gioco non deve essere perfetto
- Imparare è il vero premio

╔══════════════════════════════════════════════════════════╗
║ "L'unico modo per fallire un game jam è non finire"     ║
╚══════════════════════════════════════════════════════════╝
```

---

**FINE DEL DOCUMENTO**

---

## 📖 Come Usare Questo Documento

### Per il Team Completo
1. **Prima del Jam:** Leggere tutto il documento almeno una volta
2. **Durante il Jam:** Consultare sezioni specifiche secondo necessità
3. **Nelle riunioni:** Usare come riferimento per prendere decisioni

### Per Ogni Ruolo

**Game Designer:**
- Focus su Sezioni 1, 3, 4
- Responsabile di mantenere il GDD aggiornato
- Usare template di Notion

**Programmatore:**
- Focus su Sezioni 1, 2, 4, 5 (snippet)
- Responsabile di GitHub Issues
- Consultare troubleshooting tecnico

**Modellatore:**
- Focus su Sezioni 1, 4, 5 (pipeline Blender)
- Consultare convenzioni di naming
- Verificare specifiche tecniche

**Animatore:**
- Focus su Sezioni 1, 4, 5 (pipeline Blender)
- Coordinare con programmatore per animation events
- Usare checklist animazioni

---

**Versione:** 1.0  
**Creato:** [Data]  
**Per:** [Nome del Team]  
**Game Jam:** [Nome del Jam]

BUONA FORTUNA! 🎮🚀
