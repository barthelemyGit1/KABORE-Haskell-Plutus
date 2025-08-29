## HC15T5 : Fonction de division sécurisée avec Maybe

Écrire une fonction de division sécurisée utilisant le type Maybe pour éviter les divisions par zéro.

---

## ✅ Code Haskell

```haskell
module Main where

-- Fonction de division sécurisée
safeDiv :: Int -> Int -> Maybe Int
safeDiv _ 0 = Nothing           -- Cas dangereux : division par zéro
safeDiv x y = Just (x `div` y)  -- Cas normal

-- Programme principal pour tester
main :: IO ()
main = do
    print $ safeDiv 10 2   -- Just 5
    print $ safeDiv 7 0    -- Nothing
    print $ safeDiv 9 3    -- Just 3
```

---

## ⚡ Explications

* **`safeDiv :: Int -> Int -> Maybe Int`**

  * La fonction prend deux `Int`.
  * Retourne `Nothing` si le diviseur est `0`.
  * Sinon retourne `Just résultat`.

* **Exemples** :

  * `safeDiv 10 2` ⟶ `Just 5`
  * `safeDiv 7 0` ⟶ `Nothing`
  * `safeDiv 9 3` ⟶ `Just 3`
