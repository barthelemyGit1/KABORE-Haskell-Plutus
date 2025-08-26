## HC8T4 : Syntaxe d’enregistrement pour Employee

Définir un nouveau type Employee en syntaxe d’enregistrement, avec les champs name :: String et experienceInYears :: Float.

Créer un employé richard avec 7,5 ans d’expérience.

---

```haskell
-- Définition du type Employee avec la syntaxe d'enregistrement
data Employee = Employee
  { name :: String
  , experienceInYears :: Float
  } deriving (Show)

-- Exemple d'un employé
richard :: Employee
richard = Employee
  { name = "Richard"
  , experienceInYears = 7.5
  }

-- Exemple d’utilisation
main :: IO ()
main = print richard
```

### Explications :

* `data Employee = Employee { ... }` définit un **record** avec des champs nommés.
* `richard` est un `Employee` construit en précisant les champs avec la syntaxe `{ champ = valeur }`.
* `deriving (Show)` permet d’imprimer directement un `Employee` avec `print`.

👉 Résultat attendu :

```
Employee {name = "Richard", experienceInYears = 7.5}
```
