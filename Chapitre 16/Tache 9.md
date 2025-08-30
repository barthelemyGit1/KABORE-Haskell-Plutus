## HC16T9: Supprimer les doublons d'une liste

Implémenter une fonction qui supprime les doublons d'une liste.

Parfait, passons à **HC16T9 : Supprimer les doublons d’une liste**.

---

## ✅ Code Haskell

```haskell
module Main where

import Data.List (nub)  -- Import de la fonction intégrée pour supprimer les doublons

-- Fonction qui supprime les doublons
supprimerDoublons :: Eq a => [a] -> [a]
supprimerDoublons xs = nub xs  -- 'nub' supprime tous les doublons

main :: IO ()
main = do
    let liste = [1,2,3,2,4,5,1,6,3]
    putStrLn $ "Liste originale : " ++ show liste
    putStrLn $ "Liste sans doublons : " ++ show (supprimerDoublons liste)
```

---

## 📝 Explication

1. **Importation**

   ```haskell
   import Data.List (nub)
   ```

   * La fonction `nub` prend une liste et renvoie la même liste sans doublons.
   * Elle compare les éléments avec `==`, donc il faut que les éléments soient comparables (`Eq a`).

2. **Fonction `supprimerDoublons`**

   ```haskell
   supprimerDoublons xs = nub xs
   ```

   * Très simple : elle appelle directement `nub` sur la liste.

3. **Exemple d’exécution**

   ```
   Liste originale : [1,2,3,2,4,5,1,6,3]
   Liste sans doublons : [1,2,3,4,5,6]
   ```
