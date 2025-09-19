## HC20T3 : Calculatrice avec la monade Writer

Créer une calculatrice avec la monade Writer pour garder la trace de toutes les opérations.

---

## Code Haskell

```haskell
{-# LANGUAGE OverloadedStrings #-}

import Control.Monad.Writer

-- Type alias : une calculatrice qui retourne un Int + un log (String)
type Calc a = Writer [String] a

-- Fonctions de base
add :: Int -> Int -> Calc Int
add x y = do
  tell ["Ajout de " ++ show x ++ " + " ++ show y]
  return (x + y)

sub :: Int -> Int -> Calc Int
sub x y = do
  tell ["Soustraction de " ++ show x ++ " - " ++ show y]
  return (x - y)

mul :: Int -> Int -> Calc Int
mul x y = do
  tell ["Multiplication de " ++ show x ++ " * " ++ show y]
  return (x * y)

divide :: Int -> Int -> Calc (Maybe Int)
divide _ 0 = do
  tell ["Division par zéro (erreur)"]
  return Nothing
divide x y = do
  tell ["Division de " ++ show x ++ " / " ++ show y]
  return (Just (x `div` y))

-- Exemple d'utilisation
main :: IO ()
main = do
  let computation = do
        a <- add 5 3
        b <- mul a 2
        c <- sub b 4
        d <- divide c 2
        return d

      (result, logLines) = runWriter computation

  putStrLn "Résultat :"
  print result
  putStrLn "\nHistorique :"
  mapM_ putStrLn logLines
```

---

## Explications

* **Writer** est une monade qui associe une valeur de calcul avec un journal (log).
  Ici, on choisit `[String]` comme type de log.

* `tell` : ajoute une ligne dans le journal.

* Chaque opération (`add`, `sub`, `mul`, `divide`) :

  * effectue le calcul,
  * enregistre une phrase décrivant l’action.

* `runWriter` :

  * renvoie un couple `(résultat, historique)`.

---

### Exemple d’exécution

```text
Résultat :
Just 2

Historique :
Ajout de 5 + 3
Multiplication de 8 * 2
Soustraction de 16 - 4
Division de 12 / 2
```

Si tu essaies `divide 10 0`, tu obtiendras :

```
Résultat :
Nothing

Historique :
Division par zéro (erreur)
```

---

💡 **Astuce** : Tu peux adapter le type du Writer (`Writer String` au lieu de `[String]`) pour avoir un log formaté différemment (concaténation plutôt que liste).
