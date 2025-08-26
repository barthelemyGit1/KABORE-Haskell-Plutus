## HC10T5 : Classe de type ShowDetailed

Définir une classe de type ShowDetailed avec une fonction showDetailed :: a -> String.

L’implémenter pour un type User.

---

### Code Haskell :

```haskell
-- Définition du type User
data User = User
  { username :: String
  , age      :: Int
  , email    :: String
  } deriving (Show)

-- Définition de la classe de type ShowDetailed
class ShowDetailed a where
  showDetailed :: a -> String

-- Implémentation de ShowDetailed pour User
instance ShowDetailed User where
  showDetailed (User name age email) =
    "Nom d'utilisateur : " ++ name ++
    ", Âge : " ++ show age ++
    ", Email : " ++ email

-- Exemples d'utilisation
user1 :: User
user1 = User "alice" 30 "alice@example.com"

user2 :: User
user2 = User "bob" 25 "bob@example.com"

-- Programme principal
main :: IO ()
main = do
  putStrLn (showDetailed user1)
  putStrLn (showDetailed user2)
```

---

### 🔎 Explications

* `class ShowDetailed a where showDetailed :: a -> String` : définit une **interface** pour afficher une version détaillée d’un type.
* `instance ShowDetailed User` : implémente cette interface pour le type `User`.
* La fonction `showDetailed` retourne une **chaîne lisible** incluant tous les champs du `User`.
* On peut afficher plusieurs utilisateurs avec `putStrLn`.

---

### ✅ Résultat attendu

```
Nom d'utilisateur : alice, Âge : 30, Email : alice@example.com
Nom d'utilisateur : bob, Âge : 25, Email : bob@example.com
```
