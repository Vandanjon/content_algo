---
show_clone: false
title: "Somme des entiers"
description: "solution du contexte A"
---

[retour au sommaire](../../#contexte-a)

## Problème

Pour jouer sur une scène, un groupe doit remplir un créneau de **une heure maximum**. Ils donnent donc **une liste** de chacune de leurs **chansons en minutes**, et vous devez vérifier si la durée totale est compatible avec la scène. Sinon, trouvez une **combinaison** de chansons qui peut remplir ce créneau (sans dépasser 60 minutes).

## Code

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
