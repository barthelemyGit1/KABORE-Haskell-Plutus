## HC18T10 : Fonction nestedFmap

Créer une fonction nestedFmap qui applique une fonction à une structure imbriquée avec plusieurs appels à fmap.

---

### Module `NestedFunctor.hs`

```haskell
module NestedFunctor where

-- | Applique une fonction à une structure imbriquée avec deux niveaux de Functor
nestedFmap :: (Functor f, Functor g) => (a -> b) -> f (g a) -> f (g b)
nestedFmap fn x = fmap (fmap fn) x
```

**Explications :**

* `nestedFmap` prend une fonction `fn :: a -> b` et une structure imbriquée `f (g a)` (par exemple `[[Int]]` ou `Maybe [Int]`).
* On applique **deux `fmap`** :

  1. Le premier `fmap` agit sur le **conteneur externe** `f`.
  2. Le second `fmap` agit sur le **conteneur interne** `g`.
* Cela permet de transformer les éléments imbriqués sans avoir à dérouler manuellement chaque niveau.

---

### Exemple d’utilisation dans `Main.hs`

```haskell
module Main where

import NestedFunctor

main :: IO ()
main = do
    let listOfLists = [[1,2,3], [4,5]]
        maybeList    = Just [10,20,30]

        fn = (*2)  -- On double chaque élément

    putStrLn $ "Liste imbriquée avant : " ++ show listOfLists
    putStrLn $ "Liste imbriquée après nestedFmap : " ++ show (nestedFmap fn listOfLists)

    putStrLn $ "Maybe avant : " ++ show maybeList
    putStrLn $ "Maybe après nestedFmap : " ++ show (nestedFmap fn maybeList)
```

**Résultat attendu :**

```
Liste imbriquée avant : [[1,2,3],[4,5]]
Liste imbriquée après nestedFmap : [[2,4,6],[8,10]]
Maybe avant : Just [10,20,30]
Maybe après nestedFmap : Just [20,40,60]
```

Veux‑tu que je fasse ça ?
