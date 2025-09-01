## HC18T4 : Fonction mapToBits

Implémenter une fonction mapToBits qui convertit une liste de Bool en caractères '1' ou '0' à l’aide de fmap.

## Code haskell

```haskell
-- src/BitsUtils.hs
module BitsUtils where

-- | Convertit un Bool en '1' ou '0'
boolToChar :: Bool -> Char
boolToChar True  = '1'
boolToChar False = '0'

-- | Convertit une liste de Bool en une chaîne de caractères '1' et '0' avec fmap
mapToBits :: [Bool] -> [Char]
mapToBits = fmap boolToChar
```

### Explications

1. **`boolToChar`** : transforme `True` en `'1'` et `False` en `'0'`.
2. **`mapToBits`** : utilise `fmap` pour appliquer `boolToChar` à chaque élément de la liste de `Bool`.

   * En Haskell, `fmap` sur une liste est équivalent à `map`.

#### Exemple d’utilisation

```haskell
-- app/Main.hs
module Main where

import BitsUtils

main :: IO ()
main = do
    let boolList = [True, False, True, True, False]
    print $ mapToBits boolList
```

**Sortie :**

```
"10110"
```

Chaque `Bool` de la liste est converti en `'1'` ou `'0'` et la **structure de la liste est conservée** grâce à `fmap`.
