## HC16T6: n-ième nombre de Fibonacci

Implémenter une fonction qui retourne le n-ième nombre de Fibonacci.

---

## ✅ Code Haskell

```haskell
module Main where

-- Fonction récursive qui calcule le n-ième nombre de Fibonacci
fibonacci :: Int -> Int
fibonacci 0 = 0
fibonacci 1 = 1
fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)

main :: IO ()
main = do
    let n = 10
    putStrLn $ "Le " ++ show n ++ "-ième nombre de Fibonacci est : " ++ show (fibonacci n)
```

---

## 📝 Explication

1. **Définition de la suite de Fibonacci**

   * La suite commence par `0, 1`.
   * Chaque nombre suivant est la somme des deux précédents :

     $$
     F(n) = F(n-1) + F(n-2)
     $$

2. **Cas de base**

   ```haskell
   fibonacci 0 = 0
   fibonacci 1 = 1
   ```

   * On définit directement les deux premiers termes.

3. **Cas récursif**

   ```haskell
   fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)
   ```

   * On calcule le résultat en appelant récursivement la fonction.

4. **Exemple d’exécution**

   ```
   Le 10-ième nombre de Fibonacci est : 55
   ```
