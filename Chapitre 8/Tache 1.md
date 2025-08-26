## HC8T1 : Synonymes de type et fonction de base

Créer un synonyme de type appelé Address pour String et un synonyme de type Value pour Int.

Définir une fonction generateTx :: Address -> Address -> Value -> String qui prend deux adresses et une valeur, et retourne une chaîne qui les concatène.

---

```haskell
-- Synonymes de type
type Address = String
type Value   = Int

-- Fonction qui génère une transaction sous forme de chaîne
generateTx :: Address -> Address -> Value -> String
generateTx fromAddr toAddr val =
  "From: " ++ fromAddr ++ " -> To: " ++ toAddr ++ " | Value: " ++ show val

-- Exemple d’utilisation
main :: IO ()
main = do
  putStrLn (generateTx "Alice" "Bob" 50)
```

🔎 Explications :

* `type Address = String` crée un synonyme de type, ça permet de donner plus de **sens** au type utilisé.
* `type Value = Int` idem, pour la clarté.
* `generateTx` prend deux `Address` et une `Value`, puis retourne une chaîne (`String`).
* `show val` sert à convertir le `Int` en `String` pour pouvoir le concaténer.

👉 Résultat attendu en lançant `main` :

```
From: Alice -> To: Bob | Value: 50
```
