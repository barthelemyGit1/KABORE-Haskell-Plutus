## HC11T3 : Classe de type Container pour Box

Définir une classe de type Container avec les méthodes isEmpty, contains et replace, puis implémenter une instance pour le type Box.

---

### Code haskell

```haskell
-- Définition du type paramétrique Box
data Box a = Empty | Has a deriving (Show, Eq)

-- Définition de la classe de type Container
class Container c where
  isEmpty  :: c a -> Bool
  contains :: Eq a => c a -> a -> Bool
  replace  :: c a -> a -> c a

-- Instance Container pour Box
instance Container Box where
  isEmpty Empty   = True
  isEmpty (Has _) = False

  contains Empty _       = False
  contains (Has x) val   = x == val

  replace Empty val      = Has val
  replace (Has _) val    = Has val

-- Exemples d'utilisation
box1, box2 :: Box Int
box1 = Empty
box2 = Has 10

main :: IO ()
main = do
  print (isEmpty box1)           -- True
  print (isEmpty box2)           -- False
  print (contains box2 10)       -- True
  print (contains box2 5)        -- False
  print (replace box1 5)         -- Has 5
  print (replace box2 20)        -- Has 20
```

---

### 🔎 Explications

* `class Container c where ...` : définit une interface générique pour tout type de conteneur `c`.

  * `isEmpty :: c a -> Bool` : vérifie si le conteneur est vide.
  * `contains :: Eq a => c a -> a -> Bool` : vérifie si une valeur est dans le conteneur.
  * `replace :: c a -> a -> c a` : remplace le contenu du conteneur par une nouvelle valeur.
* `instance Container Box` : implémente ces méthodes pour `Box a`.

---

### ✅ Résultat attendu

```
True
False
True
False
Has 5
Has 20
```
