## HC18T5 : Instance Functor pour Either

Définir une instance Functor pour le type Either, en appliquant fmap uniquement sur le cas Right.

## Code haskell

```haskell
-- src/EitherFunctor.hs
module EitherFunctor where

-- Instance Functor pour Either
instance Functor (Either e) where
    fmap _ (Left x)  = Left x          -- ne change pas le Left
    fmap f (Right y) = Right (f y)     -- applique f uniquement sur Right
```

### Explications

1. **Type constructor** :

   * `Either e` est un type paramétré sur `e` (erreur) et `a` (valeur).
   * La déclaration `Functor (Either e)` signifie que `fmap` va agir sur le type `a` à l’intérieur de `Right`.

2. **Règles du Functor** :

   * `fmap _ (Left x) = Left x` : si c’est un `Left`, la valeur reste inchangée.
   * `fmap f (Right y) = Right (f y)` : si c’est un `Right`, on applique la fonction `f` à la valeur.
  
Pour ce code `Functor` sur `Either`, il n’y a **pas encore de fonction `main`**, car l’implémentation du type et de son instance est seulement une définition de **bibliothèque**.


```haskell
--app/Main.hs
module Main where

import Data.Either (Either(..))

main :: IO ()
main = do
    -- Ici, on précise que l'erreur est une String
    let r1 = fmap (+1) (Right 10 :: Either String Int)
    let r2 = fmap (+1) (Left "Erreur" :: Either String Int)

    putStrLn $ "Right 10 -> " ++ show r1
    putStrLn $ "Left \"Erreur\" -> " ++ show r2
```

### Explications

1. `Right 10` → `fmap (+1)` transforme la valeur à l’intérieur → `Right 11`.
2. `Left "Erreur"` → `fmap` n’agit pas sur le `Left` → reste `Left "Erreur"`.
3. `main` utilise `putStrLn` et `show` pour afficher le résultat sur le terminal.

En résumé :

* L’instance `Functor` définit seulement le comportement de `fmap`.
* La fonction `main` sert à **tester ou exécuter ce comportement**.

#### Exemple d’utilisation

```haskell
import EitherFunctor

example1 :: Either String Int
example1 = fmap (+1) (Right 10)  -- Résultat : Right 11

example2 :: Either String Int
example2 = fmap (+1) (Left "Erreur")  -- Résultat : Left "Erreur"
```

Cela respecte le **pattern classique de fmap sur Either**, où seules les valeurs valides (`Right`) sont transformées.
