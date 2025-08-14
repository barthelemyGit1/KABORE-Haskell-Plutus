## HC3T1 - Tâche 1 : Vérifier si un nombre est positif, négatif ou nul
Définir une fonction checkNumber :: Int -> String.

Utiliser une instruction if-then-else pour vérifier si le nombre est positif, négatif ou nul.

Retourner « Positif », « Négatif » ou « Zéro » selon le cas.

Tester la fonction avec checkNumber 5, checkNumber (-3) et checkNumber 0.

---

## ✅ Code Haskell

```haskell
-- Définir une fonction checkNumber
checkNumber :: Int -> String
checkNumber n =
    if n > 0 then "Positif"
    else if n < 0 then "Négatif"
    else "Zéro"

-- Fonction principale
main :: IO ()
main = do
    print (checkNumber 5)   -- "Positif"
    print (checkNumber (-3)) -- "Négatif"
    print (checkNumber 0)    -- "Zéro"
```

---

## 🧠 Explication

1. **Signature**

   ```haskell
   checkNumber :: Int -> String
   ```

   * La fonction prend un entier (`Int`) et retourne une chaîne (`String`).

2. **Structure `if-then-else`**

   * `if n > 0 then "Positif"` → si le nombre est strictement supérieur à 0.
   * `else if n < 0 then "Négatif"` → si le nombre est strictement inférieur à 0.
   * `else "Zéro"` → dans tous les autres cas, donc quand `n` est exactement 0.

3. **main**

   * Teste la fonction avec trois cas différents : positif, négatif et zéro.

---

## ▶️ Résultat attendu

```
"Positif"
"Négatif"
"Zéro"
```

---
