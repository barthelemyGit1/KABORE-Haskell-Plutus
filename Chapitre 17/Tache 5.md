## HC17T5 : Fonction combineLists

Implémenter une fonction combineLists qui utilise l’instance Semigroup pour concaténer deux listes d’entiers.

---

## ✅ Code Haskell

```haskell
module Main where

-- Fonction qui utilise Semigroup pour concaténer deux listes
combineLists :: [Int] -> [Int] -> [Int]
combineLists xs ys = xs <> ys   -- (<>) est l’opérateur de Semigroup

main :: IO ()
main = do
    let list1 = [1, 2, 3]
        list2 = [4, 5, 6]

    putStrLn $ "Liste 1: " ++ show list1
    putStrLn $ "Liste 2: " ++ show list2
    putStrLn $ "Combinaison: " ++ show (combineLists list1 list2)
```

---

## 📝 Explication

1. **Listes et Semigroup**
   En Haskell, les listes `[a]` ont déjà une instance de `Semigroup` et de `Monoid`.

   * `(<>)` = concaténation de listes.
   * `mempty` = `[]` (la liste vide).

2. **Fonction `combineLists`**
   Elle prend deux listes d’entiers `[Int]` et les combine avec `(<>)`.

   Exemple :

   ```haskell
   combineLists [1,2,3] [4,5,6] == [1,2,3,4,5,6]
   ```

3. **Dans `main`**
   On teste avec `[1,2,3]` et `[4,5,6]`.
