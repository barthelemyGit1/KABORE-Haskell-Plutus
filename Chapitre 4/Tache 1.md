## HC1T1 - Tâche 1 : Composition de fonctions

double : Multiplie un nombre par 2.

increment : Augmente un nombre de 1.

doubleThenIncrement : Utilise la composition de fonctions pour appliquer double puis increment.

```
-- Multiplie un nombre par 2
double :: Int -> Int
double x = x * 2

-- Augmente un nombre de 1
increment :: Int -> Int
increment x = x + 1

-- Utilise la composition de fonctions : d'abord double, puis increment
doubleThenIncrement :: Int -> Int
doubleThenIncrement = increment . double
```

✅ Explication :

* `double x` → multiplie `x` par 2.
* `increment x` → ajoute 1 à `x`.
* `increment . double` → signifie "appliquer `double`, puis appliquer `increment`".

👉 Exemple en GHCi :

```haskell
doubleThenIncrement 3
-- Résultat : 7   (car (3*2) + 1 = 7)
```
