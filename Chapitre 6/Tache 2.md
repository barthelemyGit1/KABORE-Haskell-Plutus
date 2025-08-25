## HC6T2 : Suite de Fibonacci (récursif)

Implémente une fonction récursive qui calcule le nième nombre de la suite de Fibonacci.

---

### Code Haskell

```haskell
-- Fonction Fibonacci récursive
fibonacci :: Integer -> Integer
fibonacci 0 = 0           -- Cas de base : F(0) = 0
fibonacci 1 = 1           -- Cas de base : F(1) = 1
fibonacci n = fibonacci (n - 1) + fibonacci (n - 2) -- Cas récursif

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ fibonacci 0   -- 0
    print $ fibonacci 1   -- 1
    print $ fibonacci 5   -- 5
    print $ fibonacci 10  -- 55
```

---

### Explications

1. **Cas de base**

   ```haskell
   fibonacci 0 = 0
   fibonacci 1 = 1
   ```

   * La récursion doit avoir **des valeurs initiales** pour s’arrêter.

2. **Cas récursif**

   ```haskell
   fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)
   ```

   * Le nième terme est la **somme des deux termes précédents**.
   * Exemple : `5 = 3 + 2`.

3. **Pureté**

   * La fonction est **pure**, elle dépend uniquement de son argument.

---

### Exemple de sortie

```
0
1
5
55
```
