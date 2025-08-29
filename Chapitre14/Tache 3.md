## HC14T3 : Extension NumericUnderscores

Activer l’extension NumericUnderscores. Créer des variables avec de grands nombres et les afficher.

---

## 🚀 Étape 1 : Activer l’extension

Deux façons possibles :

### (A) Dans le code Haskell

Ajoute en haut de ton `app/Main.hs` :

```haskell
{-# LANGUAGE NumericUnderscores #-}
```

### (B) Dans ton `.cabal`

Ajoute dans la section `executable` :

```cabal
default-extensions: NumericUnderscores
```

👉 Je te conseille d’abord la **solution (A)** (plus locale, plus simple).

---

## 🚀 Étape 2 : Exemple de `Main.hs`

```haskell
{-# LANGUAGE NumericUnderscores #-}

module Main where

main :: IO ()
main = do
    let grandNombre = 1_000_000
        encorePlusGrand = 12_345_678_901_234
    putStrLn $ "Grand nombre : " ++ show grandNombre
    putStrLn $ "Encore plus grand : " ++ show encorePlusGrand
```

---

## 🚀 Étape 3 : Compiler et exécuter

Recompile ton projet :

```bash
cabal build
cabal run
```

👉 Résultat attendu :

```
Grand nombre : 1000000
Encore plus grand : 12345678901234
```
