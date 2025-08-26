## HC10T4 : Instance Eq pour Box

Créer un type paramétrique Box a et en faire une instance de Eq.

---

### Code Haskell :

```haskell
-- Définition du type paramétrique Box a
data Box a = Empty | Has a deriving (Show)

-- Instance Eq pour Box a
instance Eq a => Eq (Box a) where
  Empty   == Empty   = True
  Has x   == Has y   = x == y
  _       == _       = False

-- Exemples d'utilisation
box1 :: Box Int
box1 = Has 10

box2 :: Box Int
box2 = Has 10

box3 :: Box Int
box3 = Empty

-- Programme principal
main :: IO ()
main = do
  print (box1 == box2)  -- True
  print (box1 == box3)  -- False
  print (box3 == Empty) -- True
```

---

### 🔎 Explications

* `data Box a = Empty | Has a` : type paramétrique qui peut être vide ou contenir une valeur.
* `instance Eq a => Eq (Box a)` :

  * permet de comparer deux `Box a` si le type `a` lui-même est comparable (`Eq a =>`).
* Les règles de comparaison :

  * Deux boîtes vides (`Empty`) sont égales.
  * Deux boîtes contenant des valeurs (`Has x` et `Has y`) sont égales si `x == y`.
  * Tout autre cas (`Empty` vs `Has x`) → False.

---

### ✅ Résultat attendu

```
True
False
True
```
