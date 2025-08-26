## HC8T6 : Syntaxe d’enregistrement pour variantes Shape

Définir un type Shape avec la syntaxe d’enregistrement avec les champs center :: (Float, Float), color :: String, et radius :: Float pour les cercles, et width :: Float, height :: Float, color :: String pour les rectangles.

Créer une instance de Shape pour un cercle et un rectangle.

---

Ici, on veut définir un type `Shape` qui peut représenter **soit un cercle** soit un **rectangle**, avec des champs spécifiques.
On utilise donc un **type somme** (`data ... = ... | ...`) avec la **syntaxe d’enregistrement** pour chaque constructeur.

Voici le code :

```haskell
-- Définition du type Shape avec deux variantes
data Shape
  = Circle
      { center :: (Float, Float)
      , color  :: String
      , radius :: Float
      }
  | Rectangle
      { width  :: Float
      , height :: Float
      , color  :: String
      }
  deriving (Show)

-- Exemple d'un cercle
circle1 :: Shape
circle1 = Circle
  { center = (0.0, 0.0)
  , color  = "red"
  , radius = 5.0
  }

-- Exemple d'un rectangle
rect1 :: Shape
rect1 = Rectangle
  { width  = 10.0
  , height = 5.0
  , color  = "blue"
  }

-- Programme principal
main :: IO ()
main = do
  print circle1
  print rect1
```

---

### 🔎 Explication :

* `data Shape = Circle {...} | Rectangle {...}` définit un type algébrique avec **deux constructeurs**.
* Chaque constructeur utilise la **syntaxe d’enregistrement** :

  * `Circle` a les champs `center`, `color` et `radius`.
  * `Rectangle` a les champs `width`, `height` et `color`.
* On crée deux instances :

  * `circle1` est un cercle rouge, centré en `(0,0)` avec un rayon de 5.
  * `rect1` est un rectangle bleu de largeur 10 et hauteur 5.
* `deriving (Show)` permet d’afficher directement les formes avec `print`.

👉 Résultat attendu à l’exécution :

```
Circle {center = (0.0,0.0), color = "red", radius = 5.0}
Rectangle {width = 10.0, height = 5.0, color = "blue"}
```
