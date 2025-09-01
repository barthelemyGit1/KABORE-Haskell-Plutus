## HC17T6 : Fonction maxSeverity

Définir une fonction maxSeverity qui combine une liste de valeurs Severity avec mconcat.

---

## ✅ Code Haskell

```haskell
module Main where

-- Définition du type Severity
data Severity = Low | Medium | High | Critical
  deriving (Show, Eq, Ord)

-- Instance Semigroup : le plus élevé l’emporte
instance Semigroup Severity where
    (<>) = max

-- Instance Monoid : Low est la valeur neutre
instance Monoid Severity where
    mempty = Low

-- Fonction qui combine une liste de valeurs Severity avec mconcat
maxSeverity :: [Severity] -> Severity
maxSeverity = mconcat

-- Programme principal
main :: IO ()
main = do
    let severities1 = [Low, Medium, High]
        severities2 = [Medium, Medium, Critical, Low]

    putStrLn $ "Max de " ++ show severities1 ++ " = " ++ show (maxSeverity severities1)
    putStrLn $ "Max de " ++ show severities2 ++ " = " ++ show (maxSeverity severities2)
```

---

## 📝 Explication

1. **Type `Severity`**
   Définit 4 niveaux : `Low < Medium < High < Critical`.

2. **Instance `Semigroup`**
   On choisit `(<>) = max`, donc l’opération conserve la sévérité la plus élevée.

3. **Instance `Monoid`**
   La valeur neutre (`mempty`) est `Low`.

4. **Fonction `maxSeverity`**
   `mconcat` applique `(<>)` sur toute une liste :

   ```haskell
   mconcat [Low, Medium, High] == High
   mconcat [Medium, Critical, Low] == Critical
   ```
