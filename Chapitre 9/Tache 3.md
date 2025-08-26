## HC9T3 : Fonction pour additionner les valeurs dans une Box

Créer une fonction addN qui prend un nombre et une Box a. Si la boîte contient un nombre, additionner ce nombre à la valeur.

---

### Code haskell :

```haskell
-- Type Box déjà défini
data Box a = Empty | Has a deriving (Show)

-- Fonction qui ajoute un nombre à la valeur contenue dans la boîte
addN :: Num a => a -> Box a -> Box a
addN n Empty     = Empty
addN n (Has val) = Has (val + n)

-- Exemples d'utilisation
box1 :: Box Int
box1 = Has 10

box2 :: Box Int
box2 = Empty

-- Programme principal
main :: IO ()
main = do
  print (addN 5 box1)  -- Has 15
  print (addN 3 box2)  -- Empty
```

---

### 🔎 Explications

* `Num a =>` : contrainte qui permet d’utiliser l’opérateur `+` sur le type `a`.
* `addN n Empty = Empty` : si la boîte est vide, on retourne `Empty`.
* `addN n (Has val) = Has (val + n)` : si la boîte contient une valeur, on l’additionne avec `n`.
* Cette fonction **ne change rien** si la boîte est vide.

---

### ✅ Résultat attendu

```
Has 15
Empty
```
