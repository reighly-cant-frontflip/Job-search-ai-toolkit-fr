---
name: job-search
description: Rechercher, collecter, qualifier, dédupliquer et suivre des offres, avec validation humaine avant toute écriture ou candidature.
---

# Recherche et suivi d'offres

Utiliser ce skill lorsque l'utilisateur demande de rechercher, collecter, qualifier, dédupliquer ou suivre des offres d'emploi.

Produire une sélection vérifiable avec le lien officiel de candidature lorsqu'il existe. Ne jamais postuler ni modifier un tracker sans validation explicite.

## Préparer la session

Déterminer ou demander uniquement les critères indispensables : métiers ciblés, localisation, télétravail, contrats, secteurs prioritaires, critères éliminatoires et période de publication.

Si un tracker existe, lire les offres déjà traitées. La clé de déduplication par défaut est `Entreprise + Intitulé du poste`, et non l'entreprise seule.

## Collecter avant de juger

Séparer la collecte de l'analyse. Relever les offres visibles avant de les filtrer et restituer :

| Source / mot-clé | Entreprise | Intitulé exact | Contrat | Localisation | Date de publication | Résumé |
|---|---|---|---|---|---|---|

Avec un navigateur, utiliser uniquement une session déjà authentifiée. Ne jamais demander ou saisir les identifiants, contourner un captcha, postuler, enregistrer une offre ou contacter quelqu'un sans demande explicite. Limiter chaque requête à un volume raisonnable et signaler le point d'arrêt.

Si une source est inaccessible, demander un collage ou un export plutôt qu'inventer des offres.

## Qualifier et dédupliquer

Après la collecte :

1. dédupliquer par `Entreprise + Intitulé du poste`, y compris entre plusieurs mots-clés ;
2. écarter les offres qui enfreignent un critère éliminatoire explicite ;
3. classer le reste selon les catégories définies par l'utilisateur ;
4. conserver une raison courte et vérifiable pour chaque exclusion ;
5. signaler les critères obligatoires impossibles à confirmer.

Ne pas conclure à l'adéquation sur la seule présence de mots-clés. Comparer les missions, les critères obligatoires et les preuves du CV ou du profil fourni.

## Retrouver le lien officiel

Chercher dans l'ordre la page carrière de l'entreprise, son ATS officiel, puis la source d'origine. Ne jamais présenter un lien supposé comme vérifié. Si aucun lien officiel stable n'est retrouvé, écrire `Lien officiel non trouvé`.

## Valider avant d'écrire

Présenter les offres brutes, les doublons et exclusions, les offres retenues avec leurs liens, le rendement par source ou mot-clé et une observation concise sur le marché.

Obtenir une validation explicite avant d'ajouter, modifier ou supprimer des données dans Notion, un tableur ou tout autre tracker.

Après validation, enregistrer au minimum : entreprise, poste, contrat, localisation, catégorie, lien officiel, source, statut et date d'ajout. Ajouter aussi la paire `Entreprise + Poste` à l'historique de déduplication.

Ne jamais inventer une offre, une date, un contrat, un salaire, un lien ou une adéquation. En cas d'échec d'écriture, préciser ce qui a réussi et ce qui reste à faire au lieu de recommencer en boucle.
