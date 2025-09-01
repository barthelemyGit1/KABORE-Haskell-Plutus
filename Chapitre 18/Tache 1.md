## HC18T1 : Fonction mapToLower avec fmap

Définir une fonction mapToLower utilisant fmap pour convertir tous les caractères d’une liste en minuscules.

## Code haskell

```haskell
-- src/StringUtils.hs
module StringUtils where

import Data.Char (toLower)

-- | Convertit tous les caractères d'une chaîne en minuscules
mapToLower :: String -> String
mapToLower = fmap toLower
```

### Explications

1. **`fmap`** : pour les listes, `fmap` applique une fonction à chaque élément de la liste.

   * Type général pour les listes : `fmap :: (a -> b) -> [a] -> [b]`.
2. **`toLower`** : fonction de `Data.Char` qui convertit un caractère majuscule en minuscule.
3. **Composition** : `fmap toLower` parcourt la chaîne et applique `toLower` à chaque caractère.

#### Exemple d'utilisation dans `Main.hs` :

```haskell
-- app/Main.hs
module Main where

import StringUtils

main :: IO ()
main = do
    let text = "Hello WORLD!"
    putStrLn $ "Original : " ++ text
    putStrLn $ "Minuscules : " ++ mapToLower text
```

**Sortie attendue :**

```
Original : Hello WORLD!
Minuscules : hello world!
```
