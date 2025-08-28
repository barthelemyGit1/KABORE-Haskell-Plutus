## HC12T5 : Vérification de palindrome

Créer un programme qui définit une fonction isPalindrome pour vérifier si une chaîne est un palindrome. Utiliser la fonction main pour tester cela avec une entrée utilisateur.

---

### Code haskell

```haskell
-- Import nécessaire pour toLower
import Data.Char (toLower)

-- Définition de la fonction isPalindrome
isPalindrome :: String -> Bool
isPalindrome str = cleaned == reverse cleaned
  where
    cleaned = map toLower $ filter (/= ' ') str
    -- on ignore les espaces et on convertit en minuscules pour être insensible à la casse

-- Fonction principale
main :: IO ()
main = do
  let input = "anna" 
  if isPalindrome input
    then putStrLn "C'est un palindrome !"
    else putStrLn "Ce n'est pas un palindrome."
```

---

### Explications :

1. `isPalindrome` :

   * Nettoie la chaîne pour enlever les espaces et convertir en minuscules.
   * Compare la chaîne avec son inverse (`reverse cleaned`).

2. `main` :

   * Demande à l’utilisateur de saisir une chaîne.
   * Appelle `isPalindrome` et affiche le résultat.

---
