## HC16T5: Mettre une chaîne en majuscules

Définir une fonction qui convertit tous les caractères d'une chaîne en majuscules.

---

## ✅ Code Haskell

```haskell
module Main where

import Data.Char (toUpper)  -- on importe toUpper pour transformer les caractères

-- Fonction qui convertit une chaîne en majuscules
enMajuscules :: String -> String
enMajuscules str = map toUpper str

main :: IO ()
main = do
    let texte = "Bonjour Haskell"
    putStrLn $ "Texte original : " ++ texte
    putStrLn $ "Texte en majuscules : " ++ enMajuscules texte
```

---

## 📝 Explication

1. **Importation**

   ```haskell
   import Data.Char (toUpper)
   ```

   * `toUpper` est une fonction de `Data.Char` qui transforme un caractère en majuscule.

2. **Transformation de la chaîne**

   ```haskell
   enMajuscules :: String -> String
   enMajuscules str = map toUpper str
   ```

   * `map` applique `toUpper` à chaque caractère de la chaîne.
   * Exemple : `map toUpper "abc" = "ABC"`.

3. **Exécution**

   * On définit une chaîne `"Bonjour Haskell"`.
   * On affiche l’original et la version en majuscules.

---

## ⚡ Exemple d’exécution

```
Texte original : Bonjour Haskell
Texte en majuscules : BONJOUR HASKELL
```
