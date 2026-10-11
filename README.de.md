# youtube-vers-agent

Eine Claude Code-Fähigkeit, die YouTube-Tutorials in Claude Code-Fähigkeiten durch Dual-Quellen-Verifikation (lokaler Claude + Gemini) und Spezifikationsabgleich umwandelt.

## Beschreibung

Diese Fähigkeit konvertiert YouTube-Tutorial-Inhalte in strukturierte Claude Code-Fähigkeiten durch:
1. Extrahieren von Schlüsselkonzepten und Verfahren aus Video-Transkripten
2. Überprüfen von Informationen durch Dual-Quellen-Validierung (Video + Dokumentation)
3. Erstellen korrekt formatierter SKILL.md-Dateien gemäß Claude Code-Konventionen
4. Sicherstellen von Genauigkeit und Vollständigkeit durch Kreuzreferenzierung

## Wann verwenden

Verwende diese Fähigkeit, wenn du möchtest:
- Bildungscht YouTube-Inhalte in wiederverwendbare Claude Code-Fähigkeiten umwandeln
- Fähigkeiten basierend auf Tutorial-Videos über Entwicklertools, Frameworks oder Methodiken erstellen
- Fähigkeitsgenauigkeit durch Überprüfung gegenüber offizieller Dokumentation sicherstellen
- Eine Bibliothek verifizierter Fähigkeiten aus Video-Lernressourcen aufbauen

## Fähigkeitsworkflow

### 1. Videoanalysenphase
- Verarbeite YouTube-Video mithilfe der watch-Fähigkeit, um Transkript und Schlüsselbilder zu extrahieren
- Identifiziere Hauptthemen, Verfahren und Code-Beispiele, die präsentiert werden
- Struktur die Lernziele und -ergebnisse

### 2. Dual-Quellen-Verifikation
- Für jedes Schlüsselkonzept/Verfahren konsultiere offizielle Dokumentation mithilfe der context7-mcp oder find-docs Fähigkeiten
- Kreuze Videoinhalt mit autoritativen Quellen ab
- Notiere eventuelle Abweichungen oder Versionsunterschiede
- Überprüfe, ob Code-Beispiele wie demostrated funktionieren

### 3. Fähigkeitserstellung
- Generiere eine korrekt formatierte SKILL.md-Datei gemäß Claude Code-Konventionen
- Enthalte klare Beschreibung, Nutzungsrichtlinien und schrittweisen Workflow
- Referenziere sowohl die Videquelle als auch die Dokumentationsquellen, die für die Verifikation verwendet wurden
- Füge angemessene Tool-Empfehlungen basierend auf verifizierten Verfahren hinzu

### 4. Qualitätssicherung
- Teste alle Code-Beispiele oder erwähnten Verfahren
- Validiere, dass die Fähigkeit Claude Code Fähigkeitsformatierungsstandards folgt
- Stelle sicher, dass die Fähigkeit ausführbare, überprüfbare Anleitung bietet

## Ausgabe

Erstellt eine vollständige SKILL.md-Datei im entsprechenden .claude/skills/-Verzeichnis, die:
- Zweck und Anwendbarkeit der Fähigkeit klar definiert
- Spezifische Nutzungsrichtlinien bereitstellt
- Ein überprüfbares Workflow skizziert
- Quellen referenziert, die für die Dual-Quellen-Verifikation verwendet wurden
- Claude Code Fähigkeitskonventionen folgt

## Erforderliche Tools

- watch: Für die Verarbeitung von YouTube-Video-Inhalten
- context7-mcp oder find-docs: Für Dual-Quellen-Verifikation gegenüber offizieller Dokumentation
- Bash: Für Dateioperationen und Fähigkeitserstellung

## Installation

1. Klonen dieses Repositorys:
   ```bash
   git clone https://github.com/Zero-Piege/youtube-vers-agent
   ```

2. Kopiere die Fähigkeit in dein Claude Code Fähigkeiten-Verzeichnis:
   ```bash
   cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
   ```

3. Lade Plugins neu:
   ```bash
   /reload-plugins
   ```

## Verwendung

Nach der Installation kannst du die Fähigkeit verwenden, indem du eine YouTube-URL und das zu Bauende angibst:

```
/youtube-vers-agent [YouTube-URL] [was zu extrahieren] [was zu bauen]
```

Beispiel:
```
/youtube-vers-agent https://youtu.be/zke3bTtvmLo Alles das Projekt Eine Claude Code Fähigkeit
```

## Anwendungsbeispiel

Verwandle ein YouTube-Tutorial über die Erstellung von React-Komponenten in eine Claude Code-Fähigkeit:
1. Verwende die watch-Fähigkeit, um Video-Transkript und Schlüsselpunkte zu extrahieren
2. Verwende context7-mcp, um React-Komponentenerstellungsmuster gegenüber der offiziellen React-Dokumentation zu überprüfen
3. Erstelle SKILL.md mit verifizierten Verfahren zur Erstellung von React-Komponenten in Claude Code
4. Füge Verweise auf sowohl das YouTube-Tutorial als auch die verwendete React-Dokumentation hinzu

## Verifikationsstandards

Alle erstellten Fähigkeiten müssen:
- Mindestens zwei unabhängige Quellen referenzieren (Video + Dokumentation)
- Spezifische, ausführbare Schritte enthalten
- Klare Nutzungsrichtlinien bereitstellen
- Den etablierten Claude Code Fähigkeitsformat folgen
- Überprüfbare Verfahren enthalten, die getestet werden können

## Lizenz

MIT-Lizenz - siehe [LICENSE](LICENSE) Datei für Details.