## HC15T2 : Système basique de voiture autonome réagissant aux feux tricolores

Implémenter un système d’IA de voiture autonome basique qui réagit aux couleurs des feux tricolores.

---

## 1️⃣ Code Haskell : voiture autonome basique

```haskell
module Main where

import System.IO

-- Définition des couleurs possibles du feu
data CouleurFeu = Rouge | Orange | Vert
    deriving (Show, Read, Eq)

-- Fonction qui retourne l'action de la voiture selon la couleur du feu
reagirAuFeu :: CouleurFeu -> String
reagirAuFeu Rouge  = "Stop !"
reagirAuFeu Orange = "Préparez-vous à arrêter"
reagirAuFeu Vert   = "Avancez"

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez la couleur du feu (Rouge, Orange, Vert) :"
    couleurStr <- getLine
    let maybeCouleur = safeRead couleurStr :: Maybe CouleurFeu
    case maybeCouleur of
        Just couleur -> putStrLn $ "Action de la voiture : " ++ reagirAuFeu couleur
        Nothing      -> putStrLn "Erreur : couleur invalide. Veuillez entrer Rouge, Orange ou Vert."

-- Fonction de lecture sécurisée pour les données Read
safeRead :: Read a => String -> Maybe a
safeRead s = case reads s of
    [(x,"")] -> Just x
    _        -> Nothing
```

---

## 2️⃣ Explications

1. **Type `CouleurFeu`**

   * Définit les valeurs possibles du feu : `Rouge`, `Orange`, `Vert`.

2. **`reagirAuFeu`**

   * Retourne l’action à effectuer selon la couleur.

3. **Lecture sécurisée de l’entrée utilisateur**

   * `safeRead` évite que le programme plante si l’utilisateur entre un texte invalide.

4. **Exemple d’exécution**

```
Entrez la couleur du feu (Rouge, Orange, Vert) :
Vert
Action de la voiture : Avancez
```
