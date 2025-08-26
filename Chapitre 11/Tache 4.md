## HC11T4 : Instance Container pour Present

Implémenter la classe Container pour le type Present.

---

### Code haskell

```haskell
-- Définition du type paramétrique Present
data Present a = NoPresent | Gift a deriving (Show, Eq)

-- Classe Container déjà définie
class Container c where
  isEmpty  :: c a -> Bool
  contains :: Eq a => c a -> a -> Bool
  replace  :: c a -> a -> c a

-- Instance Container pour Present
instance Container Present where
  isEmpty NoPresent   = True
  isEmpty (Gift _)    = False

  contains NoPresent _    = False
  contains (Gift x) val   = x == val

  replace NoPresent val   = Gift val
  replace (Gift _) val    = Gift val

-- Exemples d'utilisation
present1, present2 :: Present Int
present1 = NoPresent
present2 = Gift 50

main :: IO ()
main = do
  print (isEmpty present1)           -- True
  print (isEmpty present2)           -- False
  print (contains present2 50)       -- True
  print (contains present2 10)       -- False
  print (replace present1 30)        -- Gift 30
  print (replace present2 100)       -- Gift 100
```

---

### 🔎 Explications

* `data Present a = NoPresent | Gift a` : type paramétrique qui peut être vide ou contenir un cadeau.
* `instance Container Present` : implémente les trois méthodes de la classe `Container` :

  * `isEmpty` : vérifie si le présent est vide.
  * `contains` : vérifie si le présent contient une valeur spécifique.
  * `replace` : remplace le contenu du présent par une nouvelle valeur.

---

### ✅ Résultat attendu

```
True
False
True
False
Gift 30
Gift 100
```
