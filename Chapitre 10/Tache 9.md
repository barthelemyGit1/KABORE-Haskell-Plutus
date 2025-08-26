## HC10T9 : Classe de type MinMax

Implémenter une classe de type MinMax avec les méthodes minValue :: a et maxValue :: a, et fournir des instances pour Int.

--- 

### Code haskell

```haskell
-- Définition de la classe de type MinMax
class MinMax a where
  minValue :: a
  maxValue :: a

-- Instance MinMax pour Int
instance MinMax Int where
  minValue = minBound  -- valeur minimale d'un Int
  maxValue = maxBound  -- valeur maximale d'un Int

-- Exemples d'utilisation
main :: IO ()
main = do
  putStrLn ("Valeur minimale Int : " ++ show minValue)
  putStrLn ("Valeur maximale Int : " ++ show maxValue)
```

---

### 🔎 Explications

* `class MinMax a where ...` : définit une interface avec deux méthodes pour obtenir la valeur minimale et maximale d’un type.
* `instance MinMax Int` :

  * `minValue = minBound` → valeur minimale d’un `Int`.
  * `maxValue = maxBound` → valeur maximale d’un `Int`.
* `minBound` et `maxBound` fonctionnent car `Int` fait partie de la classe `Bounded`.

---

### ✅ Résultat attendu (sur une machine 64 bits)

```
Valeur minimale Int : -9223372036854775808
Valeur maximale Int : 9223372036854775807
```
