## HC9T10 : Type d’arbre binaire de recherche (BST)

Définir un type d’arbre binaire de recherche BST a avec des constructeurs pour un arbre vide et un nœud contenant une valeur et deux sous-arbres.

---

### Code Haskell :

```haskell
-- Définition du type BST
data BST a
  = EmptyBST
  | NodeBST a (BST a) (BST a)
  deriving (Show)

-- Exemples d'utilisation
bst1 :: BST Int
bst1 = NodeBST 10
          (NodeBST 5 EmptyBST EmptyBST)
          (NodeBST 15 EmptyBST EmptyBST)

bst2 :: BST String
bst2 = NodeBST "M"
          (NodeBST "C" EmptyBST EmptyBST)
          (NodeBST "Z" EmptyBST EmptyBST)

-- Programme principal
main :: IO ()
main = do
  print bst1
  print bst2
```

---

### 🔎 Explications

* `data BST a = EmptyBST | NodeBST a (BST a) (BST a)`

  * `EmptyBST` : représente un arbre vide.
  * `NodeBST a left right` : un nœud contenant une valeur `a` et deux sous-arbres `left` et `right`.
* `deriving (Show)` permet d’afficher les arbres.
* `bst1` et `bst2` sont des exemples avec des `Int` et des `String`.

---

### ✅ Résultat attendu

```
NodeBST 10 (NodeBST 5 EmptyBST EmptyBST) (NodeBST 15 EmptyBST EmptyBST)
NodeBST "M" (NodeBST "C" EmptyBST EmptyBST) (NodeBST "Z" EmptyBST EmptyBST)
```
