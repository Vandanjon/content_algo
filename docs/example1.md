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