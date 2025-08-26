## HC8T5 : Syntaxe d’enregistrement pour Person

Définir un type Person en syntaxe d’enregistrement incluant name :: String, age :: Int et isEmployed :: Bool.

Créer un person1 qui est employé, et un person2 qui est sans emploi.

---

```haskell
-- Définition du type Person avec la syntaxe d'enregistrement
data Person = Person
  { name       :: String
  , age        :: Int
  , isEmployed :: Bool
  } deriving (Show)

-- Exemples de personnes
person1 :: Person
person1 = Person
  { name = "Alice"
  , age = 30
  , isEmployed = True
  }

person2 :: Person
person2 = Person
  { name = "Bob"
  , age = 25
  , isEmployed = False
  }

-- Exemple d’utilisation
main :: IO ()
main = do
  print person1
  print person2
```

```haskell
-- Définition du type Person avec la syntaxe d'enregistrement
data Person = Person
  { name       :: String
  , age        :: Int
  , isEmployed :: Bool
  } deriving (Show)
```

### Explication

* `data Person = Person { ... }` définit un **nouveau type** appelé `Person`.
* La syntaxe `{ champ :: type }` est appelée **record syntax** : elle permet de nommer les champs.
* Ici, un `Person` possède :

  * `name :: String` → le nom de la personne
  * `age :: Int` → son âge
  * `isEmployed :: Bool` → un booléen qui dit si la personne est employée (`True`) ou non (`False`)
* `deriving (Show)` génère automatiquement une fonction pour afficher un `Person` sous forme de texte.

---

```haskell
-- Exemples de personnes
person1 :: Person
person1 = Person
  { name = "Alice"
  , age = 30
  , isEmployed = True
  }

person2 :: Person
person2 = Person
  { name = "Bob"
  , age = 25
  , isEmployed = False
  }
```

###  Création de valeurs

* `person1` et `person2` sont deux variables de type `Person`.
* Elles sont construites avec le **constructeur `Person`** en précisant les champs.
* Pour `person1`, on indique :

  * `name = "Alice"`
  * `age = 30`
  * `isEmployed = True` (donc elle est employée)
* Pour `person2`, on met `isEmployed = False` (donc il est sans emploi).

---

###  Résultat quand on exécute le programme

```
Person {name = "Alice", age = 30, isEmployed = True}
Person {name = "Bob", age = 25, isEmployed = False}
```

On voit directement la **structure de données** affichée en texte grâce à `Show`.

---
