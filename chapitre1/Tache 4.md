## ✅ Code complet avec `main`

```haskell
import Data.List (sortBy)
import Data.Ord (comparing)

-- 1. Extrait les noms des joueurs depuis une liste de tuples (nom, score)
extractPlayers :: [(String, Int)] -> [String]
extractPlayers players = [name | (name, _) <- players]

-- 2. Trie la liste de joueurs par score décroissant
sortByScore :: [(String, Int)] -> [(String, Int)]
sortByScore = sortBy (flip (comparing snd))

-- 3. Prend les 3 premiers joueurs de la liste triée
topThree :: [(String, Int)] -> [(String, Int)]
topThree = take 3

-- 4. Compose toutes les fonctions : trie, sélectionne les 3 meilleurs, puis extrait les noms
getTopThreePlayers :: [(String, Int)] -> [String]
getTopThreePlayers = extractPlayers . topThree . sortByScore

-- 5. Fonction principale
main :: IO ()
main = do
    let players = [("Alice", 45), ("Bob", 90), ("Charlie", 75), ("Diana", 85), ("Eve", 60)]
    putStrLn "Top 3 joueurs :"
    print (getTopThreePlayers players)
```

---

## 🧠 Explication détaillée

---

### `extractPlayers :: [(String, Int)] -> [String]`

* Prend une liste de tuples (nom, score).
* Utilise une **liste en compréhension** pour extraire uniquement les noms :

  ```haskell
  [name | (name, _) <- players]
  ```

---

### `sortByScore :: [(String, Int)] -> [(String, Int)]`

* Trie la liste par **score décroissant** :

  * `comparing snd` trie par le second élément du tuple (le score).
  * `flip` inverse l’ordre pour avoir un **tri décroissant**.

---

### `topThree :: [(String, Int)] -> [(String, Int)]`

* Récupère les 3 premiers joueurs de la liste triée avec `take 3`.

---

### `getTopThreePlayers = extractPlayers . topThree . sortByScore`

* C’est une **composition de fonctions** :

  1. Trie la liste.
  2. Prend les 3 premiers.
  3. Extrait les noms.

> C’est équivalent à :

```haskell
getTopThreePlayers players = extractPlayers (topThree (sortByScore players))
```

---

### `main :: IO ()`

* Crée une liste de joueurs (`players`) avec leurs scores.
* Appelle `getTopThreePlayers` sur cette liste.
* Affiche le résultat avec `print`.

---

### ✅ Résultat attendu à l'exécution :

```
Top 3 joueurs :
["Bob","Diana","Charlie"]
```

---
