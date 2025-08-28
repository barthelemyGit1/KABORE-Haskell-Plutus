## HC13T7 : Utiliser un module personnalisé dans main

Écrire un programme qui importe une fonction de votre module SumNonEmpty et calcule la somme d’une liste de nombres.

---
## Code haskell

### 1️⃣ Module `SumNonEmpty.hs`

On suppose que tu as déjà ce module :

```haskell
module SumNonEmpty (sumNonEmpty) where

-- Fonction publique
sumNonEmpty :: Num a => [a] -> a
sumNonEmpty [] = error "sumNonEmpty: liste vide"
sumNonEmpty xs = sum xs
```

---

### 2️⃣ Programme principal `Main.hs`

```haskell
import SumNonEmpty  -- On importe notre module personnalisé

main :: IO ()
main = do
    putStrLn "Entrez une liste de nombres séparés par des espaces :"
    input <- getLine
    let numbers = map read (words input) :: [Int]
    let total = sumNonEmpty numbers
    putStrLn $ "La somme des nombres est : " ++ show total
```

---

### 3️⃣ Explications

1. **Import du module** :

   ```haskell
   import SumNonEmpty
   ```

   Cela rend disponible **uniquement la fonction `sumNonEmpty`**, comme définie dans la liste d’export du module.

2. **Lecture de la liste** :

   ```haskell
   let numbers = map read (words input) :: [Int]
   ```

   * `words` sépare la chaîne entrée par l’espace.
   * `map read` convertit chaque élément en `Int`.

3. **Somme avec `sumNonEmpty`** :

   * Si la liste est vide, une erreur explicite sera générée.

---

### 4️⃣ Compilation et exécution

```powershell
ghc Main.hs
.\Main.exe
```

**Exemple d’entrée :**

```
1 2 3 4 5
```

**Sortie :**

```
La somme des nombres est : 15
```

Si la liste est vide, le programme affichera :

```
sumNonEmpty: liste vide
```
