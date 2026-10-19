# Changelog

Toutes les évolutions notables de ce toolkit sont documentées ici.

Format inspiré de [Keep a Changelog](https://keepachangelog.com/fr/1.1.0/).
Ce projet suit un versionnement sémantique simplifié : **majeure** = changement de structure ou de périmètre, **mineure** = ajout de contenu, **correctif** = corrections et clarifications.

---

## [3.3.0] — 2026-10-19

### Ajouté
- Parcours guidé de création d'un système Notion de recherche d'emploi, depuis les critères candidat jusqu'à la vérification du Dashboard
- Architecture par défaut avec une base `Jobs` unique, six vues d'action et les pages `Search Sessions`, `Market Observations`, `Search Source Library` et `Operating Rules`
- Schéma portable précisant les propriétés, types, options de statut, états de synchronisation, filtres, tris et groupements
- Gabarits de session de recherche et d'observation marché, avec pages modèles lorsque les templates natifs ne sont pas supportés
- Parcours distinct pour raccorder et migrer un tracker existant sans dupliquer la source de vérité
- Modes dégradés explicites pour les connexions absentes, en lecture seule ou incapables de créer certaines vues ou templates

### Modifié
- Le skill `job-search` se déclenche désormais aussi pour construire ou raccorder un tracker Notion complet
- L'audit récurrent utilise le Dashboard déployé comme point d'entrée, `Jobs` comme source de vérité et les pages opératoires comme mémoire
- Le guide d'installation commence maintenant par un prompt de déploiement Notion 0→1 et décrit le contrôle post-création
- Les manifests de plugin passent à la version `3.3.0`

### Sécurité et confidentialité
- Une demande explicite de construction autorise uniquement les composants présentés dans la destination confirmée ; l'installation seule ne crée rien
- La planification d'une veille reste une action séparée qui nécessite une demande explicite
- Les liens privés restent dans l'espace Notion de l'utilisateur et aucune donnée personnelle du workflow d'origine n'est publiée
- Le skill ne prétend jamais qu'une vue, un template ou une propriété non supportée a été créé

## [3.2.0] — 2026-10-18

### Ajouté
- Deux modes d'autorisation pour le suivi des offres : `autorisation continue` par défaut après activation explicite du workflow, et `validation par session` activable à tout moment
- Procédure d'audit récurrent avec contrôle des offres existantes, rotation des sources et requêtes, compte rendu et gestion des incidents d'accès
- États génériques `active`, `à vérifier` et `expirée`, accompagnés d'une date de contrôle et d'un motif
- Synchronisation confirmée séparément entre le tracker et la source d'offres, avec reprise idempotente des réussites partielles
- Deux horloges indépendantes pour la dernière recherche et la dernière observation marché

### Modifié
- Le skill `job-search` couvre maintenant les sessions ponctuelles, la maintenance du tracker et les audits récurrents
- Le tracker recommandé inclut la date de vérification et l'état de synchronisation
- Le guide d'installation documente le choix du mode d'autorisation et la configuration d'une veille récurrente
- Les manifests de plugin passent à la version `3.2.0`

### Sécurité et confidentialité
- L'installation du toolkit ne constitue ni une autorisation d'écriture ni la création d'une tâche planifiée
- Aucun mode n'autorise une candidature, un message, une modification de profil ou un contournement d'authentification
- Les offres ambiguës restent `à vérifier` et ne sont jamais synchronisées automatiquement
- Toutes les fonctions issues d'un workflow privé ont été généralisées sans publier de donnée personnelle, d'identifiant de tracker, d'adresse e-mail ou d'URL privée

## [3.1.0] — 2026-09-24

### Ajouté
- Skill portable `job-search` pour la collecte, la qualification, la déduplication et le suivi des offres
- Structure standard `skills/<nom>/SKILL.md`, commune à Claude et Codex
- Guide d'installation réel sous `guide/job-search-ai-setup.md`
- Manifestes de plugin portable et Codex
- Marketplace de dépôt pour installer le toolkit complet dans Codex

### Modifié
- Skill de lettre de motivation renforcé par la vérification des faits, l'analyse des critères obligatoires et la validation avant création de document
- Skill CV migré vers le format Agent Skills avec métadonnées YAML
- README corrigé : tous les chemins du Quick Start correspondent désormais à des fichiers présents

### Compatibilité
- Les anciens fichiers datés à la racine sont conservés temporairement
- Les nouvelles installations doivent utiliser les fichiers canoniques sous `skills/`

## [3.0] — 2026-08-22

Première publication publique sur GitHub. Le toolkit passe d'un fichier unique distribué par mail à un dépôt structuré et versionné.

### Ajouté
- `README.md` — présentation du projet, public cible, démarrage rapide
- `LICENSE` — CC BY-SA 4.0, remplace la mention informelle « Usage libre »
- `CHANGELOG.md` — ce fichier
- Arborescence `guide/` et `skills/` pour séparer la documentation des fichiers opérationnels

### Modifié
- `skill-cv.md` et `skill-lm.md` extraits du guide principal et publiés comme fichiers autonomes téléchargeables — plus besoin de copier-coller depuis un bloc de code pour les créer
- Chaque skill porte désormais un en-tête rappelant son mode d'installation dans un Project Claude.ai

### À noter pour les utilisateurs des versions précédentes
Le contenu des skills est inchangé. Si tu as déjà installé la V2, tu n'as rien à refaire — les fichiers autonomes sont strictement équivalents à ce que tu as créé manuellement.

---

## [2.0] — 2026-05

Passage d'un guide personnel à un guide universel, utilisable par n'importe quel candidat.

### Ajouté
- Questionnaire d'onboarding en 7 points en tête de guide — Claude génère les Project Instructions à partir des réponses
- Section « Ce que ce guide va t'apporter » pour clarifier le périmètre avant installation

### Modifié
- Suppression du profil personnel codé en dur dans le template de Project Instructions, remplacé par des variables `[À REMPLIR]`
- Skills reformulés au masculin/féminin neutre (« l'utilisateur » au lieu de « l'utilisatrice »)
- Section marché : retrait des références nominatives à des écoles et à des employeurs spécifiques
- Génération du prompt Claude in Chrome désormais déléguée à Claude plutôt que fournie en dur

### Retiré
- Mention « non redistribuable » — le guide devient librement partageable

---

## [1.0] — 2026-05

Version initiale, rédigée pour un usage personnel et une distribution directe.

### Ajouté
- Guide d'installation complet en 5 parties : Project Claude.ai, skills, tracker Notion, Claude in Chrome, contexte marché France 2026
- Skill de personnalisation de CV (analyse d'offre, mots-clés ATS, reformulation d'accroche)
- Skill de rédaction de lettre de motivation (structure en 3 paragraphes, contrôle qualité, 250-320 mots)
- Structure de tracker Notion en 4 sections avec système de statuts
- Tableau comparatif d'efficacité des plateformes de recherche d'emploi françaises
- Check-list finale d'installation et section dépannage

---

## Sur la feuille de route

Éléments envisagés pour les prochaines versions, sans engagement de date :
- Skill de préparation d'entretien avec simulation par Claude
- Workflow structuré de débriefing post-entretien
- Chapitre « réalité du marché » appuyé sur des données de candidatures anonymisées
- Adaptations à d'autres marchés francophones (Belgique, Suisse, Québec)
