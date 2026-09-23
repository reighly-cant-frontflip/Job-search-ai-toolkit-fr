# Guide d'installation — Job Search AI Toolkit

Ce guide installe le même socle de workflows dans Claude ou Codex. Les informations personnelles du candidat restent séparées des skills publics.

## 1. Préparer le profil candidat

Répondre à ce questionnaire dans un document privé :

1. Quels métiers et intitulés sont recherchés ?
2. Quelles localisations et modalités de télétravail sont acceptées ?
3. Quels types de contrat sont acceptés ou exclus ?
4. Quels secteurs et types d'employeurs sont prioritaires ?
5. Quelles langues, autorisations de travail, compétences et outils sont vérifiables ?
6. Quels critères sont éliminatoires ?
7. Quels documents font foi : CV, portfolio, certifications, réalisations chiffrées ?

Ne jamais publier ces réponses dans le dépôt. Les conserver dans un Project Claude, dans l'espace de travail Codex ou dans un document privé fourni au moment de la tâche.

## 2. Installer dans Claude

Les skills personnalisés Claude sont importés séparément sous forme de ZIP.

Pour chaque dossier sous `skills/` :

1. vérifier qu'il contient directement un fichier `SKILL.md` ;
2. compresser le dossier du skill, pas seulement son contenu ;
3. vérifier que la racine du ZIP contient un seul dossier portant le nom du skill ;
4. dans Claude, ouvrir **Customize → Skills** ;
5. choisir **Create skill → Upload a skill**, importer le ZIP et activer le skill.

Exemple de ZIP valide :

```text
job-search.zip
└── job-search/
    └── SKILL.md
```

Un ZIP contenant directement `SKILL.md` à sa racine n'a pas la structure attendue.

Créer ensuite un Project Claude privé pour le candidat et y ajouter :

- son CV actuel ;
- son portfolio si nécessaire ;
- les réponses au questionnaire ;
- éventuellement un export du tracker de candidatures.

Ne pas copier le profil personnel dans les fichiers du skill : cela empêcherait de réutiliser le toolkit pour un autre candidat.

## 3. Installer dans Codex

### Installation de développement

Cloner le dépôt puis utiliser l'une de ces méthodes :

- ajouter le dossier du dépôt comme marketplace local puis installer le plugin ;
- ou copier uniquement les dossiers souhaités depuis `skills/` vers le répertoire de skills de Codex.

Redémarrer Codex ou ouvrir une nouvelle tâche après l'installation afin que les descriptions des skills soient redécouvertes.

### Distribution du toolkit complet

Le dépôt contient un plugin skills-only : il regroupe les trois dossiers sous `skills/` et n'exige aucun serveur MCP. Une fois cette version publiée sur GitHub, ajouter son marketplace avec :

```text
codex plugin marketplace add reighly-cant-frontflip/Job-search-ai-toolkit-fr
```

Installer ensuite `job-search-ai-toolkit-fr` depuis le répertoire des plugins et ouvrir une nouvelle tâche. Une publication ultérieure dans le répertoire universel pourra remplacer cette étape, sans modifier le contenu des skills.


## 4. Préparer le tracker

Le tracker peut être créé dans Notion, Excel, Google Sheets ou un autre outil. Utiliser au minimum ces champs :

| Champ | Usage |
|---|---|
| Entreprise | Nom officiel de l'employeur |
| Poste | Intitulé exact |
| Contrat | CDI, CDD, stage, alternance ou non précisé |
| Localisation | Ville, région ou télétravail |
| Catégorie | Segment défini par le candidat |
| Lien officiel | Page carrière ou ATS vérifié |
| Source | Plateforme ou mot-clé d'origine |
| Statut | À examiner, retenu, candidature envoyée, entretien, refus, etc. |
| Date d'ajout | Date d'entrée dans le tracker |

La clé de déduplication recommandée est `Entreprise + Poste`. Ne pas utiliser l'entreprise seule, car un même employeur peut publier plusieurs postes pertinents.

## 5. Tester les skills

Tester chaque skill avec une demande réaliste :

- Job search : « Recherche des offres correspondant à ce profil, présente d'abord les résultats et n'écris rien dans le tracker sans ma validation. »
- CV : « Compare mon CV à cette offre et indique les modifications nécessaires sans inventer de compétence. »
- Lettre : « Rédige une lettre pour cette offre à partir de mon CV et liste les faits utilisés. »

Vérifier que le système :

- charge le bon skill ;
- n'invente pas d'expérience ni de lien ;
- signale les critères obligatoires non couverts ;
- demande une confirmation avant toute écriture externe ;
- conserve les informations personnelles hors du dépôt public.

## 6. Utilisation au quotidien

Le parcours recommandé est :

```text
Recherche brute → qualification → validation humaine → tracker
                                              ↓
                                    CV adapté → lettre
```

La recherche d'offres, l'adaptation du CV et la lettre sont trois tâches distinctes. Les séparer facilite la vérification des faits et évite qu'une sélection d'offre déclenche automatiquement une candidature.

## Dépannage

### Le skill n'apparaît pas

- vérifier le nom et la présence de `SKILL.md` ;
- vérifier les champs YAML `name` et `description` ;
- vérifier la structure interne du ZIP dans Claude ;
- activer le skill après l'import ;
- ouvrir une nouvelle conversation ou tâche après l'installation.

### Le skill se déclenche au mauvais moment

Rendre sa description plus précise : elle doit expliquer ce que fait le skill et dans quelles demandes il doit être utilisé.

### Le système ne peut pas accéder à une plateforme

Utiliser un export ou un collage des résultats. Ne jamais demander au modèle de contourner une connexion, un captcha ou une vérification de sécurité.
