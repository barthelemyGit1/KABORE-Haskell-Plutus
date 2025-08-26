## HC8T2 : Types personnalisés et constructeurs de données

Définir un nouveau type PaymentMethod avec les constructeurs Cash, Card et Cryptocurrency.

Créer un type Person qui inclut un nom, une adresse (tuple String et Int), et une méthode de paiement.

Créer une personne bob qui paie en espèces.

---

```haskell
-- Définition du type PaymentMethod
data PaymentMethod = Cash | Card | Cryptocurrency
  deriving (Show)

-- Définition du type Person
data Person = Person
  { name        :: String
  , address     :: (String, Int)  -- (Rue, Numéro)
  , paymentMeth :: PaymentMethod
  } deriving (Show)

-- Exemple d'une personne : bob
bob :: Person
bob = Person
  { name = "Bob"
  , address = ("Rue des Manguiers", 42)
  , paymentMeth = Cash
  }

-- Exemple d’utilisation
main :: IO ()
main = print bob
```

### Explications :

* `data PaymentMethod = Cash | Card | Cryptocurrency` définit un **type énuméré** (somme de constructeurs).
* `data Person = Person { ... }` définit un **type produit** avec des champs nommés (record syntax).
* `bob` est une valeur du type `Person` utilisant le constructeur `Cash`.
* `deriving (Show)` permet d’afficher directement les valeurs avec `print`.

👉 Résultat attendu en lançant `main` :

```
Person {name = "Bob", address = ("Rue des Manguiers",42), paymentMeth = Cash}
```
