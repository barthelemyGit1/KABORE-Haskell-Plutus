## HC15T7 : Calcul de vitesse avec gestion des valeurs optionnelles et du parsing

Implémenter un programme qui calcule une vitesse en utilisant des valeurs optionnelles et gère les erreurs de parsing.

---

* Utiliser `readMaybe` pour parser la saisie utilisateur.
* Manipuler les résultats avec `Maybe` (`Just` / `Nothing`).
* Effectuer le calcul de vitesse (distance / temps).
* Gérer les erreurs (parsing invalide ou division par zéro).

---

## ✅ Code Haskell : Calcul de vitesse avec `Maybe`

```haskell
module Main where

import Text.Read (readMaybe)

-- Division sécurisée avec Maybe
safeDiv :: Double -> Double -> Maybe Double
safeDiv _ 0 = Nothing
safeDiv x y = Just (x / y)

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez la distance (en km) :"
    distStr <- getLine
    putStrLn "Entrez le temps (en heures) :"
    timeStr <- getLine

    -- Parsing des entrées
    let maybeDist = readMaybe distStr :: Maybe Double
        maybeTime = readMaybe timeStr :: Maybe Double

    case (maybeDist, maybeTime) of
        (Just d, Just t) ->
            case safeDiv d t of
                Just v  -> putStrLn $ "Vitesse = " ++ show v ++ " km/h"
                Nothing -> putStrLn "Erreur : division par zéro (temps = 0)"
        _ -> putStrLn "Erreur : entrée invalide (veuillez entrer des nombres valides)."
```

---

## ⚡ Explications

1. `readMaybe` sécurise le parsing :

   * `"42"` → `Just 42.0`
   * `"abc"` → `Nothing`

2. `safeDiv` empêche la division par zéro :

   * `safeDiv 100 2` → `Just 50.0`
   * `safeDiv 100 0` → `Nothing`

3. `case` permet de traiter les différentes combinaisons de valeurs (`Just` ou `Nothing`).

---

## 📌 Exemple d’exécution

```
Entrez la distance (en km) :
100
Entrez le temps (en heures) :
2
Vitesse = 50.0 km/h
```

```
Entrez la distance (en km) :
100
Entrez le temps (en heures) :
0
Erreur : division par zéro (temps = 0)
```

```
Entrez la distance (en km) :
abc
Entrez le temps (en heures) :
2
Erreur : entrée invalide (veuillez entrer des nombres valides).
```
