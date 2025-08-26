## HC8T10 : Deriving Show pour Book

En utilisant deriving Show, définir un type Book avec les champs title :: String, author :: String et year :: Int.

Créer une instance de Book et l’afficher avec l’instance Show.

### Code haskell

```haskell
-- Définition du type Book avec deriving Show
data Book = Book
  { title  :: String
  , author :: String
  , year   :: Int
  } deriving (Show)

-- Création d'une instance de Book
myBook :: Book
myBook = Book
  { title  = "Le Petit Prince"
  , author = "Antoine de Saint-Exupéry"
  , year   = 1943
  }

-- Programme principal
main :: IO ()
main = print myBook
```

---

### 🔎 Explications

* `data Book = Book { ... }` : définit un type en **record syntax** avec des champs nommés.
* `deriving (Show)` : permet d’afficher directement une valeur de type `Book` avec `print`.
* `myBook` est une instance de `Book`.
* `print myBook` affiche la valeur complète de l’instance.

---

### ✅ Résultat attendu

```
Book {title = "Le Petit Prince", author = "Antoine de Saint-Exupéry", year = 1943}
```
