## HC10T10 : Classe Concatenatable

Créer une classe de type Concatenatable avec une fonction concatWith :: a -> a -> a.

L’implémenter pour le type [Char] (String). 

---

### Code haskell

```haskell
-- Définition de la classe de type Concatenatable
class Concatenatable a where
  concatWith :: a -> a -> a

-- Implémentation pour [Char] (String)
instance Concatenatable [Char] where
  concatWith = (++)

-- Exemples d'utilisation
main :: IO ()
main = do
  let str1 = "Bonjour "
      str2 = "le monde !"
  putStrLn (concatWith str1 str2)  -- "Bonjour le monde !"
```

---

### 🔎 Explications

* `class Concatenatable a where concatWith :: a -> a -> a` : définit une **interface** pour concaténer deux valeurs du même type.
* `instance Concatenatable [Char]` : implémente cette interface pour les chaînes de caractères en utilisant l’opérateur `(++)`.
* `concatWith str1 str2` concatène `str1` et `str2`.

---

### ✅ Résultat attendu

```
Bonjour le monde !
```
