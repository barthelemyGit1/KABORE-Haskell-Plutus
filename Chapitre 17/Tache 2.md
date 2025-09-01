## HC17T2 : Nouveaux types Min et Max avec Semigroup

Définir les nouveaux types Min et Max pour tout type Ord et implémenter leurs instances Semigroup respectives avec min et max.

---

## ✅ Code Haskell

```haskell
module Main where

-- Définition du nouveau type Min
newtype Min a = Min a
    deriving (Show, Eq, Ord)

-- Instance de Semigroup pour Min
instance (Ord a) => Semigroup (Min a) where
    (Min x) <> (Min y) = Min (min x y)

-- Définition du nouveau type Max
newtype Max a = Max a
    deriving (Show, Eq, Ord)

-- Instance de Semigroup pour Max
instance (Ord a) => Semigroup (Max a) where
    (Max x) <> (Max y) = Max (max x y)

-- Exemple d’utilisation
main :: IO ()
main = do
    let a = Min 10
        b = Min 3
        c = Max 4
        d = Max 12

    putStrLn $ "Min 10 <> Min 3 = " ++ show (a <> b)
    putStrLn $ "Max 4 <> Max 12 = " ++ show (c <> d)
```

---

## 📝 Explication

1. **`newtype Min a` et `Max a`**
   On crée deux nouveaux types pour encapsuler une valeur d’un type ordonné (`Ord a`).

   ```haskell
   newtype Min a = Min a
   newtype Max a = Max a
   ```

   On dérive `Show`, `Eq`, `Ord` pour simplifier l’affichage et les comparaisons.

2. **Instances de `Semigroup`**

   * Pour `Min`, on définit l’opération `(<>)` comme le minimum :

     ```haskell
     instance (Ord a) => Semigroup (Min a) where
         (Min x) <> (Min y) = Min (min x y)
     ```
   * Pour `Max`, on définit `(<>)` comme le maximum :

     ```haskell
     instance (Ord a) => Semigroup (Max a) where
         (Max x) <> (Max y) = Max (max x y)
     ```

3. **Exécution**

   ```
   Min 10 <> Min 3 = Min 3
   Max 4 <> Max 12 = Max 12
   ```
