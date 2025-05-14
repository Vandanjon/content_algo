[retour au sommaire](../#le-top-3-des-algos-dentretien)  

Problème :
Un magasin de vêtements doit vérifier si une combinaison de tailles de vêtements peut remplir exactement une boîte de 100 cm de longueur pour l'expédition.

Exemple :

```js
function canFillBox(clothingSizes, boxSize) {
    const n = clothingSizes.length;
    for (let i = 0; i < (1 << n); i++) {
        let sum = 0;
        for (let j = 0; j < n; j++) {
            if (i & (1 << j)) {
                sum += clothingSizes[j];
            }
        }
        if (sum === boxSize) {
            return true;
        }
    }
    return false;
}

const clothingSizes = [20, 30, 15, 25, 10];
const boxSize = 100;
console.log(canFillBox(clothingSizes, boxSize)); // true
```