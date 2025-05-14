[retour au sommaire](../#le-top-3-des-algos-dentretien)  

Dans le chat du site, on veut repérer certains mots interdits et les remplacer par [censuré]. Simple détection de mots exacts dans une phrase.

```js
const phrase = "Ce concert est nul";
const motsInterdits = ["nul", "pourri"];

function filtrer(texte) {
  return texte
    .split(' ')
    .map(mot => motsInterdits.includes(mot) ? "[censuré]" : mot)
    .join(' ');
}

console.log(filtrer(phrase)); // Ce concert est [censuré]
```