# 🎯 Guida GitHub Issue Templates per Game Jam

## 📦 Contenuto

Hai ricevuto **4 template professionali** ottimizzati per game jam:

1. **🎮 Feature Request** - Per nuove funzionalità e meccaniche
2. **🐛 Bug Report** - Per segnalare errori e problemi
3. **🎨 Asset Request** - Per richiedere assets (modelli, animazioni, audio, UI)
4. **📐 Game Design Task** - Per task di design (level design, bilanciamento, testing)

## 🚀 Installazione nel tuo Repository

### Opzione 1: Tramite interfaccia web di GitHub (Raccomandato)

1. **Vai al tuo repository su GitHub**
   ```
   https://github.com/tuo-username/tuo-repo
   ```

2. **Naviga in Settings → Features**
   - Assicurati che "Issues" sia attivato

3. **Crea la cartella dei template**
   - Nella radice del tuo repository, crea questa struttura:
   ```
   .github/
   └── ISSUE_TEMPLATE/
       ├── feature_request.md
       ├── bug_report.md
       ├── asset_request.md
       ├── design_task.md
       └── config.yml
   ```

4. **Copia il contenuto**
   - Apri ogni file `.md` che ti ho fornito
   - Crea il file corrispondente su GitHub
   - Copia e incolla il contenuto

### Opzione 2: Da Git locale (Più veloce se hai già clonato il repo)

```bash
# Dalla radice del tuo repository

# Creare la struttura delle cartelle
mkdir -p .github/ISSUE_TEMPLATE

# Copiare i file che hai scaricato
cp /percorso/a/.github/ISSUE_TEMPLATE/* .github/ISSUE_TEMPLATE/

# Commit e push
git add .github/
git commit -m "feat: add GitHub issue templates for game jam"
git push origin main
```

## 🎨 Personalizzazione

### 1. Modificare config.yml

**IMPORTANTE:** Aggiorna questi link con quelli del tuo progetto:

```yaml
contact_links:
  - name: 💬 Domanda Generale o Discussione
    url: https://github.com/TUO-USERNAME/TUO-REPO/discussions  # 👈 Cambia qui
    
  - name: 📚 Documentazione del Progetto
    url: https://notion.so/TUO-WORKSPACE  # 👈 Cambia qui
    
  - name: 🎮 Game Jam Community
    url: https://discord.gg/TUO-SERVER  # 👈 Cambia qui
```

Se non usi qualcuno di questi (Discord, Notion, Discussions), semplicemente elimina quella sezione.

### 2. Personalizzare Label

I template usano questi label. **Creali nel tuo repo:**

Vai a: `Issues → Labels → New label`

| Label | Colore | Descrizione |
|-------|--------|-------------|
| 🎮 feature | `#0E8A16` | Nuova funzionalità |
| 🐛 bug | `#D73A4A` | Errore da correggere |
| 🎨 art | `#FFA500` | Assets artistici |
| 🎵 audio | `#9C27B0` | Assets audio |
| 📐 design | `#1E90FF` | Task di design |
| 🔴 P0-critical | `#B60205` | Priorità critica |
| 🟠 P1-high | `#FF6B00` | Priorità alta |
| 🟡 P2-medium | `#FFD700` | Priorità media |
| 🟢 P3-low | `#00FF00` | Priorità bassa |
| 🚀 ready | `#0075CA` | Pronto per lavorare |
| 🔒 blocked | `#6A737D` | Bloccato |
| 💻 code | `#000000` | Richiede programmazione |
| 🎬 animation | `#E99695` | Richiede animazione |

