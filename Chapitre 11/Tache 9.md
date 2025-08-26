## HC11T9 : Type Length avec unités

Définir un nouveau type Length avec les constructeurs M et Km, dériver Eq et corriger manuellement les comparaisons entre mètres et kilomètres.

---

### Code haskell 

```haskell
-- Définition du type Length
data Length = M Double | Km Double deriving (Show, Eq)

-- Instance Ord pour Length avec conversion
instance Ord Length where
  compare (M x) (M y)     = compare x y
  compare (Km x) (Km y)   = compare x y
  compare (M x) (Km y)    = compare x (y * 1000)   -- convert Km en M
  compare (Km x) (M y)    = compare (x * 1000) y   -- convert Km en M

-- Exemples d'utilisation
l1 :: Length
l1 = M 500

l2 :: Length
l2 = Km 1

l3 :: Length
l3 = M 1500

main :: IO ()
main = do
  print (l1 == M 500)       -- True
  print (l1 < l2)           -- True (500 m < 1000 m)
  print (l3 > l2)           -- True (1500 m > 1000 m)
  print (min l1 l2)         -- M 500
  print (max l1 l2)         -- Km 1
```

---

### 🔎 Explications

* `data Length = M Double | Km Double` : type avec **deux unités**.
* `deriving Eq` : permet de vérifier l’égalité **sans conversion** (M 1000 /= Km 1).
* `instance Ord Length` : implémente **manuellement** `compare` en convertissant les kilomètres en mètres pour comparer correctement.
* `min` et `max` fonctionnent automatiquement grâce à `Ord`.

---

### ✅ Résultat attendu

```
True
True
True
M 500
Km 1
```
