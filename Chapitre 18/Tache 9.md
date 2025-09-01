## HC18T9 : Vérification de la loi de composition du foncteur

Implémenter la fonction compositionLawCheck pour vérifier la loi de composition du foncteur.

---
## Code haskell

### Module `FunctorLaws.hs` (on peut ajouter à celui de HC18T8)

```haskell
module FunctorLaws where

-- | Loi d'identité pour Functor (déjà vue)
identityLawCheck :: (Eq (f a), Functor f) => f a -> Bool
identityLawCheck x = fmap id x == x

-- | Vérifie la loi de composition pour un Functor
-- fmap (f . g) == fmap f . fmap g
compositionLawCheck :: (Eq (f c), Functor f) => (b -> c) -> (a -> b) -> f a -> Bool
compositionLawCheck f g x = fmap (f . g) x == (fmap f . fmap g) x
```

**Explications :**

* La **loi de composition** stipule que pour tout foncteur `f` et fonctions `g` et `f` :

  ```haskell
  fmap (f . g) == fmap f . fmap g
  ```
* Cela garantit que **composer des fonctions à l’intérieur d’un foncteur est équivalent à appliquer les fonctions séquentiellement**.
* `Eq (f c)` est nécessaire pour comparer les résultats.

---

### Programme principal `Main.hs`

```haskell
module Main where

import FunctorLaws

main :: IO ()
main = do
    let list1 = [1,2,3]
        maybe1 = Just 5

        f = (*2)      -- Fonction f : double la valeur
        g = (+3)      -- Fonction g : ajoute 3

    putStrLn $ "Loi de composition pour [1,2,3] : " ++ show (compositionLawCheck f g list1)
    putStrLn $ "Loi de composition pour Just 5 : " ++ show (compositionLawCheck f g maybe1)
```

**Explications :**

* Pour la liste `[1,2,3]` :
  `fmap (f . g) [1,2,3] == fmap f (fmap g [1,2,3])` → `[8,10,12]` → `True`
* Pour `Just 5` :
  `fmap (f . g) (Just 5) == fmap f (fmap g (Just 5))` → `Just 16` → `True`
* La fonction retourne `True` si la loi de composition est respectée.
