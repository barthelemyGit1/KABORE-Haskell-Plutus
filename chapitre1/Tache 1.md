HC1T1 - Tâche 1 : Composition de fonctions


### ✅ Code Haskell

-- Multiplie un nombre par 2
double :: Int -> Int
double x = x * 2

-- Augmente un nombre de 1
increment :: Int -> Int
increment x = x + 1

-- Applique double puis increment en utilisant la composition de fonctions
doubleThenIncrement :: Int -> Int
doubleThenIncrement = increment . double



### 🧠 Explication ligne par ligne :

#### 1. `double :: Int -> Int`

* **Signature** : Prend un `Int` (entier) et retourne un `Int`.
* **Implémentation** : `double x = x * 2`

  * Multiplie `x` par 2.


#### 2. `increment :: Int -> Int`

* **Signature** : Prend un `Int` et retourne un `Int`.
* **Implémentation** : `increment x = x + 1`

  * Ajoute 1 à `x`.


#### 3. `doubleThenIncrement :: Int -> Int`

* **Signature** : Prend un `Int` et retourne un `Int`.
* **Implémentation** : `doubleThenIncrement = increment . double`

  * Ici, on utilise **la composition de fonctions** avec l'opérateur `.`.
  * Cela signifie :
    `doubleThenIncrement x = increment (double x)`
    donc on applique `double`, puis on applique `increment` sur le résultat.


### ✅ Exemple dans GHCi :

```haskell
ghci> double 4
8

ghci> increment 4
5

ghci> doubleThenIncrement 4
9
```
