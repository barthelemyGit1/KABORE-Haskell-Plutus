## HC10T8 : Sous-classe AdvancedEq de Eq

Définir une sous-classe AdvancedEq de Eq avec une méthode supplémentaire compareEquality :: a -> a -> Bool.

---

### Code haskell :

```haskell
-- Définition de la sous-classe AdvancedEq de Eq
class Eq a => AdvancedEq a where
  compareEquality :: a -> a -> Bool

-- Exemple : implémentation pour Int
instance AdvancedEq Int where
  compareEquality x y = x == y  -- on utilise l'égalité existante

-- Exemples d'utilisation
main :: IO ()
main = do
  print (compareEquality (5 :: Int) (5 :: Int))   -- True
  print (compareEquality (5 :: Int) (10 :: Int))  -- False
```

---

### 🔎 Explications

* `class Eq a => AdvancedEq a` :

  * `AdvancedEq` est une **sous-classe** de `Eq`.
  * Tout type `a` qui est `AdvancedEq` doit aussi être `Eq`.
* `compareEquality :: a -> a -> Bool` : méthode supplémentaire pour comparer deux valeurs.
* Dans l’exemple, pour `Int`, `compareEquality` utilise simplement `==` existant.

---

### ✅ Résultat attendu

```
True
False
```
