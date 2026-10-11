name: youtube-vers-agent
description: Transforme un tutoriel YouTube en skill Claude Code. À utiliser quand l'utilisateur colle un lien YouTube et demande de « construire ça », d'« en faire une skill » ou « un agent ». Deux lectures indépendantes de la vidéo (Claude en local, Gemini de son côté), croisées dans SPEC.md, puis construction avec skill-creator.

## Core Workflow

When a user provides a YouTube link and asks to "build this", "make it into a skill", or "create an agent":

1. **Frame the request**: If the user hasn't specified what they want to extract from the video, ask them. For videos over 20 minutes, suggest targeting a segment with --start and --end.

2. **Claude's reading**: Use /watch:watch [link] --engine local, with appropriate --detail and --resolution 1024 if the video shows code. Write the six-part specification in notes/lecture-claude.md BEFORE reading any Gemini output.

3. **Gemini's reading**: Use /watch:watch [link] --engine gemini, same six-part request, twice, without showing Claude's specification. Record responses verbatim in notes/lecture-gemini.md.

4. **SPEC.md creation**: Each line gets labeled as CONFIRMED, UNE SOURCE, or DÉSACCORD. Resolve disagreements by examining images with --timestamps. Remove timestamps, durations, and approximate numbers; keep exact commands, package names, settings, and error messages; end with OPEN QUESTIONS list.

5. **Construction**: Provide SPEC.md to skill-creator, specifying that the specification comes from a video. Launch the new skill once on a real case and fix what breaks.

If Gemini stops responding (free quota exhausted), perform Claude's reading only and mark the entire specification as UNE SOURCE.

## Detailed Steps

### Step 1: Framing
- Ask: "What do you want to extract from this video? [whole project / only part on X]"
- Ask: "What do you want to build? [Claude Code skill / script / website]"
- For videos >20 minutes: Suggest using --start HH:MM:SS --end HH:MM:SS to focus on a segment

### Step 2: Claude's Local Reading
- Execute: /watch:watch [YouTube URL] --engine local --detail [appropriate] [--resolution 1024 if showing code] --question "[six-part request]"
- Save output to notes/lecture-claude.md
- Six-part request format:
  ```
  Tu viens de regarder ce tutoriel. Écris la fiche de construction qu'un autre agent utilisera pour refaire la même chose. Il ne peut pas voir la vidéo : ta fiche est tout ce qu'il aura.

  Ce que je veux tirer de cette vidéo : [tout le projet / seulement la partie sur X]
  Ce que je veux construire : [une skill Claude Code / un script / un site]

  Six parties, dans cet ordre :
  1. CE QUI EST CONSTRUIT. Un paragraphe : le résultat réel, pas la promesse.
  2. OUTILS ET PRÉREQUIS. Chaque outil, package, modèle, service ou compte montré ou cité, avec sa version si elle est visible. Signale ce qui est payant.
  3. COMMANDES ET RÉGLAGES, MOT POUR MOT. Chaque commande tapée, chemin de fichier, variable et valeur lisible à l'écran, avec le moment de la vidéo. Si c'est flou, coupé ou trop rapide, écris ILLISIBLE au lieu de deviner.
  4. L'ORDRE DE CONSTRUCTION. Les étapes dans l'ordre réel, y compris celles défaites puis refaites. Dis où la vidéo saute directement au résultat.
  5. LES PIÈGES. Chaque erreur à l'écran, chaque avertissement, chaque « pensez bien à… ».
  6. CE QUE LA VIDÉO NE MONTRE PAS. Ce qui a été fait hors caméra, les valeurs sorties de nulle part, les étapes annoncées mais jamais montrées.

  Règles :
  - Décris seulement CETTE vidéo. S'il manque quelque chose d'habituel dans ce genre de tuto, dis qu'il manque au lieu de le compléter.
  - Le texte exact à l'écran passe avant ta reformulation.

  Enregistre la fiche dans notes/lecture-claude.md.
  ```

### Step 3: Gemini's Reading (if available)
- Execute first time: /watch:watch [YouTube URL] --engine gemini --question "[same six-part request]"
- Save first response to notes/lecture-gemini.md under "Réponse 1"
- Execute second time: /watch:watch [YouTube URL] --engine gemini --question "[same six-part request]"
- Save second response to notes/lecture-gemini.md under "Réponse 2"
- If Gemini fails (quota exhausted), skip to step 4 with Claude only

### Step 4: SPEC.md Creation
- Read notes/lecture-claude.md and notes/lecture-gemini.md
- For each line, determine:
  - CONFIRMÉ: Both readings agree on substance (minor wording differences acceptable)
  - UNE SOURCE: Only one reading states it, or readings differ substantively
  - DÉSACCORD: Readings contradict (resolve by examining video frames with --timestamps)
- Remove all timestamps, durations, and approximate numbers from both readings
- Keep verbatim: exact commands, package names, setting keys, error messages
- For DÉSACCORD lines: Use /watch:watch --engine local --timestamps [specific moments] to examine frames, then state what is observed
- End with QUESTIONS OUVERTES list: everything neither reading could see, plus all remaining DÉSACCORD items

### Step 5: Construction with skill-creator
- Provide SPEC.md to skill-creator with context: "Cette fiche vient d'une vidéo"
- Launch the generated skill once on a real test case
- Fix any issues that arise based on test results

## Error Handling

- If Gemini is unresponsive due to quota limits: Perform only Claude's reading, mark entire specification as UNE SOURCE, proceed to SPEC.md creation with single source
- If user provides unclear framing requests: Ask clarifying questions before proceeding
- If video shows code: Always use --resolution 1024 with local engine
- If user doesn't specify scope: Default to asking for clarification rather than assuming

## Output Format

The skill should deliver:
- A new Claude skill ready for installation and use
- Intermediate files: notes/lecture-claude.md, notes/lecture-gemini.md, notes/SPEC.md
- Documentation on how to use the generated skill

## Validation

After generating a skill from a YouTube tutorial:
1. Test the skill with a relevant prompt
2. Verify it produces expected outputs based on the tutorial
3. Collect user feedback and iterate if needed