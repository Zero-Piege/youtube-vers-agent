# youtube-vers-agent

Una competenza Claude Code che trasforma i tutorial di YouTube in competenze Claude Code attraverso la verifica dual-fonte (Claude locale + Gemini) e l'incrocio delle specifiche.

## Descrizione

Questa competenza converte il contenuto dei tutorial di YouTube in competenze Claude Code strutturate mediante:
1. Estrarre concetti chiave e procedure dalle trascrizioni video
2. Verificare le informazioni attraverso la validazione dual-fonte (video + documentazione)
3. Creare file SKILL.md correttamente formattati seguendo le convenzioni di Claude Code
4. Garantire accuratezza e completezza attraverso l'incrocio delle referenze

## Quando utilizzare

Utilizza questa competenza quando vuoi:
- Convertire contenuti educativi di YouTube in competenze Claude Code riutilizzabili
- Creare competenze basate su video tutorial su strumenti di sviluppo, framework o metodologie
- Assicurare l'accuratezza delle competenze tramite verifica rispetto alla documentazione ufficiale
- Costruire una biblioteca di competenze verificate da risorse di apprendimento video

## Flusso della competenza

### 1. Fase di analisi video
- Elabora il video di YouTube usando la competenza watch per estrarre la trascrizione e i fotogrammi chiave
- Identifica gli argomenti principali, le procedure e gli esempi di codice presentati
- Struttura gli obiettivi e i risultati di apprendimento

### 2. Verifica dual-fonte
- Per ogni concetto/procedura chiave, consulta la documentazione ufficiale usando le competenze context7-mcp o find-docs
- Incrocia il contenuto video con fonti autorevoli
- Nota eventuali discrepanze o differenze di versione
- Verifica che gli esempi di codice funzionino come dimostrato

### 3. Creazione della competenza
- Genera un file SKILL.md correttamente formattato seguendo le convenzioni di Claude Code
- Includi una descrizione chiara, linee guida per l'uso e un flusso di lavoro passo-passo
- Riferisci sia la fonte video che le fonti di documentazione utilizzate per la verifica
- Aggiungi raccomandazioni sugli strumenti appropriati basate sulle procedure verificate

### 4. Controllo qualità
- Testa gli esempi di codice o le procedure menzionati
- Valida che la competenza segua gli standard di formattazione delle competenze di Claude Code
- Assicurati che la competenza fornisca indicazioni attuabili e verificabili

## Output

Genera un file SKILL.md completo nella directory appropriata .claude/skills/ che:
- Definisce chiaramente lo scopo e l'applicabilità della competenza
- Fornisce linee guida per l'uso specifiche
- Descrive un flusso di lavoro verificabile
- Riferisce le fonti utilizzate per la verifica dual-fonte
- Segue le convenzioni delle competenze di Claude Code

## Strumenti richiesti

- watch: Per elaborare il contenuto dei video di YouTube
- context7-mcp o find-docs: Per la verifica dual-fonte rispetto alla documentazione ufficiale
- Bash: Per le operazioni sui file e la creazione delle competenze

## Installazione

1. Clona questo repository:
   ```bash
   git clone https://github.com/Zero-Piege/youtube-vers-agent
   ```

2. Copia la competenza nella tua directory delle competenze di Claude Code:
   ```bash
   cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
   ```

3. Ricarica i plugin:
   ```bash
   /reload-plugins
   ```

## Utilizzo

Dopo l'installazione, puoi utilizzare la competenza fornendo un URL di YouTube e specificando cosa vuoi costruire:

```
/youtube-vers-agent [URL di YouTube] [cosa estrarre] [cosa costruire]
```

Esempio:
```
/youtube-vers-agent https://youtu.be/zke3bTtvmLo Tutto il progetto Una competenza di Claude Code
```

## Esempio di utilizzo

Trasforma un tutorial di YouTube sulla creazione di componenti React in una competenza di Claude Code:
1. Usa la competenza watch per estrarre la trascrizione del video e i punti chiave
2. Usa context7-mcp per verificare i modelli di creazione di componenti React rispetto alla documentazione ufficiale di React
3. Crea SKILL.md con procedure verificate per creare componenti React in Claude Code
4. Includi riferimenti sia al tutorial di YouTube che alla documentazione di React utilizzata

## Standard di verifica

Tutte le competenze create devono:
- Riferire almeno due fonti indipendenti (video + documentazione)
- Includere passi specifici e attuabili
- Fornire linee guida per l'uso chiare
- Seguire il formato stabilito delle competenze di Claude Code
- Contenere procedure verificabili che possano essere testate

## Licenza

Licenza MIT - vedi il file [LICENSE](LICENSE) per i dettagli.