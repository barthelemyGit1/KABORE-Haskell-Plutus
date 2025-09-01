## HC17T7 : Fonction multiplyProducts

Implémenter une fonction multiplyProducts qui prend une liste de valeurs Product et retourne le résultat combiné avec mconcat.

---

## ✅ Code Haskell

```haskell
module Main where

-- Nouveau type Product
newtype Product = Product Int
  deriving (Show, Eq)

-- Instance Semigroup : multiplication
instance Semigroup Product where
    (Product x) <> (Product y) = Product (x * y)

-- Instance Monoid : 1 est l’élément neutre
instance Monoid Product where
    mempty = Product 1

-- Fonction qui multiplie une liste de Product
multiplyProducts :: [Product] -> Product
multiplyProducts = mconcat

-- Programme principal
main :: IO ()
main = do
    let values1 = [Product 2, Product 3, Product 4]   -- 2*3*4 = 24
        values2 = [Product 5, Product 0, Product 7]   -- 5*0*7 = 0

    putStrLn $ "Multiplication de " ++ show values1 ++ " = " ++ show (multiplyProducts values1)
    putStrLn $ "Multiplication de " ++ show values2 ++ " = " ++ show (multiplyProducts values2)
```

---

## 📝 Explication

1. **Type `Product`**
   On définit un `newtype` pour encapsuler un `Int`.

2. **Instance `Semigroup`**
   L’opération `(<>)` correspond à la multiplication.

3. **Instance `Monoid`**
   L’élément neutre est `1` (car `x * 1 = x`).

4. **Fonction `multiplyProducts`**
   `mconcat` applique `(<>)` (donc la multiplication) sur toute une liste de `Product`.
