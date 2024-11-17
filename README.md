# vue-assessment-1

Création d'un créateur de fichier `package.json`.

## Partie 1 : Nom du package (7 points)

Créer des champs de formulaire permettant de gérer le nom d'un package Node.js, la version ainsi que la description de ce dernier.

Chaque fois que ce nom est modifié, il doit être représenté en dessous du formulaire sous la forme d'un object JSON permettant d'avoir la représentation direct du résultat de la modification de ce dernier.

Utiliser une balise `<pre>` et une balise `<code>` afin d'afficher la représentation du `package.json`.

Le contenu du `package.json` ne doit pas pouvoir être modifiable, mais elle doit pouvoir changer en fonction du contenu de ces champs de formulaire.

```json
{
  "name": "@aminnairi/react-table",
  "version": "4.2.7",
  "description": "React table component for easy data manipulation"
}
```

## Partie 2 : Keywords (8 points)

Ajouter un bouton permettant de faire apparaître dynamiquement des champs de formulaire permettant d'ajouter un mot-clé.

Un mot-clé est un tableau de chaînes de caractères, représenté dans un fichier `package.json`.

Le tableau doit faire partie des données déjà existantes de votre précédent `package.json` dynamiquement construit.

Pour chaque mot-clé ainsi ajouté, ajouter un bouton permettant de supprimer ce dernier. Il doit également être supprimé du tableaux des mots-clés, et donc du `package.json` généré dynamiquement.

```json
{
  "name": "@aminnairi/react-table",
  "version": "4.2.7",
  "description": "React table component for easy data manipulation",
  "keywords": [
    "typescript",
    "react",
    "table",
    "sort",
    "dynamic"
  ]
}
```

## Partie 3 : Dépendances (5 points)

Ajouter un bouton permettant d'ajouter des dépendances Node.js à votre `package.json` généré dynamiquement.

Chaque fois que le bouton est ajouté, ajouter deux champs de formulaire, l'un pour le nom du package, l'autre pour la version du package qui sera renseigné par l'utilisateur.

Vous ajouterez les dépendances au `package.json` généré précédemment dynamiquement.

Pour chaque formulaire de dépendance, ajouter un bouton permettant de supprimer dynamiquement les champs (nom, version) ainsi que sa valeur dans le `package.json` ainsi généré.

```json
{
  "name": "@aminnairi/react-table",
  "version": "4.2.7",
  "description": "React table component for easy data manipulation",
  "keywords": [
    "typescript",
    "react",
    "table",
    "sort",
    "dynamic"
  ],
  "dependencies": {
    "react": "1.2.3",
    "typescript": "4.5.6",
    "rollup": "7.8.9"
  }
}
```
