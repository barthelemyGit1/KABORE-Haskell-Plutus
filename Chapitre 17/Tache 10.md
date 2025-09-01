## HC17T10 : Instance Monoid pour Config

Implémenter l’instance Monoid pour le type Config, où l’élément neutre est une configuration avec le niveau de log minimal, le timeout maximal et le nombre de tentatives minimal.

Nous définissons une instance `Monoid` pour ton type `Config`. Le principe est :

* `mempty` : la valeur neutre.
* `mappend` ou `(<>)` : combiné via l’instance `Semigroup` que tu as déjà définie.

## Code haskell

### Config

```haskell
-- src/Config.hs
module Config where

data Config = Config
  { loggingLevel :: Int
  , timeout      :: Int
  , retries      :: Int
  } deriving (Show, Eq)

-- Semigroup déjà défini : max loggingLevel et retries, min timeout
instance Semigroup Config where
  c1 <> c2 = Config
    { loggingLevel = max (loggingLevel c1) (loggingLevel c2)
    , timeout      = min (timeout c1) (timeout c2)
    , retries      = max (retries c1) (retries c2)
    }

-- Monoid : l'élément neutre
instance Monoid Config where
  mempty = Config
    { loggingLevel = 0       -- niveau de log minimal
    , timeout      = maxBound -- timeout maximal
    , retries      = 0       -- nombre de tentatives minimal
    }
  mappend = (<>)
```
---
### Main
Un exemple de `Main.hs` pour tester ton instance `Monoid` sur `Config` :

```haskell
-- app/Main.hs
module Main where

import Config

main :: IO ()
main = do
    let cfg1 = Config { loggingLevel = 1, timeout = 5000, retries = 2 }
        cfg2 = Config { loggingLevel = 3, timeout = 3000, retries = 1 }
        cfg3 = Config { loggingLevel = 2, timeout = 4000, retries = 5 }

        combinedCfg = mconcat [cfg1, cfg2, cfg3]  -- utilise Monoid et Semigroup

    putStrLn "Configurations individuelles :"
    print cfg1
    print cfg2
    print cfg3

    putStrLn "\nConfiguration combinée (mconcat) :"
    print combinedCfg
```

### Explication

1. **`mempty`**

   * `loggingLevel = 0` → le niveau de log le plus bas.
   * `timeout = maxBound` → valeur maximale pour que toute combinaison prenne la valeur la plus basse (min).
   * `retries = 0` → nombre de tentatives minimal.

2. **`mappend` / `(<>)`**

   * On réutilise l’instance `Semigroup` déjà définie.
   * Ainsi, `mconcat [cfg1, cfg2, cfg3]` fonctionne automatiquement.

3. `cfg1`, `cfg2`, `cfg3` → trois configurations différentes.
4. `combinedCfg = mconcat [cfg1, cfg2, cfg3]` → combine toutes les configurations en utilisant l’instance `Monoid` que tu as définie.

   * `loggingLevel` prendra le maximum.
   * `timeout` prendra le minimum.
   * `retries` prendra le maximum.
5. `print` affiche les configurations individuelles puis la configuration combinée.
