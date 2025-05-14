[retour au sommaire](../#le-top-3-des-algos-dentretien)  

Lors de l'inscription, on génère un mot de passe temporaire mais on veut afficher un aperçu masqué, en remplaçant chaque lettre par *, sauf la première.

```js
const motDePasse = "metal2025";

function masquer(mot) {
  return mot[0] + "*".repeat(mot.length - 1);
}

console.log(masquer(motDePasse)); // m********
```