## HC15T3 : Définir et lancer une exception personnalisée pour les feux

Définir et lancer une exception personnalisée pour les erreurs de feux tricolores.

---

## 1️⃣ Code Haskell : exception personnalisée

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

-- Fonction qui retourne l'action de la voiture ou lève une exception
reagirAuFeu :: CouleurFeu -> String
reagirAuFeu Rouge  = "Stop !"
reagirAuFeu Orange = "Préparez-vous à arrêter"
reagirAuFeu Vert   = "Avancez"

-- Lecture sécurisée et levée d'exception si invalide
parseCouleur :: String -> CouleurFeu
parseCouleur s =
    case reads s of
        [(c,"")] -> c
        _        -> throw (CouleurInvalide s)

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez la couleur du feu (Rouge, Orange, Vert) :"
    couleurStr <- getLine
    -- On attrape l'exception pour éviter le crash
    resultat <- try (evaluate (parseCouleur couleurStr)) :: IO (Either FeuException CouleurFeu)
    case resultat of
        Right couleur -> putStrLn $ "Action de la voiture : " ++ reagirAuFeu couleur
        Left (CouleurInvalide s) -> putStrLn $ "Erreur : couleur invalide '" ++ s ++ "'"
```

---

## 2️⃣ Explications

1. **`FeuException`**

   * Type de données pour représenter une exception personnalisée.
   * On dérive `Show` pour pouvoir afficher le message.
   * On instancie `Exception` pour qu’il soit lançable via `throw`.

2. **`parseCouleur`**

   * Tente de lire la couleur depuis la saisie utilisateur.
   * Si la lecture échoue, on lance `CouleurInvalide`.

3. **Gestion avec `try` et `evaluate`**

   * `try (evaluate ...)` capture l’exception sans faire planter le programme.
   * `Either FeuException CouleurFeu` permet de distinguer succès et erreur.

4. **Exemple d’exécution**

```
Entrez la couleur du feu (Rouge, Orange, Vert) :
Bleu
Erreur : couleur invalide 'Bleu'
```

```
Entrez la couleur du feu (Rouge, Orange, Vert) :
Vert
Action de la voiture : Avancez
```
