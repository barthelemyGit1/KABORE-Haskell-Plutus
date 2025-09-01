## HC18T3 : Fonction incrementTreeValues

Définir une fonction incrementTreeValues qui ajoute un à chaque valeur d’un arbre en utilisant l’instance Functor.

## Code haskell

```haskell
-- src/TreeUtils.hs
module TreeUtils where

import Tree  -- On importe notre type Tree et son instance Functor

-- | Incrémente chaque valeur de l'arbre de 1
incrementTreeValues :: Num a => Tree a -> Tree a
incrementTreeValues = fmap (+1)
```

### Explications

1. **`fmap (+1)`** : grâce à l’instance `Functor` pour `Tree`, `fmap` applique la fonction `(+1)` à **chaque valeur du noeud** tout en conservant la structure de l’arbre.

2. **Type signature** : `Num a => Tree a -> Tree a` signifie que l’on peut incrémenter uniquement des arbres dont les valeurs sont de type numérique (`Int`, `Integer`, `Float`, etc.).

#### Exemple d’utilisation

```haskell
-- app/Main.hs
module Main where

import Tree
import TreeUtils

main :: IO ()
main = do
    let tree = Node 1 (Node 2 Empty Empty) (Node 3 Empty Empty)
    print tree
    let incrementedTree = incrementTreeValues tree
    print incrementedTree
```

**Sortie attendue :**

```
Node 1 (Node 2 Empty Empty) (Node 3 Empty Empty)
Node 2 (Node 3 Empty Empty) (Node 4 Empty Empty)
```

Chaque valeur a été incrémentée de 1, et la **structure de l’arbre est intacte** grâce au `Functor`.
