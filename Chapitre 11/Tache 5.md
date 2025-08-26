## HC11T5 : Fonction guessWhat'sInside pour Container

Créer une fonction guessWhat'sInside qui prend un Container et vérifie si un élément spécifique s’y trouve.

---

### Code haskell

```haskell
-- Classe Container déjà définie
class Container c where
  isEmpty  :: c a -> Bool
  contains :: Eq a => c a -> a -> Bool
  replace  :: c a -> a -> c a

-- Types exemples : Box et Present
data Box a = Empty | Has a deriving (Show, Eq)
data Present a = NoPresent | Gift a deriving (Show, Eq)

-- Instances Container
instance Container Box where
  isEmpty Empty   = True
  isEmpty (Has _) = False
  contains Empty _      = False
  contains (Has x) val  = x == val
  replace Empty val     = Has val
  replace (Has _) val   = Has val

instance Container Present where
  isEmpty NoPresent   = True
  isEmpty (Gift _)    = False
  contains NoPresent _    = False
  contains (Gift x) val   = x == val
  replace NoPresent val   = Gift val
  replace (Gift _) val    = Gift val

-- Fonction guessWhat'sInside
guessWhatsInside :: (Container c, Eq a) => c a -> a -> Bool
guessWhatsInside container val = contains container val

-- Exemples d'utilisation
box1 :: Box Int
box1 = Has 10

present1 :: Present String
present1 = Gift "Chocolat"

main :: IO ()
main = do
  print (guessWhatsInside box1 10)        -- True
  print (guessWhatsInside box1 5)         -- False
  print (guessWhatsInside present1 "Chocolat") -- True
  print (guessWhatsInside present1 "Jouet")    -- False
```

---

### 🔎 Explications

* `guessWhatsInside :: (Container c, Eq a) => c a -> a -> Bool` :

  * Fonction générique pour tout type de conteneur `c` et type d’élément `a`.
  * Utilise `contains` pour vérifier si la valeur est dans le conteneur.
* On peut l’utiliser avec `Box`, `Present`, ou tout autre type qui implémente `Container`.

---

### ✅ Résultat attendu

```
True
False
True
False
```
