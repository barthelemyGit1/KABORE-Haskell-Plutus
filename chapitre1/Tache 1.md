HC1T1 - Tâche 1 : Composition de fonctions

---
### ✅ Code Haskell

```haskel
-- Multiplie un nombre par 2

double :: Int -> Int
double x = x * 2

-- Augmente un nombre de 1

increment :: Int -> Int
increment x = x + 1

-- Applique double puis increment en utilisant la composition de fonctions

doubleThenIncrement :: Int -> Int
doubleThenIncrement = increment . double


-- Fonction principale

main :: IO ()
main = do
   
    print (double 5) --Affiche 10
    print (increment 9) --Affiche 10
    print (doubleThenIncrement 5) --Affiche 11
```
---

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

### `main = do`

* Le mot-clé **`do`** permet d’écrire une **séquence d’actions IO**.
* Chaque ligne dans le bloc `do` est une action exécutée dans l’ordre.

---

### `print (double 5)`

* Appelle la fonction `double` avec 5 :

  * `double 5` = `5 * 2` = `10`
* Ensuite, `print 10` affiche `10` dans le terminal.

---

### `print (increment 9)`

* Appelle `increment` avec 9 :

  * `increment 9` = `9 + 1` = `10`
* Affiche donc `10`.

---

### `print (doubleThenIncrement 5)`

* `doubleThenIncrement` est défini comme `increment . double`

  * Ce qui signifie : `increment (double 5)`
  * `double 5` = `10`
  * `increment 10` = `11`
* Affiche donc `11`.

---

## ✅ Résultat à l’écran quand tu exécutes :

```
10
10
11
```


### ✅ Exemple dans GHCi :

```haskell
ghci> double 4
8

ghci> increment 4
5

ghci> doubleThenIncrement 4
9
```
