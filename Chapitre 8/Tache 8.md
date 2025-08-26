## HC8T8 : Synonymes de type et fonction de salutation
Utiliser des synonymes de type Name pour String et Age pour Int.
Définir une fonction greet :: Name -> Age -> String qui prend un nom et un âge, et retourne un message de salutation.

---

### Code haskell

```haskell
-- Synonymes de type
type Name = String
type Age  = Int

-- Fonction de salutation
greet :: Name -> Age -> String
greet name age = "Bonjour " ++ name ++ "! Tu as " ++ show age ++ " ans."

-- Exemple d’utilisation
main :: IO ()
main = do
  putStrLn (greet "Alice" 30)
  putStrLn (greet "Bob" 25)
```

---

### 🔎 Explication :

* `type Name = String` : `Name` est juste un alias de `String`.
* `type Age = Int` : `Age` est un alias de `Int`.
* `greet` prend un `Name` et un `Age`, puis retourne une `String`.
* On utilise `show` pour convertir l’`Int` (`age`) en texte afin de l’insérer dans la phrase.

---

### ✅ Résultat attendu :

```
Bonjour Alice! Tu as 30 ans.
Bonjour Bob! Tu as 25 ans.
```
