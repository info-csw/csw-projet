# Enoncé — Projet Web Frontend : Histoire interactive (HTML, CSS, JS moderne)

## 🎯 Objectif du projet ##
Le but de ce projet est de concevoir et développer une histoire interactive inspirée du concept « Histoire dont vous êtes le héros ».  
L’utilisateur progresse dans une narration en fonction de ses choix, qui influencent la suite du récit et l’état du personnage.  
Ce projet vous permettra de mettre en pratique vos compétences en **HTML**, **CSS** et **JavaScript moderne**, avec un accent particulier sur :
- la **structuration claire du projet** (modules, organisation des fichiers, code lisible),
- la **persistance de l’information** (**localStorage et sessionStorage**),
- le respect des **bonnes pratiques de développement** (Git, commentaires JSDoc, conventions de code).

## 🎯 Objectifs d’apprentissage ##

À l’issue du projet, vous serez capable de :
- Structurer une **application web single‑page** (SPA légère) en **HTML5**, **CSS moderne** (Flexbox/Grid) et **JavaScript moderne** (ES Modules).
- **Interagir avec le DOM** : sélection, création/suppression, mise à jour, gestion d’événements, utilisation de `<template>`.
- Gérer un **état applicatif côté client**, avec **persistance** via `localStorage` et `sessionStorage`.
- **Documenter** votre code avec **JSDoc** et respecter des **conventions de nommage**, d’indentation et de modularisation.
- Travailler avec **Git** (commits réguliers et messages descriptifs).
- D'expliquer/justifier tout votre code. 

---

## 🔧 Spécifications techniques

### Structure de l’histoire
- L’histoire doit comporter au minimum **10 étapes** (“nœuds narratifs”), chacune proposant un ou plusieurs choix.
- Ces choix doivent mener vers de nouvelles étapes ou vers une fin possible de l’histoire.
- L’histoire doit proposer **au moins 3 fins** différentes.
- ⚠️ **Une seule page HTML** principale : l’histoire est gérée dynamiquement via JavaScript (pas une page HTML par chapitre).

### Navigation et interactivité
- Les choix peuvent être proposés sous forme de **boutons cliquables**, de **zones interactives sur des images**, ou d’autres mécanismes ergonomiques.
- Les transitions entre les étapes doivent être **fluides** et **claires** pour l’utilisateur.

### Formulaire initial
- Avant de démarrer l’histoire, l’utilisateur complète un **formulaire de base** (ex. nom, âge, préférences, …).
- **Point essentiel : le formulaire identifie le joueur par un _nom unique_** (dans le navigateur courant).
  - Ce **nom unique** est **stocké en `sessionStorage`** : il indique *qui joue dans cet onglet*.
- Les informations saisies doivent être **réutilisées dans l’histoire** (ex. le prénom affiché dans le récit, personnalisation de certains choix).

### Stockage et gestion de l’état
- L’état de l’histoire (progrès, objets collectés, statistiques, etc.) doit être géré via une **structure de données en mémoire**.
- Vous **devez utiliser les deux stockages** :
  - **`sessionStorage`** : *qui joue et état de la session courante*
    - `session:player` → **nom unique du joueur** (issu du formulaire).
    - `session:runState` → **état courant** de la partie dans **cet onglet** (nœud, flags, inventaire, etc.).
  - **`localStorage`** : *états complets et persistants par joueur* (pour pouvoir **reprendre plus tard**, même après fermeture du navigateur)
    - `players:index` → liste des **noms de joueurs** connus sur ce navigateur.
    - `player:<Nom>:state` → **état complet** de la partie pour ce joueur (checkpoint).
- **Flux recommandé** :
  1. Au formulaire, l’utilisateur saisit son **nom unique** → enregistrer `session:player`.
  2. Si ce nom existe déjà en local, proposer **Reprendre** (charger `player:<Nom>:state` en `session:runState`) ou **Nouvelle partie** (réinitialiser son état).
  3. Pendant le jeu, lire/écrire surtout **`session:runState`** ; aux moments clés (**checkpoint**), **sauvegarder en `localStorage`** dans `player:<Nom>:state`.
- **Attendus fonctionnels** :
  - Permettre de **reprendre la progression** après fermeture du navigateur (depuis `localStorage`).
  - Tant que l’onglet reste ouvert, la session continue avec le joueur identifié (`sessionStorage`).
  - Fournir un moyen de **réinitialiser la session** (effacer `session:*`) et de **réinitialiser la progression du joueur courant** (effacer ses clés `player:<Nom>:*` en local).

### Aspect visuel
- L’interface doit être **claire** et **agréable** : un effort en **CSS moderne** (Flexbox/Grid, lisibilité, responsive simple) est attendu.
- L’accent est mis sur la **cohérence visuelle** et la **lisibilité**, pas sur un design avancé.

### Technologies
- **HTML5** : structure sémantique claire (balises adaptées).
- **CSS** : mise en page et styles modernes (Flexbox, Grid).
- **JavaScript (ES Modules)** : logique, interactivité et gestion de l’état.

---

## 📌 Contraintes non techniques

### Documentation et commentaires
- Utilisez des **commentaires clairs et utiles** dans le code.
- Documentez vos fonctions en **JSDoc** : description, paramètres et valeur de retour.

### Méthodologie de travail
- Effectuez des **commits réguliers** dans Git pour documenter l’avancement.
- Chaque commit doit être accompagné d’un **message clair et descriptif**.

### Lisibilité et qualité du code
- Utilisez des **noms explicites** pour vos variables et fonctions.
- Suivez une **convention de nommage cohérente** (**camelCase** recommandé).
- Respectez une **indentation** et des **espacements** constants.

### Modularité
- Organisez votre JavaScript en **modules séparés** dans un dossier `/js/modules/`.
- Évitez le code JavaScript directement dans le **HTML**.
- Chaque fonction doit avoir un **rôle unique** et **clair**.

> *Rappel pédagogique simple :* **si l’information doit survivre au navigateur** → `localStorage`. **Si elle ne sert qu’à l’onglet en cours** → `sessionStorage`.

---

## ✅ Validation de l’idée du projet ##

Avant de commencer, vous devez soumettre une proposition de projet à votre enseignant pour validation. Il convient d'avertir votre enseignant de la mise à disposition de votre proposition.

Cette proposition, au format Markdown (readme.md dans le répertoire dist/), doit contenir :

- Un résumé de l’histoire que vous souhaitez développer.
- Une explication de la manière dont vous allez utiliser le formulaire initial pour personnaliser l’expérience.
