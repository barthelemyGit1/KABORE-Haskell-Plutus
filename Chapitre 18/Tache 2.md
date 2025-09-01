## HC18T2 : Instance Functor pour Tree

Créer une instance Functor pour le type d’arbre binaire Tree.

## Code haskell

```haskell
-- src/Tree.hs
module Tree where

-- Définition d'un arbre binaire générique
data Tree a = Empty
            | Node a (Tree a) (Tree a)
            deriving (Show, Eq)

-- Instance Functor pour Tree
instance Functor Tree where
    fmap _ Empty = Empty
    fmap f (Node x left right) =
        Node (f x) (fmap f left) (fmap f right)
```

### Explications

1. **Type `Tree a`** : un arbre binaire peut être vide (`Empty`) ou contenir une valeur `a` avec un sous-arbre gauche et un sous-arbre droit (`Node a (Tree a) (Tree a)`).

2. **`Functor`** : un `Functor` est quelque chose sur lequel on peut appliquer une fonction (`fmap`) à chaque élément tout en conservant la structure.

3. **Implémentation de `fmap` pour Tree** :

   * Si l’arbre est vide (`Empty`), on retourne `Empty`.
   * Sinon, on applique la fonction `f` à la valeur du noeud et on appelle récursivement `fmap f` sur les sous-arbres gauche et droit.

#### Exemple d’utilisation

```haskell
-- app/Main.hs
module Main where

import Tree

main :: IO ()
main = do
    let tree = Node 1 (Node 2 Empty Empty) (Node 3 Empty Empty)
    print tree
    print $ fmap (*2) tree
```

**Sortie attendue :**

```
Node 1 (Node 2 Empty Empty) (Node 3 Empty Empty)
Node 2 (Node 4 Empty Empty) (Node 6 Empty Empty)
```

Veux‑tu que je fasse ça ?
