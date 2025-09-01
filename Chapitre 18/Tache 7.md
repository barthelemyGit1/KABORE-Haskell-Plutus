## HC18T7 : Fonction fmapTuple

Définir une fonction fmapTuple qui applique une fonction au deuxième élément d’un tuple (a, b) en utilisant l’instance Functor de (,) a.

Voici un exemple complet pour **HC18T7 : `fmapTuple`** avec explication et programme principal pour tester :

---
## Code haskell

### Module `TupleFunctor.hs`

```haskell
module TupleFunctor where

-- | fmapTuple applique une fonction au deuxième élément d'un tuple (a, b)
-- Utilise l'instance Functor pour (,) a
fmapTuple :: (b -> c) -> (a, b) -> (a, c)
fmapTuple f pair = fmap f pair
```

**Explication :**

* Les tuples `(a, b)` ont une instance `Functor` sur le **deuxième élément**.
* `fmap f (x, y)` renvoie `(x, f y)`
* Cela permet d’appliquer une fonction uniquement sur la **valeur associée**, sans toucher à la clé ou au premier élément.

---

### Programme principal `Main.hs`

```haskell
module Main where

import TupleFunctor

main :: IO ()
main = do
    let tuple1 = ("age", 30)
        tuple2 = ("score", 100)

    -- Appliquer (+1) au deuxième élément du tuple
    let result1 = fmapTuple (+1) tuple1
        result2 = fmapTuple (*2) tuple2

    putStrLn $ "fmapTuple (+1) (\"age\", 30)   = " ++ show result1
    putStrLn $ "fmapTuple (*2) (\"score\",100) = " ++ show result2
```

**Explications :**

* `fmapTuple (+1) ("age", 30)` renvoie `("age", 31)`
* `fmapTuple (*2) ("score", 100)` renvoie `("score", 200)`
* La clé (premier élément) reste inchangée, et la fonction ne s’applique qu’au deuxième élément.
