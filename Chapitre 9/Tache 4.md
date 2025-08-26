## HC9T4 : Extraire une valeur d’une Box

Créer une fonction extract qui prend une valeur par défaut et une Box a. Elle retourne la valeur à l’intérieur de la boîte ou la valeur par défaut si la boîte est vide.

---

Code haskell

```haskell
-- Type Box déjà défini
data Box a = Empty | Has a deriving (Show)

-- Fonction extract
extract :: a -> Box a -> a
extract def Empty     = def
extract _   (Has val) = val

-- Exemples d'utilisation
box1 :: Box Int
box1 = Has 42

box2 :: Box Int
box2 = Empty

-- Programme principal
main :: IO ()
main = do
  print (extract 0 box1)  -- 42
  print (extract 0 box2)  -- 0
```

---

### 🔎 Explications

* `extract :: a -> Box a -> a` : prend **une valeur par défaut** et une `Box`, retourne une valeur de type `a`.
* `extract def Empty = def` : si la boîte est vide, retourne la valeur par défaut.
* `extract _ (Has val) = val` : si la boîte contient une valeur, on la retourne.
* `_` signifie qu’on **ignore la valeur du premier argument** dans ce cas-là.

---

### ✅ Résultat attendu

```
42
0
```
