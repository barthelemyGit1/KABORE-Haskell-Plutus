## HC10T2 : Classe de type Summable

Créer une classe de type Summable qui fournit sumUp :: [a] -> a.

L’implémenter pour le type Int.

---

### Code Haskell :

```haskell
-- Définition de la classe de type Summable
class Summable a where
  sumUp :: [a] -> a

-- Implémentation de Summable pour Int
instance Summable Int where
  sumUp = foldr (+) 0

-- Exemples d'utilisation
main :: IO ()
main = do
  print (sumUp [1,2,3,4,5])  -- 15
  print (sumUp [])           -- 0
```

---

### 🔎 Explications

* `class Summable a where sumUp :: [a] -> a` : définit une **interface** qui exige une fonction pour sommer une liste de valeurs du type `a`.
* `instance Summable Int where sumUp = foldr (+) 0` :

  * `foldr (+) 0` additionne tous les éléments de la liste.
  * Si la liste est vide, le résultat est `0`.
* On peut ensuite utiliser `sumUp` sur n’importe quelle liste d’`Int`.

---

### ✅ Résultat attendu

```
15
0
```
