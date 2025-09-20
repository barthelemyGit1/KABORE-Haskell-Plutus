## HC20T18 : MaybeT pour la validation d’entrée utilisateur

Créer un transformateur de monade MaybeT pour combiner Maybe et IO dans la validation d’entrée utilisateur.

---

### Code complet

```haskell
import Control.Monad.Trans.Maybe
import Control.Monad.Trans.Class (lift)
import Control.Monad (when)

-- Fonction pour lire et valider un entier positif
readPositiveInt :: MaybeT IO Int
readPositiveInt = MaybeT $ do
    putStrLn "Entrez un entier positif :"
    line <- getLine
    let maybeInt = case reads line of
                     [(n, "")] | n > 0 -> Just n
                     _                 -> Nothing
    return maybeInt

-- Autre exemple : lire un mot de passe non vide
readNonEmptyPassword :: MaybeT IO String
readNonEmptyPassword = MaybeT $ do
    putStrLn "Entrez un mot de passe non vide :"
    pwd <- getLine
    return $ if null pwd then Nothing else Just pwd

-- Programme principal
main :: IO ()
main = do
    putStrLn "=== Validation d'entrée avec MaybeT ==="
    
    result <- runMaybeT $ do
        n   <- readPositiveInt
        lift $ putStrLn $ "Vous avez entré : " ++ show n
        pwd <- readNonEmptyPassword
        lift $ putStrLn $ "Mot de passe accepté : " ++ pwd
        return (n, pwd)
    
    case result of
      Just (n, pwd) -> putStrLn $ "Succès ! Valeurs validées : " ++ show (n, pwd)
      Nothing       -> putStrLn "Échec de validation : entrée invalide."
```

---

### Explications

1. **`MaybeT IO a`**

   * C’est un **transformateur de monade** qui combine `Maybe` et `IO`.
   * Permet de gérer **l’échec d’une opération** tout en restant dans la monade `IO`.

2. **Lecture et validation**

   * `readPositiveInt` : lit une ligne, tente de la parser en entier positif.

     * Succès → `Just n`
     * Échec → `Nothing` (ce qui arrête la chaîne de monades `MaybeT`).
   * `readNonEmptyPassword` : lit un mot de passe non vide.

3. **`lift`**

   * Permet de **remonter une action `IO`** à l’intérieur du `MaybeT`.
   * Exemple : `lift $ putStrLn ...` pour afficher un message.

4. **Exécution**

   * `runMaybeT` transforme `MaybeT IO a` en `IO (Maybe a)`.
   * On peut ensuite gérer `Nothing` ou `Just valeur` pour savoir si la validation a réussi.

---

### Exemple d’exécution

```
=== Validation d'entrée avec MaybeT ===
Entrez un entier positif :
-3
Échec de validation : entrée invalide.
```

```
=== Validation d'entrée avec MaybeT ===
Entrez un entier positif :
42
Vous avez entré : 42
Entrez un mot de passe non vide :
Haskell123
Mot de passe accepté : Haskell123
Succès ! Valeurs validées : (42,"Haskell123")
```

---

💡 **Résumé**

* `MaybeT` simplifie la **validation séquentielle** combinée avec `IO`.
* La première entrée invalide arrête immédiatement le calcul, sans quitter `IO`.
