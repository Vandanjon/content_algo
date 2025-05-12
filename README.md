# Réussir son entretien en algo


# La théorie
## Déjà, qu'est-ce que c'est un algo ?
Un **algorithme** est une suite d'instructions claires et précises permettant de résoudre un problème ou d'accomplir une tâche. Il sert de plan pour guider un programme informatique.  

Sans algorithmes, on en serait resté au web 1.0, des sites statiques qui ne font que présenter au lieu d'intéragir avec les utilisateurs.


## Les caractéristiques d'un algorithme
### Des étapes simples
TOUTE tâche, même la plus complexe, peut être découpée en une **série d'étapes élémentaires**. C'est le même principe que le plus grand dénominateur commun en mathématiques ou un résumé de livre en littérature. (OU : C’est exactement comme lorsqu’on suit une recette de cuisine ou qu’on assemble un meuble : on suit des instructions claires, simples, dans un ordre précis.)

Exemple : Remplir un verre d'eau
```md
1. prendre un verre vide.  
2. Ouvrir une bouteille d'eau.
3. Verser l'eau dans le verre.
```

Donc : un algorithme doit être décomposable en étapes simples, compréhensibles et exécutables une à une, même par un humain sans formation particulière.
{: .alert-info }


### Une suite finie d'étapes
Le but d'un algo est de résoudre un problème donné. Pour ce faire, il doit avoir une fin. On parle de **traitement déterminé** : il commence, fait son travail, et se termine.

Exemple : Remplir des verres d'eau.
```md
1. Compter le nombre de verres.
2. prendre un verre vide.
3. Ouvrir une bouteille d'eau si elle n'est pas déjà ouverte.
4. Verser l'eau dans le verre choisi.
5. Recommencer tant que tous les verres ne sont pas remplis.
```

Donc : un algorithme doit être fini, c'est-à-dire qu'il se termine après un nombre défini d'actions.
{: .alert-info }


### La précision
Un ordinateur applique très vite ce qu'on lui demande, mais il n'est pas vraiment capable de réfléchir. Il est **binaire** : "noir" ou "blanc". Il n'y a pas de **zone "grise"**. Donc, pour éviter qu'il plante dans l'exécution de notre algo, il faut être strict et explicite dans les instructions. Il faut éviter les mots ambigus comme « un peu », « environ », « peut-être », etc...

Exemple : Déterminer si on est malade
```md
1. Si la température est supérieure à 38°C, afficher "Fièvre".
2. Sinon, afficher "Température normale".
```

Donc : un algorithme doit être précis, c'est-à-dire que la machine doit savoir exactement quoi faire à chaque étape, sans interprétation possible.
{: .alert-info }


### Cibler ses conditions d'exécution
Un algorithme prend des données pour effectuer un traitement puis donne un résultat (ou plusieurs). Ainsi, on sait précisément à quel moment dans notre futur programme on peut faire appel à notre algorithme ou non.

Exemple : Déterminer si on est malade (exemple précédent)
```md
Données en entrée : une température de type nombre exprimée en degrés Celsius.

Traitement : comparer à une température de type nombre exprimée en degrés Celsius et de valeur "38".

Données en sortie : un message de type texte et de valeur "fièvre" ou de valeur "température normale". 
```

Donc : un algorithme prend des données précises en entrée et fournit des données précises en sortie.
{: .alert-info }

