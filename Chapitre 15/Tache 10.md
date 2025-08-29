## HC15T10 : Programme de vitesse utilisant Either et les exceptions IO

Créer un programme de calcul de vitesse qui utilise à la fois Either et la gestion des exceptions IO pour illustrer la gestion hybride des erreurs.

---

1. **`Either`** → pour gérer les erreurs liées au calcul (ex : division par zéro).
2. **`try`** → pour gérer les erreurs IO lors de la lecture d’un fichier (ex : fichier inexistant).

---

## ✅ Exemple complet : calcul de vitesse hybride

```haskell
module Main where

import System.IO
import Control.Exception (try, IOException)
import Text.Read (readMaybe)

-- Division sécurisée avec Either pour messages détaillés
safeDiv :: Double -> Double -> Either String Double
safeDiv _ 0 = Left "Erreur : division par zéro (temps = 0)"
safeDiv d t = Right (d / t)

main :: IO ()
main = do
    putStrLn "Entrez le nom du fichier contenant distance et temps (sur deux lignes) :"
    fileName <- getLine

    -- Gestion des exceptions IO avec try
    result <- try (readFile fileName) :: IO (Either IOException String)

    case result of
        Left e -> putStrLn $ "Erreur lors de la lecture du fichier : " ++ show e
        Right content -> do
            let ls = lines content
            case ls of
                (dStr:tStr:_) -> do
                    case (readMaybe dStr :: Maybe Double, readMaybe tStr :: Maybe Double) of
                        (Just d, Just t) ->
                            case safeDiv d t of
                                Left err     -> putStrLn err
                                Right vitesse -> putStrLn $ "Vitesse = " ++ show vitesse ++ " m/s"
                        _ -> putStrLn "Erreur : impossible de parser distance ou temps (valeurs invalides)"
                _ -> putStrLn "Erreur : le fichier doit contenir au moins deux lignes (distance et temps)."
```

---

## ⚡ Explications

* **Fichier attendu** : deux lignes →

  ```
  100
  20
  ```

  Ici distance = 100m, temps = 20s → vitesse = 5 m/s.

* **Étapes du programme** :

  1. `try (readFile fileName)` → capture les erreurs IO (`Left IOException`).
  2. Parsing avec `readMaybe` → évite les erreurs si l’utilisateur tape du texte au lieu de chiffres.
  3. `safeDiv d t` → retourne soit une erreur (`Left "..."`), soit la vitesse (`Right valeur`).

---

### 💡 Exemple d’exécution

✅ Cas normal (`data.txt` contient `100\n20`):

```
Entrez le nom du fichier contenant distance et temps (sur deux lignes) :
data.txt
Vitesse = 5.0 m/s
```

⚠️ Cas division par zéro (`data.txt` contient `50\n0`):

```
Erreur : division par zéro (temps = 0)
```

⚠️ Cas fichier manquant :

```
Erreur lors de la lecture du fichier : data.txt: openFile: does not exist (No such file or directory)
```
