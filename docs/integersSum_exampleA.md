Problème :
Vous devez vérifier si un groupe peut jouer sur une scène spécifique en fonction du temps total de leur setlist. Vous avez un tableau contenant la durée de chaque chanson en minutes, et vous devez vérifier si une combinaison de chansons peut remplir exactement un créneau de 60 minutes.

Exemple :

```js
function canFillTimeSlot(songDurations, slotDuration) {
    // Étape 1 : Calculer le nombre total de combinaisons possibles
    // Chaque chanson peut être incluse ou non dans une combinaison. Avec n chansons, il y a 2^n combinaisons possibles.
    const n = songDurations.length;
    
    // Étape 2 : Parcourir toutes les combinaisons possibles
    // On utilise un entier i pour représenter chaque combinaison. Chaque bit de i indique si une chanson est incluse (1) ou non (0).
    for (let i = 0; i < (1 << n); i++) {
        let sum = 0; // Initialiser la somme pour la combinaison actuelle

        // Étape 3 : Vérifier quelles chansons sont incluses dans la combinaison actuelle
        for (let j = 0; j < n; j++) {
            // Si le j-ème bit de i est à 1, inclure la durée de la chanson j dans la somme
            if (i & (1 << j)) {
                sum += songDurations[j];
            }
        }

        // Étape 4 : Vérifier si la somme correspond exactement à la durée du créneau
        if (sum === slotDuration) {
            return true; // Une combinaison valide a été trouvée
        }
    }

    // Étape 5 : Si aucune combinaison valide n'a été trouvée, retourner false
    return false;
}

// Exemple d'utilisation
const songDurations = [10, 15, 20, 25, 30]; // Durées des chansons en minutes
const slotDuration = 60; // Durée du créneau en minutes
console.log(canFillTimeSlot(songDurations, slotDuration)); // true
```

### Explications détaillées :
1. **Comprendre le problème** :
   - On a une liste de durées de chansons.
   - On doit vérifier si une combinaison de ces chansons peut remplir exactement un créneau donné.

2. **Représentation des combinaisons** :
   - Chaque combinaison possible de chansons peut être représentée par un entier binaire.
   - Par exemple, si on a 3 chansons, les combinaisons possibles sont :
     - `000` (aucune chanson), `001` (seulement la 3ᵉ chanson), `010` (seulement la 2ᵉ chanson), etc.

3. **Parcourir toutes les combinaisons** :
   - On utilise une boucle pour générer toutes les combinaisons possibles (de `0` à `2^n - 1`).
   - Pour chaque combinaison, on calcule la somme des durées des chansons incluses.

4. **Vérification de la somme** :
   - Si la somme des durées pour une combinaison correspond exactement à la durée du créneau, on retourne `true`.
   - Sinon, on continue à vérifier les autres combinaisons.

5. **Retourner le résultat** :
   - Si aucune combinaison ne correspond, on retourne `false`.

Ce raisonnement permet de résoudre le problème en explorant toutes les possibilités de manière systématique.

## Code final :
```js
function canFillTimeSlot(songDurations, slotDuration) {
    const n = songDurations.length;
    for (let i = 0; i < (1 << n); i++) {
        let sum = 0;
        for (let j = 0; j < n; j++) {
            if (i & (1 << j)) {
                sum += songDurations[j];
            }
        }
        if (sum === slotDuration) {
            return true;
        }
    }
    return false;
}
```