## HC5T10 : Combiner les fonctions d’ordre supérieur

Combiner filter, map et any pour créer une fonction qui vérifie si une valeur au carré dans une liste est supérieure à 50.

---

### Code Haskell

```haskell
-- Fonction qui vérifie si un carré dans la liste est > 50
hasSquareGreaterThan50 :: [Int] -> Bool
hasSquareGreaterThan50 xs = any (>50) (map (^2) xs)

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ hasSquareGreaterThan50 [5,6,7]    -- True (7^2 = 49 < 50? attention)
    print $ hasSquareGreaterThan50 [1,2,3,4,5] -- False
    print $ hasSquareGreaterThan50 [8,1,2]    -- True (8^2 = 64 > 50)
```

---

### Explications

1. **`map (^2) xs`**

   * Élève **chaque élément** de la liste au carré.
   * Exemple : `[1,2,3]` → `[1,4,9]`.

2. **`any (>50)`**

   * Vérifie si **au moins un élément** satisfait la condition `>50`.
   * Retourne `True` si c’est le cas, sinon `False`.

3. **Combinaison**

   * `map (^2) xs` → `[éléments au carré]`
   * `any (>50) ...` → vérifie la condition sur la nouvelle liste.

---

### Exemple de sortie

```
False
False
True
```
