## HC17T1 : Type de données Severity et instance Semigroup

Créer un type de données Severity représentant la sévérité d’une urgence avec quatre niveaux (Low, Medium, High, Critical).

Implémenter une instance Semigroup pour ce type, où le niveau le plus élevé l’emporte sur le niveau inférieur.

---

## ✅ Code Haskell

```haskell
module Main where

-- Définition du type Severity
data Severity = Low | Medium | High | Critical
    deriving (Show, Eq, Ord)

-- Instance de Semigroup
instance Semigroup Severity where
    (<>) = max   -- on prend toujours le plus "élevé" (grâce à Ord)

-- Instance de Monoid (optionnelle, utile pour avoir un neutre)
instance Monoid Severity where
    mempty = Low   -- Low est le niveau neutre

-- Exemple d'utilisation
main :: IO ()
main = do
    let s1 = Low
        s2 = High
        s3 = Critical
        s4 = Medium

    putStrLn $ "Combinaison de " ++ show s1 ++ " et " ++ show s2 ++ " => " ++ show (s1 <> s2)
    putStrLn $ "Combinaison de " ++ show s2 ++ " et " ++ show s3 ++ " => " ++ show (s2 <> s3)
    putStrLn $ "Combinaison de " ++ show s4 ++ " et " ++ show s1 ++ " => " ++ show (s4 <> s1)
```

---

## 📝 Explication

1. **Type `Severity`**
   On définit 4 niveaux d’urgence :

   ```haskell
   data Severity = Low | Medium | High | Critical
   ```

   On dérive `Eq` et `Ord` pour permettre les comparaisons (`<`, `>`, `max`, etc.).

2. **Instance `Semigroup`**

   ```haskell
   instance Semigroup Severity where
       (<>) = max
   ```

   Grâce à `Ord`, `max` permet de garder le niveau le plus élevé.
   Exemple : `Medium <> Critical = Critical`.

3. **Instance `Monoid` (optionnelle)**
   On définit `mempty = Low`, car Low est le neutre (il n’élève pas la sévérité).

4. **Exécution**

   ```
   Combinaison de Low et High => High
   Combinaison de High et Critical => Critical
   Combinaison de Medium et Low => Medium
   ```
