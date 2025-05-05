🎯 Objectif
Compter le nombre de bénévoles hommes et femmes pour organiser les vestiaires.

✅ Décomposer le problème :
Avoir une liste de bénévoles avec un champ "genre" ("H" ou "F").

Trier ou filtrer cette liste selon le genre.

Compter le nombre d’éléments dans chaque groupe.

Afficher les résultats.

```
volunteersList = tableau d’objets (name, gender)

fonction CalculatePersonByGender()
  women = bénévoles filtrés où genre == "W"
  men = bénévoles filtrés où genre == "M"
  Afficher les longueurs des deux tableaux
  ```

  <details> <summary>💻 Code complet en HTML/CSS/JS</summary>

  ```js
  <!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Bénévoles Hellfest</title>
  <style>
    body { font-family: sans-serif; padding: 2rem; background: #f0f0f0; }
    button { margin: 1rem 0; padding: 0.5rem 1rem; }
    .result { font-size: 1.1rem; margin-top: 1rem; }
  </style>
</head>
<body>
  <h1>Répartition des bénévoles</h1>
  <button id="countBtn">Calculer les vestiaires à prévoir</button>
  <div class="result" id="output"></div>

  <script>
    const volunteers = [
      { name: "Alice", gender: "F" },
      { name: "Bob", gender: "H" },
      { name: "Claire", gender: "F" },
      { name: "David", gender: "H" },
      { name: "Emma", gender: "F" }
    ];

    document.getElementById('countBtn').addEventListener('click', () => {
      const females = volunteers.filter(v => v.gender === "F");
      const males = volunteers.filter(v => v.gender === "H");

      const output = `
        Vestiaires femmes : ${females.length}<br>
        Vestiaires hommes : ${males.length}
      `;
      document.getElementById('output').innerHTML = output;
    });
  </script>
</body>
</html>
```
</details>