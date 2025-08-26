## HC9T2 : Implémenter un type de données paramétrique*

Créer un type de données Box a avec deux constructeurs, Empty et Has a, pour représenter une boîte qui peut contenir une valeur ou non.

---

Code haskell

```haskell
-- Définition d'un type de données paramétrique Box a
data Box a
  = Empty      -- boîte vide
  | Has a      -- boîte contenant une valeur de type 'a'
  deriving (Show)

-- Exemples d'utilisation
emptyBox :: Box Int
emptyBox = Empty

boxWithValue :: Box String
boxWithValue = Has "Bonjour"

-- Programme principal
main :: IO ()
main = do
  print emptyBox       -- Affiche : Empty
  print boxWithValue   -- Affiche : Has "Bonjour"
```

---

### 🔎 Explications

* `data Box a = Empty | Has a` définit un **type somme paramétrique** :

  * `Empty` représente une boîte vide.
  * `Has a` contient une valeur de type `a`.
* `deriving (Show)` permet d’afficher directement une `Box`.
* On peut créer des instances de `Box` avec n’importe quel type (`Int`, `String`, etc.).

---

### ✅ Résultat attendu

```
Empty
Has "Bonjour"
```
