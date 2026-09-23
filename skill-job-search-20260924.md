# SKILL : Recherche et suivi d'offres

> Fichier à uploader dans ton Project Claude.ai (« Add content »).
> Fait partie du toolkit : Assistant IA de Recherche d'Emploi.

## Déclencheur

L'utilisateur demande de rechercher, collecter, qualifier, dédupliquer ou suivre des offres d'emploi.

## Objectif

Produire une sélection vérifiable d'offres pertinentes, avec leur lien de candidature officiel lorsque celui-ci est disponible, sans postuler ni modifier un tracker sans validation explicite.

## Étape 1 — Préparer la session

Déterminer ou demander uniquement les critères indispensables :

- métiers et intitulés ciblés ;
- localisation et télétravail accepté ;
- types de contrat ;
- secteurs ou entreprises prioritaires ;
- critères éliminatoires ;
- période de publication recherchée.

Si un tracker existe, lire les candidatures et offres déjà traitées avant la recherche. La clé de déduplication par défaut est `Entreprise + Intitulé du poste`, et non l'entreprise seule.

## Étape 2 — Collecter sans juger

Séparer strictement la collecte de l'analyse. Pour chaque source ou mot-clé, relever les offres visibles avant de les filtrer.

Restituer les données brutes avec ces colonnes :

| Source / mot-clé | Entreprise | Intitulé exact | Contrat | Localisation | Date de publication | Résumé en une ligne |
|---|---|---|---|---|---|---|

Lorsque la collecte passe par un navigateur :

- utiliser uniquement une session déjà authentifiée par l'utilisateur ;
- ne jamais demander, deviner ni saisir ses identifiants ;
- ne pas contourner un captcha, une vérification ou une limitation de plateforme ;
- ne pas postuler, enregistrer, désenregistrer ou contacter quelqu'un sans demande explicite ;
- limiter chaque requête à un volume raisonnable et signaler le point d'arrêt.

Si une source n'est pas accessible, demander un collage des résultats ou un export plutôt que d'inventer des offres.

## Étape 3 — Qualifier et dédupliquer

Après la collecte :

1. Dédupliquer les offres par `Entreprise + Intitulé du poste`, y compris entre plusieurs mots-clés.
2. Écarter les offres qui enfreignent un critère éliminatoire explicite.
3. Classer les offres restantes selon les catégories définies par l'utilisateur.
4. Pour chaque exclusion, conserver une raison courte et vérifiable.
5. Signaler séparément les critères obligatoires qui ne peuvent pas être confirmés à partir des informations disponibles.

Ne jamais conclure qu'une offre correspond au profil sur la seule présence de mots-clés. Comparer les missions prioritaires, les critères obligatoires et les preuves disponibles dans le CV ou le profil fourni.

## Étape 4 — Retrouver le lien de candidature

Pour chaque offre retenue, rechercher dans cet ordre :

1. la page carrière officielle de l'entreprise ;
2. son ATS officiel ;
3. la source d'origine si aucun lien officiel stable n'est disponible.

Ne jamais présenter un lien supposé comme vérifié. Si le lien officiel n'est pas retrouvé, écrire `Lien officiel non trouvé` et conserver la source d'origine séparément.

## Étape 5 — Présenter pour validation

Avant toute écriture dans un tracker, présenter :

- les offres brutes ;
- les doublons et exclusions avec leur motif ;
- les offres retenues, classées, avec leur lien officiel ou le statut du lien ;
- le rendement par source ou mot-clé : nombre lu, nombre retenu ;
- une observation concise sur les compétences, niveaux d'expérience ou types d'employeurs récurrents.

Demander une validation explicite. Cette validation est obligatoire avant d'ajouter, modifier ou supprimer des données dans Notion, un tableur ou tout autre tracker.

## Étape 6 — Mettre à jour le suivi après validation

Enregistrer au minimum :

| Entreprise | Poste | Contrat | Localisation | Catégorie | Lien officiel | Source | Statut | Date d'ajout |
|---|---|---|---|---|---|---|---|---|

Ajouter aussi la paire `Entreprise + Poste` à l'historique de déduplication. En cas d'échec d'écriture, ne pas recommencer en boucle : préciser ce qui a été écrit et ce qui reste à faire.

## Contraintes

- Ne jamais inventer une offre, une date, un contrat, un salaire, un lien ou une adéquation avec le profil.
- Ne jamais postuler ou contacter un tiers sans instruction explicite.
- Respecter les limites des plateformes et arrêter la collecte en cas de blocage de sécurité.
- Adapter le processus aux outils réellement disponibles ; ne pas prétendre disposer d'un connecteur absent.

