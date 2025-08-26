## HC9T5 : Type de données paramétrique avec syntaxe d’enregistrement

Définir un type de données paramétrique Shape a avec les constructeurs Circle et Rectangle, contenant chacun un champ color de type a.

---

### Code haskell :

```haskell
-- Type paramétrique Shape a avec syntaxe d'enregistrement
data Shape a
  = Circle
      { radius :: Float
      , color  :: a
      }
  | Rectangle
      { width  :: Float
      , height :: Float
      , color  :: a
      }
  deriving (Show)

-- Exemples d'utilisation
circle1 :: Shape String
circle1 = Circle
  { radius = 5.0
  , color  = "red"
  }

rect1 :: Shape String
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

### 🔎 Explications

* `data Shape a = Circle { ... } | Rectangle { ... }` : type **somme paramétrique** avec deux constructeurs.
* Chaque constructeur a un champ `color :: a`, donc le type de couleur peut être `String`, `Int`, ou même un type plus complexe.
* `deriving (Show)` permet d’afficher les valeurs avec `print`.
* `circle1` et `rect1` sont des instances avec `color :: String`.

---

### ✅ Résultat attendu

```
Circle {radius = 5.0, color = "red"}
Rectangle {width = 10.0, height = 5.0, color = "blue"}
```
