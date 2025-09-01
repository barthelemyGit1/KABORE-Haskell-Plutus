## HC19T2 : Fonction addThreeApplicative

Implémenter une fonction addThreeApplicative qui additionne trois valeurs Maybe Int en style applicatif.

---

On veut écrire une fonction :

```haskell
addThreeApplicative :: Maybe Int -> Maybe Int -> Maybe Int -> Maybe Int
```

qui additionne **trois `Maybe Int`** en style **applicatif**.

---

### 1. Rappel : `Maybe` est déjà une instance d’`Applicative`

```haskell
instance Applicative Maybe where
  pure = Just
  Nothing <*> _ = Nothing
  (Just f) <*> something = fmap f something
```

Donc on peut utiliser `<$>` et `<*>` directement.

---

### 2. Définition de la fonction

```haskell
addThreeApplicative :: Maybe Int -> Maybe Int -> Maybe Int -> Maybe Int
addThreeApplicative mx my mz =
  (\x y z -> x + y + z) <$> mx <*> my <*> mz
```

Ici :

* `(\x y z -> x + y + z)` est une fonction anonyme qui prend trois `Int` et fait la somme.
* `<$>` applique cette fonction au premier `Maybe Int` (`mx`).
* `<*>` propage ensuite au deuxième (`my`), puis au troisième (`mz`).
* Si au moins un argument est `Nothing`, tout le calcul donne `Nothing`.

---

### 3. Exemples d’utilisation

```haskell
main :: IO ()
main = do
  print $ addThreeApplicative (Just 2) (Just 3) (Just 5)
  -- Just 10

  print $ addThreeApplicative (Just 10) Nothing (Just 5)
  -- Nothing

  print $ addThreeApplicative Nothing (Just 1) (Just 2)
  -- Nothing
```
