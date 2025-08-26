## HC11T1 : Instance WeAccept pour Box

Créer une instance WeAccept pour le type Box et écrire une fonction qui retourne une liste de boîtes acceptées.

---

### Code haskell

```haskell
-- Définition du type paramétrique Box
data Box a = Empty | Has a deriving (Show, Eq)

-- Définition de la classe de type WeAccept
class WeAccept a where
  isAccepted :: a -> Bool

-- Instance WeAccept pour Box a
-- Une boîte est acceptée si elle contient une valeur
instance WeAccept (Box a) where
  isAccepted (Has _) = True
  isAccepted Empty   = False

-- Fonction qui retourne une liste de boîtes acceptées
acceptedBoxes :: [Box a] -> [Box a]
acceptedBoxes = filter isAccepted

-- Exemples d'utilisation
box1, box2, box3 :: Box Int
box1 = Has 10
box2 = Empty
box3 = Has 20

main :: IO ()
main = do
  print (acceptedBoxes [box1, box2, box3])  -- [Has 10, Has 20]
```

---

### 🔎 Explications

* `class WeAccept a where isAccepted :: a -> Bool` : interface pour vérifier si un élément est accepté.
* `instance WeAccept (Box a)` :

  * `Has _` → accepté
  * `Empty` → non accepté
* `acceptedBoxes` utilise `filter isAccepted` pour ne garder que les boîtes contenant une valeur.

---

### ✅ Résultat attendu

```
[Has 10,Has 20]
```
