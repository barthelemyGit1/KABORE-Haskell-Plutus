## HC20T1 : safeDivide avec la monade Maybe

Créer une fonction safeDivide qui effectue une division sécurisée en utilisant la monade Maybe.

---

## Code haskell

### `Main.hs`

```haskell
module Main where

-- Définition de safeDivide (division protégée avec Maybe)
safeDivide :: (Eq a, Fractional a) => a -> a -> Maybe a
safeDivide _ 0 = Nothing          -- Si dénominateur = 0 → Nothing
safeDivide x y = Just (x / y)     -- Sinon → Just résultat

-- Une fonction qui enchaîne deux divisions
chainDiv :: Double -> Double -> Double -> Maybe Double
chainDiv a b c = do
  r1 <- safeDivide a b
  r2 <- safeDivide r1 c
  return r2

main :: IO ()
main = do
  putStrLn "== safeDivide =="
  print (safeDivide 10 2)   -- Just 5.0
  print (safeDivide 10 0)   -- Nothing

  putStrLn "\n== chainDiv =="
  print (chainDiv 100 2 5)  -- Just 10.0
  print (chainDiv 100 0 5)  -- Nothing
```

---
### Explication 

Maybe gère la présence ou non d’une valeur.

safeDivide encapsule la division pour éviter les erreurs.

chainDiv montre comment enchaîner des opérations sûres grâce à la monade Maybe.

main illustre les différents scénarios.

---

💡 Résultat attendu dans le terminal :

```
== safeDivide ==
Just 5.0
Nothing

== chainDiv ==
Just 10.0
Nothing
```
