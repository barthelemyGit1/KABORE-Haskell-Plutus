## HC17T3 : Instance Monoid pour Severity

Implémenter l’instance Monoid pour le type Severity, où la valeur neutre est Low.

---

## ✅ Code Haskell

```haskell
module Main where

-- Définition du type Severity
data Severity = Low | Medium | High | Critical
    deriving (Show, Eq, Ord)

-- Instance de Semigroup (déjà vue avant)
instance Semigroup Severity where
    (<>) = max   -- la sévérité la plus forte l'emporte

-- Instance de Monoid
instance Monoid Severity where
    mempty = Low   -- valeur neutre
    mappend = (<>) -- hérite de Semigroup

-- Exemple d'utilisation
main :: IO ()
main = do
    let a = Medium
        b = High
        c = Critical
        d = Low

    putStrLn $ "Medium <> High = " ++ show (a <> b)
    putStrLn $ "Critical <> Low = " ++ show (c <> d)
    putStrLn $ "mempty <> High = " ++ show (mempty <> b)
    putStrLn $ "mconcat [Low, Medium, High] = " ++ show (mconcat [Low, Medium, High])
```

---

## 📝 Explication

1. **`Semigroup` avec `max`**
   L’opérateur `(<>)` compare deux niveaux de sévérité et garde le plus fort :

   * `Medium <> High = High`
   * `Critical <> Low = Critical`

2. **`Monoid`**

   * La valeur neutre `mempty` est **Low**.
     Cela veut dire que combiner n’importe quelle sévérité avec `Low` laisse l’autre inchangée.
   * On définit `mappend = (<>)` (déjà fourni par `Semigroup`).

3. **Exemple pratique**

   * `mempty <> High = High`
   * `mconcat [Low, Medium, High] = High`
