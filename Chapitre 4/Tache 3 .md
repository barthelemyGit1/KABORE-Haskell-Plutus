## HC4T3 - Tâche 3 : Définir une fonction gradeComment

Écrire une fonction gradeComment :: Int -> String qui prend une note et retourne un commentaire selon la tranche :

90 - 100 → « Excellent ! »

70 - 89 → « Bon travail ! »

50 - 69 → « Tu as réussi. »

0 - 49 → « Peut mieux faire. »

Tout autre nombre → « Note invalide. »

---

## ✅ Code Haskell

```haskell
-- Fonction qui retourne un commentaire en fonction de la note
gradeComment :: Int -> String
gradeComment n
    | n >= 90 && n <= 100 = "Excellent !"
    | n >= 70 && n <= 89  = "Bon travail !"
    | n >= 50 && n <= 69  = "Tu as réussi."
    | n >= 0  && n <= 49  = "Peut mieux faire."
    | otherwise           = "Note invalide."

-- Fonction principale avec quelques tests
main :: IO ()
main = do
    putStrLn ("Note 95 : " ++ gradeComment 95)
    putStrLn ("Note 75 : " ++ gradeComment 75)
    putStrLn ("Note 55 : " ++ gradeComment 55)
    putStrLn ("Note 30 : " ++ gradeComment 30)
    putStrLn ("Note 120 : " ++ gradeComment 120)
```

---

## 📝 Explication du code

1. **La fonction `gradeComment`**

   * Signature :

     ```haskell
     gradeComment :: Int -> String
     ```

     Elle prend un entier (`Int`) et renvoie une chaîne (`String`).
   * Utilise des **gardes (`|`)** pour tester différentes conditions :

     * `n >= 90 && n <= 100` → `"Excellent !"`.
     * `n >= 70 && n <= 89` → `"Bon travail !"`.
     * `n >= 50 && n <= 69` → `"Tu as réussi."`.
     * `n >= 0 && n <= 49` → `"Peut mieux faire."`.
     * `otherwise` → cas par défaut → `"Note invalide."`.

   👉 C’est une **fonction pure**, car elle dépend uniquement de son argument `n`.

2. **La fonction `main`**

   * De type `IO ()` → elle gère les entrées/sorties.
   * Affiche quelques résultats prédéfinis avec `putStrLn`.
   * Pas de `getLine` pour éviter le blocage dans les compilateurs en ligne.

---

## ▶ Exemple de sortie

En lançant ce code, tu verras :

```
Note 95 : Excellent !
Note 75 : Bon travail !
Note 55 : Tu as réussi.
Note 30 : Peut mieux faire.
Note 120 : Note invalide.
```
