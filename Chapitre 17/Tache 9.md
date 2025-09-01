## HC17T9 : Type Config et instance Semigroup

Définir un type Config avec les champs loggingLevel, timeout et retries.

Implémenter une instance Semigroup qui combine les configurations en prenant le maximum pour loggingLevel et retries et le minimum pour timeout.

---

* **loggingLevel** : un `Int` (plus le nombre est élevé, plus le niveau de log est verbeux)
* **timeout** : un `Int` (délai en secondes, plus petit est plus strict)
* **retries** : un `Int` (nombre de tentatives)

Ensuite on définit une **instance de Semigroup** pour expliquer comment combiner deux configurations :

* On garde le **maximum** pour `loggingLevel` et `retries` (on veut la valeur la plus "forte")
* On garde le **minimum** pour `timeout` (on préfère un délai plus court)

---

### ✅ Code Haskell

```haskell
module Config where

-- Définition du type Config
data Config = Config
  { loggingLevel :: Int
  , timeout      :: Int
  , retries      :: Int
  } deriving (Show)

-- Instance Semigroup pour Config
instance Semigroup Config where
  (<>) (Config log1 t1 r1) (Config log2 t2 r2) =
    Config (max log1 log2)  -- prendre le loggingLevel le plus élevé
           (min t1 t2)      -- prendre le timeout le plus petit
           (max r1 r2)      -- prendre le nombre de retries le plus élevé

-- Exemple d'utilisation
example1 :: Config
example1 = Config { loggingLevel = 1, timeout = 30, retries = 2 }

example2 :: Config
example2 = Config { loggingLevel = 3, timeout = 20, retries = 5 }

combined :: Config
combined = example1 <> example2
```

---

### 🔎 Explication

* `example1` : niveau de log = 1, timeout = 30, retries = 2
* `example2` : niveau de log = 3, timeout = 20, retries = 5

En les combinant (`example1 <> example2`) on obtient :

* `loggingLevel = max 1 3 = 3`
* `timeout = min 30 20 = 20`
* `retries = max 2 5 = 5`

👉 Résultat : `Config {loggingLevel = 3, timeout = 20, retries = 5}`
