## HC3T2 - Tâche 2 : Déterminer la note à partir d’un score avec des gardes

Définir une fonction grade :: Int -> String.

Utiliser des gardes (|) pour classer les scores en notes :

90 et plus : « A »

80 à 89 : « B »

70 à 79 : « C »

60 à 69 : « D »

En dessous de 60 : « F »

Tester la fonction avec grade 95, grade 72 et grade 50.

---
## ✅ Code Haskell

```haskell
-- Définir la fonction grade
grade :: Int -> String
grade score
    | score >= 90 = "A"
    | score >= 80 = "B"
    | score >= 70 = "C"
    | score >= 60 = "D"
    | otherwise   = "F"

-- Fonction principale pour tester
main :: IO ()
main = do
    print (grade 95)  -- "A"
    print (grade 72)  -- "C"
    print (grade 50)  -- "F"
```

---

## 🧠 Explication

1. **Signature**

   ```haskell
   grade :: Int -> String
   ```

   * La fonction prend un entier (`Int`) représentant le score et retourne une chaîne (`String`) représentant la note.

2. **Gardes (`|`)**

   * `| score >= 90 = "A"` → si le score est 90 ou plus.
   * `| score >= 80 = "B"` → si le score est entre 80 et 89.
   * `| score >= 70 = "C"` → si le score est entre 70 et 79.
   * `| score >= 60 = "D"` → si le score est entre 60 et 69.
   * `| otherwise   = "F"` → pour tout score inférieur à 60.

3. **`otherwise`**

   * C’est l’équivalent de `else` en Haskell, toujours placé en dernier.

---

## ▶️ Résultat attendu

```
"A"
"C"
"F"
```

---
