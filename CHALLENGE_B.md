## Challenge libre
Vous êtes chargé de développer une fonctionnalité pour optimiser la gestion des files d'attente aux stands du Hellfest. Voici le problème :

**Problème** :
Le Hellfest souhaite organiser les files d'attente de manière optimale en fonction de trois critères :
1. Trier les visiteurs par ordre alphabétique de leur nom.
2. Vérifier si une combinaison de visiteurs peut être servie dans un temps donné (somme des durées de service).
3. Calculer si le niveau sonore généré par les visiteurs dans une file respecte une limite maximale.

**Données en entrée** :
- Un tableau contenant les noms des visiteurs.
- Un tableau contenant les durées de service (en minutes) pour chaque visiteur.
- Un tableau contenant les niveaux sonores (en décibels) générés par chaque visiteur.
- La durée totale disponible pour servir une file (en minutes).
- La capacité sonore maximale autorisée (en décibels).

**Données en sortie** :
- Une liste triée des visiteurs qui respectent les contraintes de temps et de niveau sonore.

**Exemple** :
- Noms : ["Alice", "Bob", "Charlie"]
- Durées : [10 min, 15 min, 20 min]
- Niveaux sonores : [50 dB, 60 dB, 55 dB]
- Durée totale disponible : 30 min
- Capacité sonore maximale : 110 dB

**Résultat attendu** : Une combinaison possible est ["Alice", "Bob"] avec [10 min, 15 min] et [50 dB, 60 dB].