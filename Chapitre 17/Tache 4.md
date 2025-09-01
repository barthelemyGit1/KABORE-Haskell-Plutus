## HC17T4 : Instance Monoid pour Sum

Implémenter l’instance Monoid pour le nouveau type Sum, où l’élément neutre est 0.

---

## ✅ Code Haskell

```haskell
module Main where

-- Nouveau type Sum
newtype Sum = Sum { getSum :: Int }
    deriving (Show, Eq)

-- Instance de Semigroup : addition
instance Semigroup Sum where
    (Sum x) <> (Sum y) = Sum (x + y)

-- Instance de Monoid : neutre = 0
instance Monoid Sum where
    mempty = Sum 0
    mappend = (<>)

-- Exemple d’utilisation
main :: IO ()
main = do
    let a = Sum 5
        b = Sum 10
        c = Sum 20

    putStrLn $ "a <> b = " ++ show (a <> b)          -- 15
    putStrLn $ "mempty <> a = " ++ show (mempty <> a) -- 5
    putStrLn $ "mconcat [a, b, c] = " ++ show (mconcat [a, b, c]) -- 35
```

---

## 📝 Explication

1. **`newtype Sum`**
   On définit un type `Sum` qui encapsule un `Int`.

2. **`Semigroup`**
   La combinaison `(Sum x) <> (Sum y)` correspond à leur somme.
   Exemple : `Sum 5 <> Sum 10 = Sum 15`.

3. **`Monoid`**

   * Élément neutre `mempty = Sum 0` (car 0 est neutre pour l’addition).
   * On réutilise `(<>)` comme définition de `mappend`.

4. **Utilité**
   On peut combiner des listes de `Sum` avec `mconcat`, par exemple :
   `mconcat [Sum 5, Sum 10, Sum 20] = Sum 35`.
