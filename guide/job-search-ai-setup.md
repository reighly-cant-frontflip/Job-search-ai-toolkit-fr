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
8. Le suivi doit-il rester en `autorisation continue` — mode par défaut après activation du workflow — ou passer en `validation par session` ?

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
    ├── SKILL.md
    └── references/
        ├── notion-schema.md
        ├── notion-site-setup.md
        └── recurring-audit.md
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


## 4. Construire le site Notion de zéro

Connecter Notion, puis lancer par exemple :

> Crée mon système complet de recherche d'emploi dans Notion. Guide-moi depuis mes critères jusqu'au Dashboard, vérifie la structure créée et ne planifie rien sans me le proposer séparément.

Le skill propose soit de créer un nouveau site, soit de raccorder un tracker existant. Pour une création, il recueille les rôles, localisations, contrats, tracks, exclusions, sources et cadence souhaitée, puis affiche la destination et la structure avant d'écrire.

Le modèle par défaut est :

```text
Job Search Dashboard
├── Jobs — base unique des offres
├── Search Sessions
├── Market Observations
├── Search Source Library
└── Operating Rules
```

La base `Jobs` contient :

| Champ | Usage |
|---|---|
| Poste | Intitulé exact et titre de la page |
| Entreprise | Nom officiel de l'employeur |
| Contrat | Type de contrat adapté au marché |
| Localisation | Ville, région et modalité de travail |
| Track | Axe de recherche défini par l'utilisateur |
| Priorité | haute, moyenne ou basse |
| Statut | active, à vérifier, expirée ou applied |
| Source | Plateforme, ATS ou autre origine |
| Lien officiel | Page carrière ou ATS stable |
| Dates | Publication, ajout et dernière vérification |
| Adéquation / Contrainte | Motif de correspondance et point d'attention |
| Synchronisation | État confirmé du tracker et de la source |
| Clé de déduplication | Valeur normalisée `entreprise|poste` |

Le Dashboard ajoute les vues `À traiter — Active`, `À vérifier`, `Expirées`, `Candidatures envoyées`, `Nouvelles — 7 jours` et `Par track`. Après création, le skill relit les propriétés, options, filtres, vues et pages modèles avant d'annoncer le site comme terminé.

Sans connexion ou sans permission d'écriture, il fournit le blueprint et les étapes manuelles en signalant que le site n'a pas été construit. Si la connexion ne peut pas créer les vues ou templates, elle crée les composants supportés et énumère précisément le travail restant.

La clé de déduplication est `Entreprise + Poste`. Ne jamais utiliser l'entreprise seule, car un même employeur peut publier plusieurs postes pertinents.

## 5. Tester les skills

Tester chaque skill avec une demande réaliste :

- Installation Notion : « Construis mon Dashboard de recherche d'emploi dans Notion à partir de zéro, puis vérifie chaque composant. »
- Job search ponctuel : « Recherche des offres correspondant à ce profil et passe en validation par session avant d'écrire dans mon tracker. »
- Audit récurrent : « Configure une veille hebdomadaire de ces sources et synchronise les offres qualifiées avec mon tracker. »
- CV : « Compare mon CV à cette offre et indique les modifications nécessaires sans inventer de compétence. »
- Lettre : « Rédige une lettre pour cette offre à partir de mon CV et liste les faits utilisés. »

Vérifier que le système :

- charge le bon skill ;
- distingue une création réelle, un raccordement, un plan manuel et un déploiement partiel ;
- ne prétend pas avoir créé une propriété, une vue ou un template non supporté ;
- n'invente pas d'expérience ni de lien ;
- signale les critères obligatoires non couverts ;
- annonce le mode d'autorisation actif et explique comment le changer ;
- n'interprète pas l'installation du skill comme une autorisation d'écrire ;
- ne synchronise automatiquement aucune offre ambiguë ;
- conserve les informations personnelles hors du dépôt public.

## 6. Utilisation au quotidien

Le parcours recommandé est :

```text
Recherche brute → qualification → autorisation active → tracker/source
                                                   ↓
                                         CV adapté → lettre
```

La recherche d'offres, l'adaptation du CV et la lettre sont trois tâches distinctes. Les séparer facilite la vérification des faits et évite qu'une sélection d'offre déclenche automatiquement une candidature.

### Autorisation continue et validation par session

`autorisation continue` est le mode par défaut lorsqu'un utilisateur demande explicitement de lancer ou configurer le workflow. Il permet d'ajouter et de mettre à jour les offres qui satisfont sans ambiguïté les critères approuvés. Il ne permet jamais de postuler, d'envoyer un message ou de modifier un profil.

L'utilisateur peut dire à tout moment « passer en validation par session ». Le système présente alors chaque lot proposé et attend un accord avant les écritures. Dire « passer en autorisation continue » réactive le mode par défaut pour le périmètre déjà approuvé.

L'installation seule ne déclenche ni autorisation ni tâche planifiée.

## 7. Configurer un audit récurrent

Définir avec l'utilisateur :

- la cadence et le fuseau horaire ;
- les sources à consulter et le volume maximal par exécution ;
- les critères de sélection et d'exclusion ;
- le tracker et, éventuellement, la liste d'offres enregistrées à synchroniser ;
- le canal du compte rendu ;
- le mode d'autorisation souhaité.

Chaque audit contrôle d'abord les offres déjà suivies, puis recherche de nouvelles offres. Il conserve les états `active`, `à vérifier` et `expirée`, déduplique par `Entreprise + Poste` et confirme séparément chaque destination. Une synchronisation partielle est reprise lors de l'exécution suivante sans créer de doublon.

Maintenir deux horloges distinctes : l'intervalle depuis la dernière recherche et l'âge de la dernière observation marché. Une recherche fréquente ne doit pas provoquer le remplacement artificiel de l'observation à chaque exécution.

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
