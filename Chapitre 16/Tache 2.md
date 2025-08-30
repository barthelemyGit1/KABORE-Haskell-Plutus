## HC16T2: Vérifier si une chaine est un palindrome

Définir une fonction qui vérifie si une chaîne de caractères donnée est un palindrome.

Parfait 👍 reprenons **HC16T2** avec explication détaillée.

---

## ✅ Code Haskell pour tester un palindrome

```haskell
module Main where

-- Fonction qui vérifie si une chaîne est un palindrome
estPalindrome :: String -> Bool
estPalindrome str = str == reverse str

main :: IO ()
main = do
    putStrLn "Entrez une chaîne :"
    input <- getLine
    if estPalindrome input
        then putStrLn "C'est un palindrome !"
        else putStrLn "Ce n'est pas un palindrome."
```

---

## 📝 Explication

1. **`reverse str`**

   * La fonction `reverse` de Haskell prend une liste (ou chaîne de caractères, qui est une liste de `Char`) et retourne son inverse.
   * Exemple : `reverse "kayak"` → `"kayak"`, `reverse "haskell"` → `"lleksah"`.

2. **Comparaison `str == reverse str`**

   * On vérifie si la chaîne d’origine est égale à sa version inversée.
   * Si oui → c’est un palindrome.
   * Si non → ce n’est pas un palindrome.

3. **`main`**

   * Demande une chaîne à l’utilisateur (`getLine`).
   * Vérifie avec `estPalindrome`.
   * Affiche un message adapté.

---

## ⚡ Exemple d’exécution

```
Entrez une chaîne :
radar
C'est un palindrome !

Entrez une chaîne :
haskell
Ce n'est pas un palindrome.
```
