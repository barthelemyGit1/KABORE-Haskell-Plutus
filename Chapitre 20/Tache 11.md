## HC20T11 : randomWalk avec la monade State

Écrire une fonction randomWalk utilisant la monade State qui simule une marche aléatoire sur une grille 2D.

---

### Code haskell

```haskell
{-# LANGUAGE TupleSections #-}

import System.Random
import Control.Monad.State

-- Type pour représenter la position sur la grille
type Position = (Int, Int)

-- Les directions possibles
data Direction = North | South | East | West
  deriving (Show, Enum, Bounded)

-- Génère une direction aléatoire
randomDirection :: State StdGen Direction
randomDirection = do
  gen <- get
  let (i, gen') = randomR (fromEnum (minBound :: Direction),
                           fromEnum (maxBound :: Direction)) gen
  put gen'
  return (toEnum i)

-- Déplace une position selon une direction
move :: Position -> Direction -> Position
move (x, y) North = (x, y + 1)
move (x, y) South = (x, y - 1)
move (x, y) East  = (x + 1, y)
move (x, y) West  = (x - 1, y)

-- Effectue un pas de marche aléatoire
step :: Position -> State StdGen Position
step pos = do
  dir <- randomDirection
  return (move pos dir)

-- Simule n étapes de marche aléatoire
randomWalk :: Int -> Position -> State StdGen [Position]
randomWalk n start = go n start
  where
    go 0 p = return [p]
    go k p = do
      p'  <- step p
      ps  <- go (k - 1) p'
      return (p : ps)

-- ----------- Programme principal -----------
main :: IO ()
main = do
  putStrLn "== Marche aléatoire sur une grille 2D =="
  gen <- getStdGen
  let positions = evalState (randomWalk 10 (0,0)) gen
  mapM_ print positions
```

---

## Explications

#### 1️⃣ **Types de base**

* `Position = (Int, Int)` : coordonnées sur la grille.
* `Direction` : quatre directions cardinales.

---

#### 2️⃣ **La monade `State`**

* On utilise `State StdGen` pour transporter un générateur aléatoire `StdGen`.
* Chaque fois qu’on génère un nombre aléatoire, on met à jour l’état (`put gen'`).

---

#### 3️⃣ **Les fonctions clés**

* `randomDirection` : tire un nombre au hasard dans `[0..3]` puis le convertit en `Direction`.
* `move` : calcule la nouvelle position en fonction de la direction.
* `step` : combine les deux précédentes pour faire **un pas**.

---

#### 4️⃣ **`randomWalk`**

* Fonction récursive qui :

  1. Arrête si `n == 0`.
  2. Sinon, effectue `step`, puis continue avec `n - 1`.

> Elle retourne la **liste des positions** visitées, en commençant par la position initiale.

---

#### 5️⃣ **`main`**

* Récupère un générateur aléatoire avec `getStdGen`.
* Exécute `randomWalk` via `evalState`.
* Affiche toutes les positions.

---

### Exemple de sortie

```
== Marche aléatoire sur une grille 2D ==
(0,0)
(1,0)
(1,-1)
(1,-2)
(0,-2)
(0,-1)
(0,0)
(-1,0)
(-1,-1)
(-2,-1)
(-3,-1)
```

> Chaque exécution produira un trajet différent 🚶‍♂️

---

💡 **Résumé :**

* `State` garde le générateur aléatoire entre les étapes.
* On sépare bien : génération aléatoire, déplacement, et accumulation des positions.
* Ce modèle peut facilement être étendu (limites de grille, obstacles, etc.).
