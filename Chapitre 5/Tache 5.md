## HC5T5 : Application partielle

Créer une fonction multiplyByFive qui utilise l’application partielle pour multiplier n’importe quel nombre par 5

---

### Code Haskell

```haskell
-- Fonction qui multiplie un nombre par 5 grâce à l'application partielle
multiplyByFive :: Num a => a -> a
multiplyByFive = (5 *)

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ multiplyByFive 3     -- 15
    print $ multiplyByFive 10    -- 50
    print $ multiplyByFive 0.2   -- 1.0
```

---

### Explications

1. **Application partielle**

   ```haskell
   multiplyByFive = (5 *)
   ```

   * L’opérateur `*` attend **deux arguments** : `( * ) :: Num a => a -> a -> a`.
   * En écrivant `(5 *)`, on fixe le **premier argument à 5**.
   * Il reste une fonction `a -> a` qui multiplie n’importe quel nombre par 5.

2. **Signature de type**

   ```haskell
   Num a => a -> a
   ```

   * La fonction fonctionne pour **tout type numérique** (`Int`, `Integer`, `Float`, `Double`…).

3. **Exemples**

   * `multiplyByFive 3` → `3 * 5 = 15`
   * `multiplyByFive 0.2` → `0.2 * 5 = 1.0`

---
