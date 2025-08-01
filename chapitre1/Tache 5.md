## ✅ Code Haskell complet

```haskell
-- Génère une liste infinie de nombres à partir de 1
infiniteNumbers :: [Int]
infiniteNumbers = [1..]

-- Extrait les n premiers éléments d'une liste
firstN :: Int -> [Int] -> [Int]
firstN n xs = take n xs

-- Fonction principale
main :: IO ()
main = do
    let n = 10
    putStrLn ("Les " ++ show n ++ " premiers nombres de la liste infinie :")
    print (firstN n infiniteNumbers)
```

---

## 🧠 Explication détaillée

---

### `infiniteNumbers :: [Int]`

* C’est une **liste infinie** générée par la notation `[1..]`.
* Cela signifie : 1, 2, 3, 4, 5, ..., sans fin.
* Grâce à l’**évaluation paresseuse (lazy evaluation)** de Haskell, cette liste ne cause **aucun blocage ou crash** tant qu’on n’en demande qu’une partie.

---

### `firstN :: Int -> [Int] -> [Int]`

* Fonction qui prend un nombre `n` et une liste, et retourne les `n` premiers éléments.
* Elle utilise la fonction standard `take` :

  ```haskell
  take 5 [1..] → [1,2,3,4,5]
  ```

---

### `main :: IO ()`

* Définit `n = 10`.
* Affiche un message informatif.
* Appelle `firstN n infiniteNumbers` pour obtenir les 10 premiers éléments de la liste infinie.
* Utilise `print` pour les afficher à l’écran.

---

## ▶️ Résultat attendu à l’exécution :

```
Les 10 premiers nombres de la liste infinie :
[1,2,3,4,5,6,7,8,9,10]
```

---
