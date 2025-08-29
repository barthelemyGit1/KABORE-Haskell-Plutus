## HC14T2 : Ajouter une dépendance et afficher un nombre aléatoire 

Modifier le fichier .cabal pour inclure une dépendance sur le paquet random et afficher un nombre aléatoire entre 1 et 100.

---

## 🚀 Étape 1 : Modifier le fichier `.cabal`

Ouvre ton fichier `MonProjet.cabal` et cherche la section de l’exécutable (souvent `executable monprojet`).
Ajoute **random** dans `build-depends`. Exemple minimal :

```cabal
cabal-version:       >=1.10
name:                MonProjet
version:             0.1.0.0
build-type:          Simple

executable MonProjet
  main-is:             Main.hs
  hs-source-dirs:      app
  default-language:    Haskell2010
  build-depends:       base >=4.7 && <5,
                       random
```

⚠️ `random` est la bibliothèque standard de Haskell pour les nombres aléatoires.

---

## 🚀 Étape 2 : Modifier `app/Main.hs`

Utilise `System.Random` pour générer un nombre :

```haskell
module Main where

import System.Random (randomRIO)

main :: IO ()
main = do
    num <- randomRIO (1, 100) :: IO Int
    putStrLn $ "Nombre aléatoire entre 1 et 100 : " ++ show num
```

---

## 🚀 Étape 3 : Construire et exécuter

Recompile avec :

```bash
cabal build
```

Puis lance :

```bash
cabal run
```

👉 Exemple de sortie :

```
Nombre aléatoire entre 1 et 100 : 57
```

---

✅ Résultat attendu : un nombre aléatoire **différent à chaque exécution**.
