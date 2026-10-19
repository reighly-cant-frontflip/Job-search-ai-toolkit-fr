# Schéma du site Notion

Ce schéma décrit le modèle par défaut. Adapter les libellés à la langue de l'utilisateur sans changer leur rôle. Ne pas créer plusieurs bases pour représenter les mêmes offres.

## Arborescence

```text
Job Search Dashboard
├── Jobs
├── Search Sessions
├── Market Observations
├── Search Source Library
└── Operating Rules
```

`Jobs` est la seule base de données obligatoire. Les quatre autres composants sont des pages structurées afin de garder le déploiement initial simple.

## Base Jobs

Un enregistrement représente une offre exacte. Utiliser `Entreprise + Poste` comme clé de déduplication normalisée.

| Propriété | Type recommandé | Rôle / valeurs |
|---|---|---|
| Poste | Titre | Intitulé exact de l'offre |
| Entreprise | Texte | Nom officiel de l'employeur |
| Contrat | Sélection | Options adaptées au marché et aux critères utilisateur |
| Localisation | Texte | Ville, région et modalité de travail |
| Track | Sélection | Axes définis pendant l'onboarding |
| Priorité | Sélection | haute, moyenne, basse |
| Statut | Sélection ou statut | active, à vérifier, expirée, applied |
| Source | Sélection ou texte | Plateforme, ATS ou autre origine |
| Lien officiel | URL | Page carrière ou ATS stable ; source d'origine si aucun lien stable n'existe |
| Date de publication | Date | Facultative si la source ne l'affiche pas |
| Date d'ajout | Date | Entrée dans le système |
| Dernière vérification | Date | Dernier contrôle de validité |
| Adéquation | Texte | Motif vérifiable de correspondance |
| Contrainte | Texte | Écart, ambiguïté ou point à vérifier |
| Synchronisation | Sélection | synchronisée ; déjà présente ; tracker réussi / source en attente ; source réussie / tracker en attente ; à vérifier ; introuvable |
| Clé de déduplication | Texte | Valeur normalisée `entreprise|poste` |

Utiliser une propriété texte pour la clé afin qu'elle reste portable entre connexions. La remplir au moment de la création ou de la mise à jour. Garder les descriptions longues, critères détaillés et notes de décision dans le contenu de la page de l'offre.

## Vues requises

| Vue | Filtre | Tri / groupement |
|---|---|---|
| À traiter — Active | Statut = active | Priorité puis Date d'ajout décroissante |
| À vérifier | Statut = à vérifier | Dernière vérification croissante |
| Expirées | Statut = expirée | Dernière vérification décroissante |
| Candidatures envoyées | Statut = applied | Date d'ajout décroissante |
| Nouvelles — 7 jours | Date d'ajout dans les 7 derniers jours | Date d'ajout décroissante |
| Par track | Statut n'est pas expirée | Grouper par Track, puis Priorité |

Si la connexion ne permet pas de créer ou vérifier les vues, fournir exactement ces filtres et tris comme étapes manuelles. Ne jamais annoncer une vue comme terminée sur la seule base de son nom.

## Page Search Sessions

Créer une introduction expliquant qu'une seule page est utilisée par exécution, puis une page modèle `TEMPLATE — Search Session` :

```markdown
# Search Session — YYYY-MM-DD

Mode : ponctuel ou récurrent
Autorisation : continue ou validation par session
Intervalle depuis la dernière recherche : X jours

## Sources et requêtes
| Source | Requête | Éléments lus | Retenus | Motif d'arrêt |

## Doublons et exclusions
| Entreprise | Poste | Motif |

## Nouvelles offres et synchronisation
| Entreprise | Poste | Track | Statut | Synchronisation | Lien officiel |

## Incidents et suites

## Observation marché
Observation publiée : oui/non
Âge de l'observation précédente : X jours
```

## Page Market Observations

Créer une page modèle `TEMPLATE — Market Observation` :

```markdown
# Market Observation — YYYY-MM-DD

Période observée :
Sources consultées :
Volume et qualité :
Employeurs et contrats récurrents :
Compétences ou niveaux d'expérience récurrents :
Évolution depuis l'observation précédente :
Limites de l'échantillon :
```

Une observation est une synthèse, pas une offre active. La recherche fréquente ne remet pas à zéro son horloge de publication.

## Page Search Source Library

Créer une table simple ou, si elle n'est pas supportée, une liste structurée avec :

| Source | Track | Nom de requête | URL ou point d'entrée | Fenêtre | Dernière exécution | Rendement | Active |
|---|---|---|---|---|---|---|---|

Ne pas inventer d'URL. Les liens authentifiés ou privés restent exclusivement dans l'espace utilisateur.

## Page Operating Rules

Enregistrer :

- objectifs et intitulés ;
- localisations et modalités acceptées ;
- contrats acceptés et exclus ;
- tracks et définitions ;
- critères éliminatoires ;
- clé de déduplication ;
- mode d'autorisation actif et commandes de changement ;
- cadence et fuseau horaire souhaités ;
- date de la dernière recherche ;
- date de la dernière observation publiée ;
- limites absolues : aucune candidature, aucun message, aucune modification de profil.

## Données initiales

Ne pas créer de fausses offres pour illustrer la base. Les pages modèles peuvent contenir des libellés et des lignes vides. Ajouter des sources ou règles uniquement à partir des réponses de l'utilisateur.
