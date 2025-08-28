## HC12T8 : Fusionner deux listes triées

Définir une fonction mergeLists qui fusionne deux listes triées en une seule liste triée. Utiliser la fonction main pour tester cette fonctionnalité.

---

### Code haskell

```haskell
-- Fonction pour fusionner deux listes triées
mergeLists :: Ord a => [a] -> [a] -> [a]
mergeLists [] ys = ys
mergeLists xs [] = xs
mergeLists (x:xs) (y:ys)
    | x <= y    = x : mergeLists xs (y:ys)
    | otherwise = y : mergeLists (x:xs) ys

-- Fonction principale pour tester
main :: IO ()
main = do
    putStrLn "Entrez la première liste triée (entiers séparés par des espaces) :"
    input1 <- getLine
    putStrLn "Entrez la deuxième liste triée (entiers séparés par des espaces) :"
    input2 <- getLine

    let list1 = map read (words input1) :: [Int]
    let list2 = map read (words input2) :: [Int]

    let merged = mergeLists list1 list2
    putStrLn $ "Liste fusionnée et triée : " ++ show merged
```

---

### Explications :

1. **`mergeLists`** :

   * Cas de base : si une liste est vide, on retourne l’autre.
   * Cas récursif : on compare les têtes `x` et `y` et on met le plus petit en tête, puis on appelle récursivement sur le reste.

2. **`main`** :

   * Lit deux listes triées depuis l’utilisateur.
   * Convertit les chaînes en listes d’entiers.
   * Affiche la liste fusionnée.

---
