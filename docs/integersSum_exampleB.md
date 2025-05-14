[retour au sommaire](./)  

Problème :
Un food truck partenaire du Hellfest doit préparer des commandes de boissons. Chaque commande est un tableau de volumes de boissons en centilitres. Vous devez vérifier si une combinaison de boissons peut remplir exactement un verre de 50 cl.

Exemple :

```js
function canFillGlass(drinkVolumes, glassVolume) {
    const n = drinkVolumes.length;
    for (let i = 0; i < (1 << n); i++) {
        let sum = 0;
        for (let j = 0; j < n; j++) {
            if (i & (1 << j)) {
                sum += drinkVolumes[j];
            }
        }
        if (sum === glassVolume) {
            return true;
        }
    }
    return false;
}

const drinkVolumes = [10, 20, 15, 25, 30];
const glassVolume = 50;
console.log(canFillGlass(drinkVolumes, glassVolume)); // true
```