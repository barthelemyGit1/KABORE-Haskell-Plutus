## HC16T3: Factorielle

Définir une fonction qui calcule la factorielle d'un nombre.

---

## ✅ Code Haskell pour calculer la factorielle

```haskell
module Main where

-- Définition de la factorielle (version récursive)
factorielle :: Integer -> Integer
factorielle 0 = 1                         -- Cas de base : 0! = 1
factorielle n = n * factorielle (n - 1)   -- Cas récursif

main :: IO ()
main = do
    putStrLn "Entrez un nombre :"
    input <- getLine
    let n = read input :: Integer
    putStrLn $ "La factorielle de " ++ show n ++ " est " ++ show (factorielle n)
```

---

## 📝 Explication

1. **Signature de type**

   ```haskell
   factorielle :: Integer -> Integer
   ```

   * La fonction prend un entier (`Integer`) et retourne un entier.
   * On choisit `Integer` plutôt que `Int` car `Int` peut déborder si le nombre est grand.

2. **Cas de base**

   ```haskell
   factorielle 0 = 1
   ```

   * Par définition, `0! = 1`.

3. **Cas récursif**

   ```haskell
   factorielle n = n * factorielle (n - 1)
   ```

   * Exemple : `factorielle 5 = 5 * factorielle 4`.
   * L’évaluation continue jusqu’au cas de base.

4. **Fonction `main`**

   * Demande un nombre à l’utilisateur.
   * Convertit l’entrée en entier (`read input :: Integer`).
   * Calcule et affiche la factorielle.

---

## ⚡ Exemple d’exécution

```
Entrez un nombre :
5
La factorielle de 5 est 120
```
