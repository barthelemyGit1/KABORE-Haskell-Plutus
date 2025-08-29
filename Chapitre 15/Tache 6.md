## HC15T6 : Parsing d’entrée utilisateur avec readMaybe

Utiliser readMaybe pour parser les entrées utilisateur de façon sûre et éviter les erreurs d’exécution.

---

## ✅ Code Haskell

```haskell
module Main where

import Text.Read (readMaybe)

main :: IO ()
main = do
    putStrLn "Entrez un nombre entier :"
    input <- getLine
    case readMaybe input :: Maybe Int of
        Just n  -> putStrLn $ "Vous avez entré : " ++ show n
        Nothing -> putStrLn "Erreur : entrée invalide (ce n’est pas un entier)."
```

---

## ⚡ Explications

* **`readMaybe`** vient de `Text.Read`.

  * Il tente de parser une `String` vers un type donné (ici `Int`).
  * Retourne `Just valeur` si ça marche.
  * Retourne `Nothing` si l’entrée est invalide (par ex : `"abc"` ou `"12x"`).

* **Exemples d’exécution** :

  ```
  Entrez un nombre entier :
  42
  Vous avez entré : 42
  ```

  ```
  Entrez un nombre entier :
  hello
  Erreur : entrée invalide (ce n’est pas un entier).
  ```
