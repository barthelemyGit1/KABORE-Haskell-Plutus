## HC8T7 : Types de données et description d’animaux

Définir un nouveau type Animal avec les constructeurs Dog String et Cat String.

Créer une fonction describeAnimal :: Animal -> String qui décrit l’animal.

Créer des instances pour un chien et un chat.

---

### Code haskell

```haskell
-- Définition du type Animal
data Animal
  = Dog String   -- un chien avec un nom
  | Cat String   -- un chat avec un nom
  deriving (Show)

-- Fonction qui décrit un animal
describeAnimal :: Animal -> String
describeAnimal (Dog name) = "C'est un chien qui s'appelle " ++ name ++ "."
describeAnimal (Cat name) = "C'est un chat qui s'appelle " ++ name ++ "."

-- Exemples d'animaux
dog1 :: Animal
dog1 = Dog "Rex"

cat1 :: Animal
cat1 = Cat "Mimi"

-- Programme principal
main :: IO ()
main = do
  putStrLn (describeAnimal dog1)
  putStrLn (describeAnimal cat1)
```

---

### 🔎 Explications

* `data Animal = Dog String | Cat String` définit un **type somme** : un `Animal` est soit un `Dog` avec un nom (`String`), soit un `Cat` avec un nom.
* `describeAnimal` utilise le **pattern matching** :

  * Si l’animal est `Dog name`, on retourne une phrase qui dit que c’est un chien.
  * Si c’est `Cat name`, on retourne une phrase qui dit que c’est un chat.
* `dog1` et `cat1` sont des instances de `Animal`.

---

### ✅ Résultat attendu à l’exécution :

```
C'est un chien qui s'appelle Rex.
C'est un chat qui s'appelle Mimi.
```
