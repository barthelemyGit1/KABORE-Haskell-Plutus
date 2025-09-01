## HC19T4 : Fonction liftAndMultiply avec liftA2

Créer une fonction liftAndMultiply qui élève une fonction binaire (Int -> Int -> Int) avec liftA2.

---

### 1. Rappel rapide : `liftA2`

```haskell
liftA2 :: Applicative f => (a -> b -> c) -> f a -> f b -> f c
```

* Ça « lève » une fonction binaire classique en version qui travaille sur des conteneurs/applicatifs.
* Exemple avec `Maybe` :

  ```haskell
  liftA2 (+) (Just 3) (Just 5) == Just 8
  liftA2 (*) (Just 3) Nothing  == Nothing
  ```

---

### 2. Définition demandée

```haskell
import Control.Applicative (liftA2)

liftAndMultiply :: (Int -> Int -> Int) -> Maybe Int -> Maybe Int -> Maybe Int
liftAndMultiply f mx my = liftA2 f mx my
```

Ici :

* `f` est une fonction binaire `Int -> Int -> Int` (par exemple `(*)`, `(+)`, `\x y -> x - y` …).
* `mx` et `my` sont des `Maybe Int`.
* `liftA2 f mx my` applique `f` si les deux sont `Just`, sinon ça donne `Nothing`.

---

### 3. Exemples d’utilisation

```haskell
main :: IO ()
main = do
  print $ liftAndMultiply (*) (Just 3) (Just 4)     -- Just 12
  print $ liftAndMultiply (+) (Just 10) (Just 5)    -- Just 15
  print $ liftAndMultiply (*) (Just 7) Nothing      -- Nothing
```
