## HC7T4 : Type personnalisé avec Show et Read

Définir un type de données Shape avec les constructeurs Circle Double et Rectangle Double Double.

Implémenter les instances Show et Read pour ce type.

---

Creation  d'un type personnalisé **`Shape`** avec deux constructeurs :

* `Circle Double` (un cercle avec son rayon),
* `Rectangle Double Double` (un rectangle avec largeur et hauteur).

Ensuite, on va définir les instances **`Show`** (affichage en chaîne) et **`Read`** (conversion depuis une chaîne).

---

### Code Haskell

```haskell
-- Définition du type Shape
data Shape = Circle Double | Rectangle Double Double

-- Instance Show : comment afficher Shape en String
instance Show Shape where
    show (Circle r) = "Circle " ++ show r
    show (Rectangle w h) = "Rectangle " ++ show w ++ " " ++ show h

-- Instance Read : comment lire Shape depuis une String
instance Read Shape where
    readsPrec _ input =
        case words input of
            ["Circle", r] ->
                [(Circle (read r), "")]
            ["Rectangle", w, h] ->
                [(Rectangle (read w) (read h), "")]
            _ -> []

-- Fonction principale pour tester
main :: IO ()
main = do
    let c = Circle 5.0
    let r = Rectangle 3.0 4.0

    print c                      -- "Circle 5.0"
    print r                      -- "Rectangle 3.0 4.0"

    -- Conversion String -> Shape
    let c2 = read "Circle 7.5" :: Shape
    let r2 = read "Rectangle 10.0 20.0" :: Shape

    print c2                     -- "Circle 7.5"
    print r2                     -- "Rectangle 10.0 20.0"
```

---

### Explications

1. **Type de données**

   ```haskell
   data Shape = Circle Double | Rectangle Double Double
   ```

   * `Circle Double` → cercle avec rayon `Double`.
   * `Rectangle Double Double` → rectangle avec largeur et hauteur.

2. **Instance `Show`**

   * Définit comment convertir un `Shape` en `String`.
   * Exemple : `Circle 5.0` devient `"Circle 5.0"`.

3. **Instance `Read`**

   * Définit comment lire une chaîne et la transformer en `Shape`.
   * On découpe la chaîne avec `words`.
   * Si c’est `"Circle <r>"` → on construit `Circle r`.
   * Si c’est `"Rectangle <w> <h>"` → on construit `Rectangle w h`.
   * Sinon, on retourne `[]` (échec du parsing).

4. **Tests**

   * `print (Circle 5.0)` affiche `"Circle 5.0"`.
   * `read "Rectangle 3.0 4.0" :: Shape` construit un `Rectangle`.

---

### Exemple de sortie

```
Circle 5.0
Rectangle 3.0 4.0
Circle 7.5
Rectangle 10.0 20.0
```
