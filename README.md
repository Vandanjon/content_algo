# L'ENTRETIEN EN ALGORITHME

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

# LA PRATIQUE

Vous avez été engagé par le [HELLFEST](https://fr.wikipedia.org/wiki/Hellfest) pour un stage. Ils veulent vous faire développer différentes fonctionnalités sur leur site.

D'abord, entretien d'embauche, ils veulent voir si vous avez compris la logique de ce qu'était un algo. C'est en fait à ça que servent les entretiens d'algos : est-ce que la personne en face de moi sait raisonner comme un développeur face à un problème ?

## Le top 3 des algos d'entretien

### Somme des entiers

**Thématique** : On vous donne un tableau de nombres. Il faut trouver lesquels, additionnés, pourront donner une somme précise.

**Contexte A** : Vous devez vérifier si un groupe peut jouer sur une scène spécifique en fonction du temps total de leur setlist. Vous avez un tableau contenant la durée de chaque chanson en minutes, et vous devez vérifier si une combinaison de chansons peut remplir exactement un créneau de 60 minutes.  
[Indice 1](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Loops_and_iteration)  
[Solution ?](docs/integersSum_exampleA.md)

**Contexte B** : Un food truck partenaire du Hellfest doit préparer des commandes de boissons. Chaque commande est un tableau de volumes de boissons en centilitres. Vous devez vérifier si une combinaison de boissons peut remplir exactement un verre de 50 cl.  
[Indice 1](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Loops_and_iteration)  
[Solution ?](docs/integersSum_exampleB.md)

**Contexte C** : Un magasin de vêtements doit vérifier si une combinaison de tailles de vêtements peut remplir exactement une boîte de 100 cm de longueur pour l'expédition.  
[Indice 1](https://developer.mozilla.org/fr/docs/Web/JavaScript/Guide/Loops_and_iteration)  
[Solution ?](docs/integersSum_exampleC.md)

### Décomposer des mots

**Thématique** : On vous donne une phrase quelconque et il faut en changer des éléments automatiquement.

**Contexte A** : Un fan envoie un message au groupe préféré du Hellfest. On veut détecter si ce message (un mot ou une phrase sans espace) est un palindrome, juste pour le fun.  
[Indice 1](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/String/split)  
[Indice 2](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)  
[Solution ?](docs/stringsManipulation_exampleA.md)

**Contexte B** : Lors de l'inscription, on génère un mot de passe temporaire mais on veut afficher un aperçu masqué, en remplaçant chaque lettre par \*, sauf la première.  
[Indice 1](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)  
[Solution ?](docs/stringsManipulation_exampleB.md)

**Contexte C** : Dans le chat du site, on veut repérer certains mots interdits et les remplacer par [censuré]. Simple détection de mots exacts dans une phrase.  
[Indice 1](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/map)  
[Indice 2](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)  
[Solution ?](docs/stringsManipulation_exampleC.md)

### Suite mathématique

**Thématique** : On vous donne un nombre et il faut en déduire un autre nombre selon une formule mathématique.

**Contexte A** : Le Hellfest vend des billets par blocs. Le nombre de places dans chaque bloc suit la suite de Fibonacci : chaque bloc a autant de places que la somme des deux blocs précédents. On vous donne un numéro de bloc n, vous devez calculer combien de places contient ce bloc.  
[Indice 1](https://fr.wikipedia.org/wiki/Suite_de_Fibonacci)  
[Solution ?](docs/numbers_exampleA.md)

**Contexte B** : Le Hellfest récompense ses fans les plus fidèles. Pour chaque achat, vous gagnez deux fois plus de points que lors du précédent. Si le premier achat rapporte 10 points, combien de points allez-vous recevoir pour le nᵉ achat ?  
[Indice 1](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Math/pow)  
[Solution ?](docs/numbers_exampleB.md)

**Contexte C** : Pendant les répétitions, le volume sonore augmente régulièrement de 3 décibels chaque seconde, en partant de 60 dB. On vous demande de calculer le volume après n secondes.  
[Solution ?](docs/numbers_exampleC.md)

# LE CHALLENGE

Vous avez le choix entre deux défis.  
Le challenge guidé vous donne quelques indices mais vous laisse le choix de la solution.  
Le challenge libre va nécessiter de la recherche et de l'imagination.

## [Challenge guidé](CHALLENGE_A.md)

## [Challenge libre](CHALLENGE_B.md)
