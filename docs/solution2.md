🎯 Objectif
Afficher le prix d’un produit lorsqu’on clique dessus, en le recherchant dans une grande liste d’objets.

✅ Décomposer le problème :
Avoir une liste de produits (avec un id, nom, prix).

Avoir un bouton ou une action associée à chaque produit.

Quand on clique, récupérer l’id du produit.

Parcourir la liste jusqu’à trouver le bon objet (recherche linéaire).

Afficher le prix à l’écran.

```
ProductsList = tableau d’objets (id, name, price)

fonction FindOneProductPrice(ProductId)
  pour chaque produit dans ProductsList
    si product.id == ProductId
      retourner product.price
```

<details markdown="1">
<summary>
Exemple 2 - Articles Hellfest
</summary>
```js
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Produits Hellfest</title>
  <style>
    body { font-family: sans-serif; padding: 2rem; background: #eee; }
    .product { padding: 1rem; background: white; margin: 0.5rem 0; border-radius: 6px; cursor: pointer; }
    .price { margin-top: 1rem; font-weight: bold; font-size: 1.2rem; }
  </style>
</head>
<body>
  <h1>Hellfest Merchandising</h1>

  <div id="products"></div>
  <div class="price" id="priceDisplay">Cliquez sur un produit</div>

  <script>
    const products = [
      { id: 1, name: "T-shirt Hellfest", price: 25 },
      { id: 2, name: "Vinyle édition limitée", price: 40 },
      { id: 3, name: "Casquette collector", price: 20 }
    ];

    const container = document.getElementById('products');
    const priceDisplay = document.getElementById('priceDisplay');

    function findPrice(productId) {
      const product = products.find(p => p.id === productId);
      return product ? product.price : "Produit introuvable";
    }

    products.forEach(p => {
      const div = document.createElement('div');
      div.className = 'product';
      div.textContent = p.name;
      div.addEventListener('click', () => {
        const price = findPrice(p.id);
        priceDisplay.textContent = `Prix : ${price} €`;
      });
      container.appendChild(div);
    });
  </script>
</body>
</html>
```
</details>