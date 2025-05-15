---
show_clone: false
title: "Somme des entiers"
description: "contexte B"
---

[retour au sommaire](../#le-top-3-des-algos-dentretien)

## Problème

Un food truck partenaire du Hellfest doit préparer des commandes de boissons. Chaque commande est un **tableau** de volumes de boissons en **centilitres**. Vous devez vérifier si une **combinaison** de boissons peut remplir **exactement** un verre de **50 cl**.

## Raisonnement

### Comprendre ce qu'on vous demande

1. Vous traduisez la liste des volumes de boissons en un tableau de nombres en centilitres (parce que c'est facile de travailler sur un tableau).
2. Vous traduisez le volume du verre en centilitres (50 cl = 500 ml).
3. Vous devez additionner les nombres pour trouver une ou des combinaisons qui remplissent exactement 50 cl.
4. Si vous trouvez une combinaison, vous devez retourner `true` (le verre peut être rempli avec cette combinaison).  
   Sinon, vous devez retourner `false` (aucune combinaison ne permet de remplir le verre).
5. (BONUS) Vous devez retourner la combinaison de boissons qui remplit exactement 50 cl.

### Écrire l'algorithme

1. Algorithme de base

```js
// Étape 1 : lister les variables minimum nécessaires
- drinkVolumes = [10, 20, 15, 25, 30] // Liste des volumes en centilitres
- glassVolume = 50 // Volume du verre en centilitres
- result = false (ou true) // Résultat de la recherche
```

```js
// Étape 2 : créer une fonction pour trouver la combinaison
function canFillGlass(drinkVolumes, glassVolume) {
  // on passe la liste des volumes en paramètre
  return result; // on retourne le résultat
}
```

```js
// Étape 3 : créer une boucle pour parcourir la liste des volumes
function canFillGlass(drinkVolumes, glassVolume) {
  let result = false; // on initialise le résultat à false

  for (let i = 0; i < drinkVolumes.length; i++) {
    if (drinkVolumes[i] === glassVolume) {
      result = true;
      break;
    }
  }

  return result; // on retourne le résultat final
}
```

2. Algorithme intermédiaire

```js
// Étape 4 : Ajouter une vérification pour des combinaisons de deux volumes
function canFillGlass(drinkVolumes, glassVolume) {
  for (let i = 0; i < drinkVolumes.length; i++) {
    for (let j = i + 1; j < drinkVolumes.length; j++) {
      if (drinkVolumes[i] + drinkVolumes[j] === glassVolume) {
        return true;
      }
    }
  }
  return false;
}
```

3. Algorithme avancé

```js
// Étape 5 : Ajouter une vérification pour des combinaisons de trois volumes ou plus
function canFillGlass(drinkVolumes, glassVolume) {
  const n = drinkVolumes.length;

  for (let i = 0; i < n; i++) {
    for (let j = i + 1; j < n; j++) {
      if (drinkVolumes[i] + drinkVolumes[j] === glassVolume) {
        return true;
      }

      for (let k = j + 1; k < n; k++) {
        if (
          drinkVolumes[i] + drinkVolumes[j] + drinkVolumes[k] ===
          glassVolume
        ) {
          return true;
        }
      }
    }
  }

  return false;
}
```

### Tester notre algorithme

On génère des données de test pour vérifier que notre algorithme fonctionne correctement. On part d'une base simple, qui fonctionne, et on la change par étape pour voir si ça fonctionne toujours.

```js
const drinkVolumes = [10, 20, 15, 25, 30];
const glassVolume = 50;
const result = canFillGlass(drinkVolumes, glassVolume);
console.log(result); // true
```

Lien de test : [CODEPEN](https://codepen.io/Beno-t-VANDANJON/pen/ByyMewg)

### Optimiser notre algorithme

1. Algorithme bonus simple

```js
// Une fois que notre algo de base fonctionne, on peut l'améliorer en donnant une combinaison de volumes possible
function canFillGlass(drinkVolumes, glassVolume) {
  let result = false;
  let combination = [];

  for (let i = 0; i < drinkVolumes.length; i++) {
    for (let j = i + 1; j < drinkVolumes.length; j++) {
      if (drinkVolumes[i] + drinkVolumes[j] === glassVolume) {
        result = true;
        combination = [drinkVolumes[i], drinkVolumes[j]];
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
// Une fois que notre algo de base fonctionne, on peut aussi l'améliorer en donnant toutes les combinaisons possibles
function findAllCombinations(drinkVolumes, glassVolume) {
  let result = false;
  let combinations = [];

  for (let i = 0; i < drinkVolumes.length; i++) {
    for (let j = i + 1; j < drinkVolumes.length; j++) {
      if (drinkVolumes[i] + drinkVolumes[j] <= glassVolume) {
        combinations.push([drinkVolumes[i], drinkVolumes[j]]);
        result = true;
      }

      for (let k = j + 1; k < drinkVolumes.length; k++) {
        if (
          drinkVolumes[i] + drinkVolumes[j] + drinkVolumes[k] <=
          glassVolume
        ) {
          combinations.push([
            drinkVolumes[i],
            drinkVolumes[j],
            drinkVolumes[k],
          ]);
          result = true;
        }
      }
    }
  }

  return { result, combinations };
}
```
