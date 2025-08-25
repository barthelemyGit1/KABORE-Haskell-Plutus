## HC7T8 : Parser une valeur avec Read

Écrire une fonction parseShape qui prend une String et retourne un Shape.

La fonction doit retourner Nothing en cas d’entrée invalide.

---

### Code Haskell

```haskell
-- Définition du type Shape
data Shape = Circle Double | Rectangle Double Double
    deriving (Show, Read)

-- Fonction parseShape : String -> Maybe Shape
parseShape :: String -> Maybe Shape
parseShape s =
    case reads s :: [(Shape, String)] of
        [(shape, "")] -> Just shape  -- lecture réussie, toute la chaîne consommée
        _             -> Nothing     -- lecture échouée

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ parseShape "Circle 5.0"          -- Just (Circle 5.0)
    print $ parseShape "Rectangle 3.0 4.0"  -- Just (Rectangle 3.0 4.0)
    print $ parseShape "Triangle 5.0 6.0"   -- Nothing
    print $ parseShape "Circle abc"         -- Nothing
```

---

### Explications

1. **Type `Shape`**

   ```haskell
   data Shape = Circle Double | Rectangle Double Double
       deriving (Show, Read)
   ```

   * `Read` permet de parser directement une chaîne en `Shape` avec `reads`.

2. **Fonction `reads`**

   ```haskell
   reads :: Read a => String -> [(a, String)]
   ```

   * Retourne une liste de tuples `(valeur_parsée, reste_de_la_chaine)`.
   * Si la liste est vide → échec.
   * Si le reste de la chaîne n’est pas vide → parsing incomplet.

3. **`parseShape`**

   ```haskell
   case reads s :: [(Shape, String)] of
       [(shape, "")] -> Just shape
       _             -> Nothing
   ```

   * On ne garde que le cas où toute la chaîne a été consommée (`""`).
   * Sinon, on retourne `Nothing`.

4. **Tests**

   * Chaînes valides → `Just Shape`.
   * Chaînes invalides → `Nothing`.

---

### Exemple de sortie

```
Just (Circle 5.0)
Just (Rectangle 3.0 4.0)
Nothing
Nothing
```

---

💡 Astuce : Cette technique fonctionne pour **tout type dérivant `Read`**.
