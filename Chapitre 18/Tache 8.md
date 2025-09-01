## HC18T8 : Vérification de la loi d’identité du foncteur

Implémenter la fonction identityLawCheck pour vérifier la loi d’identité du foncteur.

---

## Code haskell

### Module `FunctorLaws.hs`

```haskell
module FunctorLaws where

-- | Vérifie la loi d'identité pour un Functor
-- fmap id == id
identityLawCheck :: (Eq (f a), Functor f) => f a -> Bool
identityLawCheck x = fmap id x == x
```

**Explication :**

* La **loi d'identité** pour les foncteurs stipule que :
  `fmap id == id`
  c’est-à-dire que si on applique `id` (fonction identité) sur tous les éléments d’un foncteur, le foncteur reste inchangé.
* `Eq (f a)` est nécessaire pour comparer le résultat avec l’original.
* `Functor f` indique que la fonction fonctionne pour **tout type ayant une instance Functor**.

---

### Programme principal `Main.hs`

```haskell
module Main where

import FunctorLaws

main :: IO ()
main = do
    let list1 = [1,2,3]
        maybe1 = Just "Hello"

    putStrLn $ "Loi d'identité pour [1,2,3] : " ++ show (identityLawCheck list1)
    putStrLn $ "Loi d'identité pour Just \"Hello\" : " ++ show (identityLawCheck maybe1)
```

**Explications :**

* Pour la liste `[1,2,3]` : `fmap id [1,2,3]` renvoie `[1,2,3]` → `True`
* Pour `Just "Hello"` : `fmap id (Just "Hello")` renvoie `Just "Hello"` → `True`
* Si la fonction retourne `True`, la loi d'identité du foncteur est respectée pour cette instance.
