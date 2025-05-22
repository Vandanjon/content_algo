---
show_clone: false
title: "Somme des entiers"
description: "contexte A"
---

[retour au sommaire](../../#contexte-a)

## Problème

Pour jouer sur une scène, un groupe doit remplir un créneau de **une heure maximum**. Ils donnent donc **une liste** de chacune de leurs **chansons en minutes**, et vous devez vérifier si la durée totale est compatible avec la scène. Sinon, trouvez une **combinaison** de chansons qui peut remplir ce créneau (sans dépasser 60 minutes).

## Raisonnement

### Comprendre ce qu'on vous demande

1. Vous traduisez la liste des chansons en un tableau de nombres en minutes (parce que c'est facile de travailler sur un tableau).
2. Vous traduisez le créneau d'une heure en minutes (60 minutes donc pour une heure).
3. Vous devez additionner les nombres du tableau pour trouver au moins une combinaison qui ne dépasse pas 60 minutes.
4. Si vous trouvez une combinaison, vous devez retourner `true` (le groupe pourra jouer sur scène car il y a au moins une combinaison).  
   Sinon, vous devez retourner `false` (le groupe ne pourra pas jouer sur scène car pas de combinaison).

### Écrire l'algorithme

On va écrire l'algorithme en javascript, mais vous pouvez l'écrire dans le langage de votre choix.

**Étape 1** : lister les variables minimum nécessaires.

```js
- tracksList = [10, 20, 30, 40, 50] // Liste des chansons en minutes
- maxDuration = 60 // Temps max sur scène
- result = false (ou true) // Résultat de l'algo
```

**Étape 2** : créer une fonction qui prend nos variables en entrée et renvoie la sortie qu'on attend.

```js
function canPlayOnStage(tracksList, maxDuration) {
  // On passe la liste des chansons et le temps max en paramètre
  let result = false; // On initialise le résultat à false parce qu'il vaut mieux penser que le groupe ne peut pas jouer sur scène pour l'organisation des scènes.

  return result; // On retourne le résultat final
}
```

**Étape 3** : créer une boucle pour parcourir la liste des chansons et additionner les durées.

```js
let total = 0; // On initialise la somme à 0

// On parcourt le tableau et on additionne chaque durée de chanson
for (let i = 0; i < tracksList.length; i++) {
  total = total + tracksList[i];
}
```

**Étape 4** : vérifier si la somme ne dépasse pas 60 minutes et renvoyer le bon résultat.

```js
if (total <= maxDuration) {
  result = true; // Le groupe peut jouer sur scène
} else {
  result = false; // Le groupe ne peut pas jouer sur scène
}
```

**Étape 5** : on colle le tout et on a notre algo.

```js
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
Vous pouvez aller sur une solution pour voir le code. [Ici en JavaScript par exemple](../solutions/contextA/intSum_exA_js.md).
