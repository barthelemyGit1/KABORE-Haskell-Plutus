## HC15T4 : Utiliser une fonction de gestion d’exception pour les feux

Utiliser une fonction gestionnaire pour intercepter et gérer les exceptions liées aux feux tricolores.

---

## 1️⃣ Code complet avec gestionnaire d’exception

```haskell
module Main where

import Control.Exception
import System.IO

-- Définition des couleurs possibles du feu
data CouleurFeu = Rouge | Orange | Vert
    deriving (Show, Read, Eq)

-- Définition d'une exception personnalisée
data FeuException = CouleurInvalide String
    deriving (Show)

instance Exception FeuException

-- Fonction qui retourne l'action de la voiture
reagirAuFeu :: CouleurFeu -> String
reagirAuFeu Rouge  = "Stop !"
reagirAuFeu Orange = "Préparez-vous à arrêter"
reagirAuFeu Vert   = "Avancez"

-- Lecture et levée d’exception si couleur invalide
parseCouleur :: String -> IO CouleurFeu
parseCouleur s =
    case reads s of
        [(c,"")] -> return c
        _        -> throwIO (CouleurInvalide s)   -- ⚡ exception IO

-- Gestionnaire d’exception
gestionnaireFeu :: FeuException -> IO ()
gestionnaireFeu (CouleurInvalide s) =
    putStrLn $ "Erreur : '" ++ s ++ "' n'est pas une couleur valide. Réessayez avec Rouge, Orange ou Vert."

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez la couleur du feu (Rouge, Orange, Vert) :"
    couleurStr <- getLine
    -- Ici, on utilise catch pour gérer les exceptions
    (parseCouleur couleurStr >>= \c ->
        putStrLn $ "Action de la voiture : " ++ reagirAuFeu c)
        `catch` gestionnaireFeu
```

---

## 2️⃣ Explications

* **`throwIO`** : lance une exception dans l’espace `IO` (plus sûr que `throw` dans ce contexte).
* **`catch gestionnaireFeu`** : intercepte uniquement les exceptions de type `FeuException`.
* **`gestionnaireFeu`** : affiche un message personnalisé au lieu de planter.

---

## 3️⃣ Exemple d’exécution

```
Entrez la couleur du feu (Rouge, Orange, Vert) :
Bleu
Erreur : 'Bleu' n'est pas une couleur valide. Réessayez avec Rouge, Orange ou Vert.
```

```
Entrez la couleur du feu (Rouge, Orange, Vert) :
Rouge
Action de la voiture : Stop !
```

---

👉 Différence avec **HC15T3** :

* Dans HC15T3 on utilisait `try` + `Either`.
* Ici, avec **HC15T4**, on centralise la gestion des exceptions avec une **fonction gestionnaire** (`catch`).
