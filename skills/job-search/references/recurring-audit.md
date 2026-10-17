# Audit récurrent des offres

Lire cette référence lorsqu'un utilisateur demande de configurer ou d'exécuter une veille récurrente, un contrôle du tracker ou une synchronisation continue.

## Activation et autorisation

L'installation du toolkit ne déclenche aucune écriture. Le workflow récurrent commence lorsque l'utilisateur demande explicitement de le lancer ou de le configurer.

À la première exécution, afficher :

- la cadence et le périmètre connus ;
- le mode actif, `autorisation continue` par défaut ;
- la possibilité de passer immédiatement ou ultérieurement en `validation par session`.

L'autorisation continue couvre seulement l'ajout ou la mise à jour d'offres répondant aux critères approuvés, ainsi que leur enregistrement dans une source lorsque l'utilisateur a inclus cette synchronisation dans le workflow. Elle ne couvre jamais les candidatures, messages, modifications de profil ou préférences, suppressions, achats, abonnements ou contournements de sécurité.

## Séquence d'un audit

1. Lire le tracker, l'historique de déduplication, la dernière session et la dernière observation marché.
2. Calculer `intervalle_recherche` et `age_observation` séparément.
3. Vérifier les offres suivies : identité exacte, contrat, localisation, URL résolue, présence de l'annonce et accès de candidature.
4. Classer chaque offre `active`, `à vérifier` ou `expirée`, avec la date et le motif. Conserver les offres expirées dans l'historique.
5. Choisir les sources et requêtes selon les critères, la fraîcheur attendue et le rendement antérieur. Signaler les requêtes à rendement nul répété au lieu de les relancer indéfiniment.
6. Collecter avant de filtrer, puis dédupliquer globalement par `Entreprise + Intitulé du poste`.
7. Qualifier les résultats. Toute ambiguïté bloquante place l'offre `à vérifier`.
8. Appliquer le mode d'autorisation actif, puis synchroniser le tracker et, si prévu, la liste enregistrée de la source.
9. Relire chaque destination. Marquer toute réussite partielle et conserver assez d'information pour reprendre sans doublon.
10. Produire un compte rendu : périmètre contrôlé, changements d'état, requêtes et sources, rendement, exclusions, nouvelles offres, synchronisations partielles, observation marché et incidents d'accès.

## Observation marché

Le renouvellement de l'observation dépend de `age_observation`, pas de la fréquence des recherches. Utiliser par défaut une cadence hebdomadaire :

- `age_observation >= 7 jours` : publier une nouvelle observation consolidée ;
- `age_observation < 7 jours` : relire l'observation existante et signaler qu'elle reste en vigueur.

L'observation peut résumer le volume, les types d'employeurs, les niveaux d'expérience, les contrats et les compétences récurrentes. La distinguer clairement d'une offre active.

## États de synchronisation

Utiliser des états explicites et idempotents :

- `synchronisée` : tracker et source confirmés ;
- `déjà présente` : aucune nouvelle action nécessaire ;
- `tracker réussi / source en attente` ;
- `source réussie / tracker en attente` ;
- `à vérifier` : information bloquante ou accès incertain ;
- `introuvable` : l'offre exacte ne peut plus être confirmée.

Lors d'une reprise, vérifier l'état déjà réussi avant d'agir sur l'autre destination. Ne jamais basculer aveuglément un bouton d'enregistrement et ne jamais créer une seconde ligne pour la même paire de déduplication.

## Incidents et arrêt

Arrêter la partie concernée en cas de connexion expirée, captcha, vérification de sécurité ou absence de connecteur. Conserver le rapport et l'état partiel dans le tracker accessible. Ne pas remplacer un outil indisponible par un autre stockage sans accord de l'utilisateur.
