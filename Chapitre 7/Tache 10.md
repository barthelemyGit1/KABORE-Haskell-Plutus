## HC7T10 : Fonction avec plusieurs contraintes de classes de types

Écrire une fonction describeAndCompare qui prend deux valeurs Describable et retourne la description de la plus grande.

---

### Code Haskell

```haskell
-- Définition de la classe Describable
class Describable a where
    describe :: a -> String

-- Instance pour Int
instance Describable Int where
    describe x = "Valeur entière : " ++ show x

-- Fonction describeAndCompare
describeAndCompare :: (Describable a, Ord a) => a -> a -> String
describeAndCompare x y
    | x >= y    = describe x
    | otherwise = describe y

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ describeAndCompare (5 :: Int) (10 :: Int)    -- "Valeur entière : 10"
    print $ describeAndCompare (20 :: Int) (15 :: Int)   -- "Valeur entière : 20"

```

---

### Explications

1. **Contraintes multiples**

   ```haskell
   (Describable a, Ord a) => a -> a -> String
   ```

   * `Describable a` : permet d’appeler `describe`.
   * `Ord a` : permet de comparer `x >= y`.

2. **Logique**

   ```haskell
   describeAndCompare x y
       | x >= y    = describe x
       | otherwise = describe y
   ```

   * Si `x` est plus grand ou égal à `y`, on retourne sa description.
   * Sinon, on retourne celle de `y`.

3. **Exemple avec Int**

   * L’instance `Describable Int` permet de tester la fonction facilement.

---

### Exemple de sortie

```
"Valeur entière : 10"
"Valeur entière : 20"
```

---

💡 Astuce : Cette fonction peut être utilisée pour **tout type qui est à la fois `Describable` et `Ord`**, par exemple des types personnalisés comme `Shape` si on définit une instance `Ord` pour eux.

Veux‑tu que je te montre un exemple avec **`Shape`** comparé par aire et décrit avec `Describable` ?
