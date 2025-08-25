## HC6T8 : Filtrer les nombres pairs

Implémente une fonction qui filtre tous les nombres pairs d’une liste.

---

### Code Haskell

```haskell
-- Fonction pour filtrer les nombres pairs
filterEvens :: [Int] -> [Int]
filterEvens xs = filter even xs

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ filterEvens [1..10]      -- [2,4,6,8,10]
    print $ filterEvens [11,13,15]  -- []
    print $ filterEvens [2,4,6]     -- [2,4,6]
```

---

### Explications

1. **`filter`**

   ```haskell
   filter even xs
   ```

   * `filter` garde uniquement les éléments qui satisfont une condition.
   * Ici, la condition est `even` (nombre pair).

2. **`even`**

   * Fonction intégrée : `even n` retourne `True` si `n` est pair, sinon `False`.

3. **Type**

   * `[Int] -> [Int]` : prend une liste d’entiers, retourne une liste d’entiers pairs.

---

### Exemple de sortie

```
[2,4,6,8,10]
[]
[2,4,6]
```

---

💡 On pourrait aussi l’écrire en **notation lambda** :

```haskell
filterEvens = filter (\x -> x `mod` 2 == 0)
```
