## HC19T5 : Fonction applyEffects avec <*>

Implémenter la fonction applyEffects avec <*> qui prend un tuple (IO Int, IO Int) et fait la somme des valeurs tout en les affichant.

---

### 1. Type attendu

On veut une fonction qui prend un tuple `(IO Int, IO Int)` et retourne une action `IO Int`.

```haskell
applyEffects :: (IO Int, IO Int) -> IO Int
```

---

### 2. Idée

* `(<$>)` permet d’appliquer une fonction normale à une valeur dans `IO`.
* `(<*>)` permet d’appliquer une fonction dans `IO` à une valeur dans `IO`.
* Donc on peut utiliser :

  ```haskell
  (\x y -> x + y) <$> io1 <*> io2
  ```

---

### 3. Implémentation

```haskell
applyEffects :: (IO Int, IO Int) -> IO Int
applyEffects (io1, io2) = (\x y -> x + y) <$> io1 <*> io2
```

---

### 4. Exemple d’utilisation

```haskell
main :: IO ()
main = do
  let a = do putStrLn "Entrez un nombre A:"; readLn :: IO Int
  let b = do putStrLn "Entrez un nombre B:"; readLn :: IO Int

  result <- applyEffects (a, b)
  putStrLn $ "La somme est: " ++ show result
```

---

### 5. Explication

* `a` et `b` sont des actions `IO Int` qui demandent une saisie utilisateur.
* `applyEffects (a, b)` combine ces deux actions :

  1. Exécute `a` et récupère un entier `x`.
  2. Exécute `b` et récupère un entier `y`.
  3. Calcule `x + y`.
* Le tout reste dans `IO`, donc on peut afficher la somme ensuite.
