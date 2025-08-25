## HC4T2 - Tâche 2 : Définir une fonction dayType

Créer une fonction dayType :: String -> String qui détermine si un jour de la semaine est un jour de semaine ou un week-end.

« Saturday » et « Sunday » → « C'est le week-end ! »

Tout autre jour de la semaine → « C'est un jour de semaine. »

Si le jour est invalide, retourner « Jour invalide ».

---

## ✅ Code Haskell complet

```haskell
-- Fonction qui détermine le type du jour
dayType :: String -> String
dayType "Saturday" = "C'est le week-end !"
dayType "Sunday"   = "C'est le week-end !"
dayType "Monday"   = "C'est un jour de semaine."
dayType "Tuesday"  = "C'est un jour de semaine."
dayType "Wednesday"= "C'est un jour de semaine."
dayType "Thursday" = "C'est un jour de semaine."
dayType "Friday"   = "C'est un jour de semaine."
dayType _          = "Jour invalide"

-- Fonction principale (pas d'entrée utilisateur pour éviter blocage en ligne)
main :: IO ()
main = do
    putStrLn (dayType "Monday")
    putStrLn (dayType "Saturday")
    putStrLn (dayType "Sunday")
    putStrLn (dayType "Holiday")   -- Exemple d'entrée invalide
```

---

## 📝 Explication

1. **La fonction `dayType`**

   * Signature :

     ```haskell
     dayType :: String -> String
     ```

     Elle prend une chaîne (`String`) en entrée et renvoie une autre chaîne (`String`).
   * **Pattern matching** :

     * `"Saturday"` et `"Sunday"` → `"C'est le week-end !"`.
     * Les autres jours `"Monday" ... "Friday"` → `"C'est un jour de semaine."`.
     * `_` (underscore) → cas par défaut → `"Jour invalide"`.

   👉 La fonction est **pure** : elle dépend uniquement de son paramètre.

2. **La fonction `main`**

   ```haskell
   main :: IO ()
   ```

   * C’est la fonction principale qui exécute le programme.
   * Ici, pas de `getLine` (pas de saisie utilisateur) pour éviter les erreurs de *timeout* dans un compilateur en ligne.
   * On affiche directement des tests prédéfinis avec `putStrLn`.

---
