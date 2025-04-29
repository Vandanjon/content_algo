# Résoudre tous les algos

## Déjà, qu'est-ce que c'est un algo ?


Un **algorithme** est une suite d'instructions claires et précises permettant de résoudre un problème ou d'accomplir une tâche. Il sert de plan pour guider un programme informatique. Sans algorithmes, on en serait resté au web 1.0, des sites statiques qui ne font que présenter au lieu d'intéragir avec les utilisateurs.


### un algorithme doit finir

### chaque étape doit avoir un et un seul but

### pour une même entrée, une même sortie

### un algorithme doit être le plus efficace possible


## Les algos simples les plus récurrents

### liste des algos et définition

### mise en situation 1

### mise en situation 2

## challenge sur une autre page. 3 choix possibles




#### Mise en situation

Le [Hellfest](https://fr.wikipedia.org/wiki/Hellfest) démarre bientôt, et il faut d'urgence monter un site de vente de billets en ligne. Vous vous occupez de la partie qui affiche le prix à payer en fonction du nombre de billets commandés. La partie HTML/CSS en soit, c'est assez facile.

Mais comment faire pour que le prix affiché en bas de page varie en fonction du nombre de billets ?

#### Les étapes de la réflexion

Ici, on a un gros indice pour savoir qu'il faut penser "algo" => le mot-clé **en fonction**. Quand je dois réfléchir à plusieurs possibilités, quand je dois conditionner des informations à d'autres informations, alors on doit écrire un algo.
{: .alert-info }

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
prixDuBillet = 15;

# fonction qui calcule le prix à afficher en multipliant
# le prix du billet par une quantité donnée quand on appelle la fonction.
fonction calculDuTotal( quantitéDeBilletsVoulus ) {
  calculer prixDuBillet * quantitéDeBilletsVoulus;
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


Mais si demain, on doit également pouvoir avoir des réductions à partir d'un certain nombre de billets achetés ? il faudra changer la formule mathématique. Ou si le prix des billets change tous les 5000 billets achetés ? il faudra également changer notre algo. Etc, etc...

Donc, quand on me demande d'écrire un algo, il faut qu'il réponde au mieux à la problématique donnée, mais il ne faut pas non plus lui en demander plus que ce qu'il doit faire.

Ici, mon algo pourrait vérifier qu'on n'achète pas tous les billets d'un coup pour les revendre après 10 fois plus cher. Ce serait bien, mais ce n'était pas ce qu'on lui demandait.