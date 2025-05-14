---
show_clone: false
title: "Somme des entiers"
description: "contexte A"
---

[retour au sommaire](../#le-top-3-des-algos-dentretien)

## Problème

Pour jouer sur une scène, un groupe doit remplir un créneau de **une heure maximum**.  
Ils donnent donc **une liste** de chacune de leurs **chansons en minutes**, et vous devez vérifier si une **combinaison** de chansons peut remplir ce créneau.

## Raisonnement

### Comprendre ce qu'on vous demande

1. Vous traduisez la liste des chansons en un tableau de nombres en minutes (parce que c'est facile de travailler sur un tableau).
2. Vous traduisez le créneau d'une heure en minutes (60 donc).
3. Vous devez additionner les nombres pour trouver une ou des combinaisons de 60 minutes.
4. Si vous trouvez une combinaison, vous devez retourner `true` (le groupe pourra jouer sur scène car il y a au moins une combinaison).  
   Sinon, vous devez retourner `false` (le groupe ne pourra pas jouer sur scène car pas de combinaison).
5. (BONUS) Vous devez retourner la combinaison de chansons qui donne 60 minutes.

### Écrire l'algorithme

1. Algorithme de base

```js
// Étape 1 : lister les variables minimum nécessaires
- tracksList = [10, 20, 30, 40, 50] // Liste des chansons en minutes
- totalTime = 60 // Temps total à remplir
- result = false (ou true) // Résultat de la recherche
```

```js
// Étape 2 : créer une fonction pour trouver la combinaison
function findCombination(tracksList) {
  // on passe la liste des chansons en paramètre
  return result; // on retourne le résultat
}
```

```js
// Étape 3 : créer une boucle pour parcourir la liste des chansons
function findCombination(tracksList) {
  let result = false; // on initialise le résultat à false. Si jamais il n'y a pas de combinaison, c'est ce qu'on retournera

  for (let i = 0; i < tracksList.length; i++) {
    // on parcourt la liste de toutes les chansons

    // si la chanson courante est supérieure à 60, on ne peut pas l'ajouter
    if (tracksList[i] > totalTime) {
      continue; // on passe à la chanson suivante
    }

    let currentSum = tracksList[i]; // on initialise la somme courante avec la chanson courante

    for (let j = i + 1; j < tracksList.length; j++) {
      // on parcourt les chansons suivantes
      currentSum += tracksList[j]; // on ajoute la chanson courante à la somme courante

      if (currentSum === totalTime) {
        // si la somme courante est égale au temps total
        result = true; // on a trouvé une combinaison
        break; // on sort de la boucle
      } else if (currentSum > totalTime) {
        // si la somme courante est supérieure au temps total
        break; // on sort de la boucle
      }
    }

    if (result) {
      // si on a trouvé une combinaison, on sort de la boucle principale
      break;
    }
  }

  return result; // on retourne le résultat final
}
```

2. Algorithme raccourci

```js
// Une fois que notre algo fonctionne, on peut en simplifier l'écriture
function findCombination(tracksList) {
  for (let i = 0; i < tracksList.length; i++) {
    let currentSum = tracksList[i];
    let currentCombination = [tracksList[i]];

    for (let j = i + 1; j < tracksList.length && currentSum <= totalTime; j++) {
      currentSum += tracksList[j];
      currentCombination.push(tracksList[j]);

      if (currentSum === totalTime) return true;
    }
  }
  return false;
}
```

### Tester notre algorithme

On génère des données de test pour vérifier que notre algorithme fonctionne correctement. On part d'une base simple, qui fonctionne, et on la change par étape pour voir si ça fonctionne toujours.

```js
const tracksList = [10, 20, 30, 40, 50];
const totalTime = 60;
const result = findCombination(tracksList);
```

Lien de test : [CODEPEN](https://codepen.io/Beno-t-VANDANJON/pen/YPPBZdY)

### Optimiser notre algorithme

1. Algorithme bonus simple

```js
// Une fois que notre algo de base fonctionne, on peut l'améliorer en donnant une combinaison de chansons possible
function findCombination(tracksList) {
  let result = false;
  let combination = [];

  for (let i = 0; i < tracksList.length; i++) {
    let currentSum = tracksList[i];
    let currentCombination = [tracksList[i]];

    for (let j = i + 1; j < tracksList.length && currentSum <= totalTime; j++) {
      currentSum += tracksList[j];
      currentCombination.push(tracksList[j]);

      if (currentSum === totalTime) {
        result = true;
        combination = currentCombination;
        break;
      }
    }

    if (result) break;
  }

  return { result, combination };
}
```

2. Algorithme bonus avancé

```js
// Une fois que notre algo de base fonctionne, on peut aussi l'améliorer en donnant toutes les combinaisons de chansons qui pourront être jouées
function findAllCombinations(songDurations, slotDuration) {
  let result = false;
  let combinations = [];

  for (let i = 0; i < songDurations.length; i++) {
    for (let j = i + 1; j < songDurations.length; j++) {
      if (songDurations[i] + songDurations[j] <= slotDuration) {
        combinations.push([songDurations[i], songDurations[j]]);
        result = true;
      }

      for (let k = j + 1; k < songDurations.length; k++) {
        if (
          songDurations[i] + songDurations[j] + songDurations[k] <=
          slotDuration
        ) {
          combinations.push([
            songDurations[i],
            songDurations[j],
            songDurations[k],
          ]);
          result = true;
        }
      }
    }
  }

  return { result, combinations };
}
```
