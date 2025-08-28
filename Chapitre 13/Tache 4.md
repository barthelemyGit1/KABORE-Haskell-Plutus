## HC13T4 : Module SumNonEmpty

Écrire un module Haskell nommé SumNonEmpty qui définit une fonction sumNonEmpty et retourne une erreur si elle est appelée sur une liste vide.

---

### Code haskell
Ici on va créer un **module séparé** `SumNonEmpty.hs` qui expose une fonction `sumNonEmpty`.
Cette fonction :

* retourne la somme des éléments d’une liste non vide
* lève une erreur (`error`) si la liste est vide

---

### ✅ Fichier `SumNonEmpty.hs`

```haskell
module SumNonEmpty (sumNonEmpty) where

-- Fonction qui somme une liste non vide
sumNonEmpty :: Num a => [a] -> a
sumNonEmpty [] = error "Error: sumNonEmpty called with an empty list!"
sumNonEmpty xs = sum xs
```

---

### ✅ Fichier `Main.hs` pour tester

```haskell
import SumNonEmpty

main :: IO ()
main = do
    putStrLn "Somme d'une liste non vide [1,2,3,4] :"
    print (sumNonEmpty [1,2,3,4])

    putStrLn "Test avec une liste vide (va provoquer une erreur):"
    print (sumNonEmpty [])
```

---

### Explications

```
module SumNonEmpty (sumNonEmpty) where
```

Déclare un module nommé SumNonEmpty.

Seule la fonction sumNonEmpty est exportée (accessible depuis d’autres fichiers).
```
sumNonEmpty [] = error "..."
```

Cas où la liste est vide → on déclenche une erreur avec un message clair.

```
sumNonEmpty xs = sum xs
```

Cas général → utilise la fonction sum de Prelude pour calculer la somme.

---

🔎 Résultat attendu :

```
Somme d'une liste non vide [1,2,3,4] :
10
Test avec une liste vide (va provoquer une erreur):
Main.exe: Error: sumNonEmpty called with an empty list!
```
