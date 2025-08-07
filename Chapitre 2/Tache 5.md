## Tâche 5 : Définir et utiliser des fonctions

Écrire une fonction circleArea qui prend un rayon (Float) et retourne l’aire du cercle.

Écrire une fonction maxOfThree qui prend trois Int et retourne la valeur maximale.

Testez vos fonctions avec différentes entrées.

---

## ✅ 1. Fonction `circleArea`

### 🔹 But :

Calculer l'aire d'un cercle à partir de son **rayon**.

---

### ✅ Signature de type :

```haskell
circleArea :: Float -> Float
```

* Elle prend un **Float** (le rayon)
* Elle retourne un **Float** (l'aire)

---

### ✅ Formule :

> Aire = π × r²
> En Haskell : `pi * r * r`

---

### ✅ Implémentation :

```haskell
circleArea r = pi * r * r
```

---

### ✅ Explication :

* `pi` est une **constante prédéfinie** dans Haskell (approximée à `3.1415927`)
* `r` est l’argument (le rayon)
* On multiplie `pi * r * r` pour obtenir l’aire

---

### ✅ Exemples de test :

```haskell
circleArea 1.0     -- Résultat : 3.1415927
circleArea 2.5     -- Résultat : 19.634954
circleArea 0       -- Résultat : 0.0
```

---

## ✅ 2. Fonction `maxOfThree`

### 🔹 But :

Trouver le **maximum** de trois entiers.

---

### ✅ Signature de type :

```haskell
maxOfThree :: Int -> Int -> Int -> Int
```

* Elle prend **trois entiers**
* Elle retourne l'entier **le plus grand**

---

### ✅ Implémentation :

```haskell
maxOfThree a b c = max a (max b c)
```

---

### ✅ Explication :

* La fonction `max` existe déjà en Haskell : `max x y` retourne le plus grand des deux.
* On utilise `max b c` d'abord, puis on compare `a` à ce résultat.
* Autrement dit :

  ```haskell
  maxOfThree a b c = max a (max b c)
  ```

  équivaut à :

  ```haskell
  if a >= b && a >= c then a
  else if b >= c then b
  else c
  ```

---

### ✅ Exemples de test :

```haskell
maxOfThree 1 2 3     -- Résultat : 3
maxOfThree 10 5 7    -- Résultat : 10
maxOfThree 4 9 2     -- Résultat : 9
maxOfThree 3 3 3     -- Résultat : 3
```

---

## 📄 Code complet à copier :

```haskell
-- Calcule l'aire d'un cercle à partir de son rayon
circleArea :: Float -> Float
circleArea r = pi * r * r

-- Retourne le maximum de trois entiers
maxOfThree :: Int -> Int -> Int -> Int
maxOfThree a b c = max a (max b c)
```

---

## ✅ Utilisation dans GHCi :

Lance GHCi (`ghci` dans ton terminal), puis :

```haskell
:load MonFichier.hs   -- si tu as mis les fonctions dans un fichier
-- ou directement :
circleArea 3.0
maxOfThree 4 1 9
```

---
