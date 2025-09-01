## HC19T3 : Fonction safeProduct pour Maybe Int

Définir une fonction safeProduct qui calcule le produit d’une liste de Maybe Int et retourne Nothing si une valeur est Nothing.

---

### 1. Type de la fonction

```haskell
safeProduct :: [Maybe Int] -> Maybe Int
```

---

### 2. Idée

* Si tous les éléments sont `Just n`, alors on calcule le produit et on retourne `Just result`.
* S’il y a au moins un `Nothing`, on retourne `Nothing`.

En Haskell, ça ressemble à une **séquence** d’actions `Applicative`.

---

### 3. Implémentation avec `sequence`

```haskell
safeProduct :: [Maybe Int] -> Maybe Int
safeProduct xs = fmap product (sequence xs)
```

#### Explication :

* `sequence :: [Maybe a] -> Maybe [a]`

  * transforme une liste de `Maybe` en un `Maybe` qui contient la liste de valeurs.
  * Si un seul `Nothing` est présent → résultat = `Nothing`.
* Ensuite `fmap product` applique la fonction `product` (multiplication de tous les `Int`) au contenu si c’est `Just`.

---

### 4. Exemples d’utilisation

```haskell
main :: IO ()
main = do
  print $ safeProduct [Just 2, Just 3, Just 4]
  -- Just 24

  print $ safeProduct [Just 5, Nothing, Just 7]
  -- Nothing

  print $ safeProduct []
  -- Just 1   (car product [] = 1)
```

---

### 5. Variante avec `foldM` (style monadique)

Une autre manière d’écrire :

```haskell
import Control.Monad (foldM)

safeProduct :: [Maybe Int] -> Maybe Int
safeProduct = foldM (\acc x -> Just (acc * x)) 1
```
