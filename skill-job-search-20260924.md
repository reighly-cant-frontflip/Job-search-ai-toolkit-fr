# SKILL : Recherche et suivi d'offres

> Fichier à uploader dans ton Project Claude.ai (« Add content »).
> Fait partie du toolkit : Assistant IA de Recherche d'Emploi.

## Déclencheur

L'utilisateur demande de rechercher, collecter, qualifier, dédupliquer ou suivre des offres d'emploi.

## Objectif

Produire une sélection vérifiable d'offres pertinentes, avec leur lien de candidature officiel lorsque celui-ci est disponible, puis maintenir un tracker en session ponctuelle ou récurrente sans jamais déclencher une candidature.

## Modes d'autorisation

Le mode par défaut est `autorisation continue` après que l'utilisateur a explicitement demandé de lancer ou configurer le workflow. Les offres qui satisfont tous les critères objectifs peuvent alors être enregistrées et mises à jour sans confirmation poste par poste.

L'utilisateur peut dire à tout moment « passer en validation par session ». Dans ce mode, présenter le lot et attendre son accord avant chaque série d'écritures. Annoncer le mode actif au premier lancement et rappeler cette possibilité. L'installation du skill ne constitue jamais une autorisation d'écrire.

Les deux modes excluent toute candidature, tout message, toute modification de profil ou de préférences et tout contournement d'authentification.

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
- ne pas postuler, contacter quelqu'un ou modifier un profil ;
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

## Étape 5 — Décider et synchroniser

Présenter ou consigner :

- les offres brutes ;
- les doublons et exclusions avec leur motif ;
- les offres retenues, classées, avec leur lien officiel ou le statut du lien ;
- le rendement par source ou mot-clé : nombre lu, nombre retenu ;
- une observation concise sur les compétences, niveaux d'expérience ou types d'employeurs récurrents.

En `validation par session`, demander une confirmation explicite avant d'écrire. En `autorisation continue`, synchroniser uniquement les offres sans ambiguïté qui respectent les critères déjà approuvés. Si le contrat, la localisation, l'identité exacte du poste ou un critère éliminatoire reste incertain, classer l'offre `à vérifier` sans la synchroniser automatiquement.

## Étape 6 — Mettre à jour et confirmer le suivi

Enregistrer au minimum :

| Entreprise | Poste | Contrat | Localisation | Catégorie | Lien officiel | Source | Statut | Date d'ajout | Date de vérification | Synchronisation |
|---|---|---|---|---|---|---|---|---|---|---|

Ajouter aussi la paire `Entreprise + Poste` à l'historique de déduplication. Confirmer séparément l'écriture dans le tracker et l'enregistrement dans la source lorsque cette fonction fait partie du workflow. Conserver les états partiels `tracker réussi / source en attente` ou `source réussie / tracker en attente`, puis reprendre sans doublon lors de la session suivante.

## Audit récurrent

Pour chaque audit :

1. Lire le tracker, l'historique, la dernière session et la dernière observation marché.
2. Calculer séparément l'intervalle depuis la dernière recherche et l'âge de la dernière observation publiée.
3. Reclasser les offres suivies comme `active`, `à vérifier` ou `expirée`, avec date et motif ; ne pas supprimer l'historique.
4. Faire tourner les sources et requêtes selon leur rendement, puis collecter, dédupliquer et qualifier.
5. Appliquer le mode d'autorisation actif et relire chaque destination après synchronisation.
6. Produire un compte rendu des changements, nouvelles offres, exclusions, rendements, états partiels et incidents d'accès.

La fréquence de recherche ne remet pas à zéro l'observation marché. La renouveler selon son propre âge, par défaut chaque semaine.

## Contraintes

- Ne jamais inventer une offre, une date, un contrat, un salaire, un lien ou une adéquation avec le profil.
- Ne jamais postuler, contacter un tiers ou modifier un profil dans le cadre de ce workflow.
- Respecter les limites des plateformes et arrêter la collecte en cas de blocage de sécurité.
- Adapter le processus aux outils réellement disponibles ; ne pas prétendre disposer d'un connecteur absent.

