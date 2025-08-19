## HC3T7 - Tâche avancée 7 : Déterminer la saison en fonction du mois avec des gardes

Définir season :: Int -> String.

Utiliser des gardes pour retourner :

12, 1, 2 → « Hiver »

3, 4, 5 → « Printemps »

6, 7, 8 → « Été »

9, 10, 11 → « Automne »

Tester avec season 3, season 7 et season 11.

---

## ✅ Code Haskell

```haskell
-- Fonction season
season :: Int -> String
season m
    | m == 12 || m == 1 || m == 2  = "Hiver"
    | m == 3  || m == 4 || m == 5  = "Printemps"
    | m == 6  || m == 7 || m == 8  = "Été"
    | m == 9  || m == 10 || m == 11 = "Automne"
    | otherwise = "Mois invalide"

-- Fonction principale pour tester
main :: IO ()
main = do
    print (season 3)   -- "Printemps"
    print (season 7)   -- "Été"
    print (season 11)  -- "Automne"
    print (season 15)  -- "Mois invalide"
```

---

## 🧠 Explication

1. **Signature**

   ```haskell
   season :: Int -> String
   ```

   * L’entrée est un `Int` (numéro du mois).
   * La sortie est une `String` (nom de la saison).

2. **Gardes (`|`)**

   * `m == 12 || m == 1 || m == 2` → hiver
   * `m == 3 || m == 4 || m == 5` → printemps
   * `m == 6 || m == 7 || m == 8` → été
   * `m == 9 || m == 10 || m == 11` → automne
   * `otherwise` → si le mois n’est pas valide (par ex. 15).

3. **Tests**

   * `season 3` → `"Printemps"` ✅
   * `season 7` → `"Été"` ✅
   * `season 11` → `"Automne"` ✅
   * `season 15` → `"Mois invalide"` ✅

---
