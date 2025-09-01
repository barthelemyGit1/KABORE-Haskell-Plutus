## HC19T1 : Instance Applicative pour Pair

Définir une instance Applicative pour un type de données personnalisé Pair a.

---

### 1. Définition du type

```haskell
data Pair a = Pair a a
  deriving (Show, Eq)
```

Ici, `Pair a` contient deux valeurs du même type `a`. Exemple :

```haskell
Pair 1 2
Pair "x" "y"
```

---

### 2. `Functor` obligatoire avant `Applicative`

Pour pouvoir définir `Applicative`, il faut d’abord définir `Functor`.

```haskell
instance Functor Pair where
  fmap f (Pair x y) = Pair (f x) (f y)
```

Cela applique une fonction `f` à chaque élément de la paire.
Exemple :

```haskell
fmap (+1) (Pair 3 4) == Pair 4 5
```

---

### 3. Instance `Applicative`

```haskell
instance Applicative Pair where
  pure x = Pair x x
  (Pair f g) <*> (Pair x y) = Pair (f x) (g y)
```

#### Explication :

* `pure x` crée une paire où les deux cases contiennent la même valeur (`Pair x x`).
  Exemple :

  ```haskell
  pure 7 == Pair 7 7
  ```

* `(<*>)` applique une paire de fonctions à une paire de valeurs.

  * Si on a `Pair f g` et `Pair x y`, alors le résultat est `Pair (f x) (g y)`.
  * Exemple :

    ```haskell
    Pair (+1) (*2) <*> Pair 10 20 == Pair 11 40
    ```

---

### 4. Petit test

```haskell
main :: IO ()
main = do
  print $ fmap (*3) (Pair 2 5)        -- Pair 6 15
  print $ pure "Hello"                -- Pair "Hello" "Hello"
  print $ Pair (++"!") reverse <*> Pair "Hi" "yo"  
  -- Résultat : Pair "Hi!" "oy"
```
