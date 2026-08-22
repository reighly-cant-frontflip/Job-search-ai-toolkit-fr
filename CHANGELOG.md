# Changelog

Toutes les évolutions notables de ce toolkit sont documentées ici.

Format inspiré de [Keep a Changelog](https://keepachangelog.com/fr/1.1.0/).
Ce projet suit un versionnement sémantique simplifié : **majeure** = changement de structure ou de périmètre, **mineure** = ajout de contenu, **correctif** = corrections et clarifications.

---

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
