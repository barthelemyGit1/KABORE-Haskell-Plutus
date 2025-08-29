## HC15T1 : Gérer les exceptions lors de la lecture d’un fichier et du calcul de la vitesse 

Gérer les exceptions dans un programme qui lit un fichier et calcule une vitesse à partir d’une saisie utilisateur.

---

1. Lit un fichier.
2. Demande une saisie utilisateur (ex: distance et temps).
3. Calcule la vitesse (`v = distance / temps`).
4. Gère les **exceptions** liées au fichier ou aux entrées invalides.

Voici un exemple complet :

---

## 1️⃣ Code Haskell avec gestion d’exceptions

```haskell
module Main where

import System.IO
import Control.Exception
import Text.Read (readMaybe)

main :: IO ()
main = do
    putStrLn "Entrez le nom du fichier à lire :"
    fileName <- getLine

    -- Lecture du fichier avec gestion d'erreurs
    fileContentResult <- try (readFile fileName) :: IO (Either IOException String)
    case fileContentResult of
        Left ex -> putStrLn $ "Erreur lors de la lecture du fichier : " ++ show ex
        Right content -> do
            putStrLn "Contenu du fichier :"
            putStrLn content

            -- Saisie de la distance
            putStrLn "Entrez la distance parcourue (en mètres) :"
            distInput <- getLine
            let maybeDist = readMaybe distInput :: Maybe Double

            -- Saisie du temps
            putStrLn "Entrez le temps écoulé (en secondes) :"
            timeInput <- getLine
            let maybeTime = readMaybe timeInput :: Maybe Double

            case (maybeDist, maybeTime) of
                (Just dist, Just t) -> 
                    if t == 0 
                        then putStrLn "Erreur : le temps ne peut pas être zéro."
                        else do
                            let vitesse = dist / t
                            putStrLn $ "Vitesse = " ++ show vitesse ++ " m/s"
                _ -> putStrLn "Erreur : saisie invalide. Veuillez entrer des nombres valides."
```

---

## 2️⃣ Explications

1. **`try (readFile fileName) :: IO (Either IOException String)`**

   * Tente de lire le fichier et capture une éventuelle exception (`IOException`).
   * Si lecture échoue → `Left ex`, sinon → `Right content`.

2. **`readMaybe`**

   * Convertit une chaîne en nombre de façon sécurisée.
   * Retourne `Nothing` si la conversion échoue.

3. **Vérification du temps = 0**

   * Evite une division par zéro.

4. Messages clairs pour **chaque type d’erreur** (fichier inexistant, saisie invalide, division par zéro).

---

## 3️⃣ Test

* Fichier existant → affiche le contenu et calcule la vitesse.
* Fichier inexistant → affiche une erreur.
* Saisie invalide ou temps = 0 → affiche un message d’erreur.
