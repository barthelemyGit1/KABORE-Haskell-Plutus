## HC3T9 - Tâche avancée 9 : Trouver le maximum de trois nombres avec let

Définir maxOfThree :: Int -> Int -> Int -> Int.

Utiliser let pour stocker les valeurs intermédiaires maximales.

Retourner le maximum des trois nombres.

Tester avec maxOfThree 10 20 15 et maxOfThree 5 25 10.

---

## ✅ Code Haskell

```haskell
-- Fonction maxOfThree
maxOfThree :: Int -> Int -> Int -> Int
maxOfThree a b c =
    let maxAB = max a b      -- maximum entre a et b
        maxABC = max maxAB c -- maximum entre (a,b) et c
    in maxABC

-- Fonction principale pour tester
main :: IO ()
main = do
    print (maxOfThree 10 20 15) -- 20
    print (maxOfThree 5 25 10)  -- 25
```

---

## 🧠 Explication

1. **Signature**

   ```haskell
   maxOfThree :: Int -> Int -> Int -> Int
   ```

   La fonction prend **3 entiers** et retourne un entier : le maximum.

2. **Utilisation de `let`**

   ```haskell
   let maxAB = max a b
       maxABC = max maxAB c
   ```

   * `maxAB` stocke le maximum entre `a` et `b`.
   * `maxABC` compare ce maximum avec `c`.

3. **Retour du résultat**

   ```haskell
   in maxABC
   ```

   La valeur finale retournée est `maxABC`.

4. **Tests**

   * `maxOfThree 10 20 15` → 20 ✅
   * `maxOfThree 5 25 10` → 25 ✅

---
