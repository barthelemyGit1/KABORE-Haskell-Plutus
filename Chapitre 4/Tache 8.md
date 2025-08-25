## HC4T8 - Tâche 8 : Extraire des valeurs de tuples

Créer une fonction describeTuple qui extrait les valeurs d’un tuple et retourne une chaîne descriptive.

---

## ✅ Code Haskell

```haskell
-- Fonction qui extrait les valeurs d'un tuple et les décrit
describeTuple :: (Show a, Show b) => (a, b) -> String
describeTuple (x, y) = "Le premier élément est " ++ show x ++
                       " et le second élément est " ++ show y

-- Fonction principale pour tester
main :: IO ()
main = do
    putStrLn $ describeTuple (5, "Bonjour")
    putStrLn $ describeTuple ("Alice", 42)
    putStrLn $ describeTuple (True, 3.14)
```

---

## 📝 Explication

1. **Signature de type**

   ```haskell
   describeTuple :: (Show a, Show b) => (a, b) -> String
   ```

   * `(a, b)` : un tuple à deux éléments.
   * `(Show a, Show b)` : contrainte qui impose que `a` et `b` puissent être convertis en texte (via `show`).
   * Retourne une `String`.

2. **Pattern matching**

   ```haskell
   describeTuple (x, y) = ...
   ```

   * `(x, y)` extrait le premier et le second élément du tuple.
   * `show x` et `show y` transforment les valeurs en texte pour les concaténer dans la phrase.

3. **La fonction `main`**

   * Utilise `putStrLn` pour afficher des exemples concrets avec différents types (Int, String, Bool, Float…).

---

## ▶ Exemple de sortie

```
Le premier élément est 5 et le second élément est "Bonjour"
Le premier élément est "Alice" et le second élément est 42
Le premier élément est True et le second élément est 3.14
```
