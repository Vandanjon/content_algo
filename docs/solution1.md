
#### décomposer le problème en éléments simples

Heureusement, dans cet exemple, pas besoin d'un algo compliqué. Il suffit de : 

- Prendre le prix unitaire d'un billet (disons qu'ils sont à 15€ pièce).
- Prendre le nombre de billets commandés (on va dire qu'ici, c'est une famille de 4 personnes qui y va).
- Multiplier les deux nombres (donc 15 * 4 = 60€).
- Afficher le résultat sur le site en bas de page (là, on va devoir penser à modifier dynamiquement le HTML. Heureusement, les variables servent à ça.)

Cette réflexion peut ensuite s'écrire dans n'importe quel langage de programmation.
Parfois, on passe par une étape de pseudo-code pour faire la transition entre le langage parlé et le langage codé. Ce n'est pas obligatoire, mais ça aide souvent.


```markdown
# variable du prix d'un billet.
TicketPrice = 15;

# fonction qui calcule le prix à afficher en multipliant
# le prix du billet par une quantité donnée quand on appelle la fonction.
fonction CalculateTotalSum( NumberOfTickets ) {
  calculer TicketPrice * NumberOfTickets;
  renvoyer la valeur du calcul;
}
```

#### valider un algo

Un algo est valide dans un cadre précis. Il sert à résoudre un problème clairement défini. Ici, on a voulu faire varier l'affichage d'un prix exigible aux clients en fonction des billets qu'ils voulaient acheter.

Regarde le code ci-dessous, en JavaScript, il répond à cette demande. Donc, il est valide.


<details markdown="1">
<summary>
Exemple 1 - Billets Hellfest
</summary>

```js

<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Commande de billets - Hellfest</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
      padding: 2rem;
      text-align: center;
    }

    .container {
      background-color: white;
      padding: 2rem;
      border-radius: 8px;
      box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      max-width: 400px;
      margin: auto;
    }

    h1 {
      margin-bottom: 1rem;
    }

    label, input {
      display: block;
      margin: 1rem auto;
      font-size: 1rem;
    }

    input[type="number"] {
      padding: 0.5rem;
      width: 100px;
      text-align: center;
    }

    .total {
      margin-top: 1.5rem;
      font-size: 1.2rem;
      font-weight: bold;
      color: #333;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Commande - Hellfest 🎸</h1>

    <label for="quantity">Nombre de billets :</label>
    <input type="number" id="quantity" min="0" value="0">

    <div class="total">
      Prix total : 0 €
    </div>
  </div>

  <script>
    const unitPrice = 15;
    const quantityInput = document.getElementById('quantity');
    const totalDiv = document.querySelector('.total');

    function updateTotal() {
      const quantity = Number(quantityInput.value);
      const total = unitPrice * quantity;
      totalDiv.textContent = `Prix total : ${total} €`;
    }

    quantityInput.addEventListener('input', updateTotal);
  </script>
</body>
</html>
```

</details>