**Tip:** Puoi creare questi label automaticamente con uno script. [Vedi sezione automazione](#automazione-label).

### 3. Aggiustare Assignees Default

In ogni template, puoi preconfigurare gli assignees:

```yaml
assignees: 'tuo-programmatore-username'
```

O lasciare vuoto:
```yaml
assignees: ''
```

## 📋 Come Usare i Template

### Creare una Nuova Issue

1. **Vai alla tab Issues del tuo repo**
2. **Click su "New Issue"**
3. **Seleziona il template appropriato:**

```
🎮 Feature Request       →  Per implementare meccaniche
🐛 Bug Report           →  Per segnalare errori
🎨 Asset Request        →  Per richiedere modelli/audio/UI
📐 Game Design Task     →  Per design/testing/bilanciamento
```

4. **Compila il template** (non eliminare sezioni, anche se vuote)
5. **Assegna label, milestone, assignee**
6. **Submit issue**

### Workflow Raccomandato

#### Per Features (Programmatore):

```markdown
1. Game Designer crea Issue con template 🎮 Feature Request
2. Definire criteri di accettazione chiaramente
3. Elencare dipendenze (serve assets?)
4. Assegnare al programmatore
5. Programmatore accetta e inizia sviluppo
6. Quando finito, segna subtask come completati
7. Sposta a Testing (label o colonna in Project)
8. Game Designer testa secondo "Testing" del template
9. Se OK → Chiudi issue
   Se bug → Crea Bug Report e collega
```

#### Per Assets (Modellatore/Animatore):

```markdown
1. Programmatore o Designer crea 🎨 Asset Request
2. Specificare dettagli tecnici (polys, formato, ecc.)
3. Allegare riferimenti visivi
4. Assegnare all'artist
5. Artist crea l'asset secondo specs
6. Esportare secondo "Formato di Export" del template
7. Importare in Unity e testare
8. Segnare checklist di integrazione
9. Notificare che è pronto (menzionare programmatore)
10. Chiudere issue
```

#### Per Bug:

```markdown
1. Chiunque trovi un bug crea 🐛 Bug Report
2. Compilare passi per riprodurre (MOLTO IMPORTANTE)
3. Assegnare priorità P0/P1/P2/P3
4. Se P0-critical → Notificare team immediatamente
5. Programmatore indaga e sistema
6. Tester verifica che sia sistemato
7. Chiudere issue
```

#### Per Game Design:

```markdown
1. Designer crea 📐 Game Design Task
2. Specificare tipo (Level Design, Bilanciamento, Testing, ecc.)
3. Se testing → Elencare scenari di prova
4. Eseguire il task
5. Documentare risultati nella stessa issue
6. Se genera modifiche necessarie → Creare issue di Feature/Bug
7. Chiudere issue quando completo
```

## 🏷️ Sistema di Label

### Prioritizzazione (usare SOLO UNA per issue)

```
🔴 P0-critical  →  Blocca sviluppo, deve sistemare ORA
🟠 P1-high      →  Importante per MVP, alta priorità
🟡 P2-medium    →  Miglioramento notevole, media priorità  
🟢 P3-low       →  Nice to have, bassa priorità
```

**Regola Game Jam:** 
- Se rimangono <24h → Lavorare solo su P0 e P1
- Se rimangono <12h → Solo P0

### Tipo (può avere multipli)

```
🎮 feature      →  Nuova funzionalità
🐛 bug          →  Errore
🎨 art          →  Asset visivo
🎵 audio        →  Asset audio
📐 design       →  Task di design
```

### Stato

```
🚀 ready        →  Pronto per iniziare
🔒 blocked      →  Bloccato da dipendenze
👀 in-review    →  In revisione/testing
✅ tested       →  Testato e approvato
```

### Ruolo Richiesto

```
💻 code         →  Richiede programmazione
🎨 art-3d       →  Richiede modellazione
🎬 animation    →  Richiede animazione
📐 design       →  Richiede game design
```

## 🔗 Integrazione con Notion

Per mantenere sincronizzazione con Notion:

### Nell'Issue di GitHub:
```markdown
### Dipendenze
- Notion: TASK-045
```

### In Notion:
```
GitHub Issue: #23
```

**Link bidirezionale:** Includere sempre il link dell'altro sistema.

## 📊 GitHub Projects (Kanban Board)

### Setup Raccomandato:

1. **Crea un Project nel tuo repo:**
   - Vai a Projects → New Project
   - Scegli template "Board"

2. **Colonne suggerite:**
   ```
   📋 Backlog  →  Issues non iniziate
   📝 To Do    →  Prioritizzate per questo sprint
   🔄 In Progress  →  In sviluppo attivo
   🧪 Testing  →  In attesa di testing/review
   ✅ Done     →  Completate
   ```

3. **Automazione:**
   - Issue creata → Va in "Backlog"
   - Issue assegnata → Va in "To Do"
   - Issue chiusa → Va in "Done"

4. **Workflow:**
   ```
   Backlog → To Do (durante daily standup)
   To Do → In Progress (quando inizi a lavorare)
   In Progress → Testing (quando finisci)
   Testing → Done (quando approvato)
   ```

## 🤖 Automazione Label

### Script per creare label automaticamente

Crea un file `create-labels.sh`:

```bash
#!/bin/bash

# Colori
RED="#B60205"
ORANGE="#FF6B00"
YELLOW="#FFD700"
GREEN="#00FF00"
BLUE="#0075CA"
PURPLE="#9C27B0"
BLACK="#000000"
GRAY="#6A737D"
PINK="#E99695"

# Il tuo repo (CAMBIARE QUI)
REPO="tuo-username/tuo-repo"

# Tipi
gh label create "🎮 feature" --color "$GREEN" --description "Nuova funzionalità" --repo $REPO
gh label create "🐛 bug" --color "$RED" --description "Errore da correggere" --repo $REPO
gh label create "🎨 art" --color "$ORANGE" --description "Assets artistici" --repo $REPO
gh label create "🎵 audio" --color "$PURPLE" --description "Assets audio" --repo $REPO
gh label create "📐 design" --color "$BLUE" --description "Task di design" --repo $REPO

# Priorità
gh label create "🔴 P0-critical" --color "$RED" --description "Priorità critica" --repo $REPO
gh label create "🟠 P1-high" --color "$ORANGE" --description "Priorità alta" --repo $REPO
gh label create "🟡 P2-medium" --color "$YELLOW" --description "Priorità media" --repo $REPO
gh label create "🟢 P3-low" --color "$GREEN" --description "Priorità bassa" --repo $REPO

# Stati
gh label create "🚀 ready" --color "$BLUE" --description "Pronto per lavorare" --repo $REPO
gh label create "🔒 blocked" --color "$GRAY" --description "Bloccato" --repo $REPO
gh label create "👀 in-review" --color "$YELLOW" --description "In revisione" --repo $REPO
gh label create "✅ tested" --color "$GREEN" --description "Testato e approvato" --repo $REPO

# Ruoli
gh label create "💻 code" --color "$BLACK" --description "Richiede programmazione" --repo $REPO
gh label create "🎨 art-3d" --color "$ORANGE" --description "Richiede modellazione" --repo $REPO
gh label create "🎬 animation" --color "$PINK" --description "Richiede animazione" --repo $REPO

echo "✅ Label creati con successo!"
```

**Eseguire:**
```bash
chmod +x create-labels.sh
./create-labels.sh
```

**Requisito:** Avere [GitHub CLI](https://cli.github.com/) installato.

## 💡 Tips e Migliori Pratiche

### ✅ DA FARE:
- **Usare sempre i template** - Non creare issue in bianco
- **Compilare tutte le sezioni** - Anche se scrivi "N/A"
- **Assegnare label correttamente** - Specialmente la priorità
- **Collegare issue correlate** - Usa `#numero` per auto-link
- **Chiudere issue quando TESTATE** - Non solo quando il codice è fatto
- **Aggiornare l'issue durante lo sviluppo** - Segna checkbox mentre avanzi

### ❌ NON FARE:
- Non creare issue duplicate (cerca prima)
- Non lasciare issue non assegnate
- Non usare linguaggio vago ("sistemare il gioco", "migliorare grafica")
- Non chiudere bug senza verificare che siano sistemati
- Non abusare di P0-critical (riservare per blocchi reali)

### 🎯 Durante la Game Jam:

**Giorno 1:**
- Creare ~10-15 issue di features core
- Assegnare tutte con priorità
- Concentrarsi su P0 e P1

**Giorno 2:**
- Creare issue di bug secondo come si trovano
- Creare issue di assets mancanti
- Ridare priorità secondo progresso

**Giorno 3+ (se applicabile):**
- Limitare a P0 e P1 solo
- Chiudere aggressivamente P2 e P3 (spostare a "Post-Jam")

**Ultime 12 ore:**
- **NO nuove features**
- Solo bug P0 e P1
- Focus su polish visibile (UI, audio, juice)

## 📱 GitHub Mobile

I template funzionano anche nell'app mobile di GitHub, utile per:
- Segnalare bug al volo
- Creare issue di assets mentre sei in Blender
- Rivedere e commentare issue durante le pause

## 🆘 Troubleshooting

### "Non vedo i template quando creo issue"
- Verifica che i file siano in `.github/ISSUE_TEMPLATE/`
- Aspetta 5-10 minuti (GitHub può impiegare tempo a processare)
- Controlla che i file abbiano estensione `.md`
- Verifica che il YAML front matter sia corretto

### "Le label non appaiono"
- Crea prima le label in `Issues → Labels`
- I nomi devono coincidere ESATTAMENTE con il template

### "Voglio modificare un template"
- Modifica il file in `.github/ISSUE_TEMPLATE/`
- Commit e push
- Le modifiche si riflettono immediatamente nelle nuove issue

## 🎓 Risorse Aggiuntive

- [GitHub Issue Templates Documentation](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)
- [GitHub Projects Guide](https://docs.github.com/en/issues/planning-and-tracking-with-projects)
- [GitHub CLI](https://cli.github.com/)

---

## 📞 Domande Frequenti

**D: Posso usare questi template fuori dalle game jam?**
R: Sì! Sono generici ma ottimizzati per sviluppo agile veloce.

**D: Devo usare tutti e 4 i template?**
R: No, usa solo quelli che ti servono. Il minimo raccomandato è Feature + Bug.

**D: Posso aggiungere più template?**
R: Sì, segui lo stesso formato e aggiungili a `.github/ISSUE_TEMPLATE/`

**D: Funzionano con GitHub Free?**
R: Sì, tutte queste funzionalità sono gratuite, inclusi i Projects.

---

**Buona fortuna con la tua Game Jam!** 🎮🚀

Se hai domande, apri un'issue usando il template appropriato 😉
