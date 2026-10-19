# Déployer le système Notion de zéro

Lire cette référence pour créer un site Notion de recherche d'emploi, raccorder un tracker existant ou reprendre un déploiement partiel. Lire aussi [le schéma du site](notion-schema.md) avant toute création.

## Résultat attendu

Livrer un Dashboard utilisable immédiatement, avec une base `Jobs` comme source de vérité, des vues orientées action et quatre pages opératoires : sessions, observations marché, bibliothèque de sources et règles de fonctionnement.

## 1. Vérifier les capacités

Détecter une seule fois les outils Notion réellement disponibles et leur portée : lecture, création de pages, création de bases, propriétés, vues, templates et mise à jour. Utiliser les schémas exposés par la connexion, sans inventer de méthode ni de connecteur.

- Sans connexion : fournir le blueprint et les étapes manuelles, puis dire clairement que rien n'a été créé.
- En lecture seule : inspecter l'existant et rendre un plan de déploiement sans prétendre avoir écrit.
- Si certaines fonctions manquent : créer les composants supportés, consigner les étapes manuelles restantes et qualifier le déploiement de partiel.

## 2. Choisir création ou raccordement

Demander une seule décision : créer un nouveau système ou raccorder un tracker existant.

Pour une création, recueillir uniquement :

- rôles et intitulés recherchés ;
- localisations et modalités de travail ;
- contrats acceptés et exclus ;
- tracks ou axes de recherche ;
- critères éliminatoires ;
- sources de recherche initiales ;
- cadence et fuseau horaire souhaités, sans créer encore de tâche planifiée.

Pour un raccordement, lire la base, ses propriétés, ses options, ses relations, ses vues et un échantillon borné d'enregistrements. Définir la clé représentant une offre exacte. Réutiliser la structure compatible et présenter le mapping des écarts qui affectent l'identité, le statut ou la conservation des données.

## 3. Confirmer la destination

Avant de construire, afficher :

- la page parent ou l'espace cible ;
- les composants à créer ou à compléter ;
- les tracks et critères recueillis ;
- le mode `autorisation continue`, actif par défaut après cette demande explicite ;
- la commande permettant de passer en `validation par session`.

Ne demander une précision supplémentaire que si la destination ou l'identité des données reste ambiguë.

## 4. Construire dans l'ordre

1. Créer la page `Job Search Dashboard` sous la destination confirmée.
2. Créer la base `Jobs` avec les propriétés et options du schéma.
3. Créer les vues après leurs propriétés. Vérifier leurs filtres et tris réels ; un nom de vue ne prouve pas sa configuration.
4. Créer `Search Sessions`, `Market Observations`, `Search Source Library` et `Operating Rules` sous le Dashboard.
5. Ajouter les gabarits décrits dans le schéma. Si les templates natifs ne sont pas pris en charge, créer une page `TEMPLATE — …` dans la section correspondante.
6. Écrire les critères, tracks, exclusions, cadence souhaitée et mode d'autorisation dans `Operating Rules`.
7. Ajouter les sources initiales sans inventer d'URL. Une URL privée fournie par l'utilisateur reste dans son espace Notion, jamais dans le toolkit public.

Conserver les identifiants des objets créés. Après un résultat incertain, relire l'état avant de réessayer et reprendre uniquement les composants absents.

## 5. Vérifier le déploiement

Relire ce que les résultats d'écriture ne garantissent pas et contrôler :

- une base `Jobs` unique, sans doublon concurrent ;
- la présence et le type de chaque propriété obligatoire ;
- les options de statut et de synchronisation ;
- les filtres, groupements et tris de chaque vue ;
- les quatre pages opératoires et leurs gabarits ;
- les règles utilisateur réellement enregistrées ;
- l'absence de données d'exemple présentées comme des offres réelles.

Une vue filtrée organise le travail mais ne constitue jamais une limite d'accès ou de confidentialité.

## 6. Mettre en service

Retourner :

- le lien du Dashboard ;
- les composants créés, réutilisés, partiels ou non supportés ;
- le mode d'autorisation actif et la manière de le changer ;
- la première action recommandée : importer l'historique, lancer une recherche ponctuelle ou compléter la bibliothèque de sources.

Proposer ensuite la veille récurrente. Ne la planifier que sur demande explicite, avec une cadence, un fuseau horaire, un périmètre et un canal de compte rendu déterminés.

## Migration d'un tracker existant

Préserver les données et les pages sources. Avant de changer une propriété, établir le mapping valeur par valeur et vérifier les enregistrements concernés. Ne jamais utiliser une vue filtrée comme inventaire complet. Créer d'abord les propriétés manquantes, migrer un échantillon, vérifier le résultat, puis couvrir le reste. En cas de doute ou de changement irréversible, s'arrêter et demander confirmation.
