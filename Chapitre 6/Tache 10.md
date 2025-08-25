## HC6T10 : Récupérer les chiffres d’un nombre (récursif)

Implémente une fonction récursive qui prend un nombre et retourne la liste de ses chiffres.

---

### Code Haskell

```haskell
-- Récupérer les chiffres d’un nombre (récursif)
digits :: Int -> [Int]
digits n
    | n < 10    = [n]                                -- Cas de base : un seul chiffre
    | otherwise = digits (n `div` 10) ++ [n `mod` 10] -- Récursif : extraire les chiffres restants

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ digits 0        -- [0]
    print $ digits 7        -- [7]
    print $ digits 12345    -- [1,2,3,4,5]
    print $ digits 987654   -- [9,8,7,6,5,4]
```

---

### Explications

1. **Cas de base**

   ```haskell
   | n < 10 = [n]
   ```

   * Si `n` est inférieur à 10, il ne reste qu’un seul chiffre → on le retourne dans une liste.

2. **Cas récursif**

   ```haskell
   digits (n `div` 10) ++ [n `mod` 10]
   ```

   * `n div 10` enlève le dernier chiffre.
   * `n mod 10` récupère le dernier chiffre.
   * On concatène la liste des chiffres restants avec le dernier.

3. **Exemple**

   ```
   digits 123
   = digits (12) ++ [3]
   = (digits 1 ++ [2]) ++ [3]
   = [1,2,3]
   ```

---

### Exemple de sortie

```
[0]
[7]
[1,2,3,4,5]
[9,8,7,6,5,4]
```

---
