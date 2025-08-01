### ✅ Code Haskell

```haskel
-- Vérifie si un nombre est supérieur à 18
greaterThan18 :: Int -> Bool
greaterThan18 x = x > 18

-- Fonction principale
main :: IO ()
main = do
    print (greaterThan18 20)   -- Affiche True
    print (greaterThan18 18)   -- Affiche False
    print (greaterThan18 10)   -- Affiche False
```

---

## 🧠 Explication ligne par ligne

### `greaterThan18 :: Int -> Bool`

* **Signature de type** :

  * La fonction prend un entier (`Int`) en entrée.
  * Elle retourne une valeur booléenne (`Bool`) — soit `True`, soit `False`.

---

### `greaterThan18 x = x > 18`

* **Définition** :

  * On compare la valeur `x` avec `18` à l’aide de l’opérateur `>`.
  * Le résultat est `True` si `x` est strictement supérieur à 18, sinon `False`.

---

## ✅ Exemples dans GHCi

```haskell
ghci> greaterThan18 20
True

ghci> greaterThan18 18
False

ghci> greaterThan18 10
False
```

---

## 💡 Variante générique (si tu veux aussi travailler avec `Float` ou `Double`) :

```haskell
greaterThan18 :: (Ord a, Num a) => a -> Bool
greaterThan18 x = x > 18
```

* Cela permet d’utiliser la fonction avec n’importe quel **type numérique comparable**.

```haskell
ghci> greaterThan18 18.5
True
```

---
