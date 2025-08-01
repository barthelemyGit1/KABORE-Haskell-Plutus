## ✅ Code Haskell complet

```haskell
-- Définit une fonction qui additionne deux entiers
addNumbers :: Int -> Int -> Int
addNumbers x y = x + y

-- Fonction principale
main :: IO ()
main = do
    let a = 7
    let b = 5
    let result = addNumbers a b
    putStrLn ("La somme de " ++ show a ++ " et " ++ show b ++ " est : " ++ show result)
```

---

## 🧠 Explication ligne par ligne

---

### `addNumbers :: Int -> Int -> Int`

* C’est la **signature de type** de la fonction :

  * Elle prend **deux entiers** (`Int`) en entrée.
  * Elle retourne **un entier** (`Int`) en sortie.

---

### `addNumbers x y = x + y`

* C’est la **définition** de la fonction :

  * Elle retourne la somme des deux arguments `x` et `y`.

---

### `main :: IO ()`

* C’est la **fonction principale** du programme (point d’entrée).
* Elle contient des **actions IO** comme `putStrLn` (afficher à l’écran).

---

### Dans `main` :

```haskell
let a = 7
let b = 5
```

* On définit deux entiers `a` et `b`.

```haskell
let result = addNumbers a b
```

* On calcule la somme en appelant la fonction `addNumbers`.

```haskell
putStrLn ("La somme de " ++ show a ++ " et " ++ show b ++ " est : " ++ show result)
```

* On affiche le résultat à l’écran.
* `show` convertit les nombres en chaînes de caractères pour l’affichage.

---

## ▶️ Résultat attendu à l’exécution :

```
La somme de 7 et 5 est : 12
```

---
