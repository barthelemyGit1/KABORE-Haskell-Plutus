## HC14T7 : Composant bibliothèque dans le .cabal 

Modifier le fichier .cabal pour supporter un composant bibliothèque en plus de l’exécutable principal. 

---

## 3️⃣ Modifier le fichier `.cabal`

Voici un exemple de fichier `ProjetCabal.cabal` avec **bibliothèque + exécutable** :

```cabal
cabal-version:       >=1.10
name:                ProjetCabal
version:             0.1.0.0
build-type:          Simple
synopsis:            Exemple projet Cabal avec lib et exe
author:              Moi

library
  hs-source-dirs:    src
  exposed-modules:   Result, MyMath
  build-depends:     base >=4.7 && <5
  default-language:  Haskell2010

executable ProjetCabal
  main-is:           Main.hs
  hs-source-dirs:    app
  build-depends:     base >=4.7 && <5,
                     ProjetCabal  -- on importe notre bibliothèque
  default-language:  Haskell2010
```

### Explications :

1. **library**

   * `hs-source-dirs: src` → tous les modules dans `src/` sont inclus dans la bibliothèque.
   * `exposed-modules: Result, MyMath` → ces modules sont visibles pour les exécutables.

2. **executable**

   * `main-is: Main.hs` → fichier principal.
   * `hs-source-dirs: app` → Cabal sait chercher `Main.hs` dans `app/`.
   * `build-depends: ProjetCabal` → l’exécutable utilise la bibliothèque définie ci-dessus.

---

## 4️⃣ Exemple d’utilisation dans `Main.hs`

```haskell
module Main where

import Result
import MyMath

main :: IO ()
main = do
    let r = Success 42
    putStrLn $ describeResult r
    putStrLn $ "Multiplication 3 * 5 = " ++ show (multiply 3 5)
```

* `Result` et `MyMath` proviennent de la **bibliothèque** du projet.

---

## 5️⃣ Compilation et exécution

```bash
cabal build
cabal run ProjetCabal
```

✅ Résultat attendu :

```
Succès avec valeur : 42
Multiplication 3 * 5 = 15
```
