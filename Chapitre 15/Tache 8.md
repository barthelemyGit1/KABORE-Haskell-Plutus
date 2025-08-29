## HC15T8 : Fonction Either pour messages d’erreur détaillés en division

Définir une fonction utilisant Either pour fournir des messages d’erreur détaillés lors de divisions.

---

## ✅ Code Haskell : Division sécurisée avec `Either`

```haskell
module Main where

-- Fonction de division sécurisée avec Either
safeDivEither :: Double -> Double -> Either String Double
safeDivEither _ 0 = Left "Erreur : division par zéro."
safeDivEither x y
    | y < 0     = Left "Erreur : le dénominateur est négatif."
    | otherwise = Right (x / y)

-- Fonction principale
main :: IO ()
main = do
    let a = 100
        b = 0
        c = -5
        d = 20

    -- Exemple 1 : division par zéro
    print $ safeDivEither a b

    -- Exemple 2 : dénominateur négatif
    print $ safeDivEither a c

    -- Exemple 3 : division normale
    print $ safeDivEither a d
```

---

## ⚡ Explications

* `Either String Double`

  * `Left String` → erreur avec un **message explicite**
  * `Right Double` → succès avec la valeur calculée

* Exemple :

  ```haskell
  safeDivEither 10 0
  -- Left "Erreur : division par zéro."

  safeDivEither 10 (-2)
  -- Left "Erreur : le dénominateur est négatif."

  safeDivEither 10 2
  -- Right 5.0
  ```
