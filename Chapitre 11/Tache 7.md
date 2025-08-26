## HC11T7 : Instance Ord pour Box

Implémenter l’instance Ord pour le type Box en utilisant la fonction compare.

---

### Code haskell 

```haskell
-- Définition du type Box
data Box a = Empty | Has a deriving (Show, Eq)

-- Instance Ord pour Box
-- Nécessite que le type a soit lui-même Ord
instance Ord a => Ord (Box a) where
  compare Empty Empty   = EQ
  compare Empty _       = LT
  compare _ Empty       = GT
  compare (Has x) (Has y) = compare x y

-- Exemples d'utilisation
box1, box2, box3 :: Box Int
box1 = Has 10
box2 = Has 20
box3 = Empty

main :: IO ()
main = do
  print (box1 < box2)   -- True
  print (box2 > box1)   -- True
  print (box1 > box3)   -- True
  print (box3 < box1)   -- True
  print (box1 == Has 10) -- True
```

---

### 🔎 Explications

* `instance Ord a => Ord (Box a)` :

  * Permet de comparer deux `Box a` si `a` est lui-même dans `Ord`.
* Règles de comparaison :

  * `Empty` est considéré plus petit que n’importe quelle boîte contenant une valeur (`Has x`).
  * Deux `Has x` et `Has y` sont comparés selon `compare x y`.

---

### ✅ Résultat attendu

```
True
True
True
True
True
```
