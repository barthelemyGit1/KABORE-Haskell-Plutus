## HC17T8 : Fonction foldWithSemigroup

Écrire une fonction foldWithSemigroup qui accepte une liste de tout type avec une instance Semigroup et combine tous les éléments avec foldr.

---

## ✅ Code Haskell

```haskell
module Main where

import Data.Semigroup
import System.IO ()

-- Fonction générique qui combine une liste en utilisant Semigroup et foldr
foldWithSemigroup :: Semigroup a => [a] -> a
foldWithSemigroup = foldr1 (<>)

-- Exemple avec des chaînes
exampleStrings :: [String]
exampleStrings = ["Hello", " ", "World", "!"]

-- Exemple avec des listes
exampleLists :: [[Int]]
exampleLists = [[1,2], [3,4], [5]]

main :: IO ()
main = do
    hSetEncoding stdout utf8
    putStrLn $ "Chaînes combinées : " ++ foldWithSemigroup exampleStrings
    putStrLn $ "Listes combinées  : " ++ show (foldWithSemigroup exampleLists)
```

---

## 📝 Explication

1. **`Semigroup a =>`**
   La fonction accepte n’importe quel type `a` qui a une instance de `Semigroup` (`String`, `List`, `Product`, `Sum`, etc.).

2. **`foldr1 (<> )`**

   * `foldr1` applique l’opérateur `(<> )` en partant de la droite.
   * `(<> )` est défini par l’instance `Semigroup` du type.

     * Pour les `String` → concaténation
     * Pour les `[Int]` → concaténation de listes
     * Pour `Product` → multiplication, etc.

3. **Exemples**

   * `"Hello" <> " " <> "World" <> "!"` → `"Hello World!"`
   * `[1,2] <> [3,4] <> [5]` → `[1,2,3,4,5]`
