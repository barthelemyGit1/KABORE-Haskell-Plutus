Tâche 2 : Signatures de fonctions
Écrire les signatures de fonctions suivantes :

Une fonction add qui prend deux Int et retourne leur somme.

Une fonction isEven qui prend un Int et retourne un Bool indiquant si le nombre est pair.

Une fonction concatStrings qui prend deux String et retourne leur concaténation.

Implémentez ces fonctions.

---

### ✅ 1. Fonction `add`

#### **Signature :**

```haskell
add :: Int -> Int -> Int
```

#### **Explication :**

* `add` est une fonction qui prend **deux entiers** (`Int`) en entrée.
* Elle retourne un **entier** en sortie.
* Le type `Int -> Int -> Int` signifie : "Prend un `Int`, retourne une fonction qui prend un `Int` et retourne un `Int`".
  (C'est ce qu'on appelle une **fonction curried** en Haskell.)

#### **Implémentation :**

```haskell
add x y = x + y
```

---

### ✅ 2. Fonction `isEven`

#### **Signature :**

```haskell
isEven :: Int -> Bool
```

#### **Explication :**

* `isEven` prend un entier (`Int`) et retourne un booléen (`Bool`) :

  * `True` si le nombre est pair
  * `False` sinon
* On utilise l’opérateur **modulo** (`mod`) pour vérifier si le reste de la division par 2 est égal à 0.

#### **Implémentation :**

```haskell
isEven n = n `mod` 2 == 0
```

*Remarque :* Les backticks \` \` autour de `mod` permettent de l'utiliser en notation **infixe** comme `n mod 2`.

---

### ✅ 3. Fonction `concatStrings`

#### **Signature :**

```haskell
concatStrings :: String -> String -> String
```

#### **Explication :**

* `concatStrings` prend **deux chaînes de caractères** (`String`) et retourne leur **concaténation**.
* En Haskell, `String` est juste une liste de caractères (`[Char]`).
* L'opérateur `(++)` permet de concaténer deux chaînes.

#### **Implémentation :**

```haskell
concatStrings s1 s2 = s1 ++ s2
```

---

### ✅ Code complet (copiable dans GHCi ou un fichier `.hs`) :

```haskell
-- Addition de deux entiers
add :: Int -> Int -> Int
add x y = x + y

-- Vérifie si un entier est pair
isEven :: Int -> Bool
isEven n = n `mod` 2 == 0

-- Concatène deux chaînes de caractères
concatStrings :: String -> String -> String
concatStrings s1 s2 = s1 ++ s2
```

---

### 🔍 Utilisation dans GHCi :

Lance GHCi dans ton terminal :

```bash
ghci
```

Puis colle les fonctions, et essaie des exemples :

```haskell
add 3 5
-- Résultat : 8

isEven 4
-- Résultat : True

isEven 7
-- Résultat : False

concatStrings "Hello, " "world!"
-- Résultat : "Hello, world!"
```

---
