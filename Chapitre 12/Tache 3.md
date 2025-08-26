## HC12T3 : Fonction factorielle

Créer un programme qui définit une fonction factorial pour calculer la factorielle d’un entier positif donné.

---

### Code haskell

```haskell
-- Fonction factorielle (récursive)
factorial :: Integer -> Integer
factorial 0 = 1
factorial n
  | n > 0     = n * factorial (n - 1)
  | otherwise = error "La factorielle n'est définie que pour les entiers positifs"

-- Programme principal
main :: IO ()
main = do
  let n = 5
  putStrLn ("La factorielle de " ++ show n ++ " est " ++ show (factorial n))
```

---

### 🔎 Explications

* `factorial 0 = 1` : condition de base.
* `factorial n = n * factorial (n - 1)` : définition récursive.
* La garde `| n > 0` assure que seuls les entiers positifs sont acceptés.
* `main` affiche le résultat de `factorial` pour un entier donné.

---

### ✅ Résultat attendu

```
La factorielle de 5 est 120
```


