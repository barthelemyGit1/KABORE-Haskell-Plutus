## HC6T1 : Factorielle (récursif) 

Implémente une fonction récursive qui calcule la factorielle d’un nombre.

---

### Code Haskell

```haskell
-- Fonction factorielle récursive
factorial :: Integer -> Integer
factorial 0 = 1                     -- Cas de base : 0! = 1
factorial n = n * factorial (n - 1) -- Cas récursif

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ factorial 0   -- 1
    print $ factorial 5   -- 120
    print $ factorial 7   -- 5040
```

---

### Explications

1. **Cas de base**

   ```haskell
   factorial 0 = 1
   ```

   * Toute fonction récursive a besoin d’un **cas de base** pour arrêter la récursion.
   * Ici, `0! = 1`.

2. **Cas récursif**

   ```haskell
   factorial n = n * factorial (n - 1)
   ```

   * Multiplie le nombre courant par la factorielle du nombre précédent.
   * Exemples : `5! = 5 * 4 * 3 * 2 * 1`.

3. **Pureté**

   * La fonction est **pure**, elle dépend uniquement de son argument.

---

### Exemple de sortie

```
1
120
5040
```
