## HC12T4 : Premiers 10 nombres de Fibonacci

Écrire un programme qui calcule et affiche les 10 premiers nombres de Fibonacci en utilisant la récursion.

---

### Code haskell
```haskell
-- Fonction récursive pour calculer le n-ième nombre de Fibonacci
fibonacci :: Int -> Int
fibonacci 0 = 0
fibonacci 1 = 1
fibonacci n = fibonacci (n - 1) + fibonacci (n - 2)

-- Programme principal
main :: IO ()
main = do
  let n = 10
      fibNumbers = [fibonacci i | i <- [0..(n-1)]]
  putStrLn ("Les " ++ show n ++ " premiers nombres de Fibonacci sont :")
  print fibNumbers
```

---

### 🔎 Explications

* `fibonacci 0 = 0` et `fibonacci 1 = 1` : conditions de base.
* `fibonacci n = fibonacci (n-1) + fibonacci (n-2)` : définition récursive.
* `[fibonacci i | i <- [0..(n-1)]]` : génère la liste des `n` premiers nombres de Fibonacci.
* `print fibNumbers` affiche la liste complète.

---

### ✅ Résultat attendu

```
Les 10 premiers nombres de Fibonacci sont :
[0,1,1,2,3,5,8,13,21,34]
```
