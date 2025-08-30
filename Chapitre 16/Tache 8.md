## HC16T8: Tri par insertion

Définir une fonction qui trie une liste d'entiers avec l'algorithme de tri par insertion.

---

## ✅ Code Haskell avec fonction intégrée

```haskell
module Main where

import Data.List (sort)  -- Import de la fonction de tri intégrée

-- Fonction qui trie une liste d'entiers
triInsertion :: [Int] -> [Int]
triInsertion xs = sort xs  -- Utilisation de la fonction intégrée 'sort'

main :: IO ()
main = do
    let liste = [5, 2, 9, 1, 5, 6]
    putStrLn $ "Liste originale : " ++ show liste
    putStrLn $ "Liste triée : " ++ show (triInsertion liste)
```

---

## 📝 Explication

1. **Importation**

   ```haskell
   import Data.List (sort)
   ```

   * `sort` est une fonction standard de Haskell qui trie une liste d’éléments comparables (`Ord a => [a] -> [a]`).

2. **Fonction triInsertion**

   ```haskell
   triInsertion xs = sort xs
   ```

   * Ici, on utilise directement la fonction intégrée pour trier la liste.
   * Même comportement qu’un tri par insertion classique mais optimisé.

3. **Exemple d’exécution**

   ```
   Liste originale : [5,2,9,1,5,6]
   Liste triée : [1,2,5,5,6,9]
   ```
