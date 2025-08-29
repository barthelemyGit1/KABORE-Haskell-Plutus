## HC14T4 : Extension TypeApplications

Activer l’extension TypeApplications et créer une fonction qui lit une String et la convertit en Int avec read.

---

## 🚀 Étape 1 : Activer l’extension

En haut de ton fichier `app/Main.hs`, ajoute :

```haskell
{-# LANGUAGE TypeApplications #-}
```

---

## 🚀 Étape 2 : Exemple de code avec `read`

On va écrire une fonction qui lit une `String` et la convertit en `Int` en utilisant `read @Int` :

```haskell
{-# LANGUAGE TypeApplications #-}

module Main where

convertStringToInt :: String -> Int
convertStringToInt s = read @Int s

main :: IO ()
main = do
    let input = "12345"
    let number = convertStringToInt input
    putStrLn $ "La chaîne \"" ++ input ++ "\" convertie en Int = " ++ show number
```

---

## 🚀 Étape 3 : Compiler et exécuter

```bash
cabal build
cabal run
```

👉 Résultat attendu :

```
La chaîne "12345" convertie en Int = 12345
```

---

✅ Grâce à `TypeApplications`, on peut écrire `read @Int "12345"` au lieu d’un `read "12345" :: Int`.
