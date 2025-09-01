## HC18T6 : Fonction applyToMaybe

Implémenter une fonction applyToMaybe qui utilise fmap pour transformer la valeur à l’intérieur d’un Maybe.

Voici un exemple complet pour **HC18T6 : `applyToMaybe`** avec explications et un petit programme `Main` pour tester :

---

### Module `MaybeFunctor.hs`

```haskell
module MaybeFunctor where

-- | applyToMaybe applique une fonction à l'intérieur d'un Maybe
-- Si c'est 'Nothing', on ne fait rien.
-- Si c'est 'Just x', on applique f à x.
applyToMaybe :: (a -> b) -> Maybe a -> Maybe b
applyToMaybe f mx = fmap f mx
```

**Explication :**

* `fmap` est la fonction générique pour tous les **functors**, y compris `Maybe`.
* Pour `Maybe` :

  * `fmap f Nothing = Nothing`
  * `fmap f (Just x) = Just (f x)`
* Cela évite d’avoir à faire un pattern matching manuel et rend le code plus concis.

---

### Programme principal `Main.hs`

```haskell
module Main where

import MaybeFunctor

main :: IO ()
main = do
    let value1 = Just 10
        value2 = Nothing

    -- Appliquer (*2) aux valeurs à l'intérieur de Maybe
    let result1 = applyToMaybe (*2) value1
        result2 = applyToMaybe (*2) value2

    putStrLn $ "applyToMaybe (*2) (Just 10) = " ++ show result1
    putStrLn $ "applyToMaybe (*2) Nothing   = " ++ show result2
```

**Explications :**

* `applyToMaybe (*2) value1` renvoie `Just 20` car `fmap` applique `(*2)` sur 10.
* `applyToMaybe (*2) value2` renvoie `Nothing` car il n’y a pas de valeur à transformer.
* Cela illustre comment utiliser `fmap` pour manipuler des valeurs encapsulées dans un contexte (`Maybe`) sans se soucier de `Nothing`.
