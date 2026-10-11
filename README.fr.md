# youtube-vers-agent

Une compétence Claude Code qui transforme les tutoriels YouTube en compétences Claude Code grâce à une vérification dual-source (Claude local + Gemini) et à la croisée des spécifications.

## Description

Cette compétence convertit le contenu des tutoriels YouTube en compétences Claude Code structurées en :
1. Extrayant les concepts clés et les procédures des transcriptions vidéo
2. Vérifiant les informations grâce à une validation dual-source (vidéo + documentation)
3. Créant des fichiers SKILL.md correctement formatés suivant les conventions Claude Code
4. Assurant l'exactitude et la complétude grâce à la croisée des références

## Quand utiliser

Utilisez cette compétence lorsque vous souhaitez :
- Convertir du contenu éducatif YouTube en compétences Claude Code réutilisables
- Créer des compétences basées sur des vidéos tutoriels concernant des outils de développement, des frameworks ou des méthodologies
- Assurer l'exactitude des compétences grâce à une vérification par rapport à la documentation officielle
- Construire une bibliothèque de compétences vérifiées à partir de ressources d'apprentissage vidéo

## Workflow de la compétence

### 1. Phase d'analyse vidéo
- Traiter la vidéo YouTube en utilisant la compétence watch pour extraire la transcription et les images clés
- Identifier les sujets principaux, procédures et exemples de code présentés
- Structurer les objectifs et résultats d'apprentissage

### 2. Vérification dual-source
- Pour chaque concept/clé procédure, consulter la documentation officielle en utilisant les compétences context7-mcp ou find-docs
- Croiser le contenu vidéo avec des sources faisant autorité
- Noter toute divergence ou différence de version
- Vérifier que les exemples de code fonctionnent comme démontré

### 3. Création de compétence
- Générer un fichier SKILL.md correctement formaté suivant les conventions Claude Code
- Inclure une description claire, des directives d'utilisation et un workflow étape par étape
- Référencer à la fois la source vidéo et les sources de documentation utilisées pour la vérification
- Ajouter des recommandations d'outils appropriés basées sur les procédures vérifiées

### 4. Assurance qualité
- Tester les exemples de code ou procédures mentionnés
- Valider que la compétence suit les normes de formatage des compétences Claude Code
- S'assurer que la compétence fournit des conseils actionnables et vérifiables

## Sortie

Produit un fichier SKILL.md complet dans le répertoire approprié .claude/skills/ qui :
- Définit clairement l'objectif et l'applicabilité de la compétence
- Fournit des directives d'utilisation spécifiques
- Décrit un workflow vérifiable
- Référence les sources utilisées pour la vérification dual-source
- Suit les conventions des compétences Claude Code

## Outils requis

- watch : Pour traiter le contenu des vidéos YouTube
- context7-mcp ou find-docs : Pour la vérification dual-source par rapport à la documentation officielle
- Bash : Pour les opérations de fichiers et la création de compétences

## Installation

1. Clonez ce dépôt :
   ```bash
   git clone https://github.com/Zero-Piege/youtube-vers-agent
   ```

2. Copiez la compétence dans votre répertoire de compétences Claude Code :
   ```bash
   cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
   ```

3. Rechargez les plugins :
   ```bash
   /reload-plugins
   ```

## Utilisation

Après installation, vous pouvez utiliser la compétence en fournissant une URL YouTube et en spécifiant ce que vous souhaitez construire :

```
/youtube-vers-agent [URL YouTube] [ce à extraire] [ce à construire]
```

Exemple :
```
/youtube-vers-agent https://youtu.be/zke3bTtvmLo Tout le projet Une compétence Claude Code
```

## Exemple d'utilisation

Transformer un tutoriel YouTube sur la création de composants React en une compétence Claude Code :
1. Utilisez la compétence watch pour extraire la transcription vidéo et les points clés
2. Utilisez context7-mcp pour vérifier les modèles de création de composants React par rapport à la documentation officielle de React
3. Créez un SKILL.md avec des procédures vérifiées pour créer des composants React dans Claude Code
4. Incluez des références à la fois au tutoriel YouTube et à la documentation React utilisée

## Normes de vérification

Toutes les compétences créées doivent :
- Référencer au moins deux sources indépendantes (vidéo + documentation)
- Inclure des étapes spécifiques et actionnables
- Fournir des directives d'utilisation claires
- Suivre le formatage établi des compétences Claude Code
- Contenir des procédures vérifiables pouvant être testées

## Licence

Licence MIT - voir le fichier [LICENSE](LICENSE) pour les détails.