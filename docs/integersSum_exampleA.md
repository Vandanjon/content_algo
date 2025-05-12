Problème :
Vous devez vérifier si un groupe peut jouer sur une scène spécifique en fonction du temps total de leur setlist. Vous avez un tableau contenant la durée de chaque chanson en minutes, et vous devez vérifier si une combinaison de chansons peut remplir exactement un créneau de 60 minutes.

Exemple :

Copier
function canFillTimeSlot(songDurations, slotDuration) {
    const n = songDurations.length;
    for (let i = 0; i < (1 << n); i++) {
        let sum = 0;
        for (let j = 0; j < n; j++) {
            if (i & (1 << j)) {
                sum += songDurations[j];
            }
        }
        if (sum === slotDuration) {
            return true;
        }
    }
    return false;
}

const songDurations = [10, 15, 20, 25, 30];
const slotDuration = 60;
console.log(canFillTimeSlot(songDurations, slotDuration)); // true