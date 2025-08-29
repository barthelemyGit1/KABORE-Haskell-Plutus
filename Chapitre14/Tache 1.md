## HC14T1 : Initialiser un projet Cabal Créer un projet Haskell en utilisant cabal init.

Ajouter un exécutable principal qui affiche « Hello, Cabal! ».

---

## 🚀 Étape 1 : Initialiser un projet Cabal

Dans le terminal, tape :

```bash
cabal init --non-interactive --minimal --exe --overwrite
```

Cela crée un projet minimal avec :

* un fichier `*.cabal` (ex. `MonProjet.cabal`),
* un dossier `app/` qui contiendra le `Main.hs`,
* un `Setup.hs` minimal.

👉 Pour configurer en mode interactif, Nous pouvons juste faire :

```bash
cabal init
```

et répondre aux questions (choisis `executable` quand il demande le type de projet).

---

## 🚀 Étape 2 : Éditer `app/Main.hs`

Ouvre `app/Main.hs` et mets :

```haskell
module Main where

main :: IO ()
main = putStrLn "Hello, Cabal!"
```

---

## 🚀 Étape 3 : Construire et exécuter

Compile le projet avec :

```bash
cabal build
```

Puis exécute avec :

```bash
cabal run
```

Cela verras :

```
Hello, Cabal!
```

---

✅ Résumé :

* `cabal init` crée la structure,
* `app/Main.hs` contient ton programme,
* `cabal run` lance ton exécutable.
