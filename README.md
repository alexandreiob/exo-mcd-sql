# MCD et SQL

## Contexte

Nous souhaitons réaliser un site qui recense des **films/séries**, les **genres** associés, **les saisons** et le nombre d'épisodes par saison pour les séries, les **acteurs/actrices** et leur **rôle(s)** dans chaque film/série. Des **utilisateurs** pourront se connecter au site afin de poster **des critiques** de films ou d'administrer les données du site.

Voici les infos obtenues suite au brief du projet :

- Un film/série peut appartenir à plusieurs genres et vice-versa.
  - Afin de resreindre le périmètre du projet initial, on ne gère pas les épisodes à part, on renseigne seulement le nombre d'épisodes par saison.
- Un acteur peut jouer dans plusieurs films/séries et avoir un à plusieurs rôles par film/série.
- Des critiques pourront être postés par les utilisateurs sur chaque film/série.
- Les utilisateurs du site auront un rôle donné (*Utilisateur* ou *Administrateur*).

## MCD

Vous devez concevoir le MCD correspondant au brief. [Ces fiches récap'](https://kourou.oclock.io/ressources/fiche-recap/bases-de-donnees/) peuvent vous aider.

A faire avec papier/crayon ou avec [MoCoDo](http://mocodo.wingi.net/).

### Rappel de syntaxe MoCoDo

#### Définir une entité

`Entité A: attribut 1, attribut 2, ...`

#### Définir une association

`Association 1, 01 Entité A, 1N Entité B, ... : attribut 1, attribut 2, ...`

### Etape 1 : Entités

- Définir les entités (sans relations).
- Identifier les attributs possibles de chaque entité.

### Etape 2 : Relations

- Ecrire les relations qui existent entre les entités.

### Etape 3 : Cardinalités

- Préciser les cardinalités de chaque côté de la relation.

## SQL

> Créer une base de données `cinema` et importez la base fournie dans le script `cinema.sql`.

## Clés étrangères

Certaines clés étrangères sont créées, d'autres non.

- Analyser les clés étrangères existantes.
- Ajouter les clés étrangères, selon le MCD final.

### Requêtes SQL pour le projet

> Consigner chaque requête dans un fichier SQL ou Markdown. On pourra s'en servir par la suite, quand on intégrera la base de données sous Symfony.

Si besoin de rappels ou d'aide, [le site *sql.sh*](https://sql.sh/) est une référence SQL avec des exemples clairs.

#### Requêtes pour les pages

- Récupérer tous les films.
- Récupérer les acteurs et leur(s) rôle(s) pour un film donné.
- Récupérer les genres associés à un film donné.
- Récupérer les saisons associées à un film/série donné.
- Récupérer les critiques pour un film donné.
- Récupérer les critiques pour un film donné, ainsi que le nom de l'utilisateur associé.
- Calculer, pour chaque film, la moyenne des critiques par film (en une seule requête).
  - Idem pour un film donné.

#### Requêtes de recherche

- Récupérer tous les films pour une année de sortie donnée.
- Récupérer tous les films pour un tire donné (par ex. 'Epic Movie').
- Récupérer tous les films dont le titre *contient* une chaîne donnée.

#### Bonus : Pagination

> Nombre de films par page : 10 (par ex.)

- Récupérer la liste des films de la page 2 (grâce à [LIMIT](https://sql.sh/cours/limit)).
- Testez la requête en faisant varier le nombre de films par page et le numéro de page.

### Contraintes sur le schéma SQL

Modifiez votre schéma pour permettre :

- Qu'il ne puisse y avoir deux films identiques.
    - Identifier les autres champs uniques si existants.
- Qu'une critique puisse être associée à aucun utilisateur (anonyme).
- Que la suppression d'un film implique la suppression de l'intégralité de son contenu (cascade).
- Que la suppression d'un utilisateur conserve ses critiques.
