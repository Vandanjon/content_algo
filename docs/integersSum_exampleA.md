---
show_clone: false
title: "Somme des entiers"
description: "contexte A"
---

[retour au sommaire](../#le-top-3-des-algos-dentretien)

## Problème

Pour jouer sur une scène, un groupe doit remplir un créneau de **une heure maximum**. Ils donnent donc **une liste** de chacune de leurs **chansons en minutes**, et vous devez vérifier si la durée totale est compatible avec la scène.
BONUS : Sinon, trouvez une **combinaison** de chansons qui peut remplir ce créneau (sans dépasser 60 minutes).

## Raisonnement

### Comprendre ce qu'on vous demande

1. Vous traduisez la liste des chansons en un tableau de nombres en minutes (parce que c'est facile de travailler sur un tableau).
2. Vous traduisez le créneau d'une heure en minutes (car il faut pouvoir travailler sur les mêmes unités).
3. Vous devez additionner les nombres du tableau et vérifier qu'ils ne dépassent pas les 60 minutes.
4. Si ça ne dépasse pas, vous devez retourner `true` (le groupe pourra jouer sur scène).  
   Sinon, vous devez retourner `false` (le groupe ne pourra pas jouer sur scène car leur set est trop long).
5. (BONUS) Vous devez retourner une combinaison de chansons qui soit inférieure à 60 minutes.

### Écrire l'algorithme

On va écrire l'algorithme en javascript, mais vous pouvez l'écrire dans le langage de votre choix.

1. Algorithme de base

```js
// Étape 1 : lister les variables minimum nécessaires
- tracksList = [10, 20, 30, 40, 50] // Liste des chansons en minutes
- maxDuration = 60 // Temps max sur scène
- result = false (ou true) // Résultat de l'algo
```

```js
// Étape 2 : créer une fonction pour trouver la combinaison
function canPlayOnStage(tracksList, maxDuration) {
  // On passe la liste des chansons et le temps max en paramètre
  let result = false; // On initialise le résultat à false parce qu'il vaut mieux penser que le groupe ne peut pas jouer sur scène pour l'organisation des scènes.

  return result; // On retourne le résultat final
}
```

```js
// Étape 3 : créer une boucle pour parcourir la liste des chansons et additionner les durées
// On additionne les durées des chansons
let total = 0; // On initialise la somme à 0

// On additionne chaque durée de chanson
for (let i = 0; i < songDurations.length; i++) {
  total = total + songDurations[i];
}
```

```js
// Étape 4 : vérifier si la somme ne dépasse pas 60 minutes
// On vérifie si la somme ne dépasse pas la durée maximale
if (total <= maxDuration) {
  result = true; // Le groupe peut jouer sur scène
} else {
  result = false; // Le groupe ne peut pas jouer sur scène
}
```

```js
// c'est bon, on colle le tout et on a notre algo
function canPlayOnStage(tracksList, maxDuration) {
  let result = false;
  let total = 0;
  for (let i = 0; i < tracksList.length; i++) {
    total = total + tracksList[i];
  }

  if (total <= maxDuration) {
    result = true;
  } else {
    result = false;
  }

  return result;
}
```

### Tester notre algorithme

Il est très important de tester notre algorithme pour s'assurer qu'il fonctionne correctement. On va le tester avec plusieurs cas de figure.

```js
// Cas 1 : le groupe a une chanson de 60 minutes (il pourra jouer sur scène)
console.log(canPlayOnStage([60], 60)); // true
```

```js
// Cas 2 : le groupe a plusieurs chansons qui, cumulées, restent en dessous ou égal à 60 minutes (il pourra jouer sur scène).
console.log(canPlayOnStage([10, 20, 30], 60)); // true
```

```js
// Cas 3 : le groupe a plusieurs chansons qui, cumulées, dépassent les 60 minutes (il ne pourra pas jouer sur scène).
console.log(canPlayOnStage([10, 20, 30, 40], 60)); // false
```

### Optimiser notre algorithme

Une fois qu'on est sûrs que l'algo fonctionne, on peut l'optimiser pour qu'il soit plus rapide et plus efficace.

1. Algorithme bonus simple

```js
function findCombination(tracksList, maxDuration) {
  let result = [];
  let total = 0;

  for (let i = 0; i < tracksList.length; i++) {
    if (total + tracksList[i] <= maxDuration) {
      result.push(tracksList[i]);
      total += tracksList[i];
    }
  }

  return result;
}
```

2. Algorithme plus court

```js
const findCombination = (tracksList, maxDuration) => {
  let total = 0;
  return tracksList.filter((track) => {
    if (total + track <= maxDuration) {
      total += track;
      return true;
    }
    return false;
  });
};
```
