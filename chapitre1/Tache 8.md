## ✅ Code Haskell complet

```haskell
-- Applique une fonction deux fois à une valeur
applyTwice :: (a -> a) -> a -> a
applyTwice f x = f (f x)

-- Exemple : fonction qui double un entier
double :: Int -> Int
double x = x * 2

-- Fonction principale
main :: IO ()
main = do
    let value = 3
    let result = applyTwice double value
    putStrLn ("Appliquer deux fois 'double' à " ++ show value ++ " donne : " ++ show result)
```

---

## 🧠 Explication détaillée

---

### `applyTwice :: (a -> a) -> a -> a`

* C’est la **signature de type** :

  * `(a -> a)` : une fonction qui prend un `a` et retourne un `a`.
  * `a` : une valeur de type quelconque.
  * En résumé, `applyTwice` prend :

    1. une fonction `f`,
    2. une valeur `x`,
    3. applique `f` deux fois sur `x`.

---

### `applyTwice f x = f (f x)`

* C’est la définition :

  * Applique `f` une première fois sur `x`, puis encore une fois sur le résultat.
  * Ex : `applyTwice double 3` → `double (double 3)` → `double 6` → `12`

---

### `double :: Int -> Int`

* Exemple de fonction simple : double une valeur entière.
* `double 3` → `6`

---

### `main :: IO ()`

* Fonction principale.

---

### Dans `main` :

```haskell
let value = 3
let result = applyTwice double value
```

* Définit `value = 3`
* Calcule `applyTwice double 3` → `double (double 3)` → `12`

```haskell
putStrLn ("Appliquer deux fois 'double' à " ++ show value ++ " donne : " ++ show result)
```

* Affiche :

  ```
  Appliquer deux fois 'double' à 3 donne : 12
  ```

---

## 🔄 Autres exemples que tu peux tester dans GHCi

```haskell
applyTwice (+1) 4     -- Résultat : 6
applyTwice (subtract 2) 10  -- Résultat : 6
```

---
