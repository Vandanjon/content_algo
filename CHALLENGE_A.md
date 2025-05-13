[retour au sommaire](./)  


## Challenge guidé
Vous êtes chargé de développer une fonctionnalité pour optimiser l'organisation du Hellfest. Voici le problème :

**Problème** :
Le Hellfest dispose de plusieurs scènes, chacune ayant une capacité sonore maximale (en décibels) et un créneau horaire précis. Vous devez :
1. Vérifier si une combinaison de groupes peut jouer sur une scène donnée sans dépasser la capacité sonore maximale.
2. Calculer si la durée totale des sets des groupes sélectionnés correspond exactement au créneau horaire disponible.

**Données en entrée** :
- Un tableau contenant les niveaux sonores (en décibels) de chaque groupe.
- Un tableau contenant les durées des sets (en minutes) de chaque groupe.
- La capacité sonore maximale de la scène (en décibels).
- La durée totale du créneau horaire (en minutes).

**Données en sortie** :
- Un message indiquant si une combinaison de groupes respecte les contraintes sonores et temporelles.

**Exemple** :
- Groupes : [90 dB, 85 dB, 95 dB], [30 min, 20 min, 40 min]
- Capacité sonore maximale : 180 dB
- Créneau horaire : 60 min

**Résultat attendu** : Une combinaison possible est [90 dB, 85 dB] et [30 min, 20 min].
