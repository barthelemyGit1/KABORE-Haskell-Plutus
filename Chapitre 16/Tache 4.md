## HC16T4: Filtrer les nombres pairs

Implémenter une fonction qui filtre uniquement les nombres pairs d'une liste.

---

## ✅ Code Haskell

```haskell
module Main where

-- Fonction qui filtre les nombres pairs
filtrerPairs :: [Int] -> [Int]
filtrerPairs xs = filter even xs

main :: IO ()
main = do
    let liste = [1..10]
    putStrLn $ "Liste originale : " ++ show liste
    putStrLn $ "Nombres pairs : " ++ show (filtrerPairs liste)
```

---

## 📝 Explication

1. **Signature de type**

   ```haskell
   filtrerPairs :: [Int] -> [Int]
   ```

   * La fonction prend une liste d’entiers `[Int]`.
   * Elle retourne une liste contenant uniquement les nombres pairs.

2. **Utilisation de `filter`**

   ```haskell
   filter even xs
   ```

   * `filter` prend une fonction de test et une liste.
   * `even` est une fonction prédéfinie qui retourne `True` si un nombre est pair.
   * Exemple : `filter even [1..10] = [2,4,6,8,10]`.

3. **Fonction `main`**

   * On définit une liste `[1..10]`.
   * On affiche la liste originale.
   * On affiche uniquement les nombres pairs après filtrage.

---

## ⚡ Exemple d’exécution

```
Liste originale : [1,2,3,4,5,6,7,8,9,10]
Nombres pairs : [2,4,6,8,10]
```
