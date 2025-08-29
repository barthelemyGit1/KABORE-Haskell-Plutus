## HC14T6 : Structure du projet avec src et app

Créer une structure de projet Cabal avec les dossiers src et app. Placer le module principal dans app et les autres modules dans src.

---

## 3️⃣ Exemple de `Main.hs` dans `app/`

```haskell
module Main where

import Result

main :: IO ()
main = do
    let ok = Success 42
        failResult = Failure "Erreur" :: Result Int
    putStrLn $ describeResult ok
    putStrLn $ describeResult failResult
```

* Ici, `Main.hs` importe le module `Result` depuis `src/`.

---

## 4️⃣ Exemple de module `Result.hs` dans `src/`

```haskell
module Result where

data Result a = Success a | Failure String
  deriving (Show)

describeResult :: Show a => Result a -> String
describeResult r@(Success x) = "Succès avec valeur : " ++ show x
describeResult (Failure msg) = "Échec : " ++ msg
```

* `Result` est un module réutilisable, séparé du code principal.

---

## 5️⃣ Configuration dans `ProjetCabal.cabal`

```cabal
executable ProjetCabal
  main-is:          Main.hs
  hs-source-dirs:   app, src
  build-depends:    base >=4.7 && <5
  default-language: Haskell2010
```

* `hs-source-dirs: app, src` → Cabal sait chercher `Main.hs` et tous les modules dans `src/`.
  
---

## 1️⃣ Module `Result.hs`

### Explications :

1. **`module Result where`**

   * Déclare que ce fichier est un module appelé `Result`.
   * Permet à d’autres fichiers (`Main.hs`) d’importer ce module.

2. **`data Result a = Success a | Failure String`**

   * Définit un **type générique paramétré** `Result a` qui peut être :

     * `Success a` → succès contenant une valeur de type `a` (ex : `Int`, `String`, etc.)
     * `Failure String` → échec avec un message d’erreur.

3. **`deriving (Show)`**

   * Permet d’afficher un `Result a` avec `show` pour déboguer.

4. **`describeResult :: Show a => Result a -> String`**

   * Fonction qui transforme un `Result a` en `String` lisible.
   * `Show a =>` → le type `a` doit être affichable (avoir une instance `Show`).

5. **Pattern matching et `@`**

```haskell
describeResult r@(Success x) = "Succès avec valeur : " ++ show x
```

* `r@(Success x)` → capture **à la fois le constructeur entier** (`r`) et la valeur contenue (`x`).
* Ici on utilise `x` pour l’afficher, mais `r` pourrait être utilisé si on voulait.

```haskell
describeResult (Failure msg) = "Échec : " ++ msg
```

* Si c’est un échec, on récupère seulement le message `msg`.

---

## 2️⃣ Module `Main.hs`

### Explications :

1. **`module Main where`**

   * Déclare que ce fichier contient l’exécutable principal.

2. **`import Result`**

   * On importe le module `Result` pour utiliser `Result a` et `describeResult`.

3. **`main :: IO ()`**

   * Point d’entrée du programme.
   * `IO ()` signifie que la fonction effectue des actions d’entrée/sortie (ici, afficher du texte).

4. **Déclaration des résultats**

```haskell
let ok = Success 42
    failResult = Failure "Erreur" :: Result Int
```

* `ok` → un succès avec la valeur `42` (`Result Int`).
* `failResult` → un échec avec message `"Erreur"`.
* L’annotation `:: Result Int` est nécessaire car `Failure` ne contient pas de valeur et Haskell doit connaître le type `a`.

5. **Affichage des résultats**

```haskell
putStrLn $ describeResult ok
putStrLn $ describeResult failResult
```

* Utilise `describeResult` pour transformer les `Result a` en `String`.
* `putStrLn` affiche ces chaînes dans le terminal.

---

## 6️⃣ Compilation et exécution

```bash
cabal build
cabal run ProjetCabal
```

* Cabal compile `Main.hs` dans `app/` et utilise les modules du dossier `src/`.

✅ Résultat attendu :

```
Succès avec valeur : 42
Échec : Erreur
```
