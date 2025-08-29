## HC14T5 : Type Result a et pattern matching avec @  

Écrire un programme Haskell utilisant un type personnalisé Result a et démontrer le pattern matching avec le symbole @.

---

## 🚀 Étape 1 : Créer le type `Result a` dans `src/Result.hs`

```haskell
module Result where

-- Type générique Result
data Result a = Success a | Failure String
  deriving (Show)

-- Fonction unique describeResult avec pattern matching et @
describeResult :: Show a => Result a -> String
describeResult r@(Success x) = "Succès avec valeur : " ++ show x
describeResult (Failure msg) = "Échec : " ++ msg
```

---

## 🚀 Étape 2 : Utiliser ce module dans `app/Main.hs`

```haskell
module Main where

import Result

main :: IO ()
main = do
    -- Création de différents résultats
    let successResult = Success 42                  -- Result Int
        failureResult = Failure "Division par zéro" :: Result Int
        stringResult = Success "Bonjour"           -- Result String

    -- Affichage avec describeResult
    putStrLn $ describeResult successResult
    putStrLn $ describeResult failureResult
    putStrLn $ describeResult stringResult
```
---

## Explication

---

## 1️⃣ Module `Result`

* `module Result where` → déclare que ce fichier est un module nommé `Result`.
* `data Result a = Success a | Failure String` → définit un **type paramétré** `Result a` :

  * `Success a` contient une valeur de type `a` (peut être `Int`, `String`, etc.)
  * `Failure String` contient un message d’erreur sous forme de `String`.
* `deriving (Show)` → permet d’utiliser `show` sur un `Result a` pour l’afficher.

1. `describeResult :: Show a => Result a -> String`

   * La contrainte `Show a =>` signifie : *pour pouvoir utiliser `show` sur la valeur contenue dans `Success`, le type `a` doit avoir une instance de `Show`*.
   * La fonction prend un `Result a` et renvoie une `String`.

2. `describeResult r@(Success x) = ...`

   * Le `r@(...)` est le **pattern matching avec @**.
   * `r@(Success x)` signifie : *on déstructure le constructeur `Success` pour récupérer `x`, mais on garde aussi `r` comme référence à toute la valeur (`Success x`) si on en a besoin*.
   * Ici on n’utilise que `x` pour l’afficher avec `show x`.

3. `describeResult (Failure msg) = ...`

   * Si c’est un `Failure`, on récupère directement le message `msg` et on construit la chaîne `"Échec : ..."`.

---

## 2️⃣ Module `Main`

* `module Main where` → ce fichier contient le programme principal.
* `import Result` → on importe le module `Result` pour utiliser `Result a` et `describeResult`.

---

* `successResult` → un `Result Int` avec la valeur `42`.
* `failureResult` → un `Result Int` avec une erreur. **Annotation de type obligatoire** car `Failure` ne contient pas de valeur de type `a` et GHC a besoin de savoir quel type utiliser pour `Show a`.
* `stringResult` → un `Result String` avec la valeur `"Bonjour"`.

---

* Chaque ligne utilise `describeResult` pour transformer un `Result a` en `String`.
* `putStrLn` affiche cette chaîne dans le terminal.

---

💡 Points clés à retenir :

1. **Pattern matching avec @** te permet d’avoir **à la fois l’accès au contenu et à la valeur complète**.
2. La **contrainte `Show a =>`** est indispensable pour afficher les types génériques.
3. Les annotations de type pour `Failure` sont nécessaires quand le type `a` ne peut pas être inféré.

---
👉 Résultat attendu :

```
Succès avec valeur : Success 42
Échec avec message : Failure "Division par zéro"
```

---

✅ Ici, le `@` est la clé :

* Dans `describeResult r@(Success _)`, tu fais **un pattern match** sur `Success _`, mais tu gardes aussi une référence au **terme complet** avec `r`.