Attention !
un algo ne doit pas être confondu avec : 
{: .alert-warning }
- **du code pur** (un algo est un schéma de pensée, ce n'est pas du code)
- **un programme** (qui est l'écriture d'un algo dans un langage informatique)
- **un outil intelligent** (un algo peut être gourmand, mal écrit. Il manque la notion d'optimisation que nous n'avons pas abordée)


# La pratique
## Les algos les plus récurrents
### liste des algos utiles pour les développeurs juniors

#### Recherche linéaire
Objectif : Trouver un utilisateur par son nom dans un tableau.

Programme : 
```js
const users = [
  { id: 1, name: 'Alice' },
  { id: 2, name: 'Bob' },
  { id: 3, name: 'Charlie' },
];

const targetName = 'Bob';

const user = users.find(user => user.name === targetName);
console.log(user);
```

Explication : `.find()` parcourt chaque élément et retourne le premier qui correspond à la condition `(user.name === targetName)`. Si rien ne matche, il retourne `undefined`.


#### Tri
Objectif : Trier une liste d’objets par âge croissant.

```js
const people = [
  { name: 'Alice', age: 30 },
  { name: 'Bob', age: 25 },
  { name: 'Charlie', age: 35 },
];

people.sort((a, b) => a.age - b.age);
console.log(people);
```

Attention : Le sort() trie par défaut en ASCII. En donnant une fonction (a, b) => a.age - b.age, on trie numériquement. Si le résultat est négatif, a vient avant b.


#### Manipulation de données (réduction par exemple)
Objectif : Calculer la somme des salaires.

```js
const employees = [
  { name: 'Alice', salary: 3000 },
  { name: 'Bob', salary: 2500 },
  { name: 'Charlie', salary: 4000 },
];

const total = employees.reduce((acc, curr) => acc + curr.salary, 0);
console.log(total);
```

.reduce() passe sur chaque élément et accumule une valeur (ici : somme des salaires). acc est le total courant, curr.salary est le salaire actuel.



# Le challenge





### liste des algos les plus demandés en entretiens

#### Somme de deux
Objectif : Trouver deux nombres qui donnent 9.

```js
const numbers = [2, 7, 11, 15];
const target = 9;

function twoSum(nums, target) {
  const map = new Map();
  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i];
    if (map.has(complement)) {
      return [map.get(complement), i];
    }
    map.set(nums[i], i);
  }
}

console.log(twoSum(numbers, target));
```


#### Palindrome
Objectif : Vérifier si une string est un palindrome.

```js
function isPalindrome(str) {
  const cleaned = str.toLowerCase().replace(/[^a-z0-9]/g, '');
  const reversed = cleaned.split('').reverse().join('');
  return cleaned === reversed;
}

console.log(isPalindrome('A man, a plan, a canal: Panama'));
```

#### Fibonacci
Objectif : Calculer le nᵉ nombre de Fibonacci

```js
// Version récursive (simple mais peu efficace)
function fibRecursive(n) {
  if (n <= 1) return n;
  return fibRecursive(n - 1) + fibRecursive(n - 2);
}

// Version itérative (optimisée)
function fibIterative(n) {
  let a = 0, b = 1;
  for (let i = 0; i < n; i++) {
    [a, b] = [b, a + b];
  }
  return a;
}

console.log(fibIterative(6));
```
Itératif
Utilise des boucles (for, while) pour répéter une action.

Gère les étapes dans la mémoire locale (variables).

Plus performant et économe en ressources.

✅ Préféré en production si possible.


Récursif
Une fonction s'appelle elle-même pour résoudre une version plus simple du problème.

Nécessite une condition d'arrêt (if (n <= 1) return n).

Peut être élégant, mais moins performant (stack overflow si trop profond).

❌ Peu adapté pour des n élevés sans optimisation (memoization / tail-call).


## Mises en situation : LE [HELLFEST](https://fr.wikipedia.org/wiki/Hellfest)

### mise en situation 1

Il faut monter un site de vente de billets en ligne. Vous vous occupez de la partie qui affiche le prix à payer en fonction du nombre de billets commandés. La partie HTML/CSS en soit, c'est assez facile.
Mais comment faire pour que le prix affiché en bas de page varie en fonction du nombre de billets ?

=> voir la solution ici

### mise en situation 2

Vous travaillez sur la billetterie du Hellfest Store qui vend aussi du merchandising (t-shirts, vinyles, posters, etc.). Chaque produit a un id, un nom, et un prix. Lorsqu’un utilisateur clique sur un article, il faut retrouver son prix à partir d’un catalogue de plusieurs centaines de milliers de références.

💡 Algorithme attendu :
Une recherche linéaire dans un tableau d’objets (ex. products.find(p => p.id === clickedId)), car les données ne sont pas triées ni indexées.

=> voir la solution ici

### mise en situation 3

Vous développez une interface de gestion pour les bénévoles du Hellfest. Vous avez une liste d’inscrits avec leur genre déclaré ("H" ou "F"), et devez afficher le nombre de vestiaires à prévoir. Pour cela, on vous demande de trier les bénévoles par genre pour les compter et les répartir.

💡 Algorithme attendu :
Un tri avec Array.prototype.sort() ou une logique de regroupement (via reduce, ou filter) pour séparer les genres et les compter. L’objectif n’est pas juste de trier, mais de faciliter un traitement en aval.

=> voir la solution ici

## LE CHALLENGE

à faire
