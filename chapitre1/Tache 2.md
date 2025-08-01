### ✅ Code Haskell :

```haskell

-- Calcule de l'aire du cercle
circleArea :: Floating a => a -> a
circleArea r = pi * r * r



-- Fonction principale

main :: IO ()
main = do
   
    print (circleArea 5) --Affiche 10
```

---

### 🔢 Ton code :

```haskell
-- Fonction principale
main :: IO ()
main = do
    print (circleArea 5) -- Affiche 78.53981633974483
```

---

### Fonction principale`

* C’est un **commentaire**. Il est ignoré par Haskell.
* Sert uniquement à expliquer que le code ci-dessous correspond à la fonction principale du programme.

---

### `main :: IO ()`

* **Signature de type** de la fonction `main`.
* Cela signifie que `main` est une **action d’entrée/sortie** (IO = Input/Output), qui **ne renvoie aucune valeur utile** (`()` = vide).
* En Haskell, tout programme commence par exécuter la fonction `main`.

---

### `main = do`

* Le mot-clé `do` permet d’exécuter **plusieurs actions IO successives** (afficher, lire clavier, écrire fichier, etc.).
* C’est un **bloc d’instructions IO**.

---

### `print (circleArea 5)`

* Appelle d’abord la fonction `circleArea` avec l’argument `5` :

  * **`circleArea 5` = `pi * 5 * 5` = `78.5398...`**
* Ensuite, la fonction `print` affiche ce résultat à l’écran :

  ```haskell
  print 78.53981633974483
  ```
  
---

## ✅ Résultat à l’écran :

```bash
78.53981633974483
```

---

## 🔍 Explication détaillée

### `circleArea :: Floating a => a -> a`

* **Signature de type** :

  * La fonction prend un argument `r` (le rayon) de type `a` et retourne aussi un `a`.
  * La contrainte `Floating a =>` signifie que `a` doit être un type **flottant** (`Float`, `Double`, etc.) car on utilise `pi`.

---

### `circleArea r = pi * r * r`

* C’est la définition de la fonction :

  * `pi` est une constante prédéfinie en Haskell (≈ 3.14159...).
  * L’aire du cercle est définie par la formule : **A = π × r²**
  * En Haskell : `pi * r * r` correspond à `π × r × r`.

---

## ✅ Exemples dans GHCi

```haskell
ghci> circleArea 3
28.274333882308138

ghci> circleArea 5.5
95.03317777109125
```

---

## 🎯 Pourquoi cette fonction est **pure** ?

* Elle **ne lit ni n’écrit** de fichiers, d’écran, ou d’état global.
* Elle **ne dépend que de son entrée** (`r`) et **donne toujours le même résultat** pour une même entrée.
* Elle **ne provoque aucun effet de bord**.

> 💡 En Haskell, **toute fonction sans `IO` dans son type est pure par défaut**.

---

