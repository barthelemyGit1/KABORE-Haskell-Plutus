## HC14T9 : Extension PartialTypeSignatures

Utiliser l’extension PartialTypeSignatures pour permettre les types jokers dans une signature de fonction.

Pour **HC14T9**, l’objectif est d’utiliser l’extension `PartialTypeSignatures` pour **mettre des “types jokers” (`_`)** dans les signatures de fonctions. Cela permet à GHC d’inférer automatiquement certaines parties du type sans que tu aies à tout préciser.

---

## 3️⃣ Exemple avec un type générique

```haskell
{-# LANGUAGE PartialTypeSignatures #-}

module PartialExample where

-- Fonction qui retourne la longueur d’une liste, mais on ne précise pas le type de l’élément
listLength :: _ -> Int
listLength xs = length xs
```

* `_` → GHC infère `[a]` pour une liste de n’importe quel type `a`.
* `Int` est explicitement le type du résultat.

---

### Explications :

* Les `_` sont des **types jokers** que GHC va inférer.
* Ici, GHC va comprendre que `x` et `y` doivent être `Int` pour que `x + y` fonctionne.
* Cela permet de **réduire la verbosité** pour des types longs ou complexes.

---

## 4️⃣ Utilisation dans `Main.hs`

```haskell
module Main where

import PartialExample

main :: IO ()
main = do
    print $ add 3 5
    print $ listLength ["a","b","c"]
```

✅ Résultat attendu :

```
8
3
```
