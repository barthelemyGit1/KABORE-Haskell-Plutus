## HC11T10 : Fonction sortContainers

Implémenter une fonction sortContainers qui trie une liste de containers à l’aide de l’instance Ord dérivée.

---

### Code haskell

```haskell
import Data.List (sort)

-- Définition du type Box
data Box a = Empty | Has a deriving (Show, Eq)

-- Instance Ord pour Box
instance Ord a => Ord (Box a) where
  compare Empty Empty       = EQ
  compare Empty _           = LT
  compare _ Empty           = GT
  compare (Has x) (Has y)   = compare x y

-- Fonction sortContainers
sortContainers :: Ord a => [Box a] -> [Box a]
sortContainers = sort

-- Exemples d'utilisation
box1, box2, box3, box4 :: Box Int
box1 = Has 10
box2 = Empty
box3 = Has 5
box4 = Has 20

main :: IO ()
main = do
  let boxes = [box1, box2, box3, box4]
  print boxes
  print (sortContainers boxes)
```

---

### 🔎 Explications

* `sortContainers :: Ord a => [Box a] -> [Box a]` : trie une liste de `Box a` en utilisant `sort` de `Data.List`.
* L’instance `Ord` pour `Box` détermine que :

  * `Empty < Has x`
  * `Has x` est comparé selon `x`.
* Ainsi, `sortContainers` place d’abord les boîtes vides, puis les boîtes contenant des valeurs **du plus petit au plus grand**.

---

### ✅ Résultat attendu

```
[Has 10,Empty,Has 5,Has 20]
[Empty,Has 5,Has 10,Has 20]
```
