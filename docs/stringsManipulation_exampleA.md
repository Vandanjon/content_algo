Un fan envoie un message au groupe préféré du Hellfest. On veut détecter si ce message (un mot ou une phrase sans espace) est un palindrome, juste pour le fun.

js
Copier
Modifier
const message = "ressasser";

function estPalindrome(mot) {
  return mot === mot.split('').reverse().join('');
}

console.log(estPalindrome(message)); // true