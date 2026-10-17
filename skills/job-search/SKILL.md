---
name: job-search
description: Rechercher, auditer, qualifier, dédupliquer et synchroniser des offres avec un tracker, en session ponctuelle ou récurrente, sans jamais déclencher une candidature.
---

# Recherche et suivi d'offres

Produire une sélection vérifiable avec le lien officiel de candidature lorsqu'il existe. Utiliser ce skill pour une recherche ponctuelle, la maintenance d'un tracker ou un audit récurrent.

## Choisir le mode d'autorisation

Deux modes gouvernent uniquement l'enregistrement et la mise à jour des offres dans le tracker ou dans la liste d'offres enregistrées de la source :

- `autorisation continue` — mode par défaut après que l'utilisateur a explicitement demandé de lancer ou configurer le workflow. Les offres qui satisfont tous les critères objectifs peuvent être synchronisées sans confirmation poste par poste.
- `validation par session` — présenter le lot proposé et attendre une confirmation explicite avant chaque série d'écritures.

Au premier lancement, annoncer le mode par défaut et indiquer que l'utilisateur peut dire à tout moment « passer en validation par session » ou « passer en autorisation continue ». L'installation du skill ne constitue pas une autorisation d'écrire. Si aucun workflow n'a encore été demandé, obtenir cette demande avant toute mutation externe.

Dans les deux modes, ne jamais postuler, envoyer un message, modifier un profil ou des préférences, retirer une candidature, ni contourner une authentification. Ne jamais supprimer une offre du tracker : la reclasser comme expirée avec son motif.

## Préparer la session

Déterminer ou demander uniquement les critères indispensables : métiers ciblés, localisation, télétravail, contrats, secteurs prioritaires, critères éliminatoires et période de publication.

Si un tracker existe, lire les offres déjà traitées. La clé de déduplication par défaut est `Entreprise + Intitulé du poste`, et non l'entreprise seule.

Pour un workflow récurrent, lire [la procédure d'audit](references/recurring-audit.md) avant d'agir. Conserver séparément :

- `intervalle_recherche`, depuis la dernière session complète ;
- `age_observation`, depuis la dernière observation marché publiée.

Le rythme de recherche ne remet pas à zéro l'âge de l'observation.

## Collecter avant de juger

Séparer la collecte de l'analyse. Relever les offres visibles avant de les filtrer et restituer :

| Source / mot-clé | Entreprise | Intitulé exact | Contrat | Localisation | Date de publication | Résumé |
|---|---|---|---|---|---|---|

Avec un navigateur, utiliser uniquement une session déjà authentifiée. Ne jamais demander ou saisir les identifiants, contourner un captcha, postuler ou contacter quelqu'un. Limiter chaque requête à un volume raisonnable et signaler le point d'arrêt.

Si une source est inaccessible, demander un collage ou un export plutôt qu'inventer des offres. Pour une recherche récurrente, faire tourner les sources et mots-clés selon leur rendement historique au lieu de répéter systématiquement les mêmes requêtes.

## Qualifier et dédupliquer

Après la collecte :

1. dédupliquer par `Entreprise + Intitulé du poste`, y compris entre plusieurs sources et sessions ;
2. écarter les offres qui enfreignent un critère éliminatoire explicite ;
3. classer le reste selon les catégories définies par l'utilisateur ;
4. conserver une raison courte et vérifiable pour chaque exclusion ;
5. signaler les critères obligatoires impossibles à confirmer.

Ne pas conclure à l'adéquation sur la seule présence de mots-clés. Comparer les missions, les critères obligatoires et les preuves du CV ou du profil fourni.

Si le contrat, la localisation, l'identité exacte du poste ou un critère éliminatoire reste ambigu, classer l'offre `à vérifier` et ne pas la synchroniser automatiquement.

## Retrouver et vérifier le lien officiel

Chercher dans l'ordre la page carrière de l'entreprise, son ATS officiel, puis la source d'origine. Ne jamais présenter un lien supposé comme vérifié. Si aucun lien officiel stable n'est retrouvé, écrire `Lien officiel non trouvé`.

Lors d'un audit, classer chaque offre suivie :

- `active` si l'offre exacte et un accès de candidature sont présents ;
- `à vérifier` si l'accès ou l'identité du poste est incertain ou techniquement inaccessible ;
- `expirée` pour un retrait explicite, une erreur 404/410 ou une redirection générique sans le poste.

Conserver la date de contrôle et un motif court.

## Décider et synchroniser

Présenter ou consigner les offres brutes, doublons, exclusions, offres retenues, rendement par source et observation marché.

En `validation par session`, attendre l'accord sur le lot avant toute écriture. En `autorisation continue`, synchroniser uniquement les offres sans ambiguïté qui satisfont les critères déjà approuvés. Une modification des critères ou du périmètre requiert une nouvelle instruction de l'utilisateur.

Pour chaque offre synchronisée, confirmer séparément :

1. l'écriture ou la mise à jour dans le tracker ;
2. l'enregistrement dans la source, si cette fonction existe et fait partie du workflow demandé.

Consigner un état tel que `synchronisée`, `tracker réussi / source en attente`, `source réussie / tracker en attente`, `déjà présente` ou `introuvable`. Reprendre une synchronisation partielle lors de la session suivante sans recréer l'entrée déjà réussie.

Enregistrer au minimum : entreprise, poste, contrat, localisation, catégorie, lien officiel, source, statut, date d'ajout, date de vérification et état de synchronisation. Ajouter aussi la paire `Entreprise + Poste` à l'historique de déduplication.

En cas d'échec, préciser ce qui a réussi et ce qui reste à faire au lieu de recommencer en boucle. Ne jamais inventer une offre, une date, un contrat, un salaire, un lien ou une adéquation.
