## HC16T1: Inverser une chaîne

Définir une fonction qui inverse une chaîne de caractères.

---

En Haskell, une `String` est juste une liste de `Char`, donc on peut utiliser la fonction standard `reverse`.

---

## ✅ Code haskell

```haskell
module Main where

-- Fonction qui inverse une chaîne
inverser :: String -> String
inverser str = reverse str

main :: IO ()
main = do
    putStrLn "Entrez une chaîne :"
    input <- getLine
    putStrLn $ "Chaîne inversée : " ++ inverser input
```

---

### ⚡ Explication

* `reverse` est une fonction standard de Prelude qui inverse une liste.
* Comme `String` = `[Char]`, ça marche directement sur les chaînes.
* Exemple d’exécution :

```
Entrez une chaîne :
haskell
Chaîne inversée : lleksah
```
