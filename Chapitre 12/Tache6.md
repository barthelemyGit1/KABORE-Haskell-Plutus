## HC12T6 : Trier une liste d’entiers

Développer un programme qui lit une liste d’entiers de l’utilisateur et affiche la liste triée dans l’ordre croissant.

---

### Code haskell

```haskell
import Data.List (sort)
import Data.Char (isDigit)
import Control.Monad (when)

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez des entiers séparés par des espaces :"
    input <- getLine
    let maybeInts = map readMaybe (words input)
    if any (== Nothing) maybeInts
        then putStrLn "Erreur : veuillez entrer uniquement des nombres entiers valides."
        else do
            let ints = map (\(Just x) -> x) maybeInts
            putStrLn $ "Liste triée : " ++ show (sort ints)

-- Fonction utilitaire pour convertir String en Maybe Int
readMaybe :: String -> Maybe Int
readMaybe s = case reads s of
                [(x, "")] -> Just x
                _         -> Nothing
```

---

### Explications :

1. **Lecture de la ligne utilisateur** :

   ```haskell
   input <- getLine
   ```

2. **Découpage en mots et conversion en entiers** :

   * `words input` sépare la chaîne par espaces.
   * `readMaybe` convertit chaque mot en `Int` de manière sûre (renvoie `Nothing` si ce n’est pas un nombre).

3. **Validation** :

   * Si `any (== Nothing) maybeInts` est vrai → entrée invalide.

4. **Tri** :

   ```haskell
   sort ints
   ```

   utilise la fonction `sort` de `Data.List`.

5. **Affichage** :

   ```haskell
   putStrLn $ "Liste triée : " ++ show (sort ints)
   ```

---
