## HC14T10 : Test suite Cabal pour counts

Écrire une suite de tests Cabal pour un module qui vérifie le bon fonctionnement de la fonction counts.

---

## 1️⃣ Structure du projet Cabal

```
ProjetCabal/
├── app/
│   └── Main.hs
├── src/
│   └── CharCounts.hs
├── test/
│   └── TestCounts.hs
├── ProjetCabal.cabal
```

* `src/` → modules de la bibliothèque (`CharCounts`, `Result`, etc.)
* `app/` → exécutable principal
* `test/` → fichiers de test

---

## 2️⃣ Modifier le `.cabal` pour ajouter une suite de tests

```cabal
test-suite ProjetCabal-test
  type:                exitcode-stdio-1.0
  hs-source-dirs:      test
  main-is:             TestCounts.hs
  build-depends:       base >=4.7 && <5,
                       ProjetCabal,    -- la bibliothèque contenant CharCounts
                       HUnit >=1.6.0.0
  default-language:    Haskell2010
```

* `build-depends: ProjetCabal` → permet au test d’importer `CharCounts`.
* `HUnit` est une bibliothèque pour les tests unitaires.

---

## 3️⃣ Exemple de test avec HUnit (`test/TestCounts.hs`)

```haskell
module Main where

import Test.HUnit
import CharCounts

-- Tests pour counts
testCounts1 :: Test
testCounts1 = TestCase $ 
    assertEqual "Comptage des caractères dans 'hello'"
                [('e',1),('h',1),('l',3),('o',1)]
                (counts "hello")

testCounts2 :: Test
testCounts2 = TestCase $ 
    assertEqual "Comptage des caractères dans 'aaaabbb'"
                [('a',4),('b',3)]
                (counts "aaaabbb")

testCounts3 :: Test
testCounts3 = TestCase $ 
    assertEqual "Comptage des caractères vide"
                []
                (counts "")

-- Liste de tous les tests
tests :: Test
tests = TestList [testCounts1, testCounts2, testCounts3]

main :: IO ()
main = do
    countsResult <- runTestTT tests
    if errors countsResult + failures countsResult == 0
       then putStrLn "Tous les tests ont réussi !"
       else putStrLn "Des tests ont échoué."
```

### Explications

1. **`assertEqual`** compare la sortie attendue et la sortie réelle.
2. Chaque test a un **message descriptif** pour savoir quel test échoue.
3. `runTestTT tests` exécute tous les tests.

---

## 4️⃣ Lancer les tests

```bash
cabal test
```

* Cabal compile la bibliothèque et le test, puis exécute `TestCounts.hs`.
* Résultat : les tests passent ou échouent avec le détail.
